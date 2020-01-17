---
title: Stora datamängder, datapunktsbegränsningar och datastrategier
description: Databegränsningar för visuella objekt och strategier för dataminskning
author: mihart
ms.reviewer: justyna
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/10/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 320e8a25206a069c43800295ab64a7ab87afbcf0
ms.sourcegitcommit: 801d2baa944469a5b79cf591eb8afd18ca4e00b1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885265"
---
# <a name="apply-data-point-limits-and-strategies-by-visual-type"></a>Använda datapunktsbegränsningar och strategier efter visuell typ

När man renderar ett visuellt objekt i Power BI måste visualiseringen vara snabb och exakt. Det kräver underliggande algoritmer som konfigurerats för varje visuell typ. Visuella objekt i Power BI måste vara tillräckligt flexibla för att hantera datauppsättningar med olika storlekar. Vissa datauppsättningar har bara ett fåtal datapunkter, medan andra datauppsättningar har flera petabyte med datapunkter. Den här artikeln beskriver de strategier som används av Power BI för att rendera visualiseringar.

## <a name="data-reduction-strategies"></a>Strategier för dataminskning
Varje visualisering använder en eller flera *dataminskningsstrategier* för att hantera de potentiellt stora mängder data som analyseras. Även en enkel tabell använder en strategi för att undvika att läsa in hela datauppsättningen till klienten.  Vilken minskningsstrategin som används varierar efter visuell typ. Varje visuellt objekt väljer bland de *dataminskningsstrategier* som stöds som en del av genereringen av databegäran som skickas till servern. 

Varje visuellt objekt styr strategiernas parametrar för att påverka den totala mängden data.   

## <a name="strategies"></a>Strategier
För varje strategi finns det standardvärden som baseras på den form och den typ av data som visualiseras. Standardinställningarna kan dock åsidosättas i formateringsfönstret i Power BI för att ge rätt användarupplevelse. 

* **Datafönsterhantering** (segmentering): Tillåt användare att bläddra igenom data i ett visuellt objekt genom att på ett progressivt sätt läsa in delar av den övergripande datamängden.
* **TopN**: Visa endast de första N objekten
* **Enkelt exempel**: Visa det första objektet, det sista objektet och N jämnt fördelade objekt däremellan.
* **BottomN**: Visa endast de sista N objekten.  Praktiskt vid övervakning av ofta uppdaterade data.
* **Högdensitetssampling** – En förbättrad samplingsalgoritm som respekterar extremvärden och/eller formen på en kurva på ett bättre sätt.
    * **Diskretiserad radsampling** – Exempeldatapunkter baseras på extremvärden i diskretiseringar längs en axel
    * **Överlappande punktsampling** – Exempeldatapunkter baseras på överlappande värden för att bevara extremvärden

## <a name="statistics"></a>Statistik
Vissa modeller kan tillhandahålla statistik om antalet värden för vissa kolumner. När det finns sådan information kan vi använda den informationen för att ge bättre belastningsutjämning över flera hierarkier, om ett visuellt objekt inte uttryckligen åsidosätter antalet värden för en strategi.

