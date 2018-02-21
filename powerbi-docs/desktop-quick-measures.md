---
title: "Använda snabbmått för att enkelt utföra vanliga och kraftfulla beräkningar i Power BI"
description: "Snabbåtgärder är färdiga DAX-formler som snabbt hanterar vanliga beräkningar"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 02/05/2018
ms.author: davidi
ms.openlocfilehash: ce971f980bf1796bfef8439b1ea260190fb678df
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2018
---
# <a name="use-quick-measures-to-easily-perform-common-and-powerful-calculations"></a>Använd snabbmått för att enkelt utföra vanliga och kraftfulla beräkningar
Du kan använda **snabbmått** när du snabbt och enkelt vill utföra vanliga och kraftfulla beräkningar. Ett **snabbmått** kör en uppsättning DAX-kommandon i bakgrunden (du behöver inte skriva DAX – det är klart) som bygger på indata som du anger i en dialogruta. Sedan presenteras resultatet i rapporten. Du kan bästa är att du kan se de DAX-kommandon som körs av snabb måttet och komma igång med eller utöka din egen DAX kunskap.

![](media/desktop-quick-measures/quick-measures_01.png)

Du skapar **snabbmått** genom att högerklicka på ett fält i **fältbrunnen** sedan välja **snabbmått** från menyn som visas. Du kan också högerklicka på ett värde i fältet **Värden** på ett befintligt visuellt objekt (till exempel fältet *Värden* i ett *stapeldiagram*). Det finns många tillgängliga kategorier för beräkningar och sätt att ändra varje beräkningen så att den passar dina behov.

### <a name="quick-measures-now-generally-available"></a>Snabbmått är nu allmänt tillgängliga

I och med lanseringen av **Power BI Desktop** i februari 2018 är snabbmått allmänt tillgängliga (inte längre i förhandsversion). Om du använder en tidigare version av **Power BI Desktop** kan du testa funktionen **Snabbmått** i den version av **Power BI Desktop** som släpps i **april 2017** genom att välja **Arkiv > Alternativ och inställningar > Alternativ > Förhandsversionsfunktioner** och sedan markera kryssrutan vid **Snabbmått**.

![](media/desktop-quick-measures/quick-measures_02b.png)

Du måste starta om **Power BI Desktop** när du har gjort valet.

## <a name="using-quick-measures"></a>Använda snabbmått
För att **snabbmått**, högerklicka på ett fält (alla fält) i brunnen **Fält** i **Power BI Desktop** och välj **snabbmått** från menyn som visas.

![](media/desktop-quick-measures/quick-measures_01.png)

Modellering måste finnas på den datauppsättning som för närvarande är inlästa för att **snabbåtgärder** ska vara tillgängliga. Därför visas inte live-anslutningar (till exempel en anslutning till en datamängd för Power BI-tjänsten) i menyn **snabbmått** objektet när du högerklickar på listan **Fält**, med undantag för SSAS live-anslutningar. 

När du använder SQL Server Analysis Services (SSAS) live-anslutningar är vissa **snabbmått** tillgängliga. **Power BI Desktop** visar endast mängden av **snabbmått** som stöds för versionen av SSAS som du ansluter till. Om du är ansluten till en SSAS live-datakälla och du inte ser vissa **snabbmått** i listan beror det på att den SSAS-version som du är ansluten till inte stöder det DAX-mått som används för att implementera **snabbmåttet**.

Följande **snabbmått** visas från högerklicksmenyn så att du kan välja önskad beräkning och fälten mot vilka du vill köra beräkningen.

![](media/desktop-quick-measures/quick-measures_03.png)

När du väljer listrutan visas med en lång lista över tillgängliga **snabbmått**.

![](media/desktop-quick-measures/quick-measures_04.png)

Det finns fem olika grupper av beräkningstyper i snabbmått, var och ett med en samling av beräkningar. Dessa grupper och beräkningar är följande:

* **Sammanställ per kategori**
  * Genomsnitt inom en kategori
  * Varians inom en kategori
  * Maxvärde inom en kategori
  * Minimivärde inom en kategori
  * Viktat genomsnitt per kategori
* **Filter**
  * Filtrerat värde
  * Skillnad från baslinje
  * Procentuell skillnad från filtrerat värde
  * Försäljning från nya kategorier
* **Tidsintelligens**
  * Summa hittills det här året
  * Summa hittills det här kvartalet
  * Summa hittills den här månaden
  * Ändring från år till år
  * Ändring från kvartal till kvartal
  * Förändring månad för månad
  * Rullande medelvärde
* **Summor**
  * Löpande summa
  * Summa för kategorin (filter applicerade)
  * Summan för kategorin (filter ej applicerade)
* **Matematiska operationer**
  * Tillägg
  * Subtraktion
  * Multiplikation
  * Division
  * Procentuell skillnad
  * Korrelationskoefficient
* **Text**
  * Omdöme i stjärnor
  * Sammanlänkad lista med värden

Vi planerar att lägga till dessa beräkningar och vill veta vilka **snabbmått** du skulle vilja se och om du har idéer (inklusive underliggande DAX-formler) för **snabbmått** som du vill att vi överväger. Mer information om detta finns i slutet på den här artikeln.

## <a name="example-of-quick-measures"></a>Exempel på snabbmått
Låt oss ta en titt på ett exempel på dessa **snabbmått** i praktiken.

Följande **matris** innehåller en tabell med försäljning för olika elektronikprodukter. Det är en enkel tabell som innehåller det totala antalet för varje kategori.

![](media/desktop-quick-measures/quick-measures_05.png)

