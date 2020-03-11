---
title: Skicka en rapportparameter i en URL för en sidnumrerad rapport – Power BI Report Builder
description: I det här avsnittet beskrivs hur du skickar rapportparametrar till en rapport genom att inkludera dem i en sidnumrerad rapport-URL.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 08/29/2019
ms.openlocfilehash: b8301ca17559b81d4db132fbeaa0955ce68a4c6e
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78922538"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Skicka en rapportparameter i en URL för en sidnumrerad rapport i Power BI 

Du kan skicka rapportparametrar till en rapport genom att inkludera dem i en sidnumrerad rapport-URL. Alla frågeparametrar kan ha motsvarande rapportparametrar. Därför skickar du en frågeparameter till en rapport genom att skicka motsvarande rapportparameter. Du behöver prefigera parameternamnet med `rp:` för att Power BI ska kunna identifiera det i URL:en. 

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

Om du vill skicka ett booleskt värde använder du 0 för falskt och 1 för sant. Om du vill skicka ett flyttalsvärde inkluderar du serverspråkets decimalavgränsare.

> [!NOTE]
> Om din rapport innehåller en rapportparameter som har ett standardvärde, och värdet för egenskapen **Prompt** är **falskt** (det vill säga egenskapen **Fråga användaren** har inte valts i Rapporthanteraren), kan du inte skicka ett värde för den aktuella rapportparametern inuti en URL. Det här ger administratörer möjlighet att förhindra att slutanvändare lägger till eller ändrar värdena för vissa rapportparametrar.

> Power BI har inte stöd för frågesträngar som är längre än 900 tecken.  Du kan överskrida det här värdet genom att använda adressparametrar för din sidnumrerade rapport.  Det här gäller särskilt om du använder parametrar med flera värden.

## <a name="additional-examples"></a>Ytterligare exempel 

Följande URL-exempel innehåller en flervärdesparameter som kallas ”Säljare”. Formatet för en parameter med flera värden är att upprepa parameternamnet för varje värde. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

I följande URL-exempel skickas en enskild parameter för SellStartDate med värdet ”7/1/2005” för en rapportserver för enhetligt läge.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Nästa steg

- [URL-parametrar i sidnumrerade rapporter i Power BI](report-builder-url-parameters.md)
- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
