---
title: 'Självstudier: Skapa beräknade kolumner i Power BI Desktop'
description: 'Självstudier: Skapa beräknade kolumner i Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 11/26/2019
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: 858ecc07deabf5b91295220c2b92791b998ecf3a
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83349251"
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>Självstudier: Skapa beräknade kolumner i Power BI Desktop

Ibland innehåller de data som du analyserar inte det fält som du behöver för att kunna hämta ett visst resultat. Det är därför vi använder *beräknade kolumner*. Beräknade kolumner använder DAX-formler (Data Analysis Expressions) för att definiera en kolumns värden, allt från att sätta ihop textvärden från ett antal olika kolumner till att beräkna ett numeriskt värde från andra värden. Anta till exempel att dina data har **Stad** och **Delstat**, men du vill ha ett enda fält för **Plats** som har båda värdena, som ”Miami, FL”. Detta är exakt vad beräknade kolumner är till för.

Beräknade kolumner liknar [mått](desktop-tutorial-create-measures.md) i och med att båda är baserade på DAX-formler, men de skiljer sig åt i hur de används. Du använder ofta åtgärder i en visualiserings område för **Värden** för att beräkna resultat baserat på andra fält. Du använder beräknade kolumner som nya **Fält** i visualiseringarnas rader, axlar, förklaringar och gruppområden.

I den här självstudien får du hjälp att förstå och skapa några beräknade kolumner och använda dem i rapportvisualiseringar i Power BI Desktop.

## <a name="prerequisites"></a>Förutsättningar

- Den här självstudien är avsedd för Power BI-användare som redan är bekanta med Power BI Desktop och som vill skapa mer avancerade modeller. Du bör redan känna till hur du använder Hämta data och Power Query-redigeraren till att importera data, arbeta med flera relaterade tabeller och lägga till fält på rapportarbetsytan. Om du är nybörjare i Power BI Desktop bör du läsa [Komma igång med Power BI Desktop](../fundamentals/desktop-getting-started.md).
  
- I självstudiekursen används [Contoso-försäljningsexemplet för Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip), samma exempel som används för självstudien [Skapa dina egna mått i Power BI Desktop](desktop-tutorial-create-measures.md). Dessa försäljningsdata från det fiktiva företaget Contoso, Inc. har importerats från en databas, så du kan inte ansluta till datakällan eller visa den i Power Query-redigeraren. Hämta och packa upp filen på din dator och öppna den sedan i Power BI Desktop.

## <a name="create-a-calculated-column-with-values-from-related-tables"></a>Skapa en beräknad kolumn med värden från relaterade tabeller

I din försäljningsrapport vill du visa produktkategorier och underkategorier som ett enskilt värde, som t.ex. ”Mobiltelefoner – tillbehör”, ”Mobiltelefoner – smartphones och surfplattor” etc. Det finns inget fält listan **Fält** som ger dessa data, men det finns ett **ProductCategory**-fält och ett **ProductSubcategory**-fält, vart och ett i sin egen tabell. Du kan skapa en beräknad kolumn som kombinerar värden från de här två kolumnerna. DAX-formulär kan utnyttja alla fördelar med den modell som du redan har, inklusive relationerna mellan olika tabeller som redan finns.

 ![Kolumner i fältlistan](media/desktop-tutorial-create-calculated-columns/create1.png)

1. Om du vill skapa en ny kolumn i tabellen **ProductSubcategory** högerklickar du på eller väljer ellipsen **...** bredvid **ProductSubcategory** i fönstret **Fält** och väljer **Ny kolumn** från menyn.

   ![Ny kolumn](media/desktop-tutorial-create-calculated-columns/create2.png)

   När du väljer **Ny kolumn** visas **formelfältet** överst på rapportarbetsytan, så att du kan namnge din kolumn och ange en DAX-formel.

   ![Formelfält](media/desktop-tutorial-create-calculated-columns/create3.png)

2. Som standard får nya beräknade kolumner namnet **Kolumn**. Om du inte byter ut det här namnet får ytterligare nya kolumner namnet **Kolumn 2**, **Kolumn 3** och så vidare. Du vill att kolumnen ska vara enklare att identifiera, så även om namnet **Kolumn** redan är markerat i formelfältet byter du ut det här namnet genom att skriva **ProductFullCategory** och sedan ett likhetstecken ( **=** ).

