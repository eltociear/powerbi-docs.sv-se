---
title: DAX-grunder i Power BI Desktop
description: DAX-grunder i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 10/21/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 96c80fbbf943ad1d03e9a2172a0711f6fd2e60ad
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239884"
---
# <a name="apply-dax-basics-in-power-bi-desktop"></a>Använda grunderna i DAX i Power BI Desktop
Den här artikeln är avsedd för nya användare i Power BI Desktop. Den är tänkt som en snabb och enkel introduktion till hur du kan använda DAX (Data Analysis Expressions) till att lösa ett antal grundläggande problem med beräkningar och dataanalys. Vi går igenom en del begrepp, några aktiviteter du kan utföra och ställer några kunskapsfrågor där du får testa vad du har lärt dig. När du har läst den här artikeln bör du ha en god förståelse för de viktigaste grundläggande begreppen i DAX.

## <a name="what-is-dax"></a>Vad är DAX?
DAX är en samling med funktioner, operatorer och konstanter som kan användas i en formel eller ett uttryck när man vill beräkna och returnera ett eller flera värden. DAX hjälper dig helt enkelt att skapa ny information från data som redan finns i din modell.

## <a name="why-is-dax-so-important"></a>Varför är DAX så viktigt?
Det är enkelt att skapa en ny Power BI Desktop-fil och importera data till den. Du kan till och med skapa rapporter med värdefulla analyser utan att använda några DAX-formler alls. Men vad gör du om du behöver analysera tillväxten i procent i flera produktkategorier och för olika datumintervall? Eller om du vill beräkna den årliga tillväxten jämfört med trender på marknaden? DAX-formlerna innehåller den här funktionen och många andra viktiga funktioner dessutom. Lär dig att skapa effektiva DAX-formler som hjälper dig få ut så mycket som möjligt av dina data. När du har fått den information du behöver, kan du börja lösa verkliga affärsproblem som påverkar ditt slutresultat. Det är detta som gör Power BI så kraftfullt, och DAX hjälper dig att komma dit.

## <a name="prerequisites"></a>Förutsättningar
Du kanske redan vet hur man skapar formler i Microsoft Excel. I så fall blir det lättare att förstå DAX, men även om du inte har några erfarenheter av formler i Excel kommer de koncept som beskrivs här hjälpa dig igång med att skapa DAX-formler och lösa problem direkt.

Vi fokuserar på förståelsen av de DAX-formler som används i beräkningar, i synnerhet i mått och beräknade kolumner. Du bör redan känna till hur du använder Power BI Desktop till att importera data och lägga till fält i en rapport. Du bör också känna till de grundläggande begreppen [Mått](desktop-measures.md) och [Beräknade kolumner](desktop-calculated-columns.md).

### <a name="example-workbook"></a>Arbetsboksexempel

Det bästa sättet att lära sig DAX är att skapa några grundläggande formler, använda dem med faktiska data och se resultaten själv. I de här exemplen och uppgifterna använder vi filen [Contoso Sales Sample for Power BI Desktop](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip). Det här är samma exempelfil som används i [Självstudie: Skapa dina egna mått i Power BI Desktop](desktop-tutorial-create-measures.md). 

## <a name="lets-begin"></a>Vi börjar!
Om du ska förstå DAX måste du lära dig tre grundläggande begrepp: *Syntax*, *Funktioner* och *Kontext*. Det finns så klart andra viktiga begrepp i DAX, men om du förstår de här har du en bra grund för att utveckla dina DAX-kunskaper.

### <a name="syntax"></a>Syntax
Innan du skapar egna formler ska vi titta på DAX-formelns syntax. Syntaxen innehåller olika element som utgör en formel, eller rättare sagt hur formeln skrivs. Här är till exempel en enkel DAX-formel för ett mått:

![DAX-formelsyntax](media/desktop-quickstart-learn-dax-basics/qsdax_1_syntax.png)

Den här formeln innehåller följande syntaxelement:

**A.** Måttnamnet, **Total Sales**.

