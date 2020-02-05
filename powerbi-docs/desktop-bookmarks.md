---
title: Använda bokmärken i Power BI Desktop för att dela insikter och skapa berättelser
description: Bokmärken i Power BI Desktop kan du spara vyer och inställningar i dina rapporter och skapa artikel-liknande presentationer
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 08d222f03991bdf605f8e465ff0152d40d07d815
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "75761897"
---
# <a name="create-bookmarks-in-power-bi-desktop-to-share-insights-and-build-stories"></a>Skapa bokmärken i Power BI Desktop för att dela insikter och skapa berättelser
Med *bokmärkesfunktionen* i Power BI Desktop kan du spara den aktuella konfigurerade vyn av en rapportsida, inklusive filtrering och tillståndet för visuella objekt. Du kan sedan gå tillbaka till det tillståndet genom att välja det sparade bokmärket. 

Du kan också skapa en samling bokmärken, ordna dem i valfri ordning och senare gå igenom varje bokmärke i en presentation för att betona ett antal insikter eller den berättelse som du vill förmedla med din visuella information och dina rapporter. 

![Bokmärken i Power BI](media/desktop-bookmarks/bookmarks_01.png)

Bokmärken har många användningsområden. Du kan till exempel använda bokmärken för att följa förloppet när du skapar rapporter (det är enkelt att lägga till, ta bort och byta namn på bokmärken) och du kan spara bokmärken för att skapa en PowerPoint-liknande presentation som visar bokmärken i ordning, så att din rapport blir till en berättelse. 

