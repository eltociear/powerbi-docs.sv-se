---
title: Skapa rapporter som är optimerade för Power BI-mobilapparna
description: Lär dig hur du optimerar rapportsidor i Power BI Desktop för Power BI-telefonapparna.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 6ac85bcaba34f705b0f21efc86ed1583e69c8c2c
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721074"
---
# <a name="create-reports-optimized-for-the-power-bi-phone-apps"></a>Skapa rapporter som är optimerade för Power BI-mobilapparna
När du [skapar en rapport i Power BI Desktop](desktop-report-view.md) kan du förbättra användningen i mobilappar genom att skapa en version av rapporten som är specifik för mobiltelefoner. Du anpassar rapporten för telefonen genom att arrangera om och ändra storlek på visuella objekt, samt kanske ta bort några för en optimal upplevelse. Du kan dessutom skapa [*dynamiska* visuella objekt](#optimize-a-visual-for-any-size) och [dynamiska utsnitt](#enhance-slicers-to-to-work-well-in-phone-reports) som anpassar sin storlek så att de ser bra ut på en telefon. Om du lägger till filter i din rapport, visas de filtren dessutom automatiskt i telefonrapporten. Dina rapportläsare kan se dem och filtrera rapporten med dem.

![Optimerad rapport i en telefon](media/desktop-create-phone-report/desktop-create-phone-report-1.png)

## <a name="lay-out-a-report-page-for-the-phone-in-power-bi-desktop"></a>Utforma en rapportsida för telefonen i Power BI Desktop
När du har [skapat en rapport i Power BI Desktop](desktop-report-view.md), kan du optimera den för telefoner.

1. I Power BI Desktop väljer du **Rapportvy** i det vänstra navigeringsfältet.
   
    ![Ikonen Rapportvy](media/desktop-create-phone-report/desktop-create-phone-report-2.png)
2. På fliken **Visa** väljer du **Telefonlayout**.  
   
    ![Ikonen Telefonlayout](media/desktop-create-phone-report/desktop-create-phone-report-3.png)
   
    Du ser en tom telefonarbetsyta. Alla visuella objekt på den ursprungliga rapportsidan visas i fönstret Visualiseringar till höger.
3. Om du vill lägga till ett visuellt objekt i telefonlayouten drar du det från fönstret Visualiseringar till telefonens arbetsyta.
   
    Telefonrapporter använder sig av en rutnätslayout. När du drar visuella objekt till mobilarbetsytan fäster de vid rutnätet.
   
    ![Dra och släppa ett visuellt objekt](media/desktop-create-phone-report/desktop-create-phone-report-4.gif)
   
    Du kan lägga till några eller alla av huvudrapportsidans visuella objekt på telefonens rapportsida. Du kan bara lägga till varje visuellt objekt en gång.
4. Du kan ändra storlek på de visuella objekten i rutnätet på samma sätt som med paneler på instrumentpaneler och mobila instrumentpaneler.
   
   > [!NOTE]
   > Telefonens rapportrutnät anpassas till telefoner av olika storlekar, vilket innebär att din rapport kommer att se lika bra ut på telefoner med stora och små skärmar.
   > 
   > 
   
   ![Ändra storlek på ett visuellt objekt](media/desktop-create-phone-report/desktop-create-phone-report-5.gif)

## <a name="optimize-a-visual-for-any-size"></a>Optimera ett visuellt objekt oavsett storlek
Du kan ange att visuella objekt i din instrumentpanel eller rapport ska vara *dynamiska*, så att de ändras dynamiskt till att visa maximal mängd data och analyser, oavsett skärmstorlek. 

När ett visuellt objekt får en annan storlek prioriterar Power BI datavyn, genom att till exempel ta bort utfyllnad och flytta förklaringen överst i det visuella objektet automatiskt, så att objektet förblir informativt även när det blir mindre.

![Dynamisk storleksändring av visuella objekt](media/desktop-create-phone-report/desktop-create-phone-report-6.gif)

Du väljer om du ska aktivera svarstider för varje visuellt objekt. Läs mer om att [optimera visuella objekt](desktop-create-responsive-visuals.md).

## <a name="considerations-when-creating-phone-report-layouts"></a>Överväganden när man skapar telefonrapportlayouter
* För rapporter med flera sidor kan du optimera alla sidor eller enbart ett fåtal. 
* Om du har definierat en bakgrundsfärg för en rapportsida, kommer telefonrapporten ha samma bakgrundsfärg.
* Du kan inte ändra formateringsinställningarna för enbart telefonen. Formateringen är likadan mellan huvud- och mobillayouter. Exempelvis kommer teckenstorlekarna vara desamma.
* Om du vill ändra ett visuellt objekt, exempelvis dess formatering, datauppsättning, filter eller andra attribut, återgår du till det vanliga rapportredigeringsläget.
* I Power BI finns standardrubriker och sidnamn för telefonrapporter i mobilappen. Om du har skapat visuella textobjekt för rubriker och sidnamn i rapporten, kan du fundera på om de ska läggas till eller ej i telefonrapporterna.     

## <a name="remove-a-visual-from-the-phone-layout"></a>Ta bort ett visuellt objekt från telefonlayouten
* Ta bort ett visuellt objekt genom att klicka på X i det övre högra fönstret på det visuella objektet på telefonarbetsytan, eller genom att markera det och trycka på **Ta bort**.
  
   Om du tar bort det visuella objektet här tas det bara bort från telefonlayoutens arbetsyta. Det visuella objektet och den ursprungliga rapporten påverkas inte.
  
   ![Ta bort ett visuellt objekt](media/desktop-create-phone-report/desktop-create-phone-report-7.gif)

## <a name="enhance-slicers-to-to-work-well-in-phone-reports"></a>Förbättra utsnitt till att fungera i telefonrapporter
Utsnitten ger filtrering av rapportdata på arbetsytan. När utformning av utsnitt sker i det vanliga rapportredigeringsläget, kan du ändra vissa utsnittsinställningar för att göra dem mer användbara i telefonrapporter:

* Bestäm om rapportläsarna ska kunna välja ett eller flera objekt.
* Placera en ruta runt utsnittet för att göra rapporten enklare att skanna.
* Gör utsnittet lodrätt, vågrätt eller *dynamiskt*. 

Om du gör utsnittet dynamiskt, visar det fler eller färre alternativ när du ändrar storleken eller formen. Det kan vara högt, kort, brett eller smalt. Om du gör det tillräckligt litet, blir det bara en filterikon på rapportsidan. 

![Power BI-dynamiskt utsnitt](media/desktop-create-phone-report/desktop-create-phone-report-8.png)

Läs mer om att [skapa dynamiska utsnitt](power-bi-slicer-filter-responsive.md).

## <a name="publish-a-phone-report"></a>Publicera en telefonrapport
* Om du vill publicera en telefonversion av en rapport [publicerar du huvudrapporten från Power BI Desktop till Power BI-tjänsten](desktop-upload-desktop-files.md). Telefonversionen publiceras samtidigt.
  
    Läs mer om [delning och behörigheter i Power BI](service-how-to-collaborate-distribute-dashboards-reports.md).

## <a name="view-optimized-and-unoptimized-reports-on-a-phone"></a>Visa optimerade och icke-optimerade rapporter i en telefon
I mobilapparna för telefoner hittar Power BI automatiskt optimerade och icke-optimerade telefonrapporter. Om det finns en telefonoptimerad rapport kommer Power BI-telefonappen automatiskt öppna den i telefonrapportläge.

Om det inte finns någon telefonoptimerad rapport kommer rapporten öppnas i en icke-optimerad liggande vy.  

När du är i telefonrapporten kommer rapporten öppnas i en icke-optimerad vy med den ursprungliga rapportlayouten när du ändrar telefonens orientering till liggande, oavsett om rapporten är optimerad eller ej.

Om du enbart optimerar vissa sidor kommer läsarna att se ett meddelande i stående vy som visar att rapporten är tillgänglig i liggande vy.

![Telefonsidan är inte optimerad](media/desktop-create-phone-report/desktop-create-phone-report-9.png)

Rapportläsarna kan vrida sina telefoner åt sidan för att se rapporten i liggande läge. Läs mer om att [använda Power BI-rapporter som är optimerade för din telefon](mobile-apps-view-phone-report.md).

## <a name="next-steps"></a>Nästa steg
* [Skapa en telefonvy av en instrumentpanel i Power BI](service-create-dashboard-mobile-phone-view.md)
* [Visa Power BI-rapporter som är optimerade för din telefon](mobile-apps-view-phone-report.md)
* [Skapa dynamiska visuella objekt som optimerats för alla storlekar](desktop-create-responsive-visuals.md)
* Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

