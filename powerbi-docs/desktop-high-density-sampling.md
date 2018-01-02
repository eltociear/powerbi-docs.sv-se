---
title: "Högdensitetssampling av linjer i Power BI"
description: "Högdensitetssampling av linjer i Power BI"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: c8eb43a86791fa067f7f2417780806eba007672c
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/06/2017
---
# <a name="high-density-line-sampling-in-power-bi"></a>Högdensitetssampling av linjer i Power BI
Från och med juni 2017-versionen av **Power BI Desktop** och uppdateringar av **Power BI-tjänsten**, finns en ny samplingsalgoritm tillgänglig som förbättrar visuella objekt som samplar högdensitetsdata. Du kan till exempel skapa ett linjediagram från din återförsäljares försäljningsresultat för varje butik som har mer än tiotusen försäljningskvitton varje år. Ett linjediagram med sådan försäljningsinformation skulle sampla data (välja en meningsfull återgivning av dessa data som illustrerar hur försäljningen varierar över tid) från datan för varje butik, samt skapa ett linjediagram med flera serier som därmed representerar underliggande data. Detta är vanligt vid visualisering av högdensitetsdata och Power BI Desktop har förbättrat sin sampling av högdensitetsdata, vilket beskrivs i den här artikeln.

![](media/desktop-high-density-sampling/high-density-sampling_01.png)

> [!NOTE]
> Algoritmen för **högdensitetssampling** som beskrivs i den här artikeln gäller för (och är tillgänglig i) både **Power BI Desktop** och **Power BI-tjänsten**.
> 
> 

## <a name="how-high-density-line-sampling-works"></a>Hur högdensitetssampling av linjer fungerar
Tidigare valde **Power BI** en uppsättning samplade datapunkter från alla underliggande data på ett deterministiskt sätt. För högdensitetsdata som omfattar ett kalenderår kan det exempelvis finnas 350 samplade datapunkter i det visuella objektet, där alla har valts för att säkerställa att en fullständig uppsättning data (övergripande serien med underliggande data) återges i det visuella objektet. För att förstå varför detta sker antar vi att vi har ritat upp aktiekursen för ett år och valt 365 datapunkter för att skapa ett linjediagram (med en datapunkt för varje dag).

I detta fall finns det många värden för aktiekursen varje dag. Naturligtvis finns det ett högsta- och lägstavärde varje dag, men det kan inträffa när som helst under dagen när börsmarknaden är öppen. Vid högdensitetssampling av linjer där den underliggande datasamplingen görs 10:30 och 12:00 varje dag, tas en representativ ögonblicksbild av underliggande data (kursen kl. 10:30 och 12:00), men den kanske inte registrerar det faktiska högsta- och lägstavärdet för aktiekursen för den representativa datapunkten (den dagen). I denna situation – och andra – är samplingen representativ för underliggande data, men den hämtar inte alltid viktiga punkter, som i det här fallet är dagliga högsta- och lägstavärden för aktiekursen.

Högdensitetsdata samplas för att möjliggöra visualiseringar som kan skapas snabbt och som är dynamiska för interaktivitet (för många datapunkter i ett visuellt objekt kan bli rörigt och försämra synligheten för trender). Det som styr skapandet av samplingsalgoritmen är hur dessa data samplas för att ge bästa möjliga visualisering. Algoritmen i Power BI Desktop har förbättrats för att ge den bästa kombinationen av svarstider, återgivning och att bevara viktiga punkter i varje tidsutsnitt.

## <a name="how-the-new-line-sampling-algorithm-works"></a>Så här fungerar den samplingsalgoritmen för linjer
Den nya algoritmen för högdensitetssampling av linjer är tillgänglig för linjediagram och ytdiagram med en kontinuerlig x-axel.

Vid visuella högdensitetsobjekt skapar **Power BI** utsnitt av dina data i segment med hög matchning och väljer sedan ut viktiga punkter som representerar varje segment. Processen för segmentering av högupplösta data är specifikt anpassad för att säkerställa att det resulterande diagrammet inte går att skilja från andra visuella objekt, men är mycket snabbare och mer interaktivt.

### <a name="minimum-and-maximum-values-for-high-density-line-visuals"></a>Lägsta och högsta värden för visuella linjeobjekt med hög densitet
Följande visuella begränsningar gäller för alla angivna visualiseringar:

* **3 500** är det maximala antalet datapunkter som kan *visas* i ett visuellt objekt, oavsett antalet underliggande datapunkter eller serier. Så om du har 10 serier med 350 datapunkter i varje, har det visuella objektet uppnått den maximala gränsen för datapunkter. Om du har en serie kan den ha upp till 3 500 datapunkter om den nya algoritmen bedömer att det är den bästa samplingen för underliggande data.
* Det finns ett maxvärde på **60 serier** för alla visuella objekt. Om du har mer än 60 serier kan du dela upp datan och skapa flera visuella objekt med 60 eller färre serier i varje. Det är bra att använda ett **utsnitt** till att endast visa segment av data (endast vissa serier). Om till exempel alla underkategorier visas i förklaringen, kan du använda ett utsnitt för att filtrera efter övergripande kategori på samma rapportsida.

Dessa parametrar säkerställer att visuella objekt i Power BI Desktop återges mycket snabbt och är dynamiska vid interaktionen med användarna, samt inte leder till onödig extra belastning på den dator som återger det visuella objektet.

### <a name="evaluating-representative-data-points-for-high-density-line-visuals"></a>Utvärdera representativa datapunkter för visuella linjeobjekt med hög densitet
När antalet underliggande datapunkter överskrider de datapunkter som kan visas i det visuella objektet (överskrider 3 500), påbörjas en process som kallas *datagruppering*. Den segmenterar underliggande data i grupper som kallas *lagerplatser* och förfinar sedan dessa lagerplatser iterativt.

