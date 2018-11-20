---
title: Vad är sidnumrerade rapporter i Power BI Premium? (Förhandsgranskning)
description: Sidnumrerade rapporter är rapporter som kan skrivas ut eller delas. Du kan kontrollera rapportlayouten i detalj. De visar alla data i en tabell, även om tabellen t.ex. sträcker sig över flera sidor.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/08/2018
ms.author: maggies
ms.openlocfilehash: 15ec21a0b86977173c16071980d7527f27db74ef
ms.sourcegitcommit: 5eb0f37f59b5fec15c0caecbbd1f8d688c7f0013
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51297054"
---
# <a name="what-are-paginated-reports-in-power-bi-premium-preview"></a>Vad är sidnumrerade rapporter i Power BI Premium? (Förhandsgranskning)
Sidnumrerade rapporter, som länge varit standardrapportformat i SQL Server Reporting Services, är nu tillgängliga i Power BI-tjänsten. Sidnumrerade rapporter är rapporter som har utformats för att skrivas ut eller delas. De kallas ”sidnumrerade” eftersom de har formaterats för att rymmas på en sida och visa alla data i en tabell även om tabellen t.ex. tar flera sidor i anspråk. Rapporterna kallas ibland ”pixelperfekta” eftersom du kan kontrollera deras sidlayout i minsta detalj. Sidnumrerade rapporter baseras på tekniken för RDL-rapporter i SQL Server Reporting Services. Report Builder är ett fristående verktyg för redigering av sidnumrerade rapporter. 

Sidnumrerade rapporter kan ha många sidor. Rapporten i följande exempel har 563 sidor, där var och en har en exakt utforming med en sida per faktura och upprepande sidhuvuden och sidfötter.

