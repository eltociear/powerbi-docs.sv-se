---
title: Uttryck i Power BI Report Builder
description: Uttryck används mycket i sidnumrerade rapporter i Power BI Paginated Report Builder för att hämta. beräkna, visa, gruppera, sortera, filtrera, parametrisera och formatera data.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d3a72fd967eeb24cfa1093d16c4434447d5fc89d
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840635"
---
# <a name="expressions-in-power-bi-report-builder"></a>Uttryck i Power BI Report Builder
  Uttryck används mycket i sidnumrerade rapporter i Power BI Paginated Report Builder för att hämta. beräkna, visa, gruppera, sortera, filtrera, parametrisera och formatera data. 
  
  Många egenskaper för rapportobjekt kan anges till ett uttryck. Med uttryck kan du kontrollera rapportens innehåll, design och interaktivitet. Uttryck skrivs i Microsoft Visual Basic, sparas i rapportdefinitionen och utvärderas av rapportbearbetaren när du kör rapporten.  
  
 Till skillnad från program som Microsoft Office Excel, där du arbetar med data direkt i ett kalkylblad, arbetar du i en rapport med uttryck som är platshållare för data. För att se faktiska data från de utvärderade uttrycken måste du förhandsgranska rapporten. När du kör rapporten utvärderar rapportbearbetaren varje uttryck genom att kombinera rapportdata och rapportlayoutelement såsom tabeller och diagram.  
  
 När du utformar en rapport anges många uttryck för rapportobjekt åt dig. När du till exempel drar ett fält från datafönstret till en tabellcell på rapportens designyta anges textrutevärdet till ett enkelt uttryck för fältet. I följande bild visar fönstret Rapportdata datamängdsfälten ID, Name, SalesTerritory, Code och Sales. Tre fält har lagts till i tabellen: [Name], [Code] och [Sales]. Notationen [Name] på designytan representerar det underliggande uttrycket `=Fields!Name.Value`.  
  
