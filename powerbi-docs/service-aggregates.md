---
title: Arbeta med aggregeringar (Summa, medelvärde och så vidare) i Power BI-tjänsten
description: Lär dig mer om att ändra aggregeringen i ett diagram (Summa, medelvärde, högsta och så vidare.) i Power BI-tjänsten.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 7cee05df6a7d13e18bc31bc1a1f34a5f89711c0d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710759"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Arbeta med aggregeringar (Summa, medelvärde och så vidare) i Power BI-tjänsten

## <a name="what-is-an-aggregate"></a>Vad är en aggregering för något?

Ibland kan du vilja kombinera värden matematiskt i dina data. Den matematiska åtgärden kan vara summa, medelvärde, Max, antal och så vidare. När du kombinerar värden i dina data kallas *sammanställa*. Resultatet av den matematiska åtgärden blir en *aggregering*.

När Power BI-tjänsten och Power BI Desktop skapar visualiseringar, kan de aggregera dina data. Ofta är det just det aggregatet som du vill ha, men andra gånger kan du vilja aggregera värdena på ett annat sätt.  En summa kontra ett medelvärde till exempel. Det finns flera olika sätt att hantera och ändra den aggregering som Power BI använder i en visualisering.

Först ska vi ta en titt på data *typer* eftersom datatypen avgör hur och om Power BI kan aggregera.

## <a name="types-of-data"></a>Typer av data

De flesta datauppsättningar har mer än en typ av data. På den mest grundläggande nivån data är antingen numeriska eller inte. Powerbi kan användas med numeriska datamängder med hjälp av en summa, medelvärde, antal, minimum, varians och mycket mer. Tjänsten kan även aggregera textdata, ofta kallad *kategoriska* data. Om du försöker aggregera ett kategoriskt fält genom att placera den i en numeriska bucket som **värden** eller **knappbeskrivningar**, Power BI kommer att räkna förekomsterna av varje kategori eller räkna distinkta förekomster av varje kategori. Särskilda typer av data, till exempel datum, har några egna aggregeringsalternativ: tidigaste, senaste, första och sista.

I exemplet nedan:

- **Sålda enheter** och **Tillverkningskostnad** är kolumner som innehåller numeriska data

- **Segment**, **Land**, **Produkt**, **Månad** och **Månadsnamn** innehåller kategoriska data

   ![Skärmbild av en exempeldatauppsättning.](media/service-aggregates/power-bi-aggregate-chart.png)

När du skapar en visualisering i Power BI, kommer tjänsten aggregera numeriska fält (standard är *summan*) över vissa kategoriska fält.  Till exempel ”sålda enheter ***per produkt***” ”, sålda enheter ***per månad***” och ”tillverkningskostnad ***efter Segment***”. Powerbi refererar till vissa numeriska fält som **mått**. Det är enkelt att identifiera mått i Power BI-rapportredigeraren – den **fält** listan visar mått med symbolen ∑ bredvid dem. Se [rapportredigeraren... ta en rundtur](service-the-report-editor-take-a-tour.md) för mer information.

