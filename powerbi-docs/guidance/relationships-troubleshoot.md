---
title: Vägledning vid felsökning av relationer
description: Vägledning för felsökning av modellrelationsproblem.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 03/02/2020
ms.author: v-pemyer
ms.openlocfilehash: e2854d82d858bb1963b691d32d561c7b3bbfc11a
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263655"
---
# <a name="relationship-troubleshooting-guidance"></a>Vägledning vid felsökning av relationer

Den här artikeln är avsedd för dig som är datamodellerare som arbetar med Power BI Desktop. Den ger vägledning om hur du felsöker specifika problem som kan uppstå när du utvecklar modeller och rapporter.

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>Checklista för felsökning

När ett visuellt rapportobjekt konfigureras för att använda fält från två (eller flera) tabeller, och det inte visar rätt resultat (eller något resultat), är det möjligt att problemet är relaterat till modellrelationer.

I det här fallet är här en allmän felsökningslista att följa. Du kan progressivt arbeta genom kontrollistan tills du har identifierat problemen.

1. Ändra det visuella objektet till en tabell eller matris eller öppna fönstret ”se data” – det är enklare att felsöka problem när du kan se frågeresultatet
1. Om det finns ett tomt frågeresultat växlar du till datavy – verifiera att tabeller har lästs in med rader med data
1. Växla till modelläge – det är enkelt att se relationerna och snabbt fastställa deras egenskaper
1. Kontrollera att det finns relationer mellan tabellerna
1. Kontrollera att egenskaper för kardinalitet är korrekt konfigurerade – de kan vara felaktiga om en kolumn för en ”många”-sida innehåller unika värden och har konfigurerats felaktigt som en ”en”-sida
1. Kontrollera att relationerna är aktiva (heldragen linje)
1. Kontrollera att filterriktningarna stöder spridning (tolka pilarna)
1. Kontrollera att rätt kolumner är relaterade – Välj antingen relationen eller hovra över den för att visa relaterade kolumner
1. Kontrollera att de relaterade kolumndatatyperna är desamma eller minst kompatibla – det är möjligt att relatera en textkolumn till en heltalskolumn, men det finns inga matchningar för filtren att sprida
1. Växla till datavy och kontrollera att matchande värden kan hittas i relaterade kolumner

## <a name="troubleshooting-guide"></a>Felsökningsguide

Här är en lista över problem tillsammans med möjliga lösningar.

|Problem|Möjliga orsaker|
|---------|---------|
|Det visuella objektet visar inga resultat|– Modellen har ännu inte lästs in med data<br />– Inga data finns i filterkontexten<br />– Säkerhet på radnivå upprätthålls<br />– Relationer sprids inte mellan tabeller – _följ kontrollistan ovan_<br />– Säkerhet på radnivå upprätthålls, men en dubbelriktad relation är inte aktiverad för att spridas – se [säkerhet på radnivå (RLS) med Power BI Desktop](../desktop-rls.md)|
|Det visuella objektet visar samma värde för varje gruppering |– Relationer finns inte<br />– Relationer sprids inte mellan tabeller – _följ kontrollistan ovan_|
|Det visuella objektet visar resultat, men de är inte korrekta|– Visuellt objekt är felaktigt konfigurerat<br />– Måttlogiken är felaktig<br />– Modelldata måste uppdateras<br />– Källdata är felaktiga<br />– Relationskolumner är felaktigt relaterade (till exempel **ProductID**-kolumnen mappar till **CustomerID**)<br />– Det är en relation mellan två DirectQuery-tabeller och kolumnen ”en”-sida i en relation innehåller dubblettvärden|
|Tomma grupperingar eller utsnitt/filter-objekt visas och källkolumnerna innehåller inte tomma steg|– Det är en stark relation och kolumnen ”många”-sida innehåller värden som inte lagras i kolumnen ”en”-sida – se [modellrelationer i Power BI Desktop (starka relationer)](../desktop-relationships-understand.md#strong-relationships)<br />– Det är en stark relation med en-till-en-relation och relaterade kolumner som innehåller tomma celler – se [modellrelationer i Power BI Desktop (starka relationer)](../desktop-relationships-understand.md#strong-relationships)<br />– En inaktiverad relationskolumn lagrar tomma celler eller innehåller värden som inte är lagrade på ”en”-sidan|
|Data saknas i visualiseringen|– Felaktiga/oväntade filter tillämpas<br />– Säkerhet på radnivå upprätthålls<br />– Det är en svag relation och det finns tomma värden i relaterade kolumner eller problem med dataintegritet – se [modellrelationer i Power BI Desktop (svaga relationer)](../desktop-relationships-understand.md#weak-relationships)<br />– Det är en relation mellan två DirectQuery-tabeller, relationen är konfigurerad att [anta referensintegritet](../desktop-relationships-understand.md#assume-referential-integrity), men det finns problem med dataintegritet (felmatchade värden i relaterade kolumner)|
|Säkerhet på radnivå är inte korrekt framtvingad|– Relationer sprids inte mellan tabeller – _följ kontrollistan ovan_<br />– Säkerhet på radnivå upprätthålls, men en dubbelriktad relation är inte aktiverad för att spridas – se [säkerhet på radnivå (RLS) med Power BI Desktop](../desktop-rls.md)|
|||

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Modellrelationer i Power BI Desktop](../desktop-relationships-understand.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
