---
title: Hantera Microsoft Power BI Premium-kapaciteter
description: Beskriver hanteringsaktiviteter för Power BI Premium-kapacitet.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565252"
---
# <a name="managing-premium-capacities"></a>Hantera Premium-kapaciteter

Hantera Power BI Premium omfattar att skapa, hantera och övervaka Premium-kapaciteter.

## <a name="creating-and-managing-capacities"></a>Skapa och hantera kapacitet

Den **kapacitetsinställningarna** i Power BI Admin-portalen visar antalet kärnor som har köpt och Premium-kapaciteter som är tillgängliga. Sidan kan Office 365 globala administratörer eller Power BI-tjänstadministratörer för att skapa Premium-kapaciteter från tillgängliga v-kärnor, eller ändra befintliga Premium-kapaciteter.

När du skapar en Premium-kapacitet krävs för administratörer att definiera:

- Kapacitetsnamn (unika i klienten).
- Kapacitet admin(s).
- Kapacitetsstorlek.
- Region för dataplacering.

Minst en kapacitetsadministratör måste tilldelas. Användare som utsetts till kapacitetsadministratörer kan:

- Tilldela kapaciteten arbetsytor.
- Hantera användarbehörigheter för att lägga till ytterligare Kapacitetsadministratörer eller användare med tilldelningsbehörighet (för att kunna tilldela kapaciteten arbetsytor).
- Hantera arbetsbelastningar, om du vill konfigurera högsta minnesanvändning för sidnumrerade rapporter och dataflöden arbetsbelastningar.
- Starta om kapacitet, för att återställa alla åtgärder på grund av en system-överlagring.

Kapacitetsadministratörer kan inte komma åt arbetsyteinnehåll såvida inte uttryckligen har tilldelats i behörigheter för arbetsytan. De också har inte åtkomst till alla Power BI-administratörsområden (såvida inte uttryckligen tilldelad), till exempel användningsstatistik, granskningsloggar och klientinställningar. Viktigt är att kapacitetsadministratörer inte har behörighet att skapa nya kapaciteter eller skala befintliga kapaciteter. Administratörer har tilldelats på basis av per kapacitet kan se till att de kan bara visa och hantera kapaciteter som de har tilldelats.

Kapacitetsstorlek väljs från en tillgänglig lista med SKU-alternativ som är begränsad av antalet tillgängliga v-kärnor i poolen. Det är möjligt att skapa flera kapaciteter från poolen, som kan hämtas från en eller flera köpt SKU: er. Till exempel kan en P3-SKU (32 kärnor) användas för att skapa tre kapacitet: en P2 (16 v-kärnor), och två P1 (2 x 8 v-kärnor). Förbättrad prestanda och skalning kan uppnås genom att skapa mindre storlekar kapacitet, enligt beskrivningen i den [optimera Premium-kapaciteter](service-premium-capacity-optimize.md) artikeln. Följande bild visar en exempelinstallation av den fiktiva Contoso-organisationen som består av fem Premium-kapaciteter (3 x P1 och 2 x P3) där var och en innehåller app-arbetsytor och flera arbetsytor i delad kapacitet.

