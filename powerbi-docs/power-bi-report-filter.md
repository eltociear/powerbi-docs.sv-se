---
title: Den nya filterupplevelsen i Power BI-rapporter
description: Filter i Power BI får nya funktioner och en ny design.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: ab7d8a34211b9cb8addd90daf2cbce7d22f10e61
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73875150"
---
# <a name="the-new-filter-experience-in-power-bi-reports"></a>Den nya filterupplevelsen i Power BI-rapporter

Filtren i Power BI har nya funktioner och en ny design. När du väljer den nya filtermiljön, kan du formatera fönstret Filter så att det ser ut som resten av rapporten. Du kan låsa och till och med dölja filter. När du skapar din rapport, visas inte längre det gamla filterfönstret alls i fönstret Visualiseringar. Du kan göra all din filterredigering och -formatering i ett enda filterfönster. 

![Ny filterupplevelse](media/power-bi-report-filter/power-bi-filter-new-look.png)

Det här är vad du kan göra i det nya fönstret för filter som rapportdesigner:

- Lägga till och ta bort fält att filtrera på. 
- Ändra filterstatusen.
- Formatera och anpassa filterfönstret så att det känns som en del av din rapport.
- Definiera om Filter-fönstret är öppet eller minimerat som standard när en användare öppnar rapporten.
- Dölja hela filterfönstret eller specifika filter som du inte vill att rapportanvändarna ser.
- Styra och till och med bokmärka synlighet och öppet och minimerat tillstånd för det nya filterfönstret.
- Lås filter som du inte vill att användarna ska kunna redigera.

Med den nya filterupplevelsen kan rapportkonsumenter även hovra över valfritt visuellt objekt för att visa en skrivskyddad lista över alla filter eller utsnitt som påverkar det aktuella visuella objektet.

![Lista över filter för ett visuellt objekt](media/power-bi-report-filter/power-bi-filter-visual.png)

## <a name="turn-on-the-new-filter-experience"></a>Aktivera den nya filterupplevelsen 

Den nya filterupplevelsen är aktiverad som standard för nya rapporter. Du kan aktivera den nya upplevelsen för befintliga rapporter i Power BI Desktop eller Power BI-tjänsten.

### <a name="turn-on-new-filters-for-an-existing-report-in-power-bi-desktop"></a>Aktivera nya filter för en befintlig rapport i Power BI Desktop

1. I Power BI Desktop i en befintlig rapport väljer du **Arkiv** > **Alternativ och inställningar** > **Alternativ**
2. I navigeringsfönstret under **Aktuell fil** väljer du **Rapportinställningar**.
3. Under **Filtreringsupplevelse** väljer du **Aktivera det uppdaterade filterfönstret och visa filter i det visuella sidhuvudet för den här rapporten**.

### <a name="turn-on-new-filters-for-an-existing-report-in-the-service"></a>Aktivera nya filter för en befintlig rapport i tjänsten

Om du har aktiverat **Nytt utseende** i Power BI-tjänsten ![Nytt utseende på](media/power-bi-report-filter/power-bi-new-look-on.png), aktiveras den nya filterupplevelsen automatiskt. Läs mer om det [nya utseendet i Power BI-tjänsten](service-new-look.md).

Om du inte har aktiverat det nya utseendet kan du fortfarande se den nya filterupplevelsen genom att följa nedanstående steg.

1. I Power BI-tjänsten väljer fliken **Rapporter** i innehållslistan för en arbetsyta.
2. Leta upp den rapport som du vill aktivera och välj ikonen **Settings** ![ikonen Rapportinställningar](media/power-bi-report-filter/power-bi-settings-icon.png) för den rapporten.
3. Under **Filtreringsupplevelse** väljer du **Aktivera det uppdaterade filterfönstret och visa filter i det visuella sidhuvudet för den här rapporten**.

    ![Aktivera det uppdaterade filterfönstret](media/power-bi-report-filter/power-bi-service-filter-enable.png)

## <a name="view-filters-for-a-visual-in-reading-mode"></a>Visa filter för ett visuellt objekt i Läsläge

I Läsläge kan du hovra över filterikonen för att se en popup-filterlista med alla filter, sektorer och så vidare som påverkar det visuella objektet. Formateringen av popup-filterlistan är densamma som för filterfönstret. 

