---
title: "Självstudie: Skapa beräknade kolumner i Power BI Desktop"
description: "Självstudie: Skapa beräknade kolumner i Power BI Desktop"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 7e959054300dafcab5f38bfce121fe0ac91dca06
ms.sourcegitcommit: f2b38777ca74c28f81b25e2f739e4835a0ffa75d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2017
---
# <a name="tutorial-create-calculated-columns-in-power-bi-desktop"></a>Självstudie: Skapa beräknade kolumner i Power BI Desktop
Ibland innehåller de data som du analyserar inte det fält som du behöver för att kunna hämta ett visst resultat. Det är därför vi använder beräknade kolumner. Beräknade kolumner använder DAX-formler till att definiera värden för en kolumn. Dessa värden kan bestå av nästan vad som helst, oavsett om det gäller att sammanfoga textvärden från ett antal olika kolumner i modellen, eller att beräkna ett numeriskt värde från andra värden. Anta till exempel att dina data har kolumnerna Stad och Stat (som fält i fältlistan), men du vill ha det enda fältet Plats med båda som ett enda värde, exempelvis Miami, FL. Detta är exakt vad beräknade kolumner är till för.

Beräknade kolumner liknar mått i och med att båda är baserade på en DAX-formel, men de skiljer sig åt i hur de används. Mått används oftast i området Värden i en visualisering för att beräkna resultat som baseras på andra fält som finns på en rad i en tabell, en axel, en förklaring eller ett gruppområde i en visualisering. Beräknade kolumner används å andra sidan när du vill ha kolumnens resultat på den raden i tabellen eller i området Axeln, Förklaring eller Grupp.

I den här självstudien får du hjälp att förstå och skapa vissa av dina egna beräknade kolumner i Power BI Desktop. Den är avsedd för Power BI-användare som redan är bekanta med Power BI Desktop och som vill skapa mer avancerade modeller. Du bör redan känna till hur man använder frågor för att importera data, att arbeta med flera relaterade tabeller och att lägga till fält på rapportarbetsytan. Om du är nybörjare i Power BI Desktop bör du läsa [Komma igång med Power BI Desktop](desktop-getting-started.md).

Om du vill slutföra stegen i den här självstudien måste du ladda ned filen [Contoso Sales Sample för Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip). Det här är samma exempelfil som användes i självstudien [Skapa dina egna mått i Power BI Desktop](desktop-tutorial-create-measures.md). Den innehåller redan försäljningsdata från det fiktiva företaget Contoso, Inc. Eftersom data i filen har importerats från en databas, kan du inte ansluta till datakällan eller visa den i frågeredigeraren. När du har filen på din dator kan du gå vidare och öppna den i Power BI Desktop.

## <a name="lets-create-a-calculated-column"></a>Nu ska vi skapa en beräknad kolumn
Anta att vi vill visa produktkategorier tillsammans med produktens underkategorier i ett enskilt värde på raderna, som t.ex. Mobiltelefoner – tillbehör, Mobiltelefoner – smartphones och surfplattor etc. Om vi tittar på våra produkttabeller i fältlistan i rapportvyn eller datavyn (vi använder rapportvyn här), finns det inget fält som visar vad vi vill. Vi har dock fälten ProductCategory och ProductSubcategory i varsin tabell.

 ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_nonewcol.png)

Vi ska skapa en ny beräknad kolumn för att kombinera värdena från dessa två kolumner till nya värden i vår nya kolumn. Vi måste därför kombinera data från två olika tabeller i en enda kolumn. Eftersom vi ska använda DAX till att skapa vår nya kolumn kan vi utnyttja alla fördelar med den modell som vi redan har, inklusive relationerna mellan olika tabeller som redan finns.

### <a name="to-create-a-productfullcategory-column"></a>Så här skapar du en ProductFullCategory-kolumn
1.  Högerklicka eller klicka på nedåtpilen i tabellen **ProductSubcategory** i fältlistan och klicka sedan på **Ny kolumn**. Den nya kolumnen läggs till i tabellen ProductSubcategory.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumn.png)
    
    Formelfältet visas överst i rapportarbetsytan eller datarutnätet. Det är där vi kan byta namn på vår kolumn och ange en DAX-formel.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_newcolumnformula.png)
    
    Som standard får en ny beräknad kolumn helt enkelt namnet Kolumn. Om vi inte byter namn på den och skapar en till kolumn, kommer den kolumnen få namnet Kolumn 2, Kolumn 3 osv. Vi vill att våra kolumner ska vara mer identifierbara, så vi ger den nya kolumnen ett nytt namn.
    
