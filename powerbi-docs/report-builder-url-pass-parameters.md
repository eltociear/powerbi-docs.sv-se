---
title: Skicka en rapportparameter i en URL för en sidnumrerad rapport – Power BI Report Builder
description: I det här avsnittet beskrivs hur du skickar rapportparametrar till en rapport genom att inkludera dem i en sidnumrerad rapport-URL.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: add2f82594d83d1e1f177bfad5045c2e0a34ba84
ms.sourcegitcommit: b53a6f5575f5f8bc443ecdca9c72525ce123518f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70189379"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Skicka en rapportparameter i en URL för en sidnumrerad rapport i Power BI 

Du kan skicka rapportparametrar till en rapport genom att inkludera dem i en sidnumrerad rapport-URL. Alla frågeparametrar kan ha motsvarande rapportparametrar. Därför skickar du en frågeparameter till en rapport genom att skicka motsvarande rapportparameter. Du måste använda prefix för parameternamnet med `rp:` för att Power BI ska kunna identifiera det i URL:en. 

Rapportparametrar är skiftlägeskänsliga och använder följande specialtecken: 

- Ett blanksteg i parameterdelen av URL:en ersätts med ett plustecken (+).  Till exempel: 

    ```rp:Holiday=Christmas+Day```

- Ett semikolon i valfri del av strängen ersätts med tecknen `%3A`.

Webbläsare ska automatiskt utföra rätt URL-kodning. Du behöver inte koda något av tecknen manuellt. 

Om du vill ange en rapportparameter i en URL, använder du följande syntax: 

```
rp:parameter=value
```

Om du till exempel vill specificera två parametrar, ”Säljare” och ”Tillstånd”, som definieras i en rapport på Min arbetsyta, använder du följande URL: 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Om du vill ange samma två parametrar som definierats i en rapport i en app använder du följande URL: 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

Om du vill skicka ett null-värde för en parameter använder du följande syntax: 

```
parameter:isnull=true
```

Till exempel:

```
rp:SalesOrderNumber:isnull=true
```

Om du vill skicka ett booleskt värde använder du 0 som falskt och 1 som sant. Om du vill skicka ett flyttalsvärde inkluderar du serverspråkets decimalavgränsare.

> [!NOTE]
> Om din rapport innehåller en rapportparameter som har ett standardvärde, och värdet för egenskapen  **Prompt** är **falskt** (dvs. egenskapen **Fråga användaren** har inte valts i Rapporthanteraren), kan du inte skicka ett värde för den aktuella rapportparametern inuti en URL. Det här ger administratörer möjlighet att förhindra att slutanvändare lägger till eller ändrar värdena för vissa rapportparametrar.

## <a name="additional-examples"></a>Ytterligare exempel 

Följande URL-exempel innehåller en flervärdesparameter som kallas ”Säljare”. Formatet för en parameter med flera värden är att upprepa parameternamnet för varje värde. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

I följande URL-exempel skickas en parameter till SellStartDate med värdet ”7/1/2005” för en rapportserver för enhetligt läge.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Nästa steg

- [URL-parametrar i sidnumrerade rapporter i Power BI](report-builder-url-parameters.md)
- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)