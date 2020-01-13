---
title: Struktur för projekt med visuella Power BI-objekt
description: I artikeln beskrivs en struktur för projekt med visuella objekt
author: zBritva
ms.author: v-ilgali
ms.reviewer: ''
ms.service: powerbi
ms.topic: tutorial
ms.subservice: powerbi-custom-visuals
ms.date: 03/15/2019
ms.openlocfilehash: 728aba749f80710fdc0bb1e180b3318e63caa88c
ms.sourcegitcommit: 331ebf6bcb4a5cdbdc82e81a538144a00ec935d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/28/2019
ms.locfileid: "75542103"
---
# <a name="power-bi-visual-project-structure"></a>Struktur för projekt med visuella Power BI-objekt

När pbiviz new `<visual project name>` har körts skapar verktyget en grundläggande struktur för filer och mappar i mappen `<visual project name>`.

## <a name="visual-project-structure"></a>Struktur för projekt med visuella objekt

![Struktur för projekt med visuella objekt](./media/visual-project-structure.png)

* `.vscode` – innehåller inställningar för projekt för VS Code. Konfigurera din arbetsyta genom att redigera filen `.vscode/settings.json`. Läs mer [om VS Code-inställningar i dokumentationen](https://code.visualstudio.com/docs/getstarted/settings)

* Mappen `assets` innehåller bara filen `icon.png`. Verktyget använder den här filen som ikon för det visuella objektet i fönstret Visualisering i Power BI.

    ![Fönstret Visualisering](./media/visualization-pane-analytics-tab.png)

* Mappen `node_modules` innehåller alla paket [som installerats av Node Pack Manager](https://docs.npmjs.com/files/folders.html).

* Mappen `src` innehåller källkoden för det visuella objektet. Som standard skapar verktyget två filer:

  * `visual.ts` – den huvudsakliga källkoden för det visuella objektet.

  * `settings.ts` – koden för inställningarna för det visuella objektet. Klasserna i filen förenklar [arbetet med egenskaperna för de visuella objekten](./objects-properties.md#properties).

* Mappen `style` innehåller filen `visual.less` med format för det visuella objektet.

* Filen `capabilities.json` innehåller huvudegenskaperna och inställningarna för det visuella objektet. Det gör att visuella objekt kan deklarera funktioner, objekt, egenskaper och datavymappning som stöds.

    Läs mer [om funktioner i dokumentationen](./capabilities.md).

* `package-lock.json` genereras automatiskt för alla åtgärder där NPM ändrar antingen trädet `node_modules` eller `package.json`.

    Läs mer [om `package-lock.json` i den officiella dokumentationen för NPM](https://docs.npmjs.com/files/package-lock.json).

* `package.json` beskriver projektpaketet. Vanligtvis innehåller den information om projektet, författarna, beskrivningen och projektets beroenden.

    Läs mer [om `package.json` i den officiella dokumentationen för NPM](https://docs.npmjs.com/files/package.json.html).

* `pbiviz.json` innehåller metadata om det visuella objektet. Ange metadata om det visuella objektet i den här filen.

    Vanligt innehåll i filen:

  ```json
    {
        "visual": {
            "name": "<visual project name>",
            "displayName": "<visual project name>",
            "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",
            "visualClassName": "Visual",
            "version": "1.0.0",
            "description": "",
            "supportUrl": "",
            "gitHubUrl": ""
        },
        "apiVersion": "2.6.0",
        "author": { "name": "", "email": "" },
        "assets": { "icon": "assets/icon.png" },
        "externalJS": null,
        "style": "style/visual.less",
        "capabilities": "capabilities.json",
        "dependencies": null,
        "stringResources": []
    }
  ```

    där

  * `name` – det visuella objektets interna namn.

  * `displayName` – det visuella objektets namn i användargränssnittet i Power BI.

  * `guid` – det visuella objektets unika ID.

  * `visualClassName` – det visuella objektets huvudklass. Power BI skapar instansen av den här klassen för att börja använda det visuella objektet i Power BI-rapporten.

  * `version` – det visuella objektets versionsnummer.

  * `author` – innehåller författarens namn och e-postadress.

  * `icon` i `assets` – sökvägen till det visuella objektets ikonfil.

  * `externalJS` innehåller sökvägar för JS-bibliotek som används i det visuella objektet.

    > [!IMPORTANT]
    > Den senaste versionen av verktyget 3.x.x eller senare använder inte längre `externalJS`.

  * `style` är sökvägen till formatfiler.

  * `capabilities` är sökvägen till filen `capabilities.json`.

  * `dependencies` är sökvägen till filen `dependencies.json`. `dependencies.json` innehåller information om R-paket som används i R-baserade visuella objekt.

  * `stringResources` är en matris med sökvägar till filer med lokaliseringar.

  Läs mer [om lokalisering i visuella objekt i dokumentationen](./localization.md)

* `tsconfig.json` är konfigurationsfilen för TypeScript.

    Läs mer [om TypeScript-konfiguration i den officiella dokumentationen](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

    `tsconfig.json` i avsnittet `files` måste innehålla sökvägen till filen *.ts där det visuella objektets huvudklass finns enligt specifikation i egenskapen `visualClassName` i filen `pbiviz.json`.

* Filen `tslint.json` innehåller TSLint-konfiguration.

    Läs mer [om TSLint-konfiguration i den officiella dokumentationen](https://palantir.github.io/tslint/usage/configuration/)

## <a name="next-steps"></a>Nästa steg

* Läs mer [om begrepp för visuella objekt](./power-bi-visuals-concept.md) för att få mer kunskap om hur visuella objekt, användare och Power BI interagerar med varandra.

* Börja utveckla egna visuella Power BI-objekt från början [med en stegvis guide](./custom-visual-develop-tutorial.md).
