---
title: Använda bokmärken i Power BI
description: Bokmärken i Power BI Desktop kan du spara vyer och inställningar i dina rapporter och skapa artikel-liknande presentationer
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/06/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1660f129ef5c93cf5aed5a3a5eda3c835e1885c1
ms.sourcegitcommit: 65426de556cd7207cbc4f478198664e25c33a769
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/30/2018
---
# <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Använda bokmärken för att dela information och skapa artiklar i Power BI 
Med hjälp av **bokmärken** i Power BI kan du avbilda konfigurerade visningar av rapportsidan, inklusive filtrering och tillstånd för visuell information och senare gå tillbaka till det aktuella tillståndet genom att helt enkelt välja det sparade bokmärket. 

Du kan också skapa en samling bokmärken, ordna dem i valfri ordning och sedan gå igenom varje bokmärke i en presentation om du vill markera en serie insikter eller artikeln som du vill förmedla med din visuella information och dina rapporter. 

![Bokmärken i Power BI](media/desktop-bookmarks/bookmarks_01.png)

Bokmärken har många användningsområden. Du kan använda dem för att övervaka förloppet i att skapa rapporter (bokmärken är lätta att lägga till, ta bort och byta namn på) och du kan skapa bokmärken för att skapa en PowerPoint-liknande presentation visar bokmärken i ordning, så att din rapport utgör en berättelse. Det kan finnas andra användningsområden, baserat på hur du vill använda bokmärken.

### <a name="enable-the-bookmarks-preview-versions-prior-to-march-2018"></a>Aktivera förhandsversionen för bokmärken (versioner före mars 2018)
Från och med versionen från mars 2018 av Power BI Desktop är bokmärken allmänt tillgängliga. 

Vi rekommenderar alltid att du uppgraderar till den senaste versionen. Men om du har en tidigare version av Power BI Desktop kan du prova funktionen **bokmärken** från och med versionen från **oktober 2017** av **Power BI Desktop**, och för rapporter som har aktiverats för bokmärken i **Power BI-tjänsten**. Aktivera förhandsversionsfunktionen genom att välja **Arkiv > Alternativ och inställningar > Alternativ > Förhandsversionsfunktioner** och markera kryssrutan bredvid **Bokmärken**. 

![Aktivera bokmärken i alternativfönstret](media/desktop-bookmarks/bookmarks_02.png)

Du måste starta om **Power BI Desktop** när du har gjort valet för att aktivera förhandsversionen av bokmärken.

## <a name="using-bookmarks"></a>Använda bokmärken
Om du vill använda bokmärken väljer du menyflikfönstret **Visa** och väljer sedan kryssrutan för **fönstret Bokmärken**. 

![Visa fönstret Bokmärken genom att aktivera det i menyfliksområdet Visa.](media/desktop-bookmarks/bookmarks_03.png)

När du skapar ett bokmärke sparas följande element med bokmärket:

* Nuvarande sida
* Filter
* Utsnitt
* Sorteringsordning
* Riktning för detaljnivån
* Synlighet (för ett objekt med hjälp av fönstret **Val**)
* Fokus- eller **Spotlight**-lägen för synliga objekt

Bokmärken sparar inte för närvarande korsmarkering. 

Konfigurera en rapport som du vill att den ska visas i bokmärket. När du har utformat din rapportsida och visuella objekt väljer du **Lägg till** från fönstret **Bokmärken** om du vill lägga till ett bokmärke. 

![Lägga till ett bokmärke](media/desktop-bookmarks/bookmarks_04.png)

**Power BI Desktop** skapar ett bokmärke och ger den ett allmänt namn. Du kan enkelt *byta namn på*, *ta bort* eller *uppdatera* ett bokmärke genom att markera ellipsen bredvid bokmärkets namn och välja en åtgärd på menyn som visas.

![Välj en undermeny för ett bokmärke med hjälp av ellipser](media/desktop-bookmarks/bookmarks_05.png)

När du har ett bokmärke kan du visa det genom att klicka på bokmärket i fönstret **Bokmärken**. 