3. Du vill att värdena i din nya kolumn ska börja med namnet i fältet **ProductCategory**. Eftersom den här kolumnen finns i annan (men relaterad) tabell, kan du använda funktionen [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) för att hämta den.

   Efter likhetstecknet skriver du **r**. En listruta med förslag visar alla DAX-funktioner som börjar med bokstaven R. Genom att välja varje funktion visas en beskrivning av dess effekt. Medan du skriver skalas alternativlistan närmre den funktion som du behöver. Välj **RELATED**, och tryck sedan på **Retur**.

   ![Välj RELATED](media/desktop-tutorial-create-calculated-columns/create4.png)

   En vänsterparentes visas tillsammans med en annan förslagslista med de relaterade kolumner som du kan överföra till funktionen RELATED, tillsammans med beskrivningar och information om förväntade parametrar.

   ![Välj ProductCategory](media/desktop-tutorial-create-calculated-columns/create5.png)

4. Du vill använda kolumnen **ProductCategory** från tabellen **ProductCategory**. Välj **ProductCategory[ProductCategory]** och tryck på **Retur**, skriv sedan en högerparentes.

    > [!TIP]
    > Syntaxfel orsakas oftast av saknade eller felplacerade parentestecken, även om Power BI Desktop ibland lägger till dem åt dig.

