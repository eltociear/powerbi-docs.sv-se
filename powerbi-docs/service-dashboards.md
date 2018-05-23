---
title: Vad är en Power BI-instrumentpanel?
description: Instrumentpaneler är en nyckelfunktion i Power BI-tjänsten.
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 03/02/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 02a88f04d3c23746da702db043c1992267baf054
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="dashboards-in-power-bi-service"></a>Instrumentpaneler i Power BI-tjänsten

En ***instrumentpanel*** i Power BI är en enskild sida, ofta kallad en arbetsyta, som använder sig av visualiseringar för att förmedla ett budskap. Eftersom den är begränsad till en sida, innehåller en väl utformad instrumentpanel endast de viktigaste elementen i detta budskap.

![instrumentpanel](media/service-dashboards/power-bi-dashboard2.png)

De visualiseringar som visas på instrumentpanelen kallas *paneler* och de *fästs* på instrumentpanelen från rapporter. Om du är nybörjare på Power BI kan du få en god grund genom att läsa [Grundläggande begrepp i Power BI](service-basic-concepts.md).

> [!NOTE]
> Instrumentpaneler är en funktion i Power BI-tjänsten och är inte tillgängliga i Power BI Desktop. Instrumentpaneler kan inte skapas i mobila enheter men de kan [visas och delas](mobile-apps-view-dashboard.md).
> 
> 

Visualiseringarna på en instrumentpanel kommer från rapporter och varje rapport baseras på en datauppsättning. Man skulle kunna se på en instrumentpanel som en entré till de underliggande rapporterna och datauppsättningarna. Om du väljer en visualisering tas du till rapporten (och datauppsättningen) som användes för att skapa den.

