---
title: Certifierade visuella Power BI-objekt
description: Krav och processer för att skicka en visualisering för certifiering. Och en lista över redan certifierade visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: 0a39496ade27cd45fae116eea92ef4b472e04582
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999754"
---
# <a name="get-a-power-bi-visual-certified"></a>Certifiera ett visuellt Power BI-objekt

Certifierade visuella Power BI-objekt är visuella objekt på *Marketplace* som uppfyller vissa *specificerade* kodkrav som *Microsoft Power BI-teamet* har testat och godkänt. Testerna är utformade för att kontrollera att det visuella objektet inte har tillgång till externa tjänster eller resurser.

Certifierade visuella Power BI-objekt används som [standardinställda visuella Power BI-objekt](power-bi-custom-visuals.md). Du kan lägga till dem i [Power BI-Desktop](../desktop-what-is-desktop.md) och [Power BI-tjänsten](../power-bi-service-overview.md) och visa dem med [Power BI Mobile](../consumer/mobile/mobile-apps-for-mobile-devices.md) och [Power BI Embedded ](embedding.md).

Certifieringsprocessen är en valfri process. Det är upp till utvecklaren att bestämma om det visuella Power BI-objektet i Marketplace ska certifieras. När ett visuellt Power BI-objekt har certifierats erbjuder det fler funktioner. Du kan [exportera det till PowerPoint](../consumer/end-user-powerpoint.md) och du kan visa det visuella objektet i e-postmeddelanden när en användare [prenumererar på rapportsidor](../consumer/end-user-subscribe.md).

