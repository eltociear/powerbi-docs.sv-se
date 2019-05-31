---
title: Automatiserad maskininlärning i Power BI (förhandsversion)
description: Lär dig hur du använder automatisk Machine Learning (AutoML) i Power BI
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
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61236837"
---
# <a name="automated-machine-learning-in-power-bi-preview"></a>Automatiserad maskininlärning i Power BI (förhandsversion)

Automatiserad machine learning (AutoML) för dataflöden kan affärsanalytiker att träna, verifiera och anropa Machine Learning-modeller direkt i Power BI. Den innehåller ett enkelt gränssnitt för att skapa en ny ML-modell där analytiker kan använda sina dataflöden för att ange indata för att träna modellen. Tjänsten automatiskt extraherar de viktigaste funktionerna, väljer en lämplig algoritm och justerar och validerar ML-modellen. När en tränas genererar en rapport som innehåller resultatet av verifieringen som förklarar prestanda och resultat att analytiker automatiskt i Power BI. Modellen kan sedan anropas för alla nya eller uppdaterade data i dataflödet.

![Machine learning-skärmen](media/service-machine-learning-automated/automated-machine-learning-power-bi-01.png)

Automatiserad machine learning är tillgänglig för dataflöden som är värd för Power BI Premium och inbäddade kapaciteter. I den här förhandsversionen kan du träna machine learning-modeller för binära förutsägelse, klassificering och Regressionsmodeller i AutoML.

## <a name="working-with-automl"></a>Arbeta med AutoML

[Power BI dataflöden](service-dataflows-overview.md) erbjuder självbetjäning dataförberedelser för stordata. AutoML kan du utnyttja dina data förberedande arbete för att skapa machine learning-modeller, direkt i Power BI.

AutoML i Power BI kan dataanalytiker du utvecklar maskininlärningsmodeller med ett förenklat sätt med dataflöden med bara Power BI-kunskaper. De flesta av datavetenskap bakom skapandet av ML-modeller automatiskt av Power BI med guardrails så att modellen produceras har god kvalitet och synlighet så att du får full insyn i den process som används för att skapa ML-modell.

AutoML stöder skapandet av **binära förutsägelse**, **klassificering**, och **Regression** modeller för dataflöden. Det här är typer av övervakade machine learning-modeller, vilket innebär att de Lär dig från kända resultat för senaste observationer att förutsäga resultat för andra observationer. Den inkommande datauppsättningen för att träna en modell för AutoML är en uppsättning poster som är **märkta** med kända resultaten.

