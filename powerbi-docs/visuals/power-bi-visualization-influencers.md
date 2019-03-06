---
title: Självstudie om visualiseringar av viktiga influencers
description: Självstudie – skapa en visualisering av viktiga influencers i Power BI
author: mihart
manager: kvivek
ms.reviewer: juluczni
ms.service: powerbi
ms.component: powerbi-service
ms.topic: tutorial
ms.date: 02/12/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 1f55a12e306af8a28e297e9feab2f2c0ae0cd60b
ms.sourcegitcommit: 87e81ba92f3d1d65c26f9fc007bf106f96f37bfd
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57461682"
---
# <a name="key-influencers-visualization"></a>Visualisering av viktiga influencers
Visualiseringen av viktiga influencers hjälper dig att förstå vilka faktorer som påverkar ett mått som du är intresserad av. Den analyserar dina data, rangordnar de faktorer som är viktiga och visar dem som viktiga influencers. Säg att du till exempel är intresserad av att räkna ut vad som påverkar personalomsättningen. En faktor kanske är anställningsavtalens längd och en annan kan vara medarbetarnas ålder. 
 
## <a name="when-to-use-key-influencers"></a>När ska du använda viktiga influencers? 
Visualiseringen av viktiga influencers är ett bra val 
- om du vill se vilka faktorer som påverkar det mått som analyseras

- om du vill jämföra den relativa vikten för de här faktorerna. Har till exempel korta avtalstider större effekt på personalomsättningen än långa avtalstider? 

## <a name="key-influencer-requirements"></a>Krav för viktiga influencers 
Det mått du analyserar måste vara ett kategoriskt fält.    


## <a name="features-of-the-key-influencer-visual"></a>Funktioner i visualiseringen av viktiga influencers

![numrerade funktioner](media/power-bi-visualization-influencers/power-bi-ki-numbers-new.png)    

1. ***Flikar*** – välj en flik för att växla mellan vyer. Viktiga influencers visar de viktigaste faktorerna som påverkar det valda måttvärdet. Viktigaste segment visar de viktigaste segmenten som påverkar det valda måttvärdet. Ett *segment* består av en kombination av värden.  Ett segment kan till exempel vara konsumenter som har varit kunder i minst 20 år och lever i region väst. 

2. ***Listruta*** – värde för det mått som undersöks. I det här exemplet tittar vi på måttet **rating** (omdöme) och det värdet vi har valt är **low** (lågt).    

3. ***Omräkning*** – hjälper oss att tolka det visuella objektet i den vänstra rutan. 

4. ***Vänster ruta*** – den vänstra rutan innehåller ett visuellt objekt.  I det här fallet visar den vänstra rutan en lista över viktigaste influencers.

5. ***Omräkning*** – hjälper oss att tolka det visuella objektet i den högra rutan.

6. ***Höger ruta*** – den högra rutan innehåller ett visuellt objekt. I det här fallet visar stapeldiagrammet alla värden för den **viktigaste influencern**, **Tema** som valts i den vänstra rutan. Det specifika värdet (**Usability**, användbarhet) från det vänstra fönstret visas i grönt och alla andra värden för **Tema** visas i svart.

7. ***Medellinje*** – medelvärdet beräknas för alla andra möjliga värden för **Tema**, utom för **Usability** (användbarhet). Så beräkningen gäller för alla värden i svart. Den visar vilken procentandel av övriga **teman** som lämnade ett lågt omdöme. När en kund lämnar ett omdöme beskriver alltså den kunden även anledningen eller **temat** för omdömet. Några teman är användbarhet, hastighet, säkerhet o.s.v. **Tema** är **användbarhet** är den näst viktigaste influencern för ett lågt omdöme enligt vårt visuella objekt i den vänstra rutan. Om vi tar ett genomsnitt av alla andra teman och hur de påverkar ett **lågt** omdöme får vi resultatet som visas i rött här. Av alla andra teman är endast 11,35 % av dem högre än **användbarhet**. 

