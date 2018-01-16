---
title: Interagera med en ArcGIS-karta som har delats med dig
description: "Använda en ArcGis-karta i läsvyn "
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: power bi, service, desktop, mobile
featuredvideoid: 
qualityfocus: monitoring
qualitydate: 06/23/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/08/2018
ms.author: mihart
ms.openlocfilehash: 6d2c14de83fcea1e9067fd3868b7559c3becce14
ms.sourcegitcommit: 804ee18b4c892b7dcbd7d7d5d987b16ef16fc2bb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2018
---
# <a name="interacting-with-arcgis-maps-in-power-bi"></a>Interagera med ArcGIS-kartor i Power BI
Det här avsnittet skrivs utifrån perspektivet för en person som *använder* en ArcGIS-karta i Power BI-tjänsten, Desktop eller i en mobil lösning. När en skapare har delat en ArcGIS-karta med dig, finns det många sätt att interagera med den.  Mer information om hur du skapar en ArcGIS-karta finns i [självstudierna om ArcGIS-kartor från Esri](power-bi-visualization-arcgis.md).

Kombinationen av ArcGIS-kartor och Power BI tar mappning längre än till bara presentation av punkter på en karta – helt enkelt till en helt ny nivå. De tillgängliga alternativen för grundläggande kartor, platstyper, teman, symbolformat och referensskikt skapar fantastiska informativa kartvisualiseringar. Kombinationen av redigerbara dataskikt (som insamlade data) på en karta med spatial analys ger en bättre förståelse av dina data i visualiseringen.

> [!TIP]
> GIS står för Geographic Information Science.
> 
> 

Det exempel som vi använder är samma ArcGIS-karta som skapades i [självstudierna om ArcGIS-kartor från Esri](power-bi-visualization-arcgis.md). Den tittar på förra årets försäljning per stad och använder en grundläggande gatukarta, bubbelsymboler för att representera storlek och ett referensskikt för hushållens genomsnittliga inkomst. Kartan innehåller tre stift och en körtidsradie (i lila).

![](media/power-bi-visualizations-arcgis/power-bi-arcgis-esri-new.png)

> [!TIP]
> Besök [Esris sida om Power BI](https://www.esri.com/powerbi) för att visa de många exemplen eller läsa kundutlåtanden. Gå sedan till Esris [startsida för att komma igång med ArcGIS Maps för Power BI](https://doc.arcgis.com/en/maps-for-powerbi/get-started/about-maps-for-power-bi.htm).
> 
> 

<br/>

## <a name="user-consent"></a>Användargodkännande
Första gången en kollega delar en ArcGIS-karta med dig, visar Power BI en prompt. ArcGIS Maps för Power BI tillhandahålls av [Esri](https://www.esri.com) och din användning av ArcGIS Maps för Power BI är föremål för Esris villkor och sekretesspolicy. Power BI-användare som vill använda de visuella objekten i ArcGIS Maps för Power BI måste ge sitt godkännande i dialogrutan.

## <a name="selection-tools"></a>Valverktyg
Du kan välja tre lägen i ArcGIS Maps för Power BI. Du kan välja högst 250 datapunkter i taget.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-tools2.png)

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-single2.png) Välj enskilda datapunkter.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-marquee2.png) Ritar en rektangel på kartan och väljer de inneslutna datapunkterna. Håll ned CTRL om du vill välja fler än ett rektangulärt område.

![](media/power-bi-visualizations-arcgis/power-bi-esri-selection-reference-layer2.png) Tillåter att gränser eller polygoner inom referensskikt kan användas för att markera inneslutna datapunkter.

<br/>

## <a name="interacting-with-an-arcgis-map"></a>Interagera med en ArcGIS-karta
Vilka funktioner som är tillgängliga beror på om du är *skaparen* (personen som gjort kartan) eller *konsumenten* (någon har delat en ArcGIS-karta med dig). Om du interagerar med en ArcGIS-karta som konsument (det vill säga i [Läsvyn](service-reading-view-and-editing-view.md)), kan du utföra följande åtgärder.

* Som med andra visualiseringstyper kan du [fästa kartan på instrumentpaneler](service-dashboard-pin-tile-from-report.md), [visa](service-reports-show-data.md) och/eller [exportera underliggande data](power-bi-visualization-export-data.md) och visa den i [Fokusläge](service-focus-mode.md) och [Helskärm](service-fullscreen-mode.md).    
* Expandera panelen **Filter** för att utforska kartan med hjälp av filter. När du stänger rapporten sparas inte filtren som du använde.    
    ![](media/power-bi-visualizations-arcgis/power-bi-filter-newer.png)  
