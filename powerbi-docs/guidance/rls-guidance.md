---
title: Vägledning säkerhet på radnivå (RLS) med Power BI Desktop
description: Vägledning för att framtvinga säkerhet på radnivå (RLS) i dina datamodeller med Power BI Desktop.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: v-pemyer
ms.openlocfilehash: 308e34e5bf70a9999939c99667075b2e468b4df4
ms.sourcegitcommit: eff98b49e794c7c07670dcfb871f43cb06ed9d3a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2020
ms.locfileid: "85095645"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Vägledning säkerhet på radnivå (RLS) med Power BI Desktop

Den här artikeln är avsedd för dig som är datamodellerare som arbetar med Power BI Desktop. Den beskriver lämpliga designmetoder för att framtvinga säkerhet på radnivå (RLS) i dina datamodeller.

Det är viktigt att förstå RLS-filtrens _tabellrader_. De kan inte konfigureras för att begränsa åtkomsten till modellobjekt som tabeller, kolumner eller mått.

> [!NOTE]
> Den här artikeln beskriver inte RLS eller hur man konfigurerar den. Mer information finns i [Begränsa dataåtkomst med säkerhet på radnivå (RLS) för Power BI Desktop](../create-reports/desktop-rls.md).
>
> Den beskriver inte heller hur man framtvingar RLS i live-anslutningar till externa värdbaserade modeller med Azure Analysis Services eller SQL Server Analysis Services. I dessa fall framtvingas RLS av Analysis Services. När Power BI ansluter med enkel inloggning (SSO), framtvingar Analysis Services RLS (såvida inte kontot har administratörsbehörighet).

## <a name="create-roles"></a>Skapa roller

Det är möjligt att skapa flera roller. När du överväger behörighetsbehoven för en enskild rapportanvändare ska du sträva efter att skapa en enda roll som ger alla dessa behörigheter, i stället för en design där en rapportanvändare blir medlem i flera roller. Anledningen är att en rapportanvändare kan mappa till flera roller, antingen direkt genom att använda sina användarkonton eller indirekt genom säkerhetsgruppsmedlemskap. Flera rollmappningar kan resultera i oväntade resultat.

När en rapportanvändare tilldelas flera roller, så blir RLS-filtren additiva. Det innebär att rapportanvändare kan se tabellrader som representerar unionen av dessa filter. I vissa fall är det dessutom inte möjligt att garantera att en rapportanvändare ser raderna i en tabell. Så till skillnad från behörigheter som tillämpas på SQL Server-databasobjekt (och andra behörighetsmodeller) gäller inte principen "om nekad alltid nekad".

Överväg att använda en modell med två roller: Den första rollen, som kallas **Arbetare** begränsar åtkomsten till alla tabellrader i **Lönelista** med hjälp av följande regeluttryck:

```dax
FALSE()
```

> [!NOTE]
> En regel returnerar inga tabellrader när dess uttryck utvärderas till **false**.

Men en annan roll, som kallas **Hanterare**, tillåter åtkomst till alla tabellrader i **Lönelista** med hjälp av följande regeluttryck:

```dax
TRUE()
```

Tänk på följande: Om en rapportanvändare mappar till båda rollerna ser hen alla tabellrader för **Lön**.

## <a name="optimize-rls"></a>Optimera RLS

RLS fungerar genom att filter tillämpas automatiskt på alla DAX-frågor, och dessa filter kan ha en negativ påverkan på frågeprestanda. Så effektiv RLS-hantering handlar om bra modelldesign. Det är viktigt att du följer råden för modelldesign enligt beskrivningarna i följande artiklar:

