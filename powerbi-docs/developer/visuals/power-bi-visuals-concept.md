---
title: Begrepp inom visuella Power BI-objekt
description: I artikeln beskrivs hur visuella objekt integreras med Power BI och hur en användare kan interagera med ett visuellt objekt i Power BI.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: bb0834527ba23c6cfcc155cc65cd0318b296ba84
ms.sourcegitcommit: 052df769e6ace7b9848493cde9f618d6a2ae7df9
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2020
ms.locfileid: "75925594"
---
# <a name="visuals-in-power-bi"></a>Visuella objekt i Power BI

I artikeln beskrivs hur visuella objekt integreras med Power BI och hur en användare kan interagera med ett visuellt objekt i Power BI. 

Följande bild visar hur vanliga visuellt baserade åtgärder som en användare vidtar, t.ex. att välja ett bokmärke, bearbetas i Power BI.

![Åtgärdsdiagram för visuella Power BI-objekt](./media/visual-concept.svg)

## <a name="visuals-get-updates-from-power-bi"></a>Visuella objekt hämtar uppdateringar från Power BI

Ett visuellt objekt anropar en `update`-metod för att hämta uppdateringar från Power BI. `update`-metoden innehåller vanligtvis huvudlogiken för det visuella objektet och ansvarar för att återge ett diagram eller visualisera data.

Uppdateringar utlöses när det visuella objektet anropar `update`-metoden.

## <a name="action-and-update-patterns"></a>Åtgärds- och uppdateringsmönster

Åtgärder och efterföljande uppdateringar i visuella Power BI-objekt sker i något av följande tre mönster:

* Användaren interagerar med ett visuellt objekt via Power BI.
* Användaren interagerar direkt med det visuella objektet.
* Det visuella objektet interagerar med Power BI.

### <a name="user-interacts-with-a-visual-through-power-bi"></a>Användaren interagerar med ett visuellt objekt via Power BI

* Användaren öppnar panelen med det visuella objektets egenskaper.

    När en användare öppnar det visuella objektets egenskapspanel, hämtar Power BI objekt och egenskaper som stöds från det visuella objektets fil *capabilities.json*. För att kunna ta emot faktiska värden för egenskaper, anropar Power BI `enumerateObjectInstances`-metoden för det visuella objektet. Det visuella objektet returnerar faktiska egenskapsvärden.

    Mer information finns i [Funktioner och egenskaper för visuella Power BI-objekt](capabilities.md).

* En användare [ändrar en egenskap för det visuella objektet](../../visuals/power-bi-visualization-customize-title-background-and-legend.md) i formatpanelen.

    När en användare ändrar värdet för en egenskap i formatpanelen, anropar Power BI `update`-metoden för det visuella objektet. Power BI skickar det nya `options`-objektet till `update`-metoden. Objekten innehåller de nya värdena.

    Mer information finns i [Objekt och egenskaper för visuella Power BI-objekt](objects-properties.md).

* En användare ändrar storlek på det visuella objektet.

    När en användare ändrar storlek på ett visuellt objekt, anropar Power BI `update`-metoden med det nya `options`-objektet. `options`-objekt har kapslade `viewport`-objekt som innehåller den nya bredden och höjden för det visuella objektet.

* Användaren tillämpar ett filter på nivån för rapporten, sidan eller det visuella objektet.

    Power BI filtrerar data baserat på filtervillkor. Power BI anropar `update`-metoden till det visuella objektet för att uppdatera det visuella objektet med nya data.

    Det visuella objektet hämtar en ny uppdatering av `options`-objektet, när det finns nya data i något av de kapslade objekten. Hur uppdateringen utförs beror på hur mappningen av datavyer är konfigurerad för det visuella objektet.

    Mer information finns i [Förstå datavymappning i visuella Power BI-objekt](dataview-mappings.md).

* Användaren väljer en datapunkt i ett annat visuellt objekt i rapporten.

    När en användare väljer en datapunkt i ett annat visuellt objekt i rapporten, filtrerar eller markerar Power BI de valda datapunkterna och anropar det visuella objektets `update`-metod. Det visuella objektet hämtar nya filtrerade data, eller samma data med en matris med markeringar.

    Mer information finns i [Markera datapunkter i visuella Power BI-objekt](highlight.md).