* Om kartan har ett referensskikt kan du välja platser där du vill visa detaljer i en knappbeskrivning. Här har vi valt Adams County för att visa data från referensskiktet för den genomsnittliga hushållsinkomsten som skaparen har lagts till i kartan.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-reference-layer.png)  
  
    I det här fallet få vi också ett diagram. Välj en stapel i diagrammet för att få mer information om dina data. Här ser vi att 79 hushåll i Adams County tjänar 200 000 dollar eller mer.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-tooltip-chart.png)
  
    Välj pilen för att visa alla ytterligare diagram.
* Hovra över den grundläggande kartans platssymboler för att visa information i en knappbeskrivning.     
  ![](media/power-bi-visualizations-arcgis/power-bi-arcgis-hover.png)
  
  > [!TIP]
  > Du kan behöva zooma in för att välja en viss plats.  Annars kan det hända att Power BI, om det finns överlappande platser, kan visa dig mer än en knappbeskrivning i taget. Välj pilarna för att flytta mellan knappbeskrivningarna.
  > 
  > ![](media/power-bi-visualizations-arcgis/power-bi-3-screens.png)
  > 
  > 
* Om skaparen har lagt till ett informationsgrafikskikt i ArcGIS-kartan, visas ytterligare data i det övre högra hörnet på kartan.  Här lade till exempel kartskaparen till ”barn under 14”.
  
    ![](media/power-bi-visualizations-arcgis/power-bi-demographics.png)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
ArcGIS Maps för Power BI finns tillgängligt i följande tjänster och appar:

<table>
<tr><th>Tjänst/app</th><th>Tillgängligt</th></tr>
<tr>
<td>Power BI Desktop</td>
<td>Ja</td>
</tr>
<tr>
<td>Power BI-tjänst (PowerBI.com)</td>
<td>Ja</td>
</tr>
<tr>
<td>Power BI Mobile-appar</td>
<td>Ja</td>
</tr>
<tr>
<td>Power BI Publicera på webben</td>
<td>Nej</td>
</tr>
<tr>
<td>Power BI Embedded</td>
<td>Nej</td>
</tr>
<tr>
<td>Power BI-tjänstinbäddning (PowerBI.com)</td>
<td>Nej</td>
</tr>
</table>

**ArcGIS-kartan visas inte**    
I tjänster eller program där ArcGIS Maps för Power BI inte är tillgängligt, visas visualiseringen som ett tomt visuellt objekt med Power BI-logotypen.

**Jag ser inte alla mina adresser på kartan**    
Vid geokodning av gatuadresser, geokodas enbart de första 1 500 adresserna. Geokodning av platsnamn eller länder omfattas inte av gränsen på 1 500 adresser.

**Kostar det något att använda ArcGIS Maps för Power BI?**

ArcGIS Maps för Power BI är tillgängligt för alla Power BI-användare utan extra kostnad. Det är en komponent som tillhandahålls av **Esri** och din användning är föremål för de villkor och den sekretesspolicy som tillhandahålls av **Esri**, enligt vad som nämnts tidigare i den här artikeln.

**Jag får ett felmeddelande om att mitt cacheminne är fullt**

Detta är ett programfel som vi håller på att åtgärda.  Välj under tiden länken som visas i felmeddelandet för anvisningar om hur du rensar ditt Power BI-cacheminne.

**Kan jag visa mina ArcGIS-kartor offline?**

Nej, Power BI behöver nätverksanslutning för att visa kartor.

## <a name="next-steps"></a>Nästa steg
Få hjälp: **Esri** tillhandahåller [omfattande dokumentation](https://go.microsoft.com/fwlink/?LinkID=828772) om funktionsuppsättningen i **ArcGIS Maps för Power BI**.

Du kan ställa frågor, hitta den senaste informationen, rapportera problem och få svar i Power BI-[communityns tråd om **ArcGIS Maps för Power BI**](https://go.microsoft.com/fwlink/?LinkID=828771).

Om du har förslag på förbättringar får du gärna skicka dem till [Power BI:s idélista](https://ideas.powerbi.com).

[Produktsida för ArcGIS Maps för Power BI](https://www.esri.com/powerbi)

