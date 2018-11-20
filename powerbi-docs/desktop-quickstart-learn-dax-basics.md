---
title: DAX-grunder i Power BI Desktop
description: DAX-grunder i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a171dd2aa375f8d12830b051dd8ce6437e4b3236
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679465"
---
# <a name="dax-basics-in-power-bi-desktop"></a>DAX-grunder i Power BI Desktop
Den här artikeln är avsedd för nya användare i Power BI Desktop. Den är tänkt att ge dig en snabb och enkel introduktion för hur du kan använda dataanalysuttryck (DAX) till att lösa flera grundläggande problem med beräkningar och dataanalys. Vi går igenom viss konceptinformation, en serie aktiviteter som du kan utföra och några kunskapsfrågor som testar vad du har lärt dig. När du har läst den här artikeln bör du ha en god förståelse för de viktigaste grundläggande begreppen i DAX.

## <a name="what-is-dax"></a>Vad är DAX?
DAX är en samling med funktioner, operatorer och konstanter som kan användas i en formel eller ett uttryck när man vill beräkna och returnera ett eller flera värden. DAX hjälper dig helt enkelt att skapa ny information från data som redan finns i din modell.

## <a name="why-is-dax-so-important"></a>Varför är DAX så viktigt?
Det är ganska enkelt att skapa en ny Power BI Desktop-fil och importera data till den. Du kan till och med skapa rapporter med värdefulla analyser utan att använda några DAX-formler alls. Men vad gör du om du behöver analysera tillväxten i procent i flera produktkategorier och för olika datumintervall? Eller om du vill beräkna den årliga tillväxten jämfört med trender på marknaden? DAX-formlerna innehåller den här funktionen och många andra viktiga funktioner dessutom. Lär dig att skapa effektiva DAX-formler som hjälper dig få ut så mycket som möjligt av dina data. När du har fått den information du behöver, kan du börja lösa verkliga affärsproblem som påverkar ditt slutresultat. Detta är styrkan i Power BI och DAX hjälper dig dit.

## <a name="prerequisites"></a>Förutsättningar
Du kanske redan vet hur man skapar formler i Microsoft Excel. I så fall blir det lättare att förstå DAX, men även om du inte har några erfarenheter av formler i Excel kommer de koncept som beskrivs här hjälpa dig igång med att skapa DAX-formler och lösa problem direkt.

Vi ska fokusera på att förstå de DAX-formler som används i beräkningar och mer specifikt i mått och beräknade kolumner. Du bör redan vara bekant med Power BI Desktop och att importera data samt lägga till fält i en rapport. Du bör också känna till de grundläggande begreppen [Mått](desktop-measures.md) och [Beräknade kolumner](desktop-calculated-columns.md).

**Arbetsboksexempel**