**B.** Operatorn likhetstecken ( **=** ), som anger starten av formeln. När den beräknas returneras ett resultat.

**C.** DAX-funktionen **SUM**, som lägger ihop alla tal i kolumnen **Sales[SalesAmount]** . Du lär dig mer om funktioner senare.

**D.** Parenteser **()** , som omger ett uttryck med ett eller flera argument. Alla funktioner kräver minst ett argument. Ett argument skickar ett värde till en funktion.

**E.** Den tabell som refereras, **Sales**.

**F.** Den kolumn som refereras, **[SalesAmount]** , i tabellen Sales. Det här argumentet anger för SUM-funktionen vilken kolumn som ska aggregera en summa.

När du försöker förstå en DAX-formel kan det underlätta att bryta ner varje element till ett språk som du tänker på och talar varje dag. Du kan till exempel läsa den här formeln som:

> *För måttet Total Sales beräknas (=) SUM av värdena i kolumnen [SalesAmount] i tabellen Sales.*
> 
> 

När den läggs till i en rapport beräknas måttet och returnerar värden genom att summera försäljningssiffrorna för de andra fält som vi inkluderar, ex.vis mobiltelefoner i USA.

Du kanske tänker ”Händer inte samma sak som om jag bara lägger till fältet SalesAmount i min rapport?” Egentligen, ja. Men det finns ett bra skäl att skapa ett eget mått som summerar värdena från fältet SalesAmount: Vi kan använda det som ett argument i andra formler. Det kan verka lite förvirrande nu, men när dina DAX-formelkunskaper växer kommer det här måttet att göra dina formler och modeller effektivare. Du kommer faktiskt se att måttet Total Sales dyker upp som ett argument i andra formler vid ett senare tillfälle.

Låt oss gå igenom ett par saker till om den här formeln. Vi har introducerat funktionen [SUM](/dax/sum-function-dax). Funktioner är färdiga formler som gör det lättare att utföra komplexa beräkningar och ändringar i tal, datum, tid, text och mycket mer. Du lär dig mer om funktioner senare.

Du kan också se att kolumnnamnet [SalesAmount] föregicks av tabellen Sales som kolumnen tillhör. Det här kallas för ett fullständigt kolumnnamn, eftersom det innehåller kolumnens namn med tabellens namn före. När du refererar till kolumner i samma tabell behöver du inte ta med tabellnamnet i formeln, vilket kan göra att långa formler med referenser till många kolumner blir kortare och enklare att läsa. Det är dock en bra idé att ta med tabellnamnet i måttformlerna, även när de finns i samma tabell.

> [!NOTE]
> Om ett tabellnamn innehåller blanksteg, reserverade nyckelord eller otillåtna tecken måste du sätta tabellnamnet inom enkla citattecken. Du måste också ange tabellnamnet inom citattecken om namnet innehåller tecken utanför intervallet med alfanumeriska ANSI-tecken, oavsett om teckenuppsättningen har stöd i dina nationella inställningar eller ej.
> 
> 

Det är viktigt formlerna har rätt syntax. Om syntaxen inte är korrekt returneras i de flesta fall ett syntaxfel. Det kan också hända att syntaxen är korrekt, men att värdena som returneras inte är vad du förväntade dig. DAX-redigeraren i Power BI Desktop innehåller en funktion för förslag, som används för att skapa syntaktiskt korrekta formler genom att hjälpa dig välja rätt element.

Nu ska vi skapa en enkel formel. Den här uppgiften hjälper dig att bättre förstå hur formelsyntaxen och förslagsfunktionen i formelfältet kan hjälpa dig.

### <a name="task-create-a-measure-formula"></a>Uppgift: Skapa en måttformel

