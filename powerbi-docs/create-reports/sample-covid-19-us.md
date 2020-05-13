---
title: COVID – 19 spårningsexempel för myndigheter i USA på lokal och delstatsnivå
description: Hämta och ändra exempelrapporten med data från USA på lokal och delstatsnivå om pandemin COVID-19.
author: LukaszPawlowski-MS
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/28/2020
ms.author: lukaszp
LocalizationGroup: Samples
ms.openlocfilehash: aca7fc70bc70de553eee070ce5e1522b96c94880
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83277903"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>COVID–19-spårningsexempel för myndigheter i USA på lokal och delstatsnivå

Power BI-teamet har skapat ett spårningsexempel för COVID-19 som gör det möjligt myndigheter i USA på lokal och delstatsnivå att publicera eller anpassa en interaktiv rapport om COVID-19. Med hjälp av Power BI Desktop kan de analysera och visualisera COVID-19-data för att hålla sina grupper informerade på ort-, region-, delstats- och nationsnivå. Sedan kan de dela rapporten för att informera medborgarna med Power BI Publicera på webben. Artikeln innehåller olika alternativ för att använda interaktiva visuella Power BI-objekt i din egen offentliga berättelse, blogg eller webbplats.

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="COVID-19-exempel med data från USA":::

Den här artikeln beskriver hur du:

- Kopierar inbäddningskod och lägger till den på din egen webbplats. 
- Gör anpassningar, till exempel formatering av en specifik delstat.
- Publicerar på Power BI-tjänsten.
- Publicerar på webben. 
- Kombinerar data med data från en annan källa. 

## <a name="prerequisites"></a>Förutsättningar

Innan du kan komma igång med Power BI för att dela din berättelse behöver du följande förutsättningar:

