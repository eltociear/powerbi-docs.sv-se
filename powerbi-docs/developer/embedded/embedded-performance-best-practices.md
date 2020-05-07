---
title: Bästa praxis för Power BI Embedded-prestanda
description: Den här artikeln innehåller riktlinjer för bästa praxis för inbäddad analys
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: 7284532d95cce780f4022477faab9033adcd764a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "79492616"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Bästa praxis för Power BI Embedded-prestanda

Den här artikeln innehåller rekommendationer för snabbare rendering av rapporter, instrumentpaneler och paneler i ditt program.

> [!Note]
> Kom ihåg att inläsningstiden huvudsakligen beror på element som är relevanta för själva rapporten och data, däribland visuella objekt, storleken på data samt komplexiteten för frågorna och beräknade mått. Mer information finns i [Power BI-optimeringsguiden](../../guidance/power-bi-optimization.md).

## <a name="update-tools-and-sdk-packages"></a>Uppdatera verktyg och SDK-paket

Se till att verktyg och SDK-paket är uppdaterade.

* Använd alltid den senaste versionen av [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

* Installera den senaste versionen av [Power BI-klientens SDK](https://github.com/Microsoft/PowerBI-JavaScript). Vi släpper kontinuerligt ytterligare förbättringar, så se till att kontrollera dem med jämna mellanrum.

## <a name="embed-parameters"></a>Parametrar för inbäddning

Metoden `powerbi.embed(element, config)` tar emot ett element och en config. Config-parametern innehåller fält som rör prestanda.

### <a name="embed-url"></a>Inbäddnings-URL

Undvik att generera inbäddnings-URL:en själv. Se i stället till att hämta inbäddnings-URL:en genom att anropa API:et för att [hämta rapporter](/rest/api/power-bi/reports/getreportsingroup), [hämta instrumentpaneler](/rest/api/power-bi/dashboards/getdashboardsingroup) eller [hämta paneler](/rest/api/power-bi/dashboards/gettilesingroup). Vi har lagt till en ny parameter i URL-adressen som heter **_config_** och som används för att förbättra prestandan.

### <a name="permissions"></a>Behörigheter

Ange behörigheter för **visning** om du inte har för avsikt att bädda in en rapport i redigeringsläget. På så sätt initierar inbäddningskod inte komponenter som används i redigeringsläget.

### <a name="filters-bookmarks-and-slicers"></a>Filter, bokmärken och utsnitt

Vanligtvis sparas visuella rapportobjekt med cachelagrade data. Cachelagrade data används för att ge upplevd prestanda. Rapporter återger cachelagrade data medan frågor körs. Om filter, bokmärken eller utsnitt tillhandahålls är cachelagrade data inte relevanta, och de visuella objekten renderas först när den visuella frågan har avslutats.

Om du bäddar in rapporter med samma filter, bokmärken och utsnitt kan du förbättra prestanda genom att spara rapporten med redan tillämpade filter, bokmärken och utsnitt. Detta renderar rapporten med cachelagrade data som innehåller filter, bokmärken och utsnitt.

## <a name="switching-between-reports"></a>Växla mellan rapporter

När du bäddar in flera rapporter i samma iframe ska du inte generera en ny iframe för varje rapport. Använd i stället `powerbi.embed(element, config)` med en annan config för att bädda in den nya rapporten.

> [!NOTE]
> Växling mellan rapporter för ett ”App äger data”-scenario är kanske inte särskilt effektivt på grund av att en ny inbäddningstoken måste skapas.

## <a name="query-caching"></a>Cachelagring av frågor

Organisationer med Power BI Premium-kapacitet eller Power BI Embedded-kapacitet kan dra nytta av cachelagring av frågor för att få snabbare rapporter som är associerade med en datamängd.

[Läs mer om cachelagring av frågor i Power BI](../../power-bi-query-caching.md).

## <a name="preload"></a>Förinläsning

Använd `powerbi.preload()` för att förbättra slutanvändarprestandan. Metod `powerbi.preload()` laddar ned javascript, css-filer och andra artefakter som används senare för att bädda in en rapport.

Anropa `powerbi.preload()` om du inte tänker bädda in rapporten direkt. Om det Power BI-inbäddade innehållet till exempel inte visas på startsidan, använder du `powerbi.preload()` för att hämta och cachelagra de artefakter som används för att bädda in innehållet.

## <a name="bootstrapping-the-iframe"></a>Använda bootstrap för iframe

> [!NOTE]
> [Power BI-klient-SDK](https://github.com/Microsoft/PowerBI-JavaScript) version 2.9 krävs för att använda bootstrap för iframe.

`powerbi.bootstrap(element, config)` gör att du kan börja bädda in innan alla nödvändiga parametrar är tillgängliga. Bootstrap-API:et förbereder och initierar iframe.
När du använder bootstrap-API:et behöver det fortfarande anropa `powerbi.embed(element, config)` på samma HTML-element.

Ett av användningsfallen för den här funktionen är till exempel att köra startprogrammet för iframe och serverdelsanrop för inbäddning parallellt.
> [!TIP]
> Använd bootstrap-API:et när det är möjligt att generera iframe innan det är synligt för slutanvändaren.

[Lär dig mer om iframe-bootstrap](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance).

## <a name="measure-performance"></a>Mäta prestanda

### <a name="performance-events"></a>Prestandahändelser

Du kan använda två händelser för att mäta inbäddad prestanda:

1. Inläst händelse: Tiden tills rapporten initieras (Power BI-logotypen försvinner när inläsningen är klar).
2. Renderad händelse: Tiden tills rapporten har renderats helt, med hjälp av faktiska data. Den renderade händelsen utlöses varje gång rapporten renderas på nytt (till exempel efter att filter har tillämpats). När du mäter en rapport bör du se till att utföra beräkningarna i den händelse som aktiveras först.

Cachelagrade data renderas när de är tillgängliga, men det genereras ingen ytterligare händelse.

[Läs mer om händelsehantering](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events).

### <a name="performance-analyzer"></a>Prestandaanalyserare

För att undersöka prestanda för rapportelementen kan du använda Prestandaanalys i Power BI Desktop.
Med Prestandaanalys kan du se och registrera loggar som mäter hur var och en av dina rapportelement presterar.

[Läs mer om Prestandaanalys](../../desktop-performance-analyzer.md).

> [!NOTE]
> Kom alltid ihåg att jämföra prestanda för den inbäddade rapporten med prestanda på powerbi.com. Detta kan hjälpa dig att förstå orsaken till dina prestandaproblem

## <a name="next-steps"></a>Nästa steg

* [Power BI-optimeringsguiden](../../guidance/power-bi-optimization.md)
* [Så här felsöker du problem i Power BI Embedded](embedded-troubleshoot.md)
* [Vanliga frågor och svar om Power BI Embedded](embedded-faq.md)
