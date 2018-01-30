---
title: "Exempel på detaljhandelsanalys för Power BI: ta en rundtur"
description: "Exempel på detaljhandelsanalys för Power BI: ta en rundtur"
services: powerbi
documentationcenter: 
author: mihart
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
ms.date: 01/17/2018
ms.author: mihart
ms.openlocfilehash: 97c8f3f74bea0629107b68b9e42a4a449863b066
ms.sourcegitcommit: 1a5446c3136dc0787f2a1d5b8cad1113704301ba
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/24/2018
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>Exempel på detaljhandelsanalys för Power BI: ta en rundtur

Det här branschexemplets instrumentpanel och underliggande rapport analyserar försäljningsdata för sålda artiklar över flera butiker och distrikt. Måtten jämför årets resultat med förra årets inom följande områden: försäljning, enheter, bruttomarginal och avvikelse, samt lagringsanalys. Det här är verkliga data från obviEnce ([www.obvience.com](http://www.obvience.com)) som har anonymiserats.

![](media/sample-retail-analysis/retail1.png)

## <a name="prerequisites"></a>Förutsättningar

 Innan du kan använda exemplet, måste du först hämta det som ett innehållspaket, en .pbix-fil eller en Excel-arbetsbok.

### <a name="get-the-content-pack-for-this-sample"></a>Hämta innehållspaketet för det här exemplet

1. Öppna Power BI-tjänsten (app.powerbi.com) och logga in.
2. Längst ned i vänster hörn väljer du **Hämta data**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. På sidan Hämta data väljer du ikonen **Exempel**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Välj **Exempel på detaljhandelsanalys** och sedan **Anslut**.  
  
   ![Exempel på detaljhandelsanalys](media/sample-retail-analysis/retail16.png)
   
5. Power BI importerar innehållspaketet och lägger till en ny instrumentpanel, rapport och datauppsättning till din aktuella arbetsyta. Det nya innehållet markeras med en gul asterisk. 
   
   ![Exempel på detaljhandelsanalys](media/sample-retail-analysis/retail17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Hämta .pbix-filen för det här exemplet

Du kan även hämta exemplet som en .pbix-fil som är avsedd för användning med Power BI Desktop. 

 * [Exempel på detaljhandelsanalys](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Hämta Excel-arbetsboken för det här exemplet
Du kan också [hämta enbart datauppsättningen (Excel-arbetsboken) för det här exemplet](http://go.microsoft.com/fwlink/?LinkId=529778). Arbetsboken innehåller Power View-blad som du kan visa och ändra. För att se rådata väljer du **Power Pivot > Hantera**.

## <a name="start-on-the-dashboard-and-open-the-report"></a>Starta på instrumentpanelen och öppna rapporten
1. Välj panelen ”Totalt antal butiker” på instrumentpanelen:

   ![](media/sample-retail-analysis/retail-analysis-7.png)  

   Du kommer då till sidan ”Översikt över butiksförsäljning” i rapporten. Du kan se att vi har 104 butiker totalt, varav 10 är nya. Vi har två kedjor, Fashions Direct och Lindseys. Fashions Directs butiker är större i genomsnitt.
2. I cirkeldiagrammet väljer du **Fashions Direct**.

   ![](media/sample-retail-analysis/retail3.png)  

   Observera resultatet i bubbeldiagrammet:

   ![](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   Distriktet FD-01 har den högsta genomsnittliga försäljningen per kvadratfot, FD-02 har den lägsta avvikelsen i försäljning jämfört med föregående år, FD-03 och FD-04 har de övergripande sämsta resultaten.
3. Välj enskilda bubblor eller andra diagram för att se korsmarkering och effekten av dina val.
4. Om du vill återgå till instrumentpanelen markerar du dess namn i det övre navigeringsfältet (synlig sökväg).

   ![](media/sample-retail-analysis/power-bi-breadcrumbs.png)
5. På instrumentpanelen väljer du panelen ”Årets försäljning”.

   ![](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   Detta motsvarar att skriva ”Detta års försäljning” i frågerutan.

   Följande skärm visas:

   ![](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>Granska en panel som skapats med Frågor och svar i Power BI
Låt oss bli lite mer specifika.

1. Lägg till ”Detta års försäljning **per distrikt**” i frågan. Observera resultatet: Svaret placeras automatiskt i ett stapeldiagram och ger förslag på andra fraser:

   ![](media/sample-retail-analysis/retail8.png)
2. Ändra nu frågan till ”Årets försäljning **per postnummer och kedja**”.

   Observera hur frågan besvaras med lämpliga diagram samtidigt som du skriver.
3. Experimentera med fler frågor och se vilken typ av resultat du får.
4. När du är klar går du tillbaka till instrumentpanelen.

## <a name="dive-deeper-into-the-data"></a>Fördjupa dig i datan
Nu ska vi titta närmare på en mer detaljerad nivå, nämligen distriktens resultat.

1. På instrumentpanelen väljer du den panel som jämför årets försäljning med föregående år.

   ![](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   Lägg märke till att det är stora skillnader i Avvikelse i % jämfört med föregående år, där januari, april och juli är särskilt dåliga månader.

   ![](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   Låt oss se om vi kan upptäcka vad problemet är.
2. Markera bubbeldiagrammet och välj **020-Herr**.

   ![](media/sample-retail-analysis/retail11.png)  

   Observera att herrkategorin inte var lika kraftigt påverkad i april som den övergripande verksamheten, men att januari och juli ändå var problemmånader.
3. Välj nu **bubblan 010-Dam**.

   ![](media/sample-retail-analysis/retail12.png)

   Observera att damkategorin hade ett mycket sämre resultat än den övergripande verksamheten under alla månader, och mycket värre under nästan alla månader jämfört med föregående år.
4. Välj bubblan igen för att ta bort filtret.

## <a name="try-out-the-slicer"></a>Testa utsnittet
Nu ska vi titta på hur det går för vissa distrikt.

1. Välj Allan Guinot i utsnittet uppe till vänster.

   ![](media/sample-retail-analysis/retail13.png)

   Observera att Allans distrikt gick bättre än förväntat mot förra året i mars och juni.
2. Nu, medan Allan fortfarande är markerad, väljer du bubblan Dam.

   ![](media/sample-retail-analysis/power-bi-allan.png)

   Observera att för damkategorin i hans distrikt uppnåddes aldrig förra året volym.
3. Utforska andra distriktschefer och kategorier – vilka andra insikter kan du hitta?
4. När du är klar går du tillbaka till instrumentpanelen.

## <a name="what-is-our-data-telling-us-about-sales-growth-this-year"></a>Vad säger våra data om försäljningstillväxten i år?
Det sista område som vi ska utforska är vår tillväxt – det har öppnats nya butiker det här året.

1. Välj panelen ”Butiker som öppnats detta år”.

   ![](media/sample-retail-analysis/retail15.png)

   Som framgår i panelen har det öppnats fler Fashion Direct-butiker än Lindseys-butiker i år.
2. Se diagrammet ”Försäljning per kvadratfot och namn”:

   ![](media/sample-retail-analysis/retail14.png)

    Det är rätt stor skillnad i den genomsnittliga försäljningen per kvadratfot för de nya butikerna.
3. Klicka på förklaringsobjektet för Fashions Direct i det övre högra diagrammet. Observera att till och med i samma kedja utklassar den bästa butiken (Winchester Fashions Direct) den sämsta butiken (Cincinnati 2 Fashions Direct) med $21.22 mot $12.86.

   ![](media/sample-retail-analysis/power-bi-lindseys.png)
4. Klicka på Winchester Fashions Direct i utsnittet och observera linjediagrammet. De första försäljningssiffrorna rapporterades i februari.
5. Klicka på Cincinnati 2 Fashions Direct i utsnittet. Du ser då i linjediagrammet att den öppnades i juni och verkar vara den sämst presterande butiken.
6. Som tidigare utforskar du genom att klicka på andra staplar, linjer och bubblor i diagrammen och se vilka insikter du kan upptäcka.

Det här är en säker miljö att testa i. Du kan alltid välja att inte spara ändringarna. Fast du sparar dem kan du alltid gå till Hämta data för att få en ny kopia av exemplet.

## <a name="connect-to-your-data"></a>Anslut till dina data
Vi hoppas att denna rundtur har visat hur Power BI-instrumentpaneler, frågor och svar, samt rapporter kan ge insikter om detaljhandelsdata. Nu är det din tur – anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer om att [komma igång med Power BI](service-get-started.md).

## <a name="next-steps"></a>Nästa steg
* [Ladda ned innehållspaketet med exempel på detaljhandelsanalys](sample-tutorial-connect-to-the-samples.md)    
* [Ladda ned Excel-arbetsboken för det här Power BI-exemplet](http://go.microsoft.com/fwlink/?LinkId=529778)    
* [Hämta data (för Power BI)](service-get-data.md)    
* [Power BI – grundläggande begrepp](service-basic-concepts.md)    
* Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
