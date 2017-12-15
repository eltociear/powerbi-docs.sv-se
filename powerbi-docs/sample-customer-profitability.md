---
title: "Exempel på kundlönsamhet för Power BI: Ta en rundtur"
description: "Exempel på kundlönsamhet för Power BI: Ta en rundtur"
services: powerbi
documentationcenter: 
author: amandacofsky
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
ms.date: 10/29/2017
ms.author: mihart
ms.openlocfilehash: 9a100b7d13c11a8bd066b72a570f45d0c2bc08be
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Exempel på kundlönsamhet för Power BI: Ta en rundtur
Innehållspaketet ”Exempel på kundlönsamhet” innehåller en instrumentpanel, en rapport och en datauppsättning för ett företag som tillverkar marknadsföringsmaterial. Den här instrumentpanelen skapades av en ekonomichef för att visa en statistiköversikt för hennes 5 enhetschefer, produkter, kunder och bruttomarginal. I korthet kan hon se vilka faktorer som påverkar lönsamheten.

Det här exemplet ingår i en serie som illustrerar hur du kan använda Power BI med affärsorienterade data, rapporter och instrumentpaneler. Det här är verkliga data från obviEnce ([www.obvience.com](http://www.obvience.com/)) som har anonymiserats.

Du kan också [hämta enbart datauppsättningen (Excel-arbetsboken) för det här exemplet](http://go.microsoft.com/fwlink/?LinkId=529781).  
![](media/sample-customer-profitability/power-bi-dash.png)

## <a name="what-is-our-dashboard-telling-us"></a>Vad kan vi utläsa från instrumentpanelen?
### <a name="company-wide-dashboard-tiles"></a>Instrumentpaneler för hela företaget
Dessa paneler get vår ekonomichef en överblick över de mått för företaget på hög nivå som är viktiga för henne.  När hon ser något intressant, kan hon välja en panel för att granska närmare.

1. Vårt företags bruttomarginal är 42,5 %.
2. Vi har 80 kunder.
3. Vi säljer 5 olika produkter.
4. Vi hade våra lägsta intäktsavvikelse % i förhållande till budget i februari, följt av vår högsta i mars.
5. De flesta av våra intäkter kommer från regionerna öst och norr. Bruttomarginalen överskred aldrig budgeten, men ER 0 och MA-0 kräver något närmare granskning.
6. Totala intäkter för året ligger nära budgeten.

### <a name="manager-specific-dashboard-tiles"></a>Chefspecifika instrumentpaneler
Dessa paneler ger ett resultatkort för teamet. Det är viktigt för ekonomichefen att kunna följa cheferna och dessa paneler ger henne en översikt över vinsten med hjälp av bruttomarginal i %. Om trenden för bruttomarginalen % är oväntad för någon chef kan hon undersöka detta närmare.

Annelies bruttomarginal % är lägst, men det syns en konstant ökning sedan mars. Å andra sidan har Valerys bruttomarginal % avtagit avsevärt. Anders har haft ett varierande år. Klicka på någon av de chefspecifika panelerna för att öppna den tillhörande rapporten. Rapporten har 3 sidor och öppnar sidan ”branschmarginalanalys”.

## <a name="explore-the-pages-in-the-report"></a>Utforska sidorna i rapporten
Vår rapport har 3 sidor:

* ”Teamresultatkort” fokuserar på de 5 chefernas prestation och deras ”räkenskaper”.
* ”Branschmarginalanalys” är ett sätt att analysera vår lönsamhet jämfört med hela branschen.
* ”Chefresultatkort” ger en överblick över var och en av våra chefer och formateras för visning i Cortana.

### <a name="team-scorecard-page"></a>Sidan teamresultatkort
![](media/sample-customer-profitability/customer2.png)

Nu ska vi titta på två teammedlemmar i detalj och se vilka insikter som kan uppnås. Med hjälp av delaren till vänster kan du välja Andrews namn för att filtrera rapportsidan så att endast information om Andrew visas.

* För en snabb KPI, titta på Anders **intäktstatus** – det är grönt. Han presterar bra.
* Ytdiagrammet ”Intäkter Var % mot budget per månad” visar att Anders presterar ganska bra överlag, förutom en svacka i februari. Hans starka region är Öst och han hanterar 49 kunder och 5 (av 7) produkter. Hans bruttomarginal % är varken högst eller lägst.
* ”RevenueTY och intäkter Var % budget per månad” visar stadig och jämn tillväxt. Men när du filtrerar genom att klicka på rutan för **centrala** i träddiagrammet för regioner ser du att Andrew endast har intäkter för mars och endast i Indiana. Är det avsiktligt eller är detta något du behöver titta på?

Vi fortsätter till Valery. Med hjälp av delaren kan du välja Valerys namn för att filtrera rapportsidan så att endast information om Valery visas.  
![](media/sample-customer-profitability/customer3.png)

* Lägg märke till röd KPI för **RevenueTY Status**. Detta måste definitivt undersökas närmare.
* Hennes intäktvarians är också oroande – hon möter inte sina intäktsmarginaler.
* Valery har bara 9 kunder, hanterar endast 2 produkter och arbetar nästan uteslutande med kunder i norr. Den här specialiseringen kan förklara varför hennes mått fluktuerar så mycket.
* När du öppnar rutan **Nord** i träddiagrammet ser du att Valerys bruttomarginal i regionen Nord överensstämmer med hennes övergripande marginal.
* När du väljer de andra **Region**-rutorna framgår en intressant berättelse: hennes bruttomarginaler i % sträcker sig från 23 % 79 % och hennes intäkter i alla regioner utom Nord är mycket säsongsbaserade.

Fortsätt att granska på djupet för att ta reda på varför Valerys område inte presterar bra. Titta på regioner, andra affärsenheter och nästa sida i rapporten – ”branschmarginalanalysen”.

### <a name="industry-margin-analysis"></a>Branschmarginalanalys
Den här rapporten innehåller ett annat datasnitt. Den ser ut på bruttomarginalen för hela branschen, uppdelat efter segment. Ekonomichefen använder den här sidan för att jämföra företaget och verksamhetens enhetsmått samt branschstatistiken för att förklara hennes trender och lönsamhet. Du kanske undrar varför ytdiagrammet ”bruttomarginal per månad och chef” är på den här sidan eftersom det gäller team. När den är här kan vi filtrera sidan efter enhetschefen.  
![](media/sample-customer-profitability/customer6.png)

Hur varierar lönsamheten i olika branscher? Hur fördelas produkter och kunder i olika branscher? Välj en eller flera branscher upp till vänster. (börja ed CPG-branschen) Använd ikonen Radera för att ta bort filtret.

Ekonomichefen letar efter de största bubblorna på bubbeldiagrammet eftersom det är dessa som har störst inverkan på intäkterna. Genom att filtrera sidan enligt chef genom att klicka på deras namn i ytdiagrammet är det lätt att se chefens inverkan för varje branschsegment.

* Andrews inflytande omfattar många olika branschsegment med vitt spridda ändringar % (de flesta är positiva) och Var %. 
* Annelies diagram är liknande, förutom att hon endast koncentrerar sig på en handfull branschsegment med fokus på federala segment och fokus på Gladius-produkten. 
* Carlos har ett tydligt fokus på tjänstsegmentet, med god vinst. Han har en avsevärt bättre varians % för tekniksegmentet och hans nya segment, industriell, presterar exceptionellt bra jämfört med budget. 
* Tina arbetar med en handfull segment och har högst bruttomarginal i %, men de förhållandevis små bubblorna visar att hennes inverkan på företagets slutresultat är minimal. 
* Valery som endast är ansvarig för en produkt, arbetar endast i 5 branschsegment. Hennes branschpåverkan är säsongsbaserat, men skapar alltid en stor bubbla, vilket anger en betydande inverkan på företagets slutresultat. Förklarar branschen hennes sämre prestanda?

### <a name="executive-scorecard"></a>Chefresultatkort
Den här sidan formateras som en svarskort för Cortana. Läs mer i [skapa Svarskort för Cortana](service-cortana-answer-cards.md)

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>Prova data genom att ställa frågor med frågor och svar
För vår analys skulle det vara bra att avgöra vilken bransch som står för den största omsättningen för Valery. Vi kan använda frågor och svar.

1. Välj **Power BI** i det övre navigeringsfältet att återgå till instrumentpanelen.
2. Markera rutan Frågor och svar överst i instrumentpanelen.
   
    ![](media/sample-customer-profitability/customer4.png)
3. Skriv **total intäkter per bransch för Valery**. Observera hur visualiseringen uppdateras när du skriver frågan.
   
    ![](media/sample-customer-profitability/customer5.png)
   
   Distributionen är det största intäktsområdet för Valery.

### <a name="dig-deeper-by-adding-filters"></a>Granska djupare genom att lägga till filter
Låt oss ta en titt på branschen *Distribution*.  

1. Gå tillbaka till instrumentpanelen och välj ytdiagrammet med Andrews bruttomarginaltrend. Detta öppnar rapporten på sidan ”branschmarginalanalys”.
2. Expandera filterfönstret till höger utan att välja någon visualisering på rapportsidan. Fönstret filter bör endast visa filter på sidonivå.  
   
   ![](media/sample-customer-profitability/power-bi-filters.png)
3. Gå till filtret för **Bransch** och välj pilen för att expandera listan. Lägg till ett sidfilter för distributionsbranschen. Avmarkera först alla kryssrutor genom att avmarkera kryssrutan **Markera alla**. Välj sedan **Distribution.**  
   
   ![](media/sample-customer-profitability/customer7.png)
4. I ytdiagrammet ”Bruttomarginal per månad och namn på chef” er vi att endast Valery och Tina har kunder i den här branschen och Valery har endast arbetat med den här branschen från juni till november.   
5. Välj **Tina** och sedan **Valery** i diagramförklaringen för ”Bruttomarginal per månad och namn på chef”. Observera att Tinas del av ”Totala intäkter per produkt” är mycket liten jämfört med Valery. 
6. Om du vill se faktiska intäkter, gå tillbaka till instrumentpanelen och sök **Totala intäkter för distribution enligt scenario och chef** i Frågor och svar.  
   
   ![](media/sample-customer-profitability/customer8.png)

Vi kan utforska andra branscher och till och med lägga till kunder i våra visuella objekt för att förstå grunden till Valerys prestationer.

Det här är en säker miljö att leka runt i. Du kan alltid välja att inte spara ändringarna. Men om du sparar dem, kan du alltid gå till **Hämta data** för en ny kopia av det här exemplet.

## <a name="next-steps-connect-to-your-data"></a>Nästa steg: anslut till dina data
Vi hoppas att denna rundtur har visat hur Power BI-instrumentpaneler, frågor och svar, samt rapporter kan ge insikter om kunddata. Nu är det din tur – anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer om att [komma igång med Power BI](service-get-started.md).

[Tillbaka till exempel i Power BI](sample-datasets.md)  

