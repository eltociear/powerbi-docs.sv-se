---
title: Trädkartor i Power BI
description: Trädkartor i Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4c28071917dbe5669e6e35bd416236ef7047eb24
ms.sourcegitcommit: 58c649ec5fd2447a0f9ca4c4d45a0e9fff2f1b6a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67408757"
---
# <a name="treemaps-in-power-bi"></a>Trädkartor i Power BI

Trädkartor visar hierarkiska data som en uppsättning kapslade rektanglar. Varje nivå i hierarkin representeras av en färgad rektangel (gren) som innehåller mindre rektanglar (löv). Power BI baserar storleken på utrymmet i varje rektangel på det uppmätta värdet. Rektanglarna ordnas i storleksordning med de största överst till vänster och de minsta längst ned till höger.

![Skärmbild av trädkarta över antal produkter efter kategori och tillverkare.](media/power-bi-visualization-treemaps/pbi-nancy-viz-treemap.png)

Om du analyserar er försäljning kanske ni till exempel har grenar på högsta nivån för klädkategorierna **Staden**, **landet**, **ungdom** och **blandat**. Power BI skulle dela era kategorirektanglar i blad för klädtillverkarna i den här kategorin. Löven skulle få sin storlek och skuggning baserat på antalet sålda artiklar.

I grenen **Urbant** ovan, såldes massor av **VanArsdel**-kläder. Mindre med **Natura** och **Fama** såldes. Och bara några **Leo** såldes. Så, grenen **Urbant** i din trädkarta har

* den största rektangeln för **VanArsdel** i det övre vänstra hörnet

* något mindre rektanglar för **Natura** och **Fama**

* massor av andra rektanglar för alla andra sålda kläder

* en liten rektangel för **Leo**.

Du skulle kunna jämföra antalet sålda artiklar med de övriga klädkategorierna genom att jämföra storlek och färg för varje lövnod; ju större rektangel och ju mörkare färg, desto högre värde.

Vill du först se någon annan skapa en trädkarta? Hoppa till 2:10 i det här videoklippet och se Amanda skapa en trädkarta.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-treemap"></a>När du ska använda en trädkarta

Trädkartor är ett bra alternativ:

* för att visa stora mängder hierarkiska data

* när ett stapeldiagram inte på ett effektivt sätt kan hantera ett stort antal värden

* för att visa proportionerna mellan delarna och helheten

* för att visa distributionsmönstret för mätvärdena för varje nivå av kategorier i hierarkin

* för att visa attribut med hjälp av storlek och färgkodning

* för att upptäcka mönster, avvikande värden, de viktigaste bidragande faktorerna och undantag.

## <a name="prerequisites"></a>Förutsättningar

* Power BI-tjänsten eller Power BI Desktop

* Rapporten Exempel på detaljhandelsanalys

## <a name="get-the-retail-analysis-sample-report"></a>Hämta rapporten Exempel på detaljhandelsanalys

Dessa anvisningar använder sig av Exempel på detaljhandelsanalys. För att skapa en visualisering krävs behörighet att redigera datauppsättningen och rapporten. Som tur är kan alla Power BI-exemplen redigeras. Om någon delar en rapport med dig, kan du inte skapa visualiseringar i rapporter. Om du vill följa med, kan du hämta [rapporten Exempel på detaljhandelsanalys](../sample-datasets.md).

När du har hämtat datamängden **Exempel på detaljhandelsanalys** kan du sätta igång.

## <a name="create-a-basic-treemap"></a>Skapa en grundläggande trädkarta

Du skapar en rapport och lägger till en grundläggande trädkarta.

1. Från **Min arbetsyta** väljer du **Datamängder** > **Skapa en rapport**.

    ![Skärmbild av Datamängder > Skapa en rapport.](media/power-bi-visualization-treemaps/power-bi-create-a-report.png)

1. I fönstret **Fält** väljer du måtten **Försäljning**  >  **Senaste årets försäljning**.

   ![Skärmbild av Försäljning > Senaste årets försäljning valt och det resulterande visuella objektet.](media/power-bi-visualization-treemaps/treemapfirstvalue_new.png)

1. Välj trädkartsikonen ![Skärmbild av trädkartsikonen](media/power-bi-visualization-treemaps/power-bi-treemap-icon.png) för att konvertera diagrammet till en trädkarta.

   ![Skärmbild av trädkartan utan konfiguration.](media/power-bi-visualization-treemaps/treemapconvertto_new.png)

1. Dra **Artikel** > **Kategori** till området **Grupp**.

    Power BI skapar en trädkarta där storleken på rektanglarna bygger på total försäljning och färgen representerar kategorin. I princip har du skapat en hierarki som visuellt beskriver den relativa storleken för den totala försäljningen per kategori. Kategorin **Mens (Herr)** har den högsta försäljningen och kategorin **Hosiery (Trikå)** har den lägsta.

    ![Skärmbild av den konfigurerade trädkartan.](media/power-bi-visualization-treemaps/power-bi-complete.png)

1. Dra **Store** > **kedjan** till den **information** bra för att slutföra din treemap. Nu kan du jämföra förra årets försäljning efter kategori och kedja.

   ![Skärmbild av trädkartan med Butik > Kedja har lagts till informationen.](media/power-bi-visualization-treemaps/power-bi-details.png)

   > [!NOTE]
   > Färgmättnad och Information kan inte användas samtidigt.

1. Hovra över ett **kedjeområde** för att visa verktygstips för den delen av **kategorin**.

    Om du exempelvis hovrar över **Fashions Direct** i rektangeln **090-Home** visas en knappbeskrivning för delen Fashions Direct i kategorin Home.

   ![Skärmbild av knappbeskrivningen för Home som visas.](media/power-bi-visualization-treemaps/treemaphoverdetail_new.png)

1. Lägg till trädkartan som en [panel på instrumentpanelen (fäst det visuella objektet)](../service-dashboard-tiles.md).

1. Spara [rapporten](../service-report-save.md).

## <a name="highlighting-and-cross-filtering"></a>Markering och korsfiltrering

Information om hur du använder fönstret [Filter finns](../power-bi-report-add-filter.md) i **Lägg till ett filter i en rapport**.

Om du markerar en **kategori** eller **information** i en trädkarta, korsmarkeras och korsfiltreras de övriga visualiseringarna på rapportsidan ... och vice versa. Lägg till några visuella objekt på den här rapportsidan eller kopiera trädkartan till någon av de andra sidorna i den här rapporten.

1. Välj en **Kategori** eller en **Kedja** inom en **Kategori** på trädkartan. Detta korsmarkerar de övriga visualiseringarna på sidan. Om du till exempel väljer **050-Skor**, får du veta att förra årets skoförsäljning uppgick till **USD 3 640 471** varav **USD 2 174 185** kom från **Fashions Direct**.

   ![Skärmbild av rapporten Översikt över butiksförsäljning som visar korsmarkering.](media/power-bi-visualization-treemaps/treemaphiliting.png)

1. I om du väljer delen **Fashions Direct** i cirkeldiagrammet **Senaste årets försäljning per kedja**, korsfiltreras trädkartan.
   ![GIF-demonstration av funktionen korsfiltrering.](media/power-bi-visualization-treemaps/treemapnoowl.gif)

1. För att hantera hur diagram korsmarkeras och korsfiltrerar varandra, se [Ändra hur visuella objekt interagerar i en Power BI-rapport](../service-reports-visual-interactions.md).

## <a name="next-steps"></a>Nästa steg

* [Vattenfallsdiagram i Power BI](power-bi-visualization-waterfall-charts.md)

* [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
