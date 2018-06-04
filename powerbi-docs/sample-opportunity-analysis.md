---
title: 'Exempel på affärsmöjlighetsanalys för Power BI: Ta en rundtur'
description: 'Exempel på affärsmöjlighetsanalys för Power BI: Ta en rundtur'
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/20/2018
ms.author: mihart
LocalizationGroup: Samples
ms.openlocfilehash: d3a18b2505739d28276fbe9fc269bbf774879fa6
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34481082"
---
# <a name="opportunity-analysis-sample-for-power-bi-take-a-tour"></a>Exempel på affärsmöjlighetsanalys för Power BI: Ta en rundtur

## <a name="overview-of-the-opportunity-analysis-sample"></a>Översikt över exemplet för analys av affärsmöjligheter
**Exemplet analys av affärsmöjligheter** innehåller en instrumentpanel (och associerad rapport) för ett programvaruföretag som har 2 försäljningskanaler: *direkt* och *partner*. Säljchefen skapade den här instrumentpanelen för att spåra affärsmöjligheter och intäkter efter region, avtalsstorlek och kanal.

Säljchefen förlitar sig på 2 intäktsmått:

* **Intäkter** – detta är en säljares uppskattning av vad han tror att intäkten kommer att bli.
* **Inberäknade intäkter** – detta beräknas som intäkter X sannolikhetsprocent och anses allmänt ge en mer rättvisande prognos om faktiska försäljningsintäkter. Sannolikheten bestäms av avtalets aktuella ***försäljningsteg***.
  * Lead – 10%  
  * Kvalificera – 20%  
  * Lösning – 40%  
  * Förslag – 60%  
  * Slutför – 80%

  ![](media/sample-opportunity-analysis/opportunity1.png)