- [Förstå star-schemat och dess betydelse för Power BI](star-schema.md)
- Alla vägledningar om relationer finns i [Power BI-vägledningsdokumentationen](https://docs.microsoft.com/power-bi/guidance/)

Oftast är det mer effektivt att använda RLS-filter på tabeller av dimensionstyp och inte på tabeller av faktatyp. Och förlita dig på väldesignade relationer när du vill se till att RLS-filter sprids till andra modelltabeller. Undvik därför att använda DAX-funktionen [LOOKUPVALUE](https://docs.microsoft.com/dax/lookupvalue-function-dax) när modellrelationer kan uppnå samma resultat.

När RLS-filter tillämpas på DirectQuery-tabeller och det finns relationer till andra DirectQuery-tabeller, så var noga med att optimera källdatabasen. Det kan innebära att du måste utforma lämpliga index eller använda bestående beräknade kolumner. Mer information finns i [Vägledning för DirectQuery-modeller i Power BI Desktop](directquery-model-guidance.md).

### <a name="measure-rls-impact"></a>Mäta RLS-påverkan

Du kan mäta RLS-filtrens prestandapåverkan i Power BI Desktop genom att använda [Prestandaanalys](../create-reports/desktop-performance-analyzer.md). Börja med att fastställa de visuella rapportobjektens frågevaraktighet när RLS inte genomdrivs. Använd sedan kommandot **Visa som** på fliken **Modellering** för att genomdriva RLS och fastställa och jämföra frågevaraktigheter.

## <a name="configure-role-mappings"></a>Konfigurera rollmappningar

När du har publicerat till Power BI måste du mappa medlemmarna till datamängdsroller. Endast datamängdsägare eller arbetsytans administratörer kan lägga till medlemmar till roller. Mer information finns i [Säkerhet på radnivå (RLS) med Power BI](../admin/service-admin-rls.md#manage-security-on-your-model).

Medlemmar kan vara användarkonton eller säkerhetsgrupper. Närhelst det är möjligt rekommenderar vi att du mappar säkerhetsgrupper till datamängdsroller. Det innebär att du får hantera medlemskap i säkerhetsgrupper i Azure Active Directory. Du kan eventuellt delegera uppgiften till dina nätverksadministratörer.

## <a name="validate-roles"></a>Validera roller

Testa varje roll så att du kan säkerställa att modellen filtreras korrekt. Det åstadkommer du enkelt med kommandot **Visa som** på menyfliken **Modellering**.

När modellen har dynamiska regler som använder DAX-funktionen [USERNAME](https://docs.microsoft.com/dax/username-function-dax), så var noga med att testa för förväntade _och oväntade_ värden. När du bäddar in Power BI-innehåll, särskilt med scenariot [Appen äger data](../developer/embedded/embedding.md#embedding-for-your-customers), så kan applogiken skicka ett värde som ett faktiskt identitetsanvändarnamn. Se till, närhelst så är möjligt, att oavsiktliga eller skadliga värden resulterar i filter som inte returnerar några rader.

Tänk på ett exempel som använder Power BI Embedded, och där appen skickar användarens jobbroll som det faktiska användarnamnet: Det är antingen Hanterare eller Arbetare. Hanterare kan se alla rader, men arbetare kan bara se rader där värdet för kolumnen **Typ** är Intern.

Följande regeluttryck definieras:

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

Problemet med det här regeluttrycket är att alla värden, förutom "Arbetare", returnerar _Alla tabellrader_. Så ett oavsiktligt värde, som exempelvis "Arbtare", returnerar oavsiktligt alla tabellrader. Därför är det säkrare att skriva ett uttryck som testar för alla förväntade värden. I följande förbättrade regeluttryck kommer ett oväntat värde att resultera i att tabellen inte returnerar några rader.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>Utforma partiell RLS

Ibland kan beräkningar behöva värden som inte begränsas av RLS-filter. En rapport kan exempelvis behöva visa förhållandet mellan den intjänade intäkten för rapportanvändarens försäljningsregion och _alla intjänade intäkter_.

Även om det inte är möjligt för ett DAX-uttryck för att åsidosätta RLS – i själva verket kan det inte ens fastställa huruvida RLS genomdrivs eller ej – så kan du använda en sammanfattningsmodellstabell. Sammanfattningsmodelltabellen får en fråga om att hämta intäkter för "alla regioner" och den begränsas inte av något RLS-filter.

Låt oss se hur dessa designkrav kan implementeras. Se först till följande modelldesign:

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="En bild av ett modelldiagram visas. Designen beskrivs i följande stycken.":::

Modellen består av fyra tabeller:

- Tabellen **Säljare** har en rad per säljare. Den innehåller kolumnen **EmailAddress** som lagrar e-postadressen för respektive säljare. Den här tabellen är dold.
- Tabellen **Försäljning** har en rad per order. Det innehåller måttet **Intäkter i % för hela regionen**, som är utformat att returnera en kvot av intäkterna som intjänats i rapportanvändarens region i förhållande till intäkterna som intjänats i alla regioner.
- Tabellen **Datum** har en rad per datum och tillåter filtrering och gruppering efter år och månad.
- **SalesRevenueSummary** är en beräknad tabell. Den lagrar totala intäkter för respektive orderdatum. Den här tabellen är dold.

Följande uttryck definierar den beräknade tabellen **SalesRevenueSummary**:

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> En [aggregeringstabell](../transform-model/desktop-aggregations.md) kan uppnå samma designkrav.

Följande RLS-regel tillämpas på tabellen **Säljare**:

```dax
[EmailAddress] = USERNAME()
```

Var och en av de tre modellrelationerna beskrivs i följande tabell:

|Relation|Beskrivning|
|---------|---------|
|![Flödesdiagrammets slutnod 1.](media/common/icon-01-red-30x30.png)|Det finns en många-till-många-relation mellan tabellerna **Säljare** och **Försäljning**. RLS-regeln filtrerar kolumnen **EmailAddress** i den dolda tabellen **Säljare** med hjälp av DAX-funktionen [USERNAME](https://docs.microsoft.com/dax/username-function-dax). Kolumnvärdet för **Region** (för rapportanvändaren) sprids till tabellen **Försäljning**.|
|![Flödesdiagrammets slutnod 2.](media/common/icon-02-red-30x30.png)|Det finns en en-till-många-relation mellan tabellerna **Datum** och **Försäljning**.|
|![Flödesdiagrammets slutnod 3.](media/common/icon-03-red-30x30.png)|Det finns en en-till-många-relation mellan tabellerna **Datum** och **SalesRevenueSummary**.|

Följande uttryck definierar måttet **Intäkter i % för hela regionen**:

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> Se till att undvika att känsliga fakta avslöjas. Om det bara finns två regioner i det här exemplet skulle det vara möjligt för en rapportanvändare att beräkna intäkterna för den andra regionen.

## <a name="avoid-using-rls"></a>Undvik att använda RLS

Undvik att använda RLS när det är det vettigaste alternativet. Om du bara har ett litet antal förenklade RLS-regler som tillämpar statiska filter bör du överväga att publicera flera datamängder i stället. Ingen av datamängderna definierar roller eftersom varje datamängd innehåller data för en speciell rapportanvändares publik, som har samma databehörigheter. Skapa sedan en arbetsyta per målgrupp och tilldela åtkomstbehörigheter till arbetsytan eller appen.

Anta att ett företag som bara har två försäljningsregioner bestämmer sig för att publicera en datamängd _för varje försäljningsregion_ till olika arbetsytor. Datamängderna genomdriver inte RLS. De använder dock [frågeparametrar](https://docs.microsoft.com/power-query/power-query-query-parameters) för att filtrera källdata. På så sätt publiceras samma modell till varje arbetsyta – de har helt enkelt bara olika datamängdsparametervärden. Säljare tilldelas åtkomst till endast en av arbetsytorna (eller de publicerade apparna).

Det finns flera fördelar med att undvika RLS:

- **Förbättrade frågeprestanda:** Det kan leda till förbättrade prestanda på grund av färre filter.
- **Mindre modeller:** Även om det resulterar i fler modeller, så är modellerna mindre i storlek. Mindre modeller kan förbättra svarstiderna för fråge och datauppdatering, särskilt om värdkapaciteten belastas. Det är också enklare att bevara modellstorlekarna under kapacitetens storleksgränser. Slutligen är det enklare att balansera arbetsbelastningar mellan olika kapaciteter, eftersom du kan skapa arbetsytor på, eller flytta arbetsytor till, olika kapaciteter.
- **Ytterligare funktioner:** Power BI-funktioner som inte fungerar med RLS, t. ex. [Publicera på webben](../collaborate-share/service-publish-to-web.md), kan användas.

Det finns dock flera fördelar med att undvika RLS:

- **Flera arbetsytor:** En arbetsyta krävs för varje rapportanvändares målgrupp. Om appar publiceras, så betyder det även att det finns en app per respektive rapportanvändares målgrupp.
- **Duplicerat innehåll:** Rapporter och instrumentpaneler måste skapas för varje arbetsyta. Detta kräver ytterligare arbete och tid för konfiguration och underhåll.
- **Högpriviligierade användare:** Högpriviligierade användare som tillhör flera målgrupper för rapportanvändare kan inte se någon samlad datavy. De måste öppna flera rapporter (från olika arbetsytor eller appar).

## <a name="troubleshoot-rls"></a>Felsöka RLS

Om RLS ger oväntade resultat, så kontrollera följande saker:

- Det föreligger felaktiga relationer mellan modelltabellerna vad gäller kolumnmappningar och filterriktningar.
- Relationsegenskapen **Tillämpa säkerhetsfilter i båda riktningarna** har inte konfigurerats korrekt. Mer information finns i [Vägledning för dubbelriktad relation](relationships-bidirectional-filtering.md).
- Tabellerna innehåller inga data.
- Felaktiga värden läses in i tabellerna.
- Användaren har mappats till flera roller.
- Modellen innehåller aggregeringstabeller, och RLS-reglerna kan inte konsekvent filtrera aggregeringar och annan information. Mer information finns i [Använda aggregeringar i Power BI Desktop (RLS för aggregeringar)](../transform-model/desktop-aggregations.md#rls-for-aggregations).

När en enskild användare inte kan se några data kan det bero på att användarens UPN inte lagras eller har angetts inkorrekt. Detta kan inträffa plötsligt om användarkontot har ändrats till följd av en namnändring.

> [!TIP]
> Lägg i testsyfte till ett mått som returnerar DAX-funktionen [USERNAME](https://docs.microsoft.com/dax/username-function-dax). Du kan ge det ett namn i stil med "Vem är jag". Lägg sedan till måttet till ett visuellt kortobjekt i en rapport och publicera det i Power BI.

När en enskild användare kan se alla data, är det möjligt att hen har åtkomst till rapporter direkt på arbetsytan och att hen är datamängdsägaren. RLS framtvingas endast när:

- Rapporten öppnas i en app.
- Rapporten öppnas på en arbetsyta och användaren mappas till rollen [Tittare](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces).

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Säkerhet på radnivå (RLS) med Power BI](../admin/service-admin-rls.md)
- [Begränsa dataåtkomsten med säkerhet på radnivå (RLS) för Power BI Desktop](../create-reports/desktop-rls.md)
- [Modellrelationer i Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