AutoML i Power BI integrerar [automatiserad ML](https://docs.microsoft.com/azure/machine-learning/service/concept-automated-ml) från den [Azure Machine Learning-tjänsten](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml) att skapa ML-modeller. Du behöver dock inte en Azure-prenumeration du använder AutoML i Power BI. Processen för utbildning och som är värd för ML-modeller hanteras helt av Power BI-tjänsten.

När en ML-modellen tränas, genererar AutoML automatiskt en Power BI-rapport som förklarar sannolikt prestanda för din ML-modell. AutoML framhäver explainability, genom att markera påverka bland dina indata som påverkar förutsägelser som returneras av din modell. Rapporten innehåller också viktiga mått för modellen, beroende på typen av ML-modellen.

Andra sidor i rapporten som genereras visar statistisk sammanfattning av modellen och utbildningsinformation. Statistisk sammanfattningen är av intresse för användare som vill se standard data science-åtgärder för prestanda för modellen. Utbildningsinformation sammanfattar alla iterationer som kördes för att skapa din modell, med tillhörande modellering parametrar. Här beskrivs också hur varje indata används för att skapa ML-modellen.

Du kan sedan använda ML-modell för dina data för bedömning. När dataflödet uppdateras, används automatiskt förutsägelser från din ML-modell till dina data. Powerbi innehåller också en individuella förklaring för varje specifik förutsägelse poäng som producerar ML-modellen.

## <a name="creating-a-machine-learning-model"></a>Skapa en modell för maskininlärning

Det här avsnittet beskriver hur du skapar en AutoML learning-modell. 

### <a name="data-prep-for-creating-an-ml-model"></a>Dataförberedelser för att skapa en ML-modell

Om du vill skapa en modell för maskininlärning i Power BI, måste du först skapa ett dataflöde för data med den historiska resultat-informationen, som används för att träna ML-modellen. Mer information om hur du konfigurerar ditt dataflöde, finns i [självbetjänad Förbered i Power BI](service-dataflows-overview.md).

Power BI använder data från bara en enda entitet för att träna ML-modellen i den aktuella versionen. Så om din historiska data består av flera enheter, måste du manuellt ansluta data i en enda dataflöde entitet. Du bör även lägga till beräknade kolumner för alla affärsmått som kan vara starkt förutsägelser för att förutsäga resultatet.

AutoML har specifika krav för att träna en maskininlärningsmodell. Kraven beskrivs i avsnitten nedan, baserat på respektive modelltyper.

### <a name="configuring-the-ml-model-inputs"></a>Konfigurera indata för ML-modell

Om du vill skapa en modell för AutoML, välj ikonen ML i den **åtgärder** kolumn med entiteten dataflöde med historiska data och välja **lägga till en maskininlärningsmodell**.

![Lägg till en modell för maskininlärning](media/service-machine-learning-automated/automated-machine-learning-power-bi-02.png)

Ett förenklat sätt startas, som består av en guide som vägleder dig genom processen att skapa ML-modellen. Guiden innehåller följande enkla steg.

1. Välj entiteten med resultatet av historiska data och fältet som du vill ha en förutsägelse
2. Välj en modelltyp av baserat på vilken typ av förutsägelser som du skulle vilja se
3. Välj de indata som du vill att modellen ska användas som förutsägande signaler
4. Namnge din modell och spara konfigurationen

Fältet historiska resultatet identifierar attributet etikett för att träna ML-modellen, som visas i följande bild.

![Välj resultatet av historiska data](media/service-machine-learning-automated/automated-machine-learning-power-bi-03.png)

När du anger fältet historiska resultatet AutoML analyserar data etikett för att identifiera vilka typer av ML-modeller som kan tränas för dessa data och ger förslag på mest sannolika ML modelltypen som kan tränas. 

> [!NOTE]
> Vissa modelltyper stöds inte för de data som du har valt.

AutoML analyserar även alla fält i den valda entiteten föreslå indata som kan användas för att träna ML-modellen. Den här processen är ungefärliga och baseras på statistiska analyser, så bör du granska de indata som används. Inga indata som är beroende av fältet historiska resultat (eller etikettfältet) bör inte användas för att träna ML-modellen eftersom de påverkar dess prestanda.

![Anpassa indatafälten](media/service-machine-learning-automated/automated-machine-learning-power-bi-04.png)

I det sista steget, kan du namnge modellen och spara dess inställningar.

Det här steget uppmanas du att uppdatera dataflöde, som börjar utbildning för ML-modellen.

### <a name="ml-model-training"></a>ML-modellträning

Utbildning av AutoML modeller är en del av dataflöde-uppdatering. AutoML först förbereder data för utbildning.

AutoML delar upp historiska data som du anger i ett utbildnings- och testningsdatauppsättningar. Test-datauppsättning är en behövs som används för att verifiera modellprestanda efter utbildning. Dessa realiseras som **träning och testning** entiteter i dataströmmen. AutoML använder korsvalidering för verifieringen av modellen.

Sedan varje indatafältet analyseras och uppräkning används, vilket ersätter värden som saknas med ersatta värden. Ett par olika uppräkning strategier som används av AutoML. Sedan tillämpas alla nödvändiga sampling och normalisering till dina data.

AutoML gäller flera transformationer är varje valda inmatningsfält baserat på dess datatyp och dess statistiska egenskaper. AutoML använder dessa omvandlingar för att extrahera funktioner för användning i utbildning ML-modell.

Träningsprocess för AutoML modeller består av upp till 50 iterationer med olika modellering algoritmer och inställningar för finjustering att hitta modellen med bäst prestanda. Prestanda för var och en av dessa modeller utvärderas av verifiering med testdata behövs. Det här steget utbildning skapar AutoML flera pipelines för utbildning och validering av dessa iterationer. Hur du utvärderar prestanda för modellerna kan ta tid, var som helst från några minuter till ett par timmar, beroende på storleken på din datauppsättning och de tillgängliga resurserna för dedikerad kapacitet.

I vissa fall kan kan den slutliga modellen som genereras använda ensemble learning där flera modeller används för att leverera förutsägbar prestanda förbättras.

### <a name="automl-model-explainability"></a>AutoML modellen explainability

När modellen har tränats, analyserar AutoML relationen mellan indatafunktionerna och utdata för modellen. Det utvärderar omfattningen och riktningen för ändring av modellen utdata för testdata behövs för varje inkommande funktion. Detta kallas den *funktionen vikten*.

![Funktionen prioritet](media/service-machine-learning-automated/automated-machine-learning-power-bi-05.png)

### <a name="automl-model-report"></a>AutoML modellen rapport

AutoML genererar en Power BI-rapport som sammanfattar prestanda för modellen vid verifiering, tillsammans med globala funktionen vikten. Rapporten innehåller en sammanfattning av resultaten från ML-modellen för behövs testdata och jämföra förutsägelser med värdena som kända resultatet.

Du kan granska modellen rapporten för att förstå dess prestanda. Du kan också bekräfta att påverka av modellen som överensstämmer med affärsinsikter om kända resultat.

Diagram och mått som används för att beskriva modellprestanda i rapporten beror på vilken modell. Dessa prestandadiagram och åtgärder beskrivs i följande avsnitt.

Fler sidor i rapporten kan beskriva statistiska åtgärder om modellen från en data science perspektiv. Exempelvis kan den **binära förutsägelse** rapporten innehåller ett diagram för vinst och ROC-kurvan för modellen.

Rapporterna innehåller också en **utbildningsinformation** sidan som innehåller en beskrivning av hur modellen har tränats och innehåller ett diagram som beskriver modellens prestanda över varje iterationer körs.

![Träningsinformation](media/service-machine-learning-automated/automated-machine-learning-power-bi-06.png)

Ett annat avsnitt på den här sidan beskriver hur uppräkning metoden används för att fylla i saknade värden för fälten inkommande samt hur varje indatafält har omvandlas för att extrahera funktioner som används i modellen. Den innehåller också de parametrar som används av den slutliga modellen.

![Mer information för modellen](media/service-machine-learning-automated/automated-machine-learning-power-bi-07.png)

Om du använder modellen produceras ensemble learning kommer **utbildningsinformation** sidan finns också ett avsnitt som beskriver vikten för varje konstituerande modell i ensemble, samt dess parametrar.

![Vikt i ensemble](media/service-machine-learning-automated/automated-machine-learning-power-bi-08.png)

## <a name="applying-the-automl-model"></a>Tillämpa AutoML modellen

Om du är nöjd med prestanda för ML-modell som har skapats kan tillämpa du den på nya eller uppdaterade data när ditt dataflöde uppdateras. Du kan göra detta från modellen-rapport genom att välja den **tillämpa** i det övre högra hörnet.

Du måste ange namnet på den entitet som den ska tillämpas och ett prefix för de kolumner som ska läggas till den här entiteten för modellen utdata om du vill använda ML-modellen. Modellnamnet är i standardprefixet för namn på kolumnerna. Den *tillämpa* funktion kan innehålla ytterligare parametrar som är specifik för modelltyp.

Tillämpa ML-modellen skapar en ny entitet dataflöde med suffixet **berikats < modellnamn >** . Till exempel om du använder den _PurchaseIntent_ modeller till den _OnlineShoppers_ entiteten utdata genererar den **OnlineShoppers berikats PurchaseIntent**.

För närvarande kan inte utdata entiteten användas för att förhandsgranska resultaten för ML-modellen i Power Query-redigeraren. Utdatakolumnerna Visa alltid null som ett resultat. Om du vill visa resultatet utdata en andra enhet med suffixet **berikats < modellnamn > förhandsversion** skapas när modellen har tillämpats.

Du måste uppdatera dataflöde, om du vill förhandsgranska resultaten i frågeredigeraren.

![Frågeredigeraren](media/service-machine-learning-automated/automated-machine-learning-power-bi-09.png)

När du använder modellen håller AutoML alltid din förutsägelser uppdaterad när dataflödet uppdateras.

AutoML innehåller också en individuella förklaring för varje rad som det poängsätter i utdata-entiteten.

Om du vill använda insikter och förutsägelser från ML-modell i en Power BI-rapport, som du kan ansluta till entiteten utdata från Power BI Desktop med den **dataflöden** connector.

## <a name="binary-prediction-models"></a>Binär Förutsägelsemodeller

Binär förutsägelsemodeller mer formellt kallas **binär klassificering modeller**, används för att klassificera en datauppsättning i två grupper. De används för att förutse händelser som kan ha ett binära resultat, till exempel om en affärsmöjlighet konverterar, om ett konto kommer omsättning, om en faktura kommer att betalas till tid; Om en transaktion är bedrägliga och så vidare.

Eftersom resultatet är binär, Power BI förväntar sig etikett för en binär förutsägelsemodell ska vara ett booleskt värde med kända resultat som är märkt **SANT** eller **FALSKT**. Exempelvis i en affärsmöjlighet konvertering modell, potentiella kunder som har tagits hem är märkta med true, de som har gått förlorade är märkta FALSKT och de öppna affärsmöjligheterna är märkta med null.

Utdata från en binär förutsägelsemodell är en sannolikhetspoäng som identifierar sannolikheten att resultatet motsvarar etikettvärdet är sant kommer att uppnås.

### <a name="training-a-binary-prediction-model"></a>Träna en modell för binära förutsägelse

Om du vill skapa en binär förutsägelsemodell måste inkommande entiteten som innehåller dina utbildningsdata ha typen Boolean som fältet historiska resultat för att identifiera de senaste kända resultat.

Förutsättningar:

* Typen Boolean måste användas som fältet historiska resultat
* Det krävs minst 50 rader med historiska data för varje klass resultat

Om de senaste resultaten identifieras av fälten i en annan datatyp, kan du i allmänhet lägga till en beräknad kolumn för att omvandla dessa till ett booleskt värde med Power Query.

Processen att skapa för en binär förutsägelsemodell följer samma steg som andra AutoML modeller, som beskrivs i avsnittet **konfigurera modellindata ML** ovan.

### <a name="binary-prediction-model-report"></a>Binär förutsägelse modellen rapport

Den binära förutsägelsemodell som producerar som utdata sannolikheten att en post kommer att uppnå resultatet som definieras av boolesk etikettvärdet som SANT. Rapporten innehåller ett utsnitt för sannolikhetströskelvärdet som påverkar hur poängen över och under sannolikhetströskelvärdet tolkas.

Rapporten beskriver prestanda för modellen i *positiva*, *falska positiva identifieringar*, *SANT negativ* och *FALSKT negativ*. SANT positiva identifieringar och SANT negativ är korrekt förutsagt resultat för de båda klasserna i resultatet data. Falska positiva identifieringar är resultat som hade värdet FALSKT faktiska booleskt etiketten men har förutse som True. Däremot är FALSKT negativ resultat där det faktiska booleska etikettvärdet var True men har förutse som FALSKT.

Mått, till exempel Precision och kanske kommer ihåg, beskriver effekten av sannolikhetströskelvärdet på de förväntade resultaten. Du kan använda utsnittet tröskelvärdet sannolikheten för att välja ett tröskelvärde som ger en balancerad kompromiss mellan Precision och återkallande.

![Förhandsversion av Precision](media/service-machine-learning-automated/automated-machine-learning-power-bi-10.png)

Den **noggrannhet rapporten** sida i rapporten modellen innehåller den *ackumulerade vinster* diagram och ROC-kurva för modellen. Det här är statistiska åtgärder av modellprestanda. Rapporterna innehåller beskrivningar av diagrammen som visas.

![Precision rapportskärm](media/service-machine-learning-automated/automated-machine-learning-power-bi-11.png)

### <a name="applying-a-binary-prediction-model"></a>Tillämpa en binär förutsägelsemodell

Du måste ange entiteten med data som du vill tillämpa förutsägelser från ML-modellen för att tillämpa en binär förutsägelsemodell. Andra parametrar är namnprefix för utdata-kolumn och sannolikhetströskelvärdet för klassificering av förväntade resultatet.

![Indata för förutsägelse](media/service-machine-learning-automated/automated-machine-learning-power-bi-12.png)

När en binär förutsägelsemodell används, läggs tre utdatakolumner till entiteten avancerad och utdata. Det här är den **PredictionScore**, **PredictionOutcome** och **PredictionExplanation**. Namn på kolumnerna i entiteten har det prefix som anges när modellen används.

Den **PredictionOutcome** kolumnen innehåller förväntade resultatet etiketten. Poster med sannolikhet som överskrider tröskeln förutspås eftersom den sannolikt kan uppnå resultatet och de nedan är förväntad som sannolikt inte kommer att få resultatet.

Den **PredictionExplanation** kolumnen innehåller en förklaring med specifika påverkan som indatafunktionerna hade på den **PredictionScore**. Det här är en JSON-formaterad samling vikterna inkommande funktioner för förutsägelse.

## <a name="classification-models"></a>Klassificering modeller

Klassificering modeller används för att klassificera en datauppsättning i flera grupper eller klasser.  De används för att förutse händelser som kan ha ett av flera möjliga resultat, till exempel om en kund är sannolikt att ha en mycket hög, hög, medel eller låg livstidsvärde; om risken för standard är hög, Måttlig, låg eller mycket låg; och så vidare.

Utdata från en modell för klassificering är en sannolikhetspoäng som identifierar sannolikheten att en post kommer att uppnå villkoren för en viss klass.

### <a name="training-a-classification-model"></a>Träna en modell med klassificering

Inkommande entiteten som innehåller dina utbildningsdata för en klassificeringsmodellen måste ha en sträng eller ett numeriskt fält som fältet historiska resultat som identifierar de senaste kända resultat.

Förutsättningar:

* Det krävs minst 50 rader med historiska data för varje klass resultat

Processen att skapa för en klassificeringsmodellen följer samma steg som andra AutoML modeller, som beskrivs i avsnittet **konfigurera modellindata ML** ovan.

### <a name="classification-model-report"></a>Modellen rapport

Klassificeringen modellen rapporten skapas genom att använda ML-modellen för behövs testa data och jämföra den förväntade klassen för en post med den faktiska kända klassen.

Modell-rapporten innehåller ett diagram som innehåller uppdelning av på rätt sätt och felaktigt klassificerad posterna för varje kända klass.

![Modell-rapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-13.png)

En ytterligare klass-specifika nedbrytning kan en analys av hur förutsägelser för en känd klass distribueras. Detta inkluderar de andra klasser som poster i som kända klass är troligt att klassificeras.

![Analysrapport](media/service-machine-learning-automated/automated-machine-learning-power-bi-14.png)

Modellen förklaring i rapporten innehåller också de översta förutsägelserna för varje klass.

Klassificering modellen rapporten innehåller också en utbildning informationssida som liknar sidorna för andra modelltyper av som beskrivs i avsnittet **AutoML modellen rapporten** tidigare i den här artikeln.

### <a name="applying-a-classification-model"></a>Tillämpa en klassificeringsmodellen

Du måste ange entiteten med indata och utdata kolumnen namnprefixet för att tillämpa en klassificering ML-modell.

När en klassificeringsmodellen används, läggs tre utdatakolumnerna till entiteten avancerad och utdata. Det här är den **PredictionScore**, **PredictionClass** och **PredictionExplanation**. Namn på kolumnerna i entiteten har det prefix som anges när modellen används.

Den **PredictionClass** kolumnen innehåller den mest sannolikt förväntade klassen för posten. Den **PredictionScore** kolumnen innehåller listan över sannolikheten poäng för posten för varje klass som möjligt.

Den **PredictionExplanation** kolumnen innehåller en förklaring med specifika påverkan som indatafunktionerna hade på den **PredictionScore**. Det här är en JSON-formaterad samling vikterna inkommande funktioner för förutsägelse.

## <a name="regression-models"></a>Regressionsmodeller

Regressionsmodeller används för att förutsäga ett värde, till exempel intäkter sannolikt kan komma från ett försäljning avtal, värde för livslängd för ett konto, hur mycket en Kundreskontra faktura som troligen kommer att betalas, det datum då en faktura kan betalas , och så vidare.

Utdata från en regressionsmodell är förutsägelsevärdet.

### <a name="training-a-regression-model"></a>Träna en regressionsmodell

Inkommande entiteten som innehåller utbildningsdata för en regressionsmodell måste ha ett numeriskt fält som fältet historiska resultat som identifierar de senaste kända resultat-värdena.

Förutsättningar:

* Det krävs minst 100 rader med historiska data för en regressionsmodell

Processen att skapa för en regressionsmodell följer samma steg som andra AutoML modeller, som beskrivs i avsnittet **konfigurera modellindata ML** ovan.

### <a name="regression-model-report"></a>Regression modell rapport

Som andra AutoML modellen rapporter och baseras Regression rapporten på resultaten från tillämpas testdata behövs modellen.

Modell-rapporten innehåller ett diagram som jämför de förväntade värdena till det faktiska värdet. I det här diagrammet anger avståndet från diagonalt felet i förutsägelser.

Övriga fel diagrammet visar fördelningen av procentandelen genomsnittlig fel för olika värden i testdata behövs. Vågrät axel representerar medelvärdet av det faktiska värdet för gruppen med storleken på bubblorna visar frekvensen eller antalet värden i intervallet. Lodrät axel är den genomsnittliga övriga fel.

![Övriga fel diagram](media/service-machine-learning-automated/automated-machine-learning-power-bi-15.png)

Regression modell rapporten innehåller också en sida med information för utbildning som rapporter för andra modelltyper av som beskrivs i avsnittet **AutoML modellen rapporten** ovan.

### <a name="applying-a-regression-model"></a>Tillämpa en regressionsmodell

Du måste ange entiteten med indata och utdata kolumnen namnprefixet för att tillämpa en Regression ML-modell.

![Tillämpa en regression](media/service-machine-learning-automated/automated-machine-learning-power-bi-16.png)

När en regressionsmodell används, läggs två utdatakolumner till entiteten avancerad och utdata. Det här är den **PredictionValue**, och **PredictionExplanation**. Namn på kolumnerna i entiteten har det prefix som anges när modellen används.

Den **PredictionValue** kolumnen innehåller det förväntade värdet för posten baserat på indatafält. Den **PredictionExplanation** kolumnen innehåller en förklaring med specifika påverkan som indatafunktionerna hade på den **PredictionValue**. Det här är en JSON-formaterad samling vikten för indatafunktionerna utifrån.

## <a name="next-steps"></a>Nästa steg

Den här artikeln används för att tillhandahålla en översikt över automatisk Machine Learning för dataflöden i Power BI-tjänsten. I följande artiklar kan också vara användbara.

* [Självstudier: Skapa en Machine Learning-modell i Power BI (förhandsversion)](service-tutorial-build-machine-learning-model.md)
* [Självstudier: Använda Cognitive Services i Power BI](service-tutorial-use-cognitive-services.md)
* [Självstudier: Anropa en Machine Learning Studio-modell i Power BI (förhandsgranskning)](service-tutorial-invoke-machine-learning-model.md)
* [Cognitive Services i Power BI (förhandsversion)](service-cognitive-services.md)
* [Azure Machine Learning-integrering i Power BI (förhandsversion)](service-machine-learning-integration.md)

Mer information om dataflöden finns i de här artiklarna:
* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Med beräknade entiteter på Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Med hjälp av dataflöden med lokala datakällor](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI dataflöden](service-dataflows-developer-resources.md)
* [Dataflöden och Azure Data Lake-integrering (förhandsversion)](service-dataflows-azure-data-lake-integration.md)


