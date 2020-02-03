---
title: Migrera till powerbi-visuals-tools version 3.x
description: Komma igång med den nya versionen av powerbi-visuals-tools
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: d9af0ab870732990201ab3478d71fdafa9e13439
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818834"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-version-3x"></a>Migrera till nya powerbi-visuals-tools version 3.*x*

Från och med version 3 använder Power BI Visual Tools (powerbi-visuals-tools, eller `pbiviz`) WebPack till att skapa anpassade visuella objekt.
Det finns många förbättringar för att skapa visuella objekt för utvecklare i den nya versionen:

- TypeScript version 3.*x* används som standard. Från och med TypeScript 1.5 så har nomenklaturen ändrats. [Läs mer om TypeScript-moduler](https://www.typescriptlang.org/docs/handbook/modules.html).

- ES6-moduler (ECMAScript 6) stöds. Nu kan du använda ES6-importer i stället för [externalJS](migrate-to-new-tools.md#configure-loading-of-external-libraries).

- Nya versioner av [D3v5](https://d3js.org/) (Data-Driven Documents) och andra modulbaserade ES6-bibliotek stöds.

- Minskad paketstorlek. WebPack använder [Tree shaking](https://webpack.js.org/guides/tree-shaking/) till att ta bort oanvänd kod. Det här minskar mängden JavaScript-kod och ger bättre prestanda vid inläsning av visuella objekt.

- Förbättrad API-prestanda.

- Biblioteket Globalize.js [är integrerat](migrate-to-new-tools.md#remove-the- globalizejs-library) i FormattingUtils.

- Power BI Visual Tools använder [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) till att visa kodbasen för det visuella objektet.

I den här artikeln beskrivs alla migreringssteg för den nya versionen av Power BI Visual Tools.

## <a name="backward-compatibility"></a>Bakåtkompatibilitet

De nya verktygen är bakåtkompatibla med kodbasen för gamla visuella objekt, men det kan krävas en del ändringar om externa bibliotek ska läsas in.

Biblioteken med stöd för modulsystem importeras som WebPack-moduler. Alla andra bibliotek och källkoden för det visuella objektet paketeras i en modul.

Globala variabler som JQuery och Lodash, som användes i tidigare versioner av Power BI Visual Tools, är nu inaktuella. Om den gamla koden för ditt visuella objekt använder globala variabler fungerar det visuella objektet förmodligen inte med de nya verktygen.

I tidigare versioner av Power BI Visual Tools behövde du definiera en visuell klass under modulen `powerbi.extensibility.visual`. I den nya versionen måste du i stället definiera en visuell klass i TypeScript-huvudfilen (.ts). Det är vanligtvis filen `src/visual.ts`.

## <a name="install-powerbi-visuals-tools"></a>Installera powerbi-visuals-tools

Installera de nya verktygen genom att köra följande kommando:

```cmd
npm install -g powerbi-visuals-tools
```

Den här koden är från filen `package.json` i [lagringsplatsen för det visuella objektet sampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L15), när det visuella projektet har uppdaterats för att fungera med de nya verktygen:

```json
{
    "name": "visual",
    "version": "3.0.0",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "package": "pbiviz package",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
        "@types/d3": "5.7.2",
        "d3": "5.12.0",
        "powerbi-visuals-api": "^2.6.1",
        "powerbi-visuals-tools": "^3.1.7",
        "powerbi-visuals-utils-dataviewutils": "^2.2.1",
        "powerbi-visuals-utils-formattingutils": "^4.4.2",
        "powerbi-visuals-utils-interactivityutils": "^5.6.0",
        "powerbi-visuals-utils-tooltiputils": "^2.3.1",
        "tslint": "^5.20.0",
        "tslint-microsoft-contrib": "^6.2.0"
    }
}
```

## <a name="install-the-power-bi-custom-visuals-api"></a>Installera Power BI-API:et för anpassade visuella objekt

Den nya versionen av powerbi-visuals-tools innehåller inte alla API-versioner. I stället måste du installera en version av paketet [powerbi-visuals-api](https://www.npmjs.com/package/powerbi-visuals-api). Välj den version av paketet som matchar API-versionen för dina visuella Power BI-objekt. Paketet innehåller alla typdefinitioner för Power BI-API:et för anpassade visuella objekt.

Lägg till `powerbi-visuals-api` i projektberoendena genom att köra det här kommandot:

```cmd
npm install --save-dev powerbi-visuals-api
```

Ta även bort eventuella länkar till gamla API-typdefinitioner, eftersom WebPack automatiskt tar med typer från `powerbi-visuals-api`. Motsvarande ändringar finns i [package.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/package.json#L14) och [tsconfig.json](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L14).

## <a name="update-tsconfigjson"></a>Uppdatera tsconfig.json

Om du vill använda externa moduler ändrar du alternativet `out` till `outDir`. Använd till exempel `"outDir": "./.tmp/build/",` i stället för `"out": "./.tmp/build/visual.js",`.

Den här ändringen behövs eftersom TypeScript-filerna kommer att kompileras till JavaScript-filer oberoende av varandra. Det är därför du inte längre behöver ange filen visual.js som utdata.

Du kan också ändra alternativet `target` till `ES6` om du vill använda modern JavaScript som utdata. Den här ändringen är [valfri](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/tsconfig.json#L7).

## <a name="update-custom-visuals-utilities"></a>Uppdatera verktyg för anpassade visuella objekt

Om du använder något av [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils)-paketen ska du även uppdatera dem till den senaste versionen. Det gör du genom att köra det här kommandot:

```cmd
npm install powerbi-visuals-utils-<UTILNAME> --save
```

Om du till exempel vill hämta den nya versionen med externa TypeScript-moduler skriver du så här: 

```cmd
npm install powerbi-visuals-utils-dataviewutils --save
```

Du kan se ett exempel på ett visuellt objekt som använder alla `powerbi-visuals-utils`-paket i [lagringsplatsen för MekkoChart](https://github.com/Microsoft/powerbi-visuals-mekkochart).

## <a name="remove-the-globalizejs-library"></a>Ta bort biblioteket Globalize.js

Den nya versionen av [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils) innehåller Globalize.js. Du behöver alltså inte inkludera det här biblioteket i dina projekt manuellt. Alla obligatoriska lokaliseringar kommer att läggas till i det slutliga paketet automatiskt.

## <a name="configure-loading-of-external-libraries"></a>Konfigurera inläsning av externa bibliotek

Inkludera nya JavaScript-filer efter bibliotek i matrisen `externalJS` i `pbiviz.json`. Till exempel:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importera biblioteken i din källkod. Du kan till exempel använda den här instruktionen för `lodash-es`:

```JS
import * as _ from "lodash-es";
```

I föregående exempel är `_` den globala variabeln för biblioteket `lodash`.

## <a name="make-changes-in-the-sources-of-your-visuals"></a>Gör ändringar i källkoden för dina visuella objekt

Den viktigaste ändringen du måste göra är att konvertera interna moduler till externa moduler. Du kan inte använda externa moduler i interna moduler.

Här är en detaljerad beskrivning av de ändringar du ska göra. Ändringarna beskrivs i kontexten för kodexemplet för det visuella stapeldiagramobjektet:

1. Ta bort alla moduldefinitioner från varje fil med [källkod](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbL1-L3):

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importera definitionerna för Power BI-API:et för anpassade visuella objekt](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR4):

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importera nödvändiga gränssnitt eller klasser](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR12-R35) från den interna `powerbi`-modulen.

    ```typescript
    import PrimitiveValue = powerbi.PrimitiveValue; 
    import VisualUpdateOptions = powerbi.extensibility.visual.VisualUpdateOptions; 
    import VisualConstructorOptions = powerbi.extensibility.visual.VisualConstructorOptions; 
    import IVisualHost = powerbi.extensibility.visual.IVisualHost; 
    import IColorPalette = powerbi.extensibility.IColorPalette; 
    import IVisual = powerbi.extensibility.visual.IVisual; 
    import VisualObjectInstance = powerbi.VisualObjectInstance; 
    import VisualObjectInstanceEnumeration = powerbi.VisualObjectInstanceEnumeration; 
    import EnumerateVisualObjectInstancesOptions = powerbi.EnumerateVisualObjectInstancesOptions; 
    import Fill = powerbi.Fill; 
    import VisualTooltipDataItem = powerbi.extensibility.VisualTooltipDataItem; 
    import ISelectionManager = powerbi.extensibility.ISelectionManager; 
    ```

4. [Importera biblioteket D3.js](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR2):

    ```typescript
    import * as d3 from "d3";
    ```

    Du kan också endast importera de nödvändiga D3-biblioteksmodulerna:

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importera de verktyg, klasser och gränssnitt som är definierade i det visuella projektet](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-433142f7814fee940a0ffc98dc75bfcbR38-R41) till huvudkällkodsfilen:

    ```typescript
    import { getLocalizedString } from "./localization/localizationHelper";
    import { getValue, getCategoricalObjectValue } from "./objectEnumerationUtility";
    import {
        ITooltipServiceWrapper,
        TooltipEventArgs,
        createTooltipServiceWrapper
    } from "./tooltipServiceWrapper";
    ```

### <a name="import-css-styles"></a>Importera CSS-formatmallar

I den nya versionen av verktygen kan du importera `CSS`- och `Less`-format direkt till TypeScript-koden. Avsnittet [Format](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/471f103fcef9af93cff76cbac9c7fc67564acd4b/pbiviz.json#L21) som användes tidigare ignoreras nu i kompilatorn.

Om du vill använda din formatmall öppnar TypeScript-huvudfilen (.ts) och lägger till följande rad:  

```typescript
import "./../style/visual.less";
```  

Dina `CSS`- och `Less`-format kompileras automatiskt.

### <a name="externaljs-section-in-pbivizjson"></a>externalJS-avsnittet i pbiviz.json

Verktygen [behöver inte någon lista med `externalJS`-bibliotek](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/commit/72ec605ce6a311a6cc004453b07973b6ed5e61f9#diff-a1a7bbee7e7d2f9d449f4b534532bcf2R20) att läsa in i det visuella paketet, eftersom WebPack innehåller alla importerade bibliotek.

> [!NOTE]
> I `pbiviz.json` lämnar du avsnittet `externalJS` tomt.

Använd det vanliga kommandot `npm run package` till att skapa det visuella paketet, eller kör `npm run start` om du vill starta utvecklingsservern.

## <a name="update-the-d3js-library-to-version-5"></a>Uppdatera biblioteket D3.js till version 5

Med de nya verktygen för visuella objekt kan du börja använda den nya versionen av biblioteket D3.js. Kör de här kommandona för att uppdatera D3 i ditt visuella projekt:

- `npm install --save d3@5` för att installera nya D3.js.

- `npm install --save-dev @types/d3@5` för att installera nya typdefinitioner för D3.js.

> [!IMPORTANT]
> I D3 version 5 introduceras flera nya stora ändringar.

Ändra koden så att den fungerar med nya D3.js:

- Gränssnittet `d3.Selection<T>` [har ändrats](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) till `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`.

- Du kan inte tillämpa flera attribut med ett enda anrop av metoden `attr`. I stället måste du [skicka varje attribut i ett separat anrop](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) av `attr`. Gör även [separata anrop till metoden `style`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247).

- I D3.js version 4 introducerades den nya metoden `merge`. Den här metoden används ofta till att sammanfoga `enter`- och `update`-urval efter en datakoppling. Den korrekta användningen av D3 är att [anropa metoden `merge`](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272).

[Läs mer](https://github.com/d3/d3/blob/master/CHANGES.md) om ändringarna i biblioteket D3.js.

## <a name="install-babel-and-core-js"></a>Installera Babel och core-js

Från och med version 3.1 använder verktygen för visuella objekt Babel till att kompilera modern JavaScript-kod till gamla ES5 (ECMAScript 5) så att många olika webbläsare kan användas.

Babel-alternativet är aktiverat som standard, men du måste importera paketet [`core-js`](https://www.npmjs.com/package/core-js) manuellt. Kör det här kommandot för att installera paketet:

```cmd
npm install --save core-js
```

Importera sedan paketet till startpunkten för det visuella objektets kod. Det är vanligtvis filen src/visual.ts.

```JS
import "core-js/stable";
```

Läs mer om Babel [i dokumenten](https://babeljs.io/docs/en/).
