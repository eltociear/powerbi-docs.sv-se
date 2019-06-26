---
title: Tips om rapportdesign i Power BI Report Builder
description: Använd följande tips för att utforma dina sidnumrerade rapporter i Power BI Report Builder.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: c1490ff0-5b8a-43c1-8d22-e459395db4f6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d7e232d09eee2a4cfff17d4565443195e6f7f1aa
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "66840359"
---
# <a name="report-design-tips-in-power-bi-report-builder"></a>Tips om rapportdesign i Power BI Report Builder
  Använd följande tips för att utforma dina sidnumrerade rapporter i Power BI Report Builder.  
  
   
  
##  <a name="DesigningReports"></a> Utforma rapporter  
  
-   En väl utformad rapport förmedlar information som leder till åtgärd. Identifiera de frågor som rapporten hjälper till att besvara. Tänk på dessa frågor när du utformar rapporten.  
  
-   För att skapa effektiva datavisualiseringar bör du tänka på hur du vill visa information som är enkel för rapportanvändare att förstå. Välj ett dataområde som passar för de data som du vill visualisera. Till exempel förmedlar diagram sammanfattningar och aggregerad information bättre än en tabell som innehåller många sidor med detaljerad information. Du kan visualisera data från en datamängd i valfritt dataområde, däribland diagram, kartor, indikatorer, miniatyrdiagram och tabelldata i olika rutnätslayouter baserat på en tablix. 
  
-   Om du planerar att leverera rapporten i ett specifikt exportformat bör du testa exportformatet tidigt i utformningen. Funktionsstöd varierar beroende på vilken renderare du väljer.  
  
-   Skapa layouten i steg när du skapar komplexa layouter. Du kan använda rektanglar som containrar för att organisera rapportobjekt. Du kan skapa dataområden direkt på designytan för att maximera ditt arbetsområde och sedan dra varje dataområde till rektangelcontainern när du slutför vart och ett. Genom att använda rektanglar som containrar kan du placera allt dess innehåll i ett enda steg. Rektanglar hjälper även till att kontrollera det sätt som rapportobjekt renderas på varje sida.  
  
-   För att minska oredan i en rapport bör du överväga att använda villkorsstyrd synlighet för specifika rapportobjekt och låta användaren välja om objekten ska visas. Du kan ange synlighet baserat på en parameter eller textruteväxel. Du kan lägga till villkorligt dolda textrutor för att visa interimresultat för uttryck. När en rapport visar oväntade data kan du visa dessa interimresultat för att få hjälp med felsökning av uttryck.  
  
-   När du arbetar med kapslade objekt i tablix-celler eller rektanglar kan du ange olika bakgrundsfärger för containern och de objekt som finns i den. Bakgrundsfärgen är som standard **Ingen färg**. Objekt med en specifik bakgrundsfärg visas genom objekt som har en bakgrundsfärg inställd på **Ingen färg**. Den här tekniken kan hjälpa dig att välja rätt objekt för att ange visningsegenskaper, till exempel kantsynlighet för tablix-celler.  
  
 Mer information om saker du bör överväga när du utformar rapporten finns i [Planera en rapport i Report Builder](report-builder-planning-report.md)).  
  
##  <a name="NamingConventions"></a> Namngivningskonventioner för rapporter, datakällor och datamängder  
  
-   Använd namngivningskonventioner för datakällor och datamängder som dokumenterar datakällan.  
  
    1.  **Datakällor.** Om du inte vill använda en faktisk server eller databas av säkerhetsskäl använder du ett alias som indikerar för användaren var datakällan finns.  
  
    2.  **Datamängder.** Använd ett namn som anger vilken datakälla den är baserad på.  
  
##  <a name="Data"></a> Arbeta med data  
  
-   Som ett första steg hämtar du alla data som du vill arbeta med och som ska visas i fönstret Rapportdata. När du förfinar de frågor som rapporten är utformad för att besvara bör du överväga hur data i rapportdatamängderna ska begränsas till endast det som behövs.  
  
-   I allmänhet bör du endast inkludera data som ska visas i en rapport. Använd frågevariabler i datamängdsfrågor så att användare kan välja vilka data de vill se i rapporten. Om du skapar delade datamängder anger du filter baserat på rapportparametrar för att ge samma funktion.  
  
-   Om du är van vid att skriva frågor är det bra att känna till att du för mellanstora mängder data bör gruppera data i rapporten och inte i frågan. Om du utför all gruppering i frågan tenderar rapporten att bli en presentation av frågeresultatuppsättningen. För visning av aggregerade värden för stora mängder data i ett diagram eller en matris behöver du dock inte inkludera detaljdata.  
  
