---
title: Visuell KPI-information
description: skapa KPI i Power BI-tjänsten och Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: bb1ebf08c7ffb7a18cc0dd273c767c082f89f1aa
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/12/2018
ms.locfileid: "44744804"
---
# <a name="kpi-visuals"></a>Visuell KPI-information
En KPI (Key Performance Indicator) är en visuell ledtråd som kommunicerar de framsteg som gjorts mot ett mätbart mål. Mer information om KPI:er finns i [Microsoft Developer Network](https://msdn.microsoft.com/library/hh272050).

## <a name="when-to-use-a-kpi"></a>När du ska använda KPI:er
KPI:er är ett bra alternativ

* för att mäta framsteg (Vad ligger jag före eller efter med?)
* för att mäta avståndet till ett mål (Hur långt före eller efter ligger jag?)   

## <a name="kpi-visual-requirements"></a>Krav för visuella KPI-objekt
En KPI (Key Performance Indicator) baseras på ett visst mått och är utformad för att hjälpa dig att utvärdera aktuellt värde och status för ett mått jämfört med ett definierat mål. Därför kräver ett visuellt KPI-objekt ett *grundläggande* mått som utvärderas mot ett värde och ett *målmått* eller -värde samt ett tröskelvärde eller ett mål.

> [!NOTE]
> För närvarande måste en KPI-datauppsättning innehålla målvärden för en KPI. Om din datauppsättning inte innehåller något, kan du skapa mål genom att lägga till ett Excel-blad med mål till din datamodell eller PBIX-fil.
> 
> 

## <a name="how-to-create-a-kpi"></a>Så här skapar du en KPI
Om du vill följa med så loggar du in på Power BI-tjänsten och väljer **Hämta data > Exempel > Exempel på detaljhandelsanalys**. Vi ska skapa en KPI som mäter de framsteg som vi har gjort mot ett försäljningsmål.

Du kan också titta på när Will visar hur du skapar ett enskilt visuellt måttobjekt: måttdiagram, kort och KPI:er.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

1. Öppna rapporten i [Redigeringsvyn](../service-reading-view-and-editing-view.md) och [lägg till en ny sida](../power-bi-report-add-page.md).    
2. Välj **Försäljning > Total Units This Year (Totalt antal enheter i år)**.  Det här är indikatorn.
3. Lägg till **Tid > Månad**.  Detta representerar trenden.
4. VIKTIGT: Sortera diagrammet efter **Månad**. När du har konverterat visualiseringen till en KPI, går det inte att sortera.

    ![](media/power-bi-visualization-kpi/power-bi-sort-by-month.png)
5. Konvertera det visuella objektet till en KPI genom att välja KPI-ikonen i visualiseringsfönstret.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi-icon.png)
6. Lägg till ett mål. Lägg till förra årets försäljning som målet. Dra **Total Units Last Year (Totalt antal enheter förra året)** till fältet **Målsättningar**.
   
    ![](media/power-bi-visualization-kpi/power-bi-kpi.png)
7. Du kan som alternativ formatera KPI:n genom att välja färgrollerikonen för att öppna panelen Formatering.
   
   * **Indikator** – styr indikatorns visningsenheter och decimalplaceringar.
   * **Trendaxel** – när denna är **På**, visas trendaxeln som bakgrund till det visuella KPI-objektet.  
   * **Mål** – när detta är inställt till **På**, visar det visuella objektet målet och avståndet från målet i procent.
   * **Färgkodning > Riktning** – vissa KPI:er anses *bättre* för högre värden och vissa anses *bättre* för lägre värden. Intäkter kontra väntetid till exempel. Vanligtvis är ett högre värde för intäkter bättre jämfört med ett högre värde för väntetid. Välj **högre är bättre** och du kan även ändra färginställningarna.

1. När du har KPI:n som du vill ha den, [fäster du den på en instrumentpanel](../service-dashboard-pin-tile-from-report.md).

KPI:er finns även tillgängliga på dina mobila enheter – så att du kan hålla dig ansluten till din verksamhet när som helst.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
* Om din KPI inte ser ut som den på bilden ovan, kan det bero på att du behöver sortera efter månad. Eftersom KPI:er saknar sorteringsalternativ, måste du sortera efter månad *innan* du konverterar visualiseringen till en KPI.

## <a name="next-steps"></a>Nästa steg

[Visualiseringar i Power BI-rapporter](power-bi-report-visualizations.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

