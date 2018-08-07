---
title: 'Exempel på leverantörskvalitetsanalys för Power BI: Ta en rundtur'
description: 'Exempel på leverantörskvalitetsanalys för Power BI: Ta en rundtur'
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 08/06/2018
ms.author: mihart
LocalizationGroup: Samples
ms.openlocfilehash: 3d89b34199decf6b27bda49bfac085688dd2e14b
ms.sourcegitcommit: d936a23f895ee6ef1420753342f5e6c055ea5e07
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582692"
---
# <a name="supplier-quality-analysis-sample-for-power-bi-take-a-tour"></a>Exempel på leverantörskvalitetsanalys för Power BI: Ta en rundtur

## <a name="a-brief-overview-of-the-supplier-quality-analysis-sample"></a>En snabb översikt över Exempel på leverantörskvalitetsanalys
Det här exemplet på en instrumentpanel och underliggande rapport från branschen fokuserar på en av de mest typiska utmaningarna i leveranskedjan – analys av leverantörskvalitet.
Två primära mått används i den här analysen: det totala antalet defekter och den totala stilleståndstid som dessa defekter har orsakat. Det här exemplet har två huvudsakliga mål:

* Förstå vilka leverantörer som är bäst och sämst med avseende på kvalitet
* Identifiera vilka anläggningar som gör ett bättre jobb när det gäller att hitta och avvisa defekter, för att minimera stilleståndstiden

![](media/sample-supplier-quality/supplier1.png)

