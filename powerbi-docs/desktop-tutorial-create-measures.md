---
title: "Självstudier: Skapa dina egna mått i Power BI Desktop"
description: "Självstudier: Skapa dina egna mått i Power BI Desktop"
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
LocalizationGroup: Learn more
ms.openlocfilehash: 96295ced577ddb18b8c56031278bf9a81cddf981
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="tutorial-create-your-own-measures-in-power-bi-desktop"></a>Självstudier: Skapa dina egna mått i Power BI Desktop
Några av de mest kraftfulla lösningarna för analys i Power BI Desktop kan skapas med hjälp av åtgärder. Mått hjälper oss genom att utföra beräkningar på våra data medan vi interagerar med vår rapporter. I den här självstudien får du hjälp att förstå och skapa vissa av dina egna grundmått i Power BI Desktop.

Den här artikeln är avsedd för Power BI-användare som redan är bekanta med Power BI Desktop och som vill skapa mer avancerade modeller. Du bör redan känna till hur man använder Hämta data och Frågeredigeraren för att importera data, att arbeta med flera relaterade tabeller och att lägga till fält på rapportarbetsytan. Om du är nybörjare i Power BI Desktop bör du läsa [Komma igång med Power BI Desktop](desktop-getting-started.md).

Om du vill slutföra stegen i den här självstudien måste du ladda ned filen [Contoso Sales Sample för Power BI Desktop](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20Sample%20for%20Power%20BI%20Desktop.zip). Den innehåller redan online-försäljningsdata från det fiktiva företaget Contoso, Inc. Eftersom data i filen har importerats från en databas, kan du inte ansluta till datakällan eller visa den i frågeredigeraren. När du har filen på din dator kan du gå vidare och öppna den i Power BI Desktop.

## <a name="what-are-these-measures-all-about"></a>Vad handlar dessa mått om?
Måtten skapas oftast för oss automatiskt, t.ex. när vi markerar kryssrutan vid fältet **SalesAmount** i tabellen **Sales** i fältlistan, eller drar **SalesAmount** till rapportarbetsytan.

![](media/desktop-tutorial-create-measures/measurestut_salesamountinfieldlist.png)

En ny diagramvisualisering visas, och ser ut så här:

![](media/desktop-tutorial-create-measures/meastut_salesamountchart.png)

Vad vi får är ett stapeldiagram som visar försäljningsvärdenas totalsumma från fältet SalesAmount.  Vårt SalesAmount-fält är egentligen bara en kolumn med namnet SalesAmount i tabellen Sales som vi redan har importerat.

Kolumnen SalesAmount innehåller över två miljoner rader med försäljningsvärden. Du kanske undrar varför du inte ser någon tabell med rader fyllda med dessa värden. Power BI Desktop vet att alla värden i SalesAmount är av en numerisk datatyp, och du vill förmodligen sammanställa dem på något sätt, genom att lägga ihop dem, räkna ut medelvärdet, räkna dem osv.

När du ser ett fält i fältlistan med en sigma-ikon, ![](media/desktop-tutorial-create-measures/meastut_sigma.png), så innebär det att fältet är numeriskt, och att dess värden kan aggregeras. När vi, i det här fallet, väljer SalesAmount så skapar Power BI Desktop egna mått och summan av alla försäljningsbelopp beräknas och visas i diagrammet.

Summa är standardaggregeringen när vi väljer ett fält med en numerisk datatyp, men vi kan enkelt ändra till en annan aggregeringstyp.

Om du klickar på nedåtpilen bredvid **SalesAmount** i området **Värde** kan du sedan välja **Medelvärde**.

![](media/desktop-tutorial-create-measures/meastut_salesamountaverage.png)

Vår visualiseringen ändras till ett medelvärde för alla försäljningsvärden i fältet SalesAmount.

![](media/desktop-tutorial-create-measures/meastut_salesamountaveragechart.png)

Vi kan ändra aggregeringstypen beroende på vilket resultat vi vill ha, men alla aggregeringstyper kan inte tillämpas på vilken numerisk datatyp som helst. För vårt SalesAmount-fält så är t.ex. Sum och Average helt meningslösa. Minimum och Maximum har också sin plats. Men Count passar verkligen inte ihop med vårt SalesAmount-fält eftersom värdena, även om de är numeriska, i själva verket är valutavärden.

Att förstå sig på aggregeringar är av avgörande betydelse om man vill förstå mått, eftersom varje mått utför någon typ av aggregering. Vi ska se fler exempel på hur man använder Sum-aggregering lite senare, när det är dags för dig att skapa några egna mått.

Värden som beräknats från mått ändras alltid som svar på våra interaktioner med rapporten. Om vi t.ex. drar fältet **RegionCountryName** från tabellen **Geography** till vårt diagram så beräknas och visas medelvärdet för varje lands försäljningssiffror.