Ocertifierade visuella Power BI-objekt innebär inte nödvändigtvis osäkra visuella objekt. Vissa visuella objekt är inte certifierade eftersom de inte är kompatibla med ett eller flera av [certifieringskraven](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Till exempel att ansluta till en extern tjänst som visuell mappning eller visuella objekt med kommersiella bibliotek.

Om du är webbutvecklare som är intresserad av att skapa egna visuella Power BI-objekt och lägga till dem i  [Microsoft AppSource](https://appsource.microsoft.com) kan du börja du med självstudien  [Utveckla ett visuellt Power BI-objekt](visuals/custom-visual-develop-tutorial.md).

> [!NOTE]
> **Microsoft** är *inte* författare till visuella Power BI-objekt från tredje part. Vi rekommenderar att kunder kontaktar upphovsmannen direkt för att verifiera funktionaliteten för visuella objekt från tredje part.

> [!IMPORTANT]
> Microsoft kan ta bort visuella Power BI-objekt från [listan över certifierade objekt](#list-of-power-bi-visuals-that-have-been-certified) efter eget gottfinnande.

## <a name="certification-requirements"></a>Certifieringskrav

Se till att visuella Power BI-objekt uppfyller de krav som anges i det här avsnittet för att [certifiera](#get-a-power-bi-visual-certified) ditt visuella Power BI-objekt. 

> [!TIP]
> Vi rekommenderar att du använder EsLint med standardsäkerhetsregler för att kontrollera koden innan den skickas.

* Godkänd för Microsoft Seller Dashboard eller Partner Center. Ditt visuella Power BI-objekt måste finnas på vår [marknadsplats](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
* Visuella Power BI-objekt måste skrivas med *API v2.5* eller senare.
* Kodlagringsplatsen måste vara tillgänglig för granskning av Power BI-teamet. Till exempel måste ett läsbart format för källkoden (Java Script eller TypeScript) vara tillgängligt för oss via GitHub.

    >[!NOTE]
    > Du måste inte dela koden offentligt i Github.

* Krav för kodlagring:
  * Måste innehålla följande filer:
    * .gitignore
    * capabilities.json
    * pbiviz.json
    * package.json
    * package-lock.json
    * tsconfig.json
  * Får inte innehålla mappen *node_modules* (lägg till *node_modules* i filen .gitingore*).
  * Kommandot *npm install* får inte returnera fel.
  * Kommandot *npm audit* får inte returnera varningar av hög eller måttlig nivå.
  * Kommandot *pbiviz package* får inte returnera några fel.
  * Måste innehålla [TSlint från Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) utan åsidosatta konfigurationer. Detta kommando får inte returnera fel.
   * Det kompilerade paketet för det visuella Power BI-objektet måste matcha det skickade paketet (md5-hashen för båda filerna ska vara likadana).
* Krav för källkod:
   * Det visuella Power BI-objektet måste ha stöd för [API:et för renderingshändelser](https://microsoft.github.io/PowerBI-visuals/docs/how-to-guide/rendering-events/).
   * Se till att ingen godtycklig/dynamisk kod körs (dålig: eval() är osäker att använda för settimeout(), requestAnimationFrame(), setinterval(någon funktion med användarindata), körning av användarindata).
   * Se till att DOM manipuleras på ett säkert sätt (dåligt: innerHTML, D3.html(<några användarindata>). Använd sanering för användarindata innan de läggs till i DOM.
   * Se till att det inte finns några JavaScript-fel eller undantag i webbläsarkonsolen för indata. Användare kan använda ditt visuella Power BI-objekt med olika mängder oväntade data. Därför får det visuella objektet inte sluta fungera. Du kan använda [den här exempelrapporten](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) som en testdatauppsättning.

* Om några egenskaper i filen *capabilities.json* ändras ser du till att de inte gör att den befintliga användarens rapporter slutar fungera.

* Kontrollera att det visuella Power BI-objektet uppfyller [riktlinjerna för visuella Power BI-objekt](./guidelines-powerbi-visuals.md).
    
* Din kod kan bara använda offentliga, granskade OSS-komponenter som offentliga Javascript- eller TypeScript-bibliotek. Källkoden måste vara tillgänglig för granskning och får inte ha kända säkerhetsrisker. Vi kan inte verifiera ett anpassat visuellt objekt med hjälp av en extern komponent.

* Det visuella Power BI-objektet får inte ha tillgång till externa tjänster eller resurser. Till exempel får inga HTTP/S- eller WebSocket-begäranden gå ut från Power BI till några tjänster. 

## <a name="submitting-a-power-bi-visual-for-certification"></a>Skicka ett visuellt Power BI-objekt för certifiering

Du kan begära att ditt visuella Power BI-objekt certifieras av Power BI-teamet via Partner Center.

>[!TIP]
>Certifieringsprocessen för Power BI kan ta tid. Om du skapar ett nytt visuellt Power BI-objekt rekommenderar vi att du publicerar visuella Power BI-objekt via Partner Center innan du begär Power BI-certifiering. Detta säkerställer att publiceringen av ditt visuella objekt inte försenas.

Så här begär du Power BI-certifiering:

1. Logga in på Partner Center.
2. På sidan **Översikt** väljer du ditt visuella Power BI-objekt och går till **Produktkonfigurationssidan**.
3. Markera kryssrutan **Begär Power BI-certifiering**.
4. På sidan **Granska och publicera** anger du en länk till källkoden och de autentiseringsuppgifter som krävs för att komma åt den i textrutan **Kommentarer för certifiering**.

>[!NOTE]
> Om du är mitt i en inlämningsprocess för ett visuellt Power BI-objekt och måste använda [Seller Dashboard](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (det gamla hanteringsverktyget) hittar du information i anvisningarna [Sändnings process för Seller Dashboard](seller-dashboard.md#seller-dashboard-certification-submission-process).

## <a name="list-of-power-bi-visuals-that-have-been-certified"></a>Lista över certifierade visuella Power BI-objekt

| Länk | Video |
| --- | --- |
| [3AG Systems – liggande stapeldiagram med relativ avvikelse](https://appsource.microsoft.com/en/product/power-bi-visuals/WA104381912) | |
| [3AG Systems – kolumndiagram med relativ avvikelse](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803) | |
| [Avancerat ringdiagram, visuellt objekt](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941) | |
| [Avancerat nätverk, visualisering](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942) | |
| [Avancerad TimeSeries, visuellt objekt](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943) | |
| [Avancerad kombination, visuellt objekt](https://appsource.microsoft.com/product/power-bi-visuals/WA104381944) | |
| [Aster-punktdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759) | |
| [Beyondsoft-kalender](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096) | |
| [Bowtie-diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838) | [Video](https://youtu.be/So5xKMSpVJI) |
| [Box and Whisker-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831) | |
| [Box- och Whisker-diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351) | [Video](https://youtu.be/JoHaFLfhXdo) |
| [Tegelstensdiagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836) | [Video](https://youtu.be/hA3DOsvn2xY) |
| [Bubbeldiagram från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340) | |
| [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755) | [Video](https://youtu.be/AOlsFYkfkcw) |
| [Bullet Chart från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953) | [Video](https://youtu.be/mtvUNl9bMjA) |
| [Kalendar från Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146) | |
| [Stearinljusstapel av OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952) | [Video](https://youtu.be/nT_18gyRxPo) |
| [Kortet med tillstånd av OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967) | |
| [Chiclet-utsnitt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756) | |
| [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761) | [Video](https://youtu.be/AQvd2FhRyCI) |
| [Cirkelmätare från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837) | [Video](https://youtu.be/9NHXALkBXuY) |
| [Klusterkarta](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806) | |
| [Cirkelmätare från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874) | [Video](https://youtu.be/DgdoWi7Gcxo) |
| [Radiell mätare](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184) | |
| [Punktritning](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760) | |
| [Punktdiagram från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949) | [Video](https://youtu.be/By16pX9KT40) |
| [Detaljgranska Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045) | |
| [Detaljgranska Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044) | |
| [Stapeldiagram med ökad detaljnivå](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857) | [Video](https://youtu.be/lBy2gQQ5YsQ) |
| [Kolumndiagram med ökad detaljnivå för tidsbaserade data](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881) | [Video](https://youtu.be/T_mRou18vx0) |
| [Ringdiagram med ökad detaljnivå](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858) | [Video](https://youtu.be/AUVFrSHmPeo) |
| [Dubbel KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774) | |
| [Dynamisk knappbeskrivning från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983) | [Video](https://youtu.be/Z-tl97BpEr0) |
| [Förbättrat punktdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762) | [Video](https://youtu.be/xCfM0cjM4do) |
| [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112) | |
| [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960) | |
| [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849) | |
| [Enlighten-våffeldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850) | |
| [Filtrera efter lista enligt Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413) | [Video](https://youtu.be/RetEWGwBu0I) |
| [Force-Directed-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764) | [Video](https://youtu.be/YsTa7uyJ4sg) |
| [Tratt med källa från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334) | [Video](https://youtu.be/R_EcimsLI8U) |
| [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765) | [Video](https://youtu.be/qJ7s_KrGiUU) |
| [Gantt-diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364) | [Video](https://youtu.be/vJLV9JRCpI8) |
| [Globdatastaplar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344) | |
| [Rutnät av MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825) | [Video](https://youtu.be/VOPoDJgZfOY) |
| [Hierarkidiagram från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333) | [Video](https://youtu.be/0ZGzJaq_KT4) |
| [Histogramdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776) | |
| [Histogram med punkter från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032) | [Video](https://youtu.be/-ILF--wExrw) |
| [Vågrät tratt från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846) | [Video](https://youtu.be/SudZei68PPo) |
| [Bild från CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297) | |
| [Bildrutnät](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355) | |
| [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898) | |
| [KPI-diagram från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432) | |
| [KPI-kolumn från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996) | [Video](https://youtu.be/rU0xoOlIq1U) |
| [KPI-rutnät från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947) | [Video](https://youtu.be/dM4PvZh71V0) |
| [KPI-indikator](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832) | |
| [KPI Ticker från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946) | [Video](https://youtu.be/cudG4gsZ2V8) |
| [Linjär mätare från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821) | [Video](https://youtu.be/7_jFaM30dkc) |
| [LineDot-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766) | |
| [Mekko-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785) | [Video](https://youtu.be/90FLCKpgicA) |
| [Multi-KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763) | |
| [Översikt av CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477) | |
| [Uppspelningsaxel (dynamiskt utsnitt)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981) | |
| [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083) | [Video](https://youtu.be/IvfIP3E6-1Q) |
| [Power KPI-matris](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299) | [Video](https://youtu.be/1enze8pcGzY) |
| [Pulsdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006) | [Video](https://youtu.be/DQWdcQtjDVw) |
| [Kvadrantdiagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011) | [Video](https://youtu.be/ppBnyhqWNC0) |
| [Polärdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771) | |
| [Ringdiagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824) | [Video](https://youtu.be/pDToHDFHnq8) |
| [Roterande diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007) | [Video](https://youtu.be/d5xBCMmb3hU) |
| [Sankey-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777) | [Video](https://youtu.be/WWP9wVUHGaA) |
| [Punktdiagram från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703) | |
| [Rullningsdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018) | |
| [Smart Filter från SQLBI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859) | [Video](https://youtu.be/gcJsDDRQq28) |
| [Miniatyrdiagram från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910) | [Video](https://youtu.be/0m3Vnvso9tY) |
| [Stream-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772) | |
| [Solstråle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767) | |
| [Synoptisk panel från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873) | |
| [Termisk tabellkarta](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818) | |
| [Tachometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937) | [Video](https://youtu.be/C3OXdETbS9o) |
| [Textfilter](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309) | |
| [Text Wrapper från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826) | |
| [Thermometer från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847) | [Video](https://youtu.be/SPX9mgrAdBc) |
| [Tidsborstningsutsnitt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798) | |
| [Tidslinjeutsnitt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786) | [Video](https://youtu.be/ozMtZ4_NZ10) |
| [Tidslinje från CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427) | [Video](https://youtu.be/szNi9YgXFJc) |
| [Storm-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768) | [Video](https://www.youtube.com/watch?v=AQvd2FhRyCI) |
| [Handelsdiagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823) | [Video](https://youtu.be/xhTR6y6J9Ko) |
| [Ultimate-avvikelse](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140) | [Video](https://youtu.be/pDYF8iZxERs) |
| [Ultimate Waterfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956) | [Video](https://youtu.be/0BZsVCQdEkc) |
| [Lista över användare från CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426) | |
| [Våffeldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049) | [Video](https://youtu.be/1vRqYUsm3Vk) |
| [Ordmoln](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752) | [Video](https://youtu.be/AblTenl9fqo) |

## <a name="faq"></a>Vanliga frågor och svar

Mer information om visuella objekt finns i [Vanliga frågor och svar om certifierade visuella objekt](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Nästa steg

* [Utveckla ett anpassat visuellt objekt i Power BI](../developer/custom-visual-develop-tutorial.md)
* [Microsofts spelningslista om anpassade visuella objekt på YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualiseringar i Power BI](../visuals/power-bi-report-visualizations.md)  
* [Anpassade visualiseringar i Power BI](power-bi-custom-visuals.md)  
* [Publicera visuella Power BI-objekt i Microsoft AppSource](../developer/office-store.md)  

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
