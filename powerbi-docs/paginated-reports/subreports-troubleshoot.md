---
title: Felsöka underrapporter i sidnumrerade Power BI-rapporter
description: I den här artikeln lär du dig om datakällor som stöds för sidnumrerade rapporter i Power BI-tjänsten samt hur du ansluter till Azure SQL Database-datakällor.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 04/29/2020
ms.openlocfilehash: 6de85f6dda69e902a98d6ee63d1fc4b86fb4180b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82615644"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>Felsöka underrapporter i sidnumrerade Power BI-rapporter

Ibland när du använder underrapporter i sidnumrerade rapporter kan du få ett oväntat resultat, eller så fungerar inte funktionen som väntat. Den här artikeln innehåller lösningar för vanliga problem när du använder underrapporter. En *underrapport* är ett rapportobjekt som visar en annan rapport inuti brödtexten i en sidnumrerad huvudrapport. Mer bakgrund finns i [Underrapporter i sidnumrerade Power BI-rapporter](subreports.md).

## <a name="subreport-couldnt-be-found"></a>Det gick inte att hitta underrapporten

**Beskrivning:** Underrapporten återges inte. I stället visas ett felmeddelande.

### <a name="message"></a>Meddelande

Det gick inte att hitta underrapporten ”Subreport1” på den angivna platsen ”CustomerDetails”. Kontrollera att underrapporten har publicerats och att namnet är korrekt.”

### <a name="possible-reasons"></a>Möjliga orsaker

- Det finns ingen underrapport med det angivna namnet i samma arbetsyta eller app som huvudrapporten.
- Användaren har inte åtkomst till underrapporten.
- Antalet underrapporter i huvudrapporten har nått gränsen för underrapporten (50 underrapporter).

### <a name="troubleshooting-steps"></a>Felsökningsanvisningar

**I en arbetsyta**

- Kontrollera att rapporten med namnet i felmeddelandet finns. Namnet är skiftlägesokänsligt.

**I en app**

- Kontrollera att rapporten med namnet i felmeddelandet finns i appen. Kontakta appens skapare om du vill ha mer hjälp.

**Om rapporten är delad**

1. Kontrollera att rapporten med namnet i felmeddelandet är delad med dig.
2. Om rapporten finns kontrollerar du att ägarens namn är detsamma för huvudrapporten och underrapporten. Kontakta sedan ägaren till huvudrapporten med den informationen.

## <a name="subreport-renders-with-unexpected-content"></a>Underrapporten återges med oväntat innehåll

### <a name="possible-reason"></a>Möjlig orsak

Power BI tillåter att användare har flera rapporter med samma namn i samma arbetsyta

### <a name="troubleshooting-steps-for-report-authors"></a>Felsökningsanvisningar (för rapportförfattare)

1. Öppna huvudrapporten i Power BI Report Builder och ange namnet på underrapporten.
2. Sök efter rapporter med samma namn i arbetsytan.
3. Leta upp den förväntade rapporten och byt namn på resten.

**För icke-författare:** Kontakta författaren.

## <a name="data-retrieval-fails"></a>Datahämtning misslyckas

**Beskrivning:** Det går inte att hämta data medan underrapporten återges. Underrapporten återges inte. I stället visas ett felmeddelande.

### <a name="message"></a>Meddelande

”Det gick inte att hämta data för underrapporten, ”Subreport1”, på: ”InvoiceDetails”. Mer information finns i loggfilerna.”

### <a name="troubleshooting-steps"></a>Felsökningsanvisningar

Samma som de allmänna felsökningsstegen för rapporter med problem med dataåtkomst.

## <a name="rendering-fails-unspecified-parameters"></a>Återgivningsfel: Ospecificerade parametrar

**Beskrivning:** Det går inte att återge underrapporter på grund av ospecificerade parametrar. Underrapporten har obligatoriska parametrar, men huvudrapporten anger inte alla.

### <a name="message"></a>Meddelande 
”En eller flera parametrar angavs inte för underrapporten, ”Subreport1, som finns på: 'SubreportAWithDS'.”

### <a name="troubleshooting-steps-for-the-report-author"></a>Felsökningsanvisningar (för rapportförfattaren)

1. Öppna en huvudrapport i Power BI Report Builder.
2. Öppna en underrapport i Power BI Report Builder.
3. Kontrollera att den uppsättning parametrar som skickas inuti underrapportens rapportobjekt i huvudrapporten matchar uppsättningen parametrar i underrapporten.

**För icke-författare:** Kontakta författaren.

## <a name="rendering-fails-recursion-limit"></a>Återgivningfel: Rekursionsgräns

**Beskrivning:** Det går inte att återge underrapporter på grund av rekursionsgränsen. Underrapporter får inte vara djupare kapslade än 20 nivåer.

### <a name="message"></a>Meddelande

”Rapporten eller underrapporten innehåller en rekursiv underrapport, ”Subreport1”, som överskrider den maximalt tillåtna rekursionsgränsen.”

### <a name="troubleshooting-steps-for-report-authors"></a>Felsökningsanvisningar (för rapportförfattare)

- Minska kapslingen.
- Designa om rapportstrukturen.

## <a name="other-errors"></a>Övriga fel

**Beskrivning:** Fel som inte hamnar i någon av de föregående kategorierna.

### <a name="message"></a>Meddelande

"Fel: Det gick inte att visa underrapporten. ”

### <a name="possible-reasons"></a>Möjliga orsaker

- Flera fel vid underrapportåtergivningen, till exempel parametermatchningsfel med datahämtningsproblem.
- Oväntade fel.

### <a name="troubleshooting-steps-for-report-authors"></a>Felsökningsanvisningar (för rapportförfattare)

1. Kontrollera att underrapporten kan återges direkt.
2. Om underrapporten kan återges kontrollerar du parametrarna i både underrapporten och huvudrapporten.
3. Se till att huvudrapporten inte har fler än 50 unika underrapporter och att underrapporten inte är kapslad djupare än 20 nivåer.
4. Kontakta supporten för Power BI om du inte kan lösa problemet.

**För icke-författare:** Kontakta författaren.

## <a name="next-steps"></a>Nästa steg

[Underrapporter i sidnumrerade Power BI-rapporter](subreports.md)

[Visa en sidnumrerad rapport i Power BI-tjänsten](../consumer/paginated-reports-view-power-bi-service.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
