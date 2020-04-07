---
title: 'Exempel på anskaffningsanalys: Ta en rundtur'
description: 'Exempel på anskaffningsanalys för Power BI: Ta en rundtur'
author: maggiesMSFT
ms.reviewer: amac
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/02/2019
ms.author: maggies
LocalizationGroup: Samples
ms.openlocfilehash: 8ee77485da03cb8e507d30d511c08aa869c3e4ba
ms.sourcegitcommit: 444f7fe5068841ede2a366d60c79dcc9420772d4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80404672"
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Exempel på anskaffningsanalys för Power BI: Ta en rundtur

Exempelinnehållspaketet anskaffningsanalys innehåller en instrumentpanel, rapport och datauppsättning som analyserar ett tillverkningsföretags leverantörsutgifter efter kategori och plats. I det här exemplet utforskar vi dessa områden:

* Vilka de viktigaste leverantörerna är
* Vilka kategorier kostar oss mest pengar
* Vilka leverantörer som ger oss de högsta rabatterna och när

![Instrumentpanel för exemplet anskaffningsanalys](media/sample-procurement/procurement1.png)

Det här exemplet ingår i en serie som visar hur du kan använda Power BI med verksamhetsorienterade data, rapporter och instrumentpaneler. Det skapades av [obviEnce](http://www.obvience.com/) med verkliga data, som har anonymiserats. Dessa data är tillgängliga i flera format: innehållsförpackning, .pbix-fil för Power BI Desktop eller Excel-arbetsbok. Se [Exempel för Power BI](sample-datasets.md). 

De här självstudierna använder Power BI-tjänsten och utforskar innehållspaketet med anskaffningsanalysexemplet. Eftersom rapportupplevelserna är så lika i Power BI Desktop och tjänsten kan du även följa med via .pbix-exempelfilen i Power BI Desktop. 

Du behöver inte en licens för Power BI för att utforska exempel i Power BI Desktop. Om du inte har en Power BI Pro-licens kan du spara exemplet på Min arbetsyta i Power BI-tjänsten. 

## <a name="get-the-sample"></a>Hämta exemplet

Innan du kan använda exemplet, måste du först hämta det som ett [innehållspaket](#get-the-content-pack-for-this-sample), en [.pbix-fil](#get-the-pbix-file-for-this-sample) eller en [Excel-arbetsbok](#get-the-excel-workbook-for-this-sample).

### <a name="get-the-content-pack-for-this-sample"></a>Hämta innehållspaketet för det här exemplet

1. Öppna Power BI-tjänsten (app.powerbi.com), logga in och öppna den arbetsyta där du vill spara exemplet. 

    Om du inte har en Power BI Pro-licens kan du spara exemplet på Min arbetsyta.

2. Längst ned i vänster hörn väljer du **Hämta data**.

    ![Välja Hämta data](media/sample-datasets/power-bi-get-data.png)
3. På sidan **Hämta data** väljer du **Exempel**.

4. Välj **Exempel på anskaffningsanalys** och sedan **Anslut**.  
  
   ![Ansluta till exempel](media/sample-procurement/procurement1a.png)
   
5. Power BI importerar innehållspaketet och lägger sedan till en ny instrumentpanel, rapport och datamängd till din aktuella arbetsyta.
   
   ![Post i exempel på anskaffningsanalys](media/sample-procurement/procurement-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>Hämta .pbix-filen för det här exemplet

Du kan även ladda ned Exempel på anskaffningsanalys som en [.pbix-fil](https://download.microsoft.com/download/D/5/3/D5390069-F723-413B-8D27-5888500516EB/Procurement%20Analysis%20Sample%20PBIX.pbix) som är avsedd för användning med Power BI Desktop. 

### <a name="get-the-excel-workbook-for-this-sample"></a>Hämta Excel-arbetsboken för det här exemplet

Om du vill visa i datakällan för det här exemplet är det även tillgängligt som en [Excel-arbetsbok](https://go.microsoft.com/fwlink/?LinkId=529784). Arbetsboken innehåller Power View-blad som du kan visa och ändra. Om du vill se rådata aktiverar du dataanalystilläggen och väljer **Power Pivot > Hantera**. Aktivering av tilläggen för Power View och Power Pivot beskrivs i avsnittet om att [Titta på Excel-exemplen inuti Excel](sample-datasets.md#explore-excel-samples-inside-excel).


## <a name="spending-trends"></a>Utgiftstrender
Börja med att söka trender i utgifter efter kategori och plats.  

1. I arbetsytan där du sparade exemplet öppnar du fliken **Instrumentpaneler**. Hitta sedan instrumentpanelen **Anskaffningsanalys** och välj den. 
2. Välj panelen på instrumentpanelen **Totalfaktura efter land/Region**, vilket öppnar sidan **Utgiftsöversikt** för rapporten **Anskaffningsanalys**.

    ![Utgiftsöversiktsida](media/sample-procurement/procurement2.png)

Observera följande information:

* I linjediagrammet **Summa faktura per månad och kategori** har kategorin **Direkt** ganska konsekventa utgifter, **Logistik** har en topp i december och  **Övrigt** har en topp i februari.
* På kartan **Summa faktura efter land/Region** är de flesta av våra utgifter i USA.
* I stapeldiagrammet **Summa faktura efter underkategori** är **maskinvara** och **indirekta varor och tjänster** de största utgiftskategorierna.
* I det liggande diagrammet **Total faktura enligt nivå** bedrivs merparten av vår verksamhet med våra leverantörer på nivå 1 (topp 10). På så sätt kan vi hantera bättre leverantörsrelationer.

## <a name="spending-in-mexico"></a>Utgifter i Mexiko
Låt oss se på utgiftsområden i Mexiko.

1. I kartan **Totalfaktura efter land/region** väljer du bubblan **Mexiko**. I stapeldiagrammet **Summa faktura efter underkategori** är merparten av utgifterna i underkategorin **Indirekta varor och tjänster**.

   ![Välj Mexiko på sidan utgiftsöversikt](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Öka detaljnivån i kolumnen **Indirekta varor och tjänster**:

   * I diagrammet **Totalfaktura efter underkategori** markerar du nedåtpilen ![Nedåtpil](media/sample-procurement/pbi_drilldown_icon.png) i det övre högra hörnet i diagrammet.
   * Välj kolumnen **Indirekta varor och tjänster**:

      Som du ser är den högsta utgiften överlägset i underkategorin **Försäljning och marknadsföring**.
   * Välj **Mexiko** på kartan igen.

      För Mexiko ligger den största utgiften i **Underhåll och reparation**.

      ![Detaljnivå för Indirekta varor och tjänster för Mexiko](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Välj uppåtpilen i det övre vänstra hörnet i diagrammet för att öka detaljnivån.
4. Markera pilen för detaljnivå igen för att inaktivera funktionen.  
5. Välj **Exempel på anskaffningsanalys** i det övre navigeringsfönstret för att återgå till instrumentpanelen.

## <a name="evaluate-different-cities"></a>Utvärdera olika städer
Vi kan använda markering för att utvärdera olika städer.

1. Välj panelen på instrumentpanelen **Totalfaktura, rabatt i % per månad**, vilket öppnar sidan **Rabattanalys** för rapporten **Anskaffningsanalys**.
2. Välj olika städer på trädkartan **Total faktura efter ort** för att visa en jämförelse. Observera att nästan alla Miamis fakturor är från nivå 1-leverantörer.

   ![Ort jämfört med rabatt % per nivå](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Leverantörsrabatter
Vi kan också utforska leverantörernas rabatter och de tidsperioder då vi får flest rabatter:
* Skiljer sig rabatterna per månad eller förblir de desamma?
* Får vissa städer fler rabatter än andra?

![Sidan rabattanalys](media/sample-procurement/procurement4.png)

### <a name="discount-by-month"></a>Rabatt per månad
Om vi tittar på kombinationsdiagrammet **Total faktura och rabatt % per månad**ser vi att februari är den vanligaste månaden och september har minst aktivitet. 

Titta på rabatten i procent under dessa månader. När volymen ökar minskar rabatten och när volymen är låg ökar rabatten. Ju mer vi behöver rabatten desto sämre erbjudanden får vi.

![Diagrammet Total faktura och rabatt % per månad](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Rabatt per stad
Ett annat område att utforska är rabatt efter ort. Markera varje stad i tur och ordning på trädkartan och hur andra diagram ändras:

* St. Louis såg en stor topp i antalet fakturor i februari och ett stort fall i rabattbesparingar i april.
* Mexiko City har den största rabatten (11,05 %) och Atlanta har den minsta (0,08 %).

![Rabattdiagram för Mexico City](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Redigera rapporten
Välj **Redigera rapporten** i det övre vänstra hörnet och utforska i redigeringsvyn:

* Se hur sidorna skapas.
* Lägg till sidor och diagram baserat på samma data.
* Ändra typen av visualisering för ett diagram. Till exempel genom att ändra ett träddiagram till en toroid.
* Fäst dem på din instrumentpanel.

## <a name="next-steps-connect-to-your-data"></a>Nästa steg: Anslut till dina data
Den här miljön är säker att leka i eftersom du kan välja att inte spara dina ändringar. Men om du sparar dem kan du alltid välja **Hämta data** för att få en ny kopia av exemplet.

Vi hoppas att denna rundtur har visat hur Power BI-instrumentpaneler, frågor och svar, samt rapporter kan ge insikter om exempeldata. Nu är det din tur – anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer i [Kom igång med Power BI-tjänsten](service-get-started.md).

