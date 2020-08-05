---
title: Prenumerera på sidnumrerade rapporter i Power BI-tjänsten
description: I den här artikeln får du lära dig några saker som är bra att tänka på när du ska prenumerera på sidnumrerade rapporter i Power BI-tjänsten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 12/03/2019
ms.openlocfilehash: 0e4a62cf6216af49ef61651dc310c93de41664b7
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87538135"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Skapa en prenumeration åt dig själv och andra på en sidnumrerad rapport i Power BI-tjänsten 

Nu kan du ställa in e-postprenumerationer åt dig själv och andra på sidnumrerade rapporter i Power BI-tjänsten. I allmänhet fungerar processen på samma sätt som när du [prenumererar på rapporter och instrumentpaneler i Power BI-tjänsten](end-user-subscribe.md). Den här artikeln går igenom skillnaderna och några överväganden. 

När du ställer in prenumerationer väljer du hur ofta du vill få e-postmeddelanden: varje dag, varje vecka, varje månad eller varje timme. Du kan också välja de tidpunkter då du vill att prenumerationen ska löpa. Totalt kan du ställa in upp till 24 olika prenumerationer för varje rapport. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Några saker att tänka på med prenumerationer på sidnumrerade rapporter 

- Till skillnad från prenumerationer på instrumentpaneler och Power BI-rapporter innehåller prenumerationen en bilaga med alla utdata i rapporten.  Följande typer av bilagor stöds: PDF, PowerPoint-presentation (PPTX), Excel-arbetsbok (XLSX), Word-dokument (DOCX), CSV-fil och XML.

- Du kan inkludera en förhandsgranskning av rapporten i e-postmeddelandets brödtext.  Detta är valfritt och kan skilja sig något från den första sidan i ditt bifogade rapportdokument beroende på vilket bilageformat som valts. 

- Maximal storlek för rapportbilagan är 25 MB. 

- Du kan ställa in prenumerationer åt andra på sidnumrerade rapporter som ansluter till datakällor som stöds för närvarande, som Azure Analysis Services eller Power BI-datamängder. Tänk på att rapportbilagan återger data baserat på dina behörigheter, precis som SQL Server Reporting Services fungerar redan idag. 

- E-postprenumerationer kan skickas med antingen de aktuellt valda parametrarna eller standardparametrarna för din rapport.  Du kan ange olika parametervärden för varje prenumeration som du skapar för rapporten. 

- Om rapportförfattaren har angett uttrycksbaserade parametrar (till exempel att standardvärdet alltid är dagens datum) använder prenumerationen det som standardvärde. Du kan ändra andra parametervärden och välja att använda aktuella värden, men såvida du inte uttryckligen ändrar även det värdet så använder prenumerationen den uttrycksbaserade parametern.

- Alternativet **Efter datauppdatering** som frekvens är inte tillgängligt för sidnumrerade rapporter. Du får alltid de senaste värdena från den underliggande datakällan. 

## <a name="next-steps"></a>Nästa steg

[Skapa en prenumeration åt dig eller andra på rapporter och instrumentpaneler i Power BI-tjänsten](../collaborate-share/service-report-subscribe.md)

[Sidnumrerade rapporter i Power BI-tjänsten](end-user-paginated-report.md)
