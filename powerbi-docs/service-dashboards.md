---
title: Vad är en instrumentpanel för kunder som använder Power BI-tjänsten?
description: Instrumentpaneler är en nyckelfunktion i Power BI-tjänsten.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 09/02/2018
ms.author: maggie
LocalizationGroup: Dashboards
ms.openlocfilehash: 6be3d095ca68cf83ff7a2ba4c7fd02a9340f3474
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2018
ms.locfileid: "48908450"
---
# <a name="dashboards-in-power-bi-service"></a>Instrumentpaneler i Power BI-tjänsten

En ***instrumentpanel*** i Power BI är en enskild sida, ofta kallad en arbetsyta, som använder sig av visualiseringar för att förmedla ett budskap. Eftersom den är begränsad till en sida, innehåller en väl utformad instrumentpanel endast de viktigaste elementen i detta budskap.

![instrumentpanel](media/service-dashboards/power-bi-dashboard2.png)

Instrumentpaneler är en funktion i Power BI-tjänsten och är inte tillgängliga i Power BI Desktop. Instrumentpaneler kan inte skapas i mobila enheter men de kan [visas och delas](mobile-apps-view-dashboard.md).

## <a name="dashboard-creators-and-dashboard-consumers"></a>Skapare av instrumentpaneler och konsumenter av instrumentpaneler
Beroende på din roll skapar du antingen instrumentpaneler för eget bruk eller för att dela med dina kollegor. Läs mer i informationen om **instrumentpaneler för skapare**. Om du tar emot instrumentpaneler från andra. Du vill lära dig att förstå och interagera med instrumentpaneler. I så fall är den här artikeln något för dig!


### <a name="if-you-will-be-receiving-and-consuming-dashboards"></a>Om du ska ta emot och konsumera instrumentpaneler

De visualiseringar som visas på instrumentpanelen kallas för *paneler* och de *fästs* på instrumentpanelen från rapporter av *instrumentpanelsskapare*. Om du är nybörjare på Power BI kan du få en god grund genom att läsa [Grundläggande begrepp i Power BI](service-basic-concepts.md).

> [!IMPORTANT]
> [Power BI Pro](service-free-vs-pro.md) krävs för att visa en delad instrumentpanel.

Visualiseringarna på en instrumentpanel kommer från rapporter och varje rapport baseras på en datauppsättning. Man skulle kunna se på en instrumentpanel som en entré till de underliggande rapporterna och datauppsättningarna. Om du väljer en visualisering tas du till rapporten (och datauppsättningen) som användes för att skapa den.

![diagram som visar relationen mellan instrumentpaneler, rapporter och datauppsättningar](media/service-dashboards/power-bi-diagram.png)



## <a name="advantages-of-dashboards"></a>Fördelarna med instrumentpaneler
Instrumentpaneler är fantastiska för att övervaka affärsverksamheten, för att leta efter svar och för att få en snabb översikt över era viktigaste mått. Visualiseringarna på en instrumentpanel kan komma från en underliggande datauppsättning eller flera, eller från en underliggande rapport eller flera. En instrumentpanel kombinerar lokala och molnlagrade data, vilket ger en samlad vy oavsett var dessa data finns.

En instrumentpanel är inte bara en fin bild, den är i hög grad interaktiv. Panelerna uppdateras när underliggande data ändras.

## <a name="dashboards-versus-reports"></a>Instrumentpaneler kontra rapporter
[Rapporter](service-reports.md) förväxlas ofta med instrumentpaneler, eftersom de också är arbetsytor fulla av visualiseringar. Men det finns några viktiga skillnader för Power BI-användare.

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
* Lär dig mer om [panelerna](service-dashboard-tiles.md) och vad som händer när du väljer en.
* Vill du spåra en enskild panel på instrumentpanelen och får ett e-postmeddelande när den når ett visst tröskelvärde? [Skapa aviseringar för paneler](service-set-data-alerts.md).
* Roa dig med att ställa frågor till instrumentpanelen. Lär dig hur du använder [Power BI:s frågor och svar](power-bi-tutorial-q-and-a.md) för att ställa en fråga om dina data och få ett svar i form av en visualisering.
