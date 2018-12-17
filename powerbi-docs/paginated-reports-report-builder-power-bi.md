---
title: Vad är sidnumrerade rapporter i Power BI Premium? (Förhandsgranskning)
description: Sidnumrerade rapporter är rapporter som kan skrivas ut eller delas. Du kan kontrollera rapportlayouten i detalj. De visar alla data i en tabell, även om tabellen t.ex. sträcker sig över flera sidor.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: overview
ms.date: 11/20/2018
ms.author: maggies
ms.openlocfilehash: 7a39d7b3bdbbd592afc6481c5936efc76569ad11
ms.sourcegitcommit: 458e091a0a0bfb71ea3980d44df6408f48bab586
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/22/2018
ms.locfileid: "52289230"
---
# <a name="what-are-paginated-reports-in-power-bi-premium-preview"></a>Vad är sidnumrerade rapporter i Power BI Premium? (Förhandsgranskning)
Sidnumrerade rapporter, som länge varit standardrapportformat i SQL Server Reporting Services, är nu tillgängliga i Power BI-tjänsten. Sidnumrerade rapporter är rapporter som har utformats för att skrivas ut eller delas. De kallas ”sidnumrerade” eftersom de är formaterade för att passa på en sida. De visar alla data i en tabell, även om tabellen sträcker sig över flera sidor. Rapporterna kallas ibland ”pixelperfekta” eftersom du kan kontrollera deras sidlayout i minsta detalj. Sidnumrerade rapporter baseras på tekniken för RDL-rapporter i SQL Server Reporting Services. Report Builder är ett fristående verktyg för redigering av sidnumrerade rapporter. 

Sidnumrerade rapporter kan ha många sidor. Den här rapporten har till exempel 563 sidor. Varje sida har en exakt utformning med en sida per faktura och upprepande sidhuvuden och sidfötter.

![Sidnumrerad rapport i Power BI-tjänsten](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

Du kan förhandsgranska rapporten i Report Builder och sedan publicera den i Power BI-tjänsten http://app.powerbi.com. Du måste ha en Power BI Pro-licens för att kunna publicera en rapport i tjänsten. Du kan publicera och dela sidnumrerade rapporter på Min arbetsyta eller på apparbetsytor, så länge arbetsytan finns i en Power BI Premium-kapacitet. Dessutom måste en Power BI-administratör aktivera sidnumrerade rapporter i Power BI-administratörsportalen. Läs mer om att [konfigurera arbetsbelastningar](service-admin-premium-manage.md#configure-workloads). 

## <a name="create-reports-in-report-builder"></a>Skapa rapporter i Report Builder

Sidnumrerade rapporter har sitt eget designverktyg: Report Builder. Om du har skapat sidnumrerade rapporter för Power BI-rapportservern eller SQL Server Reporting Services (SSRS) kan du använda samma verktyg och samma version. Sidnumrerade rapporter som du skapar för SSRS 2016 och 2017, eller lokalt för Power BI Report Server, är i själva verket kompatibla med Power BI-tjänsten. Power BI-tjänsten har bakåtkompatibilitet så att du kan flytta dina rapporter framåt och uppgradera alla sidnumrerade rapporter av äldre version. Alla funktioner är inte tillgängliga vid start. Se [Begränsningar och överväganden](#limitations-and-considerations) i den här artikeln för mer information.
     
## <a name="report-from-a-variety-of-data-sources"></a>Rapportera från en mängd olika datakällor

En enskild sidnumrerad rapport kan ha flera olika datakällor. Den har inte, till skillnad från Power BI-rapporter, en underliggande datamodell. För denna första version av sidnumrerade rapporter i Power BI-tjänsten skapar du inbäddade datakällor och datamängder i själva rapporten. Du kan inte använda delade datakällor eller delade datamängder för tillfället. Du skapar rapporter i Report Builder på din lokala dator. Om en rapport ansluter till lokala data när du har överfört rapporten till Power BI-tjänsten måste du skapa en gateway och omdirigera dataanslutningen. Här följer de datakällor som du kan ansluta till den första versionen:

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
Du kan visa din sidnumrerade rapport i Power BI-tjänsten i en webbläsare, och även i Power BI-mobilappar. Från Power BI-tjänsten kan du exportera rapporten till flera format, t.ex. HTML, MHTML, PDF, XML, CSV, TIFF, Word och Excel. Du kan också dela den med andra.  
  
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
- [Ange data direkt i en sidnumrerad rapport](paginated-reports-enter-data.md)

  