![Filter som påverkar ett visuellt objekt](media/power-bi-report-filter/power-bi-filter-per-visual.png)

Här är de typer av filter som den här vyn visar: 
- Grundläggande filter
- Utsnitt
- Korsmarkering 
- Korsfiltrering
- Avancerad filtrering
- Högsta N-filter
- Relativa datumfiltrer
- Synkroniseringsutsnitt
- Inkludera/exkludera filter
- Filter som skickas via en URL

## <a name="build-the-new-filters-pane"></a>Skapa det nya filterfönstret

När du aktiverar det nya filterfönstret så ser du det till höger på rapportsidan, som standard formaterat baserat på dina aktuella rapportinställningar. Du kan använda det nya filterfönstret för att konfigurera vilka filter som ska ingå och för att uppdatera befintliga filter i det nya fönstret. Det nya filterfönstret visar vad dina rapportanvändare får se när du publicerar din rapport. 

1. Dina rapportkonsumenter kan se filterfönstret som standard. Om du inte vill att de ska se det, väljer du ögonikonen bredvid **Filter**.

    ![Ögonikonen för Power BI-filter](media/power-bi-report-filter/power-bi-filter-eye.png)

2. Börja bygga ditt nya filterfönster genom att dra fält av intresse till det nya filterfönstret, som filter för visuellt objekt-, sid- eller rapportnivå.

När du lägger till ett visuellt objekt på en rapportarbetsyta lägger Power BI automatiskt till ett filter i filterfönstret för varje fält i det visuella objektet. 

## <a name="lock-or-hide-filters"></a>Låsa eller dölja filter

Du kan låsa eller dölja enskilda filterkort. Om du låser ett filter, kan dina rapportanvändare se men inte ändra det. Om du döljer det så kan de inte ens se det. Det är användbart att dölja filterkort om du vill dölja datarensningsfilter som exkluderar nullvärden eller oväntade värden. 

- I det nya filterfönstret markerar eller avmarkerar du ikonerna **Låsfilter** eller **Dölj filter** på ett filterkort.

   ![Dölj eller lås filter](media/power-bi-report-filter/power-bi-filter-lock-hide.png)

När du aktiverar eller inaktiverar de här inställningarna i det nya filterfönstret så ser du ändringarna i rapporten. Dolda filter visas inte i popup-filterlistan för ett visuellt objekt.

Du kan även konfigurera statusen för det nya filterfönstret så att stämmer överens med dina rapportbokmärken. Fönstrets status för öppna, stäng och synlighet går alla att bokmärka.
 
## <a name="format-the-new-filters-pane"></a>Formatera det nya Filter-fönstret

En stor del av den här nya upplevelsen är att du kan formatera filterfönstret för att matcha utseendet och känslan i din rapport. Du kan formatera filterfönstret på olika sätt för varje sida i rapporten. Här följer element som du kan formatera: 

- Bakgrundsfärg
- Bakgrundstransparens
- Kantlinje på eller av
- Färg på kantlinje
- Teckensnitt, färg och textstorlek för rubrik och huvud

Du kan också formatera de här elementen för filterkort, beroende på om de används (är inställda på något) eller tillgängliga (rensade): 

- Bakgrundsfärg
- Bakgrundstransparens
- Kantlinje: på eller av
- Färg på kantlinje
- Teckensnitt, färg och textstorlek
- Färg på textruta

### <a name="format-the-filters-pane-and-cards"></a>Formatera filterfönstret och korten

1. I rapporten klickar du på själva rapporten eller på bakgrunden (*skrivbordsunderlägget*) därefter går du till **Visualiseringar** och väljer **Format**. 
    Du ser alternativ för att formatera rapportsidan, skrivbordsunderlägget och även filterfönstret och filterkort.

1. Expandera **Filter-fönstret** för att ange färg för bakgrund, ikon och vänster kantlinje så att de matchar rapportsidan.

    ![Expandera Filter-fönster](media/power-bi-report-filter/power-bi-format-filter-pane.png)

