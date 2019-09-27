---
title: Automatiserad maskininlärning i Power BI (förhandsversion)
description: Lär dig hur du använder automatiserad maskininlärning (AutoML) i Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 894e92687a6283ce71b253bd4dc635aca0c4673f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236837"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Automatiserad maskininlärning i Power BI (förhandsversion)

Med automatiserad maskininlärning (AutoML) för dataflöden kan affärsanalytiker träna, validera och anropa maskininlärningsmodeller direkt i Power BI. Det innehåller en enkel upplevelse för skapande av en ny ML-modell (maskininlärningsmodell) där analytiker kan använda sina dataflöden för att ange indata för träning av modellen. Tjänsten extraherar automatiskt de mest relevanta egenskaperna, väljer en lämplig algoritm samt justerar och validerar ML-modellen. När en modell har tränats skapar Power BI automatiskt en rapport med resultatet av valideringen som förklarar prestanda och resultat för analytiker. Modellen kan sedan anropas på alla nya eller uppdaterade data i dataflödet.

![Skärmen för maskininlärning](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Automatiserad maskininlärning är endast tillgängligt för dataflöden som värdhanteras på Power BI Premium och inbäddade kapaciteter. I den här förhandsversionen ger AutoML dig möjligheten att träna maskininlärningsmodeller för modeller för binär förutsägelse, klassificering och regression.

## <a name="working-with-automl"></a>Arbeta med AutoML

[Power BI-dataflöden](service-dataflows-overview.md) erbjuder dataförberedelse med självbetjäning för stordata. Med AutoML kan du använda ditt arbete med dataförberedelse vid skapandet av maskininlärningsmodeller direkt i Power BI.

AutoML i Power BI gör att dataanalytiker kan använda dataflöden till att skapa maskininlärningsmodeller med en förenklad upplevelse där endast kunskap om Power BI behövs. Merparten av dataforskningen bakom skapandet av ML-modeller automatiseras av Power BI, med skyddsräcken som säkerställer att den resulterande modellen är av god kvalitet samt synlighet som ger dig fullständig insikt i den process som används vid skapandet av din ML-modell.

AutoML har stöd för skapandet av modeller för **binär förutsägelse**, **klassificering** och **regression** för dataflöden. Dessa är typer av övervakade maskininlärningsmodeller, vilket innebär att de lär sig från kända resultat från tidigare observationer för att förutsäga resultatet av andra observationer. Indatamängden för träning av en AutoML-modell är en uppsättning poster som **märks** med de kända resultaten.

AutoML i Power BI integrerar [automatiserad maskininlärning](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) från [tjänsten Azure Machine Learning ](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) för att skapa dina ML-modeller. Du behöver dock ingen Azure-prenumeration för att använda AutoML i Power BI. Processen med att träna och värdhantera ML-modeller hanteras helt av Power BI-tjänsten.

När en maskininlärningsmodell har tränats genererar AutoML automatiskt en Power BI-rapport som förklarar ML-modellens sannolika prestanda. AutoML betonar förklarbarhet genom att framhäva de främsta influerarna bland dina indata som påverkar de förutsägelser som modellen returnerar. Rapporten innehåller även nyckelmått för modellen, beroende på vilken typ av ML-modell som används.

På andra sidor i den genererade rapporten finns en statistisk sammanfattning av modellen och träningsinformationen. Den statistiska sammanfattningen är intressant för användare som vill se standardmässiga dataforskningsmått för modellens prestanda. Träningsinformationen sammanfattar alla iterationer som kördes för att skapa modellen samt associerade modelleringsparametrar. Den beskriver även hur alla indata användes för att skapa ML-modellen.

Du kan sedan tillämpa ML-modellen på dina data för poängsättning. När dataflödet uppdateras tillämpas förutsägelserna från ML-modellen automatiskt på dina data. Power BI innehåller även en individualiserad förklaring för varje specifik förutsägelsepoäng som ML-modellen skapar.

## <a name="creating-a-machine-learning-model"></a>Skapa en maskininlärningsmodell

I det här avsnittet beskrivs hur du skapar en AutoML-inlärningsmodell. 

### <a name="data-prep-for-creating-an-ml-model"></a>Förbereda data för skapandet av en ML-modell

För att skapa en maskininlärningsmodell i Power BI måste du först skapa ett dataflöde för dina data med informationen om historiska utfall, som används för träning av ML-modellen. Mer information om hur du konfigurerar dataflödet finns i [Dataförberedelser med självbetjäning i Power BI](service-dataflows-overview.md).

I den aktuella versionen använder Power BI endast data från en enda entitet för att träna ML-modellen. Om dina historiska data består av flera entiteter måste du därför manuellt kombinera data till en enskild dataflödesentitet. Du bör även lägga till beräknade kolumner för eventuella affärsmått som kan vara starka förutsägande faktorer för det resultat du försöker förutsäga.

AutoML har specifika datakrav för träning av en maskininlärningsmodell. Dessa krav beskrivs i avsnitten nedan baserat på respektive modelltyp.

### <a name="configuring-the-ml-model-inputs"></a>Konfigurera ML-modellens indata

Du skapar en AutoML-modell genom att välja ML-ikonen i kolumnen **Åtgärder** i dataflödesentiteten med historiska data och sedan välja **Lägg till en maskininlärningsmodell**.

![Lägga till en maskininlärningsmodell](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

En förenklad upplevelse startas med en guide som vägleder dig genom processen för att skapa ML-modellen. Guiden innehåller följande enkla steg.

1. Välj entiteten med data för historiska utfall samt det fält som du vill ha en förutsägelse för
2. Välj en modelltyp baserat på den typ av förutsägelse du vill ha
3. Välj de indata som du vill att modellen ska använda som förutsägande signaler
4. Namnge modellen och spara konfigurationen

Fältet för historiska utfall identifierar märkningsattributet för träning av ML-modellen enligt följande bild.

![Välja data för historiska utfall](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

När du anger fältet för historiska utfall analyserar AutoML märkningsdata för att identifiera de typer av ML-modeller som kan tränas för dessa data och föreslår den ML-modelltyp som mest sannolikt kan tränas. 

> [!NOTE]
> Vissa modelltyper stöds kanske inte för de data som du har valt.

AutoML analyserar även alla fält i den valda entiteten och föreslår de indata som kan användas för träning av ML-modellen. Den här processen är ungefärlig och baseras på statistisk analys. Därför bör du granska de indata som används. Indata som är beroende av fältet för historiska utfall (eller märkningsfältet) bör inte används för träning av ML-modellen eftersom de påverkar dess prestanda.

![Anpassa indatafälten](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

I det sista steget kan du namnge modellen och spara dess inställningar.

I det här skedet uppmanas du att uppdatera dataflödet, vilket inleder ML-modellens träningsprocess.

### <a name="ml-model-training"></a>Träning av ML-modell

Träning av AutoML-modeller är en del av dataflödesuppdateringen. AutoML förbereder först dina data för träning.

AutoML delar in historiska data som du anger i datamängder för träning respektive testning. Datamängden för testning är en uppsättning reserverade data som används för validering av modellens prestanda efter träningen. Dessa realiseras som entiteter för **träning och testning** i dataflödet. AutoML använder korsvalidering för validering av modellen.

Därefter analyseras varje indatafält och imputering tillämpas, vilket ersätter eventuella saknade värden med ersatta värden. AutoML använder några olika imputeringsstrategier. Sedan tillämpas eventuell nödvändig sampling och normalisering på dina data.

AutoML tillämpar flera transformeringar på varje valt indatafält baserat på datatyp och statistiska egenskaper. AutoML använder dessa transformeringar för att extrahera egenskaper som används vid träning av ML-modellen.

Träningsprocessen för AutoML-modeller består av upp till 50 iterationer med olika modelleringsalgoritmer och inställningar för hyperparametrar i syfte att hitta den modell som har bäst prestanda. Prestanda för var och en av dessa modeller utvärderas genom validering med testdatamängden med reserverade data. Under det här träningssteget skapar AutoML flera pipelines för träning och validering av dessa iterationer. Processen för att utvärdera modellernas prestanda kan ta tid, från några minuter till flera timmar, beroende på storleken på datamängden och tillgängliga dedikerade kapacitetsresurser.

I vissa fall kan den slutliga modell som genereras använda ensembleinlärning, där flera modeller används för att ge bättre förutsägelseprestanda.

### <a name="automl-model-explainability"></a>Förklarbarhet för AutoML-modell

När modellen har tränats analyserar AutoML relationen mellan indataegenskaperna och modellens utdata. Den utvärderar storlek av och riktning för ändringen i modellens utdata för testdatamängden med reserverade data för varje indataegenskap. Detta kallas *egenskapsprioritet*.

![Egenskapsprioritet](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>AutoML-modellrapport

AutoML genererar en Power BI-rapport som sammanfattar modellens prestanda under valideringen samt den globala egenskapsprioriteten. Rapporten sammanfattar resultatet från tillämpningen av ML-modellen på reserverade testdata och jämför förutsägelserna med de kända utfallsvärdena.

Du kan granska modellrapporten för att förstå dess prestanda. Du kan även kontrollera att modellens främsta influerare överensstämmer med affärsinsikterna om de kända utfallen.

De diagram och mått som används för att beskriva modellens prestanda i rapporten beror på modelltypen. Dessa prestandadiagram och mått beskrivs i följande avsnitt.

Ytterligare sidor i rapporten kan beskriva statistiska mått för modellen utifrån ett dataforskningsperspektiv. Till exempel innehåller rapporten om **binär förutsägelse** ett ökningsdiagram och ROC-kurvan för modellen.

Rapporterna innehåller även en sida med **träningsinformation** där det finns en beskrivning av hur modellen tränades. De innehåller även ett diagram som beskriver modellens prestanda för varje iterationskörning.

![Träningsinformation](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

I ett annat avsnitt på den här sidan beskrivs hur imputeringsmetoden användes för att fylla i saknade värden i indatafälten samt hur varje indatafält transformerades för att extrahera de egenskaper som användes i modellen. Det innehåller även de parametrar som användes av den slutliga modellen.

![Mer information om modellen](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Om den modell som skapades använder ensembleinlärning innehåller sidan med **träningsinformation** ett avsnitt som beskriver vikten för varje konstituerande modell i ensemblen samt dess parametrar.

![Vikt i ensemblen](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Tillämpa AutoML-modellen

Om du är nöjd med prestandan hos den ML-modell som skapades kan du tillämpa den på nya eller uppdaterade data när ditt dataflöde uppdateras. Du kan göra detta från modellrapporten genom att välja knappen **Tillämpa** i det övre högra hörnet.

För att kunna tillämpa ML-modellen måste du ange namnet på den entitet som modellen ska tillämpas på samt ett prefix för de kolumner som ska läggas till i den här entiteten för modellens utdata. Standardprefixet för kolumnnamnen är modellnamnet. Funktionen *Tillämpa* kan innehålla ytterligare parametrar som är specifika för modelltypen.

Vid tillämpning av ML-modellen skapas en ny dataströmsentitet med suffixet **enriched <modellnamn>** (utökad). Om du till exempel tillämpar modellen _PurchaseIntent_ på entiteten _OnlineShoppers_ genererar utdata **OnlineShoppers enriched PurchaseIntent**.

För närvarande kan inte utdataentiteten användas för att förhandsgranska ML-modellens resultat i Power Query-redigeraren. I utdatakolumnerna visas alltid null som resultat. För att visa resultatet skapas en andra utdataentitet med suffixet **enriched <modellnamn> Preview** (förhandsgranskning) när modellen tillämpas.

Du måste uppdatera dataflödet för att kunna förhandsgranska resultatet i Frågeredigeraren.

![Frågeredigeraren](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

När du tillämpar modellen håller AutoML alltid dina förutsägelser uppdaterade när dataflödet uppdateras.

AutoML innehåller även en individualiserad förklaring för varje rad som den poängsätter i utdataentiteten.

Om du vill använda insikter och förutsägelser från ML-modellen i en Power BI-rapport kan du ansluta till utdataentiteten från Power BI Desktop med hjälp av anslutningsprogrammet för **dataflöden**.

## <a name="binary-prediction-models"></a>Modeller för binär förutsägelse

Modeller för binär förutsägelse, som mer formellt kallas **modeller för binär klassificering**, används för att klassificera en datamängd i två grupper. De används för att förutsäga händelser som kan ha ett binärt utfall, till exempel huruvida en affärsmöjlighet realiseras, ett konto faller bort, en faktura betalas i tid eller en transaktion är bedräglig och så vidare.

Eftersom resultatet är binärt förväntar sig Power BI att märkningen för en modell för binär förutsägelse är en boolesk, där de kända utfallen märks som **sant** eller **falskt**. I till exempel en modell för realisering av affärsmöjligheter märks de affärsmöjligheter som har lyckats som sanna medan de som inte lyckades märks som falska och öppna affärsmöjligheter märks som null.

Utdata från en modell för binär förutsägelse är en sannolikhetspoäng som identifierar sannolikheten att det resultat som motsvarar märkningsvärdet Sant uppnås.

### <a name="training-a-binary-prediction-model"></a>Träna en modell för binär förutsägelse

För att skapa en modell för binär förutsägelse måste den indataentitet som innehåller dina träningsdata ha ett booleskt fält som fältet för historiska utfall i syfte att identifiera tidigare kända utfall.

Förutsättningar:

* Ett booleskt fält måste användas som fältet för historiska utfall
* Minst 50 rader med historiska data krävs för varje klass av utfall

I allmänhet gäller att om de tidigare utfallen identifieras av fält med olika datatyper så kan du lägga till en beräknad kolumn för att transformera dessa till en boolesk med hjälp av Power Query.

Processen för att skapa en modell för binär förutsägelse inbegriper samma steg som andra AutoML-modeller, vilket beskrivs i avsnittet **Konfigurera ML-modellens indata** ovan.

### <a name="binary-prediction-model-report"></a>Rapport för modell för binär förutsägelse

Modellen för binär förutsägelse skapar utfall i form av en sannolikhet att en post uppnår det utfall som definieras som Sant av värdet i den booleska märkningen. Rapporten innehåller ett utsnitt för sannolikhetströskeln som påverkar hur poäng över och under sannolikhetströskeln tolkas.

Rapporten beskriver modellens prestanda med avseende på *sanna positiva*, *falska positiva*, *sanna negativa* och *falska negativa* värden. Sanna positiva och sanna negativa värden är korrekt förutsagda utfall för de två klasserna i utfallsdata. Falska positiva värden är utfall med det faktiska booleska märkningsvärdet Falskt men som förutsades vara sanna. På motsvarande sätt är falska negativa värden utfall där det faktiska booleska märkningsvärdet var Sant men där värdena förutsades vara falska.

Mått såsom precision och träffsäkerhet beskriver effekten av sannolikhetströskeln på förutsagda utfall. Du kan använda utsnittet för sannolikhetströskel för att välja ett tröskelvärde som ger en balanserad avvägning mellan precision och träffsäkerhet.

![Förhandsgranskning av noggrannhet](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

Sidan **Noggrannhetsrapport** i modellrapporten innehåller diagrammet *Kumulativa ökningar* samt modellens ROC-kurva. Det här är statistiska mått för modellens prestanda. Rapporterna innehåller beskrivningar av de diagram som visas.

![Skärmen Noggrannhetsrapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Tillämpa en modell för binär förutsägelse

För att tillämpa en modell för binär förutsägelse måste du ange entiteten med de data som du vill tillämpa förutsägelserna från ML-modellen på. Andra parametrar är namnprefixet för utdatakolumnen sant sannolikhetströskeln för klassificering av det förväntade utfallet.

![Indata för förutsägelse](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

När en modell för binär förutsägelse tillämpas lägger den till tre utdatakolumner i den utökade utdataentiteten. Dessa är **PredictionScore**, **PredictionOutcome** och **PredictionExplanation**. Prefixet för kolumnnamnen anges när modellen tillämpas.

Kolumnen **PredictionOutcome** innehåller märkningen för det förutsagda utfallet. Poster med sannolikheter som överstiger tröskelvärdet förutsägs troligen uppnå utfallet, och dem som understiget tröskelvärdet förutsägs ej troligen uppnå utfallet.

Kolumnen **PredictionExplanation** innehåller en förklaring av den specifika påverkan som indataegenskaperna hade på **PredictionScore**. Det här är en JSON-formaterad samling av vikter för förutsägelsens indataegenskaper.

## <a name="classification-models"></a>Klassificeringsmodeller

Klassificeringsmodeller används för att klassificera en datamängd i flera grupper eller klasser.  De används för att förutsäga händelser som kan ha ett av flera möjliga utfall, till exempel huruvida en kund troligtvis har ett mycket högt, högt, medelhögt eller lågt livslängdsvärde, huruvida risken för försummelse är hög, medelhög, låg eller mycket låg och så vidare.

Utdata från en klassificeringsmodell är en sannolikhetspoäng som identifierar sannolikheten för att en post uppnår kriterierna för en viss klass.

### <a name="training-a-classification-model"></a>Träna en klassificeringsmodell

Den indataentitet som innehåller dina träningsdata för klassificeringsmodell måste ha en sträng eller ett numeriskt fält som fältet för historiska utfall, som identifierar de tidigare kända utfallen.

Förutsättningar:

* Minst 50 rader med historiska data krävs för varje klass av utfall

Processen för att skapa en klassificeringsmodell inbegriper samma steg som andra AutoML-modeller, vilket beskrivs i avsnittet **Konfigurera ML-modellens indata** ovan.

### <a name="classification-model-report"></a>Rapport för klassificeringsmodell

Rapporten för klassificeringsmodell skapas genom att ML-modellen tillämpas på reserverade testdata och den förutsagda klassen för en post jämförs med den faktiska kända klassen.

Modellrapporten innehåller ett diagram med en analys av korrekt och felaktigt klassificerade poster för varje känd klass.

![Modellrapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

En ytterligare klasspecifik precisering möjliggör en analys av hur förutsägelserna för en känd klass är fördelade. Detta inkluderar de andra klasserna där poster för den kända klassen sannolikt blir felklassificerade.

![Analysrapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

Modellförklaringen i rapporten innehåller även de främsta förutsägande faktorerna för varje klass.

Rapporten för klassificeringsmodell innehåller även en sida med träningsinformation som liknar sidorna för andra modelltyper, enligt beskrivningen i avsnittet **AutoML-modellrapport** tidigare i den här artikeln.

### <a name="applying-a-classification-model"></a>Tillämpa en klassificeringsmodell

För att tillämpa en ML-klassificeringsmodell måste du ange entiteten med indata och namnprefixet för utdatakolumn.

När en klassificeringsmodell tillämpas lägger den till tre utdatakolumner i den utökade utdataentiteten. Dessa är **PredictionScore**, **PredictionClass** och **PredictionExplanation**. Prefixet för kolumnnamnen anges när modellen tillämpas.

Kolumnen **PredictionClass** innehåller den mest sannolika förutsagda klassen för posten. Kolumnen **PredictionScore** innehåller en lista över sannolikhetspoäng för posten för varje möjlig klass.

Kolumnen **PredictionExplanation** innehåller en förklaring av den specifika påverkan som indataegenskaperna hade på **PredictionScore**. Det här är en JSON-formaterad samling av vikter för förutsägelsens indataegenskaper.

## <a name="regression-models"></a>Regressionsmodeller

Regressionsmodeller används för att förutsäga ett värde, till exempel de intäkter som troligen kommer att realiseras från en försäljningsaffär, livslängdsvärdet för ett konto, hur mycket av en betalbar faktura som sannolikt kommer att betalas, det datum då en faktura kan betalas och så vidare.

Utdata från regressionsmodell är det förutsagda värdet.

### <a name="training-a-regression-model"></a>Träna en regressionsmodell

Den indataentitet som innehåller träningsdata för regressionsmodell måste ha en ett numeriskt fält som fältet för historiska utfall, som identifierar de tidigare kända utfallsvärdena.

Förutsättningar:

* Minst 100 rader med historiska data krävs för en regressionsmodell

Processen för att skapa en regressionsmodell inbegriper samma steg som andra AutoML-modeller, vilket beskrivs i avsnittet **Konfigurera ML-modellens indata** ovan.

### <a name="regression-model-report"></a>Regressionsmodellrapport

Liksom andra AutoML-modellrapporter baseras regressionsrapporten på resultatet av tillämpningen av modellen på reserverade testdata.

Modellrapporten innehåller ett diagram som jämför de förutsagda värdena med det faktiska värdet. I det här diagrammet indikerar avståndet från diagonalen felet i förutsägelsen.

Diagrammet över återstående fel visar distributionen av procentandelen genomsnittligt fel för olika värden i testdatamängden med reserverade data. Den vågräta axeln representerar medelvärdet av det faktiska värdet för gruppen, och storleken på bubblan visar frekvensen eller antalet värden i det intervallet. Den lodräta axeln är det genomsnittliga återstående felet.

![Diagram över återstående fel](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

Rapporten för regressionsmodell innehåller även en sida med träningsinformation likt sidorna för andra modelltyper, enligt beskrivningen i avsnittet **AutoML-modellrapport** ovan.

### <a name="applying-a-regression-model"></a>Tillämpa en regressionsmodell

För att tillämpa en ML-regressionsmodell måste du ange entiteten med indata och namnprefixet för utdatakolumn.

![Tillämpa en regression](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

När en regressionsmodell tillämpas lägger den till två utdatakolumner i den utökade utdataentiteten. Dessa är **PredictionValue** och **PredictionExplanation**. Prefixet för kolumnnamnen anges när modellen tillämpas.

Kolumnen **PredictionValue** innehåller det förutsagda värdet för posten baserat på indatafälten. Kolumnen **PredictionExplanation** innehåller en förklaring av den specifika påverkan som indataegenskaperna hade på **PredictionValue**. Det här är en JSON-formaterad samling av vikter för indataegenskaperna.

## <a name="next-steps"></a>Nästa steg

Den här artikeln visade en översikt av automatiserad maskininlärning för dataflöden i Power BI-tjänsten. Följande artiklar kan också vara användbara.

* [Självstudier: Skapa en maskininlärningsmodell i Power BI (förhandsversion)](service-tutorial-build-machine-learning-model.md)
* [Självstudier: Använda Cognitive Services i Power BI](service-tutorial-use-cognitive-services.md)
* [Självstudier: Anropa en Machine Learning Studio-modell i Power BI (förhandsgranskning)](service-tutorial-invoke-machine-learning-model.md)
* [Cognitive Services i Power BI (förhandsversion)](service-cognitive-services.md)
* [Azure Machine Learning-integrering i Power BI (förhandsversion)](service-machine-learning-integration.md)

Mer information om dataflöden finns i de här artiklarna:
* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI-dataflöden](service-dataflows-developer-resources.md)
* [Dataflöden och Azure Data Lake-integrering (förhandsversion)](service-dataflows-azure-data-lake-integration.md)