Algoritmen skapar så många lagerplatser som det går för att ge största möjliga granularitet för det visuella objektet. Inom varje lagerplats hittar algoritmen det lägsta och högsta datavärdet, så att viktiga och betydande värden (till exempel avvikare) kan hämtas och visas i det visuella objektet. Baserat på resultatet av datagrupperingen och efterföljande utvärdering av datan med Power BI, fastställs lägsta matchning för x-axeln i det visuella objektet – för att säkerställa maximal granularitet för objektet.

Som tidigare nämnts är den lägsta granulariteten för varje serie 350 punkter, och det maximala värdet är 3 500.

Varje lagerplats representeras av två datapunkter, vilket blir den lagerplatsens representativa datapunkter i det visuella objektet. Datapunkterna är helt enkelt högsta och lägsta värdet på den lagerplatsen och genom att välja högst och lägst ser datagrupperingsprocessen till att alla viktiga höga eller låga värden samlas in och återges i det visuella objektet.

Om du tycker att det låter som mycket analys för att tillfälliga avvikare ska kunna hämtas och visas korrekt i det visuella objektet – har du rätt. Och det är den exakta orsaken bakom den nya algoritmen och datagrupperingsprocessen.

## <a name="tooltips-and-high-density-line-sampling"></a>Knappbeskrivningar och högdensitetssampling av linjer
Det är viktigt att notera att datagrupperingsprocessen – som resulterar i att det lägsta och högsta värdet på en viss lagerplats kan hämtas och visas i det visuella objektet – kan påverka hur knappbeskrivningarna visar data när du hovrar över datapunkter. För att förklara hur och varför detta sker kan vi gå tillbaka till vårt exempel om aktiekurser tidigare i den här artikeln.

Anta att du skapar ett visuellt objekt baserat på aktiekurs och du jämför två olika aktier, där båda använder **högdensitetssampling**. Underliggande data för varje serie har många datapunkter (kanske hämtar du aktiekursen en gång i sekunden på dagen). Algoritmen för högdensitetssampling av linjer utför datagruppering för varje serie oberoende av den andra.

Nu antar vi att den första aktien ökar kraftigt kl. 12:02 och snabbt går ner tio sekunder senare – det är en viktig datapunkt. När datagrupperingen inträffar för aktien blir det högsta värdet kl. 12:02 en representativ datapunkt för lagerplatsen.

Men den andra aktien hade varken en högsta eller lägsta kurs kl. 12:02 på lagerplatsen som ingick – kanske inträffade högsta och lägsta värde för lagerplatsen som innehöll 12:02 tre minuter senare. I den situationen, när linjediagrammet skapats och du hovrar över 12:02, visas ett värde i knappbeskrivningen för den första aktien (eftersom den steg vid 12:02 och värdet valdes som lagerplatsens högsta datapunkt), men du kommer *inte* att se något värde i knappbeskrivningen kl. 12:02 för det andra aktien. Det beror på att det andra aktien varken hade en hög eller låg kurs för lagerplatsen med 12:02. Så det finns inte några data att visa för det andra aktien kl. 12:02 och därför visas inga knappbeskrivningsdata.

Detta sker ofta i knappbeskrivningar. Höga och låga värden för en viss lagerplats överensstämmer inte alltid perfekt med jämnt skalade x-axelvärden och därmed visar inte knappbeskrivningen värdet.  

## <a name="how-to-turn-on-high-density-line-sampling"></a>Hur du aktiverar högdensitetssampling av linjer
Den nya algoritmen är som standard **På**. Du kan ändra den här inställningen genom att gå till fönstret **Formatering** i kortet **Allmänt**. Längst ned visas ett skjutreglage med namnet **högdensitetssampling**. Om du vill inaktivera den drar du reglaget till **Av**.

![](media/desktop-high-density-sampling/high-density-sampling_02.png)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
Den nya algoritmen för högdensitetssampling av linjer är en viktig förbättring i Power BI, men det finns några saker du behöver veta när du arbetar med högdensitetsvärden och data.

* På grund av ökad granularitet och datagrupperingsprocessen kan **knappbeskrivningarna** endast visa ett värde om representativa data justeras med markören. Se avsnittet tidigare i artikeln om **Knappbeskrivningar** för mer information.
* När storleken på en allmän datakälla är för stor, eliminerar den nya algoritmen serier (förklaringselement) för att anpassa den maximala begränsningen vid import.
  
  * I den här situationen sorterar den nya algoritmen förklaringarna i alfabetisk ordning och börjar gå nedåt i listan med förklaringselement i alfabetisk ordning tills dataimportens maximum har nåtts. Ytterligare serier importeras inte.
* När en underliggande datauppsättning har mer än 60 serier (maximalt antal serier enligt beskrivningen tidigare), sorteras den nya algoritmen i alfabetisk ordning och eliminerar serier utöver den 60:e serien som sorterats i alfabetisk ordning.
* Om datavärdena inte är av typen *numerisk* eller *datum/tid*, kommer Power BI inte använda den nya algoritmen och återgår till den tidigare algoritmen (ej högdensitetssampling).
* Inställningen **Visa objekt utan data** stöds inte med den nya algoritmen.
* Den nya algoritmen stöds inte när du använder en live-anslutning till en modell som finns i SQL Server Analysis Services (version 2016 eller tidigare). Den stöds i modeller som finns i **Power BI** eller Azure Analysis Services.

## <a name="next-steps"></a>Nästa steg
Information om högdensitetssampling i punktdiagram finns i följande artikel.

* [Högdensitetssampling i Power BI-punktdiagram](desktop-high-density-scatter-charts.md)