## <a name="arranging-bookmarks"></a>Ordna bokmärken
När du skapar bokmärken kanske du lägger märke till att ordningen du skapade dem i inte nödvändigtvis är samma ordning som du vill visa dem. Inga problem, kan du enkelt ändra ordningen på bokmärken.

I rutan **bokmärken** är det bara att dra och släppa bokmärken för att ändra deras inbördes ordning enligt i följande bild. Det gula fältet mellan bokmärkena visar var det flyttade bokmärket ska placeras.

![Ändra ordningen på bokmärkena genom att dra och släppa](media/desktop-bookmarks/bookmarks_06.png)

Ordningen på dina bokmärken kan vara viktiga när du använder funktionen **Visa** i bokmärken, enligt beskrivningen i nästa avsnitt.

## <a name="bookmarks-as-a-slide-show"></a>Bokmärken som ett bildspel
När du har en samling bokmärken som du vill presentera i ordning kan du välja **Visa** från fönstret **Bokmärken** om du vill starta ett bildspel.

När du är i **visnings**läget finns det några funktioner att observera:

1. Namnet på bokmärket visas i namnlisten för bokmärket, som visas längst ned i arbetsytan.
2. Namnlistan för bokmärket har pilar som låter dig flytta till nästa eller föregående bokmärke.
3. Du kan avsluta **Visnings**läget genom att välja **Avsluta** från rutan **Bokmärken** eller genom att välja **X** som finns i namnlisten för bokmärket. 

![Funktioner hos namnlisten för bokmärken](media/desktop-bookmarks/bookmarks_07.png)

När du är i **Visningsläget** kan du stänga fönstret **Bokmärken** (genom att klicka på X i det här fönstret) för att ge mer utrymme till presentationen. Medan du är i **Visningsläget** är alla visuella objekt interaktiva och är tillgängliga för korsmarkering, precis som de annars skulle vara när du interagerar med dem. 

## <a name="visibility---using-the-selection-pane"></a>Synlighet – använda synlighetsfönstret
Med lanseringen av bokmärken introduceras även det nya fönstret **Urval**. Fönstret **Urval** innehåller en lista över alla objekt på sidan och gör att du kan markera objektet och ange om ett angivet objekt är synlig. 

![Aktivera urvalsfönstret](media/desktop-bookmarks/bookmarks_08.png)

Du kan välja ett objekt med hjälp av fönstret **Urval**. Du kan också växla om objektet är synligt genom att klicka på ögonikonen till höger om den visuella informationen. 

![Urvalsfönstret](media/desktop-bookmarks/bookmarks_09.png)

När ett bokmärke har lagts till sparas statusen för varje objekt även baserat på dess inställning i fönstret **Urval**. 

Det är viktigt att notera att **utsnitt** fortsätter att filtrera en rapportsida, oavsett om de är synliga. Du kan därför skapa många olika bokmärken med olika utsnittsinställningar så att en enstaka rapportsida ser helt annorlunda ut (och markerar olika insikter) i olika bokmärken.

## <a name="bookmarks-for-shapes-and-images"></a>Bokmärken för former och bilder
Du kan också länka former och bilder till bokmärken. När du klickar på ett objekt med den här funktionen visas bokmärket som associeras med objektet. 

Om du vill tilldela ett objekt med ett bokmärke markerar du objektet och väljer sedan **Länk** från fönstret **Formatera form** som visas i följande bild.

![Lägga till bokmärkeslänk till ett objekt](media/desktop-bookmarks/bookmarks_10.png)

När du aktiverar skjutreglaget **Länk** till **På** kan du välja om objektet är en länk eller ett bokmärke. Om du väljer bokmärke kan sedan du välja vilka av dina bokmärken objektet är kopplat till.

Det finns alla typer av intressanta saker du kan göra med ett objektlänkat bokmärke. Du kan skapa en visuell innehållsförteckning på rapportsidan eller kan ange olika vyer (till exempel visuella typer) av samma information genom att klicka på ett objekt.