![](media/desktop-tutorial-create-measures/meastut_salesamountavchartbyrcn.png)

När resultatet av måttet ändras på grund av en interaktion med vår rapport, så påverkar vi måttets *kontext*. Varje gång du interagerar med rapporten ändrar du faktiskt den kontext i vilken ett mått beräknar och visar sina resultat.

I de flesta fall gör Power BI vad som ska göras och returnerar värden enligt de fält som vi har lagt till och de aggregeringstyper vi väljer. Men i andra fall kan du behöva skapa dina egna mått om du vill utföra mer komplexa och unika beräkningar.

Med Power BI Desktop skapar du egna åtgärder med dataanalysuttryck (DAX). DAX-formler påminner mycket om Excel-formler. I själva verket använder DAX ofta samma funktioner, operatorer och syntax som används i Excel-formler. Dock är DAX-funktionerna utformade för att fungera med relationella data och utföra mer dynamiskt beräkningar när vi interagerar med våra rapporter.

Det finns över 200 DAX-funktioner som gör allt från enkla aggregeringar som Sum och Average till mer avancerade funktioner för statistik och filtrering. Vi ska inte gå in på DAX-språket i detalj här, men det finns många resurser med vilkas hjälp du kan lära dig mer. När du har gått igenom den här kursen bör du läsa [DAX-grunder i Power BI Desktop](desktop-quickstart-learn-dax-basics.md).

När vi skapar våra egna åtgärder läggs de till i fältlistan för den tabell vi önskar. Detta kallas ett *modellmått* och det finns kvar i vår tabell som ett fält. Vissa av de stora fördelarna med modellmått är att vi kan kalla dem vad vi vill och därmed göra dem mer identifierbara. Vi kan också använda dem som argument i andra DAX-uttryck, och vi kan skapa mått som utför komplexa beräkningar mycket snabbt.

## <a name="lets-create-our-own-measure"></a>Nu ska vi skapa ett eget mått
Anta att vi vill analysera nettoförsäljningen. Om vi tittar på vår försäljningstabell i fältlistan ser vi att det inte finns något fält med namnet NetSales. Men vi har byggblocken för att skapa egna mått med vilka vi kan beräkna nettoförsäljningen.

Vi behöver ett mått för att subtrahera rabatter och returer från försäljningsbeloppen. Eftersom vi vill att vårt mått ska beräkna ett resultat oavsett kontexten i vår visualisering, så behöver vi i praktiken subtrahera summan av DiscountAmount och ReturnAmount från SalesAmount-summan. Det kan verka lite förvirrande just nu, men oroa dig inte – allt kommer att klarna om en liten stund.

### <a name="net-sales"></a>Nettoförsäljning
1.  Högerklicka eller klicka på nedåtpilen i tabellen **Sales** i fältlistan och klicka sedan på **Nytt mått**. Detta garanterar att vårt nya mått har sparats i försäljningstabellen, där det är lättare att hitta.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure.png)
    
    > [!TIP]
    > Du kan också skapa ett nytt mått genom att klicka på knappen Nytt mått i menyfliksområdet på fliken Start i Power BI Desktop.
    > 
    > ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasureribbon.png)
    > 
    > När du skapar ett mått från menyfliksområdet kan måttet skapas i vilken tabell som helst. Även om ett mått inte behöver tillhöra en viss tabell, så är det lättare att hitta det om du skapar det i den tabell som är det mest logiska alternativet för dig. Om du vill att det ska finna i en viss tabell, så aktivera först tabellen genom att klicka på den. Klicka sedan på Nytt mått. I vårt fall ska vi skapa vårt första mått i försäljningstabellen.
    > 
    > 
    
    Formelfältet visas överst på rapportarbetsytan. Det är där vi kan byta namn på vårt mått och ange en DAX-formel.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formulabar.png)
    
    Låt oss först ge det nya måttet ett namn. Som standard heter ett nytt mått helt enkelt Mått. Om vi inte byter namn på den och skapar en till kolumn, kommer den kolumnen få namnet Mått 2, Mått 3 osv. Vi vill att våra mått ska vara mer identifierbara, så låt oss ge det nya måttet namnet Nettoförsäljning.
    
2. Markera **Mått** i formelfältet och skriv sedan **Nettoförsäljning**.
    
    Nu kan vi börja ange vår formel.
    
