---
title: Arbeta med aggregat (summa, medelvärde och så vidare) i Power BI-tjänsten
description: Lär dig hur du ändrar aggregeringen i ett diagram (summa, medelvärde, maximum och så vidare) i Power BI-tjänsten.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 06/16/2020
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Reports
ms.openlocfilehash: 4addd87085eb4321253bcf34842ca135f536f981
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238111"
---
# <a name="work-with-aggregates-sum-average-and-so-on-in-the-power-bi-service"></a>Arbeta med aggregat (summa, medelvärde och så vidare) i Power BI-tjänsten

## <a name="what-is-an-aggregate"></a>Vad är en aggregering för något?

Ibland kan du vilja kombinera värden matematiskt i dina data. Den matematiska åtgärden kan vara summa, medelvärde, maximum, antal och så vidare. När du kombinerar värden i dina data kallas det för att *aggregera*. Resultatet av den matematiska åtgärden blir en *aggregering*.

När Power BI-tjänsten och Power BI Desktop skapar visualiseringar, kan de aggregera dina data. Ofta är det just det aggregatet som du vill ha, men andra gånger kan du vilja aggregera värdena på ett annat sätt.  En summa kontra ett medelvärde till exempel. Det finns flera olika sätt att hantera och ändra den aggregering som Power BI använder i en visualisering.

Först ska vi ta en titt på data*typer* eftersom datatypen avgör hur och om Power BI kan aggregera den.

## <a name="types-of-data"></a>Typer av data

De flesta datauppsättningar har mer än en typ av data. På den mest grundläggande nivån är data antingen numeriska eller inte. Power BI kan aggregera numeriska med hjälp av summa, medelvärde, antal, minimum, varians och mycket mer. Tjänsten kan även aggregera textdata, som ofta kallas *kategoriska* data. Om du försöker aggregera ett kategoriskt fält genom att placera det i en bucket som är enbart numerisk, till exempel **Värden** eller **Knappbeskrivningar**, räknar Power BI antalet förekomster av varje kategori eller räknar distinkta förekomster av varje kategori. Särskilda typer av data, till exempel datum, har några egna aggregeringsalternativ: tidigaste, senaste, första och sista.

I exemplet nedan:

- **Sålda enheter** och **Tillverkningskostnad** är kolumner som innehåller numeriska data

- **Segment**, **Land**, **Produkt**, **Månad** och **Månadsnamn** innehåller kategoriska data

   ![Skärmbild av en exempeldatamängd.](media/service-aggregates/power-bi-aggregate-chart.png)

När du skapar en visualisering i Power BI aggregerar tjänsten numeriska fält (standard är *summa*) över ett visst kategoriskt fält.  Det kan till exempel vara ”Enheter sålda ***per produkt***”, ”Enheter sålda ***per månad***” och ”Tillverkningskostnad ***per segment***”. Power BI refererar till vissa numeriska fält som **mått**. Det är lätt att identifiera mått i Power BI-rapportredigeraren – i listan **Fält** visas mått med symbolen ∑ intill. Mer information finns i [Rapportredigeraren ... ta en rundtur](service-the-report-editor-take-a-tour.md).

![Skärmbild av Power BI med listan Fält framhävt.](media/service-aggregates/power-bi-aggregate-fields.png)

## <a name="why-dont-aggregates-work-the-way-i-want-them-to"></a>Varför fungerar inte aggregeringen som jag vill?

Det kan vara förvirrande att arbeta med aggregat i Power BI-tjänsten. Kanske har du ett numeriskt fält, och Power BI låter dig inte ändra aggregeringen. Eller så har du t.ex. ett fält med år som du inte vill aggregera, du vill bara räkna antalet förekomster.