-   Beroende på dina krav kan du visa namn och platser för rapportdatakällor, kommandotext för datauppsättningsfrågor samt parametervärden i rapporten. Den första fråga som många användare ställer handlar om var data kommer från. För att minska oredan i rapporten kan du villkorligt dölja textrutor med den här typen av information och låta användarna välja om de vill se den. Försök att lägga till den här informationen på den sista sidan i rapporten. Ange synligheten för textrutan baserat på en parameter som användaren kan ändra.  
  
##  <a name="DesignSurface"></a> Interagera med rapportdesignytan  
 Rapportdesignytan är inte WYSIWYG. När du placerar rapportobjekt på designytan påverkar deras relativa plats det sätt som objekt visas på den renderade rapportens sida. Blanksteg bevaras.  
  
-   Använd justeringsguider och layoutknappar för att rikta in och ordna objekt på rapportdesignytan. Du kan till exempel rikta in överdelen eller kanterna på valda objekt, expandera ett objekt så att storleken matchar ett annat objekt eller justera avståndet mellan objekt.  
  
-   Använd piltangenterna för att justera placering och storlek för de valda objekten på designytan. Till exempel är följande tangentkombinationer mycket användbara:  
  
    -   **Piltangenter** Flytta det valda rapportobjektet.  
  
    -   **Ctrl + piltangenter** Knuffa det valda rapportobjektet.  
  
    -   **Ctrl + Skift + piltangenter** Öka eller minska storleken på det valda rapportobjektet.  
  
-   Om du vill lägga till ett objekt i en rektangel använder du musens övre vänstra spets för att peka på den första platsen för objektet i rektangelcontainern. Använd kortkommandon för att placera valda objekt. Rektangeln expanderar automatiskt för att hantera storleken på innehållsobjekten.  
  
-   Om du vill lägga till flera objekt i en tablix-cell lägger du först till en rektangel och sedan objekten.  
  
     Som standard innehåller varje tablix-cell en textruta. När du lägger till en rektangel i en cell ersätter rektangeln textrutan. Placera till exempel kapslade indikatorer i en rektangel i en tablix-cell för att kontrollera hur storleken på ett diagram eller en indikator expanderar när du ändrar höjden på den rad som cellen finns i.  
  
-   Använd **zoomkontrollen** för att justera vyn på designytan. Du kan arbeta med hela sidan eller mindre avsnitt av sidan.  
  
-   För att dra fält från fönstret Rapportdata till fönstret Gruppering bör du undvika att dra fältet över andra rapportobjekt på designytan eftersom detta markerar de andra objekten och avmarkerar tablix-dataområdet. Dra fältet nedåt i fönstret Rapportdata och sedan över till fönstret Gruppera.  
  
###  <a name="Selecting"></a> Välja objekt  
 För att markera det objekt som du vill ha på rapportdesignytan använder du Esc-tangenten, snabbmenyn via högerklick, fönstret Egenskaper samt fönstret Gruppering.  
  
-   -   Tryck på ESC för att bläddra igenom stacken med rapportobjekt som upptar samma område på designytan.  
  
    -   På vissa rapportobjekt kan du prova att använda snabbmenyn via högerklick för att markera rapportobjektet eller den del av rapportobjektet som du vill ha.  
  
    -   I fönstret Egenskaper visas egenskaper för den aktuella markeringen.  
  
    -   Om du vill arbeta med radgrupper och kolumngrupper i ett tablix-dataområde väljer du gruppen från fönstret Gruppera.  

  
##  <a name="ReportItems"></a> Arbeta med specifika typer av rapportobjekt  
  
###  <a name="Parameters"></a> Arbeta med parametrar  
  
-   Det huvudsakliga syftet med rapportparametrarna är att filtrera data vid datakällan och hämta bara det som behövs för rapporten.  
  
-   För rapportparametrar hittar du en balans mellan att ge interaktivitet och hjälpa användarna att få det resultat de vill ha. Du kan till exempel ange standardvärden för en parameter till värden som du vet är populära.  
  
###  <a name="Text"></a> Arbeta med text  
  
-   När du klistrar in flera rader i en textruta läggs texten som en enda textkörning. Varje textkörning kan endast formateras som en enhet. Om du vill formatera varje rad oberoende av varandra infogar du en ny rad genom att trycka på Retur i textkörningen vid behov. Du kan sedan använda formatering och format för varje oberoende textrad i textrutan.  
  
