---
title: Rapportdata i Power BI Report Builder
description: Det första steget när du designar en rapport i Power BI Report Builder är att skapa datakällor och datamängder som representerar underliggande rapportdata.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 06/06/2019
ms.openlocfilehash: f8f7d3b43cfc2d5a51b686598c1657ec21b44130
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527279"
---
# <a name="report-data-in-power-bi-report-builder"></a>Rapportdata i Power BI Report Builder

Rapportdata kan komma från flera datakällor i din organisation. Det första steget när du designar en Power BI Report Builder-rapport är att skapa datakällor och datamängder som representerar underliggande rapportdata. Varje datakälla innehåller information om dataanslutning. Varje datamängd innehåller ett frågekommando som definierar den uppsättning fält som ska användas som data från en datakälla. Du kan visualisera data från varje datamängd genom att lägga till ett dataområde, till exempel en tabell, en matris, ett diagram eller en översikt. När rapporten bearbetas körs frågorna på datakällan, och varje dataområde expanderas efter behov för att visa frågeresultatet för datamängden.  

Lär dig hur du [skapar en inbäddad datakälla för sidnumrerade rapporter i Power BI Report Builder](paginated-reports-embedded-data-source.md).


##  <a name="BkMk_ReportDataTerms"></a> Termer  
  
- **Dataanslutning.** Kallas även för *datakälla*. En dataanslutning innehåller ett namn och anslutningsegenskaper som är beroende av anslutningstypen. Dataanslutningar innehåller inga autentiseringsuppgifter. Dataanslutningar anger inte vilka data som ska hämtas från den externa datakällan. Det gör du i stället genom att ange en fråga när du skapar en datamängd.  
  
- **Anslutningssträng.** En anslutningssträng är en strängversion av de anslutningsegenskaper som behövs för anslutning till en datakälla. Anslutningsegenskaper varierar beroende på typen av dataanslutning.  
  
- **Inbäddad datakälla.** Kallas även *rapportspecifik datakälla*. En datakälla som definieras i en rapport och endast används av just den rapporten.  
  
- **Autentiseringsuppgifter.** Autentiseringsuppgifter är den autentiseringsinformation som måste anges för att du ska få tillgång till externa data.  
  
##  <a name="BkMk_ReportDataTips"></a> Tips för att specificera rapportdata

 Använd följande information för att utforma din strategi för rapportdata.  
  
- **Filtrera data** Rapportdata kan filtreras i frågan eller i rapporten. Du kan använda datamängder och frågevariabler för att skapa sammanhängande parametrar och ge användare möjligheten att precisera valen från tusentals alternativ till ett mer hanterbart antal. Du kan filtrera data i en tabell eller ett diagram baserat på parametervärden eller andra värden som du anger.  
  
- **Parametrar** Frågekommandon för datamängder som omfattar frågevariabler skapar automatiskt matchande rapportparametrar. Du kan även skapa parametrar manuellt. När du tittar på en rapport visar rapportverktygsfältet parametrarna. Användarna kan välja värden för att kontrollera rapportdata eller utseende på rapporten. För att anpassa rapportdata mot specifika målgrupper kan du skapa uppsättningar med rapportparametrar med olika standardvärden som är länkade till samma rapportdefinition eller använda det inbyggda fältet **UserID**. 
  
- **Gruppera och aggregera data** Rapportdata kan grupperas och aggregeras i frågan eller i rapporten. Om du aggregerar värden i frågan kan du fortsätta att kombinera värdena i rapporten inom begränsningarna för vad som är beskrivande.  
  
- **Sortera data** Rapportdata kan sorteras i frågan eller i rapporten. I tabeller kan du även lägga till en interaktiv sorteringsknapp så att användare kan kontrollera sorteringsordningen.  
  
- **Uttrycksbaserade data** Eftersom de flesta rapportegenskaper kan vara uttrycksbaserade, och uttryck kan innehålla referenser till datamängdsfält och rapportparametrar, kan du skriva kraftfulla uttryck för att kontrollera rapportdata och utseende. Du ge användare möjligheten att kontrollera de data som visas genom att definiera parametrar.  
  
- **Visa data från en datamängd** Data från en datamängd visas vanligtvis i ett eller flera dataområden, till exempel en tabell och ett diagram.  
  
- **Visa data från flera datamängder** Du kan skriva uttryck i ett dataområde baserat på en datamängd som söker efter värden eller aggregeringar i andra datamängder. Du kan inkludera underrapporter i en tabell baserat på en datamängd för att visa data från en annan datakälla.  
  
 Använd följande listan för att definiera datakällor för en rapport.  
  
- Förstå arkitekturen för programvarudatalager för organisationen och potentiella problem som kan uppstå från datatyper. Förstå hur datatillägg och databehandlingstillägg kan påverka frågeresultat. Datatyper skiljer sig åt mellan den datakälla, de dataleverantörer och de datatyper som lagras i rapportdefinitionsfilen (.rdl).  
  
- Datakällor och datamängder skapas i en rapport och publiceras till Power BI-tjänsten. När de har publicerats kan du konfigurera autentiseringsuppgifter direkt i Power BI-tjänsten eller i din företagsgateway. 

## <a name="next-steps"></a>Nästa steg

- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
- [Guide till datahämtning i sidnumrerade rapporter](guidance/report-paginated-data-retrieval.md)
