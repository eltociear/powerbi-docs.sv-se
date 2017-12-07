Det finns två primära beräkningar som du kan skapa med hjälp av DAX:

* **beräknade kolumner**
* **beräknade mått**

Innan du tar itu med att skapa endera av dessa, är det bra om du har koll på den DAX-syntax för tabeller och kolumner som du måste använda när du skapar **beräknade kolumner** eller **beräknade mått**.

## <a name="dax-table-and-column-name-syntax"></a>DAX-syntax för tabeller och kolumner
Oavsett om du skapar en ny kolumn eller ett nytt mått, så är det viktigt att du känner till det allmänna formatet för tabellnamn i DAX:

    'Table Name'[ColumnName]

Om tabellnamnet innehåller blanksteg (så som visas ovan) måste du placera tabellnamnet inom enkla citattecken. Om tabellnamnet inte innehåller några blanksteg kan du utelämna de enkla citattecknen. Då ser syntaxen ut så här:

    TableName[ColumnName]

Följande bild visar en DAX-formel som skapas i Power BI:

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

Du kan också utelämna tabellnamnet helt och hållet och bara använda kolumnnamnet, men detta är ett dåligt tillvägagångssätt om du vill skapa tydliga funktioner (och därmed en tydlig DAX-kod). Kolumnnamnen måste alltid innehålla hakparenteser.

Vi rekommenderar att du *alltid* gör följande:

* Inga blanksteg i tabellnamn
* Inkludera alltid tabellnamnet i formler (utelämna det inte, även om DAX tillåter det)

## <a name="creating-calculated-columns"></a>Skapa beräknade kolumner
**Beräknade kolumner** är användbara om du vill segmentera eller filtrera efter värdet, eller om du vill ha en beräkning för varje rad i tabellen.

Du kan skapa beräknade kolumner i Power BI Desktop genom att välja **Ny kolumn** på fliken **Modellering**. Det bästa är om du väljer vyn **Data** (snarare än **Rapport** eller **Relationer**), eftersom du kan se den nya kolumn som skapats och eftersom **formelfältet** är ifyllt och redo för din DAX-formel.

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

När du väl har valt knappen **Ny kolumn** fylls **formelfältet** med ett kolumnnamn (som du naturligtvis kan ändra så att de passar din formel) och **=**operatorn, och den nya kolumnen visas i datarutnätet, så som visas i följande bild.

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

De obligatoriska elementen för en beräknad kolumn är följande:

* ett nytt kolumnnamn
* minst en funktion eller minst ett uttryck

Om du refererar till en tabell eller kolumn i en beräknad kolumnformel, så behöver du inte ange någon rad i tabellen – Power BI beräknar kolumnen för den aktuella raden för varje beräkning.

## <a name="creating-calculated-measures"></a>Skapa beräknade mått
Använd ett **beräknat mått** när du beräknar procenttal eller förhållanden, eller när du behöver komplexa aggregeringar. Om du vill skapa ett mått med en DAX-formel, så välj knappen **Nytt mått** på fliken **Modellering**. Än en gång är det bäst att välja vyn **Data** i Power BI Desktop eftersom **formelfältet** då visas och gör det enkelt för dig att skriva din DAX-formel.

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

När du använder **mått** visas en ny måttikon med måttets namn i fönstret **Fält**. **Formelfältet** fylls återigen med namnet på din DAX-formel (den här gången med ditt mått).

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

De obligatoriska elementen för ett beräknat mått är desamma som för en beräknad kolumn:

* ett nytt måttnamn
* minst en funktion eller minst ett uttryck

> Videoinnehåll tillhandahållet av [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

