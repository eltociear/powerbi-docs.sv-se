---
title: 'Exempel på kundlönsamhet för Power BI: Ta en rundtur'
description: 'Exempel på kundlönsamhet för Power BI: Ta en rundtur'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/05/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 160c5736bc2894e629f5bb375dd07e993def1e0c
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "74265554"
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Exempel på kundlönsamhet för Power BI: Ta en rundtur

Innehållspaketet ”Exempel på kundlönsamhet” innehåller en instrumentpanel, en rapport och en datamängd för ett företag som tillverkar marknadsföringsmaterial. Den här instrumentpanelen skapades av en ekonomichef för att visa nyckelmått om de fem enhetscheferna, produkter, kunder och bruttomarginaler. I korthet kan hon se vilka faktorer som påverkar lönsamheten.

![Instrumentpanelen för Exemplet på kundlönsamhet](media/sample-customer-profitability/power-bi-dash.png)

Det här exemplet ingår i en serie som visar hur du kan använda Power BI med verksamhetsorienterade data, rapporter och instrumentpaneler. Det skapades av [obviEnce](http://www.obvience.com/) med verkliga data, som har anonymiserats. Dessa data är tillgängliga i flera format: innehållsförpackning, .pbix-fil för Power BI Desktop eller Excel-arbetsbok. Se [Exempel för Power BI](sample-datasets.md). 

De här självstudierna använder Power BI-tjänsten och innehållspaketet exempel på kundlönsamhet. Eftersom rapportupplevelserna är så lika i Power BI Desktop och tjänsten kan du även följa med via .pbix-exempelfilen i Power BI Desktop. 

Du behöver inte en licens för Power BI för att utforska exempel i Power BI Desktop. Om du inte har en Power BI Pro-licens kan du spara exemplet på Min arbetsyta i Power BI-tjänsten. 

## <a name="get-the-sample"></a>Hämta exemplet

Innan du kan använda exemplet, måste du först hämta det som ett [innehållspaket](#get-the-content-pack-for-this-sample), en [.pbix-fil](#get-the-pbix-file-for-this-sample) eller en [Excel-arbetsbok](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Hämta innehållspaketet för det här exemplet

1. Öppna Power BI-tjänsten (app.powerbi.com), logga in och öppna den arbetsyta där du vill spara exemplet.

   Om du inte har en Power BI Pro-licens kan du spara exemplet på Min arbetsyta.

2. Längst ned i vänster hörn väljer du **Hämta data**.

   ![Välja Hämta data](media/sample-datasets/power-bi-get-data.png)
3. På sidan **Hämta data** väljer du **Exempel**.

4. Välj **Exempel på kundlönsamhet** och sedan **Anslut**.  

    ![Ansluta till exempel](media/sample-customer-profitability/get-supplier-sample.png)
5. Power BI importerar innehållspaketet och lägger sedan till en ny instrumentpanel, rapport och datamängd till din aktuella arbetsyta.

    ![Post för Exempel på kundlönsamhet](media/sample-customer-profitability/customer-profitability-sample-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Hämta .pbix-filen för det här exemplet

Alternativt kan du ladda ned Exempel på kundlönsamhet som en [.pbix-fil](https://download.microsoft.com/download/6/A/9/6A93FD6E-CBA5-40BD-B42E-4DCAE8CDD059/Customer%20Profitability%20Sample%20PBIX.pbix), som används med Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Hämta Excel-arbetsboken för det här exemplet

Om du vill visa i datakällan för det här exemplet är det även tillgängligt som en [Excel-arbetsbok](https://go.microsoft.com/fwlink/?LinkId=529781). Arbetsboken innehåller Power View-blad som du kan visa och ändra. Om du vill se rådata aktiverar du dataanalystilläggen och väljer **Power Pivot > Hantera**. Aktivering av tilläggen för Power View och Power Pivot beskrivs i avsnittet om att [titta på Excel-exemplen inuti själva Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself).

## <a name="what-is-our-dashboard-telling-us"></a>Vad kan vi utläsa från instrumentpanelen?

I den arbetsyta där du sparade exemplet letar du upp instrumentpanelen för kundlönsamhet och väljer den:

![Instrumentpanelen för Exemplet på kundlönsamhet](media/sample-customer-profitability/power-bi-dash.png)

### <a name="company-wide-dashboard-tiles"></a>Instrumentpaneler för hela företaget
1. Öppna instrumentpanelen i Power BI-tjänsten. Dessa paneler på instrumentpanelen ger vår ekonomichef en överblick över de mått för företaget på hög nivå som är viktiga för henne. Säljchefen kan välja en panel för att granska data närmare när något intressant dyker upp.

2. Granska panelerna på vänster sida av instrumentpanelen.

    ![Paneler för ansvariga](media/sample-customer-profitability/power-bi-manager.png)

   Observera följande information:
   - Företagets bruttomarginal är 42,5 %.
   - Det har 80 kunder.
   - Det säljer fem olika produkter.
   - Det hade sin lägsta varians i intäktsprocent i förhållande till budgeten i februari, följt av den högsta i mars.
   - De flesta av våra intäkter kommer från de östra och norra regionerna. Bruttomarginalen har aldrig överskridit budgeten, men affärsenheterna ER-0 och MA-0 kräver närmare granskning.
   - Totala intäkter för året ligger nära budgeten.

### <a name="manager-specific-dashboard-tiles"></a>Chefspecifika instrumentpaneler
Panelerna på höger sida av instrumentpanelen ger ett poängkort för teamet. Det är viktigt för ekonomichefen att kunna följa cheferna, och dessa paneler ger en översikt över vinsten med hjälp av bruttomarginal i %. Om trenden för bruttomarginalen % är oväntad för någon chef kan detta undersökas närmare.

![Bruttomarginal i % för ansvariga](media/sample-customer-profitability/power-bi-manager2.png)

Genom att analysera chefsspecifika instrumentpaneler kan vi göra följande observationer:

- Alla chefer utom Carlos, har redan passerat försäljningsmålet. Carlos faktiska försäljning är dock den högsta.
- Annelies bruttomarginal % är lägst, men det syns en konstant ökning sedan mars.
- Å andra sidan har Valerys bruttomarginal i % sjunkit avsevärt.
- Andrew har haft ett varierande år.

## <a name="explore-the-dashboards-underlying-data"></a>Utforska instrumentpanelens underliggande data
Den här instrumentpanelen innehåller paneler som länkar till en rapport och till en Excel-arbetsbok.

### <a name="open-the-excel-online-data-source"></a>Öppna Excel Online-datakällan
Två paneler på den här instrumentpanelen **Mål kontra faktisk** och **Tillväxt år för år** har fästs från en Excel-arbetsbok. När du väljer någon av dessa paneler öppnar Power BI datakällan, i det här fallet Excel Online.

![Excel online](media/sample-customer-profitability/power-bi-excel-online.png)

1. Välj någon av panelerna som fästs från Excel. Excel Online öppnas i Power BI-tjänsten.
2. Observera att arbetsboken har tre flikar med data. Öppna **Intäkter**.
3. Nu ska vi undersöka varför Carlos inte har nått sitt mål ännu:  

    a. Från skjutreglaget **Executive** väljer du **Carlos Grilo**.   

    b. Första pivottabellen visar att Carlos intäktstillväxt för topprodukten Primus har gått ner 152 % från förra året. Diagrammet **Intäktsavvikelser år för år** visar att Carlos har varit under budgeten för de flesta månader.  

    ![Pivottabell](media/sample-customer-profitability/power-bi-pivotchart.png)

    ![Resultat för Carlos](media/sample-customer-profitability/power-bi-carlos.png)

4. Fortsätta att utforska. Om du hittar något intressant väljer du **Fäst** ![fäst-ikonen](media/sample-customer-profitability/power-bi-excel-pin.png) från det övre högra hörnet för att [fästa det på en instrumentpanel](service-dashboard-pin-tile-from-excel.md).

5. Använd din webbläsares bakåtpil för att gå tillbaka till instrumentpanelen.

### <a name="open-the-underlying-power-bi-report"></a>Öppna den underliggande Power BI-rapporten
Många av panelerna på instrumentpanelen för ”Exempel på kundlönsamhet” har fästs från underliggande exempelrapport om kundlönsamhet.

1. Välj en av dessa paneler för att öppna rapporten i läsvyn.

   Om panelen skapades i Frågor och svar öppnar den Frågor och svar-fönstret när du väljer den. Välj **Avsluta Frågor och svar** för att gå tillbaka till instrumentpanelen och prova en annan panel.

2. Rapporten innehåller tre sidor. Varje flik längst ned på rapporten representerar en egen sida.

    ![Tre flikar längst ned](media/sample-customer-profitability/power-bi-report-tabs.png)

    * **Teamresultatkort** fokuserar på de fem chefernas prestation och deras kontakter.
    * **Branschmarginalanalys** är ett sätt att analysera lönsamheten jämfört med det som pågår i branschen överlag.
    * **Chefresultatkort** ger en överblick över var och en av cheferna i anpassad sidstorlek.

### <a name="team-scorecard-page"></a>Sidan teamresultatkort
![Rapportsidan Teamresultatkort](media/sample-customer-profitability/customer2.png)

Nu ska vi titta på två teammedlemmar i detalj och se vilka insikter som kan uppnås: 

1. I utsnittet **Chef** till vänster kan du välja Andrews namn för att filtrera rapportsidan så att endast information om Andrew visas:

   * En snabb KPI finns i Andrews **Intäktsstatus (år totalt)** ; den är grön, vilket innebär att han presterar bra.
   * Diagrammet **Intäkter i % av avvikelse i budget efter månad och verkställande** visar att Andrew presterar bra, förutom en svacka i februari. Andrews starkaste region är Östra, som omfattar 49 kunder samt fem av sju produkter. Andrews bruttomarginal i % är varken den högsta eller den lägsta.
   * Diagrammet **Intäkter i år och varians i intäktsprocent mot budget efter månad** visar en stadig trend med jämn vinst. Men om du filtrerar genom att välja rutan för **centrala** i träddiagrammet för regioner ser du att Andrew endast har intäkter i mars och endast i Indiana. Är denna trend avsiktlig eller något som behöver undersökas?

2. Vi fortsätter till Valery. I utsnittet **Chef** väljer du Valerys namn för att filtrera rapportsidan så att endast data om Valery visas. 

   ![Valerys data](media/sample-customer-profitability/customer3.png)

   * Lägg märke till den röda KPI:n för **Intäktsstatus (år totalt)** . Detta objekt behöver definitivt undersökas närmare.
   * Valerys intäktvarians är också oroande – Valery uppfyller inte sina intäktsmarginaler.
   * Valery har bara nio kunder, hanterar endast två produkter och arbetar nästan uteslutande med kunder i den norra regionen. Den här specialiseringen kan förklara de stora måttfluktuationerna.
   * Om du väljer rutan **Nord** i träddiagrammet ser du att Valerys bruttomarginal i den norra regionen överensstämmer med den övergripande marginalen.
   * Om du väljer var och en av de andra rutorna för **Totala intäkter efter region** framträder något intressant: bruttomarginalen i % sträcker sig från 23 % till 79 %. Valerys intäktssiffror i alla regioner förutom den norra regionen är mycket starkt säsongsbaserade.

3. Fortsätt utforska för att ta reda på varför Valerys område inte presterar bra. Titta på regioner, andra affärsenheter och nästa sida i rapporten: **Branschmarginalanalys**.

### <a name="industry-margin-analysis"></a>Branschmarginalanalys
Den här rapporten innehåller ett annat datasnitt. Den ser ut på bruttomarginalen för hela branschen, uppdelat efter segment. Ekonomichefen använder den här sidan för att jämföra företaget och verksamhetens enhetsmått samt branschstatistiken för att förklara trender och lönsamhet. Du undrar kanske varför diagrammet **Bruttomarginal % per månad och chef** är på den här sidan eftersom det är teamspecifikt. När den är här kan vi filtrera sidan efter enhetschefen.  

![Rapportsidan branschmarginalanalys](media/sample-customer-profitability/customer6.png)

1. Hur varierar lönsamheten i olika branscher? Hur fördelas produkter och kunder i olika branscher? Få svar på dessa frågor genom att välja en eller flera branscher längst uppe till vänster (börja med CPG-branschen). Rensa filtret med hjälp av raderingsikonen.

2. På bubbeldiagrammet (**Intäktsavvikelse i % mot budget, bruttomarginal i % samt intäkter i år per bransch**) letar ekonomichefen efter de största bubblorna, eftersom de har störst inverkan på intäkterna. Du kan enkelt se varje chefs inverkan efter branschsegment genom att filtrera sidan. Det gör du genom att välja varje chefs namn i tur och ordning i ytdiagrammet.

3. Observera följande information när du markerar varje chef i diagrammet:
   * Andrews inflytande omfattar många olika branschsegment med vitt spridda ändringar % (de flesta är positiva) och Var %.
   * Annelies diagram är liknande, förutom att Annelie endast koncentrerar sig på ett fåtal branschsegment med fokus på segmentet Federalt och på produkten Gladius.
   * Carlos har ett tydligt fokus på tjänstsegmentet, med god vinst. Carlos har även avsevärt bättre variansprocent för tekniksegmentet, och hans nya segment, Industriellt, presterar exceptionellt väl jämfört med budgeten.
   * Tina arbetar med en handfull segment och har högst bruttomarginal i %, men de förhållandevis små bubblorna visar att Tinas inverkan på företagets slutresultat är minimal.
   * Valery, som endast är ansvarig för en produkt, arbetar endast i fem branschsegment. Valerys branschpåverkan är säsongsbaserad men skapar alltid en stor bubbla, vilket anger en betydande inverkan på företagets slutresultat. Förklarar branschsegmenten hennes negativa prestanda?

### <a name="executive-scorecard"></a>Chefresultatkort
Den här sidan har anpassad sidstorlek.

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>Prova data genom att ställa frågor med frågor och svar
För vår analys kan det vara bra att avgöra vilken bransch som står för den största omsättningen för Valery. Vi kan använda frågor och svar.

1. Välj **Redigera rapport** för att öppna rapporten i redigeringsvyn. Redigeringsvyn är endast tillgängligt om du äger rapporten. Den här vyn kallas ibland *skaparläge*. Om den här rapporten i stället bara delas med dig, kan du inte öppna den i redigeringsvyn.

2.  Överst på instrumentpanelen väljer du **Ställ en fråga** för att öppna frågerutan Frågor och svar.

    ![Ställ en fråga om dina data](media/sample-customer-profitability/power-bi-ask-question.png)

3. Skriv *totala intäkter per bransch för Valery* i frågerutan. Observera hur visualiseringen uppdateras när du skriver frågan.

    ![Skriva en fråga i frågerutan](media/sample-customer-profitability/power-bi-qna.png)

   Som du kan se är distributionsbranschen det största intäktsområdet för Valery.

### <a name="dig-deeper-by-adding-filters"></a>Granska djupare genom att lägga till filter
Vi tar en titt på distributionsbranschen.  

1. Öppna rapportsidan **Branschmarginalanalys**.
2. Expandera filterfönstret till höger utan att välja någon visualisering på rapportsidan (om den inte redan är expanderad). Fönstret **Filter** bör endast visa **Filter på sidnivå**.  

   ![Sidnivåfilter](media/sample-customer-profitability/power-bi-filters.png)
3. Gå till filtret för **Bransch** och välj pilen för att expandera listan. Lägg till ett sidfilter för distributionsbranschen. Avmarkera först alla kryssrutor genom att avmarkera kryssrutan **Markera alla**. Välj sedan endast **Distribution.**  

   ![filtret för Distribution](media/sample-customer-profitability/customer7.png)
4. Diagrammet **Bruttomarginal % per månad och chef** visar att endast Valery och Tina har kunder i den här branschen och att Valery endast arbetade med den här branschen från juni till november.   
5. Välj **Tina** och sedan **Valery** i diagramförklaringen för **Bruttomarginal per månad och chef**. Observera att Tinas andel av diagrammet **Totala intäkter per produkt** är liten jämfört med Valerys.
6. Om du vill visa faktiska intäkter väljer du rutan Frågor och svar på instrumentpanelen och skriver *totala intäkter efter chef för distribution enligt scenario*.  

     ![Skriva in en fråga i frågerutan Frågor och svar](media/sample-customer-profitability/power-bi-qna2.png)

    Vi kan utforska andra branscher och till och med lägga till kunder i våra visuella objekt för att förstå grunden till Valerys prestationer.

## <a name="next-steps-connect-to-your-data"></a>Nästa steg: Anslut till dina data
Den här miljön är säker att leka i eftersom du kan välja att inte spara dina ändringar. Men om du sparar dem kan du alltid välja **Hämta data** för att få en ny kopia av exemplet.

Vi hoppas att denna rundtur har visat hur Power BI-instrumentpaneler, frågor och svar, samt rapporter kan ge insikter om exempeldata. Nu är det din tur – anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer i [Kom igång med Power BI-tjänsten](service-get-started.md).