-   Du kan ange egenskaper och åtgärder på en textruta eller platshållartext i textrutan. Om det bara finns en enda rad med text är det mer effektivt att ange egenskaper för textrutan än för texten.  
  
###  <a name="Expressions"></a> Arbeta med uttryck  
  
-   Förstå enkla och komplexa uttrycksformat. Du kan skriva enkla uttrycksformat direkt i textrutor, egenskaper i fönstret Egenskap eller på platser i dialogrutor som accepterar ett uttryck.
  
-   När du skapar ett uttryck hjälper det dig att skapa varje del oberoende av varandra och verifiera dess värde. Du kan sedan kombinera alla delar i ett slutgiltigt uttryck. En användbar teknik är att lägga till en textruta i en matriscell, visa varje del av uttrycket och ange villkorsstyrd synlighet för textrutan. För att kontrollera kantstil och -färg när textrutan är dolt placerar du först textrutan i en rektangel och anger sedan kantstil- och färg för rektangeln så att de matchar matrisen.  
  
###  <a name="Indicators"></a> Arbeta med indikatorer  
  
-   Som standard visar en indikator minst tre tillstånd. När du har lagt till en indikator i en rapport kan du konfigurera den genom att lägga till eller ta bort tillstånd. Du kan göra visningen enklare för användarna genom att välja en indikator som varierar vad gäller både färg och form.  
  
##  <a name="Rendering"></a> Kontrollera renderingen av rapportobjekt på rapportsidan  
  
-   I rapportdesignytan växer rapportobjekt för att passa innehållet från tillhörande datamängd, uttryck, underrapport eller text.  
  
    -   När du placerar ett objekt på rapportsida blir avståndet mellan objektet och alla objekt som börjar till höger om objektet det minimiavstånd som måste upprätthållas när rapportobjektet växer vågrätt. På liknande sätt blir avståndet mellan ett objekt och objektet ovanför det ett minimiavstånd som måste upprätthållas när det översta objektet växer lodrätt.  
  
    -   Ett objekt i en rapport växer för att passa sina data och trycker bort peer-objekt (objekt i samma överordnade container) via följande regler:  
  
    -   Varje objekt flyttas ned att upprätthålla minimiavståndet mellan objektet självt och de objekt som slutar ovanför det.  
  
    -   Varje objekt flyttas till höger att upprätthålla minimiavståndet mellan objektet självt och de objekt som slutar till vänster om det. För system med höger-till-vänster-layout flyttas varje objekt för att upprätthålla minimiavståndet mellan objektet självt och de objekt som slutar till höger om det.  
  
    -   Containrar expanderar för att passa underordnade objekts tillväxt. För ett valt objekt identifierar egenskapen Överordnad i fönstret Egenskaper containern för det objektet. Du kan även använda fönstret Dokumentdisposition för att se inneslutningshierarkin för rapportobjekt.  
  
    -   Verktygsfältet **Layout** innehåller flera knappar för att anpassa kanter, centrering och avstånd för rapportobjekt. För att verktygsfältet **Layout** går du till menyn **Visa**, pekar på **Verktygsfält** och klickar sedan på **Layout**.  
  
-   Om du planerar att spara rapporten som en PDF-fil måste rapportbredden explicit anges till ett värde som ger det resultat du vill ha i filformatet för export. Till exempel kan du ange rapportsidans bredd till exakt 7,9375 tum och vänster- och högermarginalerna till 0,5 tum.  
  
-   Använd **Utskriftslayout** och **Utskriftsformat** i rapportgranskarens verktygsfält för att rendera en rapport i en utskriftskompatibel vy. Gör följande för att ta bort oönskade vågräta sidor:  
  
    1.  Ta bort alla extra blanksteg mellan dataområden och på rapportens kanter.  
  
    2.  Minska sidmarginaler i dialogrutan **Rapportegenskaper**.  
  
    3.  Använd **Rektanglar** som containrar för att kontrollera det sätt som rapportobjekt renderas på.  
  
    4.  I kolumnrubriker ändrar du textruteegenskapen WritingMode till att använda lodrät text.  
  
 Kombinationen av det här beteendet, egenskaper för bredd och höjd för rapportobjekt, storleken på rapportinnehållet, definitionen för sidhöjd och sidbredd, marginalinställningarna för den överordnade rapporten samt renderarspecifikt stöd för sidindelning avgör tillsammans vilka rapportobjekt som passar ihop på en renderad sida. 
 
## <a name="next-steps"></a>Nästa steg

- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)  