1. [Ladda ned](https://download.microsoft.com/download/4/6/A/46AB5E74-50F6-4761-8EDB-5AE077FD603C/Contoso%20Sales%20for%20Power%20BI%20Designer.zip) och öppna filen Contoso Sales Sample for Power BI Desktop. 
    
2. I rapportvyn i fältlistan högerklickar du på tabellen **Sales** och väljer sedan **Nytt mått**.
    
3. I formelfältet ersätter du **Mått** genom att skriva det nya måttnamnet *Previous Quarter Sales*.
    
4. Efter lika med-tecknet skriver du de första bokstäverna *CAL* och dubbelklickar på den funktion som du vill använda. I den här formeln ska du använda **CALCULATE**-funktionen.

   Du ska använda CALCULATE-funktionen till att filtrera de belopp som vi vill summera med ett argument som vi skickar till funktionen CALCULATE. Det här är vad som kallas för kapslade funktioner. CALCULATE-funktionen innehåller minst två argument. Det första är uttrycket som ska utvärderas och det andra är ett filter.
   
5. Efter öppningsparentesen *(* för funktionen **CALCULATE** skriver du *SUM* följt av ytterligare en öppningsparentes *(* . 

   Sedan ska vi skicka ett argument till funktionen SUM.

6. Börja skriva *Sal*, och välj sedan **Sales [SalesAmount]** , följt av en avslutande parentes *)* . 

   Detta är det första uttrycksargumentet för vår CALCULATE-funktion.
    
7. Skriv ett kommatecken ( *,* ) följt av ett blanksteg för att ange det första filtret och skriv sedan *PREVIOUSQUARTER* . 
    
   Vi använder tidsfunktionen PREVIOUSQUARTER för att filtrera SUM-resultatet från föregående kvartal.
    
8. Efter öppningsparentesen *(* för PREVIOUSQUARTER-funktionen skriver du *Calendar[DateKey]* .
    
   Funktionen PREVIOUSQUARTER har ett argument, en kolumn som innehåller ett sammanhängande datumintervall. I vårt fall är det kolumnen DateKey i tabellen Calendar.
    
9. stäng båda argumenten som skickas till funktionen PREVIOUSQUARTER och funktionen CALCULATE genom att skriva två högerparenteser *))* .
    
   Formeln bör nu se ut så här:
    
   **Previous Quarter Sales = CALCULATE(SUM(Sales[SalesAmount]), PREVIOUSQUARTER(Calendar[DateKey]))**
    
10. Välj bockmarkeringen ![Bockmarkeringsikon](media/desktop-quickstart-learn-dax-basics/qsdax_syntax_taskcheckmark.png) i formelfältet eller tryck på Enter för att verifiera formeln och lägga till den i modellen.

Du klarade det! Du har nu skapat ett mått med DAX, och det var inte helt enkelt heller. Den här formeln beräknar den totala försäljningen för föregående kvartal, beroende på vilka filter som används i en rapport. Om vi till exempel placerar SalesAmount och vårt nya mått Previous Quarter Sales i ett diagram och sedan lägger till Year och QuarterOfYear som utsnitt, får vi ungefär detta:

![Diagram med Previous Quarter Sales och SalesAmount](media/desktop-quickstart-learn-dax-basics/qsdax_3_chart.png)

Du har nu sett flera viktiga aspekter av DAX-formler: 

- Den här formeln innehöll två funktioner. Tidsinformationsfunktionen [PREVIOUSQUARTER](/dax/previousquarter-function-dax) kapslades och skickades som argument till filterfunktionen [CALCULATE](/dax/calculate-function-dax). 

   DAX-formler kan innehålla upp till 64 kapslade funktioner. Det är inte troligt att en formel någonsin kommer att innehålla så många kapslade funktioner. Faktum är att det skulle vara svårt att skapa och felsöka en sådan formel, och den skulle förmodligen inte vara särskilt snabb heller.

- I den här formeln använde du också filter. Filter begränsar vad som ska beräknas. I det här fallet valde du ett filter som ett argument, vilket egentligen är resultatet av en annan funktion. Du lär dig mer om filter senare.

- Du använde funktionen CALCULATE. Den är en av de kraftfullaste funktionerna i DAX. När du skriver modeller och skapar mer komplexa formler kommer du förmodligen att använda den här funktionen många gånger. Vi går inte igenom funktionen CALCULATE närmare i den här artikeln, men var särskilt uppmärksam på den när du lär dig mer om DAX.

### <a name="syntax-quickquiz"></a>QuickQuiz – Syntax
1. Vad utför den här knappen i formelfältet?
   
   > ![Knappval](media/desktop-quickstart-learn-dax-basics/qsdax_2_syntaxquiz.png)
   > 
   > 
2. Vad omger alltid ett kolumnnamn i en DAX-formel?

Svaren finns i slutet av den här artikeln.

### <a name="functions"></a>Functions
Funktioner är fördefinierade formler som utför beräkningar med specifika värden, så kallade argument, i en viss ordning eller struktur. Argument kan vara andra funktioner, en annan formel, uttryck, kolumnreferenser, tal, text, logiska värden som TRUE eller FALSE, eller konstanter.

DAX innehåller följande typer av funktioner: [Datum och tid](/dax/date-and-time-functions-dax), [Tidsinformation](/dax/time-intelligence-functions-dax), [Information](/dax/information-functions-dax), [Logisk](/dax/logical-functions-dax), [Matematisk](/dax/math-and-trig-functions-dax), [Statistisk](/dax/statistical-functions-dax), [Text](/dax/text-functions-dax), [Överordnad/underordnad](/dax/parent-and-child-functions-dax) och [Övrigt](/dax/other-functions-dax). Om du känner till funktionerna i Excel-formler, kommer du känna igen många av funktionerna i DAX. DAX-funktionerna är emellertid unika på följande sätt:

* En DAX-funktion refererar alltid till en fullständig kolumn eller tabell. Om du endast vill använda specifika värden från en tabell eller kolumn kan du lägga till filter i formeln.
* Om du behöver anpassa radbaserade beräkningar finns det DAX-funktioner där du kan använda det aktuella radvärdet eller ett relaterat värde som en typ av argument, för att utföra beräkningar som varierar beroende på kontext. Du lär dig mer om kontexter senare.
* DAX innehåller många funktioner som returnerar en tabell i stället för ett värde. Tabellen visas inte, men den används som indata för andra funktioner. Exempelvis kan du hämta en tabell och sedan räkna distinkta värden i den, eller beräkna dynamiska summor i filtrerade tabeller och kolumner.
* DAX innehåller flera olika tidsfunktioner. Med dessa funktioner kan du definiera eller välja datumintervall, samt utföra dynamiska beräkningar som baseras på dem. Exempelvis kan du jämföra summor över parallella perioder.
* Det finns en populär funktion i Excel som heter LETARAD. DAX-funktioner använder inte en cell eller ett cellområde som en referens som LETARAD gör i Excel. DAX-funktionerna använder en kolumn eller en tabell som referens. Kom ihåg att du arbetar med en relationsdatamodell i Power BI Desktop. Det är ganska enkelt att söka värden i en annan tabell, och i de flesta fall behöver du inte skapa någon formel alls.
  
  Som du ser kan funktionerna i DAX hjälpa dig att skapa kraftfulla formler. Vi bara snuddat vid grunderna i funktionerna. När du lär dig mer om DAX kommer du skapa formler med många olika funktioner. Ett bra ställe för att få mer detaljerad information om varje DAX-funktion finns i [Funktionsreferens för DAX](/dax/).

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

Filterkontext är lite svårare att förstå än radkontext. Du kan enklast föreställa dig filterkontext som: Ett eller flera filter som tillämpas i en beräkning som fastställer ett resultat eller ett värde.

Filterkontexter används inte i stället för radkontexter utan snarare förutom radkontexten. För att ytterligare begränsa vilka värden som ska ingå i en beräkning kan du exempelvis tillämpa en filterkontext som inte bara anger radkontexten utan även anger ett visst värde (filter) i radkontexten.

Filterkontext är enkel att se i rapporterna. När du lägger till TotalCost i en visualisering och därefter lägger till Year och Region, definierar du till exempel en filterkontext som väljer en delmängd av data baserat på ett visst år och region.

Varför är filterkontext så viktigt i DAX? Det beror på att även om filterkontext tillämpas enklast genom att lägga till fält i en visualisering, kan filterkontext också användas i en DAX-formel genom att definiera ett filter som använder funktioner, till exempel ALL, RELATED, FILTER, CALCULATE efter relationer och andra mått och kolumner. Nu ska vi exempelvis titta på följande formel i ett mått med namnet Store Sales:

![Måttet Store Sales](media/desktop-quickstart-learn-dax-basics/qsdax_4_context.png)

För att bättre förstå den här formeln bryter vi ned den, ungefär som med andra formler.

Den här formeln innehåller följande syntaxelement:

**A.** Måttnamnet, **Store Sales**.

**B.** Operatorn likhetstecken ( **=** ), som anger starten av formeln.

**C.** Funktionen **CALCULATE**, som utvärderar ett uttryck som ett argument i en kontext som ändras av de angivna filtren.

**D.** Parenteser **()** , som omger ett uttryck med ett eller flera argument.

**E.** Ett mått **[Total Sales]** i samma tabell som ett uttryck. Måttet Total Sales har formeln: =SUM(Sales[SalesAmount]).

**F.** Ett kommatecken ( **,** ), som avgränsar det första uttrycksargumentet från filterargumentet.

**G.** Den fullständiga refererade kolumnen **Kanal[ChannelName]** . Detta är vår radkontext. Varje rad i den här kolumnen anger en kanal som Store eller Online.

**H.** Det specifika värdet, **Store**, som ett filter. Detta är vår filterkontext.

Den här formeln ser till att endast försäljningsvärden som definieras av måttet Total Sales beräknas för rader i kolumnen Channel[ChannelName], med värdet *Store* som filter.

Du förstår säkert att genom att kunna definiera filterkontext inom en formel får man stora och kraftfulla möjligheter. Möjligheten att referera till ett visst värde i en relaterad tabell är bara ett sådant exempel. Oroa dig inte om du inte förstår kontexten direkt. När du skapar egna formler kommer du bättre förstå kontexten och varför den är så viktig i DAX.

### <a name="context-quickquiz"></a>QuickQuiz – Kontext
1. Vilka är de två kontexttyperna?
2. Vad är filterkontext?
3. Vad är radkontext?

Svaren finns i slutet av den här artikeln.

## <a name="summary"></a>Sammanfattning
Nu när du har en grundläggande förståelse för de viktigaste begreppen i DAX, kan du börja skapa DAX-formler för mått på egen hand. DAX kan verkligen vara lite svårt att lära sig, men det finns många hjälpresurser som du kan använda dig av. När du har läst igenom den här artikeln och experimenterat med några av dina egna formler, kan du läsa mer om andra DAX-begrepp och formler som kan hjälpa dig att hitta dina egna lösningar. Det finns många DAX-resurser tillgängliga för dig; den viktigaste är [Referens för dataanalysuttryck (DAX)](/dax/).

Eftersom DAX har funnits i flera år i andra Microsoft BI-verktyg som Power Pivot och Analysis Services-tabellmodeller så det finns mycket användbar information där. Mer information hittar du i böcker, faktablad och bloggar från både Microsoft och ledande BI-tekniker. [DAX Resource Center Wiki på TechNet](https://social.technet.microsoft.com/wiki/contents/articles/dax-resource-center.aspx) är också ett bra ställe att börja på.

### <a name="quickquiz-answers"></a>QuickQuiz-svar
Syntax:

1. Verifierar och anger måttet i modellen.
2. Hakparenteser [].

Funktioner:

1. En tabell och en kolumn.
2. Ja. En formel kan innehålla upp till 64 kapslade funktioner.
3. [Textfunktioner](/dax/text-functions-dax).

Kontext:

1. Radkontext och filterkontext.
2. Ett eller flera filter i en beräkning som anger ett enda värde.
3. Den aktuella raden.
