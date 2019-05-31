---
title: Villkorlig tabellformatering i Power BI Desktop
description: Tillämpa anpassad formatering
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/07/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: e23fd2aca90ee14c2376b0175c7c8b5132cf9a9f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222268"
---
# <a name="conditional-formatting-in-tables"></a>Villkorsstyrd formatering i tabeller 
Med villkorsstyrd formatering för tabeller kan du ange anpassade cellfärger baserat på cellvärden, eller baserat på andra värden eller fält. Du kan även använda toningar. Du kan också visa cellvärden med datastaplar. 

Åtkomst till villkorlig formatering, i brunnen **fält** i fönstret **Visuella objekt** i Power BI Desktop väljer du nedpilen bredvid värdet i brunnen **Värden** som du vill formatera (eller högerklicka på fältet). Du kan endast hantera villkorsstyrd formatering för fälten i området **Värden** i brunnen **Fält**.

![Menyn Villkorsstyrd formatering](media/desktop-conditional-table-formatting/table-formatting-0-popup-menu.png)

I följande avsnitt beskrivs vart och ett av dessa alternativ för villkorsstyrd formatering. Ett eller flera alternativ kan kombineras i samma tabellkolumn.

> [!NOTE]
> När villkorsstyrd formatering tillämpas i en tabell åsidosätts eventuella anpassade tabellformat som tillämpats på de villkorligt formaterade cellerna.

Om du vill ta bort villkorlig formatering från en visualisering högerklickar du bara på fältet igen, väljer **Ta bort villkorsstyrd formatering** och väljer sedan den typ av formatering som du vill ta bort.

![Menyn Ta bort villkorsstyrd formatering](media/desktop-conditional-table-formatting/table-formatting-1-remove.png)

## <a name="background-color-scales"></a>Skalor för bakgrundsfärg

Om du väljer **Villkorsstyrd formatering** och sedan **Skalor för bakgrundsfärg** visas följande dialogruta.

![Dialogrutan Skalor för bakgrundsfärg](media/desktop-conditional-table-formatting/table-formatting-1-default-dialog.png)

Du kan välja ett fält från datamodellen som färgerna ska baseras på genom att ange **Färgen baseras på** till det fältet. Du kan också ange aggregeringstypen för det valda fältet med värdet **Sammanfattning**. Fältet som färgerna tillämpas på anges i fältet **Använd färgen på**, så att du enkelt kan se vilket fält inställningarna tillämpas på. Du kan använda villkorsstyrd formatering för text- och datumfält, förutsatt att du väljer ett numeriskt värde som bas för formateringen.

![Fältet Färgen baseras på](media/desktop-conditional-table-formatting/table-formatting-1-apply-color-to.png)

Om du vill använda diskreta färgvärden för specifika värdeintervall väljer du **Färg efter regler**. Om du vill använda ett färgspektrum lämnar du alternativet **Färg efter regler** avmarkerat. 

![Dialogrutan Skalor för bakgrundsfärg](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-dialog.png)

### <a name="color-by-rules"></a>Färg efter regler

När du väljer **Färg efter regler** kan du ange ett eller flera värdeintervall, vart och ett med en bestämd färg.  Varje värdeintervall börjar med ett *Om*-värdevillkor, ett *Och*-värdevillkor och en färg.

![Värdeintervall för Färg efter regler](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-if-value.png)

Tabellceller med värden i varje intervall fylls med den angivna färgen. Det finns tre regler i följande bild.

![Exempel på Färg efter regler](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules.png)

Nu ser exempeltabellen ut så här:

![Exempeltabell med färg baserat på regler](media/desktop-conditional-table-formatting/table-formatting-1-color-by-rules-table.png)


### <a name="color-minimum-to-maximum"></a>Minsta och största värden för färg

Du kan konfigurera de *minsta* och *största* värdena och deras färger. Om du väljer rutan **Avvikande** kan du konfigurera ett valfritt *Centrumvärde*.

![Knappen Divergerande](media/desktop-conditional-table-formatting/table-formatting-1-diverging.png)

Nu ser exempeltabellen ut så här:

![Exempeltabell med avvikande färger](media/desktop-conditional-table-formatting/table-formatting-1-diverging-table.png)

## <a name="font-color-scales"></a>Färgskalor för teckensnitt

Om du väljer **Villkorsstyrd formatering** och sedan **Färgskalor för teckensnitt** visas följande dialogruta. Den här dialogrutan liknar dialogrutan **Skalor för bakgrundsfärg**, men ändrar teckensnittsfärgen i stället för cellernas bakgrundsfärg.

