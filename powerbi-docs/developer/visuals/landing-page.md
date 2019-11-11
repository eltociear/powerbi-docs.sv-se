---
title: Lägga till en landningssida för visuella Power BI-objekt
description: I den här artikeln beskrivs hur du lägger till en landningssida för visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: fdf9496c564372e385879b3e0a3feb392d10ff90
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879992"
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

![skärmbild av landningssida](./media/landing-page.png)
