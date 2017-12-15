---
title: "Aggregeringar (summa, medelvärde, maximum etc.) i Power BI"
description: "Ändra aggregeringen i ett diagram (summa, medelvärde, maximum etc.) i Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: modifying
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/23/2017
ms.author: mihart
ms.openlocfilehash: c1b926e129e8d82edd9c329a51623908c4e7c9e0
ms.sourcegitcommit: 8f72ce6b35aa25979090a05e3827d4937dce6a0d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2017
---
# <a name="aggregates-in-power-bi"></a>Aggregeringar i Power BI
## <a name="what-is-an-aggregate"></a>Vad är en aggregering för något?
Ibland kan du vilja kombinera värden matematiskt för rader i en kolumn. Den matematiska åtgärden kan vara summa, medelvärde, maximum, antal osv. Att kombinera datavärdet i rader i en kolumn kallas aggregering. Resultatet av den matematiska åtgärden blir en *aggregering*. 

Ett numeriskt fält är ett värde som ska aggregeras (exempelvis summa eller medelvärde) över vissa kategoriska fält.  Till exempel ”försäljningsbelopp per produkt” och ”antal fel per region”. Numeriska fält kallas ofta **mått**. I listan Fält visas måtten med ∑-symbolen. Mer information finns i [Rapportredigeraren... ta en rundtur](service-the-report-editor-take-a-tour.md).

Ibland är ett *mått* egentligen ett *beräknat mått*. Beräknade mått i Power BI importeras med datan (som definieras i datamodellen som rapporten baseras på). Varje beräknat mått har en egen hårdkodad formel. Du kan inte ändra aggregeringen som används, till exempel om den är en summa kan den bara vara en summa. I listan Fält anges *beräknade mått* med kalkylatorsymbolen. Mer information om hur beräknade mått skapas finns i [Mått i Power BI Desktop](desktop-measures.md).

Kategoriska fält är inte numeriska, men de kan ändå aggregeras.  När kategoriska fält placeras i en bucket som är *endast numerisk*, exempelvis **Värden** eller **Knappbeskrivningar**, kan Power BI räkna antalet förekomster i varje kategori eller antal distinkta förekomster i varje kategori.  För strängar och datum har Power BI några fler alternativ för aggregeringen: tidigaste, senaste, första och sista.  

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Varför fungerar inte aggregeringen som jag vill?
Att arbeta med aggregeringar i Power BI-tjänsten kan vara förvirrande. Du kanske har ett numeriskt fält och Power BI låter dig inte ändra aggregeringen. Eller så har du t.ex. ett fält med år som du inte vill aggregera, du vill bara räkna antalet förekomster.

Orsaken till problemet är oftast hur fältet har kategoriserats i Power BI-datauppsättningen. Kanske har fältet kategoriserats som text, vilket förklarar varför det inte går att summera eller räkna ut ett medelvärde för. Tyvärr [kan endast datauppsättningens ägare ändra hur ett fält kategoriseras](desktop-measures.md).  

För att hjälpa dig har vi ett särskilt avsnitt i slutet av den här artikeln som kallas **Tips och felsökning**.  Om du inte hittar svaret där kan du ställa din fråga i [Power BI Community-forumet](http://community.powerbi.com) och få ett snabbt svar direkt från Power BI-teamet.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Ändra hur ett numeriskt fält aggregeras
Vi antar att du har ett diagram som summerar försäljningsdata för olika regioner, men att du hellre vill se medelvärdet. 

1. Lägg till måttet i en visualisering i rapportens redigeringsvy.
2. Sök efter fältet i visualiseringsfönstret, högerklicka och välj den aggregeringstyp som passar. Om du inte ser den aggregering du söker kontaktar du datauppsättningens ägare. Det kan bero på hur fältet har kategoriserats av ägaren.  
   
   ![](media/service-aggregates/aggregate_new.png)
   
   > [!NOTE]
   > Alternativen i listrutan varierar beroende på 1) vilket fält som valts och 2) hur fältet har kategoriserats av datauppsättningens ägare.
   > 
   > 

Här visas några av de alternativ som kan vara tillgängliga vid aggregering av ett fält:

* **Summera inte**. När det här alternativet är valt behandlas varje värde i fältet separat och summeras därför inte. Det här används ofta om du har en kolumn med numeriska ID:n som inte ska summeras.
* **Summera**. Detta alternativ adderar alla värden i fältet.
* **Medelvärde**. Räknar ut ett aritmetiskt medelvärde för värdena.
* **Minimum**. Visar det minsta värdet.
* **Maximum**. Visar det högsta värdet.
* **Antal (ej tomma).** Detta räknar ut antalet värden i ett fält som inte är tomt.
* **Antal (distinkta).** Detta är antalet olika värden i fältet.
* **Standardavvikelse.**
* **Avvikelse**.
* **Median**.  Visar medianvärdet (mitten). Detta är det värde som har samma antal objekt över och under sig.  Om det finns två medianer räknar Power BI ut ett medelvärde.

