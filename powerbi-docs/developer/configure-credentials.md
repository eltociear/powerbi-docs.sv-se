---
title: Konfigurera autentiseringsuppgifter programmässigt för Power BI
description: Konfigurera autentiseringsuppgifter programmässigt för Power BI för automatisering
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: 222edd901409fa71d98308f27407838d54564834
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836598"
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

3. Kryptera autentiseringsuppgifterna med den offentliga nyckeln för gatewayen. Olika gatewayversioner kan ha olika stora offentliga nycklar.
    
    Titta på exemplet i SDK-koden som är tillgänglig från GitHub-lagringsplatsen för PowerBI-CSharp, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)

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