Vanligtvis är det underliggande problemet fältdefinitionen i datamängden. Kanske definierade datamängdens ägare fältet som text, och det förklarar varför Power BI inte kan summera eller genomsnittsberäkna det. Tyvärr [kan endast datauppsättningens ägare ändra hur ett fält kategoriseras](../transform-model/desktop-measures.md). Så om du har ägarbehörighet för datamängden, antingen i Desktop eller det program som användes för att skapa den (till exempel Excel) kan du lösa problemet. Annars måste du kontakta datauppsättningens ägare för hjälp.  

Det finns ett särskilt avsnitt i slutet av den här artikeln som heter [**Överväganden och felsökning**](#considerations-and-troubleshooting). Det innehåller tips och vägledning. Om du inte hittar svaret där kan du ställa din fråga i [Power BI Community-forumet](https://community.powerbi.com). Du får ett snabbt svar direkt från Power BI-teamet.

## <a name="change-how-a-numeric-field-is-aggregated"></a>Ändra hur ett numeriskt fält aggregeras

Anta att du har ett diagram som summerar enheter sålda för olika produkter, men du vill hellre ha medelvärdet.

1. Skapa ett **grupperat stående stapeldiagram** som använder ett mått och en kategori. I det här exemplet använder vi enheter sålda per produkt.  Som standard skapar Power BI ett diagram som summerar sålda enheter (dra måttet till källan **Värde**) för varje produkt (dra kategorin till källan **Axel**).

   ![Skärmbild av diagrammet, fönstret Visualiseringar och listan Fält med summa framhävd.](media/service-aggregates/power-bi-aggregate-sum.png)

1. I fönstret **Visualiseringar** högerklickar du på måttet och väljer den aggregattyp som behövs. I det här fallet väljer vi **Medelvärde**. Om du inte ser den aggregering du behöver kan du läsa avsnittet [**Överväganden och felsökning**](#considerations-and-troubleshooting).

   ![Skärmbild av aggregatlistan med Medelvärde valt och framhävt.](media/service-aggregates/power-bi-aggregate-average.png)

   > [!NOTE]
   > Alternativen i listrutan varierar beroende på 1) vilket fält som valts och 2) hur fältet har kategoriserats av datamängdens ägare.

1. Din visualiseringen använder nu aggregering efter medelvärde.

   ![Skärmbild av diagrammet visar nu medelvärdet av enheter som sålts per produkt.](media/service-aggregates/power-bi-aggregate-average-2.png)

## <a name="ways-to-aggregate-your-data"></a>Sätt att aggregera dina data

Här visas några av de alternativ som kan vara tillgängliga vid aggregering av ett fält:

- **Summera inte**. När det här alternativet är valt behandlar Power BI varje värde i det fältet separat och summerar dem inte. Använd det här alternativet om du har en kolumn med numeriska ID:n som tjänsten inte ska summera.

- **Summera**. Adderar alla värden i fältet.

- **Medelvärde**. Räknar ut ett aritmetiskt medelvärde för värdena.

- **Minimum**. Visar det minsta värdet.

- **Maximum**. Visar det högsta värdet.

- **Antal (ej tomma).** Räknar ut antalet värden i ett fält som inte är tomma.

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

1. Dra fältet **Produkt** till källan **Värden**. Fältet **Värden** används vanligtvis för numeriska fält. Power BI identifierar att det här fältet är ett textfält, anger aggregatet till **Summera inte** och visar dig en tabell med en enda kolumn.

   ![Skärmbild av fältet Produkt i källan Värden.](media/service-aggregates/power-bi-aggregate-value.png)

1. Om du ändrar aggregeringen från standardvärdet **Summera inte** till **Antal (distinkta)** räknar Power BI antalet olika produkter. I det här fallet finns det fyra.
  
   ![Skärmbild av det distinkta antalet produkter.](media/service-aggregates/power-bi-aggregate-count.png)

1. Om du i stället ändrar aggregeringen till **Antal**, räknar Power BI det totala antalet. I det här fallet finns det sju poster för **Produkt**.

   ![Skärmbild av antalet produkter.](media/service-aggregates/power-bi-aggregate-count-2.png)