- Ladda ned den kostnadsfria versionen av appen [Power BI Desktop](https://powerbi.microsoft.com/desktop/).
- Registrera dig för [Power BI-tjänsten](https://powerbi.microsoft.com/get-started/).

## <a name="option-1-pre-built-embed-code"></a>Alternativ 1: Fördefinierad inbäddningskod

Microsoft har publicerat exempelrapporten och skapat en inbäddningskod för publicering till webben. Du kan använda inbäddningskoden för att bädda in hela exemplet, inklusive den nationella vyn, och öka detaljnivån till delstat och region på din egen webbplats. Innan du publicerar dessa data rekommenderar vi att du går igenom [ansvarsfriskrivningarna](#disclaimers) i den här artikeln.

Om du vill inkludera den interaktiva grafiken på din webbplats kopierar du och klistrar in följande inbäddningskod till den plats där du vill att bilden ska visas på din webbplats.  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

Inbäddningskoden är ett iFrame-element i HTML som du kan infoga på en HTML-sida. Justera bredden och höjden på den iFrame som är avsedd att passa på din webbplats. Exampelrapporten har skrivits med förhållandena 16:9. Välj en storlek som bevarar förhållandet. När det implementeras korrekt visas bilden utan extra grå kantlinjer. Det är användbart att [läsa tips och råd för iFrame-storlek](../collaborate-share/service-publish-to-web.md#tips-for-iframe-height-and-width) när du genomför dessa ändringar.

## <a name="option-2-customize-the-sample-power-bi-file"></a>Alternativ 2: Anpassa Power BI-exempelfilen

Power BI-filen innehåller data och interaktiva bilder i filformatet .pbix som du kan redigera i Power BI Desktop.  

En typisk anpassning är att filtrera rapporten enligt en specifik delstat och sedan skapa en egen inbäddningskod för publicering till webbplats för din anpassade rapport.

USAFacts-data tillhandahålls under en Creative Commons-licens som måste noteras. Innan du publicerar dessa data bör du läsa [ansvarsfriskrivningstexten](#disclaimers).

Kom igång genom att [Ladda ned .pbix-filen (här)](https://go.microsoft.com/fwlink/?linkid=2125058).

### <a name="update-your-report"></a>Uppdatera din rapport 

1. Hämta den senaste versionen av den kostnadsfria appen [Power BI Desktop](https://powerbi.microsoft.com/desktop/) om du inte redan gjort det. 

2. Ladda ned [.pbix-filen](https://go.microsoft.com/fwlink/?linkid=2125058) om du inte redan har gjort det och öppna den i Power BI Desktop.

3. Om du vill filtrera rapporten enligt en specifik delstat väljer du pilen för att utöka filterfönstret.

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="Utöka filterfönstret":::

4. Välj en delstat som du är intresserad av. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="Välj en delstat":::

5. Välj **Arkiv** > **Spara** för att spara filen. 

### <a name="refresh-your-report"></a>Uppdatera rapporten 

1. Klicka på **uppdateringsknappen**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="Knappen Uppdatera":::

2. Välj **Anonym** > **Ansluta**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="Välj Anonym":::

 
3. Välj **Ignorera sekretessnivåer**, om det visas > **Spara**. 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="Ange sekretessnivåer":::

### <a name="publish-your-report-to-the-power-bi-service"></a>Publicera din rapport till Power BI-tjänsten

När du har anpassat rapporten enligt dina önskemål kan du [följa stegen som beskrivs här för att publicera rapporten](../create-reports/desktop-upload-desktop-files.md) på Power BI-tjänsten.

### <a name="configure-scheduled-refresh"></a>Konfigurera schemalagd uppdatering

För att informationen i rapporten ska vara aktuell kan du [Konfigurera schemalagd uppdatering](../connect-data/refresh-scheduled-refresh.md) när du har publicerat rapporten.

När du följer stegen kan du välja följande alternativ:

1. Autentiseringmetod för autentiseringsuppgifter för datakälla: Anonym
2. Inställningar för sekretessnivå för den här datakällan: Offentlig

Om du vill testa uppdateringsinställningen väljer du alternativet [Uppdatera nu](../connect-data/refresh-data.md#data-refresh) som är tillgängligt från datauppsättningsobjektet.

Uppdaterade data läses in varje gången schemat körs. Underliggande data tillhandahålls av USAFacts och kanske inte uppdateras lika ofta som ditt uppdateringsschema. Kontrollera [USAFacts webbplats](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) för att veta när de underliggande data senast uppdaterades. 

Om du tänker publicera den anpassade rapporten på din webbplats är det bäst att konfigurera den schemalagda uppdateringen så att den körs minst lika ofta som USAFacts-datauppdateringarna. Eftersom USAFacts kan uppdatera sina data vid olika tidpunkter kan det vara bra att konfigurera flera uppdateringar varje dag. 

### <a name="create-a-publish-to-web-embed-code"></a>Skapa en inbäddningskod för publicering till webben 

Om du vill bädda in din anpassade rapport på din egen webbplats följer du anvisningarna för hur du [skapar en egen inbäddningskod för publicering till webbplats](../collaborate-share/service-publish-to-web.md#create-embed-codes-with-publish-to-web).

När du har publicerat din inbäddningskod använder du iFrame i bekräftelsedialogrutan för att bädda in den på webbplatsen.

Om du gör ändringar i rapporten i Power BI Desktop kan du publicera och ersätta den befintliga rapporten i Power BI-tjänsten. Inbäddningskoden ändras inte. Det tar ungefär en timme för ändringar i rapporten eller uppdaterade data att visas på din webbplats. 

## <a name="option-3-mash-up-data-from-another-source"></a>Alternativ 3: Kombinera data från en annan källa 

Du kan också kombinera data i den här rapporten med data från en annan källa. Följande exempel baseras på data från [Johns Hopkins University](https://github.com/CSSEGISandData/COVID-19). Innan du publicerar dessa data rekommenderar vi att du går igenom [ansvarsfriskrivningarna](#disclaimers) i den här artikeln.

1. Välja **Hämta data** > **Webb**.

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="Knappen Hämta data":::

2. Ange följande URL:

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="Välj data från webben":::

3. Välj **OK**. 

    > [!NOTE]
    > Länken som publiceras av Johns Hopkins University kan ändras. Den senaste informationen finns på sidan [Johns Hopkins GitHub](https://github.com/CSSEGISandData/COVID-19).

4. Välj **Läs in** för att läsa in datauppsättningen för totalt antal bekräftade fall över hela världen.  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="Läs in data från webben":::

    Den här artikeln [Ansluta till webbsidor från Power BI Desktop](../connect-data/desktop-connect-to-web.md) innehåller mer information om att läsa in data från webben.
    
Du kan sedan använda Power BI Desktop för att visualisera data. Använd slutligen stegen i **Alternativ 2:** [Publicera rapporten till Power BI-tjänsten](#publish-your-report-to-the-power-bi-service) för att publicera rapporten och skapa en anpassad inbäddningskod. 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>Alternativ 4: Använda mallappen för uppföljningsrapport för COVID-19 för USA

För att tillhandahålla ytterligare ett alternativ har Power BI-teamet skapat en *mallapp* för uppföljning av COVID-19 för USA så att du kan komma igång direkt. Mallappar är paket med rapporter, instrumentpaneler och datauppsättningar för en specifik datakälla. Du laddar ned dem från AppSource, använder dem som de är eller anpassar dem efter dina behov, och distribuerar dem till dina medarbetare. 

Mallappen för uppföljning av COVID-19 för USA innehåller en fördefinierad rapport med COVID-19-mått som du kan använda som de är, anpassa direkt i Power BI-tjänsten eller ladda ned för att lägga till andra datakällor. Läs om hur du installerar [mallappen för uppföljning av COVID-19 för USA](../connect-data/service-connect-to-covid-19-tracking.md) och kommer igång direkt.

## <a name="about-the-data-source-for-this-report"></a>Om datakällan för den här rapporten
Den här interaktiva rapporten sammanställer data från Centeres for Disease Control and Prevention (centrum för sjukdomsbekämpning och skydd, CDC) och offentliga hälsomyndigheter på delstats- och lokal nivå. Data på regionsnivå bekräftas genom att hänvisa till myndigheter på delstats- och lokal nivå direkt (länk).

Data tillhandahålls av USAFacts. På grund av hur ofta dessa data uppdateras återspeglar de kanske inte de exakta siffror som rapporteras av myndigheter eller nyhetsmedier. Mer information finns på [USAFacts webbplats](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) där data också kan hämtas. 

## <a name="disclaimers"></a>Ansvarsfriskrivningar

Den här rapporten och data tillhandahålls "i befintligt skick", "med alla fel" och utan garanti av något slag. Microsoft lämnar inga uttryckliga garantier och frånsäger sig uttryckligen alla underförstådda garantier, inklusive säljbarhet, lämplighet för ett särskilt ändamål och ansvarsfrihet mot inskränkning av immaterielrätt.

USAFacts-data finns tillgängliga under en Creative Commons-licens. Om du vill använda den måste du citera USAFacts som dataleverantör och länka tillbaka till USAFacts. För exakta noteringssteg, se avsnittet **#MadewithUSAFacts** på sidan USAFacts [Coronavirus in the United States: Mapping the COVID-19 outbreak in the states and counties](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/).

Johns Hopkins Universitys data är upphovsrättsskyddad från 2020 av Johns Hopkins University, med ensamrätt. Det tillhandahålls offentligt för utbildning och akademisk forskning. Här är de fullständiga [användningsvillkoren](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) av de data som visas i kombinationsexemplet. Mer information finns på webbplatsen för [Johns Hopkins University](https://coronavirus.jhu.edu/map-faq.html).

## <a name="next-steps"></a>Nästa steg

[Hämta exempel för Power BI](../create-reports/sample-datasets.md)