3.  Efter likhetstecknet skriver du **S**. En listruta visas med förslag på alla DAX-funktioner som börjar med bokstaven S. Ju mer vi skriver, desto närmare kommer vi funktionen vi behöver. Välj **SUM** genom att bläddra nedåt och tryck sedan på Retur.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_s.png)
    
    När du har tryckt på Retur visas tillsammans med en annan förslagslista med alla tillgängliga kolumner som vi kan skicka till funktionen SUM.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_sum.png)
    
    Ett uttryck visas alltid mellan en vänster- och högerparentes. I det här fallet ska vårt uttryck innehålla ett argument som ska skickas till funktionen SUM – en kolumn som ska summeras. Vi kan begränsa listan över kolumner genom att skriva de första bokstäverna i det namn vi söker. I det här fallet söker vi efter kolumnen SalesAmount, så när vi börja skriva ”salesam” blir listan mindre, och vi ser två objekt som vi kan välja. Det är egentligen samma kolumn. En visar bara [SalesAmount] eftersom vi skapar vårt mått i samma tabell som kolumnen SalesAmount finns i. Det andra visar det tabellnamn som föregår kolumnnamnet.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_salesam.png)
    
    I allmänhet är det god praxis att ange en kolumns fullständiga kvalificerade namn. Det gör formlerna lättare att läsa.
    
4. Välj **Sales[SalesAmount]** och skriv sedan en avslutande parentes.
    
    > [!TIP]
    > Syntaxfel orsakas oftast av att en avslutande parentes saknas eller är felplacerad.
    > 
    > 
    
    Nu ska vi subtrahera våra två övriga kolumner.
    
5.  Efter det första uttryckets avslutande parentes skriver du ett blanksteg och därefter en minusoperator (**-**) följt av ytterligare ett blanksteg. Ange sedan ytterligare en SUM-funktion med kolumnen **Sales[DiscountAmount]** som argument.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_discamount.png)
    
    Vi börjar till slut på utrymme för vår formel. Inga problem.
    
6.  Klicka på fortsättningstecknet till höger i formelfältet.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_chevron.png)
    
    Nu har vi mer utrymme. Vi kan ange nya delar i vår formel på en ny rad genom att trycka på Alt+Retur. Vi kan också flytta över saker med tabbtangenten.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_formula_expanded.png)
    
    Nu kan vi lägga till formelns sista del.
    
7.  Lägga till en annan minusoperator följd av ytterligare en SUM-funktion med kolumnen **Sales [ReturnAmount]** som argument.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_newmeasure_complete.png)
    
    Nu ser formeln ut att vara klar.

8.  Slutför genom att trycka på RETUR eller klicka på bockmarkeringen i formelfältet. Formeln verifieras och läggs till i fältlistan i tabellen Sales.

### <a name="lets-add-our-new-measure-to-a-report"></a>Nu lägger vi till vårt nya mått i en rapport
Nu kan vi lägga till vårt nettoförsäljningsmått på rapportarbetsytan, och nettoförsäljningen kan beräknas för vilket annat fält som helst som vi lägger till i rapporten. Låt oss titta på nettoförsäljning per land.

1.  Dra måttet **Net Sales** från tabellen **Sales** till rapportarbetsytan.
    
2. Dra fältet **RegionCountryName** från tabellen **Geography** till diagrammet.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_byrcn.png)
    
    Låt oss lägga till lite mer data.
    
3.  Dra fältet **SalesAmount** till diagrammet, så att du kan se skillnaden mellan nettoförsäljning och försäljningsbelopp.
    
    Nu har vi verkligen två mått i diagrammet. SalesAmount, som summerades automatiskt, och Net Sales, som vi skapade själva. I båda fallen beräknades resultaten i kontexten för ett annat fält i diagrammet har vi i diagrammet – länderna i RegionCountryName.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_byrcnandsalesamount.png)
    
    Låt oss lägga till ett utsnitt, så vi kan bryta ned nettoförsäljningen och försäljningsbeloppen ytterligare efter kalenderår.
    
4.  Klicka först på ett tomt område bredvid diagrammet och klicka sedan på tabellvisualiseringen i **Visualiseringar**.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktablevisbutton.png)
    
    Detta skapar en tom tabellvisualisering på rapportarbetsytan.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_blanktable.png)
    
5.  Dra fältet **Year** från tabellen **Calendar** till en ny tom tabell.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_yearaggtable.png)
    
    Eftersom Year är ett numeriskt fält, så summerade Power BI Desktop dess värden och gav oss ett diagram. Men det fungerar inget vidare för oss som ett utsnitt.
    
6. Klicka på nedåtpilen intill **Year** i **Values** och klicka sedan på **Summera inte**.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_year_donotsummarize.png)
    
    Ny kan vi ändra fältet Year i tabellvisualiseringen till ett utsnitt.

    7.  Klicka på visualiseringen **Utsnitt** i **Visualiseringar**.

    ![](media/desktop-tutorial-create-measures/meastut_netsales_year_changetoslicer.png)
    
    Nu har vi Year som ett utsnitt. Vi kan välja vilket enskilt år eller vilken grupp av år vi vill, och rapportens visualiseringar utformas därefter.
    