1. Genom att dra samma fält (i det här fallet **Produkt**) till källan **Värden** och låta standardaggregeringen **Summera inte** vara kvar delar Power BI upp antalet efter produkt.

   ![Skärmbild av produkten och antalet produkter.](media/service-aggregates/power-bi-aggregate-final.png)

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

F:  Varför har jag inte alternativet **Summera inte**?

S:  Det fält du valt är sannolikt ett beräknat mått i en flerdimensionell modell, eller ett mått som skapats i Excel eller [Power BI Desktop](../transform-model/desktop-measures.md). Varje mått har sin egen hårdkodade formel. Du kan inte ändra den aggregering som används av Power BI. Om den till exempel är en summa, kan den bara vara en summa. Listan **Fält** visar *mått* med kalkylatorsymbolen.

F:  Mitt fält **är** numeriskt, varför är mina enda alternativ **Antal** och **Distinkt antal**?

S1:  Sannolikt är förklaringen att datamängdens ägare *inte* har klassificerat fältet som ett tal. Om en datamängd till exempel har ett **år**-fält kan datamängdens ägare kategorisera det värdet som text. Det är mer troligt att Power BI räknar **år**-fältet (till exempel antalet personer födda 1974). Det är mindre troligt att Power BI summerar eller genomsnittsberäknar det. Om du är ägaren kan du öppna datamängden i Power BI Desktop och använda fliken **Modellering** för att ändra datatypen.

S2: Om fältet har en kalkylatorikon innebär det att det är ett *mått*. Varje mått har sin egen formel som bara datauppsättningens ägare kan ändra. Den beräkning som Power BI använder kan vara en enkel aggregering, till exempel ett medelvärde eller en summa. Det kan även vara något mer komplicerat såsom ”procenten av bidraget till den överordnade kategorin” eller ”löpande totalsumma sedan årets start”. Power BI kommer inte att sammanfatta eller medelvärdesberäkna resultatet. I stället räknar det bara om (med hjälp av den hårdkodade formeln) för varje datapunkt.

S3:  En annan möjlighet är att du har släppt fältet i en *bucket* som endast tillåter kategoriska värden.  I så fall är dina enda alternativ antal och distinkt antal.

S4:  Ett fjärde alternativ är att du använder fältet som en axel. I ett stapeldiagrams axel visar till exempel Power BI en stapel för varje distinkt värde – den aggregerar inte fältvärdena alls.

>[!NOTE]
>Undantaget till denna regel är punktdiagram som *kräver* aggregerade värden för X- och Y-axlarna.

F:  Varför kan jag inte aggregera textfält för SSAS-datakällor (SQL Server Analysis Services)?

S:  Live-anslutningar till flerdimensionella SSAS-modeller tillåter inte några aggregeringar på klientsidan, inklusive första, sista, medelvärde, minimum, maximum och summa.

F:  Jag har ett punktdiagram och jag vill *inte* att mitt fält ska aggregeras.  Hur gör jag?

S:  Lägg till fältet i **Information** i stället för X- eller Y-axelns bucket.

F:  När jag lägger till ett numeriskt fält i en visualisering summeras de flesta som standard, men vissa har medelvärde, antal eller någon annan typ av aggregering som standard.  Varför är inte standardaggregeringen alltid likadan?

S:  Datamängdens ägare kan ange en standardsummering för varje fält. Om du är ägare till en datamängd kan du ändra standardsummeringen på fliken **Modellering** i Power BI Desktop.

F:  Jag är ägare till en datauppsättning och vill se till att ett fält aldrig aggregeras.

S:  I Power BI Desktop på fliken **Modellering** anger du **Datatyp** som **Text**.

F:  Jag ser inte **Summera inte** som ett alternativ i listrutan.

S:  Försök att ta bort fältet och sedan lägga till det igen.

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
