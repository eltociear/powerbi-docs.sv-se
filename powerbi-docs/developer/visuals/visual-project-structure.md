---
title: Struktur för projekt med visuella Power BI-objekt
description: I den här artikeln beskrivs mappen och filstrukturen för ett visuellt Power BI-projekt
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 2db9cdcb1238b5f26a34cf652f8f614411c2992b
ms.sourcegitcommit: 6bbc3d0073ca605c50911c162dc9f58926db7b66
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79379053"
---
# <a name="power-bi-visual-project-structure"></a>Struktur för projekt med visuella Power BI-objekt

Det bästa sättet att börja skapa ett nytt visuellt Power BI-objekt är att använda verktyget [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) för visuella Power BI-objekt.

Om du vill skapa ett nytt visuellt objekt går du till den katalog som du vill att det visuella Power BI-objektet ska finnas i och kör kommandot:

`pbiviz new <visual project name>`

Om du kör det här kommandot skapas en mapp för visuella Power BI-objekt som innehåller följande filer:

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>Beskrivning av mapp och fil

Det här avsnittet innehåller information om varje mapp och fil i katalogen som verktyget **pbiciz** för visuella Power BI-objekt skapar.  

### <a name="vscode"></a>.vscode

Den här mappen innehåller projektinställningar för VS-kod.

Konfigurera din arbetsyta genom att redigera filen `.vscode/settings.json`.

Mer information finns i [Inställningar för användare och arbetsytor](https://code.visualstudio.com/docs/getstarted/settings)

### <a name="assets"></a>tillgångar

Den här mappen innehåller filen `icon.png`.

Verktyget för visuella Power BI-objekt använder den här filen som ny ikon för visuella Power BI-objekt i fönstret för visuella Power BI-objekt.

### <a name="src"></a>src

Mappen innehåller källkoden för det visuella objektet.

I den här mappen skapar verktyget för visuella Power BI-objekt följande filer:
* `visual.ts` – den huvudsakliga källkoden för det visuella objektet.
* `settings.ts` – koden för inställningarna för det visuella objektet. Klasserna i filen innehåller ett gränssnitt för att definiera [det visuella objektets egenskaper](./objects-properties.md#properties).

### <a name="style"></a>stil

Den här mappen innehåller filen `visual.less` som innehåller det visuella objektets format.

### <a name="capabilitiesjson"></a>capabilities.json

Filen innehåller huvudegenskaperna och inställningarna (eller [kapaciteten](./capabilities.md)) för det visuella objektet. Det gör att visuella objekt kan deklarera funktioner, objekt, egenskaper och [datavymappning](./dataview-mappings.md) som stöds.

### <a name="package-lockjson"></a>package-lock.json

Filen genereras automatiskt för alla åtgärder där *npm* ändrar antingen trädet `node_modules` eller filen `package.json`.

Mer information om den här filen finns i den officiella dokumentationen om [NPM-Package-lock.json](https://docs.npmjs.com/files/package-lock.json).

### <a name="packagejson"></a>package.json

Den här filen beskriver projektpaketet. Vanligtvis innehåller den information om projektet, författarna, beskrivningen och projektets beroenden.

Mer information om den här filen finns i den officiella dokumentationen om [npm-Package.json](https://docs.npmjs.com/files/package.json.html).

### <a name="pbivizjson"></a>pbiviz.json

Den här filen innehåller metadata om det visuella objektet.

Om du vill visa en `pbiviz.json`-exempelfil med kommentarer som beskriver metadataposterna, se avsnittet [metadata-poster](#metadata-entries).

### <a name="tsconfigjson"></a>tsconfig.json

En konfigurationsfil för [TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

Filen måste innehålla sökvägen till filen **\*.ts** där det visuella objektets huvudklass finns enligt specifikation i egenskapen `visualClassName` i filen `pbiviz.json`.

### <a name="tslintjson"></a>tslint.json

Filen innehåller [TSLint-konfiguration](https://palantir.github.io/tslint/usage/configuration/).

## <a name="metadata-entries"></a>Metadata-poster

Kommentarerna i följande kodtext från `pbiviz.json`-filen beskriver metadata-posterna.

> [!NOTE]
> * Från version 3.x.x av verktyget **pbiviz** stöds inte `externalJS`.
> * [Lägg till Power BI-språkvarianten till ditt visuella objekt](./localization.md) för lokaliseringsstöd.

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>Nästa steg

* Information om interaktionen mellan ett visuellt objekt, en användare och Power BI finns i [Begrepp för visuella Power BI-objekt](./power-bi-visuals-concept.md).

* Börja utveckla egna visuella Power BI-objekt från början [med en stegvis guide](./custom-visual-develop-tutorial.md).