När vi högerklickar du på fältet **Värden** och väljer **Snabbmått** kan vi välja *Genomsnitt inom en kategori* som *beräkning*och välja *Summan av försäljning* som *basvärde*. Ange *SalesAmount* genom att dra fältet från rutan *Fält*  i den högra rutan i avsnittet *Kategori* till vänster.

![](media/desktop-quick-measures/quick-measures_06.png)

När vi väljer **OK** händer ett par intressanta saker, enligt bilden efter den här listan:

1. Nu har **matrisen** ny kolumn som visar vår beräkning (i det här fallet *Genomsnittlig försäljning inom försäljning*).
2. Ett nytt **mått** har skapats och är tillgängligt i **Fält** och har markerats (Power BI placerar en gul ruta omkring den). Det här måttet är tillgängligt för andra visuella objekt i rapporten, inte bara det visuella objektet som det ursprungligen skapades för.
3. DAX-formeln som har skapats för **snabbmåttet** visas i formelfältet.

![](media/desktop-quick-measures/quick-measures_07.png)

För att börja med det första objektet, lägg märke till att **snabbmåttet** har tillämpats på det visuella objektet. Det finns en ny kolumn och tillhörande värde som baseras på det **snabbmått** som har skapats.

![](media/desktop-quick-measures/quick-measures_08.png)

Därefter visas **snabbmåttet** visas i brunnen **fält** i datamodellen och kan användas som ett annat fält i modellen för andra visuella objekt. I följande bild har ett snabbt **stapeldiagram** skapats med hjälp av det nya fältet som skapats av **snabbmåttet**.

![](media/desktop-quick-measures/quick-measures_09.png)

Nu ska vi gå till nästa avsnitt för att diskutera det tredje objektet, DAX-formler.

## <a name="learn-dax-using-quick-measures"></a>Lär dig DAX med snabbmått
En annan stor nytta av funktionen **snabbåtgärder** är att den direkt visar DAX-formeln som skapades för att genomföra åtgärden. I följande bild, har vi valt mått som har skapats av **snabbmått** (nu är det i brunnen **Fält**, så det är bara att klicka på det). När vi gör det visas **Formelfältet**, vilket visar DAX-formeln som Power BI skapade för att verkställa måttet.

![](media/desktop-quick-measures/quick-measures_10.png)

Det är bra, eftersom den visar formeln bakom måttet. Men det gör det möjligt att använda **snabbmått** för att se hur de underliggande DAX-formlerna ska skapas.

Anta att du behöver göra en beräkning som jämför två år, men du vet inte hur du ska strukturera DAX-formeln (eller du vet inte var du ska börja!). Istället för att slå huvudet mot skrivbordet kan du skapa ett **snabbmått** med beräkningen **årsvis förändring** och se vad som händer. Till exempel, skapa ett **snabbmått** och se hur det visas i ditt visuella objekt, se hur DAX-formeln fungerade och utför ändringarna antingen direkt i DAX eller skapa ett annat mått tills beräkningarna uppfyller dina behov eller förväntningar.

Det är som att ha en snabb lärare som svarar omedelbart på hypotetiska frågor med några få klickningar. Du kan alltid ta bort dessa mått från din modell om du inte gillar dem – det är bara att högerklicka på måttet och välja **Ta bort**.

![](media/desktop-quick-measures/quick-measures_11.png)

När måttet är perfekt kan du byta namn efter behov med samma högerklicksmeny.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
Det finns några begränsningar och saker du bör tänka på.

* **Snabbmått** är endast tillgängliga om du kan ändra modellen, vilket inte är fallet när du arbetar med DirectQuery eller de flesta live-anslutningar (SSAS live-anslutningar stöds, som tidigare förklarats).
* Måttet som har lagts till i brunnen **Fält** kan användas med alla visuella objekt i rapporten.
* Du kan se DAX-uttryck som är associerade med ett **snabbmått** genom att välja det skapade måttet i brunnen **Fält**. Titta sedan på formeln i **formelfältet**.

> [!WARNING]
> Snabbmått skapar för närvarande *endast* DAX-uttryck med kommatecken för argumentavgränsare. Om din version av **Power BI Desktop** är lokaliserat till ett språk som använder kommatecken som decimalavgränsare kommer snabbmått inte att fungera korrekt.
> 
> 

### <a name="time-intelligence-and-quick-measures"></a>Tidsinformation och snabbmått
Från och med uppdateringen i oktober 2017 av **Power BI Desktop** kan du använda dina egna anpassade datum-tabeller med tidsinformation-**snabbåtgärder**. Om datamodellen har en anpassad datumtabell kan du använda den primära datumkolumnen i tabellen för snabbmått för tidsinformation. Du *måste* se till att den primära kolumnen i tabellen har markerats som en datumtabell när modellen har skapats, enligt beskrivningen [i den här artikeln](https://docs.microsoft.com/sql/analysis-services/tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular).

### <a name="additional-information-and-examples"></a>Ytterligare information och exempel
Vi förväntar oss att behöva tillhandahålla exempel och vägledning för varje beräkning i **snabbmått** beräkningar, så det är värt att återkomma för uppdateringar om den fokuserade artikeln.

Har du en idé för ett **snabbmått** som inte redan finns? Toppen! Ta en titt på [den här sidan](https://go.microsoft.com/fwlink/?linkid=842906) och skicka uppslag (och DAX-formler) för **snabbmått** du skulle vilja se i **Power BI Desktop** så kan vi att överväga att lägga till den i den angivna listan över **snabbmått** i en framtida version.

