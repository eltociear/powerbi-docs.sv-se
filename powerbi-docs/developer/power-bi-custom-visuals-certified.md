---
title: Certifierade visuella Power BI-objekt
description: Krav och processer för att skicka ett anpassat visuellt objekt för certifiering och en lista över certifierade visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 03/01/2020
ms.openlocfilehash: 8aea9041665de69b2c5be954dc8f13a6402a06e0
ms.sourcegitcommit: d55d3089fcb3e78930326975957c9940becf2e76
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260771"
---
# <a name="get-a-power-bi-visual-certified"></a>Certifiera ett visuellt Power BI-objekt

Certifierade visuella Power BI-objekt är visuella objekt i [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) som uppfyller Microsoft Power BI-teamets [kodkrav](#certification-requirements). Dessa visuella objekt testas för att kontrollera att de inte har åtkomst till externa tjänster eller resurser och att de följer säkra kodningsmönster och riktlinjer.

När ett visuellt Power BI-objekt har certifierats erbjuder det fler funktioner. Du kan [exportera det till PowerPoint](../consumer/end-user-powerpoint.md) och du kan visa det visuella objektet i e-postmeddelanden när en användare [prenumererar på rapportsidor](../consumer/end-user-subscribe.md).

Certifieringsprocessen är valfri. Visuella Power BI-objekt som inte är certifierade är inte nödvändigtvis osäkra visuella objekt i Power BI. Vissa visuella Power BI-objekt är inte certifierade eftersom de inte är kompatibla med ett eller flera av [certifieringskraven](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Till exempel en visuell karta i Power BI som ansluter till en extern tjänst eller ett visuellt Power BI-objekt som använder kommersiella bibliotek.

> [!NOTE]
> Microsoft har inte skapat de visuella Power BI-objekten från tredje part. Kontakta upphovsmannen direkt för att verifiera funktionaliteten för visuella objekt från tredje part.

## <a name="certification-requirements"></a>Certifieringskrav

För att få dina visuella Power BI-objekt [certifierade](#get-a-power-bi-visual-certified) måste ditt visuella Power BI-objekt uppfylla de krav som anges i det här avsnittet. 

### <a name="general-requirements"></a>Allmänna krav

Ditt visuella Power BI-objekt måste godkännas av instrumentpanelen för försäljnings eller Partnercenter. Vi rekommenderar att ditt visuella Power BI-objekt redan finns i [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals). Mer information om att publicera visuella Power BI-objekt till AppSource finns i [Publicera visuella Power BI-objekt på Partnercenter](office-store.md).

Innan du skickar in ditt visuella Power BI-objekt för certifiering ska du kontrollera att det uppfyller [riktlinjerna för visuella Power BI-objekt](./guidelines-powerbi-visuals.md).

När du skickar det visuella Power BI-objektet ska du se till att det kompilerade paketet exakt matchar det skickade paketet.

### <a name="code-repository-requirements"></a>Krav för kodlagring

Även om du inte behöver dela koden offentligt i GitHub måste kodlagringsplatsen vara tillgänglig för granskning av Power BI-teamet. Det bästa sättet att göra det på är genom att tillhandahålla källkoden (Java Script eller TypeScript) i GitHub.

Lagringsplatsen måste innehålla följande:
* Kod för endast ett visuellt Power BI-objekt. Den får inte innehålla kod för flera visuella Power BI-objekt eller orelaterad kod.
* En gren med namnet **certification** (skrivet med gemener). Källkoden i den här grenen måste matcha det skickade paketet. Den här koden kan bara uppdateras under nästa sändningsprocess om du skickar in det visuella Power BI-objektet igen.

Om ditt visuella Power BI-objekt använder privata NPM-paket eller Git-delmoduler måste du ge åtkomst till de övriga lagringsplatserna som innehåller den här koden.

Om du vill förstå hur en visuell Power BI-lagringsplats ser ut, så ta en titt på GitHub-lagringsplatsen för [exempelstapeldiagrammet för visuella Power BI-objekt](https://github.com/microsoft/PowerBI-visuals-sampleBarChartgi).

### <a name="file-requirements"></a>Filkrav

Använd den senaste versionen av API:t för att skriva visuella Power BI-objekt.

Lagringsplatsen måste innehålla följande filer:
* **.gitignore** – Lägg till `node_modules`, `.tmp`, `dist` till den här filen. Koden får inte innehålla mappen *node_modules*, *.tmp* eller *dist*.
* **capability. JSON-** – Om du skickar nyare versioner av visuella Power BI-objekt med ändringar i egenskaperna i den här filen ska du kontrollera att de inte bryter rapporter för befintliga användare.
* **pbiviz.json** 
* **package.json**. Det visuella objektet måste ha följande paket installerat:
   * [”tslint”](https://www.npmjs.com/package/tslint): ”5.18.0” eller senare
   * [”typescript”](https://www.npmjs.com/package/typescript): ”3.0.0” eller senare
   * [”tslint-microsoftcontrib”](https://www.npmjs.com/package/tslint-microsoft-contrib): ”6.2.0” eller senare
   * Filen måste innehålla kommando för att köra linter: ”lint”: ”tslint -c tslint.json -p tsconfig.json”
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>Kommandokrav

Kontrollera att följande kommandon inte returnerar några fel.

* `npm install`
* `pbiviz package`
* `npm audit` – Får inte returnera varningar av hög eller måttlig nivå.
* [TSlint från Microsoft](https://www.npmjs.com/package/tslint-microsoft-contrib) med [krävd konfiguration](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json). Detta kommando får inte returnera fel.

### <a name="compiling-requirements"></a>Kompileringskrav

Använd den senaste versionen av [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) för att skriva visuella Power BI-objekt.

Du måste kompilera det visuella Power BI-objektet med `pbiviz package`. Om du använder egna build-skript anger du ett `npm run package` anpassat build-kommando.



### <a name="source-code-requirements"></a>Krav för källkod

Kontrollera att du följer principlistan [Ytterligare certifiering för visuella Power BI-objekt](https://docs.microsoft.com/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification). Om ditt bidrag inte följer dessa riktlinjer innehåller e-postmeddelandet med avvisandet från Partnercenter de principnummer som anges i den här länken.

Följ de kodkrav som anges nedan för att kontrollera att koden följer Power BI:s certifieringsprinciper.  

**Krävs**
* Använd bara offentliga, granskade OSS-komponenter som offentliga Javascript- eller TypeScript-bibliotek.
* Koden måste ha stöd för [API:et för renderingshändelser](./visuals/event-service.md).
* Se till att DOM ändras på ett säkert sätt. Sanera användarindata eller användardata innan du lägger till dem i DOM.
* Använd [exempelrapporten](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix) som en testdatamängd.

**Inte tillåten**
* Tillgång till externa tjänster eller resurser. Till exempel får inga HTTP/S- eller WebSocket-begäranden gå ut från Power BI till några tjänster.
* Använda `innerHTML`eller `D3.html(user data or user input)`.
* JavaScript-fel eller undantag i webbläsarkonsolen för indata.
* Godtycklig eller dynamisk kod, till exempel `eval()`, osäker användning av `settimeout()`, `requestAnimationFrame()`, `setinterval(user input function)` och användarindata eller användardata.
* Minimerade JavaScript-filer eller-projekt.

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

### <a name="private-repository-submission-process"></a>Process för överföring av privat lagringsplats

Om du använder en privat lagringsplats, t.ex. GitHub, för att skicka in dina visuella Power BI-objekt för certifiering, så följ anvisningarna i det här avsnittet.
1. Skapa ett nytt konto för valideringsteamet.
2. Konfigurera [tvåfaktorautentisering](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa) för ditt konto.
3. [Generera en ny uppsättning återställningskoder](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes).
4. När du skickar in ditt visuella Power BI-objekt, så ange följande:
    * En länk till lagringsplatsen
    * Inloggningsuppgifter (inklusive lösenord)
    * Återställningskoder
    * Läs behörighet till vårt konto ([pbicvsupport](https://github.com/pbicvsupport))

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
* Om du är webbutvecklare som är intresserad av att skapa egna visuella Power BI-objekt och lägga till dem i  [Microsoft AppSource](https://appsource.microsoft.com) kan du börja du med självstudien  [Utveckla ett visuellt Power BI-objekt](visuals/custom-visual-develop-tutorial.md). 

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
