---
title: "Självstudie: Importera och analysera data från en webbsida med Power BI Desktop"
description: "Självstudie: Importera och analysera data från en webbsida med Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: c5139c6f9f7b2098b51a608fb7719f371173c291
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/06/2017
---
# <a name="analyzing-web-page-data-using-power-bi-desktop-tutorial"></a>Analysera webbsidedata med Power BI Desktop (självstudie)
I den här självstudien lär du dig att importera en datatabell från en webbsida och skapa en rapport för att visualisera dess data. I processen går du igenom tabeller som finns på webbsidan och tillämpar datatransformeringssteg som ger tabellen en ny form.

 I den här artikeln:

* **Aktivitet 1:** Ansluta till en webbdatakälla
* **Aktivitet 2:** Utforma data i frågevyn
  * Steg 1: Ta bort övriga kolumner om du bara vill visa intressanta kolumner
  * Steg 2: Ersätt värden för att rensa värden i en vald kolumn
  * Steg 3: Filtrera värden i en kolumn
  * Steg 4: Byt namn på en kolumn
  * Steg 5: Filtrera nullvärden i en kolumn
  * Steg 6: Byt namn på en fråga
  * Frågesteg som skapats
* **Aktivitet 3:** Skapa visualiseringar med rapportvyn
  * Steg 1: Läs in frågan i rapporten
  * Steg 2: Skapa en kartvisualisering

## <a name="task-1-connect-to-a-web-data-source"></a>Aktivitet 1: Anslut till en webbdatakälla
 I aktivitet 1 importerar du en tabell med en turneringssammanfattning från UEFA:s Wikipedia-sida på följande plats: http://en.wikipedia.org/wiki/UEFA\_European\_Football\_Championship

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage1.png)

### <a name="add-a-wikipedia-page-data-source"></a>Lägga till en Wikipedia-sida som datakälla
1. I **dialogrutan Komma igång** eller på menyfliksområdet **Start** väljer du **Hämta data**.
2. Detta öppnar dialogrutan **Hämta data** där du kan välja bland en stor mängd datakällor för att importera data till Power BI Desktop. Vi väljer **Webb** som finns i gruppen **Alla** eller **Övrigt**.
3. I dialogrutan **Webbinnehåll** i textrutan **URL** klistrar du in Wikipedias URL (http://en.wikipedia.org/wiki/UEFA\_European\_Football\_Championship).
4. Klicka på **OK**.

När du har upprättat en anslutning till webbsidan ser du en lista med tabeller på Wikipedia-sidan i dialogrutan för **navigatören**. Du kan enkelklicka på varje tabell för att förhandsgranska datan.

I det vänstra fönstret i **navigatören** väljer du tabellen **Results[edit]** för turneringssammanfattningens resultat eller tabellen **Results[edit]** och **Redigera**. Detta innebär att vi kan formatera om tabellen innan vi läser in den i rapporten, eftersom datan inte är i det format vi behöver för analysen.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/tutorialimanaly_navigator.png)

En förhandsgranskning av tabellen visas i frågevyn, där vi kan tillämpa olika transformeringssteg för att rensa datan.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage3.png)

## <a name="task-2-shape-data-in-the-subject-table"></a>Aktivitet 2: Utforma data i ämnestabellen
Nu när ämnestabellen är vald för datafrågan, lär du dig hur du utför olika datautformnings- och rensningssteg.

**Steg 1:** Ta bort övriga kolumner för att bara visa intressanta kolumner

I det här steget tar du bort alla kolumner utom **År** och **Finalvinnare**.

1. I rutnätet **Förhandsgranska fråga** väljer du kolumnerna **År** och **Finalvinnare** (använd **CTRL** + **klick**).
2. Högerklicka på en kolumnrubrik i rutnätet **Förhandsgranska fråga** och klicka på **Ta bort andra kolumner** för att ta bort de omarkerade kolumnerna. Observera att åtgärden också är tillgänglig i menyfliksområdet **Start** i gruppen **Hantera kolumner**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage4.png)

**Steg 2:** Ersätt värden för att rensa värden i en vald kolumn

I det här steget byter du ut suffixet Information i kolumnen **År**. Observera att suffixet är på en ny rad så det syns inte i tabellförhandsgranskningen. Men om du klickar på någon av cellerna med ett numeriskt värde i kolumnen År, ser du hela värdet i den detaljerade vyn.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage5.png)

1. Välj kolumnen **År**.
2. I menyfliksområdet **Frågevy** klickar du på **Ersätt värden** under fliken **Start**. Du kan också högerklicka på kolumnen **År** och klicka på **Ersätt värden** för att ersätta informationen med tom text.
3. I dialogrutan **Ersätt värden** skriver du Information i textrutan **Värde att söka efter** och lämnar testrutan **Ersätt med** tom.
4. Klicka på **OK**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage6.png)

 **Steg 3:** Filtrera värden i en kolumn