Mer information finns i [Nyheter i Analysis Services](https://docs.microsoft.com/sql/analysis-services/what-s-new-in-analysis-services?view=sql-server-2017)

## <a name="dynamic-limits"></a>Dynamiska gränser
Utöver strategierna ovan använder visuella objekt med två hierarkier med grupperade kolumner (axel och förklaring eller kategori och serie) en ytterligare strategi för som kallas för *dynamiska gränser*.  Dynamiska gränser har utformats för att skapa en bättre balans mellan datapunkter. 

Dynamiska gränser ger ett bättre val av punkter för spridda data än statiska gränser skulle göra. Till exempel kan ett visuellt objekt konfigureras för att välja 100 kategorier och 10 serier med totalt 1 000 punkter. Men data i det aktuella fallet har 50 kategorier och 20 serier.  När frågan körs väljer dynamiska gränser alla 20 serierna för att fylla de 1 000 datapunkter som begärdes.

Dynamisk begränsningar tillämpas automatiskt när servern har följande kapacitet:

* I Power BI Desktop med en lokal SSAS version från 2016 eller senare som [utnyttjar serverns SuperDax-kapacitet](https://blogs.msdn.microsoft.com/analysisservices/2015/09/02/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3/)

* I Desktop och Power BI-tjänsten när du använder en importerad modell, Direct Query, ansluter live till tjänsten eller ansluter live till AS PaaS. 

* Du kan inte använda dynamiska gränser i Power BI-tjänsten när du ansluter via en lokal gateway till en lokal SSAS. Den lokala gatewayen stöder inte strategin med dynamiska gränser som returnerar en annan struktur med resultatuppsättningar från en lokal SSAS fullt ut.  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>Strategier och datapunktsbegränsningar efter visuell typ

### <a name="area-chart"></a>Ytdiagram
Se [hur radsampling fungerar](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>Stapel-/kolumndiagram
- I kategoriskt läge
    - Kategorier: Virtualisering med fönster med 500 rader i taget
    - Serie: Översta 60
    - I skalärt läge (kan använda dynamiska gränser)
        - Maximalt antal punkter: 10 000
        - Kategorier: Exempel på 500 värden
        - Serie: Översta 20 värden

### <a name="card-multirow"></a>Kort (flera rader) 
- Värden: Virtualisering med fönster med 200 rader i taget

### <a name="combo-chart"></a>Kombinationsdiagram
 Använder samma strategier som stapeldiagram. Observera att raden i **kombinationsdiagrammet** inte använder högdensitetsalgoritmen som **linjediagrammet** använder.

### <a name="custom-visuals"></a>Anpassade visuella objekt
Kan få upp till 30 000, men det är upp till författarna av de visuella objekten att ange vilka strategier som ska användas. Standardgränsen är 1 000, men den som skapat det visuella objektet kan ändra det här värdet upp till som högst 30 000.

### <a name="doughnut"></a>Ringdiagram
- Maximalt antal punkter: 3 500
- Grupp: 500 översta
- Detaljer: Översta 20

### <a name="filled-map-choropleth"></a>Fylld koropletkarta 
Den fyllda kartan kan använda statistik eller dynamiska gränser. Power BI försöker använda minskning i följande ordning: dynamiska gränser, statistik och till sist konfiguration. 
- Maximalt antal punkter: 10 000
- Kategorier: 500 översta
- Serie (när det finns både X- och Y): Översta 20

### <a name="funnel"></a>Tratt
- Maximalt antal punkter: 3 500
- Kategorier: 3 500 översta

### <a name="kpi"></a>KPI
- Trendaxel
- 3 500 lägsta

### <a name="line-chart"></a>Linjediagram
Se [hur radsampling fungerar](../desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>Linjediagram, hög densitet
Se [Högdensitetssampling](../desktop-high-density-sampling.md)

### <a name="map"></a>Karta 
- Maximalt antal punkter: 3 500

Beroende på konfigurationen, kan en karta ha:
- Plats: 3 500 översta
- Plats, storlek: 3 500 översta
- Aggregeringar för plats, latitud och longitud (+/-storlek): 3 500 översta
- Latitud, longitud: se [Punktdiagram med hög densitet](desktop-high-density-scatter-charts.md)
- Latitud, longitud, storlek: 3 500 översta
- Förklaring, latitud, longitud: se [Punktdiagram med hög densitet](desktop-high-density-scatter-charts.md)
- Förklaring, latitud, longitud, storlek: Översta 233 förklaringarna, översta 15 latituder och longituder (kan använda statistik eller dynamiska gränser)
- Plats, förklaring, latitud, longitud som aggregeringar (+/-storlek): Översta 233 platserna, översta 15 förklaringarna (kan använda statistik eller dynamiska gränser)

### <a name="matrix"></a>Matris
- Rader: Virtualisering med fönster med 500 rader i taget
- Kolumner: 100 översta grupperade kolumner 
- Värden: flera värden räknas inte mot dataminskningen

### <a name="powerapps-visual"></a>Visuellt PowerApps-objekt
Kan få upp till 30 000, men det är upp till författarna av de visuella objekten att ange vilka strategier som ska användas. Standardgränsen är 1 000, men den som skapat det visuella objektet kan ändra det här värdet upp till som högst 30 000.

### <a name="radial-gauge"></a>Radiell mätare
Ingen strategi för dataminskning

### <a name="slicer"></a>Utsnitt
- Värden: Virtualisering med fönster med 200 rader i taget

### <a name="scatter-chart-high-density"></a>Punktdiagram (hög densitet)
Se [Punktdiagram med hög densitet](https://docs.microsoft.com/power-bi/visuals/desktop-high-density-scatter-charts)

### <a name="pie"></a>Cirkel
- Maximalt antal punkter: 3 500
- Grupp: 500 översta
- Detaljer: Översta 20

### <a name="r--python-visuals"></a>R- och Python-visualiseringar
Begränsat till 150 000 rader. Om fler än 150 000 rader har valts används endast de översta 150 000 raderna

### <a name="ribbon-chart"></a>Banddiagram
- I kategoriskt läge
    - Kategorier: Virtualisering (med fönster) med 500 rader i taget
    - Serie: Översta 60
    - I skalärt läge (kan använda dynamiska gränser)
        - Maximalt antal punkter: 10 000
        - Kategorier: Exempel på 500 värden
        - Serie: Översta 20 värden

### <a name="shape-map-preview"></a>Formkarta (förhandsversion)
Formkartan kan använda statistik eller dynamiska gränser. 
- Maximalt antal punkter: 1500
- Kategorier: 500 översta

### <a name="table"></a>Tabell
- Värden: Virtualisering (med fönster) med 500 rader i taget

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>Trädkarta (kan använda statistik eller dynamiska gränser)
- Maximalt antal punkter: 3 500
- Grupp: 500 översta
- Detaljer: Översta 20

### <a name="waterfall-chart"></a>Vattenfallsdiagram
- När endast kategoribucketen finns
    - Maximalt antal punkter: 3 500
    - Endast kategori − 3 500 översta
- När både kategori och analys på detaljnivå finns
    - Kategori: Virtualisering (med fönster) med 30 rader i taget
    - Analys − 200 översta värdena


## <a name="next-steps"></a>Nästa steg
[Visualiseringstyper](power-bi-report-visualizations.md)
