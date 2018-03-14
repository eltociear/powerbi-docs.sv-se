---
title: "Användningsstatistik för instrumentpaneler och rapporter"
description: "Så här visar, sparar och använder du användningsstatistik för Power BI-instrumentpaneler och rapporter. Mät och öka din inverkan med användningsstatistik för skapare av innehåll."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/28/2018
ms.author: mihart
LocalizationGroup: Dashboards
ms.openlocfilehash: 1ad8425917153f2f9662041dc594817857f8f499
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/09/2018
---
# <a name="usage-metrics-for-dashboards-and-reports"></a>Användningsstatistik för instrumentpaneler och rapporter
Om du skapar instrumentpaneler och rapporter kan du med användningsstatistik förstå deras inverkan. Oavsett om du kör användningsstatistik för instrumentpaneler eller rapporter ser du hur dessa instrumentpaneler och rapporter används i hela organisationen – vad som används, av vem och i vilket syfte.  

> [!NOTE]
> Användningsstatistik spårar användningen av rapporter som är inbäddade i SharePoint Online. De spårar även inbäddning av instrumentpaneler och rapporter via flödena användare äger autentiseringsuppgifterna och appen äger autentiseringsuppgifterna. Användningsstatistik spårar inte användning av rapportinbäddning via [publicera till webben](service-publish-to-web.md).

Dessa användningsstatistikrapporter är skrivskyddade. Men du kan anpassa en användningsstatistikrapport med hjälp av ”Spara som”. Detta skapar en helt ny datauppsättning och konverterar den skrivskyddade rapporten till en fullständig Power BI-rapport som du kan redigera. Den anpassade rapporten innehåller inte bara mått för vald instrumentpanel eller rapport, utan genom att ta bort standardfiltret har du nu tillgång till användningsstatistik för alla instrumentpaneler och rapporter i den valda arbetsytan.