![Dialogrutan Färgskalor för teckensnitt](media/desktop-conditional-table-formatting/table-formatting-2-diverging.png)

Nu ser exempeltabellen ut så här:

![Exempeltabell med färgskalor för teckensnitt](media/desktop-conditional-table-formatting/table-formatting-2-table.png)

## <a name="data-bars"></a>Datastaplar

Om du väljer **Villkorsstyrd formatering** och sedan **Datastaplar** visas följande dialogruta. 

![Dialogrutan Datastaplar](media/desktop-conditional-table-formatting/table-formatting-3-default.png)

Alternativet **Visa enbart stapel** är avmarkerat som standard, vilket innebär att tabellcellen visar både stapeln och själva värdet.

![Exempeltabell med datastaplar och värden](media/desktop-conditional-table-formatting/table-formatting-3-default-table.png)

Om alternativet **Visa enbart stapel** är markerat, så visar tabellcellen endast stapeln.

![Exempeltabell med endast datastaplar](media/desktop-conditional-table-formatting/table-formatting-3-default-table-bars.png)

## <a name="color-formatting-by-field-value"></a>Färgformatering efter fältvärde

Du kan använda ett mått eller en kolumn som definierar en viss färg, antingen med hjälp av ett textvärde eller en hexadecimal kod, och tillämpa den färgen på bakgrunden eller teckenfärgen i en tabell- eller matrisvisualisering. Du kan också skapa anpassad logik för ett visst fält och använda den för att tillämpa en specifik färg på texten eller bakgrunden.

I följande tabell associeras exempelvis en färg med varje produktmodell. 

![Fältet ProductName med färgnamn](media/desktop-conditional-table-formatting/conditional-table-formatting_01.png)

Om du vill formatera cellen baserat på dess fältvärde öppnar du dialogrutan **Villkorsstyrd formatering** genom att högerklicka på kolumnen *Färg* för det visuella objektet, och väljer sedan i detta fall **Bakgrundsfärg** på menyn. 

![Välj Bakgrundsfärg på menyn](media/desktop-conditional-table-formatting/conditional-table-formatting_02.png)

I dialogrutan som visas väljer du **Fältvärde** i området med listrutan **Formatera efter**, som du ser i följande bild.

![Formatera efter fältvärde](media/desktop-conditional-table-formatting/conditional-table-formatting_03.png)

Du kan upprepa processen för teckenfärgen, så att en färg i **färgkolumnen** tillämpas på resultatet i det visuella objektet, som du ser i följande skärmbild.

![Formatera efter fältvärde](media/desktop-conditional-table-formatting/conditional-table-formatting_04.png)

Du kan också skapa en DAX-beräkning baserat på affärslogik som visar olika hexadecimala koder baserat på önskade villkor. Detta är vanligtvis enklare än att skapa flera regler i dialogrutan för villkorsstyrd formatering. Titta på fältet *ColorKPI* i följande exempelbild.

![DAX-beräkningar](media/desktop-conditional-table-formatting/conditional-table-formatting_05.png)

Du kan sedan ange fältvärdet för **Bakgrundsfärg** på följande sätt.

![Ange fältfärgen baserat på en KPI](media/desktop-conditional-table-formatting/conditional-table-formatting_06.png)

På så vis kan du sedan få resultat som liknar de i följande matris.

![Matrisvisualisering med färg baserat på KPI-värde](media/desktop-conditional-table-formatting/conditional-table-formatting_07.png)

Du kan skapa många fler varianter genom att bara använda din fantasi och DAX.

Du kan använda någon av de värden som anges i CSS-specifikationen för färg på [ https://www.w3.org/TR/css-color-3/ ](https://www.w3.org/TR/css-color-3/) till bakgrundsfärg för de visuella objekten:
* 3, 6- eller 8 siffra hex kodar t.ex. #3E4AFF. Kontrollera att du inkluderar symbolen # i början av koden. ”3E4AFF” accepteras inte. 
* RGB eller RGBA värden t.ex. RGBA (234, 234, 234, 0,5)
* HSL eller HSLA t.ex. värden HSLA (123, 75%, 75%, 0,5)
* Färg namn t.ex. grönt, SkyBlue, PeachPuff 

## <a name="next-steps"></a>Nästa steg
Mer information finns i följande artikel:  

* [Tips för färgformatering i Power BI](visuals/service-tips-and-tricks-for-color-formatting.md)  