2.  Eftersom namnet **Kolumn** redan är markerat i formelfältet, skriver du helt enkelt **ProductFullCategory**.
    
    Nu kan vi börja ange vår formel. Vi vill att värdena i vår nya kolumn ska starta med namnet ProductCategory från tabellen ProductCategory. Eftersom den här kolumnen finns i annan (men relaterad) tabell, ska vi använda funktionen [RELATED](https://msdn.microsoft.com/library/ee634202.aspx) för att hämta den.
    
3.  Efter likhetstecknet skriver du **R**. En listruta visas med förslag på alla DAX-funktioner som börjar med bokstaven R. Ju mer vi skriver, desto närmare kommer vi funktionen vi behöver. Bredvid funktionen visas en beskrivning. Välj **RELATED** genom att bläddra nedåt och tryck sedan på Retur.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_1.png)
    
    En vänsterparentes visas tillsammans med en annan förslagslista med alla tillgängliga kolumner som vi kan skicka till funktionen RELATED. En beskrivning och information om vilka parametrar som förväntas visas också.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_2.png)
    
    Ett uttryck visas alltid mellan en vänster- och högerparentes. I det här fallet kommer vårt uttryck innehålla ett enda argument som skickas till funktionen RELATED, en relaterad kolumn som värden returneras från. Listan med kolumner minskas automatiskt till att endast visa de kolumner som är relaterade. I det här fallet vill vi ha kolumnen ProductCategory i tabellen ProductCategory.
    
    Välj **ProductCategory[ProductCategory]** och skriv sedan en högerparentes.
    
    > [!TIP]
    > Syntaxfel orsakas oftast av att en avslutande parentes saknas eller är felplacerad. Ofta lägger dock Power BI Desktop till den om du glömmer bort det.
    > 
    > 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_3.png)
    
4. Vi ska lägga till ett bindestreck som avgränsar varje värde, så efter högerparentesen i det första uttrycket skriver du blanksteg, et-tecken (&), citattecken, blanksteg, bindestreck (-), blanksteg, ett avslutande citattecken och sedan ett et-tecken till. Formeln bör nu se ut så här:
    
    **ProductFullCategory = RELATED(ProductCategory[ProductCategory]) & " - " &**
    
    > [!TIP]
    > Klicka på fortsättningstecknet till höger i formelfältet för att expandera formelredigeraren. Klicka på Alt och Retur för att gå en rad nedåt och Tabb för att gå vidare.
    > 
    > 
    
5.  Ange ännu en inledande hakparentes och välj kolumnen **[ProductSubcategory]** för att avsluta formeln. Formeln bör nu se ut så här:
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_5.png)
    
    Du kanske märkte att vi inte använde funktionen RELATED i det andra uttrycket när vi anropade kolumnen ProductSubcategory. Detta beror på att den här kolumnen redan finns i samma tabell som vi skapar vår nya kolumn i. Vi kan ange [ProductCategory] med tabellnamnet (fullständigt) eller utan (inte fullständigt).
    
6.  Slutför formeln genom att trycka på Retur eller klicka på bockmarkeringen i formelfältet. Formeln verifieras och läggs till i fältlistan i tabellen **ProductSubcategory**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_pfc_6.png)
    
    Du märker kanske att beräknade kolumner får en särskild ikon i fältlistan. Detta visar att de innehåller en formel. De ser bara ut så här i Power BI Desktop. I Power BI-tjänsten (din Power BI-webbplats) går det inte att ändra någon formel, så beräknade kolumnfält har inte någon ikon.
    
## <a name="lets-add-our-new-column-to-a-report"></a>Nu lägger vi till vår nya kolumn i en rapport
Nu kan vi lägga till vår nya ProductFullCategory-kolumn på rapportarbetsytan. Låt oss titta på SalesAmount i ProductFullCategory.

Dra kolumnen **ProductFullCategory** från tabellen **ProductSubcategory** till rapportarbetsytan och dra sedan fältet **SalesAmount** från tabellen **Sales** till diagrammet.