![Sidnumrerad rapport i Power BI-tjänsten](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Du kan förhandsgranska rapporten i Report Builder och sedan publicera den i Power BI-tjänsten http://app.powerbi.com. Du måste ha en Power BI Pro-licens för att kunna publicera en rapport i tjänsten. Du kan publicera och dela sidnumrerade rapporter på Min arbetsyta eller på apparbetsytor, så länge arbetsytan finns i en Power BI Premium-kapacitet. Dessutom måste en Power BI-administratör aktivera sidnumrerade rapporter i Power BI-administratörsportalen. Läs mer om att [konfigurera arbetsbelastningar](service-admin-premium-manage.md#configure-workloads). 

## <a name="create-reports-in-report-builder"></a>Skapa rapporter i Report Builder

Sidnumrerade rapporter har sitt eget designverktyg: Report Builder. Om du har skapat sidnumrerade rapporter för Power BI Report Server eller SQL Server Reporting Services (SSRS) kan du använda samma verktyg och samma version. Sidnumrerade rapporter som du skapar för SSRS 2016 och 2017, eller lokalt för Power BI Report Server, är i själva verket kompatibla med Power BI-tjänsten. Power BI-tjänsten har bakåtkompatibilitet så att du kan flytta dina rapporter framåt och uppgradera alla sidnumrerade rapporter av äldre version. Alla funktioner är inte tillgängliga från början. Mer information finns i [Begränsningar och överväganden](#limitations-and-considerations) i den här artikeln.
     
## <a name="report-from-a-variety-of-data-sources"></a>Rapportera från en mängd olika datakällor

En enskild sidnumrerad rapport kan ha flera olika datakällor. Den har inte, till skillnad från Power BI-rapporter, en underliggande datamodell. För denna första version av sidnumrerade rapporter i Power BI-tjänsten skapar du inbäddade datakällor och datauppsättningar i själva rapporten istället för att ansluta till delade datakällor eller datauppsättningar på en server. Du skapar rapporter i Report Builder på din lokala dator. Om en rapport ansluter till lokala data när du har överfört rapporten till Power BI-tjänsten måste du skapa en gateway och omdirigera dataanslutningen. Här följer de datakällor som du kan ansluta till den första versionen:

- Azure SQL Database och Data Warehouse
- SQL Server via en gateway
- SQL Server Analysis Services via en gateway
 
Fler datakällor kommer under förhandsversionsperioden.

## <a name="design-your-report"></a>Utforma din rapport  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>Skapa sidnumrerade rapporter med matriser, diagram och layouter för fritt format

Skapa tabellrapporter för kolumnbaserade data, matrisrapporter (t.ex. korstabulerings- eller pivottabellrapporter) för sammanfattade data, diagramrapporter för grafiska data och *listrapporter* i fritt format för andra saker, t.ex. fakturor. 
  
Du kan börja med någon av Report Builder-guiderna. Med hjälp av tabell-, matris- och diagramguider lär du dig att skapa en inbäddad datakällsanslutning och en inbäddad datamängd. Sedan skapar du en datamängdsfråga genom att dra och släppa fält, väljer en layout och anpassar din rapport.  
  
Med kartguiden kan du skapa rapporter som visar aggregerade data mot en geografisk eller geometrisk bakgrund. Kartdata kan vara rumsliga data från en Transact-SQL-fråga eller en formfil från Environmental Systems Research Institute, Inc. (ESRI). Du kan också lägga till en Microsoft Bing-kartrutebakgrund.  

### <a name="add-more-to-your-report"></a>Lägga till mer i din rapport

Ändra dina data genom att filtrera, gruppera och sortera data, eller genom att lägga till formler eller uttryck. Lägg till diagram, mätare, miniatyrdiagram och indikatorer som sammanfattar data i ett visuellt format.  Filtrera data för anpassade vyer med hjälp av parametrar och filter. Bädda in eller referera till bilder och andra resurser, inklusive externt innehåll.  

Allt innehåll i en sidnumrerad rapport, från rapporten i sig till varje textruta, bild, tabell och diagram, har en matris med egenskaper som du kan konfigurera så att rapporten ser ut exakt som du vill ha den.

## <a name="creating-a-report-definition"></a>Skapa en rapportdefinition

När du utformar en sidnumrerad rapport skapar du i själva verket en *rapportdefinition*. Den innehåller inte data. Den anger var data ska hämtas, vilka data som ska hämtas och hur dessa data ska visas. När du kör rapporten tar rapportprocessorn den rapportdefinitionen som du har angett, hämtar data, kombinerar dem med rapportlayouten och genererar därmed rapporten. Du överför rapportdefinitionen till Power BI-tjänsten, http://app.powerbi.com, antingen till Min arbetsyta eller till en arbetsyta som du delar med dina kollegor. Om rapportdatakällan finns lokalt, när du har överfört rapporten, så kan du omdirigera datakällsanslutningen så att den gå via en gateway. 

## <a name="view-your-paginated-report"></a>Visa din sidnumrerade rapport
Du kan visa din sidnumrerade rapport i Power BI-tjänsten i en webbläsare, och även i Power BI-mobilappar. I Power BI-tjänsten kan du exportera rapporten till flera webb- och sidorienterade datorprogramsformat, t.ex. HTML, MHTML, PDF, XML, CSV, TIFF, Word och Excel. Du kan också dela den med andra.  
  
## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Här följer några andra funktioner som inte stöds i den första versionen:

- Fästa rapportsidor eller visuella objekt på Power BI-instrumentpaneler.
- Interaktiva funktioner som dokumentkartor och Visa/Dölj-knappar.
- Underrapporter och detaljerade rapporter.
- Prenumerationer.
- Delade datakällor och delade datamängder.
- Power BI-datamängder.
- Visuella objekt från Power BI-rapporter.
- Sidnumrerade rapporter i appar. Du kan dela en sidnumrerad rapport från en apparbetsyta, men du kan inte inkludera den när du publicerar appen från arbetsytan.
 
## <a name="next-steps"></a>Nästa steg

- [Installera Report Builder från Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=734968)

- [Självstudie: Skapa en sidnumrerad rapport](paginated-reports-quickstart-aw.md)
  

