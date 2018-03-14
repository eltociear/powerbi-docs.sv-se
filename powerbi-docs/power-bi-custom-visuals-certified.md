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
ms.date: 02/13/2018
ms.author: mihart
ms.openlocfilehash: cc50e4e8830aca3951da6004b8ada3913aff28ed
ms.sourcegitcommit: 743e44fc8730fea0f7149916080b0c6d7eb6359d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2018
---
# <a name="getting-a-custom-visual-certified"></a>Få anpassade visuella objekt *certifierade*
## <a name="what-is-meant-by-certified"></a>Vad menas med begreppet *certifierad*?
En *certifierade visualisering* är en som uppfyller en uppsättning kodkrav och har klarat strikta säkerhetstest.  När anpassade visuella objekt har certifierats kan de [exporteras till PowerPoint](service-publish-to-powerpoint.md) och visas i de e-postmeddelanden som tas emot när en användare [prenumererar på rapportsidor](service-report-subscribe.md). Naturligtvis kan den också användas som [anpassade visuella objekt som är standard](power-bi-custom-visuals.md) som läggs till i Power BI-tjänsten och Power BI Desktop-rapporter och visas i Power BI Mobile och Embedded.

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
| [Association Rules](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380815) | |
| [Aster-punktdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft-kalender](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381096) | |
| [Bowtie-diagram från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380838) | [Video](https://youtu.be/So5xKMSpVJI) |
| [Box and Whisker-diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380831) | |
| [Box- och Whisker-diagram från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381351) | [Video](https://youtu.be/JoHaFLfhXdo) |
| [Tegelstensdiagram från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380836) | [Video](https://youtu.be/hA3DOsvn2xY) |
| [Bubbeldiagram från Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381340) | |
| [Bullet Chart](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380755) | [Video](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart från OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380953) | [Video](https://youtu.be/mtvUNl9bMjA) |
| [Kalendar från Tallan](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381146) | |
| [Stearinljusstapel av OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380952) | [Video](https://youtu.be/nT_18gyRxPo) |
| [Kortet med tillstånd av OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380967) | |
| [Chiclet-utsnitt](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380761) | [Video](https://youtu.be/AQvd2FhRyCI) |
| [Cirkelmätare från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380837) | [Video](https://youtu.be/9NHXALkBXuY) |
| [Klusterkarta](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380806) | |
| [Klustring](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380861) | |
| [Klustring med extremvärden](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380889) | |
| [Korrelationsrityta](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380814) | |
| [Cirkelmätare från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380874) | [Video](https://youtu.be/DgdoWi7Gcxo) |
| [Beslutsträddiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380817) | |
| [Radiell mätare](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381184) | |
| [Punktritning](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380760) | |
| [Punktdiagram från OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380949) | [Video](https://youtu.be/By16pX9KT40) |
| [Detaljgranska Cartogram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381045) | |
| [Detaljgranska Choropleth](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381044) | |
| [Stapeldiagram med ökad detaljnivå](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380857) | [Video](https://youtu.be/lBy2gQQ5YsQ) |
| [Kolumndiagram med ökad detaljnivå för tidsbaserade data](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380881) | [Video](https://youtu.be/T_mRou18vx0) |
| [Ringdiagram med ökad detaljnivå](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380858) | [Video](https://youtu.be/AUVFrSHmPeo) |
| [Dubbel KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380774) | |
| [Förbättrat punktdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380762) | [Video](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380849) | |
| [Enlighten-våffeldiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380850) | |
| [Force-Directed-diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380764) | [Video](https://youtu.be/YsTa7uyJ4sg) |
| [Prognosticering av TBATS](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381326) | |
| [Prognosticering med ARIMA](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380888) | |
| [Tratt med källa från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381334) | [Video](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380765) | [Video](https://youtu.be/qJ7s_KrGiUU) |
| [Gantt-diagram från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381364) | [Video](https://youtu.be/vJLV9JRCpI8) |
| [Globdatastaplar](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381344) | |
| [Hierarkidiagram från Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381333) | [Video](https://youtu.be/0ZGzJaq_KT4) |
| [Histogramdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380776) | |
| [Histogram med punkter från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381032) | [Video](https://youtu.be/-ILF--wExrw) |
| [Vågrät tratt från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380846) | [Video](https://youtu.be/SudZei68PPo) |
| [Bild från CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381297) | |
| [Bildrutnät](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381355) | |
| [Infographic Designer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380898) | |
| [KPI-diagram från Akvelon](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381432) | |
| [KPI-indikator](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380946) | [Video](https://youtu.be/cudG4gsZ2V8) |
| [Linjär mätare från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380821) | [Video](https://youtu.be/7_jFaM30dkc) |
| [LineDot-diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380766) | |
| [Mekko-diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380785) | [Video](https://youtu.be/90FLCKpgicA) |
| [Uppspelningsaxel (dynamiskt utsnitt)](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381083) | [Video](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI-matris](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381299) | [Video](https://youtu.be/1enze8pcGzY) |
| [Kvadrantdiagram från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381011) | [Video](https://youtu.be/ppBnyhqWNC0) |
| [Polärdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380771) | |
| [Ringdiagram från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380824) | [Video](https://youtu.be/pDToHDFHnq8) |
| [Roterande diagram från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381007) | [Video](https://youtu.be/d5xBCMmb3hU) |
| [Sankey-diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380777) | [Video](https://youtu.be/WWP9wVUHGaA) |
| [Rullningsdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381018) | |
| [Smart Filter från SQLBI](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380859) | [Video](https://youtu.be/gcJsDDRQq28) |
| [Miniatyrdiagram från OKViz](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380910) | [Video](https://youtu.be/0m3Vnvso9tY) |
| [Spline-diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380860) | |
| [Stream-diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380772) | |
| [Solstråle](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380767) | |
| [Termisk tabellkarta](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380818) | |
| [Tachometer](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380937) | [Video](https://youtu.be/C3OXdETbS9o) |
| [Textfilter](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381309) | |
| [Text Wrapper från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380826) | |
| [Termometer](https://appsource.microsoft.com/en-us/product/office/WA104379807) | |
| [Tidsseriefördelningsdiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380897) | |
| [Prognosticeringsdiagram för tidsserier](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380816) | |
| [Tidslinjeutsnitt](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380786) | [Video](https://youtu.be/ozMtZ4_NZ10) |
| [Storm-diagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380768) | [Video](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Handelsdiagram från MAQ Software](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380823) | [Video](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate-avvikelse](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381140) | [Video](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380956) | [Video](https://youtu.be/0BZsVCQdEkc) |
| [Lista över användare från CloudScope](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381426) | |
| [Våffeldiagram](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104381049) | [Video](https://youtu.be/1vRqYUsm3Vk) |
| [Ordmoln](https://appsource.microsoft.com/en-us/product/power-bi-visuals/WA104380752) | [Video](https://youtu.be/AblTenl9fqo) |

## <a name="next-steps"></a>Nästa steg
[Komma igång med utvecklarverktyg för anpassade visuella objekt (förhandsversion)](service-custom-visuals-getting-started-with-developer-tools.md)      
[Microsofts spelningslista om anpassade visuella objekt på YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
[Visualiseringar i Power BI](power-bi-report-visualizations.md)  
[Anpassade visualiseringar i Power BI](power-bi-custom-visuals.md)  
[Publicera anpassad visuell information till Microsoft AppSource](developer/office-store.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