![Designvyn i Report Builder](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 När du förhandsgranskar rapporten kombinerar rapportbearbetaren tabelldataområdet med faktiska data från dataanslutningen och visar en rad i tabellen för varje rad i resultatuppsättningen.  
  
 Om du vill ange uttryck manuellt markerar du ett objekt på designytan och använder genvägsmenyerna och dialogrutorna för att ange objektets egenskaper. När du ser knappen ***(fx)*** eller värdet `<Expression>` i en listruta innebär det att du kan ange egenskapen till ett uttryck. 
  
##  <a name="Types"></a> Förstå enkla och komplexa uttryck  
 Uttryck börjar med ett likhetstecken (=) och skrivs i Microsoft Visual Basic. Uttryck kan omfatta en kombination av konstanter, operatorer och referenser till inbyggda värden (fält, samlingar och funktioner) samt till extern eller anpassad kod.  
  
 Du kan använda uttryck för att ange värdet för många egenskaper för rapportobjekt. De vanligaste egenskaperna är värden för textrutor och platshållartext. Om en textruta innehåller endast ett uttryck är uttrycket vanligtvis värdet för textrutans egenskap. Om en textruta innehåller flera uttryck är varje uttryck värdet för platshållartexten i textrutan.  
  
 Som standard visas uttryck på rapportdesignytan som *enkla* eller *komplexa uttryck*.  
  
-   **Enkla** Enkla uttryck innehåller en referens till ett enskilt objekt i en inbyggd samling, till exempel ett datamängdsfält, en parameter eller ett inbyggt fält. På designytan visas ett enkelt uttryck inom hakparenteser. Till exempel motsvarar `[FieldName]` det underliggande uttrycket `=Fields!FieldName.Value`. Enkla uttryck skapas automatiskt åt dig när du skapar rapportlayouten och drar objekt från fönstret Rapportdata till designytan. Mer information om de symboler som representerar olika inbyggda samlingar finns i [Förstå prefixsymboler för enkla uttryck](#DisplayText).  
  
-   **Komplexa** Komplexa uttryck innehåller referenser till flera inbyggda referenser, operatorer och funktionsanrop. Ett komplext uttryck visas som <\<Expr>> när uttrycksvärdet omfattar fler än en enkel referens. Du kan visa uttrycket genom att hovra över det och använda knappbeskrivningen. Om du vill redigera uttrycket öppnar du det i dialogrutan **Uttryck**.  
  
 Följande bild visar vanliga enkla och komplexa uttryck för både textrutor och platshållartext.  
  
![Standardformat för Report Builder-uttryck](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 Om du vill visa exempelvärden i stället för text för uttryck använder du formatering på textrutan eller platshållartexten. Följande bild visar rapportdesignytan aktiverad för att visa exempelvärden:  
  
![Exempelformat för Report Builder-uttryck](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="DisplayText"></a> Förstå prefixsymbolerna i enkla uttryck  

Enkla uttryck använder symboler för att ange huruvida referensen är till ett fält, en parameter, en inbyggd samling eller samlingen ReportItems. I följande tabell visas exempel på visningstext och uttryckstext:  
  
|Objekt|Exempel på visningstext|Exempel på uttryckstext|  
|----------|--------------------------|-----------------------------|  
|Datamängdsfält|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|Rapportparametrar|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|Inbyggda fält|`[&ReportName]`|`=Globals!ReportName.Value`|  
|Vanliga tecken som används för att visa text|`\[Sales\]`|`[Sales]`|  
  
##  <a name="References"></a> Skriva komplexa uttryck  
 Uttryck kan innehålla referenser till funktioner, operatörer, konstanter, fält, parametrar, objekt från inbyggda samlingar och inbäddad anpassad kod eller anpassade sammansättningar.  
  
 I följande tabell visas de typer av referenser som du kan inkludera i ett uttryck:  
  
|Referenser|Beskrivning|Exempel|  
|----------------|-----------------|-------------|  
|Konstanter|Beskriver de konstanter som du kan komma åt interaktivt för egenskaper som kräver konstanta värden, till exempel teckenfärg.|`="Blue"`|  
|Operatorer|Beskriver de operatorer som du kan använda för att kombinera referenser i ett uttryck. Till exempel används operatorn **&** för att sammanfoga strängar.|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|Inbyggda samlingar|Beskriver de inbyggda samlingar som du kan inkludera i ett uttryck, till exempel `Fields`, `Parameters` och `Variables`.|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|Inbyggda rapport- och mängdfunktioner|Beskriver de inbyggda funktionerna, till exempel `Sum` eller `Previous`, som du kan komma åt från ett uttryck.|`=Previous(Sum(Fields!Sales.Value))`|  
|Anpassad kod och sammansättningsreferenser i uttryck i Report Builder |Beskriver hur du kan komma åt de inbyggda CLR-klasserna `xref:System.Math` och `xref:System.Convert`, andra CLR-klasser, funktioner i Visual Basic-körningsbibliotek samt metoder från en extern sammansättning.<br /><br /> Beskriver hur du kan komma åt anpassad kod som är inbäddad i din rapport eller kompilera och installera som en anpassad sammansättning på både rapportklienten och rapportservern.|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="Valid"></a> Validera uttryck  
 När du skapar ett uttryck för en specifik egenskap för rapportobjekt beror de referenser som du kan inkludera i ett uttryck på de värden som egenskapen för rapportobjekt kan acceptera och det omfång där egenskapen utvärderas. Till exempel:  
  
-   Som standard beräknar uttrycket [Sum] summan av data som ingår i omfånget vid den tidpunkt då uttrycket utvärderas. För en tabellcell beror omfånget på gruppmedlemskap för rad och kolumn. 
  
-   För värdet för en Font-egenskap måste värdet utvärderas till namnet på ett teckensnitt.  
  
-   Uttryckssyntax valideras vid designtillfället. Validering av uttryckets omfång sker när du publicerar rapporten. För validering som beror på faktiska data kan fel endast identifieras vid körning. Vissa av dessa uttryck producerar #Error som ett felmeddelande i den renderade rapporten. 

## <a name="next-steps"></a>Nästa steg

- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
