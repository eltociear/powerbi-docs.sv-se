---
title: Sidnumrerade rapporter i Power BI-tjänsten
description: Dokumentation som beskriver sidnumrerade rapporter och hur du visar dem i Power BI-tjänsten
author: mihart
ms.reviewer: chris finlan
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 12/02/2019
ms.author: mihart
LocalizationGroup: Common tasks
ms.openlocfilehash: a66189707bc6b688be012eeb59881ce4a8517ea1
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "74830478"
---
# <a name="paginated-reports-in-the-power-bi-service"></a>Sidnumrerade rapporter i Power BI-tjänsten
Du har lärt dig mer om [Power BI-rapporter](end-user-reports.md), och det är den typ av rapport du förmodligen kommer att se oftast. Det finns dock en annan typ av rapport som kallas *sidnumrerade rapporter*. *Rapportdesigners* kan dela sidnumrerade rapporter med dig på arbetsytor i Premium-kapaciteter, eller i en app på samma arbetsyta. 

## <a name="what-is-a-paginated-report"></a>Vad är en sidnumrerad rapport?

Rapporterna kallas *sidnumrerade* eftersom de är formaterade för att passa på en sida. En fördel med dem är att alla data visas i en tabell, även om tabellen sträcker sig över flera sidor. Sidnumrerade rapporter kallas ibland ”pixelperfekta” eftersom *rapportdesigners* kan kontrollera sidlayouten i minsta detalj.

När *rapportdesigners* skapar en sidnumrerad rapport skapar de i själva verket en *rapportdefinition*. Den innehåller inte data. Den anger var data ska hämtas, vilka data som ska hämtas och hur dessa data ska visas. När du kör rapporten tar bearbetningsmotorn rapportdefinitionen, hämtar data, kombinerar dem med rapportlayouten och genererar därmed rapporten. Ibland visas standarddata i rapporten. Andra gånger måste du ange parametrar innan du ser några data i rapporten. 

   ![Parametrar för rapporten](./media/end-user-paginated-report/power-bi-report-parameters.png)

Det krävs oftast ingen mer interaktion än så, att ange parametrarna. Om du är faktureringsanalytiker kan du använda sidnumrerade rapporter till att skapa eller skriva ut fakturor. Om du är försäljningschef kan du använda sidnumrerade rapporter till att visa ordrar per butik eller säljare. 

I den här enkla sidnumrerade rapporten genereras vinsten per år när du har valt parametern **År**. 

![Enkel rapport med en parameter](./media/end-user-paginated-report/power-bi-report-simple.png)

Power BI-rapporter är mycket mer interaktiva än sidnumrerade rapporter. I Power BI-rapporter kan du använda ad hoc-rapportering och många fler typer av visualiseringar, som anpassade visuella objekt.

## <a name="identify-a-paginated-report"></a>Identifiera en sidnumrerad rapport

Du kan identifiera sidnumrerade rapporter i innehållslistor och på startsidan via ikonen ![ikon för sidnumrerad rapport](media/end-user-paginated-report/power-bi-report-icon.png).  Sidnumrerade rapporter kan delas med dig antingen direkt eller via en [Power BI-app](end-user-apps.md). Om *rapportdesignern* gett dig behörighet kan du dela den sidnumrerade rapporten vidare och skapa prenumerationer för dig själv och andra.

![rapportlista med olika ikoner](./media/end-user-paginated-report/power-bi-report-list.png)

## <a name="interact-with-a-paginated-report"></a>Interagera med en sidnumrerad rapport

Du interagerar annorlunda med sidnumrerade rapporter än andra rapporter. Du kan skriva ut, skapa bokmärken, exportera och kommentera, men interaktiviteten är inte lika utbredd. Ofta måste du ange indata i sidnumrerade rapporter innan data kan visas på arbetsytan i rapporten.  Andra gånger visas standarddata i rapporten och du kan ange parametrar för att se andra data.

### <a name="print-a-paginated-report"></a>Skriva ut en sidnumrerad rapport

*Sidnumrerade* rapporter är formaterade för att passa bra på en enda sida som du kan skriva ut. Det du ser i webbläsaren är det du ser när du skriver ut. Och om rapporten har en lång tabell skrivs hela tabellen ut, även om den sträcker sig över flera sidor. 

Sidnumrerade rapporter kan ha många sidor. Den här rapporten har till exempel 563 sidor. Varje sida har en exakt utformning med en sida per faktura och upprepande sidhuvuden och sidfötter. När du skriver ut den här rapporten får du sidbrytningar mellan fakturorna.

   ![Sida ett i en sidnumrerad rapport för Tailspin Toys](./media/end-user-paginated-report/power-bi-paginated-500.png)


### <a name="navigate-the-paginated-report"></a>Navigera i sidnumrerade rapporter

Det finns tre parametrar i den här försäljningsorderrapporten: Business type (företagstyp), Reseller (återförsäljare) och Order number (ordernummer). 

![rapport med tre parametrar](./media/end-user-paginated-report/power-bi-parameter.png)

Om du vill ändra informationen som visas anger du nya värden för de tre parametrarna och väljer **Visa rapport**. Här har vi valt **Speciality bike shop**, **Alpine Ski House** och ordernumret **SO46085**. När vi väljer **Visa rapport** uppdateras arbetsytan i rapporten med den nya försäljningsordern.

![ändra parametrar](./media/end-user-paginated-report/power-bi-order.png)

Den nya försäljningsordern visas med de parametrar vi valde. 

![en ny försäljningsorder](./media/end-user-paginated-report/power-bi-new-order.png)

En del sidnumrerade rapporter kan bestå av många sidor.  Använd sidkontrollerna till att navigera i rapporten. 

![sidkontroller](./media/end-user-paginated-report/power-bi-page.png)

### <a name="export-the-paginated-report"></a>Exportera den sidnumrerade rapporten
Du kan exportera sidnumrerade rapporter i flera olika format som PDF, Word, XML, PowerPoint och Excel. När du exporterar bevaras så mycket som möjligt av formateringen. I sidnumrerade rapporter som exporteras till Excel, Word, PowerPoint, MHTML och PDF bevaras till exempel den ”pixelperfekta” formateringen. 

![en ny försäljningsorder](./media/end-user-paginated-report/power-bi-exporting.png)

![fyra olika exporttyper](./media/end-user-paginated-report/power-bi-four.png)

### <a name="subscribe-to-the-paginated-report"></a>Prenumerera på sidnumrerade rapporter
När du prenumererar på en sidnumrerad rapport skickar Power BI ett e-postmeddelande med rapporten som bilaga. När du ställer in prenumerationen väljer du hur ofta du vill få sådana e-postmeddelanden: varje dag, varje vecka, varje timme eller varje månad. Prenumerationen innehåller en bilaga med alla rapportutdata och storleken kan vara upp till 25 MB. Exportera hela rapporten eller välj parametrar i förväg. Du kan välja mellan flera olika filformat för bilagan som Excel, PDF och PowerPoint.  

![Prenumerationsformat](./media/end-user-paginated-report/power-bi-export-list.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

- Sidnumrerade rapporter kan verka vara tomma tills du anger parametrar och väljer **Visa rapport**.

- Om du inte har några sidnumrerade rapporter kan det bero på att ingen har delat den här typen av rapport med dig. Det kan också bero på att systemadministratören inte har aktiverat sidnumrerade rapporter för dig. 

 

## <a name="next-steps"></a>Nästa steg
- [Power BI-rapporter](end-user-reports.md)
- Har du fler frågor? Testa [Power BI Community](https://community.powerbi.com/).