![användningsstatistikrapport](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

## <a name="why-are-usage-metrics-important-to-me"></a>Varför är användningsstatistik viktigt för mig?
Genom att känna till hur ditt innehåll används ser du vilken inverkan det har och du kan prioritera dina åtgärder. Användningsstatistik kan t.ex. visa att en av dina rapporter används dagligen av en stor del av organisationen eller att en instrumentpanel som du har skapat inte används alls. Den här typen av feedback är ovärderlig vid planeringen av ditt arbete.

Det går bara att köra användningsstatistikrapporter i Power BI-tjänsten.  Men om du sparar användningsstatistikrapporten eller fäster den på en instrumentpanel kan du öppna och interagera med rapporten på mobila enheter.

### <a name="prerequisites"></a>Förutsättningar
- Användningsstatistikfunktionen samlar in användningsinformation från alla användare, både kostnadsfria och Pro. Dock krävs det en Pro-licens för att kunna köra och få åtkomst till användningsstatistikdata.
- Användningsstatistiken finns i instrumentpaneler och rapporter på den valda arbetsytan. För att få åtkomst till användningsstatistik för en viss instrumentpanel eller rapport, måste du:    
    • Ha redigeringsåtkomst till instrumentpanelen eller rapporten   
    • Ha en Pro-licens

## <a name="about-the-usage-metrics-report"></a>Om användningsstatistikrapporten


När du väljer **Användningsstatistik** eller ikonen ![användningsstatistikikon](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png) skapar Power BI en färdig rapport med användningsstatistik för innehållet under de senaste 90 dagarna.  Rapporten liknar de Power BI-rapporter som du redan är bekant med, men den har utformats för att vara informativ – inte interaktiv. Du kommer att kunna segmentera innehållet baserat på hur dina slutanvändare har åtkomst till det, t.ex. via webben eller en mobilapp. Allt eftersom dina instrumentpaneler och rapporter utvecklas, kommer även användningsstatistikrapporten göra det, med dagliga uppdateringar av nya data.  

Användningsstatistikrapporterna visas inte i **Senaste**, **Arbetsytor**, **Favoriter** eller andra innehållslistor. De kan inte läggas till i en app. Om du fäster en panel från en användningsstatistikrapport på en instrumentpanel går det inte att lägga till instrumentpanelen i en app eller ett innehållspaket.

Fördjupa dig i rapportdatan eller skapa egna rapporter mot datauppsättningen med **Spara som** (se [Spara användningsstatistikrapporten som en fullständig Power BI-rapport](#save-the-usage-metrics-report-as-a-full-featured-power-bi-report).

## <a name="open-a-usage-metrics-report-for-a-dashboard-or-report"></a>Öppna en användningsstatistikrapport för en instrumentpanel eller rapport
1. Starta från arbetsytan som innehåller instrumentpanelen eller rapporten.
2. Gå antingen till arbetsytans innehållslista, instrumentpanelen eller själva rapporten och välj ikonen **Användningsstatistik** ![användningsstatistikikon](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png).
   
    ![Fliken Instrumentpaneler](media/service-usage-metrics/power-bi-run-usage-metrics-report.png)
   
    ![välj Användningsstatistik](media/service-usage-metrics/power-bi-run-usage-metrics-report2.png)
3. Första gången du gör detta skapar Power BI användningsstatistikrapporten och talar om för dig när den är klar.
   
    ![uppdateringarna är klara](media/service-usage-metrics/power-bi-usage-metrics-ready.png)    
4. Om du vill öppna resultaten väljer du **Visa användningsstatistik**.
   
    Användningsstatistiken blir en kraftfull bundsförvant när du arbetar med att distribuera och underhålla Power BI-instrumentpaneler och rapporter. Undrar du vilka sidor i rapporten som är mest användbara och vilka som du bör fasa ut? Ta ett utsnitt efter **Rapportsida** för att ta reda på det. Undrar du om du ska skapa en mobil layout för instrumentpanelen? Ta ett utsnitt efter **Plattformar** för att upptäcka hur många användare som har åtkomst till ditt innehåll via mobilappar kontra webbläsaren.

5. Du kan även hovra över en visualisering och välja fäst-ikonen för att lägga till visualiseringen på en instrumentpanel. Eller välj **Fäst Live-sidan** från den översta menyraden för att lägga till hela sidan på en instrumentpanel. Från instrumentpanelen kan du övervaka användningsstatistik enklare eller dela dem med andra.
   
   > **Obs**! Om du fäster en panel från en användningsstatistikrapport på en instrumentpanel går det inte att lägga till instrumentpanelen i en app eller ett innehållspaket.
   > 
   > 

<br><br>

## <a name="what-metrics-are-reported"></a>Vilka mått rapporteras?
| Mått | Instrumentpanel | Rapport | Beskrivning |
| --- | --- | --- | --- |
| Distributionsmetod för utsnitt |ja |ja |Hur användare får åtkomst till innehållet. Det finns tre möjliga sätt: Användarna kan få åtkomst till instrumentpanelen eller rapporten genom att vara medlemmar i en [apparbetsyta](service-the-new-power-bi-experience.md), genom att låta innehållet [delas med dem](service-share-dashboards.md) eller genom att installera ett innehållspaket eller en app.  Observera att vyer via en app räknas som ”innehållspaket”. |
| Plattformsutsnitt |ja |ja |Användes instrumentpanelen eller rapporten via Power BI-tjänsten (powerbi.com) eller en mobil enhet? Mobilt innefattar alla våra iOS-, Android- och Windows-appar. |
| Utsnitt för rapportsidan |nej |ja |Om rapporten innehåller mer än en sida kan du dela upp rapporten i den sida eller de sidor som visades. Om du ser listalternativet ”Tom” betyder det att en rapportsida nyligen lagts till (inom 24 timmar kommer det riktiga namnet på den nya sidan visas i listan med utsnitt) och/eller att rapportsidor har tagits bort. I ”Tom” finns dessa typer av situationer. |
| Visningar per dag |ja |ja |Totalt antal visningar per dag – en visning definieras när en användare läser in en rapportsida eller instrumentpanel. |
| Unika användare per dag |ja |ja |Antal *olika* användare som visat instrumentpanelen eller rapporten (baserat på AAD-användarkontot). |
| Visningar per användare |ja |ja |Antal visningar de senaste 90 dagarna, fördelat på enskilda användare. |
| Delningar per dag |ja |nej |Antal gånger som instrumentpanelen har delats med en annan användare eller grupp. |
| Totalt antal visningar |ja |ja |Antal visningar de senaste 90 dagarna. |
| Totalt antal användare |ja |ja |Antal unika användare de senaste 90 dagarna. |
| Totalt antal delningar |ja |nej |Antal gånger instrumentpanelen eller rapporten har delats under de senaste 90 dagarna. |
| Totalt i organisationen |ja |ja |Antal instrumentpaneler och rapporter i hela organisationen som har minst en visning under de senaste 90 dagarna.  Används för att beräkna rangordning. |
| Rangordning: Totalt antal visningar |ja |ja |Visar hur instrumentpanelen eller rapporten rangordnas vid totalt antal visningar för alla instrumentpaneler och rapporter i organisationen under de senaste 90 dagarna. |
| Rangordning: Totalt antal delningar |ja |nej |Visar hur instrumentpanelen eller rapporten rangordnas vid totalt antal delningar för alla instrumentpaneler i organisationen under de senaste 90 dagarna. |

### <a name="dashboard-usage-metrics-report"></a>Användningsstatistikrapport för instrumentpanel
![Användningsstatistikrapport för instrumentpanel](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

### <a name="report-usage-metrics-report"></a>Användningsstatistikrapport för rapport
![Användningsstatistikrapport för rapport](media/service-usage-metrics/power-bi-report-usage-metrics-update.png)

## <a name="save-the-usage-metrics-report-as-a-full-featured-power-bi-report-personalize"></a>Spara användningsstatistikrapporten som en fullständig Power BI-rapport (anpassa)

![Spara som](media/service-usage-metrics/power-bi-save-as.png)

Använd **Spara som** för att konvertera användningsstatistikrapporten till en fullständig Power BI-rapport som kan anpassas och delas. När du har skapat en anpassad kopia får du fullständig åtkomst till den underliggande datauppsättningen, så att du kan anpassa användningsstatistikrapporten för dina specifika behov. Du kan även använda Power BI Desktop till att skapa anpassade användningsstatistikrapporter med hjälp av [live-anslutningen till Power BI-tjänstfunktionen](https://powerbi.microsoft.com/blog/connecting-to-datasets-in-the-power-bi-service-from-desktop).

Den underliggande datauppsättningen innehåller dessutom användningsinformation för alla instrumentpaneler och rapporter på arbetsytan. Detta öppnar ännu en värld av möjligheter. Du kan till exempel skapa en rapport som jämför alla instrumentpaneler i arbetsytan baserat på deras användning. Eller skapa en instrumentpanel för användningsstatistik i Power BI-appen genom att sammanställa användningen för allt innehåll som distribueras inom appen.  Se [Ta bort sidnivåfiltret](#remove-the-filter-to-see-all-the-usage-metrics-data-in-the-workspace) nedan.

### <a name="what-is-created-when-using-save-as"></a>Vad skapas när du använder ”Spara som”?
När Power BI skapar den fullständiga rapporten, skapas dessutom en ny datauppsättning **som består av alla instrumentpaneler eller alla rapporter som ingår i den aktuella arbetsytan** och som har använts under de senaste 90 dagarna. Anta exempelvis att du har en arbetsyta med namnet ”Försäljning” med tre instrumentpaneler och två rapporter och du skapar en användningsstatistikrapport på instrumentpanelen ”Nordöst”. Därefter använder du **Spara som** för att anpassa och konvertera den till en fullständig rapport. Datauppsättningen för den nya rapporten innehåller användningsstatistik, *inte bara för den instrumentpanel som har namnet ”Nordöst”*, utan för alla tre instrumentpanelerna i arbetsytan ”Försäljning”. Som standard visar rapporten data för instrumentpanelen ”Nordöst” och du måste [ta bort ett filter](#remove-the-filter-to-see-all-the-usage-metrics-data-in-the-workspace) (enkel klickning) för att visa data för alla tre instrumentpaneler.

### <a name="create-a-copy-of-the-usage-report-using-save-as"></a>Skapa en kopia av användningsrapporten med ”Spara som”
När du skapar en kopia med ”Spara som” (anpassa), konverterar Power BI den skrivskyddade färdiga rapporten till en fullständig rapport.  Vid en första titt ser den exakt likadan ut. Men nu kan du öppna rapporten i vyn Redigering, lägga till nya visualiseringar, filter och sidor, ändra eller ta bort befintliga visualiseringar och mycket mer. Power BI sparar den helt nya rapporten och datauppsättningen i den aktuella arbetsytan. I exemplet nedan är den aktuella arbetsytan **mihart**.


1. Från den färdiga användningsstatistikrapporten väljer du **Arkiv > Spara som**. Power BI konverterar användningsstatistikrapporten till en fullständig Power BI-rapport. Detta kallas en *anpassad* användningsstatistikrapport. Den anpassade användningsrapporten och datauppsättningen sparas i den aktuella arbetsytan som heter **mihart*.
   
    ![Spara som](media/service-usage-metrics/power-bi-save-as.png)
2. Öppna rapporten i redigeringsvyn och [interagera med den precis som med andra Power BI-rapporter](service-interact-with-a-report-in-editing-view.md). Du kan till exempel lägga till nya sidor och skapa nya visualiseringar, lägga till filter, formatera teckensnitt och färger etc.
   
    ![öppna en rapport i redigeringsvyn](media/service-usage-metrics/power-vi-editing-view.png)
3. Alternativt kan du starta med den nya datauppsättningen och skapa en rapport från grunden.
   
    ![Fliken Datauppsättningar](media/service-usage-metrics/power-bi-new-dataset.png)
4. Den nya rapporten sparas i den aktuella arbetsytan (miheart) och läggs också till i innehållslistan **Senaste**.
   
    ![Fliken Rapporter](media/service-usage-metrics/power-bi-new-report.png)

### <a name="remove-the-filter-to-see-all-the-usage-metrics-data-in-the-workspace"></a>Ta bort filtret för att se ***all*** användningsstatistik i arbetsytan
Om du vill visa mått för alla instrumentpaneler eller för alla rapporter i arbetsytan måste du ta bort ett filter. Som standard filtreras den anpassade rapporten till att visa mått för enbart den instrumentpanel eller rapport som användes för att skapa den.

Om du t.ex. använde instrumentpanelen med namnet ”Europeisk försäljning” till att skapa den nya anpassade rapporten, kommer endast användningsdata från instrumentpanelen ”Europeisk försäljning” att visas. Ta bort filtret och aktivera data från alla instrumentpaneler i arbetsytan:

1. Öppna den anpassade rapporten i redigeringsvyn.
   
    ![välj Redigera rapport](media/service-usage-metrics/power-bi-editing-view.png)
2. I fönstret Filter letar du reda på **Rapportnivåfilter** och tar bort filtret genom att välja ”x”.
   
    ![ta bort filtret](media/service-usage-metrics/power-bi-report-level-filter2.png)
   
    Din anpassade rapport visar nu mått för hela arbetsytan.

## <a name="admin-controls-for-usage-metrics---for-power-bi-administrators"></a>Administratörskontroller för användningsstatistik – för Power BI-administratörer
Användningsstatistikrapporter är en funktion som Power BI- eller Office 365-administratören kan aktivera eller inaktivera. Administratörerna har detaljerad kontroll över vilka användare som har åtkomst till användningsstatistiken. De är aktiverade som standard för alla användare i organisationen.

1. Öppna administrationsportalen genom att välja kugghjulsikonen i det översta högra hörnet av Power BI-tjänsten. Välj sedan **Administratörsportalen**.
   
    ![välj kugghjulsikonen](media/service-usage-metrics/power-bi-admin-portal-new.png)
2. Från Administratörsportalen väljer du **Klientinställningar** och **Användningsstatistik för skapare av innehåll**.
   
    ![Administratörsportal](media/service-usage-metrics/power-bi-usage-settings.png)
3. Aktivera (eller inaktivera) användningsstatistik och välj **Tillämpa**.
   
    ![Aktiverad användningsstatistik](media/service-usage-metrics/power-bi-tenant-settings-updated.png)

När du inaktiverar användningsstatistik för hela organisationen kan administratörerna använda alternativet **Ta bort allt befintligt innehåll för användningsstatistik** för att ta bort alla befintliga rapporter och instrumentpaneler som har skapats med användningsstatistikrapporter och datauppsättningar. Det här alternativet tar bort all åtkomst till användningsstatistiken för alla användare i organisationen som kanske redan använder den. Var försiktig, eftersom det inte går att ångra när du har tagit bort befintligt användningsstatistikinnehåll.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
F:    Jag kan inte köra användningsstatistik i en instrumentpanel eller rapport    
S:    Du kan endast se användningsstatistik för innehåll som du äger eller har behörighet att redigera.

F:    Kommer användningsstatistiken hämta visningar från inbäddade instrumentpaneler och rapporter?     
S:    Användningsstatistiken stöder för närvarande inte att hämta användning för inbäddade instrumentpaneler och rapporter, inklusive flödena [Användaren äger data](developer/integrate-report.md), [Appen äger data](developer/embed-sample-for-customers.md) och [Publicera på webben](service-publish-to-web.md). I sådana fall rekommenderar vi att du använder befintliga webbanalysplattformar till att spåra användningen för värdappen eller portalen.

F:    Jag kan inte köra användningsstatistik på något innehåll alls.    
A1:    Administratörer kan stänga av den här funktionen för organisationen.  Kontakta administratören för att ta reda på om detta är fallet.    
A2:    Användningsstatistik är en funktion i Power BI Pro.

F:    Mina data verkar inte vara uppdaterade. Till exempel visas inte fördelningsmetoderna och rapportsidor saknas.   
S:    Det kan ta upp till 24 timmar innan data uppdateras.

F:    Det finns fyra rapporter på arbetsytan men användningsstatistikrapporten visar endast tre.    
S:    Användningsstatistikrapporten innehåller endast rapporter (eller instrumentpaneler) som har använts under de senaste 90 dagarna.  Om en rapport (eller instrumentpanel) inte visas har den sannolikt inte använts de senaste 90 dagarna.

## <a name="next-steps"></a>Nästa steg
[Favoritmarkera en instrumentpanel](service-dashboard-favorite.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

