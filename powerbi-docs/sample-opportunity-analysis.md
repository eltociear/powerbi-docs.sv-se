---
title: 'Exempel på affärsmöjlighetsanalys för Power BI: Ta en rundtur'
description: 'Exempel på affärsmöjlighetsanalys för Power BI: Ta en rundtur'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: d871fa15c999e5b6c83b0334d6c978b2ba3c9870
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73858713"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Exempel på affärsmöjlighetsanalys för Power BI: Ta en rundtur

Exempelinnehållspaketet analys av affärsmöjligheter innehåller en instrumentpanel för ett programvaruföretag som har två försäljningskanaler: *direkt* och *partner*. Säljchefen skapade den här instrumentpanelen för att spåra affärsmöjligheter och intäkter efter region, avtalsstorlek och kanal.

Exemplet förlitar sig på två intäktsmått:

* Intäkter: En säljares uppskattning av vad företagets intäkter kommer att bli.
* Beräknade intäkter: Detta beräknas som intäkter X sannolikhetsprocent och ger en mer rättvisande prognos om faktiska försäljningsintäkter. Sannolikheten bestäms av avtalets aktuella *försäljningsteg*:
  * Möjlighet: 10 %  
  * Kvalificera: 20 %  
  * Lösning: 40 %  
  * Förslag: 60 %  
  * Slutför: 80 %

![Instrumentpanel för exemplet analys av affärsmöjligheter](media/sample-opportunity-analysis/opportunity1.png)