Till exempel följande data:

| Land | Belopp |
|:--- |:--- |
| USA |100 |
| Storbritannien |150 |
| Kanada |100 |
| Tyskland |125 |
| Frankrike | |
| Japan |125 |
| Australien |150 |

Ger följande resultat:

* **Summera inte**: Varje värde visas separat
* **Summera**: 750
* **Medelvärde**: 125
* **Maximum**:  150
* **Minimum**: 100
* **Antal (ej tomma):** 6
* **Antal (distinkta):** 4
* **Standardavvikelse:** 20,4124145...
* **Avvikelse:** 416,666...
* **Median:** 125

## <a name="use-a-non-aggregated-field-as-a-numeric-field"></a>Att använda ett icke-aggregerat fält som ett numeriskt fält
Du kan också använda ett icke-aggregerat fält som ett numeriskt fält. Om du exempelvis har fältet Produktnamn kan du lägga till det som ett värde och ange det som **Antal** eller **Distinkt antal**. 

1. Vi antar att du väljer **Butik > Kedja**.
   
   ![](media/service-aggregates/count-of-chain-do_not_summarize.png)
2. Om du då ändrar aggregeringen från standardvärdet **Summera inte** till **Antal (distinkta)**, räknar Power BI antalet olika kedjor. I det här fallet finns det två: Fashions Direct och Lindseys.
   
   ![](media/service-aggregates/aggregates_count.png)
3. Om du i stället ändrar aggregeringen till **Antal**, räknar Power BI det totala antalet. Det finns i det här fallet 104 poster för **Kedja**. Om du lägger till **Kedja** som ett filter kan du se att det finns 37 rader för Fashions Direct och 67 rader för Lindseys.  
   
   ![](media/service-aggregates/count_of_chain_104.png)

## <a name="tips-and-troubleshooting"></a>Tips och felsökning
F:    Varför har jag inte alternativet **Summera inte**?

S:    Fältet du har valt är troligen ett beräknat mått. Kom ihåg att varje beräknat mått har sin egen hårdkodade formel. Det går inte att ändra beräkningen.

F:    Mitt fält **är** numeriskt, varför är mina enda alternativ **Antal** och **Distinkt antal**?

S:    Sannolikt är förklaringen att datauppsättningens ägare, oavsiktligt eller avsiktligt *inte* har klassificerat fältet som ett tal. Om en datauppsättning till exempel har fältet **år**, kan datauppsättningens ägare kategorisera det som text eftersom det är troligare att fältet **år** ska räknas (t.ex. antal människor som föddes 1974) i stället för att summeras eller visa ett medelvärde. Om du är ägare kan du öppna datauppsättningen i Power BI Desktop och använda fliken **Modellering** till att ändra datatypen.  

S:    En annan möjlighet är att du har släppt fältet i en *bucket* som endast tillåter kategoriska värden.  I så fall är dina enda alternativ antal och distinkt antal.

S:    Ett tredje alternativ är att du använder fältet som en axel. I ett stapeldiagrams axel visar till exempel Power BI en stapel för varje distinkt värde – den aggregerar inte fältvärdena alls. 

>[!NOTE]
>Undantaget till denna regel är punktdiagram som *kräver* aggregerade värden för X- och Y-axlarna.


F:    Jag har ett punktdiagram och jag vill *inte* att mitt fält ska aggregeras.  Hur gör jag?

S:    Lägg till fältet i **Information** i stället för X- eller Y-axelns bucket.

F:    När jag lägger till ett numeriskt fält i en visualisering summeras de flesta som standard, men vissa har medelvärde, antal eller någon annan typ av aggregering som standard.  Varför är inte standardaggregeringen alltid likadan?

S:    Datauppsättningens ägare har möjlighet att ange en standardsummering för varje fält. Om du är ägare till en datauppsättning kan du ändra standardsummeringen på fliken **Modellering** i Power BI Desktop.

F:    Mitt fält **är** numeriskt, varför har jag inte några aggregeringsalternativ i listrutan?

S:    Om fältet har en kalkylatorikon innebär det att det är ett *beräknat mått*. Varje beräknat mått har sin egen hårdkodade formel som inte kan ändras i Power BI-tjänsten. Beräkningen som används kan vara en enkel aggregering, som t.ex. ett medelvärde eller en summa, men det kan också vara något mer komplicerat som en ”procent av bidraget till överordnad kategori” eller ”totalt antal som körs sedan årets start”. Power BI kommer inte summera eller räkna ut ett medelvärde som resultat, utan kommer i stället bara göra en ny beräkning (med den hårdkodade formeln) för varje datapunkt.

F:    Jag är ägare till en datauppsättning och vill se till att ett fält aldrig aggregeras.

S:    I Power BI Desktop på fliken **Modellering** anger du **Datatyp** som **Text**.

F:    Jag kan inte se **Summera inte** som ett alternativ i min listruta.

S:    Försök att ta bort fältet och sedan lägga till det igen.

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

