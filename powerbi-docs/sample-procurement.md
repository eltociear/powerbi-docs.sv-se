---
title: "Exempel på anskaffningsanalys: Ta en rundtur"
description: "Exempel på anskaffningsanalys för Power BI: Ta en rundtur"
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
ms.date: 12/04/2017
ms.author: mihart
ms.openlocfilehash: 957e7c05907f1fc75eddeb271c664f898203e591
ms.sourcegitcommit: 7248b5e449b2495d6baef385470d18edfacec457
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/08/2017
---
# <a name="procurement-analysis-sample-for-power-bi-take-a-tour"></a>Exempel på anskaffningsanalys för Power BI: Ta en rundtur
Detta exempel på en instrumentpanel och dess underliggande rapport analyserar ett tillverkningsföretags leverantörsutgifter efter kategori och plats. I det här exemplet utforskar vi dessa områden:

* Vilka de viktigaste leverantörerna är
* Vilka kategorier vi lägger ut mest pengar på
* Vilka leverantörer som ger oss de högsta rabatterna och när

Det här exemplet ingår i en serie som illustrerar hur du kan använda Power BI med affärsorienterade data, rapporter och instrumentpaneler. Det här är verkliga data från obviEnce ([www.obvience.com](http://www.obvience.com/)) som har anonymiserats.

![](media/sample-procurement/procurement1.png)

Vill du följa med? I [Power BI-tjänsten](https://powerbi.com), gå till **Hämta data > Exempel > Anskaffningsanalysexempel > Anslut** för att hämta din egna kopia av smakprovet.

[!Note] Du kan också [hämta enbart datauppsättningen (Excel-arbetsboken) för det här exemplet](http://go.microsoft.com/fwlink/?LinkId=529784). Arbetsboken innehåller Power View-blad som du kan visa och ändra. För att se rådata väljer du **Power Pivot > Hantera**.

## <a name="spending-trends"></a>Utgiftstrender
Börja med att söka trender i utgifter efter kategori och plats.  

1. Från arbetsytan, öppna fliken **Instrumentpaneler** och välj instrumentpanelen Anskaffningsanalys.
2. Välj fönstret **Totalfaktura efter land/region** i instrumentpanelen. Det öppnar sidan ”Utgiftsöversikt” i exempelrapporten ”Anskaffningsanalys”.
   
    ![](media/sample-procurement/procurement2.png)

Lägg märke till några saker:

* I linjediagrammet **Summa faktura per månad och kategori**: kategorin **Direkt** kategorin har ganska konsekventa utgifter **Logistik** har en topp i december och  **Övrigt** har en topp i februari.
* På kartan **Summa faktura efter land/Region**: de flesta av våra utgifter är i USA.
* I stapeldiagrammet **Summa faktura efter underkategori** : **maskinvara** och **indirekta varor och tjänster** är de största utgiftskategorierna.
* I det liggande diagrammet Total faktura enligt nivå: Merparten av vår verksamhet bedrivs med våra leverantörer på nivå 1 (topp 10). Detta hjälper oss att bättre hantera våra leverantörsrelationer.

## <a name="spending-in-mexico"></a>Utgifter i Mexiko
Låt oss se på utgiftsområden i Mexiko.

1. I diagrammet väljer du bubblan **Mexiko** på kartan. I stapeldiagrammet ”Summa faktura efter underkategori” är merparten i underkategorin **Indirekta varor och tjänster**.
   
   ![](media/sample-procurement/pbi_procsample_spendmexico.png)
2. Öka detaljnivån i kolumnen **Indirekta varor och tjänster**:
   
   * Välj nedåtpilen ![](media/sample-procurement/pbi_drilldown_icon.png) i det övre högra hörnet i diagrammet.
   * Välj kolumnen **Indirekta varor och tjänster**:
     
      De största utgifterna i den här kategorin är försäljning och marknadsföring.
   * Välj **Mexiko** på kartan igen.
     
      Den största utgiften i den här kategorin i Mexiko är underhåll och reparationer.
     
      ![](media/sample-procurement/pbi_procsample_drill_mexico.png)
3. Välj uppåtpilen i det övre vänstra hörnet i diagrammet för att öka detaljnivån.
4. Markera pilen igen för att inaktivera funktionen.  
5. Välj **Power BI** i det övre navigeringsfältet att återgå till din arbetsyta.

## <a name="evaluate-different-cities"></a>Utvärdera olika städer
Vi kan använda markering för att utvärdera olika städer.

1. Välj rutan **Totalfaktura, rabatt % enligt månad** i instrumentpanelen. Rapporten öppnar sidan ”rabattanalys”.
2. Välj olika städer på trädkartan **Total faktura efter stad** för att jämföra. Nästan alla Miamis fakturor är från nivå 1-leverantörer.
   
   ![](media/sample-procurement/pbi_procsample_miamitreemap2.png)

## <a name="vendor-discounts"></a>Leverantörsrabatter
Vi kan också utforska leverantörernas rabatter och de tidsperioder då vi får flest rabatter. 

![](media/sample-procurement/procurement4.png)

Mer specifikt, följande frågor:

* Skiljer sig rabatterna per månad eller är de samma varje månad?
* Får vissa städer fler rabatter än andra?

### <a name="discount-by-month"></a>Rabatt per månad
Om vi tittar på kombinationsdiagrammet **Total faktura och rabatt % per månad** ser vi att **februari** är den vanligaste månaden och **september** har minst aktivitet. Nu vill titta på rabatten i procent under dessa månader.
Observera att rabatten minskar när volymen går upp och att den ökar när volymen går ner. Ju mer behöver vi rabatten desto sämre erbjudanden får vi.

![](media/sample-procurement/procurement5.png)

### <a name="discount-by-city"></a>Rabatt per stad
Ett annat område att utforska är rabatt efter ort. Markera varje stad på trädkartan och hur andra diagram ändras. 

* St. Louis såg en stor topp i antalet fakturor i februari och ett stort fall i rabattbesparingar i april.
* Mexiko City har den största rabatten (11,05%) och Stockholm har den minsta (0.08%).

![](media/sample-procurement/procurement6.png)

### <a name="edit-the-report"></a>Redigera rapporten
Välj **Redigera rapporten** i det övre vänstra hörnet och utforska i redigeringsvyn.

* Se hur sidorna skapas
* Lägga till sidor och diagram baserat på samma data
* Ändra typen av visualisering för ett diagram – till exempel ändra ett träddiagram till en toroid
* Fäst dem på din instrumentpanel

Det här är en säker miljö att leka runt i. Du kan alltid välja att inte spara ändringarna. Fast du sparar dem kan du alltid gå till **Hämta data** för en ny kopia av det här exemplet.

## <a name="next-steps-connect-to-your-data"></a>Nästa steg: anslut till dina data
Vi hoppas att denna rundtur har visat hur Power BI-instrumentpaneler, samt rapporter kan ge insikter om upphandlingsdata. Nu är det din tur &#151; anslut till dina egna data. Med Power BI kan du ansluta till en mängd olika datakällor. Läs mer om att [komma igång med Power BI](service-get-started.md).

