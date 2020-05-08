---
title: Utföra vanliga frågeuppgifter i Power BI Desktop
description: Utföra vanliga frågeuppgifter i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/09/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 8921737fac842d040d014244e2ce80e9bc158b23
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76039941"
---
# <a name="perform-common-query-tasks-in-power-bi-desktop"></a>Utföra vanliga frågeuppgifter i Power BI Desktop

I fönstret Power Query-redigeraren i Power BI Desktop finns det några återkommande uppgifter. I den här artikeln visas dessa återkommande uppgifter och länkar med ytterligare information.

De återkommande frågeuppgifter som beskrivs är:

* Ansluta till data
* Forma och kombinera data
* Gruppera rader
* Pivotera kolumner
* Skapa anpassade kolumner
* Fråga formler

Vi kommer att använda några dataanslutningar för att utföra dessa uppgifter. Du kan hämta eller ansluta till dessa data, ifall du vill gå igenom dessa uppgifter på egen hand.

Den första dataanslutningen är [en Excel-arbetsbok](https://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx), som du kan ladda ned och spara lokalt. Den andra är en webbresurs, som även används i andra Power BI Desktop-artiklar:

<https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/>

De steg s du måste följa för att ansluta till båda dessa datakällor inleder själva frågeuppgiftsarbetet.

## <a name="connect-to-data"></a>Ansluta till data

Om du vill ansluta till data i Power BI Desktop väljer du **Start** och sedan **Hämta data**. Power BI Desktop visar en meny med de vanligaste datakällorna. Om du vill ha en fullständig lista över de datakällor som Power BI Desktop kan ansluta till, väljer du **Mer** längst ned i menyn. Mer information finns i [Datakällor i Power BI Desktop](desktop-data-sources.md).

![Menyn Mest vanliga datakällor, knappen Hämta data, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

Börja genom att välja **Excel**, ange den Excel-arbetsbok som nämndes ovan och välj sedan **Öppna**. Frågan söker igenom arbetsboken och presenterar sedan de data den hittat i dialogrutan **Navigatör** när du har valt en tabell.

![Excel-datakälla, dialogrutan Navigatör, Hämta data, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

Du kan välja **Transformera data** om du vill redigera, justera eller *forma* datan innan du läser in den i Power BI Desktop. Redigering är särskilt användbart när du arbetar med stora datamängder som du vill skala ner före inläsningen.

Att ansluta till olika datatyper är lika enkelt. Du ska nu ansluta till en webbresurs. Välj **Hämta data** > **Mer** och sedan **Annan** > **Webb** > **Anslut**.

![Webbdatakälla, dialogrutan Hämta data, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

Dialogrutan **Från webben** öppnas där du kan ange webbsidans URL.

![Dialogrutan Från webben, webbdatakälla, Hämta data, Power BI Desktop](media/desktop-common-query-tasks/datasources_fromwebbox.png)

Välj **OK**. Precis som förut kontrollerar Power BI Desktop webbsidans data och visar förhandsgranskningsalternativ i dialogrutan **Navigatör**. När du väljer en tabell visas en förhandsgranskning av datan.

Andra dataanslutningar är av liknande slag. Om autentisering krävs för att göra en dataanslutning så uppmanas du av Power BI Desktop att ange autentiseringsuppgifterna.

En stegvis demonstration av hur man ansluter till data i Power BI Desktop finns i [Anslut till data i Power BI Desktop](desktop-connect-to-data.md).

## <a name="shape-and-combine-data"></a>Forma och kombinera data

Du kan enkelt forma och kombinera data med Power Query-redigeraren. Det här avsnittet innehåller några exempel på hur du kan forma data. En mer fullständig demonstration av att forma och kombinera data finns i [Forma och kombinera data med Power BI Desktop](desktop-shape-and-combine-data.md).

I det förra avsnittet anslöt du till två datauppsättningar: en Excel-arbetsbok och en webbresurs. När datan har lästs in i Power Query-redigeraren väljer du webbsidans fråga bland tillgängliga frågor i fönstret **Frågor**, enligt nedan:

![Fönstret Frågor, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

När du formar data omvandlar du en datakälla till ett formulär och ett format som motsvarar dina behov.

I Power Query-redigeraren finns många kommandon i menyfliksområdet och i snabbmenyer. Om du t.ex. högerklickar på en kolumn kan du ta bort kolumnen med snabbmenyn. Du kan också markera en kolumn och sedan välja knappen **Ta bort kolumner** på fliken **Start** i menyfliksområdet.

![Kommandot Ta bort kolumner, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

Du kan forma datan på många andra sätt i den här frågan. Du kan ta bort valfritt antal rader uppifrån eller nerifrån. Du kan också lägga till kolumner, dela upp kolumner, ersätta värden och utföra andra formuppgifter. Med dessa funktioner kan du styra Power Query-redigeraren att hämta data på det sätt som du vill.

## <a name="group-rows"></a>Gruppera rader

I Power Query-redigeraren kan du gruppera värden från flera rader till ett enda värde. Detta kan vara användbart när du ska sammanfatta antalet erbjudna produkter, total försäljning eller antalet studenter.

I det här exemplet grupperar du raderna i en datamängd för utbildningsregistrering. Datan hämtas från Excel-arbetsboken. Den är formad i Power Query-redigeraren till att bara hämta de kolumner du behöver, byta namn på tabellen och göra några andra transformeringar.

Nu ska vi ta reda på hur många myndigheter det finns i varje stat. (Myndigheter kan vara skoldistrikt, andra utbildningsmyndigheter, regionala servicedistrikt med mera.) Välj kolumnen **Byrå-ID – NCES tilldelade \[Distrikt\] Senaste tillgängliga år** och sedan knappen **Gruppera efter** på fliken **Transformera** eller **Start** i menyfliksområdet. (**Gruppera efter**  finns på båda flikarna.)

![Dialogrutan Gruppera efter, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

Dialogrutan **Gruppera efter** öppnas. När Power Query-redigeraren grupperar rader, skapas en ny kolumn där **Gruppera efter**-resultatet placeras. Du kan justera åtgärden **Gruppera efter** på följande sätt:

1. Den omärkta listrutan anger vilken kolumn som ska grupperas. Power Query-redigeraren använder som standard det här värdet för den markerade kolumnen, men du kan ändra det till valfri kolumn i tabellen.
2. **Nytt kolumnnamn**: Power Query-redigeraren föreslår ett namn på den nya kolumnen, baserat på den åtgärd som ska tillämpas på den grupperade kolumnen. Du kan ge den nya kolumn vilket namn du vill dock.
3. **Åtgärd**: Du kan välja vilken åtgärd som Power Query-redigeraren ska utföra, till exempel **Sum**, **Median** eller **Räkna distinkta rader**. Standardvärdet är **Räkna rader**.
4. **Lägg till gruppering** och **Lägg till aggregering**: Dessa knappar är bara tillgängliga om du väljer alternativet **Avancerat**. I en enda åtgärd kan du med hjälp av dessa knappar utföra grupperingsåtgärder (**Gruppera efter**) på många kolumner och skapa flera aggregeringar. Baserat på dina val i dialogrutan skapar Power Query-redigeraren en ny kolumn som kan användas på flera kolumner.

Välj **Lägg till gruppering** eller **Lägg till aggregering** om du vill lägga till fler grupperingar eller aggregeringar i en **Gruppera efter**-åtgärd. Om du vill ta bort en gruppering eller aggregering, väljer du ellips-ikonen ( **...** ) till höger om raden. Klicka sedan på **Ta bort**. Gå vidare och utför åtgärden **Gruppera efter** genom att använda standardvärdena och se vad som händer.

![Dialogrutan Gruppera efter, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

När du väljer **OK**, utför frågan **Gruppera efter**-åtgärden och returnerar resultatet. Oj, ser man på – Ohio, Illinois, Texas och Kalifornien har nu över tusen myndigheter vardera!

![Kolumnen Räkna, åtgärden Gruppera efter, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

Med Power Query-redigeraren kan du dessutom alltid ta bort den senaste formåtgärden. I fönstret **Frågeinställningar** under **Använda steg**, väljer du helt enkelt **X** bredvid det nyligen slutförda steget. Så nu kan du gå vidare och experimentera. Gör om steget om du inte gillar resultatet, till dess att Power Query-redigeraren har format dina data så som du vill ha dem.

## <a name="pivot-columns"></a>Pivotera kolumner

Du kan pivotera kolumner och skapa en tabell med aggregerade värden för varje unikt värde i en kolumn. Om du t.ex. vill ta reda på hur många olika produkter det finns i varje produktkategori, kan du snabbt skapa en tabell som visar detta.

Låt oss titta på ett exempel. Följande tabell **Products_by_Categories** har utformats till att bara visa varje unik produkt (efter namn) och vilken kategori varje produkt finns i. Om du vill skapa en ny tabell som visar antalet produkter i varje kategori (baserat på kolumnen **CategoryName**), markerar du först kolumnen och väljer sedan **Transformera** > **Pivotera kolumn**.

![Kommandot Pivotera kolumn, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

Dialogrutan **Pivotera kolumn** öppnas där du kan se vilka kolumnvärden som kommer att användas för att skapa nya kolumner (1). (Om det önskade kolumnnamnet för **CategoryName** inte visas, kan du välja det i listrutan.) När du expanderar **Avancerade alternativ** (2), kan du välja den funktion som ska tillämpas på de aggregerade värdena (3).

![Dialogrutan Pivotera kolumn, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

När du väljer **OK**, visar frågan tabellen enligt transformeringsinstruktionerna i dialogrutan **Pivotera kolumn**.

![Resultat för Pivotera kolumn, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>Skapa anpassade kolumner

I Power Query-redigeraren kan du skapa anpassade formler som kan köras på flera kolumner i tabellen. Sedan kan du placera resultatet av formlerna i en ny (anpassad) kolumn. Med Power Query-redigeraren är det enkelt att skapa anpassade kolumner.

När du har Excel-arbetsbokens data i Power Query-redigeraren, går du till fliken **Lägg till kolumn** i menyfliksområdet och väljer **Anpassad kolumn**.

![Kommandot Lägg till anpassad kolumn, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

Nedanstående dialogruta öppnas. I exemplet skapar du en anpassad kolumn med namnet *Percent ELL* som beräknar hur stor andel av det totala antalet studenter som är English Language Learners (ELL).

![Dialogrutan Anpassad kolumn, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

Precis som med andra tillämpade steg i Power Query-redigeraren, kan du ta bort steget om den nya anpassade kolumnen inte ger de data du söker. I fönstret **Frågeinställningar** under **Använda steg**, väljer du helt enkelt **X** bredvid steget **Lägg till egen**.

![Använda steg, fönstret Frågeinställningar, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>Fråga formler

Du kan redigera stegen som Power Query-redigeraren genererar. Du kan också skapa anpassade formler för att kunna ansluta till och forma dina data mer exakt. När Power Query-redigeraren utför en åtgärd på data, visas den formel som är kopplad till åtgärden i formelfältet. Om du vill se formelfältet går du till fliken **Visa** i menyfliksområdet och väljer sedan **Formelfält**.

![Alternativet Formelfält, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_formulabar.png)

Power Query-redigeraren behåller alla använda steg för varje fråga som text, som du sedan kan visa och redigera. Du kan visa eller ändra texten för en fråga med hjälp av **Avancerad redigerare**. Välj bara **Visa** och sedan **Avancerad redigerare**.

![Kommandot Avancerad redigerare, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

Låt oss ta en titt på den **avancerade redigeraren**, med de frågesteg som är kopplade till den visade frågan **USA\_StudentEnrollment**. De här stegen skapas i Power Query-formelspråket, vilket ofta kallas *M*. Mer information finns i [Lär dig mer om Power Query-formler](https://support.office.com/article/learn-about-power-query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f). Om du vill se själva språkspecifikationen kan du gå till [Specifikation för Power Query M-språket](/powerquery-m/power-query-m-language-specification).

![Dialogrutan Avancerad redigerare, Power Query-redigeraren, Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

Power BI Desktop innehåller en omfattande uppsättning formelkategorier. Mer information och en fullständig referens för alla formler i Power Query-redigeraren finns i [Referens för Power Query M-funktioner](/powerquery-m/power-query-m-function-reference).

## <a name="next-steps"></a>Nästa steg

Du kan göra många olika saker med Power BI Desktop. I följande resurser finns mer information om dess möjligheter:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Ansluta till data i Power BI Desktop](desktop-connect-to-data.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
