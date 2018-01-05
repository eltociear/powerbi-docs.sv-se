---
title: Certifierade anpassade visualiseringar i Power BI
description: "Krav och processer för att skicka en visualisering för certifiering. Och en lista över redan certifierad anpassad visuell information."
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
featuredvideoid: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/20/2017
ms.author: mihart
ms.openlocfilehash: 3d51475b300fadc55f33960b03c3adc0031a39b8
ms.sourcegitcommit: 12236d08c27c7ee3fabb7ef9d767e9dee693f8aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/21/2017
---
# <a name="getting-a-custom-visual-certified"></a>Få anpassade visuella objekt *certifierade*
## <a name="what-is-meant-by-certified"></a>Vad menas med begreppet *certifierad*?
En *certifierade visualisering* är en som uppfyller en uppsättning kodkrav och har klarat strikta säkerhetstest.  När anpassade visuella objekt har certifierats kan de [exporteras till PowerPoint](service-publish-to-powerpoint.md) och visas i de e-postmeddelanden som tas emot när en användare [prenumererar på rapportsidor](service-report-subscribe.md).

Är du webbutvecklare och intresserad av att skapa egna visualiseringar och lägga till dem i [Microsoft AppSource](https://appsource.microsoft.com)? Se [Kom igång med utvecklingsverktyg](service-custom-visuals-getting-started-with-developer-tools.md) för att lära dig hur.


## <a name="certification-requirements"></a>Certifieringskrav
* Godkänt för Microsoft AppSource    
* Anpassade visuella objekt skrivs med version av API 1.2 eller högre    
* Databas som är tillgänglig för granskning (t.ex. visuell kod som är tillgänglig för oss via GitHub)    
* Använder endast offentliga OSS-komponenter som kan granskas    
* Har inte tillgång till externa tjänster eller resurser    

> **Tips**: Vi rekommenderar att du använder EsLint med standardsäkerhetsregler för att kontrollera koden innan den skickas.
> 
> 

## <a name="process-for-submitting-a-custom-visual-for-certification"></a>Processen för att skicka ett anpassat visuellt objekt för certifikatutfärdare
Gör så här för att skicka ett anpassat visuellt objekt för certifikatutfärdare:

1. Skicka ett e-postmeddelande till supporten för anpassade visuella objekt i Power BI (pbicvsupport@microsoft.com). Inkludera följande information i e-postmeddelandet:    
   
   * Ämne: Begäran om certifiering av visuellt objekt    
   * Länk till GitHub-lagringsplatsen där källkoden för det visuella objektet finns    
   * Uppfyll kraven (se ovan)    
   * Bli godkänt i kod- och säkerhetsgranskningen    
2. Teamet för anpassade visuella objekt hos Microsoft informerar dig när ditt anpassade visuella objekt har certifierats och lagts till i listan över certifierade objekt (nedan) eller avvisats med en rapport som innehåller fel som ska åtgärdas. Det är utvecklarens ansvar för att kommunicera med Microsoft och för att uppdatera sina certifierade visuella objekt vid behov.

## <a name="removal-of-power-bi-certified-custom-visuals"></a>Borttagning av Power BI-certifierade anpassade visuella objekt
Microsoft kan ta bort visuella objekt från listan över certifierade objekt efter eget gottfinnande.  

## <a name="list-of-custom-visuals-that-have-been-certified"></a>Lista över certifierade visuella objekt
| Länk till AppSource | Länk till video |
| --- | --- |
| [Aster-punktdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759?src=office&tab=Overview) | |
| [Bowtie-diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838?src=office&tab=Overview) |[Video](https://youtu.be/So5xKMSpVJI) |
| [BciCalendar (Beyondsoft Calendar)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096?src=office&tab=Overview)  | |
| [Box and Whisker](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831?src=office&tab=Overview) | |
| [Bullet Chart](https://store.office.com/app.aspx?assetid=WA104380755) |[Video1](https://youtu.be/AOlsFYkfkcw)   [Video2](https://youtu.be/AQvd2FhRyCI) |
| [Bullet Chart från OKViz](https://store.office.com/bullet-chart-by-okviz-WA104380953.aspx) |[Video](https://youtu.be/mtvUNl9bMjA) |
| [Kalendar från Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146?src=office&tab=Overview) | |
| [Chiclet-utsnitt](https://store.office.com/chiclet-slicer-WA104380756.aspx) |[Video](https://youtu.be/iYOkJ1APueY) |
| [Ackorddiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761?src=office&tab=Overview) |[Video](https://youtu.be/AQvd2FhRyCI) |
| [Cirkelmätare från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837?tab=Overview) | |
| [Cylindrisk mätare](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | |
| [Radiell mätare](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) |[Video](https://youtu.be/AOlsFYkfkcw) |
| [Toroid (ringdiagram) från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824?tab=Overview) |[Video](https://youtu.be/pDToHDFHnq8) |
| [Punktdiagram från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104381101?src=office&tab=Overview) |[Video](https://youtu.be/4lskRgcpFJY) |
| [Drill-down toroid från ZoomCharts](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | |
| [Dubbel KPI](https://store.office.com/dual-kpi-WA104380774.aspx) |[Video](https://youtu.be/821o0-eVBXo?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112?src=office&tab=Overview) | |
| Enlighten World Flags – kommer snart | |
| Enlighten Stack Shuffle – kommer snart | |
| [Gantt](https://store.office.com/gantt-WA104380765.aspx) |[Video](https://youtu.be/qJ7s_KrGiUU) |
| [Histogram](https://store.office.com/histogram-chart-WA104380776.aspx) | |
| [Vågrät tratt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) |[Video](https://youtu.be/SudZei68PPo) |
| [KPI-indikator](https://store.office.com/kpi-indicator-WA104380832.aspx) | |
| [Linjär mätare från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821?src=office&tab=Overview) |[Video](https://youtu.be/AOlsFYkfkcw) |
| [Mekko-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785?src=office&tab=Overview)  | [Video](https://youtu.be/90FLCKpgicA)|
| [Uppspelningsaxel (dynamiskt utsnitt)](https://store.office.com/play-axis-dynamic-slicer-WA104380981.aspx) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) |[Video](https://youtu.be/IvfIP3E6-1Q) |
| [Polärdiagram](https://store.office.com/radar-chart-WA104380771.aspx) | |
| [Ringdiagram (Toroid) från MAQSoftware](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824?src=office&tab=Overview) | [Video](https://youtu.be/pDToHDFHnq8)|
| [Sankey-diagram](https://store.office.com/app.aspx?assetid=WA104380777.aspx) |[Video](https://youtu.be/WWP9wVUHGaA) |
| [Rullningsdiagram](https://store.office.com/scroller-WA104381018.aspx) |[Video](https://youtu.be/uhRFQF2cGSY) |
| [Smart Filter från SQLBI](https://store.office.com/smart-filter-by-okviz-WA104380859.aspx) |[Video](https://youtu.be/gcJsDDRQq28) |
| [Miniatyrdiagram från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910?src=office&tab=Overview) |[Video](https://youtu.be/0m3Vnvso9tY) |
| [Solstråle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767?src=office&tab=Overview) | |
| [Tachometer](https://store.office.com/tachometer-WA104380937.aspx?) |[Video](https://www.youtube.com/watch?v=C3OXdETbS9o) |
| [Termometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847?src=office&tab=Overview) | [Video](https://youtu.be/SPX9mgrAdBc)|
| [Tidsseriefördelning](https://appsource.microsoft.com/product/power-bi-visuals/WA104380897) | |
| [Termisk tabellkarta](https://store.office.com/table-heatmap-WA104380818.aspx) | |
| [Textomslutning](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Tidslinje-utsnitt](https://store.office.com/timeline-slicer-WA104380786.aspx) |[Video](https://youtu.be/ozMtZ4_NZ10) |
| [Storm-diagram](https://store.office.com/tornado-chart-WA104380768.aspx) |[Video](https://youtu.be/AQvd2FhRyCI) |
| [Våffeldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049?src=office&tab=Overview) |[Video](https://youtu.be/1vRqYUsm3Vk) |
| [Ordmoln](https://store.office.com/word-cloud-WA104380752.aspx?) |[Video](https://www.youtube.com/watch?v=AblTenl9fqo) |

## <a name="next-steps"></a>Nästa steg
[Komma igång med utvecklarverktyg för anpassade visuella objekt (förhandsversion)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Microsofts spelningslista om anpassade visuella objekt på YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualiseringar i Power BI](power-bi-report-visualizations.md)  
[Anpassade visualiseringar i Power BI](power-bi-custom-visuals.md)  
[Publicera anpassad visuell information till Microsoft AppSource](developer/office-store.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

