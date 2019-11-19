---
title: Övervaka användningsstatistik för instrumentpaneler och rapporter
description: Så här visar, sparar och använder du användningsstatistik för Power BI-instrumentpaneler och rapporter.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/21/2019
LocalizationGroup: Dashboards
ms.openlocfilehash: 9aa2e11dd2068cae118336268c5c55ead1e25b8b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871208"
---
# <a name="monitor-usage-metrics-for-power-bi-dashboards-and-reports"></a>Övervaka användningsstatistik för Power BI-instrumentpaneler och -rapporter

Om du skapar instrumentpaneler och rapporter kan du med användningsstatistik förstå deras inverkan. Oavsett om du kör användningsstatistik för instrumentpaneler eller rapporter ser du hur dessa instrumentpaneler och rapporter används i hela organisationen, av vem och i vilket syfte.  

Dessa användningsstatistikrapporter är skrivskyddade. Du kan dock kopiera en användningsstatistikrapport. När du kopierar skapas en standard Power BI-rapport som du kan redigera. Du kan också skapa egna rapporter i Power BI Desktop baserat på den underliggande datauppsättningen, som innehåller användningsstatistik för alla instrumentpaneler och rapporter i en arbetsyta. Till att börja med visar den kopierade rapporten endast mått för den valda instrumentpanelen eller rapporten. Du kan ta bort standardfiltret och få åtkomst till den underliggande datauppsättningen med all användningsstatistik för den valda arbetsytan. Du kan även se namnen på specifika användare om detta tillåts av din administratör.