I det här steget filtrerar du kolumnen **År** till att visa rader som inte innehåller ”År”.

1. Klicka på filtrets listrutepil i kolumnen **År**.
2. I listrutan **Filter** avmarkerar du alternativet **År**.
3. Klicka på **OK**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage7.png)

**Steg 4:** Byt namn på en kolumn

Nu när vi har rensat datan i kolumnen **År** ska vi arbeta med kolumnen **Finalvinnare**.

Eftersom vi endast ser listan med vinnare kan vi byta namn på kolumnen till **Land**.

1. Välj kolumnen **Finalvinnare** i Förhandsgranska fråga.
2. I menyfliksområdet **Frågevy** under fliken **Transformera** och gruppen **Vilken kolumn som helst** hittar du **Byt namn**.
3. Kolumnnamnet blir redigerbart. Vi byter namn på kolumnen till **Land**.

**Steg 5:** Filtrera nullvärden i en kolumn

Vi måste också filtrera bort nullvärden i kolumnen **Land**. För att kunna göra detta kan vi använda filtermenyn som vi såg i Steg 3, eller också kan vi:

1. Högerklicka på en av cellerna i kolumnen **Land** som innehåller ett nullvärde.
2. Välj **Textfilter –\> Är inte lika med** i snabbmenyn.
3. Detta skapar ett nytt filtersteg som tar bort rader med nullvärden i kolumnen **Land**.

**Steg 6:** Namnge en fråga

I det här steget namnger du slutfrågan **EM-vinnare**.

1. I fönstret **Frågeinställningar** i textrutan **Namn** skriver du **EM-vinnare**.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage8.png)

## <a name="task-3-create-visualizations-using-the-report-view"></a>Aktivitet 3: Skapa visualiseringar med rapportvyn
Nu när vi har konverterat datan till det format vi behöver för analysen, kan vi läsa in resulterande tabell i rapporten och skapa några visualiseringar.

**Steg 1:** Läsa in frågan i rapporten

För att kunna läsa in frågeresultaten i Power BI Desktop och skapa en rapport väljer vi **Stäng och läs in** i menyfliksområdet **Start**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage9.png)

Detta utlöser utvärderingen av frågan och läser in tabellresultatet i rapporten. I Power BI Desktop väljer du ikonen **Rapport** för att se Power BI Desktop i rapportvyn.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage10.png)

Du kan se resulterande tabellfält i **fönstret Fält** till höger om **Rapportvy**.

![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage11.png)

**Steg 2:** Skapa en kartvisualisering

För att kunna skapa en visualisering kan vi dra fält från **Fältlista** och släppa dem på **rapportarbetsytan**.

1. Dra fältet **Land** och släpp det på **rapportarbetsytan**. Detta skapar en ny visualisering på **rapportarbetsytan**. I det här fallet när vi har en lista med länder skapas en **kartvisualisering**.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage12.png)
2. Vi kan enkelt ändra visualiseringstyp genom att klicka på en annan ikon i fönstret **Visualisering**.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage13.png)
3. Vi stannar kvar i visualiseringstypen **Karta**. Vi kan också ändra storlek på visualiseringen genom att dra från ett av hörnen i visualiseringen upp till önskad storlek.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage14.png)
4. Observera att just nu har alla punkter på kartan samma storlek. Vi vill ändra detta så att länder med fler vunna EM-turneringar visas med en större punkt i kartan. För att göra detta drar vi fältet **År** i **Fältlista** till rutan **värden** i den nedre halvan av **fönstret Fält**.
   
   ![](media/desktop-tutorial-importing-and-analyzing-data-from-a-web-page/webpage15.png)

Som du kan se är det enkelt att anpassa visualiseringar i rapporten, för att kunna visa datan så som du vill. I Power BI Desktop är det enkelt att hämta data från en stor mängd datakällor och utforma dem efter dina analysbehov för att visualisera datan på interaktiva sätt. När rapporten är klar kan du [ladda upp den på Power BI](desktop-upload-desktop-files.md) och skapa instrumentpanelen som baseras på den, och sedan dela den med andra Power BI-användare.

Nu är du klar med självstudien **Importera data från webben**. Du kan hämta den färdiga Power BI Desktop-filen [här](http://download.microsoft.com/download/1/4/E/14EDED28-6C58-4055-A65C-23B4DA81C4DE/Analyzing_Data_From_The_Web.pbix).

## <a name="where-else-can-i-get-more-information"></a>Var kan jag få mer information?
* [Läs andra Power BI Desktop-självstudier](http://go.microsoft.com/fwlink/?LinkID=521937)
* [Se Power BI Desktop-videor](http://go.microsoft.com/fwlink/?LinkID=519322)
* [Besök Power BI-forumet](http://go.microsoft.com/fwlink/?LinkID=519326)
* [Läs Power BI-bloggen](http://go.microsoft.com/fwlink/?LinkID=519327)

