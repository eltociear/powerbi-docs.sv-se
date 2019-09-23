---
title: Konfigurera autentiseringsuppgifter programmässigt för Power BI
description: Konfigurera autentiseringsuppgifter programmässigt för Power BI för automatisering
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/25/2019
ms.openlocfilehash: f93119a621330d673fd2cf6035e0416646bd5e6a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61380194"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Konfigurera autentiseringsuppgifter programmässigt för Power BI

Följ dessa anvisningar för att konfigurera autentiseringsuppgifter programmässigt för Power BI.

## <a name="configure-a-credential-flow-for-data-sources"></a>Konfigurera en flöde för autentiseringsuppgifter för datakällor

1. Anropa [Hämta datakällor](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) för att identifiera datakällorna i datauppsättningen. I svarstexten för varje datakälla finns typ, anslutningsinformation, gateway och ID för datakälla.

    ```csharp
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First(); // select a datasource
    ```

2. Skapa en sträng för autentiseringsuppgifter enligt [exemplen för att uppdatera datakälla](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) beroende på typ av autentiseringsuppgifter.

    ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

3. Skapa autentiseringsuppgiftsinformation.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    credentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.None,
                    PrivacyLevelEnum.Private);
    ```

4. Anropa [Uppdatera datakälla](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) för att ange autentiseringsuppgifter, med gateway och ID för datakälla från steg 1 och med autentiseringsuppgiftsinformation från steg 4.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

### <a name="expired-on-premises-data-source-credentials-flow"></a>Flöde för autentiseringsuppgifter för lokal datakälla som upphört

1. [Följ steg 1 och 2 från det föregående scenariot](#configure-a-credential-flow-for-data-sources).

2. Anropa [Hämta gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) för att hämta den offentliga nyckeln för gatewayen.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Kryptera autentiseringsuppgifterna med den offentliga nyckeln för gatewayen med hjälp av RSA-krypteringsalgoritmen.

    Använd följande hjälpklass för kryptering:

    ```csharp
        public static class AsymmetricKeyEncryptionHelper
        {
            private const int SegmentLength = 85;
            private const int EncryptedLength = 128;

            /// <summary>

            /// Encrypts credentials using the RSA algorithm

            /// </summary>

            public static string EncodeCredentials(string credentialData, string publicKeyExponent, string publicKeyModulus)
            {
                using (RSACryptoServiceProvider rsa = new RSACryptoServiceProvider(EncryptedLength * 8))
                {
                    var parameters = rsa.ExportParameters(false);

                    parameters.Exponent = Convert.FromBase64String(publicKeyExponent);

                    parameters.Modulus = Convert.FromBase64String(publicKeyModulus);

                    rsa.ImportParameters(parameters);

                    return Encrypt(credentialData, rsa);
                }
            }

             private static string Encrypt(string plainText, RSACryptoServiceProvider rsa)
            {

                byte[] plainTextArray = Encoding.UTF8.GetBytes(plainText);

                // Split the message into different segments, each segment's length is 85. So, the result may be 85,85,85,20. 

                bool hasIncompleteSegment = plainTextArray.Length % SegmentLength != 0; 

                int segmentNumber = (!hasIncompleteSegment) ? (plainTextArray.Length / SegmentLength) : ((plainTextArray.Length SegmentLength) + 1);

                byte[] encryptedData = new byte[segmentNumber * EncryptedLength];

                int encryptedDataPosition = 0;

                for (var i = 0; i < segmentNumber; i++)
                {
                    int lengthToCopy;

                    if (i == segmentNumber - 1 && hasIncompleteSegment)

                        lengthToCopy = plainTextArray.Length % SegmentLength;

                    else

                        lengthToCopy = SegmentLength;

                    var segment = new byte[lengthToCopy];

                    Array.Copy(plainTextArray, i * SegmentLength, segment, 0, lengthToCopy);

                    var segmentEncryptedResult = rsa.Encrypt(segment, true);

                    Array.Copy(segmentEncryptedResult, 0, encryptedData, encryptedDataPosition, segmentEncryptedResult.Length);

                    encryptedDataPosition += segmentEncryptedResult.Length;

                }

                return Convert.ToBase64String(encryptedData);

            }

        }

        var encryptedCredentials = AsymmetricKeyEncryptionHelper.EncodeCredentials(credentials);
    ```

4. Skapa information om autentiseringsuppgifter med krypterade autentiseringsuppgifter.

    ```csharp
    var credentialDetails = new CredentialDetails(
                    encryptedCredentials,
                    CredentialTypeEnum.Basic,
                    EncryptedConnectionEnum.Encrypted,
                    EncryptionAlgorithmEnum.RSA-OAEP,
                    PrivacyLevelEnum.Private);
    ```

5. Anropa [Uppdatera datakälla](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) för att ange autentiseringsuppgifter.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Konfigurera en ny datakälla för en datagateway

1. Installera den [lokala datagatewayen](https://powerbi.microsoft.com/gateway/) på datorn.

2. Anropa [Hämta gatewayer](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) för att hämta gateway-ID:t och den offentliga nyckeln.

    ```csharp
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First(); // select a gateway
    ```

3. Skapa information om autentiseringsuppgifter som i det föregående scenariot med den offentliga nyckeln för gatewayen som hämtades i steget [Flöde för autentiseringsuppgifter för lokal datakälla som upphört](#expired-on-premises-data source-credentials-flow-on-premises-data-gateway).

4. skapa begärantexten

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
    dataSourceType: "SQL",
    connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
    credentialDetails: credentialDetails,
    dataSourceName: "my sql datasource");
    ```

5. Anropa API:et [Skapa datakälla](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource).

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="troubleshooting"></a>Felsökning

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Ingen gateway och inget ID för datakälla hittades vid anrop för att hämta datakällor

Problemet betyder att datauppsättningen inte är bunden till en gateway. När du skapar en ny datauppsättning skapas en datakälla utan autentiseringsuppgifter automatiskt på användarens molngateway för varje molnanslutning. Denna gateway används för att lagra autentiseringsuppgifterna för molnanslutningar.

När du har skapat datauppsättningen görs en automatisk bindning mellan datauppsättningen och en lämplig gateway, som innehåller matchande datakällor för alla anslutningar. Om det inte finns någon sådan gateway eller flera lämpliga gatewayer misslyckas den automatiska bindningen.

Skapa eventuella lokala datakällor som saknas och bind datauppsättningen till en gateway manuellt med hjälp av [Bind till gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway).

Om du vill identifiera gatewayer som kan bindas använder du [Identifiera gatewayer](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways).
