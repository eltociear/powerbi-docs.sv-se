---
title: Migrera SQL Server Reporting Services-rapporter till Power BI
description: Vägledning som hjälper dig att migrera dina SSRS-rapporter (SQL Server Reporting Services) till Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/03/2020
ms.author: v-pemyer
ms.openlocfilehash: 06bff0a199db9955f11487a05ba78268bb8a942d
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561603"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>Migrera SQL Server Reporting Services-rapporter till Power BI

Den här artikeln är avsedd för personer som skriver SSRS-rapporter (SQL Server Reporting Services) och Power BI-administratörer. Det ger vägledning som hjälper dig att migrera dina [RDL-rapporter (Report Definition Language)](/sql/reporting-services/reports/report-definition-language-ssrs) till Power BI.

> [!NOTE]
> Du kan bara migrera RDL-rapporter. I Power BI kallas RDL-rapporter för _sidnumrerade rapporter_.

Vägledningen är indelad i fyra steg. Vi rekommenderar att du läser hela artikeln innan du börjar migrera dina rapporter.

1. [Innan du börjar](#before-you-start)
1. [Förmigreringssteget](#pre-migration-stage)
1. [Migreringssteget](#migration-stage)
1. [Eftermigreringssteget](#post-migration-stage)

Du kan migrera utan driftavbrott för SSRS-servrarna eller att störa dina rapportanvändare. En viktig sak att förstå är att du inte behöver ta bort några data eller rapporter. Det innebär att du kan behålla den nuvarande miljön tills du är redo att dra tillbaka den.

## <a name="before-you-start"></a>Innan du börjar

Innan du startar migreringen bör du kontrollera att din miljö uppfyller vissa krav. Vi så gå igenom de här förutsättningarna och även presentera ett användbart migreringsverktyg.

### <a name="preparing-for-migration"></a>Förberedelse för migreringen

När du förbereder dig inför migreringen av dina rapporter till Power BI ska du först kontrollera att organisationen har en [Power BI Premium](../admin/service-premium-what-is.md)-prenumeration. Du behöver en sådan prenumeration för att lagra och köra dina sidnumrerade Power BI-rapporter.

### <a name="supported-versions"></a>Versioner som stöds

Du kan migrera SSRS-instanser som körs lokalt eller på virtuella datorer som körs av molnleverantörer som Azure.

I den här listan ser du vilka SQL Server-versioner som stöds för migrering till Power BI:

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

Du kan även migrera från Power BI-rapportserver.

### <a name="migration-tool"></a>Migreringsverktyg

Vi rekommenderar att du använder [verktyget RDL Migration](https://github.com/microsoft/RdlMigration) till att förbereda och migrera dina rapporter. Microsoft har utvecklat det här verktyget som hjälp för kunder som ska migrera RDL-rapporter från sina SSRS-servrar till Power BI. Du hittar det på GitHub tillsammans med dokumentation för ett komplett migreringsscenario.

De här uppgifterna sköts automatiskt i verktyget:

* Det söker efter [datakällor](../paginated-reports/paginated-reports-data-sources.md) och [rapportfunktioner](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) som inte stöds
* Det konverterar eventuella _delade_ resurser till _inbäddade_ resurser:
  * delade **datakällor** blir inbäddade datakällor
  * delade **datamängder** blir inbäddade datamängder.
* Det publicerar rapporter (som passerar kontroller) som sidnumrerade rapporter till en angiven Power BI-arbetsyta (i en Premium-kapacitet)

Det modifierar inte och tar inte bort några befintliga rapporter. När verktyget har slutförts visas en sammanfattning av alla åtgärder som körts, både de som utförts och de som misslyckats.

Microsoft kan göra förbättringar i verktyget med tiden. Communityn uppmuntras också att bidra och hjälpa till.

## <a name="pre-migration-stage"></a>Förmigreringssteget

När du har verifierat att din organisation uppfyller förutsättningarna är du redo att starta _förmigreringssteget_. Det här steget består av tre faser:

1. Utforska
1. Utvärdera
1. Förbereda

### <a name="discover"></a>Utforska

Målet i steget _Utforska_ är att identifiera dina befintliga SSRS-instanser. I den här processen ingår att genomsöka nätverket och identifiera alla SQL Server-instanser i organisationen.

Du kan använda [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826). Det här kallas även för ett ”MAP-verktyg”, som identifierar och rapporterar dina SQL Server-instansers version och installerade funktioner. Det är ett kraftfullt verktyg för inventering, utvärdering och rapportering som gör din migreringsplanering enklare.

### <a name="assess"></a>Utvärdera

När du har identifierat dina SSRS-instanser är målet i fasen _Utvärdera_ att förstå vilka SSRS-rapporter, eller serverobjekt, som inte kan migreras.

Du kan bara migrera RDL-rapporter från SSRS-servrar till Power BI. Varje migrerad RDL-rapport blir till en sidnumrerad Power BI-rapport.

De här SSRS-objekttyperna kan du dock inte migrera till Power BI:

- Delade datakällor <sup>1</sup>
- Delade datamängder <sup>1</sup>
- Resurser, som bildfiler
- KPI:er (SSRS 2016 eller senare – endast Enterprise Edition)
- Mobila rapporter (SSRS 2016 eller senare – endast Enterprise Edition)
- Rapportmodeller (inaktuella)
- Rapportdelar (inaktuella)

<sup>1</sup> [Verktyget RDL Migration](https://github.com/microsoft/RdlMigration) konverterar automatiskt delade datakällor och datamängder förutsatt att de använder datakällor som stöds.

Om dina RDL-rapporter använder funktioner som [ännu inte stöds i sidnumrerade Power BI-rapporter](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) kan du planera att utveckla dem på nytt som [Power BI-rapporter](../consumer/end-user-reports.md). Även om det går att migrera dina RDL-rapporter så rekommenderar vi att du överväger att modernisera dem till Power BI-rapporter om det går.

Om dina RDL-rapporter behöver hämta data från _lokala datakällor_ kan de inte använda enkel inloggning (SSO). För närvarande görs alla datahämtningar från dessa källor med hjälp av säkerhetskontexten för _Gateway-datakällans användarkonto_. Det är inte möjligt för SQL Server Analysis Services (SSAS) att framtvinga säkerhet på radnivå (RLS) per användare.

Sidnumrerade Power BI-rapporter är i allmänhet optimerade för **utskrift** eller **PDF-generering**. Power BI-rapporter är optimerade för **utforskning och interaktivitet**. Läs mer i [Använda sidnumrerade rapporter i Power BI](report-paginated-or-power-bi.md).

### <a name="prepare"></a>Förbereda

Målet i fasen _Förbereda_ är att göra allting redo. Det är här du konfigurerar Power BI-miljön, planerar hur du ska skydda och publicera dina rapporter och tänker igenom hur du ska utveckla om SSRS-objekt som inte går att migrera.

1. Se till att [arbetsbelastningen Sidnumrerade rapporter](../admin/service-admin-premium-workloads.md#paginated-reports) är aktiverad för din Power BI Premium-kapacitet och att den har tillräckligt med minne.
1. Kontrollera att det finns stöd för dina rapporters [datakällor](../paginated-reports/paginated-reports-data-sources.md) och konfigurera en [Power BI-gateway](../connect-data/service-gateway-onprem.md) för anslutning till eventuella lokala datakällor.
1. Bekanta dig med säkerheten i Power BI och planera [hur du ska återskapa dina SSRS-mappar och tillhörande behörigheter](/sql/reporting-services/security/secure-folders) som [arbetsytor och arbetsyteroller i Power BI](../collaborate-share/service-new-workspaces.md).
1. Bekanta dig med delning i Power BI och planera hur du ska distribuera innehåll genom att publicera [Power BI-appar](../collaborate-share/service-create-distribute-apps.md).
1. Överväg att använda [delade Power BI-datamängder](../connect-data/service-datasets-build-permissions.md) i stället för dina delade SSRS-datakällor.
1. Använd [Power BI Desktop](../fundamentals/desktop-what-is-desktop.md) till att utveckla rapporter optimerade för mobila enheter, eventuellt med hjälp av [det anpassade visuella objektet Power KPI](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview) i stället för dina mobila rapporter och KPI:er i SSRS.
1. Utvärdera användningen av det inbyggda fältet **UserID** i dina rapporter igen. Om du förlitar dig på **UserID** för att skydda rapportdata, bör du känna till att för sidnumrerade rapporter (om de finns i Power BI-tjänsten) returneras användarhuvudnamnet (UPN). I stället för att returnera NT-kontonamnet, till exempel _AW\mblythe_, kommer det inbyggda fältet att returnera något som _m.blythe&commat;adventureworks.com_. Du måste ändra dina datauppsättningsdefinitioner och eventuellt källdata. När du har ändrat och publicerat rekommenderar vi att du testar dina rapporter noggrant för att säkerställa att databehörigheter fungerar som förväntat.
1. Utvärdera användningen av det inbyggda fältet **ExecutionTime** i dina rapporter igen. För sidnumrerade rapporter (när de finns i Power BI-tjänsten) returnerar det inbyggda fältet datum/tid _i UTC (Coordinated Universal Time)_ . Det kan påverka rapportparameterns standardvärden och etiketter för rapportkörningstid (som vanligtvis läggs till i rapport med sidfot).
1. Om datakällan är SQL Server (lokalt) kontrollerar du att rapporterna inte använder kartvisualiseringar. Kartvisualiseringar är beroende av rumsliga SQL Server-datatyper som inte stöds av gatewayen. Mer information finns i [Guide till datahämtning för sidnumrerade rapporter (komplexa SQL Server-datatyper)](report-paginated-data-retrieval.md#sql-server-complex-data-types).
1. Se till att rapportförfattarna har [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md) installerat och att de senare versionerna enkelt kan distribueras i hela organisationen.

## <a name="migration-stage"></a>Migreringssteget

När du har förberett Power BI-miljön och dina rapporter är du redo för _migreringssteget_.

Det finns två migreringsalternativ: _manuell_ och _automatisk_. Manuell migrering passar om du har ett litet antal rapporter eller rapporter som måste ändras innan migreringen. Automatisk migrering passar när du ska migrera ett stort antal rapporter.

### <a name="manual-migration"></a>Manuell migrering

Alla som har behörighet att komma åt SSRS-instansen och Power BI-arbetsytan kan migrera rapporter manuellt till Power BI. Gör så här:

1. Öppna SSRS-portalen som innehåller de rapporter du vill migrera.
1. Ladda ned varje rapportdefinition och spara .rdl-filerna lokalt.
1. Öppna _den senaste versionen_ av Power BI Report Builder och anslut till Power BI-tjänsten med dina autentiseringsuppgifter för Azure AD.
1. Öppna varje rapport i Power BI Report Builder och gör följande:
   1. Kontrollera att alla datakällor och datamängder är inbäddade i rapportdefinitionen och att de är [datakällor som stöds](../paginated-reports/paginated-reports-data-sources.md).
   1. Förhandsgranska rapporten för att se om den återges korrekt.
   1. Välj alternativet _Spara som_ och sedan _Power BI-tjänst_.
   1. Välj på vilken arbetsyta som rapporten ska ligga.
   1. Kontrollera att rapporten sparas. Om vissa funktioner i rapportdesignen inte stöds än kan du inte spara rapporten. Du får ett meddelande om anledningen. I så fall måste du göra om rapportdesignen och försöka spara rapporten igen.

### <a name="automated-migration"></a>Automatisk migrering

Det finns två alternativ för automatisk migrering. Du kan använda:

- Verktyget RDL Migration
- De allmänt tillgängliga API:erna för SSRS och Power BI

[Verktyget RDL Migration](#migration-tool) har redan beskrivits i den här artikeln.

Du kan också använda de allmänt tillgängliga API:erna för SSRS och Power BI till att automatisera migreringen av ditt innehåll. Även om de här API:erna redan används i verktyget RDL Migration så kan du skapa ett eget verktyg som passar just dina behov.

Du kan läsa mer om API:erna i de här resurserna:

- [Power BI REST API-referens](../developer/automation/rest-api-reference.md)
- [REST-API:er för SQL Server Reporting Services](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>Eftermigreringssteget

När du har slutfört migreringen är du redo för _eftermigreringssteget_. I det här steget ingår att gå igenom en serie uppgifter efter migreringen som säkerställer att allt fungerar som det ska.

### <a name="configure-data-sources"></a>Konfigurera datakällor

När du har migrerat rapporter till Power BI måste du se till att datakällorna är korrekt konfigurerade. Du kan behöva tilldela datakällor till gatewayer och ordna med [säker lagring av autentiseringsuppgifter för datakällor](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication). De här åtgärderna utförs inte i verktyget RDL Migration.

### <a name="review-report-performance"></a>Granska rapportprestanda

Vi rekommenderar att du utför följande åtgärder för att ge rapportanvändarna bästa möjliga upplevelse:

1. Testa rapporterna i alla [webbläsare som stöds av Power BI](../fundamentals/power-bi-browsers.md) och kontrollera att rapporten återges korrekt.
1. Kör tester för att jämföra rapportens återgivningstider i SSRS och Power BI. Kontrollera att Power BI-rapporter återges rimligt snabbt.
1. Om Power BI-rapporterna inte går att återge på grund av otillräckligt minne ska du allokera [ytterligare resurser till din Power BI Premium-kapacitet](../admin/service-admin-premium-workloads.md#paginated-reports).
1. För rapporter som tar lång tid att återge kan du överväga att låta Power BI leverera dem till rapportanvändarna som [e-postprenumerationer med rapportbilagor](../consumer/paginated-reports-subscriptions.md).
1. För Power BI-rapporter som baseras på Power BI-datamängder ska du granska modelldesignen så att den är helt optimerad.

### <a name="reconcile-issues"></a>Lösa problem

Eftermigreringsfasen är viktig när det gäller att lösa eventuella fel och åtgärda prestandaproblem. Att lägga till arbetsbelastningen för sidnumrerade rapporter i en kapacitet kan leda till långsamma prestanda, både för de sidnumrerade  rapporterna _och för annat innehåll_ i kapaciteten.

Du kan läsa mer om de här problemen och se hur du bättre kan förstå och lösa dem, i följande artiklar:

- [Optimera Premium-kapaciteter](../admin/service-premium-capacity-optimize.md)
- [Övervaka Premium-kapaciteter i appen](../admin/service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Vad är sidnumrerade rapporter i Power BI Premium?](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Guide till datahämtning i sidnumrerade rapporter](report-paginated-data-retrieval.md)
- [Använda sidnumrerade rapporter i Power BI](report-paginated-or-power-bi.md)
- [Sidnumrerade rapporter i Power BI: Vanliga frågor och svar](../paginated-reports/paginated-reports-faq.md)
- [Nätbaserad kurs: Sidnumrerade rapporter på en dag](../learning-catalog/paginated-reports-online-course.md)
- [Vanliga frågor och svar om Power BI Premium](../admin/service-premium-faq.md)
- [Verktyget RDL Migration](https://github.com/microsoft/RdlMigration)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com)

Våra Power BI-partners finns där och kan hjälpa din organisation att lyckas med migreringsprocessen. Om du vill kontakta en Power BI-partner går du till [partnerportalen för Power BI](https://powerbi.microsoft.com/partners/).
