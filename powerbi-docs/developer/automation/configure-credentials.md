---
title: Konfigurera autentiseringsuppgifter programmässigt för Power BI
description: Så här konfigurerar du autentiseringsuppgifter programmässigt när du automatiserar Power BI
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/23/2020
ms.openlocfilehash: ed35775ac077be7c45807b950530e4e1277d5ac3
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85355017"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>Konfigurera autentiseringsuppgifter programmässigt för Power BI

Följ stegen i den här artikeln för att konfigurera autentiseringsuppgifter programmässigt för Power BI.

>[!NOTE]
>* Den anropande användaren måste vara en datauppsättningsägare eller en gatewayadministratör. Du kan även använda [tjänstens huvudnamn](../embedded/embed-service-principal-certificate.md). Tjänstens huvudnamn kan till exempel vara datauppsättningens ägare.
>* Molndatakällor och deras motsvarande autentiseringsuppgifter hanteras på användarnivå.

## <a name="update-credentials-flow-for-data-sources"></a>Uppdatera ett flöde för autentiseringsuppgifter för datakällor

1. Anropa [Hämta datakällor](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasourcesingroup) för att identifiera datakällorna i datauppsättningen. I svarstexten för varje datakälla finns typ, anslutningsinformation, gateway och ID för datakälla.

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. Skapa en sträng för autentiseringsuppgifter enligt [exemplen för att uppdatera datakälla](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) beroende på typ av autentiseringsuppgifter.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

2. Anropa [Hämta gateway](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) för att hämta den offentliga nyckeln för gatewayen.

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

3. Kryptera autentiseringsuppgifterna.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    Kryptera autentiseringsuppgifterna med den offentliga nyckeln för gatewayen från steg 2. Olika gatewayversioner kan ha olika stora offentliga nycklar. Se följande exempel i SDK-koden, som är tillgängliga från [PowerBI-CSharp GitHub-lagringsplatsen](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions):
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

4. Skapa information om autentiseringsuppgifter med krypterade autentiseringsuppgifter.

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    Använd klassen AssymetricKeyEncriptor med den offentliga nyckel som hämtades i **steg 3**.

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

5. Anropa [Uppdatera datakälla](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) för att ange autentiseringsuppgifter.

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>Konfigurera en ny datakälla för en datagateway

1. Installera den [lokala datagatewayen](https://powerbi.microsoft.com/gateway/) på datorn.

2. Anropa [Hämta gatewayer](https://docs.microsoft.com/rest/api/power-bi/gateways/getgateways) för att hämta gateway-ID:t och den offentliga nyckeln.

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. Skapa information om autentiseringsuppgifter som beskrivs i steget [uppdatera flödet t för autentiseringsuppgifter för datakällor](#update-credentials-flow-for-data-sources) med samma offentliga gateway-nyckel som hämtades i **steg 2**.

4. Skapa begärandetexten.

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

## <a name="credential-types"></a>Typer av autentiseringsuppgifter

När du anropar [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Skapa datakälla) eller [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Uppdatera datakälla) under en **lokal företagsgateway** med [Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/), måste värdet för autentiseringsuppgifter krypteras med gatewayens offentliga nyckel.

>[!NOTE]
>.NET SDK v3 kan också köra de .NET SDK v2-exempel som anges nedan.

### <a name="windows-and-basic-credentials"></a>Windows- och grundläggande autentiseringsuppgifter

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>Nyckelautentiseringsuppgifter

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**OAuth2**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**Anonyma**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>Felsökning

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>Ingen gateway och inget ID för datakälla hittades vid anrop för att hämta datakällor

Problemet betyder att datauppsättningen inte är bunden till en gateway. När du skapar en ny datauppsättning skapas en datakälla utan autentiseringsuppgifter automatiskt på användarens molngateway för varje molnanslutning. Denna gateway används för att lagra autentiseringsuppgifterna för molnanslutningar.

När du har skapat datauppsättningen skapas en automatisk bindning mellan datauppsättningen och en lämplig gateway, som innehåller matchande datakällor för alla anslutningar. Om det inte finns någon sådan gateway eller flera lämpliga gatewayer misslyckas den automatiska bindningen.

Om du använder lokala datauppsättningar skapar du de lokala datakällor som saknas och binder datauppsättningen till en gateway manuellt med hjälp av [Bind till gateway](https://docs.microsoft.com/rest/api/power-bi/datasets/bindtogateway).

Om du vill identifiera gatewayer som kan bindas använder du [Identifiera gatewayer](https://docs.microsoft.com/rest/api/power-bi/datasets/discovergateways).