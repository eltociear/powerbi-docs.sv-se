---
title: Prenumerera på sidnumrerade rapporter i Power BI-tjänsten
description: I den här artikeln får du lära dig några saker som är bra att tänka på när du ska prenumerera på sidnumrerade rapporter i Power BI-tjänsten.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: 472606fcb3b823cdcb722c9d8d6421d0ec652d24
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839556"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Skapa en prenumeration åt dig själv och andra på en sidnumrerad rapport i Power BI-tjänsten 

Nu kan du ställa in e-postprenumerationer åt dig själv och andra på sidnumrerade rapporter i Power BI-tjänsten. I allmänhet fungerar processen på samma sätt som när du [prenumererar på rapporter och instrumentpaneler i Power BI-tjänsten](service-report-subscribe.md). Den här artikeln går igenom skillnaderna och några överväganden. 

När du ställer in prenumerationer väljer du hur ofta du vill få e-postmeddelanden: varje dag, varje vecka eller varje timme. Om du väljer varje dag eller varje vecka kan du välja vilken tid som prenumerationen ska köras. Totalt kan du ställa in upp till 24 olika prenumerationer per dag för varje rapport. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Några saker att tänka på med prenumerationer på sidnumrerade rapporter 

- Till skillnad från prenumerationer på instrumentpaneler och Power BI-rapporter innehåller prenumerationen en bilaga med alla utdata i rapporten.  Följande typer av bilagor stöds: PDF, PowerPoint-presentation (PPTX), Excel-arbetsbok (XLSX), Word-dokument (DOCX), CSV-fil och XML.

- Det visas ingen förhandsgranskning av rapporten i e-postmeddelandets brödtext.  Vi planerar att införa ett alternativ för att visa en bild av den första sidan i rapporten. 

- Maximal storlek för rapportbilagan är 25 MB. 

- Du kan ställa in prenumerationer åt andra på sidnumrerade rapporter som ansluter till datakällor som stöds för närvarande, som Azure Analysis Services eller Power BI-datamängder. Tänk på att rapportbilagan återger data baserat på dina behörigheter, precis som SQL Server Reporting Services fungerar redan idag. 

- Prenumerationer på rapportsidor är knutna till namnet på rapporten.  

- E-postprenumerationer skickas med standardvärden för rapportens parametrar. 

- Alternativet **Efter datauppdatering** som frekvens är inte tillgängligt för sidnumrerade rapporter. Du får alltid de senaste värdena från den underliggande datakällan. 

## <a name="next-steps"></a>Nästa steg

[Skapa en prenumeration åt dig eller andra på rapporter och instrumentpaneler i Power BI-tjänsten](service-report-subscribe.md)

[Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
