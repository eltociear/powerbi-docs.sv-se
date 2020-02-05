---
title: Villkorlig tabellformatering i Power BI Desktop
description: Tillämpa anpassad formatering
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 12/26/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: c79a8ddd68fa64b0a16663500a3f02e9a991835b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "75730532"
---
# <a name="use-conditional-formatting-in-tables"></a>Använda villkorsstyrd formatering i tabeller 

Med villkorsstyrd formatering för tabeller i Power BI Desktop kan du ange egna cellfärger baserat på fältvärden, inklusive toningar. Du kan också representera cellvärden som datastaplar eller KPI-ikoner, eller som aktiva webblänkar. Du kan använda villkorsstyrd formatering för all text och alla datatyper, så länge du baserar formateringen på ett fält som har värden i form av numeriska tal, namn på färger, hexadecimal kod eller webbadresser. 

Om du vill använda villkorsstyrd formatering väljer du en **tabell** eller **matris** i Power BI Desktop. I avsnittet **Fält** i fönstret **Visualiseringar** högerklickar du på eller väljer nedpilen bredvid de **Värden** du vill formatera. Välj **Villkorsstyrd formatering** och sedan den typ av formatering du vill använda.

![Menyn Villkorsstyrd formatering](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

> [!NOTE]
> Villkorsstyrd formatering ersätter eventuella anpassade bakgrunder eller teckenfärger du har angivit för den villkorsstyrt formaterade cellen.

Om du vill ta bort villkorsstyrd formatering från en visualisering väljer du **Ta bort villkorsstyrd formatering** från listrutan för fältet och sedan den typ av formatering du vill ta bort.

![Menyn Ta bort villkorsstyrd formatering](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

I följande avsnitt beskrivs de olika alternativen för villkorsstyrd formatering. Du kan använda fler än ett alternativ i samma tabellkolumn.

## <a name="format-background-or-font-color"></a>Formatera bakgrund eller teckenfärg

Om du vill formatera cellens bakgrund eller teckenfärg väljer du **Villkorsstyrd formatering** för ett fält och väljer sedan antingen **Bakgrundsfärg** eller **Teckenfärg** från listrutan. 

![Välj Bakgrundsfärg eller Teckenfärg](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

Dialogrutan **Bakgrundsfärg** eller **Teckenfärg** öppnas, med namnet på det fält du formaterar i rubriken. När du har valt alternativ för villkorsstyrd formatering väljer du **OK**. 

![Dialogrutorna Bakgrundsfärg och Teckenfärg](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

Alternativen **Bakgrundsfärg** och **Teckenfärg** fungerar på samma sätt, men påverkar cellens bakgrundsfärg respektive teckenfärg. Du kan använda samma eller olika villkorsstyrd formatering för ett fälts teckenfärg och bakgrundsfärg. Om du använder samma teckenfärg och bakgrundsfärg för ett fält smälter tecknen ihop med bakgrunden så att du bara ser själva färgen i tabellkolumnen.

## <a name="color-by-color-scale"></a>Färg efter färgskala

Om du vill formatera cellbakgrunden eller teckenfärgen efter en färgskala går du till fältet **Formatera efter** i dialogrutan **Bakgrundsfärg** eller **Teckenfärg** och väljer **Färgskala**. Under **Baserat på fält** väljer du fältet som formateringen ska baseras på. Du kan basera formateringen på det aktuella fältet eller något annat fält i modellen som har numeriska data eller färgdata. 

Under **Sammanfattning** anger du vilken typ av aggregering du vill använda för det valda fältet. Under **Standardformatering** väljer du en formatering för tomma värden. 

Under **Minimum** och **Maximum** väljer du om färgschemat ska tillämpas baserat på de lägsta och högsta fältvärdena eller på anpassade värden som du anger själv. Välj de färger du vill använda för de lägsta och högsta värdena från listrutorna. Markera kryssrutan **Divergerande** om du vill ange värde och färg för **Centrera**. 

![Ange cellbakgrund med färgskala](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

Så här kan en tabell med bakgrundsfärg efter färgskala på kolumnen **Affordability** (prisvärdhet) se ut:

![Exempel på tabell med divergerande färgskala för bakgrunden](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

Så här kan en tabell med teckenfärg efter färgskala på kolumnen **Affordability** (prisvärdhet) se ut:

![Exempel på tabell med divergerande färgskala för teckenfärgen](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="color-by-rules"></a>Färg efter regler

Om du vill formatera cellbakgrunden eller teckenfärgen efter regler går du till fältet **Formatera efter** i dialogrutan **Bakgrundsfärg** eller **Teckenfärg** och väljer **Regler**. I **Baserat på fält** anger du återigen vilket fält formateringen ska baseras på, och i **Sammanfattning** anges fältets aggregering. 

Under **Regler** anger du ett eller flera värdeintervall och en färg för vart och ett. Varje värdeintervall har ett *om*-värdevillkor, ett *och*-värdevillkor och en färg. Cellbakgrunderna eller teckensnitten i respektive värdeintervall ges den angivna färgen. I det här exemplet används tre regler:

![Färg efter regler](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Så här kan en tabell med regelbaserad bakgrundsfärg på kolumnen **Affordability** (prisvärdhet) se ut:

![Exempeltabell med färg baserat på regler](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)

## <a name="color-by-color-values"></a>Färg efter färgvärden

Om du har ett fält eller mått med färgnamn eller hexadecimala värden kan du använda villkorsstyrd formatering till att automatiskt använda dessa färger som bakgrundsfärg eller teckenfärg för en kolumn. Du kan också använda anpassad logik för tillämpningen av teckenfärg eller bakgrundsfärg.

Fältet kan innehålla alla färgvärden som anges i specifikationen för CSS-färger på [https://www.w3.org/TR/css-color-3/](https://www.w3.org/TR/css-color-3/). De här färgvärdena kan vara:
- 3-, 6- eller 8-siffriga hexadecimala koder, till exempel #3E4AFF. #-symbolen ska finnas med i början av koden. 
- RGB- eller RGBA-värden, till exempel RGBA(234, 234, 234, 0.5).
- HSL- eller HSLA-värden, till exempel HSLA(123, 75%, 75%, 0.5).
- Färgnamn, till exempel Green, SkyBlue eller PeachPuff. 

I den här tabellen är ett färgnamn kopplat till varje delstat: 

![Delstatstabell med färgnamn](media/desktop-conditional-table-formatting/conditional-table-formatting_01.png)

Om du vill formatera kolumnen **Färg** baserat på dess fältvärden väljer du **Villkorsstyrd formatering** för fältet **Färg** och sedan **Bakgrundsfärg** eller **Teckenfärg**. 

I dialogrutan **Bakgrundsfärg** eller **Teckenfärg** väljer du **Fältvärde** i listrutan **Formatera efter**.

![Formatera efter fältvärde](media/desktop-conditional-table-formatting/conditional-table-formatting_02.png)

Så här kan en tabell med fältvärdesbaserad formatering av **bakgrunden** i kolumnen **Color** (färg) se ut:

![Exempeltabell med bakgrundsformatering efter fältvärde](media/desktop-conditional-table-formatting/conditional-table-formatting_03.png)

Om du även använder **Fältvärde** till att formatera kolumnens **Teckenfärg** blir kolumnen **Color** helfärgad:

![Formatera bakgrund och teckensnitt efter fältvärde](media/desktop-conditional-table-formatting/conditional-table-formatting_04.png)

## <a name="color-based-on-a-calculation"></a>Färg baserat på en beräkning

Du kan skapa en DAX-beräkning som ger olika värden baserat på affärslogik du anger. Det går vanligtvis snabbare att skapa en DAX-formel än att skapa flera regler i dialogrutan för villkorsstyrd formatering. 

I den här DAX-formeln används till exempel hexadecimala färgvärden för den nya kolumnen **Affordability rank** (rangordning av prisvärdhet) baserat på de befintliga värdena i kolumnen **Affordability**:

![DAX-beräkning](media/desktop-conditional-table-formatting/conditional-table-formatting_05.png)

Du tillämpar färgerna genom att välja villkorsstyrd formatering baserad på **Bakgrundsfärg** eller **Teckenfärg** för kolumnen **Affordability** och basera formateringen på **Fältvärde** hos kolumnen **Affordability rank**. 

![Basera bakgrundsfärgen på en beräknad kolumn](media/desktop-conditional-table-formatting/conditional-table-formatting_06.png)

Så här ser exempeltabellen med bakgrundsfärg för **Affordability** baserad på beräkningen av **Affordability rank** ut:

![Exempeltabell med en beräknad värdebaserad färg](media/desktop-conditional-table-formatting/conditional-table-formatting_07.png)

Du kan skapa många fler varianter med hjälp av din fantasi och DAX.

## <a name="add-data-bars"></a>Lägga till datastaplar

Om du vill visa datastaplar baserade på cellvärden väljer du **Villkorsstyrd formatering** för fältet **Affordability** och sedan **Datastaplar** från listrutan. 

I dialogrutan **Datastaplar** är alternativet **Visa enbart stapel** avmarkerat som standard, så att du ser både staplar och faktiska värden i tabellcellerna. Om du bara vill visa datastaplarna markerar du kryssrutan **Visa endast stapel**.

Du kan ange värden för **Minimum** och **Maximum**, färger och riktning för datastaplarna och färger för axlarna. 

![Dialogrutan Datastaplar](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

Så här ser exempeltabellen ut med datastaplar för kolumnen **Affordability** ut:

![Exempeltabell med datastaplar](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)

## <a name="add-icons"></a>Lägga till ikoner

Om du vill visa ikoner baserade på cellvärden väljer du **Villkorsstyrd formatering** för fältet och sedan **Ikoner** från listrutan. 

I dialogrutan **Ikoner**, under **Formatera efter**, väljer du antingen **Regler** eller **Fältvärde**. 

Om du vill formatera efter regler väljer du ett fält i **Baserat på fält**, en metod för **Sammanfattning**, värden för **Ikonlayout** och **Ikonjustering**, ett **Format** och en eller flera **Regler**. Under **Regler** anger du en eller flera regler med ett *om*-villkor, ett *och*-villkor och en ikon som ska användas för varje regel. 

Om du vill formatera efter fältvärden väljer du ett fält i **Baserat på fält**, en metod för **Sammanfattning** samt en **Ikonlayout** och en **Ikonjustering**.

I det här exemplet lägger vi till ikoner baserat på tre regler:

![Dialogrutan Ikoner](media/desktop-conditional-table-formatting/table-formatting-1-default-table.png)

Välj **OK**. Så här ser exempeltabellen ut med ikoner baserade på regler för kolumnen **Affordability** ut:

![Exempeltabell med ikoner](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

## <a name="format-as-web-urls"></a>Formatera som webbadresser

Om du har en kolumn eller ett mått som innehåller webbadresser kan du använda villkorsstyrd formatering så att webbadresserna används som aktiva länkar för fälten. Den här tabellen innehåller till exempel kolumnen **Website** med en webbadress för varje delstat:

![Tabell med webbadresskolumn](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

Om du vill visa namnet på varje delstat som en länk till webbplatsen för den väljer du **Villkorsstyrd formatering** för fältet **State** (delstat) och sedan **Webbadress**. I dialogrutan **Webbadress**, under **Baserat på fält**, väljer du **Webbplats** och sedan **OK**. 

När formateringen **Webbadress** används för fältet **State** visas namnet på varje delstat som en aktiv länk till webbplatsen. I den här exempeltabellen används formateringen **Webbadress** för kolumnen **State**, och villkorsstyrda **datastaplar** och **bakgrundsfärger** används för kolumnen **Affordability**. 

![Tabell med webbadresser, datastaplar och bakgrundsfärg](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
Det finns några saker att tänka på när du arbetar med villkorsstyrd tabellformatering:

- Villkorsstyrd formatering tillämpas endast på värdena i tabeller och matriser, inte på delsummor, totalsummor eller raden **Totalt**. 
- Tabeller som saknar gruppering visas som en enda rad som inte har stöd för villkorsstyrd formatering.
- Du kan inte använda toningsformat med automatiska max/min-värden eller regelbaserad formatering med procentregler om dina data innehåller *NaN*-värden. NaN står för ”Inte ett nummer” och orsakas vanligtvis av fel vid division med noll. Du kan använda [DAX-funktionen DIVIDE()](https://docs.microsoft.com/dax/divide-function-dax) för att undvika dessa fel.
- När du använder villkorsstyrd formatering behövs en aggregering eller ett mått som ska tillämpas på värdet. Det är därför du ser ”First” (första) eller ”Last” (sista) i exemplet **Färg efter värde**. Om du skapar din rapport mot en flerdimensionell Analysis Service-kub kan du inte använda ett attribut för villkorsstyrd formatering om inte kubens ägare har skapat ett mått som tillhandahåller värdet.

## <a name="next-steps"></a>Nästa steg

Du kan läsa mer om färgformatering i [Tips för färgformatering i Power BI](visuals/service-tips-and-tricks-for-color-formatting.md)  

