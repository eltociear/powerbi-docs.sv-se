---
title: Lägga till en kolumn från ett exempel i Power BI Desktop
description: Skapa snabbt en ny kolumn i Power BI Desktop med hjälp av befintliga kolumner som exempel.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/16/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 9632bfaecc524aac95ec524cccb59ba08a7bc21f
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85229081"
---
# <a name="add-a-column-from-examples-in-power-bi-desktop"></a>Lägga till en kolumn från exempel i Power BI Desktop
Med *Lägg till kolumn från exempel* i Power Query-redigeraren kan du lägga till nya kolumner i datamodellen genom att ange ett eller flera exempelvärden för de nya kolumnerna. Du kan skapa de nya kolumnexemplen från ett urval eller ange inmatning baserat på alla befintliga kolumner i tabellen.

![](media/desktop-add-column-from-example/add-column-from-example_01.png)

Med hjälp av *Lägg till kolumn från exempel* kan du snabbt och enkelt skapa nya kolumner. Det passar utmärkt i följande situationer:

- Du vet vilka data du vill ha i den nya kolumnen, men du är inte säker på vilken omvandling, eller samling av omvandlingar, som tar dig dit.
- Du vet redan vilka omvandlingar du behöver men vet inte vad du ska välja i användargränssnittet för att det ska hända.
- Du vet vilka omvandlingar du behöver tack vare uttrycket *Anpassad kolumn* i språket *M*, men ett eller flera av dessa uttryck är inte tillgängliga i användargränssnittet.

Det är enkelt att lägga till en kolumn från ett exempel. Det framgår hur enkelt det är i följande avsnitt.

## <a name="add-a-new-column-from-examples"></a>Lägga till en ny kolumn från exempel

För att hämta exempeldata från Wikipedia väljer du **Hämta data** > **Webben** på fliken **Start** i menyfliksområdet för Power BI Desktop. 

![Hämta data från webben](media/desktop-add-column-from-example/add-column-from-example_02.png)

Klistra in följande URL i den dialogruta som visas och välj **OK**: 

*https:\//wikipedia.org/wiki/List_of_states_and_territories_of_the_United_States*

I dialogrutan **Navigatör** väljer du tabellen **States of the United States of America** och sedan **Transformera data**. Tabellen öppnas i Power Query-redigeraren.

Alternativt kan du öppna data som redan lästs in från Power BI Desktop genom att välja **Redigera frågor** på fliken **Start** i menyfliksområdet. Dessa data öppnas i Power Query-redigeraren. 

![Välja Redigera frågor i Power BI Desktop](media/desktop-add-column-from-example/add-column-from-example_05.png)

När exempeldata har öppnats i Power Query-redigeraren väljer du fliken **Lägg till kolumn** i menyfliksområdet och sedan **Kolumn från exempel**. Välj själva ikonen **Kolumn från exempel** för att skapa kolumnen från alla befintliga kolumner, eller välj listrutepilen för att välja mellan **Från alla kolumner** eller **Från urval**. I den här genomgången använder du **Från alla kolumner**.

![Välja Lägg till kolumn från exempel](media/desktop-add-column-from-example/add-column-from-example_03.png)

## <a name="add-column-from-examples-pane"></a>Fönstret Lägg till kolumn från exempel
När du väljer **Lägg till kolumn** > **Från exempel** öppnas fönstret **Lägg till kolumn från exempel** överst i tabellen. Den nya **Kolumn 1** visas till höger om de befintliga kolumnerna (du kan behöva rulla för att se alla). När du anger exempelvärdena i de tomma cellerna i **Kolumn 1** skapar Power BI regler och omvandlingar som matchar dina exempel och använder dem för att fylla i resten av kolumnen.

Observera att **Kolumn från exempel** även visas som ett **Tillämpat steg** i fönstret **Frågeinställningar**. Som alltid registrerar Power Query-redigeraren dina omvandlingssteg och tillämpar dem på frågan i rätt ordning.