Det här exemplet ingår i en serie som visar hur du kan använda Power BI med verksamhetsorienterade data, rapporter och instrumentpaneler. Det skapades av [obviEnce](http://www.obvience.com/) med verkliga data, som har anonymiserats. Dessa data är tillgängliga i flera format: innehållsförpackning, .pbix-fil för Power BI Desktop eller Excel-arbetsbok. Se [Exempel för Power BI](sample-datasets.md). 

De här självstudierna använder Power BI-tjänsten och utforskar innehållspaketet med exemplet på analys av affärsmöjligheter. Eftersom rapportupplevelserna är så lika i Power BI Desktop och tjänsten kan du även följa med via .pbix-exempelfilen i Power BI Desktop. 

Du behöver inte en licens för Power BI för att utforska exempel i Power BI Desktop. Om du inte har en Power BI Pro-licens kan du spara exemplet på Min arbetsyta i Power BI-tjänsten. 

## <a name="get-the-sample"></a>Hämta exemplet

Innan du kan använda exemplet, måste du först hämta det som ett [innehållspaket](#get-the-content-pack-for-this-sample), en [.pbix-fil](#get-the-pbix-file-for-this-sample) eller en [Excel-arbetsbok](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Hämta innehållspaketet för det här exemplet

1. Öppna Power BI-tjänsten (app.powerbi.com), logga in och öppna den arbetsyta där du vill spara exemplet. 

    Om du inte har en Power BI Pro-licens kan du spara exemplet på Min arbetsyta.

2. Längst ned i vänster hörn väljer du **Hämta data**.

    ![Välja Hämta data](media/sample-datasets/power-bi-get-data.png)
3. På sidan **Hämta data** väljer du **Exempel**.

4. Välj **Exempel på analys av affärsmöjlighetet** och sedan **Anslut**.  

   ![Ansluta till exempel](media/sample-opportunity-analysis/opportunity-connect.png)
5. Power BI importerar innehållspaketet och lägger sedan till en ny instrumentpanel, rapport och datamängd till din aktuella arbetsyta.

   ![Post i exempel på affärsmöjlighetsanalys](media/sample-opportunity-analysis/opportunity-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>Hämta .pbix-filen för det här exemplet

Du kan även ladda ned Exempel på analys av affärsmöjligheter som en [.pbix-fil](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix) som är avsedd för användning med Power BI Desktop.

### <a name="get-the-excel-workbook-for-this-sample"></a>Hämta Excel-arbetsboken för det här exemplet

Om du vill visa i datakällan för det här exemplet är det även tillgängligt som en [Excel-arbetsbok](https://go.microsoft.com/fwlink/?LinkId=529782). Arbetsboken innehåller Power View-blad som du kan visa och ändra. Om du vill se rådata aktiverar du dataanalystilläggen och väljer **Power Pivot > Hantera**. Aktivering av tilläggen för Power View och Power Pivot beskrivs i avsnittet om att [titta på Excel-exemplen inuti själva Excel](sample-datasets.md#optional-take-a-look-at-the-excel-samples-from-inside-excel-itself).

## <a name="what-is-our-dashboard-telling-us"></a>Vad kan vi utläsa från instrumentpanelen?
Vår säljchef har skapat en instrumentpanel för att spåra de mått som är viktigast. Säljchefen kan välja en panel för att granska data närmare när något intressant dyker upp:

- Företagets intäkter är 2 miljarder dollar och de beräknade intäkterna är 461 miljoner dollar.
- Antalet affärsmöjligheter och intäkter följer en bekant trattmönster där summorna minskar för varje efterföljande steg.
- De flesta affärsmöjligheterna är i region öst.
- Stora affärsmöjligheterna genererar mer intäkter än de medelstora eller små affärsmöjligheterna.
- Stora partnererbjudanden ger större intäkter: 8 miljoner USD i genomsnitt jämfört med 6 miljoner USD för direktförsäljning.

Eftersom ansträngningen för att få till ett avtal är samma oavsett om avtalet klassas som stort, medelstort eller litet, bör vårt företag analysera data för att lära sig mer om stora affärsmöjligheter.

1. I arbetsytan där du sparade exemplet öppnar du fliken **Instrumentpaneler**. Hitta sedan instrumentpanelen **Affärsmöjlighetsanalys** och välj den.

2. Välj panelen **Antal affärsmöjligheter efter partnerdrivna försäljningssteg** för att öppna den första sidan i rapporten Analys av affärsmöjligheter. 

    ![Panelen antal affärsmöjligheter efter partnerdrivna försäljningssteg](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>Utforska sidorna i rapporten

Visa alla sidor i rapporten genom att välja flikarna längst ned på sidan.

### <a name="opportunity-count-overview-page"></a>Sidan Översikt över antal affärsmöjligheter
![Sidan antal affärsmöjligheter](media/sample-opportunity-analysis/opportunity3.png)

Observera följande information:
* Öst är vår största region när det gäller antal affärsmöjligheter.  
* I cirkeldiagrammet **Antal affärsmöjligheter efter region** väljer du varje region i tur och ordning för att filtrera sidorna efter region. Observera att storleken på de affärsmöjligheter som partners satsar på ökar för varje region.   
* Stapeldiagrammet **antal affärsmöjligheter efter partnerdrivna och storlek på affärsmöjligheter** visar tydligt att de flesta av de stora affärsmöjligheterna är partnerdrivna och flera av de små och medelstora affärsmöjligheterna inte är partnerdrivna.
* I stapeldiagrammet **Antal affärsmöjligheter efter försäljningsfas** markerar du varje **Försäljningssteg** i tur och ordning för att se skillnaden i regionala antal. Trots att den östra regionen har det största antalet affärsmöjligheter kan du observera att alla tre regioner har jämförbara antal i säljstegen Lösning, Förslag och Slutför. Det här innebär att vi slutför en högre procentandel avtal i de centrala och västra regionerna.

### <a name="revenue-analysis-page"></a>Sidan intäktsanalys
Den här sidan tar en liknande titt på data, men med ett intäktsperspektiv istället för antal.  

![Sidan Översikt över intäkter](media/sample-opportunity-analysis/opportunity4.png)

Observera följande information:
* Öst är vår största region inte bara när det gäller antal affärsmöjligheter, men även intäkter.  
* Om du filtrerar diagrammet **intäkter efter försäljningssteg och partnerdrivna** genom att välja **Ja** för **Partnerdrivna** visas intäkter på 1,5 miljarder USD och beräknade intäkter på 294 miljoner USD. Jämför dessa belopp med 644 miljoner USD och 166 miljoner USD för intäkter som inte är partnerdrivna. 
* Genomsnittliga intäkter för stora konton är större vid 8 miljoner om affärsmöjligheten är partnerdriven jämfört med 6 miljoner för icke-partnerdriven verksamhet.  
* För partnerdriven verksamhet är de genomsnittliga intäkterna för stora affärsmöjligheter nästan dubbelt jämfört med medelstora affärsmöjligheter.  
* Genomsnittlig intäkt för små och medelstora företag är jämförbara för både partnerdrivna och icke-partnerdrivna företag.   

Våra samarbetspartners gör uppenbart ett bättre jobb än icke-partners när det gäller att sälja till kunder. Det kan vara klokt att styra fler affärer via våra partners.

### <a name="opportunity-count-by-region-and-stage"></a>Antal affärsmöjligheter efter Region och Steg
Den här sidan i rapporten tittar på data som liknar data i den föregående sidan men delar upp dem efter region och steg. 

![Sidan antal steg per region](media/sample-opportunity-analysis/opportunity5.png)

Observera följande information:
* Om du väljer **Öst** i cirkeldiagrammet **Antal affärsmöjligheter efter region** för att filtrera efter regionen Öst ser du att affärsmöjligheterna i den här regionen är nästan lika uppdelade mellan partnerdrivna och icke-partnerdrivna.
* Stora affärsmöjligheter är vanligast i den centrala regionen, små affärsmöjligheter är vanligast i region öst och medelstora affärsmöjligheter är vanligast i region väst.

### <a name="upcoming-opportunities-by-month-page"></a>Sidan kommande affärsmöjligheter efter månad
Vi tittar än en gång på liknande faktorer, men den här gången från perspektivet datum och tid. 
 
![Sidan kommande affärsmöjligheter](media/sample-opportunity-analysis/opportunity6.png)

Vår ekonomichef använder den här sidan för att hantera arbetsbelastning. Genom att titta på intäktsmöjligheter efter säljsteg och månad kan ekonomichefen planera på lämpligt sätt.

Observera följande information:
* Genomsnittliga intäkter för steget Slutför är högst. Det är av högsta vikt att slutföra de här avtalen.
* Om du filtrerar per månad (genom att välja månadsnamnet i utsnittet **Månad**) ser du att januari har en hög andel stora avtal i Slutför-steget med beräknade intäkter på 75 miljoner USD. Å andra sidan hade februari främst medelstora avtal i lösnings- och förslagstegen.
* Generellt sätt, varierar de beräknade intäktssiffrorna baserat på säljsteg, antal affärsmöjligheter och avtalsstorlek. Lägg till filter med **filterfönstret** till höger för att upptäcka ytterligare insikter.

## <a name="next-steps-connect-to-your-data"></a>Nästa steg: Anslut till dina data
Den här miljön är säker att leka i eftersom du kan välja att inte spara dina ändringar. Men om du sparar dem kan du alltid välja **Hämta data** för att få en ny kopia av exemplet.

Vi hoppas att denna rundtur har visat hur Power BI-instrumentpaneler, frågor och svar, samt rapporter kan ge insikter om exempeldata. Nu är det din tur – anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer i [Kom igång med Power BI-tjänsten](service-get-started.md).

