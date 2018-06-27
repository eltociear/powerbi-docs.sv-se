---
title: Anpassade layouter med Power BI-inbäddat innehåll
description: Lär dig mer om anpassade layouter vid inbäddning av Power BI-innehåll i programmet.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 12/19/2017
ms.author: maghan
ms.openlocfilehash: fc684ebdf6b1ccb53bdd7794b19c1120ece635a3
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34288140"
---
# <a name="custom-layouts"></a>Anpassade layouter


Du kan använda en anpassad layout för att bädda in en rapport med en layout som skiljer sig åt från den i en ursprunglig rapport. Att definiera en ny layout varierar mellan att definiera endast en sidstorlek, kontrollera visuella objekts storlekar eller placering och synlighet.

För att definiera en anpassad layout, definierar du ett anpassat layoutobjekt och skickar det till inställningsobjektet i en inbäddningskonfiguration. Sedan ställer du in LayoutType till Anpassad. Mer information finns i [Bädda in konfigurationsinformation](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details).

```javascript
var embedConfig = {
    ...
    settings: {
            layoutType: models.LayoutType.Custom
    customLayout: {...}
    }
};
```

## <a name="object-definition"></a>Objektdefinition

```javascript
interface ICustomLayout {
  pageSize?: IPageSize;
  displayOption?: DisplayOption;
  pagesLayout?: PagesLayout;
}

enum PageSizeType {
  Widescreen,
  Standard,
  Cortana,
  Letter,
  Custom
}
interface IPageSize {
  type: PageSizeType;
}
interface ICustomPageSize extends IPageSize {
  width?: number;
  height?: number;
}

enum DisplayOption {
  FitToPage,
  FitToWidth,
  ActualSize
}
```

- `pageSize`: Använd sidstorleken för att styra arbetsytans storlek (det vill säga rapportens vita område).
- `displayOptions`: Möjliga värden är: FitToWidth, FitToPage och ActualSize. Här styr du hur arbetsytan ska skalas för att passa iFrame.
- `pagesLayout`: Styr layouten för varje visuellt objekt. Mer information finns i PagesLayout.

## <a name="pages-layout"></a>Sidlayout

Att definiera ett sidlayoutsobjekt är i princip detsamma som att definiera en layout för varje sida och för varje sida en layout för varje visuellt objekt.
PageLayout är valfritt. Om du inte definierar en layout för en sida, används standardlayouten (som sparas i rapporten).

pagesLayout är en karta från sidnamn till PageLayout-objekt. Definition:

```javascript
type PagesLayout = { [key: string]: IPageLayout; };
```

PageLayout innehåller en visuell layoutkarta som mappar varje visuellt objekts namn till ett visuellt layoutobjekt:

```javascript
interface IPageLayout {
  visualsLayout: { [key: string]: IVisualLayout; };
}
```

## <a name="visual-layout"></a>Visuell layout

För att definiera en visuell layout, ställer du in en ny placering och storlek och ett nytt visningstillstånd.

```javascript
interface IVisualLayout {
  x?: number;
  y?: number;
  z?: number;
  width?: number;
  height?: number;
  displayState?: IVisualContainerDisplayState;
}

interface IVisualContainerDisplayState {
  mode: VisualContainerDisplayMode;
}

enum VisualContainerDisplayMode {
  Visible,
  Hidden
}
```

- `x,y,z`: Definierar det visuella objektets nya placering.
- `width`, höjd: Definierar det visuella objektets nya storlek.
- `displayState`: Definierar det visuella objektets synlighet.


## <a name="update-layout"></a>Uppdatera layouten

Du kan använda metoden updateSettings för att uppdatera rapportlayouten när som helst när rapporten läses in. Se [Uppdatera inställningarna](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Update-Settings).

## <a name="code-example"></a>Kodexempel

```javascript
// Get models. models contains enums that can be used.
var models = window['powerbi-client'].models;
    
var embedConfiguration = {
    type: 'report',
    id: '5dac7a4a-4452-46b3-99f6-a25915e0fe55',
    embedUrl: 'https://app.powerbi.com/reportEmbed',
    tokenType: models.TokenType.Embed,
    accessToken: 'H4...rf',
    settings: {
            layoutType: models.LayoutType.Custom
        customLayout: {
            pageSize: {
                type: models.PageSizeType.Custom,
                width: 1600,
                height: 1200
            },
            displayOption: models.DisplayOption.ActualSize,
            pagesLayout: {
                "ReportSection1" : {
                    visualsLayout: {
                        "VisualContainer1": {
                            x: 1,
                            y: 1,
                            z: 1,
                            width: 400,
                            height: 300,
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Visible
                            }
                        },
                        "VisualContainer2": {
                            displayState: {
                                mode: models.VisualContainerDisplayMode.Hidden
                            }
                        },
                    }
                }
            }
        }
    }
};
     
// Get a reference to the embedded report HTML element
var embedContainer = document.getElementById('embedContainer');
 
// Embed the report and display it within the div container.
var report = powerbi.embed(embedContainer, embedConfiguration);

```


## <a name="see-also"></a>Se också

[Bädda in dina Power BI-instrumentpaneler, -rapporter och -paneler](embedding-content.md)   
[Fråga Power BI Community](https://community.powerbi.com/)