![Fönstret Lägg till kolumn från exempel](media/desktop-add-column-from-example/add-column-from-example_04.png)

När du skriver exemplet i den nya kolumnen visar Power BI en förhandsgranskning av hur resten av kolumnen kommer att se ut baserat på de omvandlingar den skapar. Om du exempelvis skriver *Alabama* på den första raden motsvarar det värdet **Alabama** i den första tabellkolumnen. När du trycker på RETUR fyller Power BI i resten av den nya kolumnen baserat på det första kolumnsvärdet och ger kolumnen namnet **Namn och förkortning av postnummer[12] – kopia**.

Gå nu till raden **Massachusetts[E]** i den nya kolumnen och ta bort delen **[E]** i strängen. Power BI identifierar ändringen och använder exemplet för att skapa en transformering. Power BI beskriver omvandlingarna i fönstret **Lägg till kolumn från exempel** och byter namn på kolumnen till **Text före avgränsare**. 

![Omvandlad kolumn från exempel](media/desktop-add-column-from-example/add-column-from-example_06.png)

När du anger fler exempel lägger Power Query-redigeraren till dem i omvandlingarna. När du är nöjd väljer du **OK** för att genomföra ändringarna. 

Du kan när som helst byta namn på den nya kolumnen genom att dubbelklicka på kolumnrubriken eller högerklicka på den och välja **Byt namn**. 

Titta på den här videon för att se hur **Lägg till kolumn från exempel** fungerar i praktiken med exempeldatakällan: 

[Power BI Desktop: Lägg till kolumn från exempel](https://www.youtube.com/watch?v=-ykbVW9wQfw). 

## <a name="list-of-supported-transformations"></a>Lista över omvandlingar som stöds
Många, men inte alla, omvandlingar är tillgängliga när du använder **Lägg till kolumn från exempel**. I följande lista visas de omvandlingar som stöds:

**Allmänt**

- Villkorskolumn

**Referens**
  
- Referens till en specifik kolumn, inklusive omvandlingarna trimma, rensa och skiftläge

**Texttransformeringar**

- Kombinera (stöder kombinationen av literala strängar och hela kolumnvärden)
- Ersätt
- Längd
- Extrahera   
  - Första tecken
  - Sista tecken
  - Intervall
  - Text före avgränsare
  - Text efter avgränsare
  - Text mellan avgränsare
  - Längd
  - Ta bort tecken
  - Behåll tecken

> [!NOTE]
> Alla transformeringar av *Text* räknar med det potentiella behovet att trimma, rensa eller tillämpa skiftlägestransformeringar på kolumnvärdet.

**Datumtransformeringar**

- Dag
- Dag i veckan
- Namn på veckodag
- Dag på året
- Månad
- Namn på månad
- Kvartal på året
- Vecka i månad
- Vecka på året
- År
- Ålder
- Årets start
- Årets slut
- Månadens start
- Månadens slut
- Kvartalets start
- Dagar i månad
- Kvartalets slut
- Veckans start
- Veckans slut
- Dag i månaden
- Dagens början
- Dagens slut

**Tidstransformeringar**

- Hour
- Minut
- Second  
- Till lokal tid

> [!NOTE]
> Alla *Datum*- och *Tids*transformeringar räknar med ett potentiellt behov att konvertera kolumnvärdet till *Datum*, *Tid* eller *DateTime*.

**Taltransformeringar** 

- Absolut värde
- Arccosinus
- Arcsinus
- Arctangens
- Konvertera till tal
- Cosinus
- Kub
- Dividera
- Exponent
- Fakultet
- Heltalsdivision
- Är jämnt
- Är udda
- Ln
- 10-logaritm
- Modulo
- Multiplicera
- Avrunda nedåt
- Avrunda uppåt
- Tecken
- Sin
- Kvadratrot
- Kvadrat
- Subtrahera
- Summa
- Tangens
- Behållare/intervall

