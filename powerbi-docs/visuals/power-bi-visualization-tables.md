---
title: Tabellvisualiseringar i Power BI-rapporter och instrumentpaneler
description: Självstudier för att arbeta med tabellvisualiseringar i Power BI-rapporter och instrumentpaneler, inklusive hur du ändrar kolumnbredder.
author: mihart
ms.reviewer: willt
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 02/10/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 11ccbdd3a5586aa10c051e6bfed820ed7f0ae48b
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237536"
---
# <a name="tables-in-power-bi-reports-and-dashboards"></a>Tabeller i Power BI-rapporter och instrumentpaneler

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]


[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

En tabell är ett rutnät som innehåller relaterade data i en logisk serie med rader och kolumner. Det kan också innehålla rubriker och en rad för summor. Tabeller fungerar bra med kvantitativa jämförelser där du tittar på många värden för en enskild kategori. I den här tabellen visas till exempel fem olika mått för **Kategori**.

![Skärmbild av en tabell som visar fem olika mått för Kategori.](media/power-bi-visualization-tables/power-bi-table-grid3.png)

Skapa tabeller i rapporter och korsmarkera flera element i tabellen med andra visuella objekt på samma rapportsida. Du kan välja rader, kolumner och även enskilda celler och korsmarkeringar. Du kan också kopiera och klistra in enskilda celler och markeringar av flera celler i andra program.

## <a name="when-to-use-a-table"></a>När du ska en tabell

Tabeller är ett bra alternativ:

* för att visa och jämföra detaljerade data och exakta värden (istället för visuella representationer)

* för att visa data i tabellformat

* för att visa numeriska data efter kategorier.

## <a name="prerequisite"></a>Förutsättning

De här självstudierna använder sig av [PBIX-filen Exempel på detaljhandelsanalys](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix).

1. Välj **Arkiv** > **Öppna** uppe till vänster på menyraden
   
2. Leta reda på kopian av **PBIX-filen Exempel för detaljhandelsanalys**

1. Öppna **PBIX-filen Exempel för detaljhandelsanalys** i rapportvyn ![Skärmbild av rapportvisningsikonen.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Välj ![Skärmbild av den gula fliken.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) för att lägga till en ny sida.

> [!NOTE]
> För att dela en rapport med en Power BI-kollega krävs att du både har individuella Power BI Pro-licenser eller att rapporten har sparats med Premium-kapacitet.

## <a name="create-a-table"></a>Skapa en tabell

Du ska skapa tabellen som visas i början av artikeln för att visa försäljningsvärden efter objektskategori.


1. I fönstret **Fält** väljer du **Objekt** > **Kategori**.

    Power BI skapar automatiskt en tabell som listar alla kategorier.

    ![resultatet av att lägga till kategori](media/power-bi-visualization-tables/power-bi-table1.png)

1. Välj **Försäljning > Genomsnittligt enhetspris** och **Försäljning > Senaste årets försäljning**.

1. Välj sedan **Försäljning > Försäljning detta år** och välj alla tre alternativen: **Värde**, **Mål** och **Status**.

1. Identifiera området **Värden** i fönstret **Visualiseringar** och markera värdena tills ordningen på diagramkolumnerna matchar den första bilden på den här sidan. Dra värdena i området vid behov. Området **Värden** bör se ut så här:

    ![Värden](media/power-bi-visualization-tables/power-bi-table2.png)


## <a name="format-the-table"></a>Formatera tabellen

Det finns många sätt för att formatera en tabell. Här beskrivs bara några av dem. Ett bra sätt att lära sig mer om de andra formateringsalternativen är att öppna fönstret **Format** (rollerikonen ![roller](media/power-bi-visualization-tables/power-bi-format.png)) och utforska det.

* Försök att formatera tabellrutnätet. Här lägger du till ett blått lodrätt rutnät, lägger till utrymme i raderna och ökar kantlinjen och textstorleken.

    ![Rutnätskort](media/power-bi-visualization-tables/power-bi-table-gridnew.png)

    ![tabell som visar resultat](media/power-bi-visualization-tables/power-bi-table-grid3.png)

* Ändra bakgrundsfärgen för kolumnrubrikerna, lägg till en kantlinje och öka teckenstorleken.

    ![Kolumnrubrikskort](media/power-bi-visualization-tables/power-bi-table-column-headers.png)

    ![rubrikformatering in tabell](media/power-bi-visualization-tables/power-bi-table-column2.png)

* Du kan även formatera enskilda kolumner och kolumnrubriker. Starta genom att utvidga **Fältformatering** och markera den kolumn som ska formateras från listrutan. Med **Fältformatering** kan du, beroende på kolumnvärdena, t.ex. ange visningsenheter, teckensnittsfärg, antal decimaler, bakgrund, justering och mycket mer. När du har justerat inställningarna kan du ange om dessa inställningar även ska tillämpas på rubrik och summarad.

    ![Fältformatering för Försäljning detta år](media/power-bi-visualization-tables/power-bi-field-formatting.png)

    ![Fältformatering för Försäljning detta år i tabellen](media/power-bi-visualization-tables/power-bi-field-formatting-1.png)

* Här är vår slutliga tabell, efter ytterligare lite formatering.

    ![tabell med all formatering hittills](media/power-bi-visualization-tables/power-bi-table-format.png)

### <a name="conditional-formatting"></a>Villkorsstyrd formatering

*Villkorsstyrd formatering* är en typ av formatering. Power BI kan använda villkorsstyrd formatering för de fält du lägger till i avsnittet **Värden** i fönstret **Visualiseringar**.

![Fönstret Visualisering](media/power-bi-visualization-tables/power-bi-table-values.png)

Med villkorsstyrd formatering för tabeller kan du ange ikoner, webbadresser, cellbakgrundsfärger och teckenfärger baserat på cellvärden, inklusive toningar.

1. Gå till fönstret **Format** och öppna kortet **Villkorsstyrd formatering**.

    ![Kortet Villkorsstyrd formatering](media/power-bi-visualization-tables/power-bi-conditional.png)

1. Välj ett fält att formatera och flytta skjutreglaget för **Bakgrundsfärg** till På. Power BI använder toning baserat på värdena i kolumnen. Om du vill ändra standardfärgerna väljer du **Avancerade kontroller**.

    Om du väljer alternativet **Divergerande** kan du även konfigurera ett valfritt **centreringsvärde**.

    ![Skärmen Skalor för bakgrundsfärg](media/power-bi-visualization-tables/power-bi-conditional-formatting-background2.png)

    Vi kan lägga till anpassad formatering våra värden för Genomsnittligt enhetspris. Välj **Divergerande**, lägg till några färger och välj **OK**.

    ![tabell som visar avvikande färger](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-background.png)
1. Lägg till ett nytt fält i tabellen som innehåller både positiva och negativa värden. Välj **Försäljning > Total försäljningsvarians**.

    ![visar ett nytt fält till höger](media/power-bi-visualization-tables/power-bi-conditional-formatting2.png)

1. Lägg till villkorsstyrd formatering för datastaplar genom att flytta skjutreglaget för **Datastaplar** till På.  

    ![Kortet Villkorsstyrd formatering med datastaplar aktiverade](media/power-bi-visualization-tables/power-bi-data-bar-matrix.png)

1. Om du vill anpassa datastaplarna väljer du **Avancerade kontroller**. I dialogrutan som visas anger du färger för **Positiv stapel** och **Negativ stapel**, markerar alternativet **Visa enbart stapel** och gör eventuella andra ändringar som du önskar.

    ![markeringen för Visa endast liggande](media/power-bi-visualization-tables/power-bi-data-bar.png)

1. Välj **OK**.

    Datastaplar ersätter de numeriska värdena i tabellen, vilket gör den lättare att söka igenom.

    ![samma tabell men med staplar i sista kolumnen](media/power-bi-visualization-tables/power-bi-conditional-formatting-data-bars2.png)

1. Du kan ge visuell vägledning i dina tabeller med *villkorsstyrda ikoner*.  Öppna kortet **Villkorsstyrd formatering** och välj **Årets försäljning** från listrutan. Flytta reglaget för **Ikoner** till **På**.  Om du vill anpassa ikonerna väljer du **Avancerade kontroller**.

    ![Tabell med tillagda ikoner](media/power-bi-visualization-tables/power-bi-table-icons.png)


## <a name="copy-values-from-power-bi-tables-for-use-in-other-applications"></a>Kopiera värden från Power BI-tabeller så att du kan använda dem i andra program

Din tabell eller matris kan ha innehåll som du vill använda i andra program som Dynamics CRM eller Excel eller t.o.m. i andra Power BI-rapporter. Genom att högerklicka i en cell i Power BI kan du kopiera de data som finns i cellen, eller ett urval av celler, till Urklipp och sedan klistra in informationen i de andra programmen.

För att kopiera värdet i en cell:

1. Markera den cell som du vill kopiera.

1. Högerklicka i cellen.

1. Välj **Kopiera** > **Kopiera värde**.

    ![kopieringsalternativ](media/power-bi-visualization-tables/power-bi-copy-value.png)

    Med det oformaterade cellvärdet i Urklipp kan du nu klistra in det i ett annat program.

För att kopiera fler än en cell:

1. Markera ett område med celler eller använd **Ctrl** för att välja en eller flera celler.

1. Högerklicka i en av cellerna som du har valt.

1. Välj **Kopiera** > **Kopiera markering**.

    ![kopieringsalternativ](media/power-bi-visualization-tables/power-bi-copy-selection.png)

## <a name="adjust-the-column-width-of-a-table"></a>Justera kolumnbredden i en tabell

Power BI trunkerar ibland en kolumnrubrik i en rapport eller på en instrumentpanel. Om du vill visa hela kolumnnamnet håller du muspekaren över utrymmet till höger om rubriken för att visa dubbelpilarna, markerar och drar.

![närbild på storleksändring av kolumn](media/power-bi-visualization-tables/resizetable.gif)


## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

* Om du lägger till kolumnformatering kan du bara välja ett justeringsalternativ per kolumn: **automatisk justering**, **vänsterjustering**, **centrering**, **högerjustering**. Oftast innehåller en kolumn antingen text eller tal, inte en blandning av både text och tal. Om en kolumn innehåller både tal och text, vänsterjusteras texten och talen högerjusteras om du väljer **Auto**. Det här beteendet används med ”vänster till höger”-språk.

* Om textdata i tabellens celler eller rubriker innehåller tecken för ny rad, så ignoreras dessa tecken om du inte växlar alternativet "Automatiskt radbyte" i elementets associerade formatpanelskort. 


## <a name="next-steps"></a>Nästa steg

* [Trädkartor i Power BI](power-bi-visualization-treemaps.md)

* [Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
