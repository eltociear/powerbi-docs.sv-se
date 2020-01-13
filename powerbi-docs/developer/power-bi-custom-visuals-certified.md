---
title: Certifierade visuella Power BI-objekt
description: Krav och processer för att skicka en visualisering för certifiering. Och en lista över certifierade visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/02/2019
ms.openlocfilehash: c39b96122016746905ea09c0983adf50356f0c77
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2020
ms.locfileid: "75221975"
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
> Microsoft kan ta bort visuella Power BI-objekt från listan över [certifierade visuella Power BI-objekt](#certified-power-bi-visuals) efter eget gottfinnande.

## <a name="certification-requirements"></a>Certifieringskrav

Se till att visuella Power BI-objekt uppfyller de krav som anges i det här avsnittet för att [certifiera](#get-a-power-bi-visual-certified) ditt visuella Power BI-objekt. 

> [!TIP]
> Vi rekommenderar att du använder EsLint med standardsäkerhetsregler för att kontrollera koden innan den skickas.

* Godkänd för Microsoft Seller Dashboard eller Partner Center. Ditt visuella Power BI-objekt måste finnas på vår [Marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals).
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
   * Det kompilerade paketet för det visuella Power BI-objektet måste matcha det skickade paketet.
* Krav för källkod:
   * Det visuella Power BI-objektet måste ha stöd för [API:et för renderingshändelser](./visuals/event-service.md).
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
>Certifieringsprocessen för Power BI kan ta tid. Om du skapar ett nytt visuellt Power BI-objekt rekommenderar vi att du publicerar ditt visuella Power BI-objekt via Partnercenter innan du begär Power BI-certifiering. Detta säkerställer att publiceringen av ditt visuella objekt inte försenas.

Så här begär du Power BI-certifiering:

1. Logga in på Partner Center.
2. På sidan **Översikt** väljer du ditt visuella Power BI-objekt och går till **Produktkonfigurationssidan**.
3. Markera kryssrutan **Begär Power BI-certifiering**.
4. På sidan **Granska och publicera** anger du en länk till källkoden och de autentiseringsuppgifter som krävs för att komma åt den i textrutan **Kommentarer för certifiering**.

>[!NOTE]
> Om du är mitt i en inlämningsprocess för ett visuellt Power BI-objekt och måste använda [Seller Dashboard](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) (det gamla hanteringsverktyget) hittar du information i anvisningarna [Sändnings process för Seller Dashboard](seller-dashboard.md#seller-dashboard-certification-submission-process).

## <a name="certified-power-bi-visuals"></a>Certifierade visuella Power BI-objekt

De certifierade visuella Power BI-objekten anges nedan. Klicka på länken för att öppna det visuella Power BI-objektet i AppSource. Om en video är tillgänglig kan du klicka på videolänken för att titta på den.

* [3AG Systems – liggande stapeldiagram med absolut avvikelse](https://appsource.microsoft.com/product/power-bi-visuals/WA104381802)
*  [3AG Systems – liggande stapeldiagram med relativ avvikelse](https://appsource.microsoft.com/product/power-bi-visuals/WA104381912)
*  [3AG Systems – kolumndiagram med relativ avvikelse](https://appsource.microsoft.com/product/power-bi-visuals/WA104381803)
*  [3AG Systems – kolumndiagram med varians](https://appsource.microsoft.com/product/power-bi-visuals/WA104381724)
* [Visuellt objekt för avancerat ringdiagram (fullständig utgåva)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381941)
*  [Visuellt objekt för avancerat ringdiagram (lätt utgåva)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858)
*  [Visuellt objekt för avancerad graf](https://appsource.microsoft.com/product/power-bi-visuals/WA104382086)
*  [Avancerat nätverk, visualisering](https://appsource.microsoft.com/product/power-bi-visuals/WA104381942)
*  [Visuellt objekt för avancerad tidsserie (fullständig utgåva)](https://appsource.microsoft.com/product/power-bi-visuals/WA104381943)
*  [Aster-punktdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380759)
*  [Beyondsoft-kalender](https://appsource.microsoft.com/product/power-bi-visuals/WA104381096)
*  [Bowtie-diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380838)
*  [Box and Whisker-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380831)
* [Box- och Whisker-diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381351)
*  [Tegelstensdiagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380836)
*  [Bubbeldiagram från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381340)
*  [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755),  **[videolänk](https://youtu.be/AOlsFYkfkcw)**
* [Bullet Chart](https://appsource.microsoft.com/product/power-bi-visuals/WA104380755)
*  [Bullet Chart by OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380953), **[videolänk](https://youtu.be/mtvUNl9bMjA)**
* [Kalender från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381844)
*  [Kalendar från Tallan](https://appsource.microsoft.com/product/power-bi-visuals/WA104381146)
*  [Stearinljusstapel från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380952), **[videolänk](https://youtu.be/nT_18gyRxPo)**
*  [Kortet med tillstånd av OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380967)
*  [Chiclet-utsnitt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380756)
*  [Chord](https://appsource.microsoft.com/product/power-bi-visuals/WA104380761), **[videolänk](https://youtu.be/AQvd2FhRyCI)**
*  [Cirkelmätare från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380837)
*  [Klusterkarta](https://appsource.microsoft.com/product/power-bi-visuals/WA104380806)
* [Anpassad kalender från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381179)
* [Cirkelmätare från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380874)
*  [Radiell mätare](https://appsource.microsoft.com/product/power-bi-visuals/WA104381184)
[Punktritningsdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380760)
*  [Punktritningsdiagram från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380949), **[videolänk](https://youtu.be/By16pX9KT40)**
*  [Detaljgranska Cartogram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381045)
*  [Detaljgranska Choropleth](https://appsource.microsoft.com/product/power-bi-visuals/WA104381044)
*  [Kolumndiagram med ökad detaljnivå](https://appsource.microsoft.com/product/power-bi-visuals/WA104380857), **[videolänk](https://youtu.be/lBy2gQQ5YsQ)**
*  [Kolumndiagram med ökad detaljnivå för tidsbaserade data](https://appsource.microsoft.com/product/power-bi-visuals/WA104380881), **[videolänk](https://youtu.be/T_mRou18vx0)**
*  [Ringdiagram med ökad detaljnivå](https://appsource.microsoft.com/product/power-bi-visuals/WA104380858), **[videolänk](https://youtu.be/AUVFrSHmPeo)**
*  [Dubbel KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104380774)
*  [Dynamisk knappbeskrivning från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380983)
*  [Förbättrat punktdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380762), **[videolänk](https://youtu.be/xCfM0cjM4do)**
*  [Enlighten Aquarium](https://appsource.microsoft.com/product/power-bi-visuals/WA104381112)
*  [Enlighten Slicer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380960)
*  [Enlighten Stack Shuffle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380849)
*  [Enlighten-våffeldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380850)
*  [Filtrera efter lista från Devscope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381413), **[videolänk](https://youtu.be/RetEWGwBu0I)**
*  [Force-Directed-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380764), **[videolänk](https://youtu.be/YsTa7uyJ4sg)**
*  [Tratt med källa från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381334)
*  [Gantt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380765), **[videolänk](https://youtu.be/qJ7s_KrGiUU)**
* [Gantt-diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381364)
*  [Globdatastaplar](https://appsource.microsoft.com/product/power-bi-visuals/WA104381344)
*  [Rutnät av MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380825)
*  [Hierarkidiagram från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381333), **[videolänk](https://youtu.be/0ZGzJaq_KT4)**
*  [Histogramdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380776)
*  [Histogram med punkter från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381032)
* [Vågrätt stapeldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381230)
*  [Vågrät tratt från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380846)
*  [Bild från CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381297)
*  [Bildrutnät](https://appsource.microsoft.com/product/power-bi-visuals/WA104381355)
*  [Infographic Designer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380898)
*  [KPI-diagram från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381432)
*  [KPI-kolumn från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380996)
*  [KPI-rutnät från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380947)
*  [KPI-indikator](https://appsource.microsoft.com/product/power-bi-visuals/WA104380832)
*  [KPI Ticker från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380946)
* [Linjär mätare från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380821)
*  [LineDot-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380766)
*  [Mekko-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380785), **[videolänk](https://youtu.be/90FLCKpgicA)**
*  [Multi-KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381763)
*  [Översikt av CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381477)
*  [Uppspelningsaxel (dynamiskt utsnitt)](https://appsource.microsoft.com/product/power-bi-visuals/WA104380981)
*  [Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083), [videolänk](https://youtu.be/IvfIP3E6-1Q)
*  [Power KPI-matris](https://appsource.microsoft.com/product/power-bi-visuals/WA104381299), **[videolänk](https://youtu.be/1enze8pcGzY)**
*  [Pulsdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381006), **[videolänk](https://youtu.be/DQWdcQtjDVw)**
*  [Kvadrantdiagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381011)
*  [Polärdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380771)
*  [Ringdiagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380824)
*  [Roterande diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381007)
*  [Sankey-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380777), **[videolänk](https://youtu.be/WWP9wVUHGaA)**
*  [Punktdiagram från Akvelon](https://appsource.microsoft.com/product/power-bi-visuals/WA104381703)
*  [Rullningsdiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381018)
*  [Smart Filter från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380859), **[videolänk](https://youtu.be/gcJsDDRQq28)**
*  [Miniatyrdiagram från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380910), **[videolänk](https://youtu.be/0m3Vnvso9tY)**
*  [Stream-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380772)
*  [Solstråle](https://appsource.microsoft.com/product/power-bi-visuals/WA104380767)
*  [Synoptisk panel från OKViz](https://appsource.microsoft.com/product/power-bi-visuals/WA104380873)
*  [Termisk tabellkarta](https://appsource.microsoft.com/product/power-bi-visuals/WA104380818)
*  [Takometer](https://appsource.microsoft.com/product/power-bi-visuals/WA104380937), **[videolänk](https://youtu.be/C3OXdETbS9o)**
*  [Textfilter](https://appsource.microsoft.com/product/power-bi-visuals/WA104381309)
*  [Text Wrapper från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380826)
*  [Thermometer från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380847)
*  [Tidsborstningsutsnitt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380798)
*  [Tidslinjeutsnitt](https://appsource.microsoft.com/product/power-bi-visuals/WA104380786), **[videolänk](https://youtu.be/ozMtZ4_NZ10)**
*  [Tidslinje från CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381427), [videolänk](https://youtu.be/szNi9YgXFJc)
*  [Tornado-diagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104380768), **[videolänk](https://www.youtube.com/watch?v=AQvd2FhRyCI)**
*  [Handelsdiagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104380823)
* [Ultimate KPI-kort](https://appsource.microsoft.com/product/power-bi-visuals/WA104381977)
*  [Ultimate-varians](https://appsource.microsoft.com/product/power-bi-visuals/WA104381140), **[videolänk](https://youtu.be/pDYF8iZxERs)**
*  [Ultimate-vattenfall](https://appsource.microsoft.com/product/power-bi-visuals/WA104380956), **[videolänk](https://youtu.be/0BZsVCQdEkc)**
*  [Lista över användare från CloudScope](https://appsource.microsoft.com/product/power-bi-visuals/WA104381426)
*  [Venn-diagram från MAQ Software](https://appsource.microsoft.com/product/power-bi-visuals/WA104381231)
*  [Fioldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381947)
*  [Visuellt Visio-objekt](https://appsource.microsoft.com/product/power-bi-visuals/WA104381132)
*  [Våffeldiagram](https://appsource.microsoft.com/product/power-bi-visuals/WA104381049), **[videolänk](https://youtu.be/1vRqYUsm3Vk)**
*  [Ordmoln](https://appsource.microsoft.com/product/power-bi-visuals/WA104380752), **[videolänk](https://youtu.be/AblTenl9fqo)**

## <a name="faq"></a>Vanliga frågor och svar

Mer information om visuella objekt finns i [Vanliga frågor och svar om certifierade visuella objekt](power-bi-custom-visuals-faq.md#certified-power-bi-visuals).

## <a name="next-steps"></a>Nästa steg

* [Utveckla ett anpassat visuellt objekt i Power BI](../developer/custom-visual-develop-tutorial.md)
* [Microsofts spelningslista om anpassade visuella objekt på YouTube](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)  
* [Visualiseringar i Power BI](../visuals/power-bi-report-visualizations.md)  
* [Anpassade visualiseringar i Power BI](power-bi-custom-visuals.md)  
* [Publicera visuella Power BI-objekt i Microsoft AppSource](../developer/office-store.md)  

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