5. Du vill använda bindestreck och blanksteg till att avgränsa **ProductCategory**- och **ProductSubcategory**-värden i de nya värdena, så efter högerparentesen i det första uttrycket skriver du ett blanksteg, ett et-tecken ( **&** ), ett dubbelt citattecken ( **"** ), ett blanksteg, ett bindestreck ( **-** ), ett blanksteg till, ett dubbelt citattecken till och ett et-tecken till. Formeln bör nu se ut så här:

    `ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &`

    > [!TIP]
    > Om du behöver mer plats, välj fortsättningstecknet till höger i formelfältet för att expandera formelredigeraren. I redigeraren, tryck på **Alt + Retur** för att gå en rad nedåt och **Tab** för att gå vidare.

6. Ange ännu en inledande hakparentes ( **[** ) och välj kolumnen **[ProductSubcategory]** för att avsluta formeln. 

    ![Välj ProductSubcategory](media/desktop-tutorial-create-calculated-columns/create6.png)

    Du behöver inte använda en annan RELATED-funktion till att anropa tabellen **ProductSubcategory** i det andra uttrycket eftersom du skapar den beräknade kolumnen i den här tabellen. Du kan ange **[ProductSubcategory]** med tabellnamnets prefix (fullständigt) eller utan (inte fullständigt).

7. Slutför formeln genom att trycka på **Retur** eller välja bockmarkeringen i formelfältet. Formeln valideras och kolumnnamnet **ProductFullCategory** visas i tabellen **ProductSubcategory** i fönstret **Fält**.

   ![Slutförd ProductFullCategory-kolumn](media/desktop-tutorial-create-calculated-columns/create7.png)

    >[!NOTE]
    >I Power BI Desktop får beräknade kolumner en särskild ikon i listan **Fält** som visar att de innehåller formler. I Power BI-tjänsten (din Power BI-webbplats) går det inte att ändra formler, så beräknade kolumner har inte ikoner.

## <a name="use-your-new-column-in-a-report"></a>Använda din nya kolumn i en rapport

Nu kan du använda din nya **ProductFullCategory**-kolumn till att titta på **SalesAmount** per **ProductFullCategory**.

1. Välj eller dra kolumnen **ProductFullCategory** från tabellen **ProductSubcategory** till rapportarbetsytan och skapa en tabell som visar alla **ProductFullCategory**-namn.

   ![ProductFullCategory-tabell](media/desktop-tutorial-create-calculated-columns/vis1.png)

2. Välj eller dra fältet **SalesAmount** från tabellen **Sales** till tabellen om du vill visa **SalesAmount** för varje **ProductFullCategory**.

   ![SalesAmount enligt ProductFullCategory-tabellen](media/desktop-tutorial-create-calculated-columns/vis2.png)

## <a name="create-a-calculated-column-that-uses-an-if-function"></a>Skapa en beräknad kolumn som använder en IF-funktion

Contoso-försäljningsexemplet innehåller försäljningsdata för både aktiva och inaktiva butiker. Du vill se till att försäljningen i aktiva butiker tydligt avgränsas från försäljningen i inaktiva butiker i rapporten genom att skapa fältet **Active StoreName**. I den nya beräknade kolumnen **Active StoreName** visas alla aktiva butiker med butikens fullständiga namn, medan försäljningen för inaktiva butiker grupperas under posten **Inactive** (inaktiv).

Lyckligtvis har tabellen **Stores** en kolumn med namnet **Status**, med värdet ”On” för aktiva butiker och ”Off” för inaktiva butiker, som vi använder till att skapa värden för vår nya **Active StoreName**-kolumn. DAX-formeln använder den logiska funktionen [IF](https://msdn.microsoft.com/library/ee634824.aspx) till att testa varje butiks **status** och returnerar ett visst värde beroende på resultatet. Om butikens **status** är ”On” returnerar formeln butikens namn. Om den är ”Off” tilldelar formeln ett **Active StoreName** med värdet ”Inactive”.

1. Skapa en ny beräknad kolumn i tabellen **Stores** och ge den namnet **Active StoreName** i formelfältet.

2. Efter **=** -tecknet, börja skriva **IF**. Förslagslistan visar vad du kan lägga till. Välj **IF**.

    ![Välj IF](media/desktop-tutorial-create-calculated-columns/if1.png)

3. Det första argumentet för **IF** är ett logiskt test av om butikens **status** är ”On”. Skriv en inledande hakparentes **[** , som visar kolumner från tabellen **Stores** och välj **[Status]** .

    ![Välj Status](media/desktop-tutorial-create-calculated-columns/if2.png)

4. Direkt efter **[Status]** , skriv **= ”On”** , och skriv ett komma ( **,** ) för att avsluta argumentet. Knappbeskrivningen föreslår att du nu behöver lägga till ett värde som returneras när resultatet är TRUE.

    ![Lägg till värdet TRUE](media/desktop-tutorial-create-calculated-columns/if3.png)

5. Om butikens status är ”On” vill du visa butikens namn. Skriv en inledande hakparentes **[** och välj sedan kolumnen **[StoreName]** och skriv ett kommatecken till. Knappbeskrivningen anger att du nu behöver lägga till ett värde som returneras när resultatet är FALSE.

    ![Lägg till FALSE-värde](media/desktop-tutorial-create-calculated-columns/if4.png)

6. Du vill att värdet ska vara ”Inactive”, så skriv **”Inactive”** och slutför sedan formeln genom att trycka på **Retur** eller välja kryssmarkeringen i formelfältet. Formeln valideras och den nya kolumnens namn visas i tabellen **Stores** i fönstret **Fält**.

    ![Active StoreName-kolumn](media/desktop-tutorial-create-calculated-columns/if5.png)

7. Nu kan du använda din nya **Active StoreName**-kolumn i visualiseringar precis som andra fält. Om du vill visa **SalesAmounts** efter **Active StoreName** väljer du fältet **Active StoreName** eller drar det till rapportarbetsytan och väljer sedan fältet **SalesAmount** eller drar det till tabellen. I den här tabellen visas aktiva butiker individuellt efter namn, men inaktiva butiker grupperas samman i slutet som **Inactive**.

    ![SalesAmount efter Active StoreName-tabell](media/desktop-tutorial-create-calculated-columns/if6.png)

## <a name="what-youve-learned"></a>Vad du har lärt dig

Beräknade kolumner kan utöka dina data och ge enklare analyser. Du har lärt dig hur du skapar beräknade kolumner i fönstret **Fält** och med formelfältet, använder förslagslistor och knappbeskrivningar för att konstruera formler, anropar DAX-funktioner som RELATED och IF med rätt argument och använder de beräknade kolumnerna i rapportvisualiseringar.

## <a name="next-steps"></a>Nästa steg

Om du vill ha en grundligare genomgång av DAX-formler och skapa beräknade kolumner med mer avancerade formler, kan du läsa mer i [DAX-grunder i Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Den här artikeln handlar om grundläggande begrepp i DAX, till exempel syntax, funktioner och en mer omfattande beskrivning av kontext.

Det kan vara bra att lägga till [Referens för dataanalysuttryck (DAX)](https://msdn.microsoft.com/library/gg413422.aspx) i dina Favoriter. Där hittar du detaljerad information om DAX-syntax, operatorer och fler än 200 DAX-funktioner.
