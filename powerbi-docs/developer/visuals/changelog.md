---
title: Ändringslogg för API för visuella Power BI-objekt
description: Den här artikeln beskriver huvudsakliga ändringar i olika versioner av API för visuella Power BI-objekt
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: 3cf415cbd14da28d523a042fdf4099fe464a4a8b
ms.sourcegitcommit: a07fa723bb459494c60cf6d749b4554af723482a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2020
ms.locfileid: "84739194"
---
# <a name="power-bi-visuals-api-changelog"></a>Ändringslogg för API för visuella Power BI-objekt
Den här sidan innehåller en snabböversikt över API-versionerna. Versioner som anges här betraktas som stabila och kommer inte att ändras.

## <a name="api-v320"></a>API v3.2.0
  * Stöder **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)**

## <a name="api-v260"></a>API v2.6.0
  * Lägger till **isInFocus** till alternativet Uppdatera och **switchFocusModeState**-metoden till visuell värd
  * Stöder **delsummor**-anpassning

## <a name="api-v250"></a>API v2.5.0
  * Stöder **[Fönstret Analys](./analytics-pane.md)**
  * Stöder metoderna `SelectionIdBuilder`**withMatrixNode** och **withTable**
  * Har inte längre stöd för `DataRepetitionSelector`-gränssnittet, ersatt med `data.CustomVisualOpaqueIdentity`-gränssnittet

## <a name="api-v230"></a>API v2.3.0
  * **[API för Landningssida](./landing-page.md)**
  * **[API för lokal lagring](./local-storage.md)**
  * **[API för tuppelfilter (flerkolumnsfilter)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[API för rendering av händelser](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * Stöder **[återställning av JSON-filter från DataView](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[ContextMenu API](./context-menu.md)**

## <a name="api-v210"></a>API v2.1.0
  * Prestandaförbättringar:
    * Snabbare inläsningstider
    * Mindre minnesstorlek
    * Optimerade data- och händelsetransaktioner  

**Viktig information**
* Omstrukturerade filtrerings-API:er finns tillgängliga i API 2.2 och stöds inte i API 2.1.
* Visuella objekt tar bara emot den dataView-typ som har deklarerats i deras funktioner. Visuella objekt som använder flera dataView-typer kommer att sluta fungera till följd av den här uppdateringen.
* Har inte längre stöd för `DataViewScopeIdentity`-gränssnittet, ersatt med `data.DataRepetitionSelector`-gränssnittet. Om du har använt nyckelegenskapen i `DataViewScopeIdentity`-gränssnittet kan du ersätta den med `JSON.stringify(identity)`
* `undefined` ersätts med `null` inuti dataView. När du itererar över en matris med `var item in myArray` hoppar den över `undefined`, men hoppar inte över `null`. Visuella objekt som använder det här mönstret kan sluta fungera med den här uppdateringen. Se till att söka efter `null` i matriser:
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* Egenskapen `proto` lagrar inte längre dolda metadata\data i dataView. Visuella objekt med som kommer åt egenskaper via `proto` kan sluta fungera med den här uppdateringen.

## <a name="api-v1130"></a>API v1.13.0
* Stöder **[Sync-utsnitt](./enable-sync-slicers.md)** , observera att detta endast fungerar för enskilda fältutsnitt på grund av PBI aktuellt kodtillstånd [läs mer](/power-bi/desktop-slicers).
* Tillgänglighet: [Högkontraststöd](./high-contrast-support.md) 
* Tillgänglighet: Tillåt tangentbordsfokusflagga

## <a name="api-v1120"></a>API v1.12.0
* Stöder teman
* Har stöd för **[fetchMoreData](./fetch-more-data.md)** , observera att **Hämta mer data-API:t** överkommer den hårda gränsen på 30 000 datapunkter
* **[API för arbetsytans knappbeskrivningar](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[FilterManager API](./filter-api.md)**
* Stöder **[bokmärken](./bookmarks-support.md)** 

## <a name="api-v1100"></a>API v1.10.0
* Lägger till `ILocalizationManager`
* **API för autentisering**

## <a name="api-v190"></a>API v1.9.0
* **[launchUrl API](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* Stöder den nya typen **fillRule** (toning) i funktionsschemat
* Stöder **regel**-egenskapen i funktionsschemat för objektegenskaper

## <a name="api-v170"></a>API v1.7.0
* Stöder **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API v1.6.2
* Stöder **[Redigeringsläge](./advanced-edit-mode.md)** för visuella objekt för att komma in i visuellt redigeringsläge
* Stöder **[Interaktiv (HTML) visuella R Power BI-objekt](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** , baserat på HTML

## <a name="api-v150"></a>API v1.5.0
* Stöder **[Tillåt interaktioner](./visuals-interactions.md)** för visuell interaktivitet

## <a name="api-v140"></a>API v1.4.0
* Stöder **[Lokalisering](./localization.md)**

## <a name="api-v130"></a>API v1.3.0
* Stöder **[Knappbeskrivningar](./add-tooltips.md)**

## <a name="api-v120"></a>API v1.2.0
* Lägger till **colorPalette** för att hantera de färger som används i ditt visuella objekt.
* Stöder **Markering av flera** – selectionManager kan acceptera en matris med `SelectionId`.
* Stöder **[visuella R-objekt](https://microsoft.github.io/PowerBI-visuals/tutorials/building-r-powered-custom-visual/creating-r-visuals.md)** med R-skript

## <a name="api-v110"></a>API v1.1.0
* Stöder visuella felsökningsobjekt i iFrame
* Lägger till begränsat läge för låg vikt med snabbare initiering av iFrame
* Åtgärdar [Capabilities.objects stöder inte text-typ](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12) problem
* Stöder `pbiviz update` att uppdatera Visual API Type-definitioner och schema
* Stöder `--api-version` flagga i `pbiviz new` för att skapa visuella objekt med en särskild API-version
* Stöder alfaversionen av API v1.2.0

**Visuell värd**
* Lägger till **createSelectionIdBuilder** för att skapa unika identifierare som används för dataurval
* Lägger till **createSelectionManager** för att hantera markeringsstatus för det visuella objektet och kommunicerar ändringar i den visuella värden
* Lägger till en matris med standard **färger** som ska användas i visuella objekt

## <a name="api-v100"></a>API v1.0.0
* Initial API-version
