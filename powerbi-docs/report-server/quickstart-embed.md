---
title: "Bädda in en rapport med iFrame"
description: "Det går mycket snabbt att installera Power BI Reports Server. Att hämta, installera eller konfigurera tar bara några minuter."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/09/2017
ms.author: asaxton
ms.openlocfilehash: df22a7ed0772979d164a9afae18f4931310ec4a1
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="quickstart-embed-a-power-bi-report-using-an-iframe-and-url-parameters"></a>Snabbstart: Bädda in en Power BI-rapport med iFrame och URL-parametrar

Du kan bädda in valfri rapport med iFrame i ditt program. 

## <a name="url-parameter"></a>URL-parameter

Du kan lägga till en frågesträngsparameter i form av `?rs:Embed=true` för valfri URL till en rapport.

Exempel:

```
http://myserver/reports/powerbi/Sales?rs:embed=true
```

Detta fungerar på alla rapporttyper i Power BI-rapportservern.

## <a name="iframe"></a>iFrame

När du har din URL kan du skapa en iFrame på en webbsida som värd för rapporten.

Exempel:

```
<iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
```

## <a name="url-filter"></a>URL-filter

Du kan lägga till en frågesträngsparameter till URL:en för att filtrera de data som returneras i Power BI-rapporten.

Syntaxen är enkel. Börja med rapport-URL:en, lägg till ett frågetecken och sedan den här filtersyntaxen.

URL?filter=***Tabell***/***Fält*** eq '***värde***'

Tänk på följande:

- Namnen **Tabell** och **Fält** är skiftlägeskänsliga, men **värde** är det inte.
- Du kan filtrera en rapport med fält som är dolda från rapportvyn.
- **Värdet** måste omges med enkla citattecken.
- Fälttypen måste vara en sträng.
- Tabell- och fältnamnen får inte innehålla några blanksteg.

###  <a name="example-filter-on-a-field"></a>Exempel: Filtrera i ett fält

Ta som exempel[Exempel på detaljhandelsanalys](../sample-datasets.md). Låt oss säga att detta är URL:en till rapporten på rapportservern i en mapp med namnet ”power bi”:

```
https://report-server/reports/power-bi/Retail-Analysis-Sample
```

Du kan se att kartvisualiseringen i exemplet på detaljhandelsanalys visar butiker i North Carolina och andra stater.

![Kartvisualisering av exemplet på detaljhandelsanalys](media/quickstart-embed/report-server-retail-analysis-sample-map.png)

*NC* är det värde för North Carolina som lagras i fältet **Område** i tabellen **Butik**. För att filtrera rapporten för att endast visa data för butiker i North Carolina, lägger du till följande till URL:en:

?filter=Butik/Område eq 'NC'

Nu filtreras rapporten för North Carolina; alla visualiseringar på rapportsidan visar endast data för North Carolina.

![Filtrerade visualiseringar för exemplet på detaljhandelsanalys](media/quickstart-embed/report-server-retail-analysis-sample-filtered-map.png)

### <a name="create-a-dax-formula-to-filter-on-multiple-values"></a>Skapa en DAX-formel för att filtrera på flera värden

Ett annat sätt att filtrera på flera fält är att skapa en beräknad kolumn i Power BI Desktop som sammanfogar två fält till ett enda värde. Sedan kan du filtrera efter det värdet.

Exemplet på detaljhandelsanalys har till exempel två fält: Område och Kedja. I Power BI Desktop kan du [skapa en beräknad kolumn](../desktop-tutorial-create-calculated-columns.md) (Fält) som kallas OmrådeKedja. Kom ihåg att namnet i **Fält** inte får innehålla blanksteg. Här är DAX-formeln för kolumnen.

OmrådeKedja = [Område] & "-" & [Kedja]

Publicera rapporten på Power BI-rapportservern och använd sedan URL-frågesträngen för att filtrera och visa data för endast Lindseys butiker i NC.

```
https://report-server/reports/power-bi/Retail-Analysis-Sample?filter=Store/TerritoryChain eq 'NC-Lindseys'

```

## <a name="next-steps"></a>Nästa steg

[Snabbstart: Skapa en Power BI-rapport för Power BI-rapportservern](quickstart-create-powerbi-report.md)  
[Snabbstart: Skapa en sidnumrerad rapport för Power BI-rapportservern](quickstart-create-paginated-report.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)