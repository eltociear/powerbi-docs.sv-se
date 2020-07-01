---
title: Komma igång med Power BI Desktop
description: Kom igång med Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 03/13/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 409771c8786fb704fbf2a882353e8e3f20ec2437
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85222195"
---
# <a name="get-started-with-power-bi-desktop"></a>Komma igång med Power BI Desktop
Välkommen till Komma igång-guiden för Power BI Desktop. Den här guiden visar hur Power BI Desktop fungerar, vad det kan göra samt hur du skapar robusta datamodeller och fantastiska rapporter som förbättrar din Business Intelligence.

Om du vill få en snabb översikt över hur Power BI Desktop fungerar och hur du använder det kan du gå igenom bilderna i den här guiden på bara några minuter. För en mer ingående förståelse kan du läsa igenom avsnitten, utföra stegen och skapa din egen Power BI Desktop-fil som kan publiceras till [Power BI-tjänsten](https://app.powerbi.com/) och delas med andra.

![Power BI Desktop-rapport](media/desktop-getting-started/hero-02.png)

Du kan även titta på videon [Komma igång med Power BI Desktop](https://www.youtube.com/watch?v=Qgam9M8I0xA) och ladda ned Excel-arbetsboken [Financial Sample](https://go.microsoft.com/fwlink/?LinkID=521962) (Ekonomiexempel) för att följa med videon.

## <a name="how-power-bi-desktop-works"></a>Så här fungerar Power BI Desktop
Med Power BI Desktop kan du:
1. Ansluta till data, däribland flera datakällor.
1. Forma data med frågor som skapar insiktsfulla, övertygande datamodeller.
1. Använda datamodeller för att skapa visualiseringar och rapporter. 
1. Dela dina rapportfiler så att andra kan använda, bygga vidare på och dela dem. Du kan dela *.pbix*-filer för Power BI Desktop på samma sätt som med andra filer, men den kanske främsta metoden är att ladda upp dem till [Power BI-tjänsten](https://preview.powerbi.com/). 

Power BI Desktop integrerar beprövade tekniker för Microsoft-frågemotorn, datamodellering och visualisering. Dataanalytiker och andra kan skapa samlingar med frågor, dataanslutningar, modeller samt rapporter och enkelt dela dem med andra. Kombinationen av Power BI Desktop och Power BI-tjänsten gör det enklare att modellera, bygga, dela och utöka nya insikter från datavärlden.

Power BI Desktop centraliserar, förenklar och strömlinjeformar något som annars kan uppfattas som en utspridd, lösryckt och mödosam process med att business intelligence-centrallager och -rapporter.
Är du redo att testa? Nu börjar vi.

> [!NOTE]
> För data och rapportering som måste hanteras lokalt finns det en separat och specialiserad version av Power BI som heter [Power BI-rapportserver](../report-server/get-started.md). Power BI-rapportserver använder en separat och specialiserad version av Power BI Desktop som heter Power BI Desktop för Power BI-rapportserver, som bara fungerar med rapportserver-versionen av Power BI. I den här artikeln beskrivs standardversionen av Power BI Desktop.

## <a name="install-and-run-power-bi-desktop"></a>Installera och kör Power BI Desktop
Om du vill ladda ned Power BI Desktop går du till [nedladdningssidan för Power BI Desktop](https://powerbi.microsoft.com/desktop) och väljer **Ladda ned kostnadsfritt**. Om du vill få nedladdningsalternativ väljer du [Se alternativ för nedladdning eller språk](https://www.microsoft.com/download/details.aspx?id=58494). 

Du kan även ladda ned Power BI Desktop från Power BI-tjänsten. Välj ikonen **Ladda ned** på den översta menyraden och välj sedan **Power BI Desktop**.

![Ladda ned Power BI Desktop från Power BI-tjänsten](media/desktop-getting-started/gsg_download.png)

På Microsoft Store-sidan väljer du **Hämta** och följer anvisningarna för att installera Power BI Desktop på datorn. Starta Power BI Desktop i **Starta-menyn** i Windows eller via ikonen i aktivitetsfältet i Windows.

Första gången Power BI Desktop startar visas skärmen **Välkommen**.

På skärmen **Välkommen** kan du **Hämta data**, se **Senaste källor**, öppna de senaste rapporterna, **Öppna andra rapporter** eller välja andra länkar. Du kan även välja om skärmen **Välkommen** alltid ska visas vid start. Välj ikonen Stäng för att stänga skärmen **Välkommen**.

![Välkomstskärmen för Power BI Desktop](media/desktop-getting-started/designer_gsg_startsplashscreen.png)

På vänster sida i Power BI Desktop finns ikoner för de tre Power BI Desktop-vyerna: **Rapport**, **Data** och **Relationer**, uppifrån och ned. Den aktuella vyn anges av det gula fältet till vänster, och du kan ändra vyer genom att välja bland ikonerna. 

![Ikoner för de tre Power BI Desktop-vyerna](media/desktop-getting-started/designer_gsg_viewtypes.png)

Standardvyn är vyn **Rapport**. 

![Rapportvy i Power BI Desktop](media/desktop-getting-started/designer_gsg_blankreport.png)

Power BI Desktop innehåller även **Power Query-redigeraren**, som öppnas i ett separat fönster. I **Power Query-redigeraren** kan du skapa frågor och transformera data. Du kan därefter läsa in denna förfinade datamodell i Power BI Desktop för att skapa rapporter.

## <a name="connect-to-data"></a>Ansluta till data
Med Power BI Desktop installerat är du redo att ansluta till den ständigt växande datavärlden. Om du vill se de många typer av datakällor som är tillgängliga väljer du **Hämta data** > **Mer** på fliken **Start** i Power BI Desktop, och i fönstret **Hämta data** bläddrar du igenom listan med **Alla** datakällor. I den snabbturen ansluter du till ett par olika datakällor för **Webben**.

![Välja webbdatakälla från Hämta data ](media/desktop-getting-started/getdataweb.png)

Föreställ dig att du arbetar som dataanalytiker hos en återförsäljare av solglasögon. Du vill hjälpa kunden att fokusera försäljning av solglasögon till de områden där solen skiner oftast. Bankrate.com-sidan [Best and worst states for retirement](https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/) (de bästa och sämsta delstaterna för pension) innehåller intressant information om det här ämnet.

På fliken **Start** i Power BI Desktop väljer du **Hämta data** > **Webben** för att ansluta till en webbdatakälla. 

![Välja webbdatakälla](media/desktop-getting-started/gsg_syw_2.png)

I dialogrutan **Från webben** klistrar du in adressen *https:\//www.bankrate.com/retirement/best-and-worst-states-for-retirement/* i fältet **URL** och väljer **OK**. 

![Klistra in webbadress i dialogrutan Från webben](media/desktop-getting-started/gettingstarted_8.png)

På skärmen **Anslut till webbinnehåll** väljer du **Anslut**, om du uppmanas till det, för att använda anonym åtkomst. 

Frågefunktionen i Power BI Desktop börjar arbeta och kontaktar webbresursen. Fönstret **Navigatör** returnerar det som hittas på webbsidan, i det här fallet en tabell som heter **Ranking of best and worst states for retirement** (Rangordning av de bästa och sämsta delstaterna för pension) samt ett dokument. Det är tabellen som är intressant, så välj den för att se en förhandsgranskning.

Nu kan du välja **Läs in** för att läsa in tabellen eller **Transformera data** för att göra ändringar i tabellen innan du läser in den.

![Förhandsgranskning av tabell från webbsida](media/desktop-getting-started/datasources_fromnavigatordialog.png)

När du väljer **Transformera data** öppnas Power Query-redigeraren med en representativ vy av tabellen. Fönstret **Frågeinställningar** finns till höger. Du kan även välja att alltid visa det genom att välja **Frågeinställningar** på fliken **Visa** i Power Query-redigeraren. 

![Power Query-redigeraren med frågeinställningar](media/desktop-getting-started/designer_gsg_editquery.png)

Mer information om hur du ansluter till data finns i [Anslut till data i Power BI Desktop](../connect-data/desktop-connect-to-data.md).

## <a name="shape-data"></a>Forma data
Nu när vi har anslutit till en datakälla kan du justera dessa data så att de uppfyller behoven. Om du vill *forma* data ger du Power Query-redigeraren stegvisa instruktioner för att justera data vid inläsning och presentera dem. Formning påverkar inte den ursprungliga datakällan, utan bara just den här datavyn. 

> [!NOTE]
> De tabelldata som används i den här handboken kan komma att ändras med tiden. De steg som du behöver följa kan därför vara annorlunda, varför du behöver vara kreativ när du anpassar steg eller resultat – men det är också en del av det roliga med inlärningen. 

Formning kan innebära att *transformera* data, till exempel byta namn på kolumner eller tabeller, ta bort rader eller kolumner eller ändra datatyper. Power Query-redigeraren samlar de här stegen sekventiellt under **Tillämpade steg** i fönstret **Frågeinställningar**. Varje gång den här frågan ansluter till datakällan utförs de stegen så att data alltid formas på det sätt du anger. Den här processen inträffar när du använder frågan i Power BI Desktop eller när någon använder din delade fråga, till exempel i Power BI-tjänsten. 

Observera att **Tillämpade steg** i **Frågeinställningar** redan innehåller några steg. Du kan välja varje steg för att se dess inverkan i Power Query-redigeraren. Först angav du en webbadress och sedan förhandsgranskade du tabellen i fönstret **Navigatör**. I det tredje steget, **Ändrad typ**, identifierade Power BI heltalsdata när dessa importerades och ändrade automatiskt den ursprungliga **Text**-*datatypen* för webb till **Heltal**. 

![Fönstret Frågeinställningar med tre tillämpade steg](media/desktop-getting-started/designer_gsg_appliedsteps_changedtype.png)

Om du behöver ändra en datatyp markerar du den kolumn eller de kolumner som du vill ändra. Håll ned tangenten **Skift** för att markera flera intilliggande kolumner, eller **Ctrl** för att markera kolumner som inte är intilliggande. Antingen högerklickar du på en kolumnrubrik, väljer **Ändra typ** och väljer en ny datatyp i menyn, eller så visar du listan intill **Datatyp** i gruppen **Transformera** på fliken **Start** och väljer en ny datatyp.

![Ändra datatyp](media/desktop-getting-started/designer_gsg_changedatatype.png)

> [!NOTE]
> Power Query-redigeraren i Power BI Desktop använder menyfliksområdet eller högerklicksmenyerna för tillgängliga uppgifter. De flesta uppgifter som du kan välja på flikarna **Start** eller **Transformera** i menyfliksområdet är även tillgängliga om du högerklickar på ett objekt och väljer från den meny som visas.

Nu kan du tillämpa dina egna ändringar och transformeringar på data och se dem i **Tillämpade steg**. 

Till exempel är du för försäljning av solglasögon kanske mest intresserad av väderrangordningen, så du väljer att sortera tabellen efter kolumnen **Väder** i stället för **Övergripande ranking**. Klicka på pilen intill rubriken **Väder** och välj **Sortera stigande**. Data visas nu sorterade efter väderrangordning, och steget **Sorterade rader** visas i **Tillämpade steg**. 

![Sortera rader stigande](media/desktop-getting-started/shapecombine-changetype-b.png)

Du är inte intresserad av att sälja solglasögon till delstaterna med det sämsta vädret, så du väljer att ta bort dem från tabellen. Från gruppen **Minimera rader** på fliken **Start** väljer du **Ta bort rader** > **Ta bort de nedersta raderna**. I dialogrutan **Ta bort de nedersta raderna** anger du *10* och väljer sedan **OK**. 

![Ta bort de nedersta raderna](media/desktop-getting-started/pbi_gsg_getdata3.png)

De tio nedersta raderna med sämst väder tas bort från tabellen, och steget **Borttagna nedre rader** visas i **Tillämpade steg**.

Du anser att tabellen har för mycket extra information för dina behov och tar bort kolumnerna **Priser**, **Brottslighet**, **Kultur** och **Hälsa**. Markera rubriken för varje kolumn som du vill ta bort. Håll ned tangenten **Skift** för att markera flera intilliggande kolumner, eller **Ctrl** för att markera kolumner som inte är intilliggande. 

I gruppen **Hantera kolumner** på fliken **Start** väljer du sedan **Ta bort kolumner**. Du kan även högerklicka på en av de valda kolumnrubrikerna och välja **Ta bort kolumner** i menyn. De markerade kolumnerna tas bort, och steget **Borttagna kolumner** visas i **Tillämpade steg**.

![Ta bort kolumner](media/desktop-getting-started/pbi_gsg_getdata3a.png)

Vid närmare eftertanke kan **Priser** trots allt vara relevant för försäljning av solglasögon. Du skulle vilja få tillbaka den kolumnen. Du kan enkelt ångra det senaste steget i fönstret **Tillämpade steg** genom att välja borttagningsikonen **X** intill steget. Gör nu om steget och markera bara de kolumner som du vill ta bort. Du kan få mer flexibilitet genom att ta bort varje kolumn som ett separat steg. 

Du kan högerklicka på valfritt steg i fönstret **Tillämpade steg** och välja att ta bort det, byta namn på det, flytta det uppåt eller nedåt i sekvensen eller lägga till eller ta bort steg efter det. För mellanliggande steg varnar Power BI Desktop dig om ändringen kan påverka senare steg och bryta frågan.  

![Ändra tillämpade steg](media/desktop-getting-started/designer_gsg_install.png)

Om du till exempel inte längre vill sortera tabellen efter **Väder** kan du försöka ta bort steget **Sorterade rader**. Power BI Desktop varnar dig om att borttagning av det här steget kan göra att frågan bryts. Du har tagit bort de nedersta tio raderna efter att du sorterat efter väder, så om du tar bort sorteringen tas olika rader bort. Du får även en varning om du väljer steget **Sorterade rader** och försöker lägga till ett nytt mellanliggande steg där.  

![Varning om borttagning av steg](media/desktop-getting-started/deletestepwarning.png)

Slutligen ändrar du tabellrubriken så att den handlar om försäljning av solglasögon i stället för pension. Under **Egenskaper** i rutan **Frågeinställningar** ersätter du den gamla rubriken med *De bästa delstaterna för försäljning av solglasögon*.

Den färdiga frågan för dina formade data ser ut så här:

![Slutförd fråga](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

Mer information om hur du formar data finns i [Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md).

## <a name="combine-data"></a>Kombinera data
Data om olika delstater är intressanta och kommer vara användbara när vi skapar andra analyser och frågor. Men det finns ett problem: de flesta data använder en förkortning med två bokstäver för delstatskoder, inte det fullständiga namnet på delstaterna. För att kunna använda dessa data behöver du ett sätt att associera delstatsnamn med deras förkortningar.

Som tur är går det att ordna. Det finns en annan offentlig datakälla som gör precis detta, men dessa data behöver en del formning innan du kan *kombinera* dem med din tabell för solglasögon.

Du importerar data om delstaternas förkortningar till Power Query-redigeraren genom att välja **Ny källa** > **Webb** i gruppen **Ny fråga** på fliken **Start** i menyfliksområdet. 

![Ny källa](media/desktop-getting-started/pbi_gettingstartedsplash_resized.png)

I dialogrutan **Från webb** anger du URL:en till webbplatsen för delstaternas förkortningar: *https:\//en.wikipedia.org/wiki/List_of_U.S._state_abbreviations*.

I fönstret **Navigatör** väljer du tabellen **Koder och förkortningar för amerikanska delstater, federala distrikt, territorier och andra regioner** och väljer sedan **OK**. Tabellen öppnas i Power Query-redigeraren.

Ta bort alla kolumner förutom **Regionens namn och status**, **Regionens namn och status2** och **ANSI**. Behåll endast dessa kolumner genom att hålla ned **Ctrl** och markera kolumnerna. Sedan högerklickar du antingen på en av kolumnrubrikerna och väljer **Ta bort andra kolumner** eller går till gruppen **Hantera kolumner** på fliken **Start** och väljer **Ta bort andra kolumner**. 

Klicka på pilen intill kolumnrubriken **Regionens namn och status2** och välj **Filter** > **Är lika med**. I dialogrutan **Filtrera rader** visar du fältet **Ange eller välj ett värde** intill **är lika med** och väljer **Delstat**. 

Välj **Eller**. Intill det andra fältet **är lika med** väljer du sedan **Delstat ("Commonwealth")** . Välj **OK**. 

![Filtrera rader](media/desktop-getting-started/filterrows.png)

Nu när de extra värdena såsom **Federala distrikt** och **ö** har tagits bort har du en lista över de 50 delstaterna och deras officiella förkortningar med två bokstäver. Du kan byta namn på kolumnerna så att de blir mer begripliga, till exempel **Delstatsnamn**, **Status** och **Förkortning** genom att högerklicka på kolumnrubrikerna och välja **Byt namn**.

Observera att alla dessa steg finns under **Tillämpade steg** i fönstret **Frågeinställningar**.

Nu ser den formade tabellen ut så här:

![Formad tabell med Delstatskoder](media/desktop-getting-started/statecodes.png)

Byt namn på tabellens rubrik till *Delstatskoder* i fältet **Egenskaper** i **Frågeinställningar**. 

När tabellen **Delstatskoder** har formats kan du *kombinera* dessa två tabeller till en tabell. Eftersom de tabeller du har nu är resultatet av frågor som du har tillämpat på data kallas de även också för *frågor*. Det finns två huvudsakliga sätt att kombinera frågor: *sammanslå* och *lägga till*. 

När du har en eller flera kolumner som du vill lägga till i en annan fråga kan du *sammanslå* frågorna. När du har ytterligare rader med data som du vill lägga till en befintlig fråga kan du *lägga till* frågan.

I det här fallet vill du *sammanslå* frågan **Delstatskoder** till frågan **De bästa delstaterna för solglasögon**. För att sammanfoga frågorna växlar du till frågan **De bästa delstaterna för solglasögon** genom att välja den i rutan **Frågor** till vänster i Power Query-redigeraren. Välj sedan **Sammanslå frågor** i gruppen **Kombinera** på fliken **Start** i menyfliksområdet.

I fönstret **Sammanslå** visar du fältet för att välja **Delstatskoder** bland de andra tillgängliga frågorna. Markera den kolumn som ska matchas från varje tabell, i det här fallet **Delstat** från frågan **De bästa delstaterna för solglasögon** och **Delstatsnamn** från frågan **Delstatskoder** fråga. 

Om dialogrutan **Sekretessnivåer** visas väljer du **Ignorera kontroller av sekretessnivå för den här filen** och sedan **Spara**. Välj **OK**. 

![Sammanslå frågor](media/desktop-getting-started/shapecombine_merge.png)

En ny kolumn med namnet **Delstatskoder** visas till höger om tabellen **De bästa delstaterna för försäljning av solglasögon**. Den innehåller den fråga för delstatskoder som du sammanslog med frågan för de bästa delstaterna för försäljning av solglasögon. Alla kolumner från den sammanslagna tabellen samlas i kolumnen **Delstatskoder**. Du kan *expandera* den sammanslagna tabellen och endast inkludera de kolumner som du vill ha. 

![Sammanslagen frågekolumn](media/desktop-getting-started/mergedquery.png)

Om du vill expandera den sammanslagna tabellen och välja vilka kolumner som ska inkluderas väljer du ikonen **Expandera** i kolumnrubriken. I dialogrutan **Expandera** väljer du bara kolumnen **Förkortning**. Avmarkera **Använd det ursprungliga kolumnnamnet som prefix** och välj sedan **OK**. 

![Välja expanderad kolumn från sammanslagen tabell](media/desktop-getting-started/shapecombine_mergeexpand.png)

> [!NOTE]
> Du kan prova olika sätt att införa tabellen **Delstatskoder**. Experimentera lite. Om du inte gillar resultatet tar du bara bort det steget från listan **Tillämpade steg** i fönstret **Frågeinställningar**. Det är som en gratis uppfräschning, som du kan upprepa hur många gånger som helst tills du är nöjd med expanderingsprocessen.

En fullständig beskrivning av stegen för att forma och kombinera data finns i [Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md).

Nu har du en enda frågetabell där de två datakällor kombineras, och var och en är formad efter dina behov. Den här frågan kan fungera som bas för många intressanta dataanslutningar, till exempel demografi, välståndsnivåer eller rekreationsmöjligheter i delstaterna.

![Formade och kombinerade frågor](media/desktop-getting-started/mergedcolumn.png)

För tillfället har du tillräckligt med data för att skapa en intressant rapport i Power BI Desktop. Eftersom det här är en milstolpe tillämpar du ändringarna i **Power Query-redigeraren** och läser in dem i Power BI Desktop genom att välja **Stäng och tillämpa** på fliken **Start** i menyfliksområdet. Du kan även välja **Tillämpa** för att låta frågan vara öppen i Power Query-redigeraren medan du arbetar i Power BI Desktop. 

![Stäng och tillämpa ändringarna](media/desktop-getting-started/shapecombine_closeandapply.png)

Du kan göra fler ändringar i en tabell när den har lästs in i Power BI Desktop och läsa in modellen igen för att tillämpa de ändringar du gör. Om du vill öppna **Power Query-redigeraren** på nytt från Power BI Desktop väljer du **Redigera frågor** på fliken **Start** i menyfliksområdet i Power BI Desktop. 

## <a name="build-reports"></a>Skapa rapporter
I vyn **Rapport** i Power BI Desktop kan du bygga visualiseringar och rapporter. Vyn **Rapport** innehåller sex huvudområden:

![Rapportvy i Power BI Desktop](media/desktop-getting-started/designer_gsg_reportview.png)

1. Menyfliksområdet längst upp, där vanliga uppgifter som är hör till rapporter och visualiseringar visas.
2. Arbetsytan i mitten, där visualiseringar skapas och arrangeras.
3. Sidfliken längst ned, där du kan välja eller lägga till rapportsidor.
4. Fönstret **Filter**, där du kan filtrera datavisualiseringar.
5. Fönstret **Visualiseringar**, där du kan lägga till, ändra eller anpassa visualiseringar och tillämpa visning av detaljerad information.
6. Rutan **Fält**, som visar tillgängliga fält i dina frågor. Du kan dra de här fälten till arbetsytan, fönstret **Filter** eller fönstret **Visualiseringar** för att skapa eller ändra visualiseringar.

Du kan expandera och minimera fönstren **Filter**, **Visualiseringar** och **Fält** genom att välja pilarna överst i fönstren. Om du minimerar fönstren skapas mer utrymme på arbetsytan för att bygga häftiga visualiseringar. 

![Expandera eller minimera fönster](media/desktop-getting-started/designer_gsg_collapsepanes.png)

Om du vill skapa en enkel visualisering väljer du bara ett fält i fältlistan eller drar fältet från listan **Fält** till arbetsytan. Du kan till exempel dra fältet **Delstat** från **De bästa delstaterna för försäljning av solglasögon** till arbetsytan och se vad som händer.

![Dra fältet Delstat för att skapa en kartvisualisering](media/desktop-getting-started/designer_gsg_reportfirstdrag.png)

Ser man på! Power BI Desktop registrerade att fältet **Delstat** innehöll geoplatsdata och skapade automatiskt en kartbaserad visualisering. Visualiseringen visar datapunkter för de 40 delstaterna från din datamodell. 

Fönstret **Visualiseringar** visar information om visualiseringen och gör att du kan ändra den. 

![Fönstret Visualisering](media/desktop-getting-started/designer_gsg_visualizationtypes.png)

1. Ikonerna visar vilken typ av visualisering som skapats. Du kan ändra typen för en vald visualisering genom att välja en annan ikon eller skapa en ny visualisering genom att välja en ikon utan att någon befintlig visualisering har valts. 
2. Med alternativet **Fält** i fönstret **Visualisering** kan du dra datafält till **Förklaring** och andra fältbrunnar i fönstret. 
3. Med alternativet **Format** kan du tillämpa formatering och andra kontroller på visualiseringar. 

De alternativ som är tillgängliga i områdena **Fält** och **Format** beror på vilken typ av visualisering och data du har.

Du vill att kartvisualiseringen bara ska visa de tio delstater som har bäst väder. Om du bara vill visa de 10 främsta delstaterna går du till fönstret **Filter**, hovrar över **Delstaten är (Alla)** och expanderar den pil som visas. Under **Filtertyp** öppnar du och väljer **Högsta N**. Under **Visa objekt** väljer du **Lägsta**, eftersom du vill visa objekten med de lägsta numeriska rangordningarna, och anger *10* i nästa fält.

Dra fältet **Väder** från fönstret **Fält** till fältet **Efter värde** och välj **Tillämpa filter**. 

![Filtret Topp 10 för väder](media/desktop-getting-started/gsg_share5.png)

Nu visas bara de tio delstaterna med bäst väder i kartvisualiseringen. 

Byt namn på visualiseringens rubrik genom att välja ikonen **Format** i fönstret **Visualiseringar** följt av **Rubrik** och skriva *De tio delstaterna med bäst väder* under **Rubriktext**. 

![Ändra rubrik](media/desktop-getting-started/designer_gsg_report1.png)

Om du vill lägga till en visualisering som visar namnen på de tio delstaterna med bäst väder och deras rangordning från 1 till 10 markerar du ett tomt område på arbetsytan och väljer sedan ikonen **Kolumndiagram** i fönstret **Visualisering**. I fönstret **Fält** väljer du **Delstat** och **Väder**. Ett kolumndiagram visar de 40 delstaterna i frågan rangordnade från högsta till lägsta numeriska rang eller sämst till bäst väder. 

![Visualisering med kolumndiagram](media/desktop-getting-started/gsg_share7.png)

Om du vill växla ordningen på rangordningen så att siffran 1 visas först väljer du ellipsen **Fler alternativ** längst upp till höger i visualiseringen och sedan **Sortera stigande** i menyn. 

![Sortera stigande](media/desktop-getting-started/shapecombine_mergequeries.png)

Om du vill begränsa tabellen till de 10 främsta delstaterna använder du filter för de lägsta tio som du gjorde för kartvisualiseringen. 

Byt namn på visualiseringens rubrik på samma sätt som för kartvisualiseringen. I avsnittet **Format** i fönstret **Visualiseringar** ändrar du även **Y-axel** > **Axelrubrik** från **Väder** till *Väderrangordning* så att den blir lättare att förstå. Sedan växlar du **Y-axel** till **Av** och **Dataetiketter** till **På**. 

Nu visas de tio delstaterna med bäst väder i rangordning tillsammans med sin numeriska rangordning. 

![Avslutade stapeldiagram](media/desktop-getting-started/shapecombine_changetype.png)

Du kan skapa liknande eller andra visualiseringar för fälten **Priser** och **Övergripande rangordning** eller kombinera flera fält till en enda visualisering. Det finns en massa olika intressanta rapporter och visualiseringar som du kan skapa. Dessa visualiseringar för **Tabell** och **Linjediagram och grupperat stående stapeldiagram** visar de tio delstaterna med bäst väder tillsammans med deras priser och övergripande rangordning:

![Visualiseringar av tabell samt linjediagram och grupperat stående diagram](media/desktop-getting-started/designer_gsg_report2costofliving.png)

Du kan visa olika visualiseringar på olika rapportsidor. Om du vill lägga till en ny sida väljer du symbolen **+** intill de befintliga sidorna i sidfältet eller väljer **Infoga** > **Ny sida** på fliken **Start** i menyfliksområdet. Om du vill byta namn på en sida dubbelklickar du på sidans namn i sidfältet eller högerklickar på den och väljer **Byt namn på sida** och skriver sedan det nya namnet. Om du vill gå till en annan sida i rapporten väljer du sidan i sidfältet. 

![Sidfält](media/desktop-getting-started/pages.png)

Du kan lägga till textrutor, bilder och knappar till rapportsidorna från gruppen **Infoga** på fliken **Start**. Om du vill ange formateringsalternativ för visualiseringar väljer du en visualisering och väljer sedan ikonen **Format** i fönstret **Visualiseringar**. Om du vill konfigurera sidstorlekar, bakgrunder och annan sidinformation väljer du ikonen **Format** utan någon visualisering markerad.

När du har skapat sidorna och visualiseringarna väljer du **Arkiv** > **Spara** och sparar rapporten. 

![Slutförd rapportsida i Power BI Desktop](media/desktop-getting-started/finished-report.png)

Mer information om rapporter finns i [Rapportvyn i Power BI Desktop](../create-reports/desktop-report-view.md).

## <a name="share-your-work"></a>Dela ditt arbete
Nu när du har en Power BI Desktop-rapport kan du dela den med andra. Det finns några olika sätt att dela ditt arbete. Du kan distribuera rapportens *.pbix*-fil som med andra filer, ladda upp *.pbix*-filen från Power BI-tjänsten eller publicera direkt från Power BI Desktop till Power BI-tjänsten. Du måste ha ett Power BI-konto för att kunna publicera eller ladda upp rapporter till Power BI-tjänsten. 

Om du vill publicera till **Power BI-tjänsten** från Power BI Desktop går du till fliken **Start** i menyfliksområdet och väljer **Publicera**.

![Välja Publicera](media/desktop-getting-started/gsg_syw_1.png)

Du uppmanas kanske att logga in på Power BI eller välja ett mål.

När publiceringsprocessen är klar visas följande dialogruta:

![Power BI – Publiceringen lyckades](media/desktop-getting-started/gsg_syw_3.png)

När du väljer länken för att öppna rapporten i Power BI öppnas rapporten på Power BI-plats under **Min arbetsyta** > **Rapporter**. 

Ett annat sätt att dela ditt arbete är att läsa in det från **Power BI**-tjänsten. Gå till *https:\//app.powerbi.com* för att öppna Power BI i en webbläsare. På sidan **Start** i Power BI väljer du **Hämta data** längst ned till vänster för att påbörja processen med att läsa in din Power BI Desktop-rapport.

![Välja Hämta data på Power BI-startsidan](media/desktop-getting-started/pbi_gsg_getdata1.png)

På nästa sida väljer du **Hämta** i avsnittet **Filer**.

![Hämta filer](media/desktop-getting-started/pbi_gsg_getdata2.png)

På nästa sida väljer du **Lokal fil**. Bläddra till och välj din Power BI Desktop *.pbix*-fil följt av **Öppna**. 

När filen har importerats visas den under **Min arbetsyta** > **Rapporter** i det vänstra fönstret i Power BI-tjänsten.

![Power BI Desktop-fil som importerats till Power BI](media/desktop-getting-started/pbi_gsg_getdata4.png)

När du väljer filen visas den första sidan i rapporten. Du kan välja olika sidor från flikarna till vänster i rapporten. 

Du kan göra ändringar i en rapport i **Power BI-tjänsten** genom att välja **Fler alternativ** > **Redigera** från rapportarbetsytans överkant. Spara ändringarna genom att välja **Spara en kopia**.

![Redigera en rapport och spara en kopia](media/desktop-getting-started/gsg_share4.png)

Det finns en massa olika intressanta visualiseringar som du kan skapa i **Power BI-tjänsten**, som du sedan kan fästa på en *instrumentpanel*. Mer information om instrumentpaneler i **Power BI-tjänsten** finns i [Tips för att designa en utmärkt instrumentpanel](../create-reports/service-dashboards-design-tips.md). Mer information om hur du skapar, delar och modifierar instrumentpaneler finns i [Dela en instrumentpanel](../collaborate-share/service-share-dashboards.md).

Om du vill dela en rapport eller instrumentpanel väljer du **Dela** längst upp på den öppna rapportsidan eller instrumentpanelen, eller så kan du välja ikonen **Dela** intill rapportens eller instrumentpanelens namn i listorna **Min arbetsyta** > **Rapporter** eller **Min arbetsyta** > **Instrumentpaneler**.

Slutför skärmen **Dela rapport** eller **Dela instrumentpanel** för att skicka ett e-postmeddelande eller hämta en länk för att dela rapporten eller instrumentpanelen med andra. 

![Dela rapport](media/desktop-getting-started/gsg_share6.png)

Det finns många intressanta datarelaterade kombinationer och visualiseringar som du kan skapa med Power BI Desktop och Power BI-tjänsten. 

## <a name="next-steps"></a>Nästa steg
Power BI Desktop stöder anslutning till en diagnostikport. Diagnostikporten gör att andra verktyg kan ansluta och utföra spårningar i diagnossyfte. Vid användning av diagnostikporten *finns det inte stöd för att göra ändringar i modellen. Ändringar i modellen kan leda till skador och förlorade data.*

Mer information om de många funktionerna i Power BI Desktop finns i följande resurser:

* [Frågeöversikt i Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datakällor i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Ansluta till data i Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Självstudie: Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   
