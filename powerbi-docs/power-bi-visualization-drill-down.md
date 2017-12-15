---
title: "Öka detaljnivån i en visualisering i Power BI"
description: "Det här dokumentet beskriver hur du ökar detaljnivån i en visualisering i Microsoft Power BI-tjänsten och Power BI Desktop."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: MNAaHw4PxzE
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/18/2017
ms.author: mihart
ms.openlocfilehash: 83c63ee2bed5ae7674223cf2fc3f9241308926e9
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="drill-down-in-a-visualization-in-power-bi"></a>Öka detaljnivån i en visualisering i Power BI
## <a name="drill-down-requires-a-hierarchy"></a>Detaljnivån kräver en hierarki
När en visualisering har en hierarki kan du öka detaljnivån till att visa ytterligare information. Du kan till exempel ha en visualisering som kontrollerar OS-medaljantal enligt en hierarki som består av sport, gren och evenemang. Som standard visar visualiseringen medaljantal enligt sport – gymnastik, skidåkning, vattensport o.s.v. Men eftersom den har en hierarki, skulle val av ett av de visuella elementen (till exempel ett stapel-, linje- eller bubbeldiagram), visa en allt mer detaljerad bild. Välj elementet **vattensporter** för att se data för simning, simhopp och vattenpolo.  Välj elementet **simhopp** för att visa detaljer för trampolin, plattform och synkroniserade simhopp.

Du kan lägga till hierarkier till rapporter som du äger men inte till de som delats med dig.
Är du osäker på vilka Power BI-visualiseringar som innehåller en hierarki?  Hovra över en visualisering och om du ser dessa kontroller för ökad detaljnivå i de övre hörnen, har din visualiseringen en hierarki.