![](media/desktop-tutorial-create-calculated-columns/calccol_fileds_report_1.png)

## <a name="lets-create-another"></a>Nu ska vi skapa en till
Nu när du vet hur du skapar en beräknad kolumn kan vi skapa en till.

Contoso Sales Sample för Power BI Desktop-modellen innehåller försäljningsdata för både aktiva och inaktiva butiker. Vi ska göra detta tydligt genom de data som visas för inaktiva butiker ska kunna identifieras som sådana. Vi vill därför ha ett fält med namnet Active StoreName. För att göra detta skapar vi en kolumn till. När en butik är inaktiv vill vi att vår nya Active StoreName-kolumn (som ett fält) ska visa butikens namn som ”Ej aktiv”, men visa butikens verkliga namn när det är en aktiv butik.

Lyckligtvis har vår butikstabell en kolumn med namnet Status, med värdet På för aktiva butiker och Av för inaktiva butiker. Vi kan testa värden för varje rad i kolumnen Status för att skapa nya värden i vår nya kolumn.

### <a name="to-create-an-active-storename-column"></a>Så här skapar du kolumnen Active StoreName
1.  Skapa en ny beräknad kolumn med namnet **Active StoreName** i tabellen **Stores**.
    
    I den här kolumnen kommer vår DAX-formel att kontrollera varje butiks status. Om butikens status är På returnerar vår formel dess namn. Om den inte är aktiv får den namnet ”Ej aktiv”. För att göra detta använder vi den logiska funktionen [IF](https://msdn.microsoft.com/library/ee634824.aspx) som testar butikens status och returnerar ett visst värde om resultatet är sant eller falskt.
    
2.  Börja med att skriva **IF**. Förslagslistan visar vad vi kan lägga till. Välj **IF**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_1.png)
    
    Det första argumentet för IF är ett logiskt test. Vi vill testa om en butik har statusvärdet ”På” eller inte.
    
3.  Skriv en inledande hakparentes **[** för att vi ska kunna välja kolumner från tabellen Stores. Välj **[Status]**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_2.png)
    
4.  Direkt efter **[Status]**, skriver du **="På"** och sedan ett kommatecken (**,**) för att ange det andra argumentet. Knappbeskrivningen föreslår att vi lägger till värdet för när resultatet är sant.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_3.png)
    
5.  Om butiken är På vill vi visa dess namn. Skriv en inledande hakparentes **[** och välj sedan kolumnen **[StoreName]**. Skriv ett kommatecken till så att vi kan ange vårt tredje argument.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step5.png)
    
6.  Vi måste lägga till ett värde för när resultatet har värdet falskt. I det här fallet vill vi att värdet ska vara **”Ej aktiv”**.
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_step6.png)
    
7.  Slutför formeln genom att trycka på Retur eller klicka på bockmarkeringen i formelfältet. Formeln verifieras och läggs till i fältlistan i tabellen Stores.
    
    Precis som i andra fält kan vi använda vår nya kolumn Active StoreName i visualiseringar. I det här diagrammet visas butiker med statusen På individuellt efter namn, men med statusen Av grupperas de och visas som inaktiva. 
    
    ![](media/desktop-tutorial-create-calculated-columns/calccol_activestore_viz.png)
    
## <a name="what-weve-learned"></a>Vad har vi lärt oss?
Beräknade kolumner kan utöka våra data, vilket ger enklare analyser. Vi har lärt dig hur du skapar beräknade kolumner med hjälp av formelfältet, hur du använder förslagslistan och hur du bäst namnger nya kolumner.

## <a name="next-steps"></a>Nästa steg
Om du vill ha en grundligare genomgång av DAX-formler och skapa beräknade kolumner med mer avancerade DAX formler, kan du läsa mer i [DAX-grunder i Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Den här artikeln handlar om grundläggande begrepp i DAX, till exempel syntax, funktioner och en mer omfattande beskrivning av kontext.

Det kan vara bra att lägga till [Referens för dataanalysuttryck (DAX)](https://msdn.microsoft.com/library/gg413422.aspx) i dina Favoriter. Det är där du hittar detaljerad information om DAX-syntax, operatorer och drygt 200 DAX-funktioner.

