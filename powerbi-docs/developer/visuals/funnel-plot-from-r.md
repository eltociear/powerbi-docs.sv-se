---
title: Skapa ett trattdiagram från R-skript till visuellt R-objekt
description: Den här artikeln beskriver hur du skapar en trattritning med ett R-skript och ett visuellt Power BI-baserat R-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: tutorial
ms.date: 04/02/2020
ms.openlocfilehash: 2cc37d1296d7f170bf8c6280465e7a3f1aa52e33
ms.sourcegitcommit: 0d0ab427bb71b37c9e5170c515a8f274e1f20c17
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87878689"
---
# <a name="tutorial-build-a-funnel-plot-from-r-script-to-r-visual"></a>Självstudie: Skapa ett trattdiagram från R-skript till visuellt R-objekt
Den här artikeln beskriver steg för steg hur du skapar en trattritning med ett R-skript och ett visuellt R-objekt.

I den här artikeln lär du dig hur du skapar:

> [!div class="checklist"]
>
> * ett R-skript för RStudio
> * ett visuellt R-objekt i Power BI
> * ett *PNG-baserat* visuellt R-objekt i Power BI
> * ett *HTML-baserat* visuellt R-objekt i Power BI

En trattritning är ett enkelt sätt att använda, tolka och visa mängden förväntad variation. **Tratten** formas med hjälp av konfidensgränser och avvikande värden visas som punkter utanför tratten.

I det här exemplet används trattritningen för att jämföra och analysera olika uppsättningar med data.  

> [!NOTE]
> Källfiler finns tillgängliga för nedladdning i varje uppsättning steg.

## <a name="build-an-r-script-with-dataset"></a>Skapa ett R-skript med datauppsättning

1. Ladda ned ett [minimalt R-skript](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_00.r) och tillhörande datatabell, [dataset.csv](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/dataset.csv).

1. Redigera sedan skriptet så att det avspeglar [det här skriptet](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter1_R/script_R_v1_01.r). Med den här ändringen lägger du till hantering av inmatningsfel och användarparametrar som styr ritytans utseende.

## <a name="build-a-report"></a>Skapa en rapport

Redigera sedan skriptet så att det avspeglar [det här skriptet](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/script_RV_v2_00.r). Med den här ändringen kommer *dataset.csv* att läsas in i stället för *read.csv* på Power BI Desktop-arbetsytan, och tabellen **Cancer Mortality** (Dödlighet vid cancer) skapas. Se resultatet i följande [PBIX-fil](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter2_Rvisual/funnelPlot_Rvisual.pbix).

> [!NOTE]
> `dataset` är ett hårdkodat namn för `data.frame`-inmatningen för visuella R-objekt. 

## <a name="create-an-r-powered-visual-and-package-in-r-code"></a>Skapa ett R-baserat visuellt objekt och paket i R-kod