Det bästa sättet att lära sig DAX är att skapa några grundläggande formler, använda faktiska data och se resultaten själv. De exempel och uppgifter som visas här använder Contoso Sales Sample i den förhandsgranskade Power BI Desktop-filen. Det här är samma exempelfil som används i [självstudien: Skapa dina egna mått i Power BI Desktop](desktop-tutorial-create-measures.md). Här är [exempelfilen](http://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip) för nedladdning.

## <a name="lets-begin"></a>Vi börjar!
Vi kommer att inrikta vår DAX-förståelse runt tre grundläggande begrepp: *Syntax*, *Funktioner* och *Kontext*. Naturligtvis finns det andra viktiga begrepp i DAX, men att förstå dessa tre ger den bästa grunden till att bygga upp DAX-kunskaperna.

### <a name="syntax"></a>Syntax
Innan du skapar egna formler ska vi titta på DAX-formelns syntax. Syntaxen innehåller olika element som utgör en formel, eller rättare sagt hur formeln skrivs. Till exempel ska vi nu titta på en enkel DAX-formel för ett mått.

![](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Den här formeln innehåller följande syntaxelement:

**A.** Måttnamnet **Total Sales**.

**B.** Operatorn likhetstecken (**=**) anger början av formeln. När den beräknas returneras ett resultat.

**C.** DAX-funktionen **SUM** lägger ihop alla tal i kolumnen **Sales[SalesAmount]**. Du lär dig mer om funktioner senare.

**D.** Parenteser **()** omger ett uttryck som innehåller ett eller flera argument. Alla funktioner kräver minst ett argument. Ett argument skickar ett värde till en funktion.

**E.** Den refererade tabellen **Sales**.

**F.** Den refererade kolumnen **[SalesAmount]** i tabellen Sales. Det här argumentet anger för SUM-funktionen vilken kolumn som ska aggregera en summa.

När du försöker förstå en DAX-formel kan det hjälpa att bryta ner varje element till ett språk som du tänker på och talar varje dag. Du kan till exempel läsa den här formeln som:

> *För måttet Total Sales beräknas (=) SUM av värdena i kolumnen [SalesAmount] i tabellen Sales.*
> 
> 

När den läggs till i en rapport beräknas måttet och returnerar värden genom att summera försäljningssiffrorna för de andra fält som vi inkluderar, ex.vis mobiltelefoner i USA.

Du kanske tänker ”Händer inte samma sak som om jag bara lägger till fältet SalesAmount i min rapport?” Egentligen, ja. Men det finns ett bra skäl att skapa ett eget mått som summerar värdena från fältet SalesAmount: Vi kan använda det som ett argument i andra formler. Det kan verka lite förvirrande nu – men allt eftersom dina DAX-formelkunskaper växer, blir dina formler och din modell effektivare. Du kommer faktiskt se att måttet Total Sales dyker upp som ett argument i andra formler vid ett senare tillfälle.

Låt oss gå igenom ett par saker till om den här formeln. Vi har introducerat funktionen [SUM](https://msdn.microsoft.com/library/ee634387.aspx). Funktioner är färdiga formler som gör det lättare att utföra komplexa beräkningar och ändringar i tal, datum, tid, text och mycket mer. Du lär dig mer om funktioner senare.

Du kan också se att kolumnen [SalesAmount] föregicks av tabellen Sales som kolumnen tillhör. Detta kallas för ett fullständigt kolumnnamn, eftersom det innehåller kolumnens namn med tabellens namn före. I kolumner som refereras i samma tabell måste inte namnet på tabellen tas med i formeln. Detta innebär att långa formler som refererar till många kolumner blir kortare och lättare att läsa. Det är dock en bra idé att inkludera tabellnamnet i måttformlerna, även när de är i samma tabell.

> [!NOTE]
> Om ett tabellnamn innehåller blanksteg, reserverade nyckelord eller otillåtna tecken, måste du skriva tabellnamnet inom enkla citattecken. Du måste också ange tabellnamnet inom citattecken om namnet innehåller tecken utanför intervallet med alfanumeriska ANSI-tecken, oavsett om teckenuppsättningen har stöd i dina nationella inställningar eller ej.
> 
> 

Det är viktigt formlerna har rätt syntax. Om syntaxen inte är korrekt returneras i de flesta fall ett syntaxfel. I annat fall kanske syntaxen är korrekt, men värdena som returneras kanske inte är vad du förväntade dig. DAX-redigeraren i Power BI Desktop innehåller en funktion för förslag, som används för att skapa syntaktiskt korrekta formler genom att hjälpa dig välja rätt element.

Nu ska vi skapa en enkel formel. Den här uppgiften hjälper dig att bättre förstå hur formelsyntaxen och förslagsfunktionen i formelfältet kan hjälpa dig.

### <a name="task-create-a-measure-formula"></a>Uppgift: Skapa en måttformel
För att kunna utföra den här aktiviteten måste du öppna Power BI Desktop-filen Contoso Sales Sample.
    
1. I rapportvyn i fältlistan högerklickar du på tabellen **Sales** och klickar sedan på **Nytt mått**.
    
2. I formelfältet ersätter du **Mått** genom att skriva det nya måttnamnet **Previous Quarter Sales**.
    
3. Efter lika med-tecknet skriver du de första bokstäverna **CAL** och dubbelklickar på den funktion som du vill använda. I den här formeln ska du använda **CALCULATE**-funktionen.

   Du ska använda CALCULATE-funktionen till att filtrera de belopp som vi vill summera med ett argument som vi skickar till funktionen CALCULATE. Det här kallas för kapslade funktioner. CALCULATE-funktionen innehåller minst två argument. Det första är uttrycket som ska utvärderas och det andra är ett filter.
   
4. Efter öppningsparentesen **(** för funktionen **CALCULATE** skriver du **SUM** följt av ytterligare en öppningsparentes **(**. Nu ska vi skicka argument till funktionen SUM.

5. Börja skriva **Sal**, och välj sedan **Sales [SalesAmount]**, följt av en avslutande parentes **)**. Detta är det första uttrycksargumentet för vår CALCULATE-funktion.
    
6. Skriv ett kommatecken (**,**) följt av ett blanksteg för att ange det första filtret och skriv sedan **PREVIOUSQUARTER** . Det här är vårt filter.
    
   Vi använder tidsfunktionen PREVIOUSQUARTER för att filtrera SUM-resultatet från föregående kvartal.
    
7. Efter öppningsparentesen **(** för PREVIOUSQUARTER-funktionen skriver du **Calendar[DateKey]**.
    
   Funktionen PREVIOUSQUARTER har ett argument, en kolumn som innehåller ett sammanhängande datumintervall. I vårt fall är det kolumnen DateKey i tabellen Calendar.
    
8. Se till att båda argumenten skickas till funktionen PREVIOUSQUARTER och att funktionen CALCULATE avslutas med två högerparenteser **))**.
    
   Formeln bör nu se ut så här:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
9. Klicka på bockmarkeringen ![](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) i formelfältet eller tryck på RETUR för att verifiera formeln och lägga till den i modellen.

Du klarade det! Du har nu skapat ett mått med DAX och den var inte helt enkel heller. Den här formeln beräknar den totala försäljningen för föregående kvartal, beroende på vilka filter som används i en rapport. Om vi exempelvis placerar SalesAmount och vårt nya mått Previous Quarter Sales i ett diagram och sedan lägger till Year och QuarterOfYear som utsnitt, får vi ungefär detta:

![](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Du har nu sett flera viktiga delar av DAX-formlerna. Den här formeln innehöll först två funktioner. Observera att tidsinformationsfunktionen [PREVIOUSQUARTER](https://msdn.microsoft.com/library/ee634385.aspx) kapslades som ett argument som skickades till filterfunktionen [CALCULATE](https://msdn.microsoft.com/library/ee634825.aspx). DAX-formler kan innehålla upp till 64 kapslade funktioner. Det är inte troligt att en formel någonsin kommer att innehålla så många kapslade funktioner. Faktum är att en sådan formel skulle vara svår att skapa och felsöka och den skulle förmodligen inte vara särskilt snabb heller.

I den här formeln använde du också filter. Filter begränsar vad som ska beräknas. I det här fallet valde du ett filter som ett argument, vilket egentligen är resultatet av en annan funktion. Du lär dig mer om filter senare.

Slutligen använde du funktionen CALCULATE. Detta är en av de kraftfullaste funktionerna i DAX. När du redigerar modeller och skapar mer komplexa formler, kommer du troligen att använda den här funktionen många gånger. Att diskutera funktionen CALCULATE ligger utanför innehållet för den här artikeln, men allt eftersom dina kunskaper om DAX växer bör du vara särskilt uppmärksam på den.

### <a name="syntax-quickquiz"></a>QuickQuiz – Syntax
1. Vad utför den här knappen i formelfältet?
   
   > ![](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. Vad omger alltid ett kolumnnamn i en DAX-formel?

Svaren finns i slutet av den här artikeln.

### <a name="functions"></a>Funktioner
Funktioner är fördefinierade formler som utför beräkningar med specifika värden, så kallade argument, i en viss ordning eller struktur. Argument kan vara andra funktioner, en annan formel, uttryck, kolumnreferenser, tal, text, logiska värden som TRUE eller FALSE, eller konstanter.

DAX innehåller följande typer av funktioner: [Datum och tid](https://msdn.microsoft.com/library/ee634786.aspx), [Tidsinformation](https://msdn.microsoft.com/library/ee634763.aspx), [Information](https://msdn.microsoft.com/library/ee634552.aspx), [Logisk](https://msdn.microsoft.com/library/ee634365.aspx), [Matematisk](https://msdn.microsoft.com/library/ee634241.aspx), [Statistisk](https://msdn.microsoft.com/library/ee634822.aspx), [Text](https://msdn.microsoft.com/library/ee634938.aspx), [Överordnad/underordnad](https://msdn.microsoft.com/library/mt150102.aspx) och [Övrigt](https://msdn.microsoft.com/library/mt150101.aspx). Om du känner till funktionerna i Excel-formler, kommer du känna igen många av funktionerna i DAX. DAX-funktionerna är emellertid unika på följande sätt:

* En DAX-funktion refererar alltid till en fullständig kolumn eller tabell. Om du endast vill använda specifika värden från en tabell eller kolumn kan du lägga till filter i formeln.
* Om du behöver anpassa radbaserade beräkningar finns det DAX-funktioner där du kan använda det aktuella radvärdet eller ett relaterat värde som en typ av argument, för att utföra beräkningar som varierar beroende på kontext. Du lär dig mer om kontext senare.
* DAX innehåller många funktioner som returnerar en tabell i stället för ett värde. Tabellen visas inte, men den används som indata för andra funktioner. Exempelvis kan du hämta en tabell och sedan räkna distinkta värden i den, eller beräkna dynamiska summor i filtrerade tabeller och kolumner.
* DAX innehåller flera olika tidsfunktioner. Med dessa funktioner kan du definiera eller välja datumintervall, samt utföra dynamiska beräkningar som baseras på dem. Exempelvis kan du jämföra summor över parallella perioder.
* Det finns en mycket populär funktion i Excel som heter LETARAD. DAX-funktioner använder inte en cell eller ett cellområde som en referens som LETARAD gör i Excel. DAX-funktionerna använder en kolumn eller en tabell som referens. Kom ihåg att i Power BI Desktop arbetar du med en relationsdatamodell. I de flesta fall behöver du inte skapa någon formel alls och sökning efter värden i en annan tabell är egentligen ganska enkelt.
  
  Som du ser kan funktionerna i DAX hjälpa dig att skapa mycket kraftfulla formler. Vi bara snuddat vid grunderna i funktionerna. Allt eftersom dina kunskaper om DAX växer, kommer du skapa formler med många olika funktioner. Ett bra ställe för att få mer detaljerad information om varje DAX-funktion finns i [Funktionsreferens för DAX](https://msdn.microsoft.com/query-bi/dax/data-analysis-expressions-dax-reference).

### <a name="functions-quickquiz"></a>QuickQuiz – Funktioner
1. Vad refererar en funktion alltid till?
2. Kan en formel innehålla mer än en funktion?
3. Vilken kategori av funktioner ska du använda för att sammanfoga två textsträngar till en sträng?

Svaren finns i slutet av den här artikeln.

### <a name="context"></a>Kontext
Kontext är ett av de viktigaste DAX-begreppen att förstå. Det finns två typer av kontext i DAX: radkontext och filterkontext. Först ska vi titta på radkontext.

**Radkontext**

Det är enklast att tänka på radkontexten som den aktuella raden. Den används när en formel har en funktion som tillämpar filter för att identifiera en enda rad i en tabell. Funktionen tillämpar en radkontext för varje rad i tabellen som den filtrerar. Den här typen av radkontext gäller oftast mått.

**Filterkontext**

Filterkontext är lite svårare att förstå än radkontext. Du kan enklast tänka på filterkontext som ett eller flera filter som tillämpas i en beräkning som ska ge ett resultat eller ett värde.

Filterkontext finns inte i stället för radkontext, utan den tillämpas utöver radkontexten. För att ytterligare begränsa vilka värden som ska ingå i en beräkning kan du exempelvis tillämpa en filterkontext som inte bara anger radkontext, utan även anger ett specifikt värde (filter) i den radkontexten.

Filterkontext är enkel att se i rapporterna. När du lägger till TotalCost i en visualisering och därefter lägger till Year och Region, definierar du till exempel en filterkontext som väljer en delmängd av data baserat på ett visst år och region.

Varför är filterkontext så viktigt i DAX? Det beror på att även om filterkontext tillämpas enklast genom att lägga till fält i en visualisering, kan filterkontext också användas i en DAX-formel genom att definiera ett filter som använder funktioner, till exempel ALL, RELATED, FILTER, CALCULATE efter relationer och andra mått och kolumner. Nu ska vi exempelvis titta på följande formel i ett mått med namnet Store Sales:

![](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

För att bättre förstå den här formeln bryter vi ned den, ungefär som med andra formler.

Den här formeln innehåller följande syntaxelement:

**A.** Måttnamnet **Store Sales**.

**B.** Operatorn likhetstecken (**=**) anger början av formeln.

**C.** Funktionen **CALCULATE** utvärderar ett uttryck som ett argument i en kontext som ändras av de angivna filtren.

**D.** Parenteser **()** omger ett uttryck som innehåller ett eller flera argument.

**E.** Ett mått **[Total Sales]** i samma tabell som ett uttryck. Måttet Total Sales har formeln: =SUM(Sales[SalesAmount]).

**F.** Ett kommatecken (**,**) avgränsar det första uttrycksargumentet från filterargumentet.

**G.** Den fullständiga refererade kolumnen **Kanal[ChannelName]**. Detta är vår radkontext. Varje rad i den här kolumnen anger en kanal: Store, Online etc.

**H.** Det specifika värdet **Store** som ett filter. Detta är vår filterkontext.

Den här formeln säkerställer att endast försäljningsvärden som definieras av måttet Total Sales beräknas för rader i kolumnen Kanal[ChannelName] med värdet ”Store” som ett filter.

Du förstår säkert att genom att kunna definiera filterkontext inom en formel får man stora och kraftfulla möjligheter. Att kunna referera till ett visst värde i en relaterad tabell är bara ett sådant exempel. Oroa dig inte om du inte förstår kontexten direkt. När du skapar egna formler kommer du bättre förstå kontexten och varför den är så viktig i DAX.

### <a name="context-quickquiz"></a>QuickQuiz – Kontext
1. Vilka är de två kontexttyperna?
2. Vad är filterkontext?
3. Vad är radkontext?

Svaren finns i slutet av den här artikeln.

## <a name="summary"></a>Sammanfattning
Nu när du har en grundläggande förståelse för de viktigaste begreppen i DAX, kan du börja skapa DAX-formler för mått på egen hand. DAX kan verkligen vara lite svårt att lära sig, men det finns många hjälpresurser som du kan använda dig av. När du har läst igenom den här artikeln och experimenterat med några av dina egna formler, kan du läsa mer om andra DAX-begrepp och formler som kan hjälpa dig att hitta dina egna lösningar. Det finns många DAX-resurser tillgängliga för dig; den viktigaste är [Referens för dataanalysuttryck (DAX)](https://msdn.microsoft.com/library/gg413422.aspx).

DAX har funnits i flera år i andra Microsoft BI-verktyg, till exempel Power Pivot och Analysis Services-tabellmodeller, så det finns mycket användbar information där. Mer information hittar du i böcker, faktablad och bloggar från både Microsoft och ledande BI-tekniker. [DAX Resource Center Wiki på TechNet](http://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) är också ett bra ställe att börja på.

### <a name="quickquiz-answers"></a>QuickQuiz-svar
Syntax:

1. Verifierar och anger måttet i modellen.
2. Hakparenteser [].

Funktioner:

1. En tabell och en kolumn.
2. Ja. En formel kan innehålla upp till 64 kapslade funktioner.
3. [Textfunktioner](https://msdn.microsoft.com/library/ee634938.aspx).

Kontext:

1. Radkontext och filterkontext.
2. Ett eller flera filter i en beräkning som anger ett enda värde.
3. Den aktuella raden.

