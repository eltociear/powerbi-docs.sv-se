---
title: Introduktion till instrumentpaneler för Power BI-designers
description: Instrumentpaneler är en nyckelfunktion i Power BI-tjänsten. De är en enda sida, som ofta kallas för arbetsyta, som har ett budskap via visualiseringar.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 709518924fbb9d83201eb5c070b7a3e93838ec79
ms.sourcegitcommit: 35d763dfc75c229204d36fd8b35c1e860786b707
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52331952"
---
# <a name="intro-to-dashboards-for-power-bi-designers"></a>Introduktion till instrumentpaneler för Power BI-designers

En Power BI-***instrumentpanel*** är en enda sida, som ofta kallas för arbetsyta, som har ett budskap via visualiseringar. Eftersom den är begränsad till en sida, innehåller en väl utformad instrumentpanel endast höjdpunkterna i detta budskap. Läsare kan visa relaterade rapporter för att få information.

![instrumentpanel](media/service-dashboards/power-bi-dashboard2.png)

Instrumentpaneler är en funktion i Power BI-tjänsten. De finns inte tillgängliga i Power BI Desktop. Du kan inte skapa instrumentpaneler på mobila enheter, men du kan [visa och dela](mobile-apps-view-dashboard.md) dem.

## <a name="dashboard-basics"></a>Grunderna i instrumentpanelen 

De visualiseringar som visas i instrumentpanelen kallas *paneler*. Du *fäster* paneler på en instrumentpanel från rapporter. Om du är nybörjare på Power BI kan du få en god grund genom att läsa [Grundläggande begrepp i Power BI](service-basic-concepts.md).

> [!IMPORTANT]
> Du behöver en [Power BI Pro](service-free-vs-pro.md)-licens för att skapa instrumentpaneler.

Visualiseringarna på en instrumentpanel kommer från rapporter och varje rapport baseras på en datamängd. Man skulle kunna se på en instrumentpanel som en entré till de underliggande rapporterna och datamängderna. Om du väljer en visualisering tas du till rapporten (och datamängden) som den är baserad på.

![diagram som visar relationen mellan instrumentpaneler, rapporter och datauppsättningar](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Fördelarna med instrumentpaneler
Instrumentpaneler är fantastiska för att övervaka affärsverksamheten och för att få en snabb översikt över era viktigaste mått. Visualiseringarna på en instrumentpanel kan komma från en underliggande datauppsättning eller flera, eller från en underliggande rapport eller flera. En instrumentpanel kombinerar lokala och molndata, vilket ger en samlad vy oavsett var dessa data finns.

En instrumentpanel är inte bara en fin bild. Den är i hög grad interaktiv. Panelerna uppdateras när underliggande data ändras.

## <a name="dashboards-versus-reports"></a>Instrumentpaneler kontra rapporter
[Rapporter](service-reports.md) och instrumentpaneler kan verka lika eftersom de båda är arbetsytor som är fyllda av visualiseringar. Men det finns några viktiga skillnader.

| **Kapacitet** | **Instrumentpaneler** | **Rapporter** |
| --- | --- | --- |
| Sidor |En sida |En eller flera sidor |
| Datakällor |En eller flera rapporter och en eller flera datauppsättningar per instrumentpanel |En enskild datauppsättning per rapport |
| Tillgängliga i Power BI Desktop |Nej |Ja, ***skapare*** kan skapa och visa rapporter i Desktop |
| Prenumerera |Kan prenumerera på en instrumentpanel |Det går att prenumerera på rapportsidor |
| Filtrering |Det går inte att filtrera eller dela upp |Det finns många olika sätt att filtrera, markera och dela upp |
| Aktuella |Det går att ange en instrumentpanel som din ”aktuella” instrumentpanel |Det går inte att skapa en aktuell rapport |
| Favorit | Kan markera instrumentpaneler som *favoriter* | Kan markera rapporter som *favoriter*
| Ställa in avisering |Tillgänglig för instrumentpaneler i vissa fall |Inte tillgängligt från rapporter |
| Frågor med naturligt språk |Tillgängligt från instrumentpanelen |Inte tillgängligt från rapporter |
| Det går att visa tabeller och fält från den underliggande datauppsättningen |Nej. Det går att exportera data men tabeller och fält visas inte i själva instrumentpanelen. |Ja. Det går att visa datauppsättningens tabeller, fält och värden. |
| Anpassning |Nej |I läsvyn kan du publicera, bädda in, filtrera, exportera, ladda ned som.pbix, visa relaterat innehåll, generera QR-koder, analysera i Excel med mera.  |

## <a name="next-steps"></a>Nästa steg
* Bekanta dig med instrumentpaneler genom att ta en titt på ett av våra [exempel](sample-tutorial-connect-to-the-samples.md).
* Läs om [panelerna på instrumentpanelen](service-dashboard-tiles.md).
* Vill du spåra en enskild panel på instrumentpanelen och får ett e-postmeddelande när den når ett visst tröskelvärde? [Skapa aviseringar för paneler](service-set-data-alerts.md).
* Lär dig hur du använder [Power BI:s frågor och svar](power-bi-tutorial-q-and-a.md) för att ställa en fråga om dina data och få ett svar i form av en visualisering.