Det här exemplet ingår i en serie som illustrerar hur du kan använda Power BI med verksamhetsorienterade data, rapporter och instrumentpaneler.
Det här är verkliga data från obviEnce ([www.obvience.com](http://www.obvience.com/)) som har anonymiserats.

## <a name="prerequisites"></a>Förutsättningar

 Innan du kan använda exemplet, måste du först hämta det som ett [innehållspaket](https://docs.microsoft.com/power-bi/sample-supplier-quality#get-the-content-pack-for-this-sample), en [.pbix-fil](http://download.microsoft.com/download/8/C/6/8C661638-C102-4C04-992E-9EA56A5D319B/Supplier-Quality-Analysis-Sample-PBIX.pbix) eller en [Excel-arbetsbok](http://go.microsoft.com/fwlink/?LinkId=529779).

### <a name="get-the-content-pack-for-this-sample"></a>Hämta innehållspaketet för det här exemplet

1. Öppna Power BI-tjänsten (app.powerbi.com) och logga in.
2. Längst ned i vänster hörn väljer du **Hämta data**.
   
    ![](media/sample-datasets/power-bi-get-data.png)
3. På sidan Hämta data väljer du ikonen **Exempel**.
   
   ![](media/sample-datasets/power-bi-samples-icon.png)
4. Välj **Exempel på leverantörskvalitetsanalys** och sedan **Anslut**.  
  
   ![Exempel på leverantörskvalitetsanalys](media/sample-supplier-quality/supplier16.png)
   
5. Power BI importerar innehållspaketet och lägger till en ny instrumentpanel, rapport och datauppsättning till din aktuella arbetsyta. Det nya innehållet markeras med en gul asterisk. 
   
   ![Asterisk](media/sample-supplier-quality/supplier17.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Hämta .pbix-filen för det här exemplet

Du kan även hämta exemplet som en .pbix-fil som är avsedd för användning med Power BI Desktop. 

 * [PBIX-filen Exempel på leverantörskvalitetsanalys](http://download.microsoft.com/download/8/C/6/8C661638-C102-4C04-992E-9EA56A5D319B/Supplier-Quality-Analysis-Sample-PBIX.pbix)

### <a name="get-the-excel-workbook-for-this-sample"></a>Hämta Excel-arbetsboken för det här exemplet
Du kan också [hämta enbart datauppsättningen (Excel-arbetsboken) för det här exemplet](http://go.microsoft.com/fwlink/?LinkId=529779). Arbetsboken innehåller Power View-blad som du kan visa och ändra. För att se rådata väljer du **Power Pivot > Hantera**.


## <a name="downtime-caused-by-defective-materials"></a>Stilleståndstid som orsakas av defekta material
Nu ska vi analysera den stilleståndstid som orsakas av defekta material och se vilka leverantörer som är ansvariga.  

1. På instrumentpanelen väljer du sifferpanelen **Total Defect Quantity (Totalt antal defekta)** eller **Total Downtime Minutes (Total stilleståndstid i minuter)**.  

   ![](media/sample-supplier-quality/supplier2.png)  

   Rapporten ”Exempel på leverantörskvalitetsanalys” öppnas på sidan ”Downtime Analysis” (Stilleståndstidsanalys). Observera att vi totalt har 33 000 000 antal defekta delar och att den totala stilleståndstiden som orsakats av dessa defekta delar är 77 000 minuter. Vissa material har färre defekta delar men kan orsaka stor fördröjning som resulterar i längre stilleståndstid. Vi ska undersöka dem på rapportsidan.  
2. Om vi tittar på raden **Total Downtime Minutes (Total stilleståndstid i minuter)** i kombinationsdiagrammet **Defects and Downtime (min) by Material Type (Defekter och stilleståndstid (min) per materialtyp)**, ser vi att korrugerade material orsakar längst stilleståndstid.  
3. Välj kolumnen **Corrugate (Korrugerad)** i samma kombinationsdiagram för att se vilka anläggningar som påverkas mest av den här defekten och vilken leverantör som är ansvarig.  

   ![](media/sample-supplier-quality/supplier3.png)  
4. Välj enskilda anläggningar på kartan för att se vilken leverantör eller vilket material som ansvarar för stilleståndstiden på anläggningen.

### <a name="which-are-the-worst-suppliers"></a>Vilka är de sämsta leverantörerna?
 Vi vill hitta de åtta sämsta leverantörerna och fastställa hur stor procentandel av stilleståndstiden som de står för. Vi kan göra detta genom att ändra ytdiagrammet **Downtime (min) by Vendor (Stilleståndstid (min) per leverantör)** till en trädkarta.  

1. På sidan 3 i rapporten, ”Downtime Analysis (Stilleståndstidsanalys)”, väljer du **Redigera rapport** i det övre vänstra hörnet.  
2. Välj ytdiagrammet **Downtime (min) by Vendor (Stilleståndstid (min) per leverantör)** och sedan Trädkarta i fönstret Visualiseringar.  

   ![](media/sample-supplier-quality/supplier4.png)  

    Trädkartan ställer automatiskt in fältet **Leverantör** som **Grupp**.  

    ![](media/sample-supplier-quality/supplier5.png)  

   I den här trädkartan kan vi se att de åtta främsta leverantörerna är de åtta blocken till vänster i trädkartan. Vi kan också se att de svarar för 50 % av all stilleståndstid i minuter.  
3. Välj **Exempel på leverantörskvalitetsanalys** i det övre navigeringsfältet för att gå tillbaka till instrumentpanelen.

### <a name="comparing-plants"></a>Jämföra anläggningar
Nu ska vi titta närmare på vilken anläggning som är bäst på att hantera defekta material, vilket resulterar i kortare stilleståndstid.  

1. Välj kartrutan **Total Defect Reports by Plant (Totalt antal rapporterade defekter per anläggning), Defect Type (Defekttyp)**.  

    Rapporten öppnas på sidan för ”leverantörskvalitet”.  

   ![](media/sample-supplier-quality/supplier6.png)  
2. Välj cirkeln **Påverkan** i kartans förklaring.  

    ![](media/sample-supplier-quality/supplier7.png)  

    Notera i bubbeldiagrammet att **Logistik** är den kategori som har flest problem – den är störst vad gäller totalt antal defekter, totalt antal defektrapporter och total stilleståndstid i minuter. Låt oss utforska den här kategorin mer.  
3. Välj Logistik-bubblan i bubbeldiagrammet och titta på anläggningarna i Springfield i Illinois och i Naperville i Illinois. Naperville verkar göra ett mycket bättre arbete med att hantera defekta material eftersom de har ett stort antal avvisade artiklar och låg påverkan, jämfört med Springfields höga siffra för påverkan.  

   ![](media/sample-supplier-quality/supplier8.png)  
4. Välj **Exempel på leverantörskvalitetsanalys** i det övre navigeringsfältet att återgå till din aktiva arbetsyta.

## <a name="which-material-type-is-best-managed"></a>Vilken materialtyp hanteras bäst?
Den bäst hanterade materialtypen är den med lägst stilleståndstid eller utan påverkan, oavsett antalet defekter.

* I instrumentpanelen tittar vi närmare på panelen **Total Defect Quantity by Material Type (Totalt antal defekta per materialtyp), Defect Type (Defekttyp)**.

  ![](media/sample-supplier-quality/supplier9.png)

Observera att **Råmaterial** har ett stort antal totala defekter, men att de flesta av dessa antingen avvisas eller saknar påverkan.

Vi ska kontrollera att råmaterial inte orsakar långa stilleståndstider, trots högt antal defekter.

* I instrumentpanelen tittar vi närmare på panelen **Total Defect Qty (Totalt antal defekta), Total Downtime Minutes by Material Type (Total stilleståndstid i minuter per materialtyp)**.

  ![](media/sample-supplier-quality/supplier10.png)

Uppenbarligen hanteras råmaterial bra: de har fler defekter, men total lägre stilleståndstid i minuter.

### <a name="compare-defects-to-downtime-by-year"></a>Jämföra defekter med stilleståndstid per år
1. Välj kartrutan **Total Defect Reports by Plant (Totalt antal rapporterade defekter per anläggning), Defect Type (Defekttyp)** för att öppna rapporten på den första rapportsidan, om leverantörskvalitet.
2. Observera att **Defect Qty (Defekt antal)** är högre 2014 än 2013.  

    ![](media/sample-supplier-quality/supplier11.png)  
3. Innebär fler defekter längre stilleståndstid? Vi kan ställa frågor i Frågor och svar-rutan för att ta reda på det.  
4. Välj **Exempel på leverantörskvalitetsanalys** i det övre navigeringsfältet för att gå tillbaka till instrumentpanelen.  
5. Eftersom vi vet att råmaterial har det högsta antalet defekter, skriver vi ”visa materialtyper, år och totalt antal defekta” i frågerutan.  

    Det förekom många fler råmaterialsdefekter under 2014 än under 2013.  

    ![](media/sample-supplier-quality/supplier12.png)  
6. Ändra nu frågan till ”visa materialtyper, år och total stilleståndstid i minuter”.  

   ![](media/sample-supplier-quality/supplier13.png)

Stilleståndstiden för råmaterial låg på ungefär samma nivå 2013 och 2014, trots att det förekom många fler råmaterialdefekter 2014.

Det visar sig att de fler råmaterialdefekterna under 2014 inte resulterade i särskilt mycket mer stilleståndstid till följd av råmaterial under samma år.

### <a name="compare-defects-to-downtime-month-to-month"></a>Jämför defekterna med stilleståndstiden månad för månad
Nu ska vi titta på en annan instrumentpanels panel som rör det totala antalet defekta material.  

1. Välj bakåtpilen ![](media/sample-supplier-quality/backarrow.png) i det övre vänstra hörnet ovanför frågerutan för att komma tillbaka till instrumentpanelen.  

    Om vi tittar närmare på panelen för **totala antalet defekta material per månad och år**, ser vi att den första halvan av 2014 hade ett motsvarande antal defekter som 2013, men under andra halvan av 2014 steg antalet defekter avsevärt.  

    ![](media/sample-supplier-quality/supplier14.png)  

    Låt oss se om det ökade antalet defekter ledde till en lika stor ökad stilleståndstid i minuter.  
2. Skriv ”total stilleståndstid i minuter per månad och år som ett linjediagram” i frågerutan.  

   ![](media/sample-supplier-quality/supplier15.png)

   Vi kan se en tydlig ökning av stilleståndstiden i minuter under juni och oktober men utöver det resulterade inte det större antalet defekter i någon väsentlig ökning av stilleståndstiden. Detta visar att vi hanterar defekter bra.  
3. Om du vill fästa diagrammet på din instrumentpanel, väljer du fästikonen ![](media/sample-supplier-quality/pin.png) till höger om frågerutan.  
4. Om du vill utforska de avvikande månaderna, kontrollerar du stilleståndstiden i minuter under oktober per materialtyp, kategori och så vidare genom att ställa frågor som ”total stilleståndstid i minuter i oktober per anläggning”.    
5. Välj bakåtpilen ![](media/sample-supplier-quality/backarrow.png) i det övre vänstra hörnet ovanför frågerutan för att komma tillbaka till instrumentpanelen.

Det här är en säker miljö att leka runt i. Du kan alltid välja att inte spara ändringarna. Men om du sparar dem, kan du alltid gå till **Hämta data** för en ny kopia av det här exemplet.

## <a name="next-steps-connect-to-your-data"></a>Nästa steg: anslut till dina data
Vi hoppas att denna rundtur har visat hur Power BI-instrumentpaneler, Frågor och svar, samt rapporter kan ge insikter om leverantörskvalitetsdata. Nu är det din tur – anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer om att [komma igång med Power BI](service-get-started.md).