> [!TIP]
> Information om hur du använder personliga bokmärken i Power BI-tjänsten finns i [avsnittet om den nya funktionen för personliga bokmärken i Power BI-tjänsten](https://powerbi.microsoft.com/blog/announcing-personal-bookmarks-in-the-power-bi-service/). 

## <a name="using-bookmarks"></a>Använda bokmärken
Om du vill använda bokmärken väljer du fliken **Visa** i menyfliksområdet i Power BI Desktop och väljer **Bokmärkesfönster**. 

![Aktivera bokmärkesfönstret](media/desktop-bookmarks/bookmarks_03.png)

När du skapar ett bokmärke sparas följande element med bokmärket:

* Nuvarande sida
* Filter
* Utsnitt, inklusive utsnittstyp (till exempel listruta eller lista) och utsnittstillstånd
* Tillstånd för markering i visuellt objekt (till exempel filtrering för flera markeringar)
* Sorteringsordning
* Riktning för detaljnivån
* Ett objekts synlighet (med hjälp av **markeringsfönstret**)
* Fokus- eller **Spotlight**-lägen för synliga objekt

Konfigurera en rapportsida så som du vill att den ska visas i bokmärket. När du har utformat din rapportsida och dina visuella objekt väljer du **Lägg till** från fönstret **Bokmärken** om du vill lägga till ett bokmärke. 

![Lägga till ett bokmärke](media/desktop-bookmarks/bookmarks_04.png)

Power BI Desktop skapar ett bokmärke och ger den ett allmänt namn. Du kan enkelt **byta namn på**, **ta bort** eller **uppdatera** ett bokmärke genom att välja ellipsen bredvid bokmärkets namn och sedan välja en åtgärd på menyn som visas.

![Välj bokmärkesmenyn genom att välja ellipsen](media/desktop-bookmarks/bookmarks_05.png)

När du har skapat ett bokmärke kan du visa det genom att markera det i fönstret **Bokmärken**. 

Du kan också välja om varje bokmärke ska tillämpa **Data**-egenskaper, som filter och utsnitt, **Visa**-egenskaper, som spotlightläge och synlighet, samt ändringar av **Aktuell sida** som visar den sida som var synlig när bokmärket lades till. De här funktionerna är användbara när du använder bokmärken för att växla mellan rapportvyer och urval av visuella objekt – då du förmodligen vill inaktivera dataegenskaperna så att filter inte återställs när användarna byter vy genom att välja ett bokmärke. 

Om du vill göra sådana ändringar väljer du ellipsen bredvid bokmärkets namn och markerar eller avmarkerar kryssrutorna bredvid **Data**, **Visa** och andra kontroller. 

## <a name="arranging-bookmarks"></a>Ordna bokmärken
När du skapar bokmärken kanske du upptäcker att du inte vill presentera dem för din målgrupp i samma ordning som du skapade dem i. Inga problem, kan du enkelt ändra ordningen på bokmärken.

- Dra och släpp bokmärkena i **bokmärkesfönstret** om du vill ändra deras ordning. 

   Det gula fältet mellan bokmärkena visar var det flyttade bokmärket ska placeras.

   ![Ändra ordningen på bokmärkena genom att dra och släppa](media/desktop-bookmarks/bookmarks_06.png)

Som du ser i nästa avsnitt kan bokmärkenas inbördes ordning vara viktig när du använder **Visa**-funktionen för dina bokmärken.

## <a name="bookmarks-as-a-slide-show"></a>Bokmärken som ett bildspel
När du har en samling bokmärken som du vill presentera i ordning kan du välja **Visa** från fönstret **Bokmärken** om du vill starta ett bildspel.

Det finns många intressanta funktioner i **visningsläget**.

   ![Funktioner hos namnlisten för bokmärken](media/desktop-bookmarks/bookmarks_07.png)

1. Namnet på bokmärket visas i namnlisten för bokmärket, som visas längst ned i arbetsytan.

2. Namnlistan för bokmärket har pilar som låter dig flytta till nästa eller föregående bokmärke.

3. Du kan avsluta **visningsläget** genom att välja **Avsluta** från **bokmärkesfönstret** eller genom att välja **X** på namnlisten för bokmärken. 

När du arbetar i **visningsläget** kan du stänga **bokmärkesfönstret** genom att klicka på **X** i fönstret så att presentationen får mer utrymme. Alla visuella objekt är interaktiva i **visningsläget** och kan korsmarkeras på samma sätt som när du interagerar med dem direkt. 

## <a name="visibility-using-the-selection-pane"></a>Synlighet: Använda markeringsfönstret
**Markeringsfönstret** är kopplat till **bokmärkesfönstret** och visar en lista över alla objekt på den aktuella sidan, som du sedan kan välja att visa eller inte. 

![Aktivera urvalsfönstret](media/desktop-bookmarks/bookmarks_08.png)

I **markeringsfönstret** väljer du ett objekt och visar eller döljer det genom att välja ögonikonen till höger om objektet. 

![Urvalsfönstret](media/desktop-bookmarks/bookmarks_09.png)

När du lägger till ett bokmärke sparas även synlighetsstatusen för varje objekt, baserat på dess inställning i **markeringsfönstret**. 

Det är viktigt att notera att utsnitt fortsätter att filtrera en rapportsida, oavsett om de är synliga. Du kan därför skapa många olika bokmärken med olika utsnittsinställningar så att en enstaka rapportsida ser annorlunda ut (och markerar olika insikter) i olika bokmärken.

## <a name="bookmarks-for-shapes-and-images"></a>Bokmärken för former och bilder
Du kan också länka former och bilder till bokmärken. Med den här funktionen visas bokmärket som är associerat med ett objekt när du väljer objektet. Den här funktionen är särskilt användbar när du arbetar med knappar. Mer information finns i [Använda knappar i Power BI](desktop-buttons.md). 

Så här tilldelar du ett bokmärke till ett objekt: 

1. Markera objektet på rapportarbetsytan. Från fönstret **Formatera form** som visas växlar du sedan skjutreglaget för **Åtgärd** till **På**.

2. Expandera avsnittet **Åtgärd**. Under **Typ** väljer du **Bokmärke**.

3. Under **Bokmärken** väljer du ett bokmärke.

   ![Lägga till bokmärkeslänk till ett objekt](media/desktop-bookmarks/bookmarks_10.png)

Det finns alla typer av intressanta saker du kan göra med ett objektlänkat bokmärke. Du kan skapa en visuell innehållsförteckning på rapportsidan eller visa olika vyer (till exempel visuella typer) av informationen.

När du är i redigeringsläge trycker du på **CTRL** och väljer länken för att följa den. När du inte är i redigeringsläge väljer du objektet för att följa länken. 

## <a name="bookmark-groups"></a>Bokmärkesgrupper

Från och med Power BI Desktop-versionen för augusti 2018 kan du skapa och använda bokmärkesgrupper. En bokmärkesgrupp är en samling bokmärken som du anger, som kan visas och ordnas i en grupp. 

Så här skapar du en bokmärkesgrupp: 
1. Tryck på **CTRL** och välj de bokmärken som du vill ta med i gruppen. 

2. Välj ellipsen bredvid de valda bokmärkena och välj sedan **Grupp** på menyn som visas.

   ![Skapa en bokmärkesgrupp](media/desktop-bookmarks/bookmarks_15.png)

Power BI Desktop ger automatiskt gruppen namnet *Grupp 1*. Du kan välja ellipsen bredvid namnet, välja **Byt namn** och byta namn på gruppen till önskat namn.

![Byta namn på en bokmärkesgrupp](media/desktop-bookmarks/bookmarks_16.png)

När du expanderar namnet på en bokmärkesgrupp expanderas eller komprimeras bara gruppen med bokmärken, och du ser alltså inte själva bokmärkena i gruppen. 

När du använder **Visa**-funktionen för bokmärken gäller följande:

* Om det valda bokmärket finns i en grupp när du väljer **Visa** från bokmärken, visas endast bokmärkena *i den gruppen* i visningssessionen. 

* Om det valda bokmärket inte finns i en grupp, eller om det finns på den högsta nivån (till exempel namnet på en bokmärkesgrupp), visas alla bokmärken för hela rapporten, inklusive alla bokmärken i alla grupper. 

Så här delar du upp bokmärken: 
1. Markera ett bokmärke i en grupp och välj ellipsen. 

2. Välj **Dela upp grupp** på menyn som visas.

   ![Dela upp en bokmärkesgrupp](media/desktop-bookmarks/bookmarks_17.png)

   Om du väljer **Dela upp grupp** för ett bokmärke från en grupp tas alla bokmärken bort från gruppen. Gruppen tas bort, men inte själva bokmärkena. 

Så här tar du bort ett enskilt bokmärke från en grupp: 
1. **Avgruppera** valfri medlem i gruppen, vilket gör att hela grupperingen tas bort. 

2. Välj de medlemmar som ska ingå i den nya gruppen genom att trycka på **CTRL** och markera varje bokmärke och välj sedan **Grupp** igen. 


## <a name="using-spotlight"></a>Använda Spotlight
En annan funktion som lanseras med bokmärken är *Spotlight*. Med Spotlight kan du dra uppmärksamhet till ett specifikt diagram, till exempel när du presenterar dina bokmärken i **visningsläget**.

Vi kan jämföra spotlightläge med fokusläge för att se hur de skiljer sig åt:

1. I fokusläge väljer du ikonen för **fokusläge** för ett visuellt objekt, vilket gör att det visuella objektet fyller hela arbetsytan.

2. I spotlightläge väljer du **Spotlight** från ellipsen för ett visuellt objekt för att framhäva ett visuellt objekt i dess ursprungliga storlek, vilket gör att alla andra visuella objekt på sidan tonas ut tills de nästan är genomskinliga. 

![Jämföra spotlightläge med fokusläge](media/desktop-bookmarks/bookmarks_11.png)

När du väljer ikonen för **fokusläge** för det visuella objektet i föregående bild visas sidan så här:

![Fokusläge](media/desktop-bookmarks/bookmarks_12.png)

När du i stället har valt **Spotlight** från ellipsmenyn för det visuella objektet visas sidan så här:

![Spotlightläge](media/desktop-bookmarks/bookmarks_13.png)

Om du väljer fokus- eller spotlightläge när du lägger till ett bokmärke, behålls det läget i bokmärket.

## <a name="bookmarks-in-the-power-bi-service"></a>Bokmärken i Power BI-tjänsten
När du publicerar en rapport i Power BI-tjänsten med minst ett bokmärke kan du visa och interagera med dessa bokmärken i Power BI-tjänsten. När bokmärken är tillgängliga i en rapport visar du **markerings-** och **bokmärkesfönstren** genom att välja **Visa** > **Markeringsfönster** eller **Visa** > **Bokmärkesfönster**. 

![Visa bokmärken och fönster för urval i Power BI-tjänsten](media/desktop-bookmarks/bookmarks_14.png)

I Power BI-tjänsten fungerar **bokmärkesfönstret** som i Power BI Desktop, och precis som där kan du välja **Visa** för att visa dina bokmärken i ordning, som ett bildspel.

Använd den grå namnlisten för bokmärken, i stället för de svarta pilarna, för att bläddra igenom bokmärkena. (Med de svarta pilarna bläddrar du igenom rapportsidor, inte bokmärken.)

## <a name="enable-the-bookmarks-preview-versions-prior-to-march-2018"></a>Aktivera förhandsversionen för bokmärken (versioner före mars 2018)
Från och med versionen från mars 2018 av Power BI Desktop är bokmärken allmänt tillgängliga. 

Vi rekommenderar alltid att du uppgraderar till den senaste versionen. Om du har en tidigare version av Power BI Desktop kan du prova bokmärkesfunktionen från och med versionen från oktober 2017 av Power BI Desktop, och för rapporter som har aktiverats för bokmärken i Power BI-tjänsten. 

Så här aktiverar du funktionen för förhandsgranskning av bokmärken: 

1. Välj **Arkiv** > **Alternativ och inställningar** > **Alternativ** > **Förhandsversionsfunktioner** och välj sedan **Bokmärken**. 

   ![Aktivera bokmärken i alternativfönstret](media/desktop-bookmarks/bookmarks_02.png)

2. Aktivera förhandsversionen av bokmärken genom att starta om Power BI Desktop.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Det finns några begränsningar och saker du bör tänka på för den här versionen av bokmärkesfunktionerna.

* De flesta anpassade visuella objekt bör fungera väl med bokmärkning. Men om du stöter på problem med bokmärkning och ett anpassat visuellt objekt, kontaktar du den person som skapat det anpassade visuella objektet och ber dem att lägga till stöd för bokmärken till sina visuella objekt. 
* Om du lägger till ett visuellt objekt på en rapportsida efter att du har skapat ett bokmärke kommer det visuella objektet att visas i dess standardläge. Det innebär att om du introducerar ett utsnitt på en sida där du tidigare skapade bokmärken så fungerar utsnittet som i dess standardtillstånd.
* Om du flyttar ett visuellt objekt efter att ett bokmärke har skapats så återges det automatiskt i bokmärket. 

## <a name="next-steps"></a>Nästa steg
Mer information om liknande funktioner och funktioner som interagerar med bokmärken finns i följande artiklar:

* [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md)
* [Visa en instrumentpanel eller rapportvisualisering i fokusläge](consumer/end-user-focus.md)