* Användaren väljer ett bokmärke i bokmärkespanelen i rapporten.

    När en användare väljer ett bokmärke i rapportens bokmärkespanel, kan en av två åtgärder utföras:

    * Power BI anropar en funktion som skickas och registreras av `registerOnSelectionCallback`-metoden. Funktionen för motringning hämtar matriser med markeringar för motsvarande bokmärke.

    * Power BI anropar `update`-metoden med ett motsvarande `filter`-objekt inuti `options`-objektet.

    I båda fallen måste det visuella objektet ändra sitt tillstånd enligt de mottagna alternativen eller `filter`-objektet.

    Mer information om bokmärken och filter finns i [API för visuella filter i visuella Power BI-objekt](filter-api.md).

### <a name="user-interacts-with-the-visual-directly"></a>Användaren interagerar direkt med det visuella objektet

* En användare hovrar musen över ett dataelement.

    Det visuella objektet kan visa ytterligare information om en datapunkt via API:et för Power BI-knappbeskrivningar. När en användare hovrar musen över ett visuellt element kan det visuella objektet hantera händelsen och visa data om den associerade knappbeskrivningen. Det visuella objektet kan antingen visa en standardknappbeskrivning eller en knappbeskrivning för rapportsidan.

    Mer information finns i [Knappbeskrivningar i visuella Power BI-objekt](add-tooltips.md).

* En användare ändrar egenskaperna för det visuella objektet. (Användaren kanske expanderar ett träd och det visuella objektet sparar tillståndet i egenskaperna.)

    Det visuella objektet kan spara egenskapsvärden via API:et i Power BI. Om en användare exempelvis interagerar med det visuella objektet och det visuella objektet behöver spara eller uppdatera egenskapsvärdena, kan det visuella objektet anropa `presistProperties`-metoden.

* En användare väljer en URL.

    Som standard kan ett visuellt objekt inte öppna en URL direkt. För att öppna URL:en på en ny flik kan det visuella objektet i stället anropa `launchUrl`-metoden och skicka URL:en som en parameter.

    Mer information finns i [Skapa en start-URL](launch-url.md).

* En användare använder ett filter via det visuella objektet.

    Ett visuellt objekt kan anropa `applyJsonFilter`-metoden och skicka villkor som filtrerar data i andra visuella objekt. Det finns flera typer av filter, inklusive filtren Grundläggande, Avancerat och Tuppel.

    Mer information finns i [API för visuella filter i visuella Power BI-objekt](filter-api.md).

* En användare väljer element i det visuella objektet.

    Mer information om val i ett visuellt Power BI-objekt finns i [Lägg till interaktivitet med visuella markeringar i Power BI](selection-api.md).

### <a name="visual-interacts-with-power-bi"></a>Det visuella objektet interagerar med Power BI

* Ett visuellt objekt begär mer data från Power BI.

    Ett visuellt objekt bearbetar data del för del. API-metoden `fetchMoreData` begär nästa datafragment i datamängden.

    Mer information finns i [Hämta flera data från Power BI](fetch-more-data.md).

* Händelsetjänsten utlöses.

    Power BI kan exportera en rapport till PDF eller skicka en rapport via e-post (gäller endast certifierade visuella objekt). För att meddela Power BI att återgivningen är klar och att det nu går att hämta det visuella objektet som PDF eller e-post, ska det visuella objektet anropa API:et för återgivningshändelser.

    Mer information finns i [Exportera rapporter från Power BI till PDF](../../consumer/end-user-pdf.md).

    Mer information om händelsetjänsten finns i [Rendera händelser i visuella Power BI-objekt](event-service.md).

## <a name="next-steps"></a>Nästa steg

Är du intresserad av att skapa visualiseringar och lägga till dem i Microsoft AppSource? Läs följande artiklar:

* [Utveckla ett visuellt Power BI-objekt](./custom-visual-develop-tutorial.md)
* [Publicera visuella Power BI-objekt på Partnercenter](../office-store.md)
