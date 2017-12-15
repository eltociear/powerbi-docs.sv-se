---
title: "Lägg till Power BI-rapportparametrarna med hjälp av webbadressen"
description: "Filtrera en rapport med hjälp av URL:en för frågesträngparametrar – du kan även filtrera på mer än ett fält."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/25/2017
ms.author: mihart
ms.openlocfilehash: 6858f85cb08c493f7a73dc888a4bb21f66c5f217
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>Filtrera en rapport med frågesträngparametrar i URL:en
När du öppnar en rapport i Power BI-tjänsten har varje sida i rapporten en egen unik URL. Du kan använda filterfönstret på rapportarbetsytan om du vill filtrera rapportsidan.  Eller så kan du lägga till frågesträngparametrar i URL:en för att filtrera rapporten. Du kanske har en rapport som du vill visa dina kolleger men du vill filtrera den först åt dem. Ett sätt att göra detta på är att börja med standard-URL:en för rapporten, lägga till filterparametrar och sedan skicka dem hela URL:en med e-post.

![](media/service-url-filters/power-bi-report2.png)

<iframe width="640" height="360" src="https://www.youtube.com/embed/WQFtN8nvM4A?list=PLv2BtOtLblH3YE_Ycas5B1GtcoFfJXavO&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="query-string-parameter-syntax-for-filtering"></a>Frågesträngparameterns syntax för filtrering
Syntaxen är rätt enkel. Börja med rapport-URL:en, lägg till ett frågetecken och sedan filtersyntaxen.

URL?filter=***Tabell***/***Fält*** eq '***värde***'

![](media/service-url-filters/power-bi-filter-urls7b.png)

* **Tabell** och **Fält** är skiftlägeskänsliga, men **värde** är det inte.
* Fält som är dolda från rapportvyn kan fortfarande filtreras.
* **Värdet** måste omges med enkla citattecken.
* Fälttypen måste vara en sträng.
* Tabell- och fältnamnen får inte innehålla några blanksteg.

Om du fortfarande tycker det är förvirrande kan du fortsätta läsa så förklarar vi mer.  

## <a name="filter-on-a-field"></a>Filtrera i ett fält
Vi antar att URL:en till vår rapport är följande.

![](media/service-url-filters/power-bi-filter-urls6.png)

Och vi ser i vår kartvisualisering (ovan) att vi har butiker i North Carolina.

>[!NOTE]
>Det här exemplet är baserat på [Exempel på detaljhandelsanalys](sample-datasets.md).
> 

Filtrera rapporten till att endast visa data för butiker i ”NC” (North Carolina) genom att lägga till följande i URL:en:

?filter=Butik/Område eq 'NC'

![](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>*NC* är ett värde som lagras i fältet **Område** i tabellen **Butik**.
> 
> 

Vår rapport är filtrerad för North Carolina, vilket innebär att alla visualiseringar på rapportsidan endast visar data för North Carolina.

![](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-multiple-fields"></a>Filtrera på flera fält
Du kan också filtrera på flera fält genom att lägga till ytterligare parametrar i URL:en. Nu går vi tillbaka till vår ursprungliga filterparameter.

```
?filter=Store/Territory eq 'NC'
```

Om du vill filtrera på ytterligare fält lägger du till ett `and` och ett till fält i samma format som ovan. Här är ett exempel.

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

<iframe width="640" height="360" src="https://www.youtube.com/embed/0sDGKxOaC8w?showinfo=0" frameborder="0" allowfullscreen></iframe>


### <a name="using-dax-to-filter-on-multiple-values"></a>Använda DAX för att filtrera på flera värden
Ett annat sätt att filtrera på flera fält är genom att skapa en beräknad kolumn som sammanfogar två fält till ett enstaka värde. Sedan kan du filtrera efter det värdet.

Vi har till exempel två fält: Område och Kedja. I Power BI Desktop [skapar du en ny beräknad kolumn](desktop-tutorial-create-calculated-columns.md) (fält) med namnet OmrådeKedja. Kom ihåg att namnet **Fält** inte får innehålla några blanksteg. Här är DAX-formeln för kolumnen.

OmrådeKedja = [Område] & " - " & [Kedja]

Publicera rapporten till Power BI-tjänsten och använd sedan URL-frågesträngen för att enbart filtrera och visa data för Lindseys butiker i NC.

https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Butik/OmrådeKedja eq 'NC–Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>Fästa en panel från en filtrerad rapport
När du har filtrerat rapporten med frågesträngparametrarna kan du fästa visualiseringarna från rapporten på instrumentpanelen. Panelen på instrumentpanelen visar filtrerade data och när du väljer den instrumentpanelen öppnas rapporten som användes för att skapa den.  Emellertid sparas inte filtreringen som du gjorde med hjälp av URL:en i rapporten och när instrumentpanelen är markerad öppnas rapporten i sitt ofiltrerade tillstånd.  Det innebär att data som visas i instrumentpanelen inte matchar de data som visas i rapportvisualiseringen.

Det kan finnas tillfällen när det är användbart, t.ex. när du vill se olika resultat: Filtrerade på instrumentpanelen och ofiltrerade i rapporten.

## <a name="limitations-and-troubleshooting"></a>Begränsningar och felsökning
Det finns några saker som du bör vara medveten om när du använder frågesträngparametrarna.

* Frågesträngfiltrering fungerar inte med URL:er i [Publicera på webben](service-publish-to-web.md).
* Fälttypen måste vara en sträng.
* Tabell- och fältnamnen får inte innehålla några blanksteg.

## <a name="next-steps"></a>Nästa steg
[Fästa en visualisering på en instrumentpanel](service-dashboard-pin-tile-from-report.md)  
[Testa – det är kostnadsfritt!](https://powerbi.com/)

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

