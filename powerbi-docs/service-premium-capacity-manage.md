---
title: Hantera Microsoft Power BI Premium-kapaciteter
description: Beskriver hanteringsuppgifter för Power BI Premium-kapaciteter.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 2e32a61891cee2fb5e2a80167d5283962dc164bb
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74697484"
---
# <a name="managing-premium-capacities"></a>Hantera Premium-kapaciteter

Hantering av Power BI Premium innebär att skapa, hantera och övervaka Premium-kapaciteter. Den här artikeln innehåller en översikt av kapaciteter. Stegvisa instruktioner finns i [Konfigurera och hantera kapaciteter](service-admin-premium-manage.md).

## <a name="creating-and-managing-capacities"></a>Skapa och hantera kapaciteter

Sidan **Kapacitetsinställningar** i Power BI-administratörsportalen visar det antal v-kärnor som har köpts samt tillgängliga Premium-kapaciteter. Sidan gör att globala administratörer för Office 365 eller Power BI-tjänsten kan skapa Premium-kapaciteter från tillgängliga v-kärnor eller ändra befintliga Premium-kapaciteter.

När administratörer skapar en Premium-kapacitet måste de definiera:

- Kapacitetsnamn (unikt i klientorganisationen).
- Kapacitetsadministratör(er).
- Kapacitetsstorlek.
- Region för datahemvist.

Minst en kapacitetsadministratör måste tilldelas. Användare som utsetts till kapacitetsadministratörer kan:

- Tilldela arbetsytor till kapaciteten.
- Hantera användarbehörigheter för att lägga till ytterligare kapacitetsadministratörer eller användare med tilldelningsbehörighet (så att de kan tilldela arbetsytor till kapaciteten).
- Hantera arbetsbelastningar för att konfigurera högsta minnesanvändning för sidnumrerade rapporter och dataflödesarbetsbelastningar.
- Starta om kapaciteten för att återställa alla åtgärder på grund av systemöverbelastning.

Kapacitetsadministratörer kan inte komma åt arbetsyteinnehåll såvida de inte uttryckligen tilldelas i behörigheter för arbetsyta. De har heller inte åtkomst till alla Power BI-administrationsområden (såvida de inte uttryckligen tilldelas sådan), till exempel användningsmått, granskningsloggar och inställningar för klientorganisation. Viktigt är att kapacitetsadministratörer inte har behörighet att skapa nya kapaciteter eller skala befintliga kapaciteter. Administratörer tilldelas per kapacitet, vilket försäkrar att de bara kan visa och hantera de kapaciteter som de är tilldelade.

Kapacitetsstorlek väljs från en tillgänglig lista med SKU-alternativ, som begränsas av antalet tillgängliga v-kärnor i poolen. Det går att skapa flera kapaciteter från poolen som kan hämtas från en eller flera köpta SKU:er. Till exempel kan en P3-SKU (32 kärnor) användas för att skapa tre kapacitet: en P2 (16 v-kärnor), och två P1 (2 x 8 v-kärnor). Förbättrad prestanda och skala kan uppnås genom kapaciteter av mindre storlek skapas, vilket beskrivs i artikeln [Optimera Premium-kapaciteter](service-premium-capacity-optimize.md). I den här bilden ser du en exempelinstallation av den fiktiva Contoso-organisationen som består av fem Premium-kapaciteter (3 x P1 och 2 x P3) där var och en har arbetsytor, samt flera arbetsytor i delad kapacitet.