![](media/power-bi-visualization-drill-down/power-bi-drill-icon4.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  ![](media/power-bi-visualization-drill-down/power-bi-drill-icon3.png)
![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png) ![](media/power-bi-visualization-drill-down/power-bi-drill-icon6.png)  

Datum är en unik typ av hierarki. När du lägger till ett datumfält i en visualisering lägger Power BI automatiskt till en tidshierarki som innehåller år, kvartal, månad och dag. Mer information finns i [Visuella hierarkier och beteende för ökad detaljnivå](guided-learning/visualizations.yml#step-18) eller titta på videon nedan.

  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Om du vill lära dig mer om att skapa hierarkier med hjälp av Power BI Desktop, titta på videon [Hur du skapar och lägger till hierarkier](https://youtu.be/q8WDUAiTGeU)
> 
> 

## <a name="two-methods-to-drill-down"></a>Två metoder för att öka detaljnivån
Det finns två olika sätt att bryta ned (och upp) din visualisering.  Båda beskrivs i den här artikeln. Båda metoderna gör samma sak, så använd den du gillar mest.

> [!NOTE]
> För att följa med, [öppna exemplet för detaljhandelsanalys](sample-datasets.md) i Power BI-tjänsten och skapa ett treemap-diagram som kontrollerar (värdena) **totala enheter detta år** enligt (grupperna) **Område**, **Stad**, **Postnummer** och **Namn**.  
> 
> 

## <a name="method-1-for-drill-down"></a>Metod 1 för ökad detaljnivå
Den här metoden använder de ikoner för ökad detaljnivå som visas de i övre hörnen av själva visualiseringen.

1. I Power BI öppnar du en rapport i [Läsvy](service-report-open-in-reading-view.md) eller [Redigeringsvy](service-reading-view-and-editing-view.md). Ökad detaljnivå kräver en visualisering med en hierarki. 
   
   En hierarki visas i animeringen nedan.  Visualiseringen har en hierarki som består av område, stad, postnummer och stadsnamn. Varje område har en eller flera städer, varje stad har ett eller flera postnummer o.s.v. Visualiseringen visar som standard endast områdesdata, eftersom *Område* visas först i listan.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Om du vill aktivera ökad detaljnivå väljer du pilikonen längst upp till höger på visualiseringen. När ikonen är mörk är ökad detaljnivå aktiverat. Om du inte aktiverar ökad detaljnivå, kommer valet av ett visuellt element (till exempel ett stapel- eller bubbeldiagram) att korsfiltrera diagrammen på sidan.    
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-icon.png)
3. För att öka detaljnivån ***ett fält i taget***, klickar du på ett av elementen i din visualisering. I ett stapeldiagram innebär det att klicka på någon av staplarna och i ett treemap-diagram innebär det att välja något av *bladen*. Observera att rubriken ändras när du ändrar detaljnivån ner och upp igen. I den här animeringen ändras den från ”Totalt antal enheter i år enligt område” till ”totalt antal enheter i år enligt område och stad” till ”Totalt antal enheter i år enligt område, stad och postnummer” till ”totalt antal enheter i år enligt område, stad, postnummer och namn”. Och om du vill öka detaljnivån väljer du ikonen **öka detaljnivån** ![](media/power-bi-visualization-drill-down/power-bi-drill-icon5.png)i det övre vänstra hörnet av visualiseringen enligt nedan.
   
   ![](media/power-bi-visualization-drill-down/drill.gif)
4. För att minska detaljnivån med ***alla fält samtidigt***, väljer du den dubbla pilen i det övre vänstra hörnet av visualiseringen.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillall.png)
5. Om du vill öka detaljnivån igen väljer du uppåtpilen i det övre vänstra hörnet av visualiseringen.
   
   ![](media/power-bi-visualization-drill-down/pbi_drillup2.png)

## <a name="method-2-for-drill-down"></a>Metod 2 för ökad detaljnivå
Den här metoden använder listrutan **Utforska** från den översta menyraden i Power BI.

1. I Power BI öppnar du en rapport i [Läsvy](service-report-open-in-reading-view.md) eller [Redigeringsvy](service-reading-view-and-editing-view.md). Ökad detaljnivå kräver en visualisering med en hierarki. 
   
   En hierarki visas på bilden nedan.  Visualiseringen har en hierarki som består av område, stad, postnummer och stadsnamn. Varje område har en eller flera städer, varje stad har ett eller flera postnummer o.s.v. Visualiseringen visar som standard endast områdesdata, eftersom *Område* visas först i listan.
   
   ![](media/power-bi-visualization-drill-down/power-bi-hierarcy-list.png)
2. Om du vill aktivera ökad detaljnivå, väljer du en visualisering för att göra den aktiv från den övre menyraden i Power BI och väljer **Utforska** > **Ökad detaljnivå**. Ikonen för ökad detaljnivå i det övre högra hörnet av visualiseringen ändras till en svart bakgrund. ![](media/power-bi-visualization-drill-down/power-bi-drill-icon2.png)  
   
   ![](media/power-bi-visualization-drill-down/power-bi-explore2.png)
3. Då aktiverad, kan du öka detaljnivån ett fält i taget genom att välja ett av bladen i treemap-diagrammet. I det här exemplet har jag valt området som heter **NC** för att se det totala antalet sålda enheter i år i North Carolina enligt stad.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drilldown-1.png)
4. Om du vill öka detaljnivån för alla fält samtidigt, väljer du **Utforska** > **Visa nästa nivå**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-show-next-level.png)
5. Om du vill gå tillbaka upp, väljer du **Utforska** > **Minskad detaljnivå**.
   
   ![](media/power-bi-visualization-drill-down/power-bi-drill-up2.png)
6. Om du vill se de data som används för att skapa visualiseringar väljer du **Se data**. Data visas i ett fönster nedanför den visuella informationen. Det här fönstret är kvar när du fortsätter att gå igenom den visuella informationen. Mer information finns i [Visa data som används för att skapa visuell information](service-reports-show-data.md).

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
* Om tillägget av ett datumfält i en visualisering inte skapar en hierarki, kan det bero på att ”datum”-fältet faktiskt inte har sparats som ett datum. Om du äger datauppsättningen, öppna den i vyn *Data* i Power BI Desktop, välj den kolumn som innehåller datum och välj fliken Modellering och ändra **Datatyp** till **Datum** eller **Datum/Tid**. Om rapporten har delats med dig, kontakta ägaren om du vill begära ändringen.  
  
  ![](media/power-bi-visualization-drill-down/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Nästa steg
[Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md)

[Power BI-rapporter](service-reports.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

