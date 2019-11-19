---
title: Uttrycksexempel i Power BI Report Builder
description: Uttryck används ofta i sidnumrerade rapporter i Power BI Paginated Report Builder för att kontrollera innehåll och rapportens utseende.
ms.date: 10/21/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 06847956eae4dfefc7cff75b5a360fbb8b892c39
ms.sourcegitcommit: d173e22f5a3e76717adfaa573ea391bde0338ffe
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728549"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Uttrycksexempel i Power BI Report Builder
Uttryck används ofta i sidnumrerade rapporter i Power BI Paginated Report Builder för att kontrollera innehållets och rapportens utseende. Uttryck skrivs i Microsoft Visual Basic och kan använda inbyggda funktioner, anpassad kod, rapport- och gruppvariabler samt användardefinierade variabler. Uttryck inledas med ett likhetstecken (=).   

Det här avsnittet innehåller exempel på uttryck som kan användas för ofta förekommande uppgifter i en rapport.  
  
-   [Visual Basic-funktioner](#VisualBasicFunctions) Exempel för datum, sträng, konvertering och villkorsstyrda Visual Basic-funktioner.  
  
-   [Rapportfunktioner](#ReportFunctions) Exempel för aggregat och andra inbyggda rapportfunktioner.  
  
-   [Utseende på rapportdata](#AppearanceofReportData) Exempel för att ändra utseendet på en rapport.  
  
-   [Egenskaper](#Properties) Exempel för att ange egenskaper för rapportobjekt i syfte att kontrollera format eller synlighet.  
  
-   [Parametrar](#Parameters) Exempel på användning av parametrar i ett uttryck.  
  
-   [Anpassad kod](#CustomCode) Exempel på inbäddad anpassad kod.  
  
Mer information om enkla och komplexa uttryck, var du kan använda uttryck och samt de typer av referenser som du kan inkludera i uttryck finns i ämnena under [Uttryck i Power BI Report Builder](report-builder-expressions.md). 
  
## <a name="functions"></a>Functions  
 Många uttryck rapporter innehåller funktioner. Du kan formatera data, tillämpa logik och komma åt rapportmetadata med hjälp av dessa funktioner. Du kan skriva uttryck som använder funktioner från Microsoft Visual Basic-körningsbiblioteket samt från namnrymderna `xref:System.Convert` och `xref:System.Math`. Du kan lägga till referenser i funktioner i anpassad kod. Du kan även använda klasser från Microsoft .NET Framework, däribland `xref:System.Text.RegularExpressions`.  
  
##  <a name="VisualBasicFunctions"></a> Visual Basic-funktioner  
 Du kan använda Visual Basic-funktioner för att ändra data som visas i textrutor eller som används för parametrar, egenskaper eller andra delar av rapporten. Det här avsnittet innehåller exempel som visar några av dessa funktioner. Mer information finns i [Medlemmar i Visual Basic-körningsbiblioteket](https://go.microsoft.com/fwlink/?LinkId=198941) på MSDN.  
  
 .NET Framework innehåller många alternativ för anpassade format, till exempel för specifika datumformat. Mer information finns i [Formateringstyper](/dotnet/standard/base-types/formatting-types).  
  
### <a name="math-functions"></a>Matematikfunktioner  
  
-   Funktionen **Round** (Avrunda) är användbar för att avrunda siffror till närmaste heltal. Följande uttryck avrundar 1,3 till 1:  
  
    ```  
    = Round(1.3)  
    ```  
  
     Du kan även skriva ett uttryck för att avrunda ett värde till en multipel som du anger, på ett sätt som liknar funktionen **MAVRUNDA** i Excel. Multiplicera värdet med en faktor som skapar ett heltal, avrunda talet och dela sedan med samma faktor. För att till exempel avrunda 1,3 till närmaste multipel av 0,2 (1,4) använder du följande uttryck:  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="DateFunctions"></a> Datumfunktioner  
  
-   Funktionen **Today** (I dag) ger dagens datum. Det här uttrycket kan användas i en textruta för att visa datumet i rapporten eller i en parameter för att filtrera data baserat på det aktuella datumet.  
  
    ```  
    =Today()  
    ```  
  
-   Använd funktionen **DateInterval** för att hämta en viss del av ett datum. Här är några giltiga **DateInterval**-parametrar:

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    Till exempel visar det här uttrycket veckonumret under det aktuella året för dagens datum:
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   Funktionen **DateAdd** är användbar för att tillhandahålla ett datumintervall baserat på en enda parameter. Följande uttryck ger ett datum som är sex månader efter datumet från en parameter som heter *StartDate*.  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   Funktionen **Year** (År) visar året för ett visst datum. Du kan använda det här för att gruppera datum eller för att visa året som en etikett för en uppsättning med datum. Det här uttrycket ger året för en viss grupp av säljorderdatum. Funktionen **Month** (Månad) och andra funktioner kan också användas för att ändra datum. Mer information finns i Visual Basic-dokumentationen.  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   Du kan kombinera funktioner i ett uttryck för att anpassa formatet. Följande uttryck ändrar formatet för ett datum i formatet månad-dag-år till månad-vecka-veckonummer. Exempel: 12/23/2009 till december vecka 3:  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     När det här uttrycket används som ett beräknat fält i en datamängd kan du använda det i ett diagram för att aggregera värden efter vecka i varje månad.  
  
-   Följande uttryck formaterar SellStartDate-värdet som MMM-ÅÅ. Fältet SellStartDate är en datetime-datatyp.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   Följande uttryck formaterar SellStartDate-värdet som dd/MM/åååå. Fältet SellStartDate är en datetime-datatyp.  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   Funktionen **CDate** konverterar värdet till ett datum. Funktionen **Now** (Nu) returnerar ett datumvärde som innehåller aktuellt datum och tid enligt systemet. **DateDiff** returnerar ett Long-värde som anger antalet tidsintervall mellan två Date-värden (datum).  
  
     I följande exempel visas startdatumet för det aktuella året  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   I följande exempel visar startdatumet för den föregående månaden baserat på den aktuella månaden.  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   Följande uttryck genererar intervallåren mellan SellStartDate och LastReceiptDate. De här fälten finns i två olika datamängder, DataSet1 och DataSet2.  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   Funktionen **DatePart** returnerar ett Integer-värde (heltal) som innehåller den angivna komponenten i ett visst Date-värde. Följande uttryck returnerar året för det första värdet för SellStartDate i DataSet1. Datamängdens omfång anges eftersom det finns flera datamängder i rapporten.  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   Funktionen **DateSerial** returnerar ett Date-värde (datum) som representerar ett angivet år, månad och dag med tidsinformationen angiven till midnatt. I följande exempel visar slutdatumet för den föregående månaden baserat på den aktuella månaden.  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   Följande uttryck visar olika datum baserat på ett datumparametervärde som väljs av användaren.  
  
|Exempelbeskrivning|Exempel|  
|-------------------------|-------------|  
|Igår|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|Två dagar sedan|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|En månad sedan|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|Två månader sedan|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|Ett år sedan|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|Två år sedan|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="StringFunctions"></a> Strängfunktioner  
  
-   Kombinera flera fält genom att använda sammanfogningsoperatorer och Visual Basic-konstanter. Följande uttryck returnerar två fält, vart och ett på en separat rad i samma textruta:  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   Formatera datum och siffror i en sträng med funktionen **Format**. Följande uttryck visar värdena för parametrarna *StartDate* (Startdatum) och *EndDate* (Slutdatum) i långt datumformat:  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     Om textrutan endast innehåller ett datum eller ett tal bör du använda egenskapen Format för textrutan för formatering i stället för funktionen **Format** i textrutan.  
  
-   Funktionerna **Right**, **Len** och **InStr** är användbara för att returnera en understräng, till exempel att trimma *DOMÄN*\\*användarnamn* till bara användarnamnet. Följande uttryck returnerar delen av strängen till höger om ett omvänt snedstrecktecken (\\) från en parameter som heter *User* (användaren):  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     Följande uttryck resulterar i samma värde som det tidigare uttrycket med hjälp av medlemmar i .NET Framework-klassen `xref:System.String` i stället för Visual Basic-funktioner:  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   Visa de valda värdena från en flervärdesparameter. I följande exempel används funktionen **Join** för att sammanfoga de valda värdena för parametern *MySelection* till en enda sträng som kan anges som ett uttryck för värdet för en textruta i ett rapportobjekt:  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     I följande exempel utförs samma som i exemplet ovan, och en textsträng visas före listan med valda värden.  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   **Regex**-funktionerna från .NET Framework `xref:System.Text.RegularExpressions` är användbara för att ändra formatet för befintliga strängar, till exempel formatering av ett telefonnummer. I följande exempel används funktionen **Replace** (Ersätt) för att ändra formatet för ett tiosiffrigt telefonnummer i ett fält från ”*nnn*-*nnn*-*nnnn*” till ”(*nnn*) *nnn*-*nnnn*”:  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  Kontrollera att värdet för Fields!Phone.Value inte innehåller några extra blanksteg och är av typen `xref:System.String`.  
  
### <a name="lookup"></a>Lookup  
  
-   Genom att ange ett nyckelfält kan du använda funktionen **Lookup** för att hämta ett värde från en datamängd för en en-till-en-relation, till exempel ett nyckel/värde-par. Följande uttryck visar produktnamnet från en datamängd (”Product”) givet det produkt-ID som ska matchas:  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   Genom att ange ett nyckelfält kan du använda funktionen **LookupSet** för att hämta en uppsättning värden från en datamängd för en en-till-många-relation. Exempelvis kan en person ha flera telefonnummer. I följande exempel antar vi att datamängden PhoneList innehåller ett person-ID och ett telefonnummer på varje rad. **LookupSet** returnerar en matris med värden. Följande uttryck kombinerar returvärdena till en enskild sträng och visar listan över telefonnummer för den person som anges av ContactID:  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="ConversionFunctions"></a> Konverteringsfunktioner  
 Du kan använda Visual Basic-funktioner för att konvertera ett fält från en datatyp till en annan datatyp. Konverteringsfunktioner kan användas för att konvertera standarddatatypen för ett fält till den datatyp som behövs för att utföra beräkningar eller kombinera text.  
  
-   Följande uttryck konverterar konstanten 500 till typen Decimal för att jämföra den med en Transact-SQL-pengadatatyp i fältet Value (värde) för ett filteruttryck.  
  
    ```  
    =CDec(500)  
    ```  
  
-   Följande uttryck visar antalet värden som har valts för flervärdesparametern *MySelection*.  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="DecisionFunctions"></a> Beslutsfunktioner  
  
-   Funktionen **Iif** returnerar ett av två värden beroende på om uttrycket är sant eller inte. Följande uttryck använder funktionen **Iif** för att returnera det booleska värdet **True** (Sant) om värdet för `LineTotal` överskrider 100. Annars returnerar det **False** (Falskt):  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   Använd flera **IIF**-funktioner (kallas även ”kapslade IIF:er”) för att returnera ett av tre värden beroende på värdet för `PctComplete`. Följande uttryck kan placeras i fyllningsfärgen för en textruta för att ändra bakgrundsfärgen beroende på värdet i textrutan.  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     Värden större än eller lika med 10 visas med en grön bakgrund, mellan 1 och 9 visas med blå bakgrund och mindre än 1 visas med en röd bakgrund.  
  
-   Ett annat sätt att få samma funktionalitet är att använda funktionen **Switch** (Växla). Funktionen **Switch** är användbar när du har tre eller fler villkor att testa. Funktionen **Switch** returnerar det värde som är associerat med det första uttrycket i en serie som utvärderas till sant:  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     Värden större än eller lika med 10 visas med en grön bakgrund, mellan 1 och 9 visas med blå bakgrund, lika med 1 visas med en gul bakgrund och 0 eller mindre visas med en röd bakgrund.  
  
-   Testa värdet för fältet `ImportantDate` och returnera ”Röd” om det är mer än en vecka gammalt och ”Blå” i annat fall. Det här uttrycket kan användas för att kontrollera egenskapen Color (Färg) i en textruta i ett rapportobjekt:  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   Testa värdet för fältet `PhoneNumber` och returnera ”Inget värde” om det är **null** (**Nothing** (Inget) i Visual Basic); returnera annars värdet för telefonnummer. Det här uttrycket kan användas för att kontrollera värdet för en textruta i ett rapportobjekt.  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   Testa värdet för fältet `Department` och returnera antingen ett namn på underrapport eller **null** (**Nothing** (Inget) i Visual Basic). Det här uttrycket kan användas för villkorsstyrda underrapporter med visning av detaljerad information.  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   Testa om ett fältvärde är null. Det här uttrycket kan användas för att kontrollera egenskapen **Hidden** (Dold) för ett bildrapportobjekt. I följande exempel visas den bild som anges av fältet [LargePhoto] endast om värdet för fältet inte är null.  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   Funktionen **MonthName** returnerar ett strängvärde som innehåller namnet på den angivna månaden. I följande exempel visar NA i fältet Month (Månad) när fältet innehåller värdet 0.  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="ReportFunctions"></a> Rapportfunktioner  
 I ett uttryck kan du lägga till en referens till ytterligare rapportfunktioner som ändrar data i en rapport. Det här avsnittet innehåller exempel för två av dessa funktioner. 
  
###  <a name="Sum"></a> Sum  
  
-   Funktionen **Sum** kan summera värdena i en grupp eller ett dataområde. Den här funktionen kan vara användbar i huvudet eller foten för en grupp. Följande uttryck visar summan av data i gruppen eller dataområdet Order:  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   Du kan även använda funktionen **Sum** för villkorsstyrda aggregatberäkningar. Om en datamängd till exempel har ett fält som heter State (Tillstånd) med de möjliga värdena Not Started (Ej påbörjad), Started (Påbörjad) och Finished (Slutförd) beräknar följande uttryck aggregatsumman för endast värdet Finished när det placeras i ett grupphuvud:  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="RowNumber"></a> RowNumber  
  
-   När funktionen **RowNumber** (Radnummer) används i en textruta i ett dataområde visar den radnumret för varje instans av den textruta där uttrycket visas. Den här funktionen kan användas till att numrera rader i en tabell. Den kan även vara användbar för mer avancerade uppgifter, till exempel att ge sidbrytningar baserat på antalet rader. Mer information finns i [Sidbrytningar](#PageBreaks) i det här ämnet.  
  
     Det omfång som du anger för **RowNumber** kontrollerar när omnumrering börjar. Nyckelordet **Nothing** (Inget) anger att funktionen börjar räkna från den första raden i det yttersta dataområdet. Om du vill att räkningen ska börja i kapslade dataområden använder du namnet på dataområdet. Om du vill att räkningen ska börja i en grupp använder du namnet på gruppen.  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="AppearanceofReportData"></a> Utseendet på rapportdata  
 Du kan använda uttryck för att ändra hur data visas i en rapport. Du kan till exempel visa värdena för två fält i en enda textruta, visa information om rapporten eller påverka hur sidbrytningar infogas i rapporten.  
  
###  <a name="PageHeadersandFooters"></a> Sidhuvuden och sidfötter  
 När du skapar en rapport vill du kanske visa namnet på rapporten och sidnumret i rapportsidfoten. Det kan du göra med hjälp av följande uttryck:  
  
-   Följande uttryck ger namnet på rapporten och den tid då den kördes. Det kan placeras i en textruta i rapportsidfoten eller i rapportens brödtext. Tiden formateras med .NET Framework-formateringssträngen för kort datum:  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   När följande uttryck placeras i en textruta i sidfoten för en rapport ger det sidnumret och totalt antal sidor i rapporten:  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 I följande exempel beskrivs hur de första och sista värdena från en sida ska visas i sidhuvudet, på ett sätt som liknar en katalogvisning. Exemplet förutsätter ett dataområde som innehåller en textruta med namnet `LastName`.  
  
-   När följande uttryck placeras i en textruta på vänster sida av sidhuvudet ger det första värdet för textrutan `LastName` på sidan:  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   När följande uttryck placeras i en textruta på höger sida av sidhuvudet ger det sista värdet för textrutan `LastName` på sidan:  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 I följande exempel beskrivs hur du visar sidans summa. Exemplet förutsätter ett dataområde som innehåller en textruta med namnet `Cost`.  
  
-   När följande uttryck placeras i sidhuvudet eller sidfoten ger det summan av värdena i textrutan `Cost` för sidan:  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  Du kan referera till endast ett rapportobjekt per uttryck i ett sidhuvud eller en sidfot. Du kan även referera till textrutans namn, men inte det faktiska datauttrycket i textrutan, i sidhuvud- och sidfotsuttryck.  
  
###  <a name="PageBreaks"></a> Sidbrytningar  
 I vissa rapporter vill du kanske placera en sidbrytning i slutet av ett angivet antal rader i stället för, eller utöver, i grupper eller rapportobjekt. Det gör du genom att skapa en grupp som innehåller de grupper eller informationsposter du vill ha, lägga till en sidbrytning i gruppen och sedan lägga till ett grupputtryck för att gruppera efter ett angivet antal rader.  
  
-   När följande uttryck placeras i grupputtrycket tilldelar det ett tal till varje uppsättning med 25 rader. När en sidbrytning definieras för gruppen resulterar det här uttrycket i en sidbrytning var 25:e rad.  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     Om du vill tillåta användaren att ange ett värde för antalet rader per sida skapar du en parameter med namnet `RowsPerPage` och baserar grupputtrycket på parametern, såsom det visas i följande uttryck:  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="Properties"></a> Egenskaper  
 Uttryck används inte bara för att visa data i textrutor. De kan även användas för att ändra hur egenskaper tillämpas på rapportobjekt. Du kan ändra stilinformation för ett rapportobjekt eller ändra dess synlighet.  
  
###  <a name="Formatting"></a> Formatering  
  
-   När följande uttryck används i egenskapen Color (Färg) för en textruta ändras färgen på texten beroende på värdet för fältet `Profit`:  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     Du kan även använda Visual Basic-objektvariabeln `Me`. Den här variabeln är ett annat sätt att referera till värdet för en textruta.  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   När följande uttryck används i egenskapen BackgroundColor (Bakgrundsfärg) för ett rapportobjekt i ett dataområde växlar bakgrundsfärgen för varje rad mellan ljusgrön och vit:  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     Om du använder ett uttryck för ett angivet omfång behöver du kanske ange datamängden för mängdfunktionen:  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  Tillgängliga färger kommer från .NET Framework KnownColor-uppräkningen.  
  
### <a name="chart-colors"></a>Diagramfärger  
 Om du vill ange färger för ett formdiagram kan du använda anpassad kod för att kontrollera den ordning med vilken färger mappas till datapunktsvärden. Detta hjälper dig att använda konsekventa färger för flera diagram som har samma kategorigrupper. 
  
###  <a name="Visibility"></a> Synlighet  
 Du kan visa och dölja objekt i en rapport med hjälp av synlighetsegenskaper för rapportobjektet. I ett dataområde som en tabell kan du till en början dölja rader med detaljerad information baserat på värdet i ett uttryck.  
  
-   När följande uttryck används för inledande synlighet för rader med detaljerad information i en grupp visar det rader med detaljerad information för all försäljningen som överstiger 90 procent i fältet `PctQuota`:  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   När följande uttryck anges i egenskapen Hidden (Dold) i en tabell visar det tabellen endast om den innehåller fler än 12 rader:  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   När följande uttryck anges i egenskapen **Hidden** (Dold) för en kolumn visar det kolumnen endast om fältet finns i rapportdatamängden efter att data har hämtats från datakällan:  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="Hyperlinks"></a> URL:er  
 Du kan anpassa URL:er med hjälp av rapportdata och även villkorligt kontrollera huruvida URL:er läggs till som en åtgärd för en textruta.  
  
-   När följande uttryck används som en åtgärd i en textruta genererar det en anpassad URL som anger datamängdsfältet `EmployeeID` som en URL-parameter.  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   Följande uttryck styr villkorligt huruvida en URL ska läggas till i en textruta. Det här uttrycket är beroende av en parameter med namnet `IncludeURLs` som gör att användaren kan bestämma huruvida aktiva URL:er ska användas i en rapport. Det här uttrycket anges som en åtgärd i en textruta. Genom att ange parametern till False (Falskt) och sedan visa rapporten kan du exportera rapporten till Microsoft Excel utan hyperlänkar.  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
##  <a name="ReportData"></a> Rapportdata  
 Uttryck kan användas för att ändra de data som används i rapporten. Du kan referera till parametrar och annan rapportinformation. Du kan även ändra den fråga som används för att hämta data för rapporten.  
  
###  <a name="Parameters"></a> Parametrar  
 Du kan använda uttryck i en parameter för att variera standardvärdet för parametern. Du kan till exempel använda en parameter för att filtrera data till en viss användare baserat på det användar-ID som används för att köra rapporten.  
  
-   När följande uttryck används som standardvärdet för en parameter samlar det in användar-ID för den person som kör rapporten:  
  
    ```  
    =User!UserID  
    ```  
  
-   Om du vill referera till en parameter i en frågeparameter, ett filteruttryck, en textruta eller något annat område i rapporten använder du den globala samlingen **Parameters** (Parametrar). Det här exemplet förutsätter att parametern heter *Department* (Avdelning):  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   Parametrar kan skapas i en rapport men anges till att vara dolda. När rapporten körs på rapportservern visas inte parametern i verktygsfältet, och rapportläsaren kan inte ändra standardvärdet. Du kan använda en dold parameter som angetts till ett standardvärde som en anpassad konstant. Du kan använda det här värdet i valfritt uttryck, däribland fältuttryck. Följande uttryck identifierar det fält som anges av standardparametervärdet för parametern med namnet *ParameterField*:  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="CustomCode"></a> Anpassad kod  
 Du kan använda anpassad kod som är inbäddad i en rapport. 
  
### <a name="using-group-variables-for-custom-aggregation"></a>Använda gruppvariabler för anpassad aggregering  
 Du kan initiera värdet för en gruppvariabel som är lokal för ett visst gruppomfång och sedan inkludera en referens till den variabeln i uttryck. Ett sätt att använda en gruppvariabel med anpassad kod är att implementera ett anpassat aggregat. 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>Undertrycka nullvärden eller nollvärden vid körning  
 Vissa värden i ett uttryck kan utvärderas till null eller odefinierat vid tiden för rapportbearbetning. Detta kan ge upphov till körningsfel som gör att **#Error** visas i textrutan i stället för det utvärderade uttrycket. Funktionen **IIF** är särskilt känslig för det här beteendet eftersom varje del av **IIF**-instruktionen, till skillnad från en If-Then-Else-instruktion, utvärderas (inklusive funktionsanrop) innan den skickas till den rutin som testar för **sant** eller **falskt**. Instruktionen `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` genererar **#Error** i den återgivna rapporten om `Fields!Sales.Value` är NOTHING (Inget).  
  
 Undvik det här problemet genom att använda någon av följande strategier:  
  
-   Ange täljaren till 0 och nämnaren till 1 om värdet för fältet B är 0 eller odefinierat. Annars anger du täljaren till värdet för fältet A och nämnaren till värdet för fältet B.  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   Använd en anpassad kodfunktion för att returnera värdet för uttrycket. I följande exempel returneras den procentuella skillnaden mellan ett aktuellt värde och ett tidigare värde. Detta kan användas för att beräkna skillnaden mellan två på varandra följande värden, och det hanterar extremfallet för den första jämförelsen (när det inte finns något tidigare värde) och fall där antingen det tidigare värdet eller det aktuella värdet är **null** (**Nothing** (Inget) i Visual Basic).  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     Följande uttryck visar hur du anropar den här anpassade koden från en textruta för containern ”ColumnGroupByYear” (grupp eller dataområde).  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     Detta bidrar till att undvika körningsundantag. Du kan nu använda ett uttryck som `=IIF(Me.Value < 0, "red", "black")` i egenskapen **Color** (Färg) för textrutan för att villkora visningstexten baserat på huruvida värdena är större eller mindre än 0.  
  
## <a name="next-steps"></a>Nästa steg

- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