![En exempelinstallation för det fiktiva företaget Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

En annan region än hemregion av Power BI-klient som kallas hjälpdokumentation för flera geografiska kan tilldelas en Premium-kapacitet. Hjälpdokumentation för flera geografiska ger administrativ kontroll över vilka datacenter i definierade geografiska områden som finns i Power BI-innehåll. Anledningen till en multi-geo-distribution är vanligtvis för efterlevnad för företag eller myndigheter, snarare än för prestanda och skalning. Inläsning av rapporter och instrumentpaneler involverar fortfarande förfrågningar om metadata från hemregionen. Mer information finns i [Multi-Geo-stöd för Power BI Premium](service-admin-premium-multi-geo.md).

Power BI-tjänstadministratörer och globala Office 365-administratörer kan ändra Premium-kapaciteter. Mer specifikt kan de:

- Ändra storleken på kapacitet att skala upp eller skala ned resurserna.
- Lägg till eller ta bort Kapacitetsadministratörer.
- Lägg till eller ta bort användare som har tilldelningsbehörighet.
- Lägg till eller ta bort ytterligare arbetsbelastningar.
- Ändra de regioner.

Tilldelningsbehörigheter krävs för att tilldela en arbetsyta till en specifik Premium-kapacitet. Behörigheterna kan beviljas till hela organisationen, specifika användare eller grupper.

Som standard stöder Premium-kapaciteterna arbetsbelastningar som är associerade med att köra Power BI-frågor. Premium-kapaciteter har också stöd för ytterligare arbetsbelastningar: **AI (Cognitive Services)** , **sidnumrerade rapporter**, och **dataflöden**. Varje arbetsbelastning kräver att du konfigurerar den högsta mängd minne (som en procentandel av den totala mängden tillgängligt minne) som kan användas av arbetsbelastningen. Det är viktigt att förstå att öka maximal minnesallokeringar kan påverka antalet aktiva modeller som kan användas och dataflödet för uppdateringar. 

Minne allokeras dynamiskt till dataflöden, men tilldelas statiskt sidnumrerade rapporter. Orsaken till att statiskt allokera maximalt minne är att sidnumrerade rapporter körs inom ett säkert inneslutet utrymme av kapaciteten. Försiktighet bör iakttas vid inställning av minne för sidnumrerade rapporter eftersom det minskar tillgängligt minne för att läsa in modeller. Mer information finns i den [standard minnesinställningarna](service-admin-premium-workloads.md#default-memory-settings).

Tar bort en Premium-kapacitet är möjligt och resultera inte i borttagningen av dess arbetsytor och innehåll. I stället flyttas den tilldelade arbetsytor till delad kapacitet. När Premium-kapacitet skapades i en annan region, flyttas arbetsytan till delad kapacitet för hemregion.

### <a name="assigning-workspaces-to-capacities"></a>Tilldela arbetsytor till kapacitet

Arbetsytor kan tilldelas en Premium-kapacitet i Power BI-administratörsportalen, eller för en app-arbetsyta i den **arbetsytan** fönstret.

Kapacitetsadministratörer, samt globala administratörer för Office 365 eller Power BI-tjänstadministratörer kan masstilldela arbetsytor i Power BI-administratörsportalen. Masstilldelningar kan gälla för:

- **Arbetsytor av användare** -alla arbetsytor som ägs av dessa användare, inklusive personliga arbetsytor har tilldelats Premium-kapacitet. Detta inkluderar omtilldelning av arbetsytor när de redan är tilldelade till en annan Premium.kapacitet. Dessutom kan användare också tilldelas behörigheter för arbetsytetilldelning.

- **Särskilda arbetsytor**
- **Hela organisationens arbetsytor** -alla arbetsytor, inklusive personliga arbetsytor har tilldelats Premium-kapacitet. Alla nuvarande och framtida användare tilldelas behörigheter för arbetsytetilldelning. Den här metoden rekommenderas inte. En mer riktad metod är att föredra.

En arbetsyta kan läggas till en Premium-kapacitet med hjälp av fönstret **Arbetsyta** förutsatt att användaren är både administratör för en arbetsyta och har behörighet för kapacitetstilldelning.

![Använda fönstret arbetsyta för att tilldela en arbetsyta till en Premium-kapacitet](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Administratörer för arbetsytan kan ta bort en arbetsyta från en kapacitet (till en delad kapacitet) utan att behöva tilldelningsbehörighet. Ta bort arbetsytor från dedikerade kapaciteter flyttar effektivt arbetsytan till en delad kapacitet. Observera att ta bort en arbetsyta från en Premium-kapacitet kan ha negativa konsekvenser vilket till exempel resulterar i att delat innehåll skulle bli otillgängligt för Power BI Free-licensierade användare eller inaktivering av schemalagd uppdatering när de överskrider de tilldelningar som stöds av delade kapaciteter.

I Power BI-tjänsten identifieras en arbetsyta som tilldelats en Premium-kapacitet lätt via diamantikonen som pryder arbetsytans namn.

![Identifiera en arbetsyta som tilldelats en Premium-kapacitet](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Övervaka kapaciteter

Övervakning av Premium-kapaciteter ger administratörer en förståelse för hur kapaciteterna utförs. Kapaciteter kan övervakas med hjälp av Power BI-administratörsportalen eller **Power BI Premium-kapacitet** app (Power BI).

### <a name="power-bi-admin-portal"></a>Power BI-administratörsportalen

I administrationsportalen för varje kapacitet kan den **hälsotillstånd** fliken innehåller sammanfattning för kapaciteten och varje aktiverat arbetsbelastning. Mätningar visar ett genomsnitt under de senaste sju dagarna.  

På nivån kapacitet mått som är tillämpliga för alla aktiverade arbetsbelastningar. följande mått tillhandahålls:

- **CPU-belastning** -innehåller genomsnittlig processoranvändning i procent av total tillgänglig CPU för kapaciteten.  
- **MINNESANVÄNDNING** -ger genomsnittlig minnesanvändning (i GB) som en summa av det tillgängliga minnet för kapaciteten. 

För varje aktiverat arbetsbelastning tillhandahålls processoranvändning och minnesanvändning samt ett antal arbetsbelastning specifika mått. Till exempel för arbetsbelastningen dataflöde **Totalt antal** visar totalt antal uppdateringar för varje dataflöde och **Genomsnittlig varaktighet** visar den genomsnittliga varaktigheten för uppdatering för dataflödet.

![Kapacitet på fliken hälsa i portalen](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Läs mer om alla tillgängliga mått för varje arbetsbelastning i [övervaka kapaciteter i Admin portal](service-admin-premium-monitor-portal.md).

Övervakningsfunktionerna i Power BI-administratörsportalen är utformad att ge en snabb sammanfattning av viktiga kapacitetsmåtten. Mer detaljerad övervakning, bör du använda den **Power BI Premium-kapacitet** app.

### <a name="power-bi-premium-capacity-metrics-app"></a>Kapacitetsmåttappen för Power BI Premium

Den [Power BI Premium-kapacitet app](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) är en Power BI-appen som är tillgängligt för kapacitetsadministratörer och installeras som andra Power BI-appen. Den innehåller en instrumentpanel och rapport.

![Kapacitetsmåttappen för Power BI Premium](media/service-premium-capacity-manage/capacity-metrics-app.png)

När appen öppnas läses instrumentpanelen in för att presentera flera paneler som uttrycker en aggregerad vy över alla kapaciteter som användaren är kapacitetsadministratör för. Instrumentpanelens layout innehåller fem huvudområden:

- **Översikt över** -appversion, antal kapaciteter och arbetsytor
- **Systemöversikt** -minne och CPU-mått
- **Sammanfattning av datauppsättningen** - nummer för datauppsättningar, DQ/LC, uppdatera och fråga mått
- **Dataflöde sammanfattning** - nummer för dataflöden och datauppsättningen mått
- **Sidnumrerad Rapportsammanfattning** – uppdatera och visa mått

Den underliggande rapporten, varifrån instrumentpanelens paneler har fästs, kan nås genom att klicka på valfri panel på instrumentpanelen. Den ger en mer detaljerad översikt över vart och ett av instrumentpanelens avsnitt och stöder interaktiv filtrering. 

Filtrering kan uppnås genom att ange utsnitt efter datumintervall, kapacitet, arbetsyta och arbetsbelastning (rapport, datauppsättning, dataflöde) och genom att välja element i rapportens visuella objekt för att korsfiltrera rapportsidan. Korsfiltreringen är en kraftfull teknik för att begränsa till bestämda tidsperioder, kapaciteter, arbetsytor, datauppsättningar, etc. och kan vara mycket användbar när du utför rotorsaksanalys.

Detaljerad information om en instrumentpanel och rapport mätvärden i appen finns i [övervakaren Premium-kapaciteter med appen](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Tolka mått

Mått bör övervakas för att upprätta en grundläggande förståelse för resursanvändning och arbetsbelastningsaktivitet. Om kapaciteten blir långsam, är det viktigt att förstå vilka mått som ska övervakas och vilka slutsatser du kan dra.

Vi rekommenderar att frågor bör slutföras inom en sekund för att leverera dynamiska upplevelser till rapportanvändare och möjliggöra högre frågedataflöde. Det är vanligtvis mindre viktigt när bakgrundsprocesser, inklusive uppdateringar, tar längre tid att slutföra.

I allmänhet kan långsamma rapporter vara en indikation på en överhettad kapacitet. När det inte gick att läsa in rapporter, är det här en indikation på en överhettad kapacitet. I båda fallen kan rotorsaken tillskrivas många faktorer, bland annat:

- **Misslyckade frågor** indikerar verkligen minnesbelastning och att en modell inte kunde läsas in i minnet. Power BI-tjänsten kommer att försöka läsa in en modell i 30 sekunder innan åtgärden misslyckas.

- **Långa frågeväntetider** kan ha flera olika orsaker:
  - Behovet av Power BI-tjänsten till första avvisa modell(er) och sedan läsa in modellen till ska-fråga (återkallande att högre datauppsättning borttagning har enbart inte ingår priser en indikation på kapacitet stress utan att länge fråga väntetider som indikerar minnesförslöing).
  - Läs in modell tider (särskilt väntetiden på att läsa in en stor modellen i minnet).
  - Långvariga frågor.
  - För många LC\DQ anslutningar (överstiger kapacitetsbegränsningar).
  - Processormättnad till.
  - Komplexa rapporten layouter med många visuella objekt på en sida (återkallande att varje visuellt objekt är en fråga).

- **Långa frågevaraktigheter** kan tyda på att modellutformningarna inte är optimerade, särskilt när flera datauppsättningar är aktiva i en kapacitet och bara en datauppsättning ger långa frågevaraktigheter. Detta tyder på att kapaciteten är tillräckligt resurstilldelad och att datauppsättningen i fråga är icke-optimal eller bara långsam. Långvariga frågor kan vara problematiska eftersom de kan blockera åtkomst till resurser som krävs av andra processer.
- **Uppdatera länge väntetider** tyda på otillräckligt med minne på grund av många active modeller som förbrukar minne eller att en uppdatering av problematiska blockerar andra uppdaterar (överstiger parallella uppdatering begränsningar).

En mer detaljerad förklaring av hur du använder mått som beskrivs i den [optimera Premium-kapaciteter](service-premium-capacity-optimize.md) artikeln.

## <a name="acknowledgements"></a>Bekräftelser

Den här artikeln är skriven av Peter Myers, Data Platform MVP och oberoende BI-expert med [bitvis lösningar](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
> [Optimera Premium-kapaciteter](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Konfigurera arbetsbelastningar i en Premium-kapacitet](service-admin-premium-workloads.md)   

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

||||||
