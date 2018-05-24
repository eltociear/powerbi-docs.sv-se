Med DAX får du tillgång till många funktioner för att forma, ställa upp eller i övrigt analysera dina data. Dessa funktioner kan grupperas i en handfull kategorier:

* **Aggregerings**funktioner
* **Inventerings**funktioner
* **Logiska** funktioner
* **Informations**funktioner
* **Text**funktioner
* **Datum**funktioner

När du börjar skriva en formel i Power BI Desktops **formelfält** visas, ungefär som i Excel, en lista över tillgängliga funktioner som hjälper dig att avgöra vilken av de tillgängliga funktionerna som du vill välja. Och med hjälp av **upp**- och **ned**pilarna på tangentbordet kan du markera alla tillgängliga funktioner för att visa en kort beskrivning.

Power BI visar de funktioner som matchar de bokstäver som du har skrivit hittills, så om du skriver *S* visas bara funktioner som börjar med *S* i listan. Om du skriver *Su*, visas bara funktioner som *innehåller* bokstavssekvensen *Su* i listan (de måste inte börja med *Su*, de behöver bara innehålla den bokstavssekvensen).

![](media/7-3-dax-functions/dax-functions_1.png)

Det är enkelt att experimentera med DAX på det här sättet och att hitta var och en av de olika DAX-funktionerna som är tillgängliga i Power BI. Allt du behöver göra är att börja skriva så hjälper Power BI dig.

Nu när vi vet hur man startar upp DAX-formeln ska vi ta en titt på var och en av dessa funktionskategorier i tur och ordning.

## <a name="aggregation-functions"></a>Aggregeringsfunktioner
DAX har ett antal **aggregeringsfunktioner**, inklusive följande vanliga funktioner:

* SUM
* MEDEL
* MIN
* MAX
* SUMX (och andra *X*-funktioner)

Dessa funktioner fungerar endast för numeriska kolumner och kan vanligtvis bara sammanställa en kolumn i taget.

Särskilda aggregeringsfunktioner som slutar med **X**, som **SUMX**, kan dock fungera med flera kolumner. Dessa funktioner går igenom tabellen och utvärderar uttrycket för varje rad.

## <a name="counting-functions"></a>Inventeringsfunktioner
Ofta använda **inventerings**funktioner i DAX inkluderar följande:

* COUNT
* COUNTA
* COUNTBLANK
* COUNTROWS
* DISTINCTCOUNT

Dessa funktioner räkna olika delar som distinkta värden, icke-tomma värden och tabellrader.

## <a name="logical-functions"></a>Logiska funktioner
Samlingen av **logiska** funktioner i DAX inkluderar:

* AND
* OR
* NOT
* IF
* IFERROR

Dessa särskilda funktioner kan också anges med *operatorer*. Till exempel **AND** kan skrivas som (ersättas med) **&&** i en DAX-formel.

Du kan använda operatorer (som **&&**) när du behöver fler än två villkor i din formel, men i övrigt är det bästa praxis att använda själva funktionsnamnet (som **AND**) för DAX-kodens läsbarhet.

## <a name="information-functions"></a>Informationsfunktioner
**Informations**funktionerna i DAX inkluderar:

* ISBLANK
* ISNUMBER
* ISTEXT
* ISNONTEXT
* ISERROR

Dessa funktioner kan vara användbara i en viss situation, men det finns ett värde i att veta datatypen för dina kolumner i förväg, i stället för att vara beroende av att dessa funktioner ska tillhandahålla datatypen.

DAX använder **MAX**- och **MIN**-funktionerna för att både *aggregera* värden och *jämföra* värden.

## <a name="text-functions"></a>Textfunktioner
**Textfunktionerna** i DAX inkluderar följande:

* CONCATENTATE
* REPLACE
* SEARCH
* UPPER
* FIXED

Dessa **textfunktioner** fungerar ungefär som Excel-funktionerna med samma namn, så om du känner till hur Excel hanterar textfunktioner ligger du redan steget före. Om inte kan du alltid experimentera med de här funktionerna i Power BI och lära dig mer om hur de beter sig.

## <a name="date-functions"></a>Datumfunktioner
DAX innehåller följande **datumfunktioner**:

* DATE
* HOUR
* NOW
* EOMONTH
* WEEKDAY

Dessa funktioner är användbara för att beräkna och extrahera informationen från *datumvärden* men fungerar inte för tidsinformation, som använder en datumtabell.

> Videoinnehåll tillhandahållet av [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

