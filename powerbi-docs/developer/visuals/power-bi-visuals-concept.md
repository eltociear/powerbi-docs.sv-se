---
title: Begrepp för visuella Power BI-objekt
description: I den här artikeln beskrivs hur visuella objekt integreras med Power BI
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 36742917829013a6efca9d74f88b01bc686437a8
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700856"
---
# <a name="power-bi-visual-concept"></a>Begrepp för visuella Power BI-objekt

I artikeln förklaras hur en användare och ett visuellt objekt interagerar med Power BI och hur en användare interagerar med visuella Power BI-objekt. I diagrammet ser du vilka åtgärder som påverkar det visuella objektet direkt eller via Power BI (om användaren till exempel väljer bokmärken).

![Visuellt Power BI-objekt](./media/visual-concept.svg)

## <a name="the-visual-gets-update-from-power-bi"></a>Det visuella objektet uppdateras via Power BI

Det visuella objektet har metoden `update`. Den här metoden innehåller vanligtvis huvudlogiken för det visuella objektet och ansvarar för att återge diagram eller visualisera data.

De flesta uppdateringar görs via anrop av metoden `update`.

### <a name="user-interacts-with-visual-through-power-bi"></a>Användaren interagerar med det visuella objektet via Power BI

* Användaren öppnar panelen med det visuella objektets egenskaper.

    Power BI hämtar de objekt och egenskaper som stöds från `capabilities.json` för det visuella objektet. Power BI anropar metoden `enumerateObjectInstances` för att hämta de faktiska egenskapsvärdena.

    Det visuella objektet måste returnera faktiska egenskapsvärden.

    Läs mer om [egenskaper och funktioner för visuella objekt](capabilities.md).

* [Användaren ändrar egenskapen för det visuella objektet](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) på formatpanelen.

    När värdet för en egenskap har ändrats anropar Power BI metoden `update` för det visuella objektet och skickar nya `options`-objekt samt nya värden för objekten till uppdateringsmetoden.

    Läs mer om [objekt och egenskaper för visuella objekt](objects-properties.md).

* Användaren ändrar storlek på det visuella objektet.

    När en användare ändrar en storlek på ett visuellt objekt anropar Power BI metoden `update` med ett nytt `option`-objekt. option-objekt har kapslade `viewport`-objekt med det visuella objektets nya bredd och höjd.

* Användaren tillämpar filter på rapport-, sid- eller objektnivå.

    Power BI filtrerar data enligt filtervillkoren och anropar metoden `update` för det visuella objektet så att nya data skickas till det visuella objektet.

    Det visuella objektet hämtar en ny uppdatering av `options`-objektet med nya data i ett av de kapslade objekten. Det beror på hur mappningen av datavyer är konfigurerad för det visuella objektet.

    Läs mer om [mappning av datavyer](dataview-mappings.md).

* Användaren väljer en datapunkt i ett annat visuellt objekt i rapporten.

    Power BI filtrerar eller framhäver valda datapunkter och anropar metoden `update` för det visuella objektet.

    Det visuella objektet hämtar nya filtrerade data eller samma data med en array med markeringar.

    Läs mer om att [framhäva data i visuella objekt](highlight.md).

* Användaren väljer ett bokmärke på bokmärkespanelen i rapporten.

    Två saker kan hända:

    1. Power BI anropar funktionen som är registrerad i metoden `registerOnSelectionCallback` och återanropsfunktionen får arrayer med urval för motsvarande bokmärke.

    2. Power BI anropar metoden `update` med motsvarande filterobjekt i `options`-objektet.

    I båda fallen måste det visuella objektet ändra visualiseringstillstånd enligt mottagna urval eller filterobjekt.

    Om du vill veta mer om bokmärken kan du [läsa om hantering av bokmärken](filter-api.md).

    Om du vill veta mer om filter kan du [läsa om hur visuella Power BI-objekt kan filtrera data i andra visuella objekt](filter-api.md).

### <a name="user-interacts-with-visual-directly"></a>Användaren interagerar direkt med det visuella objektet

* Användaren hovrar med musen över ett dataelement

    Det visuella objektet kan visa ytterligare information om datapunkten via API:et Power BI Tooltips.
    Användaren hovrar med musen över det visuella elementet, det visuella objektet kan hantera händelsen och visa data i knappbeskrivningselementet.

    Det visuella objektet kan visa en standardbeskrivning eller en beskrivning som är specifik för rapportsidan.

    Mer information finns i guiden [om att lägga till knappbeskrivningar](add-tooltips.md).

* Användare ändrar visuella egenskaper (användaren kanske expanderar ett träd och det visuella objektet sparar statusen i egenskaperna)

    Det visuella objektet kan spara egenskapsvärden via Power BI-API:et. Ett exempel är när användaren interagerar med det visuella objektet. Och det visuella objektet måste spara eller uppdatera egenskapsvärden. Då kan det visuella objektet anropa metoden `presistProperties`.

* Användaren klickar på en webbadress.

    Som standard kan inte det visuella objektet öppna webbadressen. För att öppna webbadressen i en ny flik måste det visuella objektet anropa metoden `launchURL` och skicka adressen som parameter.

    Läs mer om [API:et för att visa webbadresser](launch-url.md).

* Användaren tillämpar filter för det visuella objektet

    Det visuella objektet anropar metoden `applyJSONFilter` och skickar filtervillkoren till filtret för att filtrera data i andra visuella objekt.

    Det visuella objektet kan använda flera typer av filter som grundläggande filter, avancerade filter och tupelfilter.

    Om du vill veta mer om filter kan du [läsa om hur visuella Power BI-objekt kan filtrera data i andra visuella objekt](filter-api.md).

* Användaren klickar på/väljer element i det visuella objektet.

    Om du vill veta mer om urval kan du läsa om [hur visuella objekt interagerar](selection-api.md).

### <a name="the-visual-interacts-with-power-bi"></a>Det visuella objektet interagerar med Power BI

* Det visuella objektet begär mer data från Power BI.

    Det visuella objektet kan bearbeta data i mindre delar. API-metoden FetchMoreData begär nästa fragment av datamängden.

    Läs mer om `fetchMoreData` i artikeln om att [hämta mer data från Power BI](fetch-more-data.md)

* Händelsetjänst

    Power BI kan exportera rapporter i PDF-format eller skicka dem via e-post (endast certifierade visuella objekt stöds). Det visuella objektet bör meddela Power BI att återgivningen har slutförts och är redo för PDF/e-post genom att anropa API:et Rendering Events.

    Läs mer om att [exportera rapporter från Power BI till PDF](../../consumer/end-user-pdf.md)

    Läs mer [information om Event Service](event-service.md)

## <a name="next-steps"></a>Nästa steg

Är du webbutvecklare och intresserad av att skapa egna visualiseringar och lägga till dem i AppSource? Läs mer i [Skapa ett visuellt objekt i Power BI](./custom-visual-develop-tutorial.md) och lär dig hur du [publicerar visuella Power BI-objekt till AppSource](../office-store.md).