8. Gå vidare och klicka på **2013**. Du ser att diagrammet har ändrats. Våra Net Sales- och SalesAmount-mått beräknas igen, och visar nya resultat för 2013. Här har vi återigen ändrat den kontext i vilken våra mått beräknar och visar resultat.
    
    ![](media/desktop-tutorial-create-measures/meastut_netsales_chartslicedbyyear.png)

## <a name="lets-create-another-measure"></a>Låt oss skapa ett nytt mått
Nu när du vet hur du skapar ett eget mått så låt oss skapa ett till.

### <a name="net-sales-per-unit"></a>Nettoförsäljning per enhet
Hur gör vi om vi vill ta reda på vilka produkter med störst försäljning per enhet?

Vi kan skapa ett nytt mått. I det här fallet vill vi dividera nettoförsäljningen med antalet sålda enheter. Vi vill med andra ord dela resultatet för måttet Net Sales med summan för Sales[SalesQuantity].

1.  Skapa ett nytt mått med namnet **Net Sales per Unit** i Sales- eller Products-tabellen.
    
    I det här måttet kommer vi att använda måttet Net Sales som vi skapade tidigare. Med DAX kan vi refererar till andra mått i vår formel.
    
2.  Börja skriva **Net Sales**. Förslagslistan visar vad vi kan lägga till. Välj **[Net Sales]**.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2a.png)
    
    Du kan också referera till ett annat mått genom att helt enkelt skriva en inledande hakparentes (**[**). Listan över förslag visar bara de mått som vi kan lägga till i vår formel.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_formulastep2b.png)
    
3.  Ange ett blanksteg direkt efter **[Net Sales]**, följt av en divisionsoperator (**/**), ange en SUM-funktion och skriv sedan **Quantity**. Listan över förslag visar alla kolumner med Quantity i namnet. Välj **Sales [SalesQuantity]**. Formeln bör nu se ut så här:
    
    > **Nettoförsäljning per enhet = [Net försäljning] / SUM(Sales[SalesQuantity])**
    > 
    > 
    
    Rätt läckert, eller hur? Att ange DAX formler är egentligen ganska enkelt när vi använder DAX-redigerarens sök- och förslagsfunktioner. Låt oss nu se vad vi får fram med vårt nya Net Sales per Unit-mått.
    
4. Dra måttet **Net Sales per Unit** till ett tomt område på rapportarbetsytan.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_chart.png)
    
    Inte särskilt intressant, eller hur? Oroa dig inte.
    
5.  Ändra diagramvisualiseringens typ till **Trädkarta**.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_changetotreemap.png)
    
6. Dra fältet **ProductCategory** från tabellen **ProductCategory** ned till området **Group**.
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_byproductcat.png)
    
    Det här är bra information, men vad gör vi om vi vill titta på nettoförsäljningen per produkt?
    
7. Ta bort fältet **ProductCategory** och dra sedan fältet **ProductName** från tabellen **Product** ned till området **Group** istället. 
    
    ![](media/desktop-tutorial-create-measures/meastut_nspu_byproductname.png)
    
    Ok, nu leker vi lite, men medge att det är lite häftigt! Naturligtvis vi kan filtrera den här trädkartan på många olika sätt, men det ligger utanför den här självstudiekursens syfte.

## <a name="what-weve-learned"></a>Vad vi har lärt oss
Att mått är ett mycket kraftfullt hjälpmedel när vi vill hämta insikter från våra data. Vi har lärt oss hur man skapar mått med hjälp av formelfältet. Vi kan namnge måtten så att de är begripliga, och med hjälp av förslagslistorna kan vi lättare hitta och välja rätt element till våra formler. Vi har också insett betydelsen av den kontext i vilken resultaten av måttberäkningarna kan ändras beroende på andra fält eller uttryck i din måttformel.

## <a name="next-steps"></a>Nästa steg
Om du vill ha en grundligare genomgång av DAX-formler och skapa mer avancerade mått, kan du läsa mer i [DAX-grunder i Power BI Desktop](desktop-quickstart-learn-dax-basics.md). Den här artikeln handlar om grundläggande begrepp i DAX, till exempel syntax, funktioner och en mer omfattande beskrivning av kontext.

Det kan vara bra att lägga till [Referens för dataanalysuttryck (DAX)](https://msdn.microsoft.com/library/gg413422.aspx) i dina Favoriter. Det är där du hittar detaljerad information om DAX-syntax, operatorer och drygt 200 DAX-funktioner.

