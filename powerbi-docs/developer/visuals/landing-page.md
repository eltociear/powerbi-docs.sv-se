---
title: Lägga till en landningssida för visuella Power BI-objekt
description: I den här artikeln beskrivs hur du lägger till en landningssida för visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 6f1590d5635ed6e55833350027c52379e5d7cf51
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79379980"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>Lägga till en landningssida för visuella Power BI-objekt

Med API-version 2.3.0 kan du lägga till en landningssida för visuella Power BI-objekt. Det gör du genom att lägga till `supportsLandingPage` i funktionerna och ange det till true (sant). Den här åtgärden initierar och uppdaterar det visuella objektet innan du lägger till data i det. Eftersom det visuella objektet inte längre visar någon vattenstämpel kan du designa din egen landningssida som ska visas i det visuella objektet så länge det inte innehåller några data.

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

Ett exempel på en landningssida visas i följande bild:

![skärmbild av landningssida](media/landing-page/app-landing-page.png)