![Skärmbild av Power BI med fältlistan påpekas.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Varför fungerar inte aggregeringen som jag vill?

Arbeta med aggregeringar i Power BI kan service vara förvirrande. Du kanske har ett numeriskt fält och Power BI kan du inte ändra aggregeringen. Eller så har du t.ex. ett fält med år som du inte vill aggregera, du vill bara räkna antalet förekomster.

Det underliggande problemet är vanligtvis fältdefinition i datauppsättningen. Kanske datauppsättningens ägare definieras fältet som text och som förklarar varför Power BI kan inte summera eller genomsnittlig den. Tyvärr [kan endast datauppsättningens ägare ändra hur ett fält kategoriseras](desktop-measures.md). Om du har ägarbehörighet för datauppsättningen, antingen i Desktop eller det program som används för att skapa datauppsättningen (till exempel Excel), kan så du lösa problemet. Annars måste du kontakta datauppsättningens ägare för hjälp.  

Det finns ett särskilt avsnitt i slutet av den här artikeln som kallas [ **överväganden och felsökning**](#considerations-and-troubleshooting). Du får tips och vägledning. Om du inte hittar svaret där kan du publicera din fråga på den [Power BI Community-forum](http://community.powerbi.com). Du får ett snabbt svar direkt från Power BI-teamet.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Ändra hur ett numeriskt fält aggregeras

Anta att du har ett diagram som summerar enheter sålda för olika produkter, men du vill hellre ha medelvärdet.

1. Skapa en **klustrat stapeldiagram** som använder ett mått och en kategori. I det här exemplet använder vi enheter sålda per produkt.  Som standard skapar Power BI ett diagram som summerar sålda enheter (dra måttet i den **värdet** bra) för varje produkt (dra kategori i den **axel** bra).

   ![Skärmbild av diagrammet, fönstret visualiseringar och fältlistan med summan påpekas.](media/service-aggregates/power-bi-aggregate-sum.png)

1. I den **visualiseringar** fönstret högerklickar du på måttet och välj den Aggregeringstyp. I det här fallet väljer vi **genomsnittlig**. Om du inte ser aggregeringen du behöver, se den [ **överväganden och felsökning** ](#considerations-and-troubleshooting) avsnittet.

   ![Skärmbild av en sammanställd lista med medeltal valt och påpekas.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > Alternativen som finns i den nedrullningsbara listan varierar beroende på 1) på fältet som valts och 2) hur datauppsättningens ägare kategoriserade fältet.

1. Din visualiseringen använder nu aggregering efter medelvärde.

   ![Skärmbild av diagrammet nu visar genomsnittlig för enheter sålda per produkt.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Sätt att aggregera dina data

Här visas några av de alternativ som kan vara tillgängliga vid aggregering av ett fält:

- **Summera inte**. Med det här alternativet är valt, Power BI behandlar varje värde i fältet separat och summera inte dem. Använd det här alternativet om du har en numeriska ID-kolumn som tjänsten inte bör sum.

- **Summera**. Adderar alla värden i fältet.

- **Medelvärde**. Räknar ut ett aritmetiskt medelvärde för värdena.

- **Minimum**. Visar det minsta värdet.

- **Maximum**. Visar det högsta värdet.

- **Antal (ej tomma).** Räknar antalet värden i fältet som inte är tom.

- **Antal (distinkta).** Räknar ut antalet olika värden i fältet.

- **Standardavvikelse.**

- **Avvikelse**.

- **Median**.  Visar medianvärdet (mitten). Det här värdet har samma antal objekt över och under.  Om det finns två medianer räknar Power BI ut ett medelvärde.

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

- **Summera inte**: Varje värde visas separat

- **Summa**: 750

- **Medelvärde**: 125

- **Maximum**:  150

- **Minimum**: 100

- **Antal (ej tomma):** 6

- **Antal (distinkta):** 4

- **Standardavvikelse:** 20,4124145 ...

- **Avvikelse:** 416,666 ...

- **Medianvärde:** 125

## <a name="create-an-aggregate-using-a-category-text-field"></a>Skapa en aggregering med hjälp av ett kategorifält (text)

Du kan även aggregera ett icke-numeriskt fält. Om du exempelvis har ett produktnamnsfält, kan du lägga till det som ett värde och ställa in det som **Antal**, **Distinkt antal**, **Första** eller **Sista**.

1. Dra den **produkten** fält till den **värden** bra. Den **värden** brunnen används vanligtvis för numeriska fält. Powerbi identifierar att det här fältet är ett textfält, ställer in aggregeringen till **summera inte**, och ger dig en tabell med en kolumn.

   ![Skärmbild av fältet produkt i värdena som är bra.](media/service-aggregates/power-bi-aggregate-value.png)

1. Om du ändrar aggregeringen från standardvärdet **summera inte** till **antal (distinkta)** , räknar Power BI antalet olika produkter. I det här fallet finns det fyra.
  
   ![Skärmbild av Distinkt antal produkter.](media/service-aggregates/power-bi-aggregate-count.png)

1. Om du i stället ändrar aggregeringen till **Antal**, räknar Power BI det totala antalet. I det här fallet det finns sju transaktioner för **produkten**.

   ![Skärmbild av antal produkter.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Genom att dra samma fältet (i det här fallet **produkten**) till den **värden** brunnen och lämna standardaggregeringen **summera inte**, Power BI eliminerar antal efter produkt.

   ![Skärmbild av produkten och antal produkter.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

F:  Varför har jag inte alternativet **Summera inte**?

S:  Det fält du har valt är troligen ett beräknat mått eller avancerat mått som skapats i Excel eller [Power BI Desktop](desktop-measures.md). Varje beräknat mått har en egen hårdkodad formel. Du kan inte ändra den aggregering som använder Power BI. Om den till exempel är en summa, kan den bara vara en summa. Den **fält** lista visas *beräknade mått* med kalkylatorsymbolen.

F:  Mitt fält **är** numeriskt, varför är mina enda alternativ **Antal** och **Distinkt antal**?

S1:  Sannolikt är förklaringen är att datauppsättningens ägare har *inte* klassificerat fältet som ett tal. Exempel: om en datauppsättning som har en **år** fältet datauppsättningens ägare kategorisera värdet som text. Det är troligare att Power BI räknas den **år** fält (till exempel antal människor som föddes 1974). Det är mindre troligt att Power BI ska summeras eller genomsnittlig den. Om du är ägare, du kan öppna datauppsättningen i Power BI Desktop och använda den **modellering** flik för att ändra datatypen.

S2: Om fältet har en kalkylatorikon, innebär det är en *beräknat mått*. Varje beräknat mått har sin egen hårdkodade formel som endast datauppsättningens ägare kan ändra. Den beräkning som använder Power BI kan vara en enkel aggregering, som ett medelvärde eller en summa. Det kan också vara något mer komplicerat som en ”procent av bidraget till överordnad kategori” eller ”totalt antal som körs sedan årets start”. Powerbi kommer inte att kunna summera eller medelvärde som resultat. I stället det ska bara räkna om (med den hårdkodade formeln) för varje datapunkt.

S3:  En annan möjlighet är att du har släppt fältet i en *bucket* som endast tillåter kategoriska värden.  I så fall är dina enda alternativ antal och distinkt antal.

S4:  Och ett fjärde alternativ är att du använder fältet som en axel. I ett stapeldiagrams axel visar till exempel Power BI en stapel för varje distinkt värde – den aggregerar inte fältvärdena alls.

>[!NOTE]
>Undantaget till denna regel är punktdiagram som *kräver* aggregerade värden för X- och Y-axlarna.

F:  Varför kan jag inte aggregera textfält för SSAS-datakällor (SQL Server Analysis Services)?

S:  Live-anslutningar till flerdimensionella SSAS-modeller tillåter inte några aggregeringar på klientsidan, inklusive första, sista, medelvärde, minimum, maximum och summa.

F:  Jag har ett punktdiagram och jag vill *inte* att mitt fält ska aggregeras.  Hur gör jag?

S:  Lägg till fältet i **Information** i stället för X- eller Y-axelns bucket.

F:  När jag lägger till ett numeriskt fält i en visualisering summeras de flesta som standard, men vissa har medelvärde, antal eller någon annan typ av aggregering som standard.  Varför är inte standardaggregeringen alltid likadan?

S:  Datauppsättningens ägare kan ange en standardsummering för varje fält. Om du är ägare till en datauppsättning kan du ändra standardsummeringen på den **modellering** fliken av Power BI Desktop.

F:  Jag är ägare till en datauppsättning och vill se till att ett fält aldrig aggregeras.

S:  I Power BI Desktop på fliken **Modellering** anger du **Datatyp** som **Text**.

F:  Jag ser inte **summera inte** som ett alternativ i min listrutan.

S:  Försök att ta bort fältet och sedan lägga till det igen.

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)