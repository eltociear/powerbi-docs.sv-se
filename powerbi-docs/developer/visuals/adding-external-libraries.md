---
title: Lägga till externa bibliotek i visuella objekt för Power BI
description: I den här artikeln beskrivs hur du använder externa bibliotek i visuella objekt för Power BI.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 02/24/2020
ms.openlocfilehash: 13d5f2ed62ddefb8ac99fe2c91c72fc599a15936
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78922515"
---
# <a name="adding-external-libraries"></a>Lägga till externa bibliotek

I den här artikeln beskrivs hur du använder externa bibliotek i visuella objekt för Power BI. Den innehåller information om hur du installerar, importerar och anropar externa bibliotek från koden för visuella objekt för Power BI.

## <a name="javascript-libraries"></a>JavaScript-bibliotek

1. Installera ett externt JavaScript-bibliotek med valfri pakethanterare som *npm* eller *yarn*.
2. Importera de nödvändiga modulerna till källfilerna med hjälp av det externa biblioteket.

>[!NOTE]
>Om du vill lägga till text i JavaScript-biblioteket och få IntelliSense- och kompileringssäkerhet’ måste du installera rätt paket.

### <a name="installing-the-d3-library"></a>Installera d3-biblioteket

Detta är ett exempel på hur du installerar [d3-biblioteket](https://www.npmjs.com/package/d3) och [@types/d3](https://www.npmjs.com/package/@types/d3)-paketet med [npm](https://www.npmjs.com/).

Ett fullständigt exempel finns i koden för [visuella Power BI-objekt](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29).

1. Installera *d3*-paketet och *d3-textpaketet*.

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. Importera *d3*-biblioteket i de filer som använder den, till exempel `visual.ts`.

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS framework

1. Installera ett externt CSS-bibliotek med valfri pakethanterare som *npm* eller *yarn*.
2. Ta med instruktionen `import` i filen `.less` för det visuella objektet.

### <a name="installing-bootstrap"></a>Installerar bootstrap

Det här är ett exempel på hur du installerar [bootstrap-](https://www.npmjs.com/package/bootstrap) med [npm](https://www.npmjs.com/).

Ett fullständigt exempel finns i koden för [visuella Power BI-objekt](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32).

1. Installera *bootstrap*-paketet.

    ```powershell
    npm install bootstrap --save
    ```

2. Ta med instruktionen `import` i `visual.less`.

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