![diagram som visar relationen mellan instrumentpaneler, rapporter och datauppsättningar](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Fördelarna med instrumentpaneler
Instrumentpaneler är fantastiska för att övervaka affärsverksamheten, för att leta efter svar och för att få en snabb översikt över era viktigaste mått. Visualiseringarna på en instrumentpanel kan komma från en underliggande datauppsättning eller flera, eller från en underliggande rapport eller flera. En instrumentpanel kombinerar lokala och molnlagrade data, vilket ger en samlad vy oavsett var dessa data finns.

En instrumentpanel är inte bara en fin bild, den är i hög grad interaktiv och anpassningsbar och panelerna uppdateras när underliggande data ändras.

## <a name="dashboards-versus-reports"></a>Instrumentpaneler kontra rapporter
[Rapporter](service-reports.md) förväxlas ofta med instrumentpaneler, eftersom de också är arbetsytor fulla av visualiseringar. Men det finns några viktiga skillnader.

| **Kapacitet** | **Instrumentpaneler** | **Rapporter** |
| --- | --- | --- |
| Sidor |En sida |En eller flera sidor |
| Datakällor |En eller flera rapporter och en eller flera datauppsättningar per instrumentpanel |En enskild datauppsättning per rapport |
| Tillgängliga i Power BI Desktop |Nej |Ja, du kan skapa och visa rapporter i Desktop |
| Fästning |Det går bara att fästa befintliga visualiseringar (paneler) från den aktuella instrumentpanelen till dina övriga instrumentpaneler |Det går att fästa visualiseringar (som paneler) på alla dina instrumentpaneler. Det går att fästa hela rapportsidor på alla dina instrumentpaneler. |
| Prenumerera |Det går inte att prenumerera på en instrumentpanel |Det går att prenumerera på rapportsidor |
| Filtrering |Det går inte att filtrera eller dela upp |Det finns många olika sätt att filtrera, markera och dela upp |
| Ställa in avisering |Det går att skapa e-postaviseringar när vissa villkor uppfylls |Nej |
| Visning av aktuellt objekt |Det går att ange en instrumentpanel som din ”aktuella” instrumentpanel |Det går inte att skapa en aktuell rapport |
| Frågor med naturligt språk |Tillgängligt från instrumentpanelen |Inte tillgängligt från rapporter |
| Det går att ändra visualiseringstyp |Nej. Den fästa visualiseringen på instrumentpanelen uppdateras inte om rapportägaren ändrar visualiseringstyp i rapporten |Ja |
| Det går att visa tabeller och fält från den underliggande datauppsättningen |Nej. Det går att exportera data men tabeller och fält visas inte i själva instrumentpanelen. |Ja. Det går att visa datauppsättningens tabeller, fält och värden. |
| Kan skapa visualiseringar |Det går endast att lägga till widgetar i instrumentpanelen med hjälp av ”Lägg till panel” |Det går att skapa många olika typer av visualiseringar, lägga till anpassade visuella objekt, redigera visualiseringar med mera med Redigera behörigheter |
| Anpassning |Det går att ändra visualiseringarna (panelerna). Det går att flytta och ordna dem, byta storlek, lägga till länkar, byta namn, ta bort och visa dem i helskärmsläge. Men alla data och visuella objekt är skrivskyddade. |I läsvyn kan du publicera, bädda in, filtrera, exportera, hämta som.pbix, visa relaterat innehåll, generera QR-koder, analysera i Excel och annat.  Du kan göra allt det ovanstående och mycket mer i redigeringsvyn. |

## <a name="dashboard-creators-and-dashboard-consumers"></a>Skapare av instrumentpaneler och konsumenter av instrumentpaneler
Beroende på din roll skapar du antingen instrumentpaneler för eget bruk eller för att dela med dina kollegor. Du kanske vill lära dig att skapa och dela instrumentpaneler. Eller kanske är du någon som tar emot instrumentpaneler från andra. Du vill lära dig att förstå och interagera med instrumentpaneler.

Här följer några avsnitt, ordande efter roll, som hjälper dig att komma igång.

Power BI Pro krävs för att både dela en instrumentpanel och visa en delad instrumentpanel.

### <a name="if-you-will-be-creating-and-sharing-dashboards"></a>Om du ska skapa och dela instrumentpaneler
* Använd ett av våra exempel för att [skapa en instrumentpanel från en rapport](service-dashboard-create.md).
* Lär dig mer om [instrumentpanelens paneler](service-dashboard-tiles.md) och de olika sätten för att fästa dem på en instrumentpanel.
* Du kan hjälpa dina instrumentpanelsanvändare genom att skapa instrumentpaneler som [fungerar bra med de naturliga språkfrågorna i Frågor och svar](service-prepare-data-for-q-and-a.md) och med [Quick Insights](service-insights-optimize.md).
* Identifiera de olika sätt som du kan [dela en instrumentpanel med kollegor](service-how-to-collaborate-distribute-dashboards-reports.md).

### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Om du ska ta emot och konsumera instrumentpaneler
* Bekanta dig med instrumentpaneler genom att ta en titt på ett av våra [exempel](sample-tutorial-connect-to-the-samples.md).
* Lär dig mer om [panelerna](service-dashboard-tiles.md) och vad som händer när du väljer en.
* Gillar du inte utseendet på en instrumentpanel?  Du kan [ändra storlek, flytta och byta namn på panelerna](service-dashboard-edit-tile.md).
* Vill du spåra en enskild panel på instrumentpanelen och får ett e-postmeddelande när den når ett visst tröskelvärde? [Skapa aviseringar för paneler](service-set-data-alerts.md).
* Roa dig med att ställa frågor till instrumentpanelen. Lär dig hur du använder [Power BI:s frågor och svar](power-bi-tutorial-q-and-a.md) för att ställa en fråga om dina data och få ett svar i form av en visualisering.

> [!TIP]
> Om du inte hittade det du söker efter här, kan du använda innehållsförteckningen till vänster.
> 
> 

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)  
[Power BI – grundläggande begrepp](service-basic-concepts.md)  
[Power BI Premium – vad är det?](service-premium.md)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