![användningsstatistikrapport](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

> [!NOTE]
> Användningsstatistik spårar användningen av rapporter som är inbäddade i SharePoint Online. Dock spårar inte användningsstatistik inbäddning av instrumentpaneler och rapporter via flödena ”användare äger autentiseringsuppgifterna” och ”appen äger autentiseringsuppgifterna”. Användningsstatistik spårar inte heller användning av rapportinbäddning via [publicera till webben](service-publish-to-web.md).

## <a name="why-usage-metrics-are-important"></a>Därför är användningsstatistik viktigt

Genom att känna till hur ditt innehåll används ser du vilken inverkan det har och du kan prioritera dina åtgärder. Användningsstatistik kan t.ex. visa att en av dina rapporter används dagligen av en stor del av organisationen eller att en instrumentpanel som du har skapat inte används alls. Den här typen av feedback är ovärderlig vid planeringen av ditt arbete.

Du kan bara köra användningsstatistikrapporter i Power BI-tjänsten. Men om du sparar användningsstatistikrapporten eller fäster den på en instrumentpanel kan du öppna och interagera med rapporten på mobila enheter.

## <a name="prerequisites"></a>Förutsättningar

- Det krävs en Power BI Pro-licens för att kunna köra och få åtkomst till användningsstatistikdata. Användningsstatistikfunktionen samlar dock in användningsinformation från alla användare, oavsett vilken licens de har tilldelats.
- För att få åtkomst till användningsstatistik för en viss instrumentpanel eller rapport, måste du ha skrivrättigheter till denna.
- Power BI-administratören måste ha aktiverat användningsstatistik för skapare av innehåll. Power BI-administratören kan också har aktiverat insamling av data per användare i användningsmått. Läs mer om att [aktivera dessa alternativ i administratörsportalen](service-admin-portal.md#control-usage-metrics). 

## <a name="view-a-usage-metrics-report"></a>Visa en rapport om användningsstatistik

1. Starta från arbetsytan som innehåller instrumentpanelen eller rapporten.
2. Gå antingen till arbetsytans innehållslista, instrumentpanelen eller själva rapporten och välj ikonen **Användningsstatistik** ![användningsstatistikikon](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png).

    ![Fliken Instrumentpaneler](media/service-usage-metrics/power-bi-run-usage-metrics-report.png)

    ![välj Användningsstatistik](media/service-usage-metrics/power-bi-run-usage-metrics-report2.png)
3. Första gången du gör detta skapar Power BI användningsstatistikrapporten och talar om för dig när den är klar.

    ![uppdateringarna är klara](media/service-usage-metrics/power-bi-usage-metrics-ready.png)
4. Om du vill se resultaten väljer du **Visa användningsstatistik**.

    Användningsstatistiken är en kraftfull bundsförvant när du arbetar med att distribuera och underhålla Power BI-instrumentpaneler och rapporter. Undrar du vilka sidor i rapporten som är mest användbara och vilka som du bör fasa ut? Ta ett utsnitt efter **Rapportsida** för att ta reda på det. Undrar du om du ska skapa en mobil layout för instrumentpanelen? Ta ett utsnitt efter **Plattformar** för att upptäcka hur många användare som har åtkomst till ditt innehåll via mobilappar kontra webbläsaren.

5. Du kan även hovra över en visualisering och välja fäst-ikonen för att lägga till visualiseringen på en instrumentpanel. Eller välj **Fäst Live-sidan** från den översta menyraden för att lägga till hela sidan på en instrumentpanel. Från instrumentpanelen kan du övervaka användningsstatistik enklare eller dela dem med andra.

    > [!NOTE]
    > Om du fäster en panel från en användningsstatistikrapport på en instrumentpanel går det inte att lägga till instrumentpanelen i en app.

### <a name="dashboard-usage-metrics-report"></a>Användningsstatistikrapport för instrumentpanel

![Användningsstatistikrapport för instrumentpanel](media/service-usage-metrics/power-bi-dashboard-usage-metrics-update-3.png)

### <a name="report-usage-metrics-report"></a>Användningsstatistikrapport för rapport

![Användningsstatistikrapport för rapport](media/service-usage-metrics/power-bi-report-usage-metrics-update.png)

## <a name="about-the-usage-metrics-report"></a>Om användningsstatistikrapporten

När du väljer **Användningsstatistik** eller ikonen ![användningsstatistikikon](media/service-usage-metrics/power-bi-usage-metrics-report-icon.png) intill en instrumentpanel eller rapport skapar Power BI en färdig rapport med användningsstatistik för innehållet under de senaste 90 dagarna.  Rapporten liknar de Power BI-rapporter som du redan är bekant med. Du kommer att kunna segmentera innehållet baserat på hur dina slutanvändare har åtkomst till det, t.ex. via webben eller en mobilapp. Allt eftersom dina instrumentpaneler och rapporter utvecklas, kommer även användningsstatistikrapporten göra det, med dagliga uppdateringar av nya data.  

Användningsstatistikrapporterna visas inte i **Senaste**, **Arbetsytor**, **Favoriter** eller andra innehållslistor. De kan inte läggas till i en app. Om du fäster en panel från en användningsstatistikrapport på en instrumentpanel går det inte att lägga till instrumentpanelen i en app.

För att analysera rapportdata för att bygga dina egna rapporter mot den underliggande datauppsättningen har du två alternativ: 

- Skapa en kopia av en rapport i Power BI-tjänsten. Se [Spara en kopia av användningsstatistikrapporten](#save-a-copy-of-the-usage-metrics-report) senare i den här artikeln för information.
- Anslut till datauppsättningen från Power BI Desktop. För varje arbetsyta har datamängden namnet ”Report Usage Metrics Model” (Modell för mått av användningsstatistik). Se [upprätta en anslutning till en publicerad datauppsättning](desktop-report-lifecycle-datasets.md#establish-a-power-bi-service-live-connection-to-the-published-dataset) för mer information.

    ![Ansluta till en datauppsättning för rapportanvändning](media/service-usage-metrics/power-bi-usage-dataset.png)

## <a name="which-metrics-are-reported"></a>Vilka mått rapporteras?

| Mått | Instrumentpanel | Rapport | Beskrivning |
| --- | --- | --- | --- |
| Distributionsmetod för utsnitt |ja |ja |Hur användare får åtkomst till innehållet. Det finns tre metoder: användarna kan få åtkomst till instrumentpanelen eller rapporten genom att vara medlemmar i en [arbetsyta](consumer/end-user-experience.md), genom att innehållet [delas med dem](service-share-dashboards.md) eller genom att installera ett innehållspaket eller en app.  Observera att vyer via en app räknas som ”innehållspaket”. |
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

## <a name="save-a-copy-of-the-usage-metrics-report"></a>Spara en kopia av användningsstatistikrapporten

Använd **Spara som** för att konvertera användningsstatistikrapporten till en vanlig Power BI-rapport som du kan anpassa efter dina specifika behov. Du kan också använda Power BI Desktop för att skapa anpassade användningsstatistikrapporter baserat på den underliggande datauppsättningen. Se [upprätta en anslutning till en publicerad datauppsättning](desktop-report-lifecycle-datasets.md#establish-a-power-bi-service-live-connection-to-the-published-dataset) för mer information.

Den underliggande datauppsättningen innehåller dessutom användningsinformation för alla instrumentpaneler och rapporter på arbetsytan. Det öppnar upp fler möjligheter. Du kan till exempel skapa en rapport som jämför alla instrumentpaneler i arbetsytan baserat på deras användning. Eller skapa en instrumentpanel för användningsstatistik i Power BI-appen genom att sammanställa användningen för allt innehåll som distribueras inom appen.  Se hur du tar bort filtret och [visar all användningsstatistik för arbetsytan](#see-all-workspace-usage-metrics) senare i den här artikeln.

### <a name="create-a-copy-of-the-usage-report"></a>Skapa en kopia av användningsrapporten

När du skapar en kopia av den skrivskyddade färdiga användningsrapporten skapar Power BI en redigerbar kopia av rapporten. Vid första anblicken ser den likadan ut. Men nu kan du öppna rapporten i vyn Redigering, lägga till nya visualiseringar, filter och sidor, ändra eller ta bort befintliga visualiseringar och mycket mer. Power BI sparar den nya rapporten i den aktuella arbetsytan.

1. Från den färdiga användningsstatistikrapporten väljer du **Arkiv > Spara som**. Power BI skapar en redigerbar Power BI-rapport som sparas i den aktuella arbetsytan.

    ![Spara som](media/service-usage-metrics/power-bi-save-as.png)
2. Öppna rapporten i redigeringsvyn och [interagera med den precis som med andra Power BI-rapporter](service-interact-with-a-report-in-editing-view.md). Du kan till exempel lägga till nya sidor och skapa nya visualiseringar, lägga till filter, formatera teckensnitt och färger etc.

    ![Öppna en rapport i redigeringsvyn](media/service-usage-metrics/power-vi-editing-view.png)
3. Den nya rapporten sparas i på fliken **Rapporter** den aktuella arbetsytan och läggs också till i innehållslistan **Senaste**.

    ![Fliken Rapporter](media/service-usage-metrics/power-bi-new-report.png)

## <a name="see-all-workspace-usage-metrics"></a>Visa *all* användningsstatistik för arbetsytor

Om du vill visa mått för alla instrumentpaneler eller för alla rapporter i arbetsytan måste du ta bort ett filter. Som standard filtreras rapporten till att visa mått för enbart den instrumentpanel eller rapport som användes för att skapa den.

1. Välj **Redigera rapport** för att öppna rapporten i redigeringsvyn.

    ![välj Redigera rapport](media/service-usage-metrics/power-bi-editing-view.png)
2. I fönstret Filter letar du reda på **Rapportnivåfilter** och tar bort filtret genom att välja raderingsverktyget intill **ReportGuid**.

    ![Ta bort filtret](media/service-usage-metrics/power-bi-usage-report-clear-filter.png)

    Din rapport visar nu mått för hela arbetsytan.

## <a name="power-bi-admin-controls-for-usage-metrics"></a>Administratörskontroller för Power BI för användningsstatistik

Användningsstatistikrapporter är en funktion som Power BI- eller Office 365-administratören kan aktivera eller inaktivera. Administratörerna har detaljerad kontroll över vilka användare som har åtkomst till användningsstatistiken. De är **aktiverade** som standard för alla användare i organisationen.

> [!NOTE]
> Endast administratörer för Power BI-klienten kan se administratörsportalen och redigera inställningarna. 

Som standard är data per användare aktiverat för användningsstatistik och kontoinformation om konsumenter av innehåll ingår i statistikrapporten. Om administratörer inte vill exponera den här informationen för vissa eller alla användare kan de inaktivera funktionen för specifika säkerhetsgrupper eller hela organisationen. Kontoinformation visas sedan i rapporten som *Namnlös*.

När du inaktiverar användningsstatistik för hela organisationen kan administratörerna använda alternativet **Ta bort allt befintligt innehåll för användningsstatistik** för att ta bort alla befintliga rapporter och instrumentpaneler som har skapats med användningsstatistikrapporter. Det här alternativet tar bort all åtkomst till användningsstatistiken för alla användare i organisationen som kanske redan använder den. Det inte går att ångra när du har tagit bort befintligt användningsstatistikinnehåll.

Se [Kontrollera användningsstatistik](service-admin-portal.md#control-usage-metrics) i administratörsportalartikeln för information om de här inställningarna. 

## <a name="usage-metrics-in-national-clouds"></a>Använda statistik i nationella moln

Power BI finns tillgängligt i enskilda nationella moln. Molnen ger samma nivåer av säkerhet, sekretess, efterlevnad och transparens som den globala versionen av Power BI, kombinerat med en unik modell för lokala föreskrifter om tillhandahållande av tjänster, datahemvist, åtkomst och kontroll. Tack vare denna unika modell för lokala föreskrifter är inte användningsstatistik tillgänglig i nationella moln. Mer information finns i artikeln om [nationella moln](https://powerbi.microsoft.com/clouds/).

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

### <a name="discrepancies-between-audit-logs-and-usage-metrics"></a>Skillnader mellan spårningsloggar och användningsstatistik

Det är viktigt att förstå att skillnader kan uppstå när du jämför användningsstatistik och spårningsloggar och varför. *Spårningsloggar* samlas in med data från Power BI-tjänsten och *användningsstatistik* samlas in från klienten. Det sammanställda antalet aktiviteter i spårningsloggarna överensstämmer inte alltid med användningsstatistiken på grund av följande:

* Användningsstatistik kan ibland underberäkna aktiviteter på grund av inkonsekventa nätverksanslutningar, reklamblockering eller andra problem som kan störa skickandet av händelser från klienten.
* Vissa typer av vyer ingår inte i användningsstatistiken, vilket beskrivs tidigare i den här artikeln.
* Användningsstatistiken kan ibland överberäkna aktiviteter i situationer där klienten uppdateras utan att en begäran behöver skickas tillbaka till Power BI-tjänsten.

### <a name="other-considerations"></a>Ytterligare överväganden

Du måste visa innehållet i din arbetsyta inifrån arbetsytan minst en gång. Om innehållet på arbetsytan inte har minst en visning korreleras inte data om programvisningarna i rapporten med användningsstatistik. Om du vill avblockera bearbetningen av data för den här rapporten visar du innehållet från arbetsytan minst en gång.


## <a name="frequently-asked-questions"></a>Vanliga frågor och svar

Förutom eventuella skillnader mellan användningsstatistik och spårningsloggar så följande frågor och svar om användningsstatistik vara hjälpsamma för användare och administratörer:

**F:**    Jag kan inte köra användningsstatistik i en instrumentpanel eller rapport

**S:**    Du kan endast se användningsstatistik för innehåll som du äger eller har behörighet att redigera.

**F:**    Hämtar användningsstatistiken visningar från inbäddade instrumentpaneler och rapporter?

**S:**    Användningsstatistiken stöder för närvarande inte hämtning av användning för inbäddade instrumentpaneler, rapporter och flödet [publicera till webben](service-publish-to-web.md). I sådana fall rekommenderar vi att du använder befintliga webbanalysplattformar till att spåra användningen för värdappen eller portalen.

**F:**    Jag kan inte köra användningsstatistik på något innehåll alls.

**S1:**    Administratörer kan stänga av den här funktionen för organisationen.  Kontakta administratören för att ta reda på om detta är fallet.

**S2:**    Användningsstatistik är en funktion i Power BI Pro.

**F:**    Mina data verkar inte vara uppdaterade. Till exempel visas inte fördelningsmetoderna och rapportsidor saknas.

**S:**    Det kan ta upp till 24 timmar innan data uppdateras.

**F:**    Det finns fyra rapporter på arbetsytan men användningsstatistikrapporten visar endast tre.

**S:**    Användningsstatistikrapporten innehåller endast rapporter (eller instrumentpaneler) som har använts under de senaste 90 dagarna.  Om en rapport (eller instrumentpanel) inte visas har den sannolikt inte använts de senaste 90 dagarna.

## <a name="next-steps"></a>Nästa steg

[Administrera Power BI i Admin-portalen](service-admin-portal.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
