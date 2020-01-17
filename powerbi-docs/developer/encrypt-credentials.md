---
title: Kryptera autentiseringsuppgifter
description: Genomgång – Kryptera autentiseringsuppgifter för datakällor för lokal gateway
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 01/08/2020
ms.openlocfilehash: b1fc4a505aa993c606743eefb6e8fb8c0379317d
ms.sourcegitcommit: 4b926ab5f09592680627dca1f0ba016b07a86ec0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75836609"
---
# <a name="encrypt-credentials"></a>Kryptera autentiseringsuppgifter

När du anropar [Create Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/createdatasource) (Skapa datakälla) eller [Update Datasource](https://docs.microsoft.com/rest/api/power-bi/gateways/updatedatasource) (Uppdatera datakälla) under en **lokal företagsgateway** med [Power BI Rest API](https://docs.microsoft.com/rest/api/power-bi/), måste värdet för autentiseringsuppgifter krypteras med gatewayens offentliga nyckel.

Se kodexemplet nedan hur du krypterar autentiseringsuppgifterna i .NET.

Autentiseringsuppgifterna som anges för metoden EncodeCredentials nedan ska vara i något av följande format, beroende på typ av autentiseringsuppgifter:

**Grundläggande/Windows**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

**Nyckel**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

**OAuth2**

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

**Anonyma**

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

**Krypterade**

Kryptera autentiseringsuppgifterna med gatewayens offentliga nyckel. Olika gatewayversioner kan ha olika stora offentliga nycklar.

Titta på exemplet i SDK-koden som är tillgänglig från GitHub-lagringsplatsen för PowerBI-CSharp, [PowerBI-CSharp/sdk/PowerBI.Api/Extensions/V2/](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions/V2).

- [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricKeyEncryptor.cs)
- [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/Asymmetric1024KeyEncryptionHelper.cs)
- [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AsymmetricHigherKeyEncryptionHelper.cs)
- [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/V2/AuthenticatedEncryption.cs)