1. [Installera PBIVIZ-verktyg](./custom-visual-develop-tutorial.md#installing-packages) innan du börjar.

1. Kör följande kommando för att skapa ett nytt R-baserat visuellt objekt:

   ```bash
   pbiviz new funnel-visual -t rvisual
   cd funnel-visual
   npm install 
   pbiviz package
   ```

   Med det här kommandot skapas mappen *funnel-visual* med en första mallvisualisering (där `-t` står för **template**, dvs. mall). Du hittar PBIVIZ i mappen *dist* och R-koden i filen *script.r*. Prova att importera den till Power BI och se vad som händer.

1. Redigera filen *script.r* och ersätt innehållet med ditt tidigare skript.

1. Redigera *capabilities.json* och ersätt strängen `Values` med `dataset`. Med den här ändringen ersätts ”Role”-namnet i mallen så att det avspeglar namnet i R-koden.

   ![före och efter](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/capabilities-changes.PNG)

1. *(valfritt)* Redigera *dependencies.json* och lägg till ett avsnitt för varje R-paket som krävs av R-skriptet. Genom att göra detta beordrar du Power BI att automatiskt importera paketen första gången det visuella objektet läses in.

   ![före och efter](./samples/funnel-plot/chapter-3/funnel-r-visual-v01/dependencies-changes.PNG)

1. Paketera om det visuella objektet med kommandot `pbiviz package` och prova att importera det till Power BI.

> [!NOTE]
> Se [PBIX](https://github.com/microsoft/PowerBI-visuals/blob/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) och [källkoden](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v01/) för nedladdningen.

## <a name="make-r-based-visual-improvements"></a>Förbättra det R-baserade visuella objektet

Det visuella objektet är inte särskilt användarvänligt än eftersom användaren måste känna till kolumnordningen i indatatabellen.

1. Dela in indatafältet `dataset` i tre fält (roller): `Population`, `Number` och `Tooltips`

   ![CV01to02](./media/funnel-plot/diagram-one.PNG)

1. Redigera *capabilities.json* och ersätt rollen `dataset` med de tre nya rollerna, eller ladda ned [capabilities.json](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/capabilities.json).

   Du måste uppdatera avsnitten `dataRoles` och `dataViewMappings`, som definierar namn, typer, knappbeskrivningar och maximalt antal kolumner för varje indatafält.

   ![före och efter](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/capabilities-before-vs-after.png)
   
   Mer information finns i avsnittet om [funktioner](./capabilities.md).

1. Redigera *script.r* för att ge stöd för `Population`, `Number` och `Tooltips` som dataframes för inmatning i stället för `dataset`, eller ladda ned [script.r](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02/script.r).

   ![skript](./samples/funnel-plot/chapter-3/funnel-r-visual-v02/script-r-before-vs-after.png)

   > [!TIP]
   > Om du vill följa ändringarna i R-skriptet söker du efter kommentarsblock: 
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Added to enable visual fields
   > ...
   > #RVIZ_IN_PBI_GUIDE:END: Added to enable visual fields
   > 
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields 
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN: Removed to enable visual fields
   > ```

1. Paketera om det visuella objektet med kommandot `pbiviz package` och prova att importera det till Power BI.

> [!NOTE]
> Se [PBIX](https://github.com/microsoft/PowerBI-visuals/raw/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) och [källkoden](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v02) för nedladdningen.

## <a name="add-user-parameters"></a>Lägga till användarparametrar

1. Lägg till funktioner som gör att användaren kan styra färgerna och storleken på visuella element, inklusive interna parametrar från användargränssnittet.

   ![CV02to03](./media/funnel-plot/diagram-two.PNG)

1. Redigera *capabilities.json* och uppdatera avsnittet `objects`. Här definierar vi namn, knappbeskrivningar och parametertyperna och bestämmer även partitioneringen av parametrar i grupper (tre grupper i det här fallet).

   ladda ned [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/capabilities.json); mer information finns i avsnittet om [objektegenskaper](./objects-properties.md)

   ![funktioner](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/capabilities-before-after.PNG)

1. Redigera *src/settings.ts* så att det avspeglar [settings.ts](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/src/settings.ts). Den här filen är skriven i TypeScript.  

   Här hittar du två kodblock av koden som lagts till i:
   - Deklarera ett nytt gränssnitt för att lagra egenskapsvärdet
   - Definiera en medlemsegenskap och standardvärden

   ![inställningar](./samples/funnel-plot/chapter-3/funnel-r-visual-v03/settings-ts-before-after.PNG)

1. Redigera *script.r* så att det avspeglar detta [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script.r). Den här ändringen lägger till stöd för parametrar i användargränssnittet genom att lägga till `if.exists`-anrop per användarparameter.

   > [!TIP]
   > Om du vill följa ändringarna i R-skriptet söker du efter kommentarer:
   >
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to enable user parameters
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Added to enable user parameters
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to enable user parameters 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:END:Removed to enable user parameters
   > ```

   ![skript före och efter](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/script_r_before_after_1.png)

   Du kan välja att inte exponera parametrarna för användargränssnittet, som vi gjorde.  

1. Paketera om det visuella objektet med kommandot `pbiviz package` och prova att importera det till Power BI.

> [!NOTE]
> Se [PBIX](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelPlot_RCustomVisual.pbix) och [källkoden](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter3_RCustomVisual/funnelRvisual_v03/) för nedladdningen.

> [!TIP]
> Här har vi lagt till olika typer av parametrar (booleska, numeriska, sträng och färg) samtidigt. Ett enkelt exempel som illustrerar hur du lägger till en enstaka parameter finns [här](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/PropertiesPane.md). 

## <a name="convert-visual-to-rhtml-based-visual"></a>Konvertera ett visuellt objekt till ett RHTML-baserat visuellt objekt

Eftersom det resulterande visuella objektet är PNG-baserat, svarar det inte på muspekaren, kan inte zoomas in och så vidare. Så, vi måste konvertera det till ett HTML-baserat visuellt objekt. Vi ska skapa en tom mall för ett HTML-baserat visuellt R-objekt och sedan kopiera några skript från det PNG-baserade projektet.

1. Kör kommandot:

   ```bash
   pbiviz new funnel-visual-HTML -t rhtml
   cd funnel-visual-HTML
   npm install 
   pbiviz package
   ```

1. Öppna *capabilities.json* och notera raden `"scriptOutputType":"html"`.

1. Öppna *dependencies.json* och notera namnen på R-paketen som visas.

1. Öppna *script.r* och notera strukturen. Du kan öppna och köra det i RStudio eftersom det inte använder externa indata. 

   *out.html* skapas och sparas. Den här filen är fristående (utan externa beroenden) och definierar grafiken inuti HTML-widgeten. 

   > [!IMPORTANT]
   > `htmlWidgets`-användare hittar R-verktyg i [mappen r_files](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files) som hjälper dem att konvertera `plotly`- eller `widget`-objekt till fristående HTML. 
   > 
   > Den här versionen av det R-baserade visuella objektet stöder också kommandot `source` (till skillnad från tidigare typer av visuella objekt) så att koden blir lättare att läsa.   
 
1. Ersätt *capabilities.json* med *capabilities.json* i det föregående steget, eller ladda ned [capabilities.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/capabilities.json).

   Behåll:

   `"scriptOutputType": "html"`

1. Slå ihop den senaste versionen av *script.r* med *script.r* från mallen, eller ladda ned [script.r](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/script.r).

   Det nya skriptet använder `plotly`-paketet för att konvertera **ggplot**-objektet till ett **plotly**-objekt, och sedan `htmlWidgets`-paketet för att spara det till en HTML-fil. 

   De flesta verktygsfunktionerna flyttas till [_r_files/utils.r_](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/r_files/utils.r) och `generateNiceTooltips`-funktionen läggs till för utseendet av **plotly**-objektet.

   ![1](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-1.PNG)
   
   ![2](./samples/funnel-plot/chapter-4/RHTML-v01/script-before-after-2.PNG)

   > [!TIP]
   > Om du vill följa ändringarna i R-skriptet söker du efter kommentarer:
   > 
   > ```r
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based 
   >  ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Added to create HTML-based
   >
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based  
   > ...
   > #RVIZ_IN_PBI_GUIDE:BEGIN:Removed to create HTML-based
   > ```

1. Slå ihop den senaste versionen av *dependencies.json* med *dependencies.json* från mallen, för att lägga till nya R-paketberoenden, eller ladda ned [dependencies.json](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/dependencies.json).

1. Redigera *src/settings.ts* på samma sätt som i föregående steg.

1. Paketera om det visuella objektet med kommandot `pbiviz package` och prova att importera det till Power BI.

> [!NOTE]
> Se [PBIX och källkoden](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01) för nedladdningen.

## <a name="build-additional-examples"></a>Skapa ytterligare exempel

1. Kör följande kommando för att skapa ett tomt projekt: 

   ```bash
   pbiviz new example -t rhtml
   cd example
   npm install 
   pbiviz package
   ```

1. Använd kod från den här [demonstrationen](http://www.htmlwidgets.org/showcase_networkD3.html) och utför de markerade ändringarna:

   ![Markerade ändringar](./media/funnel-plot/diagram-three.PNG)

1. Ersätt din malls *script.r* och kör `pbiviz package` igen. Nu tas det visuella objektet med i din Power BI-rapport!

## <a name="tips-and-tricks"></a>Tips

* Vi rekommenderar att utvecklare redigerar *pbiviz.json* för att lagra rätt metadata, t.ex. **version**, **e-postadress**, **namn**, **licenstyp** och så vidare.

   > [!IMPORTANT]
   > Fältet **guid** är den unika identifieraren för ett visuellt objekt. Om du skapar ett nytt projekt för varje visuellt objekt, kommer objekten att ha olika GUID. Det är bara samma om du använder ett gammalt projekt som kopierats till ett nytt visuellt objekt, vilket du inte bör göra.

* Redigera [*assets/icon.png*](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/funnelRHTMLvisual_v01/assets/icon.png) om du vill skapa unika ikoner för ditt visuella objekt. 

* Du kan felsöka R-kod i RStudio med hjälp av samma data som i din Power BI-rapport genom att lägga till följande i början av R-skriptet (redigera `fileRda`-variabeln):

   ```r
   #DEBUG in RStudio
   fileRda = "C:/Users/yourUserName/Temp/tempData.Rda"
   if(file.exists(dirname(fileRda)))
   {
     if(Sys.getenv("RSTUDIO")!="")
       load(file= fileRda)
     else
       save(list = ls(all.names = TRUE), file=fileRda)
   }
   ```

   Med den här ändringen sparas miljön från en Power BI-rapport och läses in i RStudio. 

* Du behöver inte utveckla R-baserade visuella objekt från grunden. Du kan använda kod som finns på [GitHub](https://github.com/Microsoft?utf8=%E2%9C%93&q=PowerBI&type=&language=R). Du kan välja det visuella objekt som du vill använda som mall och kopiera koden till ett nytt projekt.

   Prova till exempel att använda det [anpassade visuella Spline-objektet](https://github.com/Microsoft/PowerBI-visuals-spline).

* Varje visuellt R-objekt använder `unique`-operatorn i sin indatatabell. Om du vill undvika att identiska rader tas bort kan du lägga till ett extra indatafält med ett unikt ID och ignorera det i R-koden.   

* Om du har ett Power-BI konto kan du använda Power BI-tjänsten för att utveckla ett visuellt objekt [direkt](/power-bi/developer/visuals/custom-visual-develop-tutorial/) i stället för att paketera om dem med kommandot `pbiviz package`.

### <a name="html-widgets-gallery"></a>HTML-widgetgalleri
Utforska visuella objekt i [HTML-widgetgalleriet](http://gallery.htmlwidgets.org/) som du kan använda med ditt nästa visuella objekt. För att göra det enkelt har vi skapat en [lagringsplats för visualiseringsprojekt](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML) med över 20 interaktiva HTML-visualiseringar som du kan välja bland!

> [!TIP]
> Du kan växla mellan HTML-widgetar via **Format** > **Inställningar** > **Typ**. Testa [den här PBIX-filen](https://github.com/Microsoft/PowerBI-visuals/tree/master/RVisualTutorial/TutorialFunnelPlot/chapter4_RHTMLCustomVisual/multipleRHTML/assets/sample.pbix). 

#### <a name="to-use-a-sample-for-your-visual"></a>Så här använder du ett exempel för ett visuellt objekt

1. Ladda ned hela mappen.
1. Redigera *script.r* och *dependencies.json* så att endast en widget finns kvar.
1. Redigera *capabilities.json* och *settings.ts* för att ta bort `Type`-väljaren.
1. Ändra `const updateHTMLHead: boolean = true;` till `false` i *visual.ts*. *(för bättre prestanda)*
1. Ändra metadata i *pbiviz.json*, framför allt fältet `guid`.
1. Paketera om och fortsätt att anpassa det visuella objektet efter önskemål. 

![CV02to03](./media/funnel-plot/diagram-four.PNG)

![CV02to03](./media/funnel-plot/diagram-five.PNG)

> [!NOTE]
> Alla widgetar i det här projektet stöds inte av tjänsten.

## <a name="next-steps"></a>Nästa steg

Mer information finns i andra självstudier om [visuella Power BI-objekt](./custom-visual-develop-tutorial.md) och [visuella R-objekt](/power-bi/visuals/service-r-visuals).

Lär dig hur du [utvecklar och skickar visuella objekt](https://powerbi.microsoft.com/documentation/powerbi-developer-office-store/) till [Office Store (galleri)](https://store.office.com/appshome.aspx?ui=en-US&rs=en-US&ad=US&clickedfilter=OfficeProductFilter%3aPowerBI&productgroup=PowerBI), eller utforska fler exempel i [R-skriptdemonstrationerna](https://community.powerbi.com/t5/R-Script-Showcase/bd-p/RVisuals)