1. Expandera **Filterkort** för att ange färg och kantlinje för **Tillgänglig** och **Använd**. Om du gör korten tillgänglig och använd olika färger så blir det uppenbart vilka filter som används. 
  
    ![Expandera Filter-kortet](media/power-bi-report-filter/power-bi-format-filter-cards.png)

## <a name="theming-for-filter-pane"></a>Teman för filterfönstret
Du kan nu ändra standardinställningarna för filterfönstret med temafilen. Här är ett avsnitt ur ett exempeltema som du kan använda för att komma igång:

 
```
"outspacePane": [{ 

"backgroundColor": {"solid": {"color": "#0000ff"}}, 

"foregroundColor": {"solid": {"color": "#00ff00"}}, 

"transparency": 50, 

"titleSize": 35, 

"headerSize": 8, 

"fontFamily": "Georgia", 

"border": true, 

"borderColor": {"solid": {"color": "#ff0000"}} 

}], 

"filterCard": [ 

{ 

"$id": "Applied", 

"transparency": 0, 

"backgroundColor": {"solid": {"color": "#ff0000"}}, 

"foregroundColor": {"solid": {"color": "#45f442"}}, 

"textSize": 30, 

"fontFamily": "Arial", 

"border": true, 

"borderColor": {"solid": {"color": "#ffffff"}}, 

"inputBoxColor": {"solid": {"color": "#C8C8C8"}} 

}, 

{ 

"$id": "Available", 

"transparency": 40, 

"backgroundColor": {"solid": {"color": "#00ff00"}}, 

"foregroundColor": {"solid": {"color": "#ffffff"}}, 

"textSize": 10, 

"fontFamily": "Times New Roman", 

"border": true, 

"borderColor": {"solid": {"color": "#123456"}}, 

"inputBoxColor": {"solid": {"color": "#777777"}} 

}] 
```

## <a name="sort-the-filter-pane"></a>Sortera filterfönstret

En anpassad sorteringsfunktion ingår i det nya filterfönstret. Rapportskapare kan dra och släppa filter för att ordna om dem i den ordning som de önskar.

![Ändra sorteringsordning för filter](media/power-bi-report-filter/power-bi-filter-sort.gif)

Standardordningen för sortering är alfabetisk för filter. För att börja anpassa sorteringsläget drar du bara ett filter till en ny plats. Du kan bara sortera filter inom den nivå som de gäller för, till exempel visuell nivå, sidnivå eller rapportnivå.

## <a name="improved-filters-pane-accessibility"></a>Förbättrad åtkomst till filterfönstret

Vi har förbättrat tangentbordsnavigeringen för det nya filterfönstret. Du kan växla mellan alla delar i filterfönstret och använda snabbtangenten på tangentbordet eller Shift + F10 för att öppna snabbmenyn.

![Åtkomst till filterfönstret](media/power-bi-report-filter/power-bi-filter-accessible.png)

## <a name="rename-filters"></a>Byta namn på filter
När du redigerar filterfönstret kan du dubbelklicka på rubriken för att redigera den. Att kunna byta namn är användbart om du vill uppdatera filterkortet så att det verkar mer logiskt för dina slutanvändare. Tänk på att namnbytet för filterkortet *inte* medför att namnet på visningsnamnet för fältet i fältlistan ändras. Det ändrar bara det visningsnamn som används på filterkortet.

![Byta namn på ett filter](media/power-bi-report-filter/power-bi-filter-rename.png)

## <a name="restrict-changes-to-filter-type"></a>Begränsa ändringar efter filtertyp

Under avsnittet Filtreringsupplevelse i rapportinställningarna har du möjlighet att ange om användarna ska kunna ändra filtertypen.

![Begränsa ändringar av filtertyp](media/power-bi-report-filter/power-bi-filter-restrict-change.png)

## <a name="next-steps"></a>Nästa steg

Testa den nya filterupplevelsen. Lämna gärna feedback om den här funktionen och hur vi kan fortsätta att förbättra den på [Power BI:s webbplats för idéer](https://ideas.powerbi.com/forums/265200-power-bi). 

- [Så här använder du rapportfilter](consumer/end-user-report-filter.md)
- [Filtrera och markera i rapporter](power-bi-reports-filters-and-highlighting.md)
- [Olika typer av filter i Power BI](power-bi-report-filter-types.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

