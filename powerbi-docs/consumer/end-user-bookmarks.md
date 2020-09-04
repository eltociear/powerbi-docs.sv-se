---
title: Översikt över bokmärken i Power BI-tjänstrapporter
description: Dokumentationsöversikt för bokmärken i Power BI-tjänsten.
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 08/26/2020
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: f865815c76df179c87c1487e1243c37108375167
ms.sourcegitcommit: 13c4bec679313f2951f1833033316cb8176da8a1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88937724"
---
# <a name="what-are-bookmarks"></a>Vad är bokmärken?

[!INCLUDE[consumer-appliesto-ynnm](../includes/consumer-appliesto-ynnm.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Bokmärken registrerar den aktuella konfigurerade vyn för en rapportsida, inklusive filter, utsnitt och tillståndet för visuella objekt. När du väljer ett bokmärke går Power BI tillbaka till den vyn. Det finns två typer av bokmärken – sådana som du skapar själv och sådana som skapas av *rapportdesigners*. Alla Power BI-användare kan skapa personliga bokmärken. För att använda bokmärken som skapats av andra behöver du dock en Power BI Pro- eller Premium-licens. [Vilken licens har jag?](end-user-license.md)

## <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Använda bokmärken för att dela information och skapa artiklar i Power BI 
Bokmärken har många användningsområden. Anta att du upptäcker en intressant insikt och vill bevara den – skapa ett bokmärke så att du kan gå tillbaka senare. Om du behöver göra något annat och vill spara ditt nuvarande arbete kan du skapa ett bokmärke. Du kan dessutom göra ett bokmärke till din standardvy för rapporten så att den vyn av rapportsidan öppnas först varje gång du kommer tillbaka. 

Du kan även skapa en samling bokmärken, ordna dem i valfri ordning och sedan gå igenom varje bokmärke i en presentation och framhäva en serie med insikter som du vill förmedla.  

![Visa Bokmärkesfönstret genom att välja det i menyfliksområdet.](media/end-user-bookmarks/power-bi-bookmark-icon.png)

## <a name="open-bookmarks"></a>Öppna bokmärken
Du kan öppna Bokmärkesfönstret genom att välja **Bokmärken** > **Visa flera bokmärken** på menyraden. 

![skärmbild av rapportarbetsyta med fönstret Bokmärken öppet.](media/end-user-bookmarks/power-bi-show-bookmarks.png)

Om du vill återgå till den ursprungligen publicerade vyn för rapporten väljer du ikonen för **återställning**.

![skärmbild där återställningsikonen har valts](media/end-user-bookmarks/power-bi-revert.png)

### <a name="report-bookmarks"></a>Rapportbokmärken
Om *rapportdesignern* inkluderade rapportbokmärken finns de under rubriken **Rapportbokmärken**. Den här rapportsidan har fyra bokmärken: B1, B2, VanArsdel YTD och All YTD. **All YTD** är valt just nu.

> [!NOTE]
> Du behöver Power BI Pro eller Premium för att visa delade rapporter. 

![Visa rapportbokmärken.](media/end-user-bookmarks/power-bi-bookmark-list.png)

Välj ett bokmärke för att ändra till den rapportvyn. 

![Video som visar rapportbokmärken som väljs.](media/end-user-bookmarks/power-bi-bookmarks.gif)

### <a name="personal-bookmarks"></a>Personliga bokmärken

Om du kan se en rapport, kan du också lägga till personliga bokmärken.  När du skapar ett bokmärke sparas följande element med bokmärket:

* Nuvarande sida
* Filter
* Utsnitt, inklusive utsnittstyp (till exempel listruta eller lista) och utsnittstillstånd
* Tillstånd för markering i visuellt objekt (till exempel filtrering för flera markeringar)
* Sorteringsordning
* Riktning för detaljnivån
* Synlighet (för ett objekt med hjälp av fönstret **Val**)
* Fokus- eller **Spotlight**-lägen för synliga objekt

Konfigurera en rapport som du vill att den ska visas i bokmärket. I det här exemplet:

1. Vi har ändrat det befintliga datumfiltret i fönstret **Filter**,
1. ändrat filter för befintliga regioner i fönstret **Filter** och
1.  markerat datapunkter i ringdiagrammets visuella objekt för att korsfiltrera och korsmarkera rapportarbetsytan. 

När du har utformat din rapportsida och visuella objekt väljer du **Lägg till** från fönstret **Bokmärken** om du vill lägga till ett bokmärke. 

![Lägg till personliga bokmärken.](media/end-user-bookmarks/power-bi-personal.png)

**Power BI** skapar ett personligt bokmärke och ger det ett allmänt namn eller ett namn som du anger. Du kan *byta namn på*, *ta bort* eller *uppdatera* ditt bokmärke genom att välja ellipsen intill bokmärkets namn och sedan välja en åtgärd på den meny som visas.

När du har ett bokmärke kan du visa det genom att välja bokmärket i fönstret **Bokmärken**. 

![Visa ett specifikt bokmärke genom att välja det.](media/end-user-bookmarks/power-bi-selected.png)


<!--
## Arranging bookmarks
As you create bookmarks, you might find that the order in which you create them isn't necessarily the same order you'd like to present them to your audience. No problem, you can easily rearrange the order of bookmarks.

In the **Bookmarks** pane, simply drag-and-drop bookmarks to change their order, as shown in the following image. The yellow bar between bookmarks designates where the dragged bookmark will be placed.

![Change bookmark order by drag-and-drop](media/desktop-bookmarks/bookmarks_06.png)

The order of your bookmarks can become important when you use the **View** feature of bookmarks, as described in the next section. 

-->

## <a name="bookmarks-as-a-slide-show"></a>Bokmärken som ett bildspel
Om du vill presentera eller visa bokmärken i ordning väljer du **Visa** i fönstret **Bokmärken** för att starta ett bildspel.

När du är i **visnings**läget finns det några funktioner att observera:

- Namnet på bokmärket visas i namnlisten för bokmärket, som visas längst ned i arbetsytan.
- Namnlistan för bokmärket har pilar som låter dig flytta till nästa eller föregående bokmärke.
- Du kan avsluta **Visnings**läget genom att välja **Avsluta** från rutan **Bokmärken** eller genom att välja **X** som finns i namnlisten för bokmärket.

![Bildspel med bokmärken](media/end-user-bookmarks/power-bi-view-bookmarks.png)

När du är i **Visningsläget** kan du stänga fönstret **Bokmärken** (genom att klicka på X i det här fönstret) för att ge mer utrymme till presentationen. Medan du är i **Visningsläget** är alla visuella objekt interaktiva och är tillgängliga för korsmarkering, precis som de annars skulle vara när du interagerar med dem. 

<!--
## Visibility - using the Selection pane
With the release of bookmarks, the new **Selection** pane is also introduced. The **Selection** pane provides a list of all objects on the current page and allows you to select the object and specify whether a given object is visible. 

![Enable the Selection pane](media/desktop-bookmarks/bookmarks_08.png)

You can select an object using the **Selection** pane. Also, you can toggle whether the object is currently visible by clicking the eye icon to the right of the visual. 

![Selection pane](media/desktop-bookmarks/bookmarks_09.png)

When a bookmark is added, the visible status of each object is also saved based on its setting in the **Selection** pane. 

It's important to note that **slicers** continue to filter a report page, regardless of whether they are visible. As such, you can create many different bookmarks, with different slicer settings, and make a single report page appear very different (and highlight different insights) in various bookmarks.


## Bookmarks for shapes and images
You can also link shapes and images to bookmarks. With this feature, when you click on an object, it will show the bookmark associated with that object. This can be especially useful when working with buttons; you can learn more by reading the article about [using buttons in Power BI](../create-reports/desktop-buttons.md). 

To assign a bookmark to an object, select the object, then expand the **Action** section from the **Format Shape** pane, as shown in the following image.

![Add bookmark link to an object](media/desktop-bookmarks/bookmarks_10.png)

Once you turn the **Action** slider to **On** you can select whether the object is a back button, a bookmark, or a Q&A command. If you select bookmark, you can then select which of your bookmarks the object is linked to.

There are all sorts of interesting things you can do with object-linked bookmarking. You can create a visual table of contents on your report page, or you can provide different views (such as visual types) of the same information, just by clicking on an object.

When you are in editing mode you can use ctrl+click to follow the link, and when not in edit mode, simply click the object to follow the link. 


## Bookmark groups

Beginning with the August 2018 release of **Power BI Desktop**, you can create and use bookmark groups. A bookmark group is a collection of bookmarks that you specify, which can be shown and organized as a group. 

To create a bookmark group, hold down the CTRL key and select the bookmarks you want to include in the group, then click the ellipses beside any of the selected bookmarks, and select **Group** from the menu that appears.

![Create a bookmark group](media/desktop-bookmarks/bookmarks_15.png)

**Power BI Desktop** automatically names the group *Group 1*. Fortunately, you can just double-click on the name and rename it to whatever you want.

![Rename a bookmark group](media/desktop-bookmarks/bookmarks_16.png)

With any bookmark group, clicking on the bookmark group's name only expands or collapses the group of bookmarks, and does not represent a bookmark by itself. 

When using the **View** feature of bookmarks, the following applies:

* If the selected bookmark is in a group when you select **View** from bookmarks, only the bookmarks *in that group* are shown in the viewing session. 

* If the selected bookmark is not in a group, or is on the top level (such as the name of a bookmark group), then all bookmarks for the entire report are played, including bookmarks in any group. 

To ungroup bookmarks, just select any bookmark in a group, click the ellipses, and then select **Ungroup** from the menu that appears. 

![Ungroup a bookmark group](media/desktop-bookmarks/bookmarks_17.png)

Note that selecting **Ungroup** for any bookmark from a group takes all bookmarks out of the group (it deletes the group, but not the bookmarks themselves). So to remove a single bookmark from a group, you need to **Ungroup** any member from that group, which deletes the grouping, then select the members you want in the new group (using CTRL and clicking each bookmark), and select **Group** again. 
-->





## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Det finns några begränsningar och saker du bör tänka på i den här versionen av **bokmärken**.

* De flesta visuella Power BI-objekt bör fungera väl med bokmärkning. Om du stöter på problem med bokmärkning och ett visuellt Power BI-objekt, kontaktar du den som har skapat det visuella Power BI-objektet och ber den personen att lägga till stöd för bokmärken till sina visuella objekt.
* Om du lägger till ett visuellt objekt på en rapportsida efter att du har skapat ett bokmärke kommer det visuella objektet att visas i sitt standardläge. Det innebär att om du lägger till ett utsnitt på en sida där du tidigare skapade bokmärken så fungerar utsnittet i standardtillståndet.
* Generellt påverkas inte dina bokmärken om *rapportdesignern* uppdaterar eller publicerar rapporten på nytt. Men om designern gör större ändringar i rapporten, till exempel att ta bort fält som används av ett bokmärke, visas ett felmeddelande nästa gång du försöker öppna det bokmärket. 

<!--
## Next steps
spotlight?
-->