8. ***Kryssruta*** – visa enbart värden som är influencers.

## <a name="create-a-key-influencers-visual"></a>Skapa ett visuellt objektet av viktiga influencers 
 
Titta på det här videoklippet och lär dig hur du skapar ett visuellt objekt av viktiga influencers. Följ sedan stegen nedan för att skapa ett själv. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/fDb5zZ3xmxU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Vår produktchef vill ta reda på vilka faktorer som gjorde att kunder lämnade negativa recensioner vår molntjänst.  Öppna [PBIX-filen med kundfeedback](https://github.com/Microsoft/powerbi-desktop-samples/blob/master/2019/customerfeedback.pbix) i Power BI Desktop. Du kan också hämta [Excel-filen med kundfeedback för Power BI-tjänsten eller Power BI Desktop](https://github.com/Microsoft/powerbi-desktop-samples/blob/master/2019/customerfeedback.xlsx). 

> [!NOTE]
> Datauppsättningen Customer Feedback (kundfeedback) bygger på [Moro et al., 2014] S. Moro, s. Cortez och s. Rita. A Data-Driven Approach to Predict the Success of Bank Telemarketing. Decision Support Systems, Elsevier, 62:22-31, June 2014 

1. Öppna rapporten och välj ikonen viktiga influencers.  

    ![Välj mallen Viktiga influencers från rutan Visualiseringar](media/power-bi-visualization-influencers/power-bi-template-new.png)

2. Dra det mått du vill undersöka till fältet **Analysera**. Fältet **Analysera** har endast stöd för kategoriska (icke-kontinuerliga) variabler. Eftersom vi är intresserade av vad som gör att kundomdömet för vår tjänst blir **lågt** väljer vi **Customer Table** (Kundtabell) > **Rating** (Omdöme).    
3. Dra sedan fält som du tror skulle kunna påverka **Rating** (Omdöme) till **Förklara med**. Du kan dra in så många fält som du vill. I det här fallet börjar vi med: 
    - Land/region 
    - Roll i organisationen 
    - Prenumerationstyp 
    - Företagsstorlek 
    - Tema     
4. Eftersom vi är intresserade av negativa omdömen markerar du **Low** (låg) i listrutan för **Vad påverkar Rating (omdöme) att vara**.  

    ![välj Låg i listrutan](media/power-bi-visualization-influencers/power-bi-key-influencers.png)

Analysen körs på tabellnivå i fältet som analyseras. I det här fallet är vi intresserade av måttet **Rating** (Omdöme), som definieras på kundnivå (varje kund har antingen gett ett högt eller lågt betyg). Alla våra förklarande faktorer måste vara definierade på kundnivå om det visuella objektet ska kunna använda dem. 

I exemplet ovan har alla våra förklarande faktorer antingen en 1: 1- eller många-till-en-relation med vårt mått. Till exempel associeras varje betyg med exakt ett tema (det huvudsakliga temat för kundrecensionen). På samma sätt kommer kunder från ett land, de har en medlemskapstyp och en roll i organisationen. Våra förklarande faktorer är därför redan attribut för en kund och ingen omvandling behövs – det visuella objektet kan använda dem omedelbart. 

Senare i självstudien ska vi titta på mer komplexa exempel där vi har en-till-många-relationer. I sådana fall måste kolumnerna först aggregeras på kundnivå innan analysen kan köras.  

Mått och aggregeringar som används som förklarande faktorer utvärderas också på tabellnivån för måttet **Analysera**. Vi ser några exempel på det senare i den här artikeln. 

## <a name="interpreting-categorical-key-influencers"></a>Tolka kategoriska viktiga influencers 
Låt oss ta en titt på våra viktigaste influencers för låga omdömen. 

### <a name="top-single-factor-influencing-likelihood-of-a-low-rating"></a>Främsta enskilda faktor som påverkar sannolikheten för ett lågt omdöme

I vår organisation har vi tre roller: konsumenter, administratörer och utgivare. Att vara konsument är den viktigaste faktorn som bidrar till ett lågt omdöme. 

![välj roll i organisationen är konsument](media/power-bi-visualization-influencers/power-bi-role-consumer.png)


Mer exakt är konsumenter 2,57 x mer troliga att ge oss ett negativt betyg. I diagrammet Viktiga influencers står **Role in Org is consumer** (Roll i organisationen är konsument) överst på listan till vänster. Genom att markera **Role in Org is consumer** (Roll i organisationen är konsument) får vi se mer information i Power BI i fönstret till höger – den jämförelsevisa effekten av varje **roll** på sannolikheten för ett lågt omdöme.
  
- 14,93 % av konsumenter ger en låg poäng  
- I genomsnitt ger alla andra roller en låg poäng i 5,78 % av fallen 
- Konsumenterna är därför 2,57 x mer troliga att ge en låg poäng jämfört med alla andra roller (skillnaden mellan grön stapel och röd streckad linje) 

### <a name="second-single-factor-influencing-likelihood-of-a-low-rating"></a>Den näst viktigaste enskilda faktorn som påverkar sannolikheten för ett lågt omdöme

I det visuella objektet av viktiga influencers kan vi jämföra och rangordna faktorer utifrån många olika variabler.  Vår andra influencer har inget samband med **Roll i organisationen**.  Välj den andra influencern i listan, **Theme is usability** (Tema är användbarhet). 

![välj tema är användbarhet](media/power-bi-visualization-influencers/power-bi-theme.png)

Här ser vi att den näst viktigaste faktorn handlar om temat för kundens recension. Kunder som kommenterade produktens *användbarhet* var 2,21 x mer troliga att ge ett lågt betyg jämfört med kunder som kommenterade andra teman, till exempel tillförlitlighet, design eller hastighet. 

Om du jämför de visuella objekten ser vi att medelvärdet (röd streckad linje) har ändrats från 5,78 % till 11,34 %. Medelvärdet är dynamiskt eftersom det baseras på medelvärdet för alla andra värden. När det gäller den första influencern uteslöts kundroll, medan för den andra var det temat användbarhet som uteslöts. 
 
Om du markerar rutan längst ned i det visuella objektet filtreras vyn så att endast influerande värden visas (i det här fallet som driver ett lågt betyg). Vi går från att titta på tolv teman till de fyra som Power BI har identifierat som drivande för låga omdömen. 

![markera kryssrutan](media/power-bi-visualization-influencers/power-bi-only-show.png)

## <a name="interacting-with-other-visuals"></a>Arbeta med andra visuella objekt 
 
Varje gång en användare klickar på ett utsnitt, ett filter eller ett annat visuellt objekt på arbetsytan, körs analysen i det visuella objektet med viktiga influensers igen på den nya delen data. Vi kan till exempel dra in Company Size (Företagsstorlek) i rapporten och använda den som ett utsnitt. Vi vill se om de viktiga influencers för kunder i stora företag (företagsstorlek är större än 50 000) skiljer sig från allmänheten.  
 
När vi väljer **> 50 000** körs analysen igen och vi kan se att våra influencers har ändrats. För kunder i stora företag är den viktigaste influencern för låga omdömen att ha ett **tema** som rör **säkerhet**. Det kanske vi vill undersöka vidare och se om det finns specifika säkerhetsfunktioner som våra kunder i stora företag är missnöjda med. 

![utsnitt efter företagsstorlek](media/power-bi-visualization-influencers/power-bi-filter.png)

## <a name="interpreting-continuous-key-influencers"></a>Tolka kontinuerliga viktiga influencers 
 
Hittills har vi använt det visuella objektet för att utforska hur olika kategoriska fält påverkar låga omdömen. Det är också möjligt att ta in kontinuerliga faktorer (till exempel ålder, höjd, pris) i ”Förklara med”. Låt oss titta på vad händer om vi drar in Tenure (Nyttjandeperiod) från tabellen Customer (Kund) i ”Förklara med”. Nyttjandeperioden visar hur länge kunden har använt tjänsten. 
 
Vi ser att när värdet för **Tenure** (Nyttjandeperiod) ökar, ökar även sannolikheten att få ett lägre omdöme. Denna trend tyder på att det är troligare att våra långsiktiga kunder ger ett negativt betyg, vilket är en intressant insikt som jag kanske vill följa upp senare.  
 
Visualiseringen talar om för oss att varje gång nyttjandeperioden går upp med 13,44 månader, ökar i genomsnitt sannolikheten för ett lågt omdöme med 1,23 x. I det här fallet motsvarar 13,44 månader standardavvikelsen för nyttjandeperioden. Så den insikt vi får är att om nyttjandeperioden ökar med en standardmängd (standardavvikelsen för nyttjandeperioden) påverkar det sannolikheten att få ett lågt omdöme. 
 
Spridningsdiagrammet till höger visar den genomsnittliga % av låga omdömen för varje värde av nyttjandeperiod och visar en trendlinje som markerar lutningen.  


![spridningsdiagram för nyttjandeperiod](media/power-bi-visualization-influencers/power-bi-tenure.png)

## <a name="interpreting-measuresaggregate-as-key-influencers"></a>Tolka mått/aggregering som viktiga influencers 
 
Slutligen kan användare också använda mått och aggregeringar som förklarande faktorer i sin analys. Vi kanske till exempel vill se vilken effekt antalet kundsupportärenden eller genomsnittlig varaktighet för ett öppet ärende har på vilket betyg vi får. 
 
I så fall vill vi se om antalet supportärenden en kund har påverkar vilken poäng de ger oss. Vi ska ta in supportärende-ID från tabellen Support Ticket (supportärende). Eftersom en kund kan ha flera supportärenden behöver vi aggregera ID på kundnivå. Den här aggregeringen är viktig eftersom vi kör analysen på kundnivå, så alla drivande faktorer måste definieras på den precisionsnivån. 
 
Vi ska titta på antalet ID:n (så att varje kundrad har ett antal supportärenden som är associerade till dem). I det här fallet ser vi att när antalet supportärenden ökar, så ökar också sannolikheten för ett lågt omdöme med 5,51 x. Det visuella objektet till höger visar det genomsnittliga antalet supportärenden efter olika omdömesvärden (utvärderas på kundnivå). 

![påverkan av Support Ticket ID (supportärende-ID)](media/power-bi-visualization-influencers/power-bi-support-ticket.png)



## <a name="interpreting-the-results-top-segments"></a>Tolka resultaten: viktigaste segment 
 
På fliken Viktiga influencers kan användare utvärdera varje faktor individuellt, men man kan även växla till Viktiga segment och se hur en kombination av faktorer påverkar det mått man analyserar. 
 
Inledningsvis visar Viktiga segment en översikt över alla segment som har identifierats av Power BI. I exemplet nedan kan vi se att sex segment har hittats. Dessa segment är rangordnade efter % av låga omdömen i segmentet. Vi kan se att segment 1 till exempel har 74,3 % låga kundomdömen.  Ju högre bubbla, desto högre andel låga omdömen. Storleken på bubblan representerar hur många kunder som finns i segmentet. 

![välj fliken för Viktigaste segment](media/power-bi-visualization-influencers/power-bi-top-segments-tab.png)

Om du markerar en bubbla visas mer detaljerad information om det segmentet. Om vi till exempel väljer Segment 1 ser vi att det består av relativt etablerade kunder (som har funnits hos oss mer än 29 månader) som har ett stort antal supportärenden (större än 4). Slutligen är de inte utgivare (så de är antingen konsumenter eller administratörer).  
 
I den här gruppen har 74,3 % lämnat ett lågt omdöme. Den genomsnittliga kunden ger ett lågt omdöme 11,7 % av fallen, så det här segmentet har en betydligt större andel låga omdömen (63 procentenheter högre). Vi ser också att segment 1 innehåller cirka 2,2 % av våra data, så det motsvarar en adresserbar del av populationen. 

![välj det viktigaste segmentet](media/power-bi-visualization-influencers/power-bi-top-segments2.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning 
 
**Vilka begränsningar har förhandsversionen?** 
 
Det visuella objektet av viktiga influencers finns för närvarande i offentlig förhandsversion, och det finns flera begränsningar som användare bör känna till. Funktioner som för närvarande inte är tillgängliga omfattar följande: 
- Analysera mått som är aggregeringar/mått 
- Använda det visuella objektet i Power BI Embedded
- Använda det visuella objektet i Power BI-mobilappar
- RLS-stöd 
- Direct Query-stöd 
- Live-anslutningsstöd 
 
**Jag får ett felmeddelande om att inga influencers/segment hittades. Varför?**  

![fel – inga influencers hittades](media/power-bi-visualization-influencers/power-bi-error1.png)


Det här felet uppstår när du har dragit in fält i **Förklara med** men inga influencers hittades.   
- Du har lagt till det mått som du analyserar i både Analysera och Förklara med (du bör ta bort det från **Förklara med**) 
- Dina förklarande fält har för många kategorier med få observationer. Det gör det svårt för visualiseringen att avgöra vilka faktorer som är influencers eftersom det är svårt att generalisera utifrån en handfull observationer 
- Dina förklarande faktorer har ett tillräckligt antal observationer för att göra generaliseringar, men visualiseringen kunde inte att hitta någon meningsfull korrelation att rapportera 
 
**Jag ser ett fel om att det mått jag analyserar inte har tillräckligt med data för att köra analysen. Varför?**  

![fel – inte tillräckligt med data](media/power-bi-visualization-influencers/power-bi-not-enough-data.png)

Visualiseringen skapas genom att titta på mönster i data för en grupp (till exempel för kunder som lämnade låga omdömen) jämfört med andra grupper (till exempel kunder som lämnade höga omdömen). Om data i din modell har mycket få observationer är det svårt att hitta mönster. Om visualiseringen inte har tillräckligt med data för att hitta meningsfulla influencers meddelas du att mer data behövs för att köra analysen. Vi rekommenderar att du har minst 100 observationer för det valda tillståndet (kunder som lämnar) och minst 10 observationer för tillstånd som du använder för jämförelse (kunder som inte lämnar).  
 
**Jag ser ett fel om att ett fält i Förklara med inte är unikt relaterat till tabellen som innehåller det mått jag analyserar. Varför?**  
 
Analysen körs på tabellnivå i fältet som analyseras. Om du till exempel analyserar kundfeedback för din tjänst kanske du har en tabell som anger om en kund lämnade ett högt eller lågt omdöme. I så fall skulle din analys köras på kundtabellsnivån. 

Om du har en relaterad tabell som har definierats på en mer detaljerad nivå än tabellen som innehåller dina mått får du det här felet. Vi illustrerar detta med ett exempel: 
 
- Du analyserar vad som påverkar kunder att ge låga omdömen om din tjänst 
- Du är intresserad av att se om vilken enhet kunden använder din tjänst på, påverkar vilka omdömen de ger 
- En kund kan använda tjänsten på flera olika sätt   
- I exemplet nedan använder kund 10000000 både en webbläsare och en surfplatta för att interagera med tjänsten 

![fel – om du har en relaterad tabell som har definierats på en mer detaljerad nivå än tabellen som innehåller dina mått](media/power-bi-visualization-influencers/power-bi-error2.png)

Om du försöker använda enhetskolumnen som en förklarande faktor visas följande fel: 

![fel – fel kolumn](media/power-bi-visualization-influencers/power-bi-error3.png)

Det beror på att enhet inte har definierats på kundnivån – en kund kan använda tjänsten på flera enheter. Om visualiseringen ska kunna hitta mönster måste enheten bli ett attribut för kunden. I det här fallet har jag flera lösningar, beroende på min förståelse av verksamheten: 
 
- Jag kan ändra sammanfattningen av enheten till att exempelvis räknas om jag tror att antalet enheter kan påverka vilken poäng en kund ger 
- Jag kan pivotera enhetskolumnen för att se om användning av tjänsten på en viss enhet påverkar en kunds omdöme  
 
I det här exemplet pivoterar jag mina data för att skapa nya kolumner för ”browser” (webbläsare), ”mobile” (mobiltelefon) och ”tablet” (surfplatta). Nu kan jag använda dem i Förklara med. Vi upptäcker att alla enheter är influencers och att webbläsaren har den största effekten på kundpoängen. 

Mer exakt är kunder som inte använder webbläsaren för att använda tjänsten 3,79 x mer troliga att ge en låg poäng än de som gör det. Längre ned i listan ser vi att det omvända är sant för mobiltelefoner. Det är mer troligt att kunder som använder mobilappen ger ett lägre betyg än de som inte gör det.  

![fel – löst](media/power-bi-visualization-influencers/power-bi-error3-solution.png)

**Jag ser en varning om att mått inte tagits med i min analys. Varför?** 

![fel-mått togs inte med](media/power-bi-visualization-influencers/power-bi-measures-not-included.png)


Analysen körs på tabellnivå i fältet som analyseras. Om du analyserar kundomsättning kan du ha en tabell som anger om en kund har lämnat er eller inte. I så fall skulle din analys köras på kundtabellsnivån.
 
Mått och aggregeringar analyseras som standard på den tabellnivån. Om vi hade ett mått för ”Genomsnittliga utgifter per månad” skulle det analyseras på kundtabellsnivån.  

Om kundtabellen inte har en unik identifierare kan vi inte utvärdera måttet och den ignoreras i analysen. Undvik det genom att kontrollera att tabellen med ditt mått (i det här fallet kundtabellen) har en unik identifierare (t.ex. kund-ID). Det är också mycket enkelt att lägga till en indexkolumn med hjälp av Power Query.
 
**Jag ser en varning om att det mått jag analyserar har fler än 10 unika värden och att detta kan påverka kvaliteten på min analys. Varför?**  

AI-visualiseringen är optimerad för att analysera kategorier (till exempel Kvarvarande är Ja eller Nej, Kundnöjdhet är Hög, Medel eller Låg o.s.v.). Om vi ökar antalet kategorier innebär det att vi har färre observationer per kategori, vilket gör det svårare att hitta mönster i data för visualiseringen. 

Vi rekommenderar att man grupperar liknande värden i en och samma enhet för att hitta starkare influencers. Om du till exempel har ett mått för pris får du troligtvis bättre resultat genom att samla liknande priser i grupper som Högt, Medel, Lågt i stället för att använda enskilda prispunkter. 

![fel – fler än tio unika faktorer](media/power-bi-visualization-influencers/power-bi-error4.png)


**Det finns faktorer i mina data som ser ut som om de borde vara influencers, men det är de inte. Hur kan det bli så?**

I exemplet nedan ser vi att kunder som är konsumenter oftare ger låga omdömen (14,93 % av omdömena är låga). Intressant är att även administratörsrollen har en hög andel låga omdömen (13,42 %), men den anses inte vara en influencer. 

Anledningen är att visualiseringen också tar hänsyn till antalet datapunkter vid identifiering av influencers. I exemplet nedan har vi över 29 000 konsumenter och 10 gånger färre administratörer (cirka 2 900). Dessutom gav endast 390 av dem ett lågt omdöme. Det visuella objektet har därför inte tillräckligt med data för att avgöra om det verkligen är ett mönster i administratörsomdömena eller om det bara är en slump.  

![fel – hur influencers identifieras](media/power-bi-visualization-influencers/power-bi-error5.png)

**Hur beräknas viktiga influencers?**

AI-visualiseringen använder [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) för att köra en logistisk regression för att beräkna viktiga influencers. En logistisk regression är en statistisk modell som jämför olika grupper med varandra. Om vi skulle titta på vad som driver fram låga omdömen skulle den logistiska regressionen titta på hur kunder som gav en låg poäng skiljer sig från dem som gav höga betyg. Om vi hade flera kategorier (högt betyg, neutralt betyg, lågt betyg) skulle vi titta på hur de kunder som gav ett lågt omdöme skiljer sig från kunder som inte gav ett lågt omdöme (hur de skiljer sig från de som lämnade ett högt ELLER ett neutralt omdöme). 
 
Den logistiska regressionen söker efter mönster i data, som visar hur kunder som lämnade ett lågt omdöme kan skilja sig från dem som lämnade ett högt omdöme. Den kanske till exempel upptäcker att kunder som har fler supportärenden ger en mycket högre % av låga omdömen än de som har få eller inga supportärenden.
 
Den logistiska regressionen väger också in hur många datapunkter det finns. Om till exempel kunder med administratörsroll proportionellt sett ger mer negativa betyg, men om det bara finns en handfull administratörer, räknas inte det som en påverkande faktor. Det beror på att det inte finns tillräckligt med datapunkter tillgängliga för att härleda ett mönster. Ett statistiskt test (Wald-test) används för att avgöra om en faktor ska betraktas som en influencer. Det visuella objektet använder p-värdet 0,05 för att fastställa tröskelvärdet. 


**Hur beräknas segment?**

AI-visualiseringen använder [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) för att köra ett beslutsträd för att hitta intressant undergrupper. Syftet med beslutsträdet är att få en undergrupp av datapunkter som har ett relativt högt värde för det mått vi är intresserade av (till exempel kunder som lämnade ett lågt omdöme). 

Beslutsträdet tar varje förklarande faktor och försöker avgöra vilken faktor som ger den bästa uppdelningen. Om vi till exempel filtrerar data så att endast kunder i stora företag inkluderas, skulle det skilja ut kunder som gav oss ett högt jämfört med ett lågt omdöme? Eller kanske det blir bättre om vi filtrerar data så att vi endast inkluderar användare som har kommenterat säkerheten? 

När beslutsträdet har gjort en uppdelning går den vidare med den undergruppen av data (till exempel kunder som har kommenterat säkerheten) och försöker ta reda på är vilken uppdelningen som är bäst för dessa data. Efter varje uppdelning väger den också in om den har tillräckligt med datapunkter för att det ska vara en representativ grupp att härleda ett mönster från eller om det bara kan vara en anomali i data och därmed inget segment. (Ett annat statistiskt test används för att kontrollera uppdelningens statistiska signifikans, med p-värdet 0,05). 

När beslutsträdet har slutförts blir alla uppdelningar (säkerhetskommentarer, stort företag) Power BI-filter. Den här filterkombinationen paketeras som ett segment i det visuella objektet. 
 
**Varför blir visa faktorer influencers/slutar vara influencers när jag drar in fler fält i Förklara med?**

Visualiseringen utvärderar alla förklarande faktorer tillsammans. Det innebär att även om en faktor på egen hand kan vara en influencer kanske den inte är det i förhållande till andra faktorer. Föreställ dig att vi analyserar vad som påverkar höga huspriser med sovrum och husstorlek som förklarande faktorer. 
- På egen hand kanske sovrum är en påverkande faktor för höga huspriser 
- Om vi tar med husstorlek i analysen ser vi vad som händer med sovrum om vi håller husstorleken konstant 
- Om vi håller husstorlek konstant på 140 m2 är det osannolikt att ett kontinuerligt ökande antal sovrum dramatiskt ökar huspriset. Sovrum kanske inte är en lika viktig faktor som den var innan husstorlek vägdes in. 




## <a name="next-steps"></a>Nästa steg
[Kombinationsdiagram i Power BI](power-bi-visualization-combo-chart.md)

[Visualiseringstyper i Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