När du är i redigeringsläge kan du använda ctrl + klicka om du vill följa länken när du inte är i redigeringsläget. Bara klicka på objekt om du vill följa länken. 

## <a name="using-spotlight"></a>Använda Spotlight
En annan funktion som lanseras med bokmärken är **Spotlight**. Med **Spotlight** kan du dra uppmärksamhet till ett specifikt diagram, till exempel när du presenterar dina bokmärken i **Visningsläget**.

Vi kan jämföra **Spotlight** med **fokus**läge för att se hur de skiljer sig åt.

1. I **fokus**läge kan du låta ett visuellt objekt fylla hela arbetsytan genom att välja ikonen **Fokusläge**.
2. Med hjälp av **Spotlight** kan du markera ett visuellt objekt i ursprunglig storlek genom att låta andra visuella objekt tona bort så att de nästan är osynliga. 

![Jämför fokusläge med spotlight](media/desktop-bookmarks/bookmarks_11.png)

När det visuella objektet i föregående bild har aktiverat **fokus**ikonen ser sidan ut ungefär så här:

![fokusläge](media/desktop-bookmarks/bookmarks_12.png)

Däremot, när **Spotlight** väljs från ellipsmenyn för det visuella objektet ser sidan ut så här:

![spotlightläge](media/desktop-bookmarks/bookmarks_13.png)

Om något av dessa lägen aktiveras när du har lagt till ett bokmärke blir läget (fokus eller spotlight) kvar i bokmärket.

## <a name="bookmarks-in-the-power-bi-service"></a>Bokmärken i Power BI-tjänsten
När du publicerar en rapport i **Power BI-tjänsten** med minst ett bokmärke kan du visa och interagera med dessa bokmärken i **Power BI-tjänsten**. För varje rapport som du publicerar måste du ha minst ett bokmärke som skapas i rapporten innan du publicerar, så att funktionen bokmärket blir tillgängliga i **Power BI-tjänsten**.

När bokmärken är tillgängliga i en rapport kan du välja **Visa > urvalsfönster** eller **Visa > Fönstret bokmärken** för att visa var och ett av dessa fönster.

![Visa bokmärken och fönster för urval i Power BI-tjänsten](media/desktop-bookmarks/bookmarks_14.png)

I **Power BI-tjänsten** fungerar **Fönstret bokmärken** precis som **Power BI Desktop**, inklusive möjligheten att välja **Visa** att visa dina bokmärken i ordning, precis som ett bildspel.

Observera att du måste använda den grå namnlisten för att navigera bland bokmärken snarare än de svarta pilarna (de svarta pilarna förflyttar dig genom rapportens sidor, inte bokmärken).

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Det finns några begränsningar och saker du bör tänka på för den här versionen av **bokmärken**.

* Anpassad visuell information fungerar inte med bokmärken om de är *källan* för filtret. Om du använder anpassad visuell information för att filtrera element på sidan (till exempel ett chiclet-utsnitt) och återgår till sidan med ett bokmärke, filtreras sidan men anpassade visuella uppdateras inte för att visa hur sidan filtreras. 
* Markering av mellan status för ett rapportfönster sparas *inte* när du skapar ett bokmärke. 
* Om du lägger till ett visuellt objekt på en rapportsida efter att du har skapat ett bokmärke kommer det visuella objektet att visas i sitt standardläge. Det innebär att om du lägger till ett utsnitt på en sida där du tidigare skapade bokmärken så fungerar utsnittet i standardtillståndet.
* Flytta runt visuella objekt när ett bokmärke har skapats visas i bokmärket. 
* Du *måste* ha minst ett bokmärke i din rapport när du publicerar den på **Power BI-tjänsten** för att bokmärken ska vara tillgängliga i tjänsten. Detta är ett krav för varje rapport som du publicerar.

## <a name="next-steps"></a>Nästa steg
Mer information om liknande funktioner eller funktioner som interagerar med bokmärken finns i följande artiklar:

* [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md)
* [Visa instrumentpanelen eller rapportvisualiseringen i läget Fokus](service-focus-mode.md)

