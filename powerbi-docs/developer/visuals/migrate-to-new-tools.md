---
title: Migrera till powerbi-visuals-tools 3.x
description: Komma igång med den nya versionen av powerbi-visuals-tools
author: zBritva
ms.author: v-ilgali
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: cc554bff1cbd248ccd69a80ee47b60af981cdab1
ms.sourcegitcommit: f7b28ecbad3e51f410eff7ee4051de3652e360e8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2019
ms.locfileid: "74061832"
---
# <a name="migrate-to-the-new-powerbi-visuals-tools-3xx"></a>Migrera till nya powerbi-visuals-tools 3.x.x

Från och med version 3 använder Power BI:s verktyg för visuella objekt WebPack till att bygga anpassade visuella objekt.
I den nya versionen finns många nya möjligheter för utvecklare som skapar visuella objekt:

* TypeScript v3.x.x som standard. Starten från TypeScript 1.5-nomenklaturen har ändrats. [Läs mer om TypeScript-moduler](https://www.typescriptlang.org/docs/handbook/modules.html).

* ES6-moduler stöds. Du behöver inte använda [externalJS](migrate-to-new-tools.md#fix-loading-external-libraries) längre, använd ES6-importer i stället.

* Nya versioner av [D3v5](https://d3js.org/) och andra ES6-modulbaserade bibliotek stöds.

* Minskad paketstorlek. WebPack använder [Tree Shaking](https://webpack.js.org/guides/tree-shaking/) till att ta bort oanvänd kod. Den minskar koden i JS och ger bättre prestanda vid inläsning av visuella objekt.

* Förbättrad API-prestanda.

* Globalize.js-biblioteket [är integrerat](migrate-to-new-tools.md#remove-globalizejs-library) i formatting-utils.

* Verktygen använder [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) till att visa kodbasen för det visuella objektet.

Alla migreringssteg i den nya versionen av Power BI:s verktyg för visuella objekt beskrivs nedan.

## <a name="backward-compatibility"></a>Bakåtkompatibilitet

De nya verktygen sparar bakåtkompatibiliteten för kodbasen till gamla visuella objekt, men det kan krävas vissa ändringar om externa bibliotek ska läsas in.

Biblioteken stöder modulsystem och kommer att importeras som WebPack-moduler. Alla andra bibliotek och den visuella källkoden kommer att komprimeras till en modul.

De globala variablerna JQuery och Lodash som användes i tidigare pbiviz-verktyg är nu inaktuella. Det innebär att om det gamla koden för det visuella objektet använder globala variabler, kan det visuella objektet skadas.

Den tidigare versionen av Power BI:s verktyg för visuella objekt krävs för att kunna definiera en visuell klass under `powerbi.extensibility.visual`-modulen.

## <a name="how-to-install-powerbi-visuals-tools"></a>Så här installerar du powerbi-visuals-tools

De nya verktygen installeras genom att du kör kommandot

```cmd
npm install -g powerbi-visuals-tools
```

Exempel på ett visuellt sampleBarChart-objekt och motsvarande [ändringar](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L16) i `package.json`:

```json
{
    "name": "visual",
    "version": "1.2.3",
    "scripts": {
        "pbiviz": "pbiviz",
        "start": "pbiviz start",
        "lint": "tslint -r \"node_modules/tslint-microsoft-contrib\"  \"+(src|test)/**/*.ts\"",
        "test": "pbiviz package --resources --no-minify --no-pbiviz"
    },
    "devDependencies": {
      "@types/d3": "5.0.0",
      "d3": "5.5.0",
      "powerbi-visuals-tools": "^3.1.0",
      "tslint": "^4.4.2",
      "tslint-microsoft-contrib": "^4.0.0"
    }
}
```

## <a name="how-to-install-power-bi-custom-visuals-api"></a>Så här installerar du Power BI-API:et för anpassade visuella objekt

Den nya versionen av powerbi-visuals-tools innehåller inte alla API-versioner. I stället bör utvecklaren därför installera en specifik version av [`powerbi-visuals-api`](https://www.npmjs.com/package/powerbi-visuals-api)-paketet. Paketversionen matchar API-versionen för Power BI:s anpassade visuella objekt och innehåller alla typdefinitioner till Power BI-API:et för anpassade visuella objekt.

Lägg till `powerbi-visuals-api` i dina projektberoenden genom att köra kommandot `npm install --save-dev powerbi-visuals-api`.
Du bör även ta bort länken till gamla definitioner av API-typen. Typer från `powerbi-visuals-api` inkluderas automatiskt av WebPack. Motsvarande ändringar finns på [den här](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/package.json#L14) raden i `package.json`.

## <a name="update-tsconfigjson"></a>Uppdatera `tsconfig.json`

Om du vill använda externa moduler bör du byta `out`-alternativet till `outDir`.
`"outDir": "./.tmp/build/",` i stället för `"out": "./.tmp/build/visual.js",`.

Detta är nödvändigt eftersom TypeScript-filerna kommer att kompileras till JavaScript-filer oberoende av varandra. Det är därför du inte längre behöver ange filen visual.js som utdata.

Du kan också ändra `target`-alternativet till `ES6` om du vill använda modern JavaScript som utdata. [Det är valfritt](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/tsconfig.json#L6).

## <a name="update-custom-visuals-utils"></a>Uppdatera verktyg för anpassade visuella objekt

Om du använder [powerbi-visuals-utils](https://www.npmjs.com/search?q=powerbi-visuals-utils) bör du även uppdatera dem till den senaste versionen.

Kör kommandot `npm install powerbi-visuals-utils-<UTILNAME> --save`. (Exempelvis `npm install powerbi-visuals-utils-dataviewutils --save`) för att hämta den nya versionen med externa moduler av TypeScript.

Det finns exempel på [lagringsplatsen](https://github.com/Microsoft/powerbi-visuals-mekkochart) för MekkoChart.
Det här visuella objektet använder alla verktyg.

## <a name="remove-globalizejs-library"></a>Ta bort Globalize.js-biblioteket

Globalize.js finns redan i den nya versionen av [powerbi-visuals-utils-formattingutils@4.3](https://www.npmjs.com/package/powerbi-visuals-utils-formattingutils).
Du behöver inte inkludera det här biblioteket manuellt i projektet.
Alla obligatoriska lokaliseringar kommer att läggas till i det slutliga paketet automatiskt.

## <a name="fix-loading-external-libraries"></a>Åtgärda inläsning av externa bibliotek

Inkludera en ny JS-fil i stället efter biblioteken i `externalJS`-matrisen för `pbiviz.json`. Exempel:

```JSON
"externalJS": [
    ...
    "node_modules/lodash/lodash.min.js",
    "externalJS/init.lodash.js",
    ...
]
```

Importera bibliotek till källan. Exempel på `lodash-es`:

```JS
import * as _ from "lodash-es";
```

där `_` är en global variabel för `lodash`-biblioteket.

## <a name="changes-in-the-visuals-sources"></a>Ändringar i de visuella objektens källor

Huvudändringen konverterar interna moduler till externa moduler, eftersom du inte kan använda externa moduler i interna moduler.

Ändringarna beskriver modifieringar som har tillämpats på stapeldiagram

Detaljerade ändringsbeskrivningar visas nedan:

1. Ta bort alla moduldefinitioner från varje fil med [källkod](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L153)

    ```typescript
    module powerbi.extensibility.visual {
        ...
    }
    ```

2. [Importera API-definitioner för ett anpassat visuellt objekt i Power BI](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L2).

    ```typescript
    import powerbi from "powerbi-visuals-api";
    ```

3. [Importera](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L12-L23) nödvändiga gränssnitt eller klasser från en intern `powerbi`-modul.

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

4. [Importera](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L1) D3.js-biblioteket

    ```typescript
    import * as d3 from "d3";
    ```

    Eller importera endast de d3-biblioteksmoduler som krävs

    ```typescript
    import { max, min } from "d3-array";
    ```

5. [Importera](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/src/barChart.ts#L4-L10) verktyg, klasser och gränssnitt som har definierats i det visuella projektet till huvudkällans fil

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

Med den nya verktygsversionen kan utvecklare importera CSS- och LESS-format direkt till TypeScript-koden.

Därför kommer de [formatavsnitt](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L22) som använts tidigare att ignoreras av kompileraren.

Om du vill använda din formatmall öppnar du ts-huvudfilen och lägger till följande rad:  

```typescript
import "./../style/visual.less";
```  

Dina CSS- och LESS-format kompileras automatiskt.  

### <a name="externaljs-section-in-pbivizjson"></a>externalJS-avsnittet i pbiviz.json

Verktygen [kräver inte](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/sample-next/pbiviz.json#L20) någon lista med `externalJS` som ska läsas in i det visuella objektpaketet. WebPack innehåller alla importerade bibliotek.

**Avsnittet för externalJS i pbivi.json ska vara tomt.**

Anropa vanliga `npm run package`-kommandon för att skapa det visuella paketet, eller `npm run start` för att starta utvecklingsservern.

## <a name="updating-d3js-library-to-version-5"></a>Uppdatera D3.js-biblioteket till version 5

Med de nya verktygen kan du börja använda den nya versionen av D3.js-biblioteket.

Anropskommandon för att uppdatera D3 i ditt visuella projekt

`npm install --save d3@5` för att installera nya D3.js.

`npm install --save-dev @types/d3@5` för att installera nya typdefinitioner för D3.js.

Det finns flera icke-bakåtkompatibla ändringar och du bör ändra koden för att kunna använda nya D3.js.

1. Gränssnittet `d3.Selection<T>` [har ändrats](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR157) till `Selection<GElement extends BaseType, Datum, PElement extends BaseType, PDatum>`

2. Du kan inte tillämpa flera attribut med ett enda anrop för `attr`-metoden. Du [bör skicka](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR278) varje attribut i ett eget anrop med `attr`-metoden. Det är [ungefär likadant](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/af2ff9fb0fc70bd94ea0c604d75a362411d5abeb#diff-433142f7814fee940a0ffc98dc75bfcbR247) för `style`-metoden.

3. I D3.js v4 finns en ny sammanslagningsmetod. Den här metoden används ofta för att sammanfoga retur- och uppdateringsval efter en datakoppling. [Anropa sammanslagningsmetoden](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/83fe8d52d362dccd0034dd8e32c94080d9376b29#diff-433142f7814fee940a0ffc98dc75bfcbR272) för att använda D3 på rätt sätt.

[Läs mer](https://github.com/d3/d3/blob/master/CHANGES.md) om ändringar i D3.js-biblioteket.

## <a name="babel"></a>Babel

Från och med version 3.1 använder verktygen Babel för att kompilera ny modern JS-kod till gamla ES5 och kunna stödja många olika webbläsare.

Det här alternativet är aktiverat som standard, men du måste importera [`@babel/polyfill`](https://babeljs.io/docs/en/babel-polyfill)-paketet manuellt.

Kör kommandot för att installera paketet

`npm install --save @babel/polyfill`

och importera paketet vid startpunkten för den visuella objektkoden (vanligtvis filen ”src/visual.ts”):

`import "@babel/polyfill";`

Läs mer om Babel [i dokumenten](https://babeljs.io/docs/en/).

Kör slutligen [webpack-visualizer](https://github.com/chrisbateman/webpack-visualizer) för att visa kodbasen till det visuella objektet.  

![Statistik över visuella koder](./media/webpack-stats.png)
