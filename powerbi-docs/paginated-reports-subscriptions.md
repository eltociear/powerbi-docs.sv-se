---
title: Prenumerera på sidnumrerade rapporter i Power BI-tjänsten
description: I den här artikeln får du lära dig saker att tänka på om att prenumerera på sidnumrerade rapporter i Power BI-tjänsten.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: ccec6658808d94728f2a4f14de67c36da0f51def
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222207"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Prenumerera på dig själv och andra sidnumrerade rapporter i Power BI-tjänsten 

Du kan nu ställa in e-postprenumerationer för dig själv och andra för sidnumrerade rapporter i Power BI-tjänsten. I allmänhet processen är samma som [prenumerera på rapporter och instrumentpaneler i Power BI-tjänsten](service-report-subscribe.md). Den här artikeln anger skillnader och överväganden. 

Att konfigurera prenumerationer, väljer du hur ofta du vill ta emot e-postmeddelanden: varje dag, vecka eller per timme. Om du väljer varje dag eller varje vecka, kan du välja tid vill du att prenumerationen ska köras. I alla, kan du ange upp till 24 olika prenumerationer per dag för varje rapport. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Överväganden för sidnumrerade rapportprenumerationer 

- Till skillnad från prenumerationer för instrumentpaneler och rapporter för Power BI innehåller prenumerationen bifogad fil på hela rapporten utdata.  Följande typer av bifogad fil stöds: PDF-, PowerPoint-presentation (PPTX), Excel-arbetsboken (XLSX), Word-dokument (DOCX), CSV-fil och XML.

- Det finns ingen förhandsversion bild i rapporten i e-postmeddelandets brödtext.  Vi planerar att ha bild av den första sidan i rapporten som ett valfritt objekt. 

- Maximal rapport bilagans storlek är 25 MB. 

- Du kan prenumerera på andra användare för sidnumrerade rapporter som ansluter till alla stöds för närvarande datakällor, inklusive Azure Analysis Services eller Power BI-datauppsättningar. Tänk på den bifogade filen i rapporten visar data baserat på dina behörigheter, precis som du gör i dag med SQL Server Reporting Services. 

- Rapportsideprenumerationer är knutna till namnet på rapporten.  

- E-postprenumerationer skickas med rapportens standardparametervärden. 

- Det finns inga **efter datauppdatering** alternativ för frekvensen med sidnumrerade rapporter. Du kan alltid hämta de senaste värdena från den underliggande datakällan. 

## <a name="next-steps"></a>Nästa steg

[Prenumerera på dig själv och andra rapporter och instrumentpaneler i Power BI-tjänsten](service-report-subscribe.md)

[Vad är sidnumrerade rapporter i Power BI Premium? (Förhandsversion)](paginated-reports-report-builder-power-bi.md)
