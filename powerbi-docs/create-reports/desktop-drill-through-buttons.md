---
title: Skapa en knapp för detaljgranskning i Power BI
description: Du kan lägga till knappar för detaljgranskning i Power BI-rapporter som gör att dina rapporter fungerar som appar, och fördjupar engagemanget hos användarna.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/26/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: b1a0548a8c82eb30ccd004268d7ef064e1c0545a
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84121182"
---
# <a name="create-a-drill-through-button-in-power-bi"></a>Skapa en knapp för detaljgranskning i Power BI

Du kan skapa en knapp för *detaljgranskning* i Power BI, en knapp som granskar en sida med information som filtreras till en speciell kontext.

Ett sätt att detaljgranska i en rapport är att högerklicka i ett visuellt objekt. Om du vill att detaljgranskningen ska bli tydligare kan du skapa en knapp för detaljgranskning istället. Knappen kan öka identifierbarheten för viktiga detaljgranskningsscenarier i dina rapporter. Du kan villkorligt bestämma mycket av hur knappen ser ut och fungerar. Du kan till exempel visa olika text på en knapp om vissa villkor är uppfyllda. Läs vidare om du vill veta mer. 

I det här exemplet aktiveras knappen **Se information** när du har valt Word-fältet i diagrammet.

![Knappen Se information](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

När du väljer knappen **Se information** går du vidare till sidan för varukorgsanalys. Som du kan se på det visuella objektet till vänster filtreras nu sidan med detaljerad information för Word.

![Filtrerat visuellt objekt](media/desktop-drill-through-buttons/power-bi-drill-through-destination.png)

## <a name="set-up-a-drill-through-button"></a>Konfigurera en knapp för att gå ner på detaljnivå

Om du vill konfigurera en detaljgranskningsknapp måste du först [konfigurera en giltig sida med detaljerad visning](desktop-drillthrough.md) i rapporten. Sedan måste du skapa en knapp med **Detaljvisning** som åtgärdstyp och välja sidan med detaljvisning som **Mål**.

Eftersom knappen för detaljgranskning har två tillstånd ser du två alternativ för knappbeskrivning.

![Konfigurera en knapp för att gå ner på detaljnivå](media/desktop-drill-through-buttons/power-bi-create-drill-through-button.png)

Om du lämnar rutorna för knappbeskrivningar tomma genererar Power BI automatiskt knappbeskrivningar. Dessa knappbeskrivningar baseras på målet och fältet/fälten för detaljnivån.

Här är ett exempel på den automatiskt genererade knappbeskrivningen när knappen är inaktiverad:

”Om du vill gå vidare till varukorgsanalys [målsidan] väljer du en enskild datapunkt från Produkt [fältet för detaljnivå].”

![Automatiskt genererad knappbeskrivning för inaktiverad](media/desktop-drill-through-buttons/power-bi-drill-through-tooltip-disabled.png)

Och här är ett exempel på den automatiskt genererade knappbeskrivningen när knappen är aktiverad:

”Klicka om du vill visa detaljnivån för varukorgsanalys [målsidan].”

![Automatiskt genererad knappbeskrivning för aktiverad](media/desktop-drill-through-buttons/power-bi-drill-through-visual-button.png)

Men om du vill ange anpassade knappbeskrivningar kan du alltid ange en statisk sträng. Du kan också använda [villkorsstyrd formatering för knappbeskrivningar](#set-formatting-for-tooltips-conditionally).

## <a name="pass-filter-context"></a>Tillämpa filterkontext

Knappen fungerar som den normala detaljgranskningen: Du kan tillämpa filter på ytterligare fält genom att korsfiltrera de visuella objekt som innehåller fältet för detaljgranskning. Om du t.ex. använder **Ctrl** + **klickning** och korsfiltrering kan du tillämpa flera filter från Store till sidan med detaljerad information, eftersom dina val korsfiltrerar det visuella objekt som innehåller Produkt, fältet med detaljnivån:

![Tillämpa filterkontext](media/desktop-drill-through-buttons/power-bi-cross-filter-drill-through-button.png)

När du väljer knappen för detaljgranskning ser du filter för både Butik och Produkt som tillämpas på målsidan:

![Filter på den här sidan](media/desktop-drill-through-buttons/power-bi-button-filters-passed-through.png)

### <a name="ambiguous-filter-context"></a>Tvetydig filterkontext

Eftersom knappen för detaljnivån inte är kopplad till ett enskilt visuellt objekt, inaktiveras knappen om ditt val är tvetydigt.

I det här exemplet är knappen inaktiverad eftersom de två visuella objekten båda innehåller ett enda val för Produkt. Det är tvetydigt vilken datapunkt från vilket visuellt objekt som ska kopplas till detaljvisningsåtgärden för att:

![Tvetydig filterkontext](media/desktop-drill-through-buttons/power-bi-button-disabled-ambiguity.png)

## <a name="customize-formatting-for-disabled-buttons"></a>Anpassa formatering för inaktiverade knappar
Du kan anpassa formateringsalternativen för inaktiverat läge för detaljgranskningsknappar.


:::image type="content" source="media/desktop-drill-through-buttons/drill-through-customize-disabled-button.png" alt-text="Anpassa formatering av inaktiverade knappar":::
 
Formateringsalternativen är:
- **Knapptextkontroller**: text, färg, utfyllnad, justering, storlek och teckensnittsfamilj

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-text.png" alt-text="Formatera inaktiverad knapptext":::

- **Knappfyllningskontroller**: färg, genomskinlighet och *ny* fyllningsbild (mer information finns i nästa avsnitt)

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-fill.png" alt-text="Inaktiverad knappfyllning":::

- **Ikonkontroller**: form, utfyllnad, justering, linjefärg, transparens och vikt

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-icon.png" alt-text="Inaktiverade knappikoner":::

- **Dispositionskontroller**: färg, transparens, vikt, runda kanter

     :::image type="content" source="media/desktop-drill-through-buttons/drill-through-disabled-button-outline.png" alt-text="Inaktiverad knappdisposition":::

## <a name="set-formatting-for-button-text-conditionally"></a>Ange formatering för knapptext enligt villkor
Du kan använda villkorsstyrd formatering för att ändra knapptexten baserat på det valda värdet för ett fält. Om du vill göra detta måste du skapa ett mått som matar ut den önskade strängen baserat på DAX-funktionen SELECTEDVALUE.

Här är ett exempel på ett mått som matar ut ”Visa produktinformation” om ett enstaka produktvärde INTE har valts, annars visas ”Visa information för [den valda produkten]”:

```dax
String_for_button = If(SELECTEDVALUE('Product'[Product], 0) == 0, "See product details", "See details for " & SELECTEDVALUE('Product'[Product]))
```

När du har skapat det här måttet väljer du alternativet **Villkorsstyrd formatering** för knapptexten:

![Välj Villkorsstyrd formatering](media/desktop-drill-through-buttons/power-bi-button-conditional-tooltip.png)

Sedan väljer du det mått som du skapade för knapptexten:

![Värde baserat på fältet](media/desktop-drill-through-buttons/power-bi-conditional-measure.png)

När en enstaka produkt väljs blir knapptexten:

Visa information om Word

![När ett enstaka värde väljs](media/desktop-drill-through-buttons/power-bi-conditional-button-text.png)

Om inga produkter är markerade eller om du har valt fler än en produkt är knappen inaktiverad. Knapptexten är:

Visa produktinformation

![När flera värden väljs](media/desktop-drill-through-buttons/power-bi-button-conditional-text-2.png)

## <a name="set-formatting-for-tooltips-conditionally"></a>Ange formatering för knappbeskrivningar enligt villkor

Du kan villkorligt formatera knappbeskrivningen för detaljgranskningsknappen när den är aktiverad eller inaktiverad. Om du har använt villkorsstyrd formatering för att dynamiskt ange målet för detaljgranskningen, kanske du vill att knappbeskrivningen för knappläget är mer informativ, baserat på din slutanvändares val. Nedan visas några exempel:

- Du kan ange knappbeskrivning för inaktiverat tillstånd så att den kan användas enligt varje enskilt fall med ett anpassat mått. Om du till exempel vill att användaren ska välja en enskild produkt *och* en enda butik innan hen kan gå vidare till sidan för marknadsanalys, kan du skapa ett mått med följande logik:

    Om användaren inte har valt antingen en enskild produkt eller en enskild butik, returnerar måttet: ”Välj en enskild produkt och klicka på Ctrl + för att även välja en enskild butik.”

    Om användaren har valt en enskild produkt men inte en enskild butik, returnerar måttet: ”Klicka på Ctrl + för att välja en enskild butik.”

- På samma sätt kan du ställa in knappbeskrivningen för det aktiverade läget så att den är specifik för användarens val. Om du till exempel vill att användaren ska veta vilken produkt och butik sidan med detaljerad information ska filtreras till, kan du skapa ett mått som returnerar:

    ”Klicka för att öka detaljnivån till [information om sidnamn] om du vill ha mer information om försäljningen av [produktnamn] i [butiksnamn]-butiker.”


## <a name="set-the-drill-through-destination-conditionally"></a>Ange villkor för att öka detaljnivån

Du kan använda villkorsstyrd formatering för att ställa in ett mål för detaljgranskningen baserat på utdata för ett mått.

Här följer några scenarier där du kanske vill att knappen detaljvisningsmålet ska vara villkorlig:

- Du vill bara aktivera detaljvisning till en sida **när flera villkor har uppfyllts**. Annars är knappen inaktiverad.

    Om du till exempel vill att användarna ska kunna välja en enda produkt *och* en enda butik innan hen kan gå till sidan med marknadsinformation. Annars är knappen inaktiverad.

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-store.png" alt-text="Välj en produkt och butik":::
 
- Du vill att knappen **har stöd för flera detaljgranskningsmål** baserat på användarval.

    Anta till exempel att du har flera destinationer (marknadsinformation och butiksinformation) som användarna kan gå ner på detaljnivå för. Du kan låta dem välja ett speciellt mål att gå till innan knappen aktiveras för det här detaljgranskningsmålet.

    :::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-destination.png" alt-text="Välj produkt och mål":::
 
- Du kan också ha intressanta **fall för ett hybridscenario** för att stödja både flera detaljgranskningsmål och vissa villkor där du vill att knappen ska inaktiveras. Läs vidare om du vill ha mer information om de här tre alternativen.

### <a name="disable-the-button-until-multiple-conditions-are-met"></a>Inaktivera knappen tills flera villkor är uppfyllda

Låt oss titta på det första fallet där du vill behålla knappen inaktiverad tills ytterligare villkor är uppfyllda. Du måste skapa ett grundläggande DAX-mått som matar ut en tom sträng (””) om inte villkoret har uppfyllts. När det är uppfyllt, returnerar det namnet på sidan för detaljgranskningsmålet.

Här är ett exempel på DAX-mått som kräver att en butik väljs innan användaren kan detaljgranska en informationssida för produkt till butik:

```dax
Destination logic = If(SELECTEDVALUE(Store[Store], “”)==””, “”, “Store details”)
```

När du har skapat måttet väljer du knappen villkorsstyrd formatering (FX) bredvid **målet** för knappen:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-formula.png" alt-text="Välj knappen för villkorsstyrd formatering":::
 
I det sista steget väljer du det DAX-mått som du skapade som fältvärde för målet:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-based-formula.png" alt-text="Mål baserat på fält"::: 

Nu visas knappen som inaktiverad även när en enskild produkt väljs, eftersom måttet även kräver att du väljer ett enskild butik:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-button-disabled.png" alt-text="Knappen detaljnivå inaktiverad":::

### <a name="support-multiple-destinations"></a>Stöd för flera mål
 
För det andra vanliga fallet där du vill ha stöd för flera mål börjar du med att skapa en tabell med enda kolumn med namnen på de olika detaljgranskningsmålen:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-create-table.png" alt-text="Skapa en tabell":::

Power BI använder den exakta strängmatchningen för att ställa in detaljgranskningsmålet, så dubbelkolla att värdena som anges exakt överensstämmer med dina namn för detaljnivån.

När du har skapat tabellen lägger du till den på sidan som ett utsnitt för enskilt val:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-slicer.png" alt-text="Utsnitt för detaljgranskning":::
 
Om du behöver mer lodrätt utrymme konverterar du utsnittet till en listruta. Ta bort utsnittsrubriken och lägg till en textruta med rubriken bredvid den:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-drop-down-slicer.png" alt-text="Utsnitt för detaljgranskning utan sidhuvud":::
 
Du kan också ändra listutsnittet från lodrät till vågrät riktning:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-horizontal-slicer.png" alt-text="Horisontellt utsnitt":::

För inmatade mål för åtgärden detaljgranskning väljer du knappen villkorsstyrd formatering (FX) bredvid **mål** för knappen:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-formula.png" alt-text="Välj knappen för villkorsstyrd formatering":::
 
Välj namnet på kolumnen som du skapade, i det här fallet **Välj ett mål**:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-destination.png" alt-text="Välj ett mål":::
 
Nu ser du att knappen för detaljgranskning bara är aktiverad när du har valt en produkt *och* ett mål:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-select-product-destination.png" alt-text="Välj produkt och mål":::
 
### <a name="hybrid-of-the-two-scenarios"></a>Hybrid av de två scenarierna

Om du är intresserad av en hybrid av de två scenarierna kan du skapa och referera till ett DAX-mått för att lägga till ytterligare logik för val av mål.

Här är ett exempel på DAX-mått som kräver att användaren väljer en butik innan hen kan detaljgranska en produkt på någon av detaljgranskningssidorna:

```dax
Destination logic = If(SELECTEDVALUE(Store[Store], “”)==””, “”, SELECTEDVALUE(‘Table'[Select a destination]))
```

Sedan väljer du det DAX-mått som du skapade som fältvärde för målet.
I det här exemplet måste användaren välja en produkt, en butik, *och* en målsida innan knappen för detaljgranskning aktiveras:

:::image type="content" source="media/desktop-drill-through-buttons/drill-through-product-store-destination.png" alt-text="Välj produkt, butik och mål":::

## <a name="limitations"></a>Begränsningar

- Den här knappen tillåter inte flera mål med en enda knapp.
- Den här knappen stöder bara detaljvisning i samma rapport. Det finns med andra ord inte stöd för detaljvisning i flera rapporter.
- Formateringen för inaktiverat tillstånd för knappen är kopplad till färgklasserna i ditt rapporttema. Lär dig mer om [färgklasser](desktop-report-themes.md#setting-structural-colors).
- Åtgärden för detaljvisning fungerar för alla inbyggda visuella objekt, och fungerar med *vissa* visuella objekt som importeras från AppSource. Men det finns ingen garanti för att den fungerar med *alla* visuella objekt som importeras från AppSource.

## <a name="next-steps"></a>Nästa steg
Mer information om liknande funktioner eller funktioner som interagerar med knappar finns i följande artiklar:

* [Skapa knappar](desktop-buttons.md)
* [Använda detaljvisning i Power BI-rapporter](desktop-drillthrough.md)
* [Använda bokmärken för att dela information och skapa artiklar i Power BI](desktop-bookmarks.md)