Det här exemplet ingår i en serie som illustrerar hur du kan använda Power BI med affärsorienterade data, rapporter och instrumentpaneler. Det här är verkliga data från obviEnce ([www.obvience.com](http://www.obvience.com/)) som har anonymiserats.

## <a name="prerequisites"></a>Förutsättningar

 Innan du kan använda exemplet, måste du först hämta det som ett [innehållspaket](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample), en [.pbix-fil](http://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity-Analysis-Sample-PBIX.pbix) eller en [Excel-arbetsbok](http://go.microsoft.com/fwlink/?LinkId=529782).

### <a name="get-the-content-pack-for-this-sample"></a>Hämta innehållspaketet för det här exemplet

1. Öppna Power BI-tjänsten (app.powerbi.com) och logga in.
2. Längst ned i vänster hörn väljer du **Hämta data**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. På sidan Hämta data väljer du ikonen **Exempel**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Välj **Exempel på detaljhandelsanalys** och sedan **Anslut**.  
  
   ![Hämta data](media/sample-opportunity-analysis/opportunity-connect.png)
   
5. Power BI importerar innehållspaketet och lägger till en ny instrumentpanel, rapport och datauppsättning till din aktuella arbetsyta. Det nya innehållet markeras med en gul asterisk. 
   
   ![Asterisk](media/sample-opportunity-analysis/opportunity-asterisk.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Hämta .pbix-filen för det här exemplet

Du kan även hämta exemplet som en .pbix-fil som är avsedd för användning med Power BI Desktop. 

 * [Exempel på affärsmöjlighetsanalys](http://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Hämta Excel-arbetsboken för det här exemplet
Du kan också [hämta enbart datauppsättningen (Excel-arbetsboken) för det här exemplet](http://go.microsoft.com/fwlink/?LinkId=529782). Arbetsboken innehåller Power View-blad som du kan visa och ändra. För att se rådata väljer du **Power Pivot > Hantera**.


## <a name="what-is-our-dashboard-telling-us"></a>Vad kan vi utläsa från instrumentpanelen?
Vår säljchef har skapat en instrumentpanel för att spåra de mått som är viktigast för henne. När hon ser något intressant, kan hon välja en panel för att granska närmare.

1. Företagets intäkter är 2 miljarder dollar och de beräknade intäkterna är 461 miljoner dollar.
2. Antalet affärsmöjligheter och intäkter följer en bekant trattmönster där summorna minskar för varje efterföljande steg.
3. De flesta affärsmöjligheterna är i region öst.
4. De stora affärsmöjligheterna genererar mer intäkter än de medelstora eller små affärsmöjligheterna.
5. Stora partneravtal genererar mer intäkter: 8 miljoner dollar i genomsnitt jämfört med 6 miljoner dollar direkt försäljning.

Eftersom ansträngningen för att få till ett avtal är samma oavsett om avtalet klassas som stort, medelstort eller litet, bör vårt företag analysera data för att lära sig mer om stora affärsmöjligheter.

Välj panelen **antal affärsmöjligheter efter partnerdrivna och försäljningsfas** för att öppna sida 1 i rapporten.  
![](media/sample-opportunity-analysis/opportunity2.png)

## <a name="explore-the-pages-in-the-report"></a>Utforska sidorna i rapporten
### <a name="page-1-of-our-report-is-titled-opportunity-count-overview"></a>Sida 1 i vår rapport heter översikt över antal affärsmöjligheter.
![](media/sample-opportunity-analysis/opportunity3.png)

* Öst är vår största region när det gäller antal affärsmöjligheter.  
* I cirkeldiagrammet markerar du varje region en åt gången för att filtrera sidan. För varje region, går partners efter betydligt fler stora affärsmöjligheter.   
* Stapeldiagrammet antal affärsmöjligheter efter partnerdrivna och storlek på affärsmöjligheter visar tydligt att de flesta av de stora affärsmöjligheterna är partnerdrivna och flera av de små och medelstora affärsmöjligheterna inte är partnerdrivna.
* Markera varje försäljningssteg i stapeldiagrammet i nedre vänstra hörnet för att se skillnaden i regionala antal och notera att även om öst är vår största region vad det gäller antal så har stegen lösning, förslag och slutför i alla 3 regioner jämförbara antal. Det här betyder att vi väljer en högre procentandel avtal i central och väst.

### <a name="page-2-of-our-report-is-titled-revenue-overview"></a>Sida 2 av vår rapport heter intäktsöversikt.
Den här sidan tar en liknande titt på data, men med ett intäktsperspektiv istället för antal.  
![](media/sample-opportunity-analysis/opportunity4.png)

* Öst är vår största region inte bara när det gäller antal affärsmöjligheter, men även intäkter.  
* Filtrering efter partnerdriven (välj **ja** i teckenförklaringen uppe till höger) visar intäkter på 1,5 miljarder dollar och 294 miljoner dollar. Jämför det här med 644 miljarder dollar och 166 miljoner dollar för icke-partnerdrivna intäkter.  
* Genomsnittliga intäkter för stora konton är större (8 miljoner) om affärsmöjligheten är partnerdriven jämfört med 6 miljoner för icke-partnerdrivna företag.  
* För partnerdrivna verksamheter är de genomsnittliga intäkterna för stora affärsmöjligheter nästan dubbelt jämfört med medelstora affärsmöjligheter (4 miljoner).  
* Genomsnittlig intäkt för små och medelstora företag är jämförbara för både partnerdrivna och icke-partnerdrivna företag.   

Våra samarbetspartners gör uppenbart ett bättre jobb med att sälja till kunder.  Det kan vara klokt att styra fler affärer via våra partners.

### <a name="page-3-of-our-report-is-titled-region-stage-counts"></a>Sida 3 av vår rapport heter antal regionssteg
Den här sidan visar liknande data men delar upp dem efter region och steg.  
![](media/sample-opportunity-analysis/opportunity5.png)

* Om du filtrerar efter öst (välj **öst** i cirkeldiagrammet) så ser du att affärsmöjligheterna i öst nästan är helt jämt uppdelade mellan partnerdrivna och icke-partnerdrivna.
* Stora affärsmöjligheter är vanligast i den centrala regionen, små affärsmöjligheter är vanligast i region öst och medelstora affärsmöjligheter är vanligast i region väst.

### <a name="page-4-of-our-report-is-titled-upcoming-opportunities"></a>Sida 4 i vår rapport heter kommande affärsmöjligheter
Vi tittar än en gång på liknande faktorer, men den här gången från perspektivet datum/tid.  
![](media/sample-opportunity-analysis/opportunity6.png)

Vår ekonomichef använder den här sidan för att hantera arbetsbelastning. Genom att titta på intäktsmöjligheter efter säljsteg och månad, kan hon planera på lämpligt sätt.

* Genomsnittliga intäkter för steget slutför är högst. Det är av högsta vikt att slutföra de här avtalen.
* Filtrering per månad (genom att välja månadsnamnet i det vänstra utsnittet) visar att januari har en hög andel stora avtal i slutför-steget med beräknade intäkter på 75 miljoner dollar. Å andra sidan hade februari främst medelstora avtal i lösnings- och förslagstegen.
* Generellt sätt, varierar de beräknade intäktssiffrorna baserat på säljsteg, antal affärsmöjligheter och avtalsstorlek. Lägg till filter (med filterfönstret till höger) för de här faktorerna för att upptäcka ytterligare insikter.

Det här är en säker miljö att leka runt i. Du kan alltid välja att inte spara ändringarna. Men om du sparar dem, kan du alltid gå till **Hämta data** för en ny kopia av det här exemplet.

## <a name="next-steps-connect-to-your-data"></a>Nästa steg: anslut till dina data
Vi hoppas att den här rundturen har visat hur Power BI-instrumentpaneler, frågor och svar, samt rapporter kan ge insikter om data för affärsmöjlighetsspårning. Nu är det din tur – anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer om att [komma igång med Power BI](service-get-started.md).

[Hämta exempel](sample-datasets.md)  