![En exempelinstallation för det fiktiva företaget Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

En Premium-kapacitet kan tilldelas till en annan region än Power BI-klientorganisationens hemregion, vilket kallas multi-geo. Multi-geo ger administrativ kontroll över vilka datacenter inom definierade geografiska områden som ditt Power BI-innehåll finns. Anledningen till en multi-geo-distribution är vanligtvis för efterlevnad för företag eller myndigheter, snarare än för prestanda och skalning. Inläsning av rapporter och instrumentpaneler involverar fortfarande förfrågningar om metadata från hemregionen. Mer information finns i [Multi-Geo-stöd för Power BI Premium](service-admin-premium-multi-geo.md).

Power BI-tjänstadministratörer och globala Office 365-administratörer kan ändra Premium-kapaciteter. Mer specifikt kan de:

- Ändra kapacitetsstorlek för att skala upp eller skala ned resurser.
- Lägga till eller ta bort kapacitetsadministratörer.
- Lägga till eller ta bort användare som har tilldelningsbehörigheter.
- Lägga till eller ta bort ytterligare arbetsbelastningar.
- Ändra regioner.

Tilldelningsbehörigheter krävs för att tilldela en arbetsyta till en specifik Premium-kapacitet. Behörigheterna kan beviljas till hela organisationen, specifika användare eller grupper.

Som standard stöder Premium-kapaciteterna arbetsbelastningar som är associerade med att köra Power BI-frågor. Premium-kapaciteter har även stöd för ytterligare arbetsbelastningar: **AI (Cognitive Services)** , **sidnumrerade rapporter** och **dataflöden**. Varje arbetsbelastning kräver att du konfigurerar den högsta mängd minne (som en procentandel av den totala mängden tillgängligt minne) som kan användas av arbetsbelastningen. Det är viktigt att förstå att en ökning av maximala minnesallokeringar kan påverka det antal aktiva modeller som kan värdhanteras samt flödet av uppdateringar. 

Minne allokeras dynamiskt till dataflöden, men allokeras statiskt till sidnumrerade rapporter. Orsaken till att statiskt allokera maximalt minne är att sidnumrerade rapporter körs inom ett säkert inneslutet utrymme av kapaciteten. Försiktighet bör iakttas vid inställning av minne för sidnumrerade rapporter eftersom det minskar tillgängligt minne för att läsa in modeller. Mer information finns i [Standardinställningar för minne](service-admin-premium-workloads.md#default-memory-settings).

Det är möjligt att ta bort en Premium-kapacitet, och det leder inte till borttagning av dess arbetsytor och innehåll. I stället flyttas alla tilldelade arbetsytor till delad kapacitet. När Premium-kapaciteten skapades i en annan region flyttas arbetsytan till delad kapacitet för hemregionen.

### <a name="assigning-workspaces-to-capacities"></a>Tilldela arbetsytor till kapaciteter

Arbetsytor kan tilldelas till en Premium-kapacitet i Power BI-administratörsportalen, eller i fönstret **Arbetsyta** för enskilda arbetsytor.

Kapacitetsadministratörer samt globala administratörer för Office 365 eller Power BI-tjänstadministratörer kan masstilldela arbetsytor i Power BI-administratörsportalen. Masstilldelningar kan gälla för:

- **Arbetsytor från användare** – Alla arbetsytor som ägs av dessa användare, däribland personliga arbetsytor, tilldelas till Premium-kapaciteten. Detta omfattar omtilldelning av arbetsytor när de redan har tilldelats till en annan Premium-kapacitet. Dessutom kan användare också tilldelas behörigheter för arbetsytetilldelning.

- **Särskilda arbetsytor**
- **Hela organisationens arbetsytor** – Alla arbetsytor, däribland personliga arbetsytor, tilldelas till Premium-kapaciteten. Alla aktuella och framtida användare tilldelas behörigheter för arbetsytetilldelning. Den här metoden rekommenderas inte. Ett mer riktat tillvägagångssätt är att föredra.

En arbetsyta kan läggas till en Premium-kapacitet med hjälp av fönstret **Arbetsyta** förutsatt att användaren är både administratör för en arbetsyta och har behörighet för kapacitetstilldelning.

![Använda fönstret arbetsyta för att tilldela en arbetsyta till en Premium-kapacitet](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Administratörer för arbetsytan kan ta bort en arbetsyta från en kapacitet (till en delad kapacitet) utan att behöva tilldelningsbehörighet. Ta bort arbetsytor från dedikerade kapaciteter flyttar effektivt arbetsytan till en delad kapacitet. Observera att ta bort en arbetsyta från en Premium-kapacitet kan ha negativa konsekvenser vilket till exempel resulterar i att delat innehåll skulle bli otillgängligt för Power BI Free-licensierade användare eller inaktivering av schemalagd uppdatering när de överskrider de tilldelningar som stöds av delade kapaciteter.

I Power BI-tjänsten identifieras en arbetsyta som tilldelats en Premium-kapacitet lätt via diamantikonen som pryder arbetsytans namn.

![Identifiera en arbetsyta som tilldelats en Premium-kapacitet](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Övervaka kapaciteter

Övervakning av Premium-kapaciteter ger administratörer en förståelse för hur kapaciteterna utförs. Kapaciteter kan övervakas med hjälp av Power BI-administratörsportalen eller appen **Kapacitetsmått för Power BI Premium** (Power BI).

### <a name="power-bi-admin-portal"></a>Power BI-administratörsportalen

I administratörsportalen innehåller fliken **Hälsa** för varje kapacitet sammanfattningsmått för kapaciteten och varje aktiverad arbetsbelastning. Mått visar ett genomsnitt för de senaste sju dagarna.  

På kapacitetsnivå är måtten ackumulerade för alla aktiverade arbetsbelastningar. Följande mått tillhandahålls:

- **CPU UTILIZATION** (CPU-användning) – visar genomsnittlig CPU-användning som en procentandel av de totala tillgängliga CPU-resurserna för kapaciteten.  
- **MEMORY USAGE** (Minnesanvändning) – visar genomsnittlig minnesanvändning (i GB) som totalt tillgängligt minne för kapaciteten. 

För varje aktiverad arbetsbelastning anges CPU-användning och minnesanvändning samt ett antal arbetsbelastningsspecifika mått. För till exempel arbetsbelastningen Dataflöde visar **Totalt antal** de totala uppdateringarna för varje dataflöde, och **Genomsnittlig varaktighet** visar genomsnittlig varaktighet för uppdatering för dataflödet.

![Fliken Kapacitetshälsa i portalen](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Mer information om alla tillgängliga mått för varje arbetsbelastning finns i [Övervaka kapaciteter i administratörsportalen](service-admin-premium-monitor-portal.md).

Övervakningsfunktionerna i Power BI-administratörsportalen är utformade för att ge en snabb sammanfattning av viktiga kapacitetsmått. För mer detaljerad övervakning rekommenderas det att du använder appen **Kapacitetsmått för Power BI Premium**.

### <a name="power-bi-premium-capacity-metrics-app"></a>Kapacitetsmåttappen för Power BI Premium

Appen [Kapacitetsmått för Power BI Premium](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) är en Power BI-app som är tillgänglig för kapacitetsadministratörer och installeras på samma sätt som andra Power BI-appar. Den innehåller en instrumentpanel och rapport.

![Kapacitetsmåttappen för Power BI Premium](media/service-premium-capacity-manage/capacity-metrics-app.png)

När appen öppnas läses instrumentpanelen in för att presentera flera paneler som uttrycker en aggregerad vy över alla kapaciteter som användaren är kapacitetsadministratör för. Instrumentpanelens layout innehåller fem huvudavsnitt:

- **Översikt** – Appversion, antalet kapaciteter och arbetsytor
- **Sammanfattning av systemet** – Mått för minne och CPU
- **Sammanfattning av datamängder** – Antalet datamängder, DQ/LC samt uppdaterings- och frågemått
- **Sammanfattning av dataflöden** – Antalet dataflöden samt datamängdsmått
- **Sammanfattning av sidnumrerad rapport** – Uppdaterings- och visningsmått

Du kan nå den underliggande rapporten, som instrumentpanelens paneler fästes från, genom att klicka på valfri panel på instrumentpanelen. Den ger en mer detaljerad översikt över vart och ett av instrumentpanelens avsnitt och stöder interaktiv filtrering. 

Filtrering kan uppnås genom att ange utsnitt efter datumintervall, kapacitet, arbetsyta och arbetsbelastning (rapport, datauppsättning, dataflöde) och genom att välja element i rapportens visuella objekt för att korsfiltrera rapportsidan. Korsfiltreringen är en kraftfull teknik för att begränsa till bestämda tidsperioder, kapaciteter, arbetsytor, datauppsättningar, etc. och kan vara mycket användbar när du utför rotorsaksanalys.

Detaljerad information om mått för instrumentpaneler och rapporter i appen finns i [Övervaka Premium-kapaciteter med appen](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Tolka mått

Mått bör övervakas för att upprätta en grundläggande förståelse för resursanvändning och arbetsbelastningsaktivitet. Om kapaciteten blir långsam, är det viktigt att förstå vilka mått som ska övervakas och vilka slutsatser du kan dra.

Vi rekommenderar att frågor bör slutföras inom en sekund för att leverera dynamiska upplevelser till rapportanvändare och möjliggöra högre frågedataflöde. Det är vanligtvis mindre viktigt när bakgrundsprocesser, inklusive uppdateringar, tar längre tid att slutföra.

I allmänhet kan långsamma rapporter vara en indikation på en överhettad kapacitet. När det inte gick att läsa in rapporter, är det här en indikation på en överhettad kapacitet. I båda fallen kan rotorsaken tillskrivas många faktorer, bland annat:

- **Misslyckade frågor** indikerar verkligen minnesbelastning och att en modell inte kunde läsas in i minnet. Power BI-tjänsten kommer att försöka läsa in en modell i 30 sekunder innan åtgärden misslyckas.

- **Långa frågeväntetider** kan ha flera olika orsaker:
  - Behovet av att Power BI-tjänsten först tar bort modellen/modellerna och sedan läser in den modell som frågor ska köras mot (beakta att enbart högre borttagningsfrekvenser för datamängder i sig inte är någon indikation på kapacitetsstress, såvida de inte åtföljs av långa frågeväntetider som indikerar minnessönderhackning).
  - Modellinläsningstider (särskilt väntetiden för att läsa in en stor modell i minnet).
  - Långvariga frågor.
  - För många LC-\DQ-anslutningar (överstiger kapacitetsbegränsningar).
  - Processormättnad.
  - Komplex rapportdesign med överdrivet många visuella objekt på en sida (beakta att varje visuellt objekt är en fråga).

- **Långa frågevaraktigheter** kan tyda på att modellutformningarna inte är optimerade, särskilt när flera datauppsättningar är aktiva i en kapacitet och bara en datauppsättning ger långa frågevaraktigheter. Detta tyder på att kapaciteten är tillräckligt resurstilldelad och att datauppsättningen i fråga är icke-optimal eller bara långsam. Långvariga frågor kan vara problematiska eftersom de kan blockera åtkomst till resurser som krävs av andra processer.
- **Långa väntetider för uppdatering** tyder på otillräckligt med minne på grund av många aktiva modeller som förbrukar minne eller att en problematisk uppdatering blockerar andra uppdateringar (överstiger gränser för parallella uppdateringar).

En mer detaljerad förklaring av hur du använder mått finns i artikeln [Optimera Premium-kapaciteter](service-premium-capacity-optimize.md).

## <a name="acknowledgements"></a>Bekräftelser

Den här artikeln är skriven av Peter Myers, Data Platform MVP och oberoende BI-expert på [Bitwise Solutions](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
> [Optimera Premium-kapaciteter](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Konfigurera arbetsbelastningar i en Premium-kapacitet](service-admin-premium-workloads.md)   

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

