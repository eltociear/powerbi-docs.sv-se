---
title: Felsöka XMLA-slutpunktsanslutning i Power BI Premium (förhandsversion)
description: Beskriver hur du felsöker anslutningar via XMLA-slutpunkten i Power BI Premium.
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 07/28/2020
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 8a815f69d4f74ec925c3ac0cc8a84c2a13d80346
ms.sourcegitcommit: a254f6e2453656f6783690669be8e881934e15ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363972"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>Felsöka anslutning för XMLA-slutpunkt

XMLA-slutpunkter i Power BI Premium förlitar sig på det interna Analysis Services-kommunikationsprotokollet för åtkomst till Power BI-datauppsättningar. På grund av detta är felsökning av XMLA-slutpunkter ungefär likadant som vid felsökning av en typisk Analysis Services-anslutning. Vissa skillnader kring Power BI-specifika beroenden gäller dock.

## <a name="before-you-begin"></a>Innan du börjar

Innan du felsöker ett XMLA-slutpunktsscenario bör du se igenom grunderna i [Datauppsättningsanslutning med XMLA-slutpunkt](service-premium-connect-tools.md). De vanligaste användningsfallen för XMLA-slutpunkter beskrivs där. Andra Power BI-felsökningsguider, till exempel [Felsöka gatewayer – Power BI](../connect-data/service-gateway-onprem-tshoot.md) och [Felsökningsanalys i Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md), kan också vara till hjälp.

## <a name="enabling-the-xmla-endpoint"></a>Aktivera XMLA-slutpunkten

XMLA-slutpunkten kan aktiveras på både Power BI Premium- och Power BI Embedded-kapaciteter. På mindre kapaciteter, till exempel en a1-kapacitet med bara 2,5 GB minne, kan du stöta på ett fel i kapacitetsinställningarna när du försöker ställa in XMLA-slutpunkten för att **läsa/skriva** och sedan välja **Tillämpa**. Felet säger ”Det uppstod ett problem med dina arbetsbelastningsinställningar. Försök igen om en liten stund.”.

Här är några saker du kan prova:

- Begränsa minnesförbrukningen för andra tjänster på kapaciteten, till exempel dataflöden till 40 % eller mindre, eller inaktivera en onödig tjänst helt.  
- Uppgradera kapaciteten till en större SKU. Om du till exempel uppgraderar från en A1- till en A3-kapacitet löser det konfigurationsproblemet utan att du behöver inaktivera dataflöden.

Kom ihåg att du även måste aktivera [Exportera datainställningen](service-premium-connect-tools.md#security) på klientnivå på Power BI Admin-portalen. Den här inställningen krävs också för funktionen Analysera i Excel.

## <a name="establishing-a-client-connection"></a>Upprätta en klientanslutning

När du har aktiverat XMLA-slutpunkten är det en bra idé att testa anslutningen till en arbetsyta på kapaciteten. Läs mer i [Ansluta till en Premium-arbetsyta](service-premium-connect-tools.md#connecting-to-a-premium-workspace). Se också till att läsa avsnittet [Anslutningskrav](service-premium-connect-tools.md#connection-requirements) för användbara tips och information om aktuella begränsningar för XMLA-anslutningen.

### <a name="connecting-with-a-service-principal"></a>Logga in med ett huvudnamn för tjänsten

Om du har aktiverat klientinställningar för att tillåta att tjänstens huvudnamn använder Power BI API:er, som det beskrivs i [Aktivera tjänstens huvudnamn](service-premium-service-principal.md#enable-service-principals) så kan du ansluta till en XMLA-slutpunkt genom att använda ett huvudnamn för tjänsten. Tänk på att tjänstens huvudnamn kräver samma behörighetsnivå på arbetsytan eller datauppsättningsnivån som vanliga användare.

Om du vill använda ett huvudnamn för tjänsten måste du ange programmets identitetsinformation i anslutningssträngen som:

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

Till exempel:

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

Om du får följande fel:

”Det går inte att ansluta till datauppsättningen på grund av ofullständig kontoinformation. För tjänstens huvudnamn, se till att du anger klient-ID tillsammans med app-ID med hjälp av formatappen:\<appId>@\<tenantId> och försök igen. "

Se till att du anger klient-ID tillsammans med app-ID med rätt format.

Det är också giltigt att ange app-ID utan klient-ID. I detta fall måste du dock ersätta `myorg`-aliaset i datakällans URL med faktiskt klient-ID. Power BI kan sedan hitta tjänstens huvudnamn i rätt klientorganisation. Men vi rekommenderar att du använder `myorg`-aliaset och anger klient-ID tillsammans med app-ID i User ID-parametern.

### <a name="connecting-with-azure-active-directory-b2b"></a>Ansluta med Azure Active Directory B2B

Med stöd för Azure Active Directory (Azure AD) Business-to-Business (B2B) i Power BI kan du ge externa gästanvändare åtkomst till datauppsättningar via XMLA-slutpunkten. Se till att inställningen [Dela innehåll med externa användare](service-admin-portal.md#export-and-sharing-settings) är aktiverad på Power BI-administratörsportalen. Läs mer i [Distribuera Power BI-innehåll till externa gästanvändare med Azure Active Directory B2B](service-admin-azure-ad-b2b.md).

## <a name="deploying-a-dataset"></a>Distribuera en datauppsättning

Du kan distribuera ett tabellmodellprojekt i Visual Studio (SSDT) till en Power BI Premium-arbetsyta på ungefär samma sätt som att distribuera till Azure Analysis Services. Men när du distribuerar till en Power BI Premium-arbetsyta finns det några ytterligare överväganden. Se till att granska avsnittet [Distribuera modellprojekt från Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt) i artikeln Datauppsättningsanslutning med XMLA-slutpunkt.

### <a name="deploying-a-new-model"></a>Distribuera en ny modell

I standardkonfigurationen försöker Visual Studio bearbeta modellen som en del av distributionsåtgärden för att läsa in data till datauppsättningen från datakällorna. Som det beskrivs i [Distribuera modellprojekt från Visual Studio (SSDT)](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt), kan den här åtgärden misslyckas eftersom autentiseringsuppgifter för datakällan inte kan anges som en del av distributionsåtgärden. Om autentiseringsuppgifterna för datakällan inte redan har definierats för någon av dina befintliga datauppsättningar, måste du i stället ange autentiseringsuppgifter för datakällan i datauppsättningens inställningar med hjälp av Power BI-användargränssnittet (**Datauppsättningar** > **Inställningar** > **Autentiseringsuppgifter för datakälla** > **Redigera autentiseringsuppgifter**). När du har definierat autentiseringsuppgifterna för datakällan kan Power BI sedan använda autentiseringsuppgifterna för datakällan automatiskt för nya datauppsättningar, efter att metadatadistributionen har slutförts och datauppsättningen har skapats.

Om Power BI inte kan binda din nya datauppsättning till autentiseringsuppgifter för datakällan så får du felmeddelandet ”Det går inte att bearbeta databasen. Orsak: Det gick inte att spara ändringarna på servern.” med felkoden DMTS_DatasourceHasNoCredentialError, som du ser nedan:

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="Modelldistributionsfel":::

Du undviker bearbetningsfelet genom att ange **Distributionsalternativ** > **Bearbetningsalternativ** till **Bearbeta inte**, som du ser i följande bild. Visual Studio distribuerar därefter bara metadata. Du kan sedan konfigurera autentiseringsuppgifterna för datakällan och klicka på **Uppdatera nu** för datauppsättningen i Power BI-användargränssnittet. Information om hur du felsöker bearbetningsproblem finns i avsnittet [Uppdatera en datauppsättning](#refreshing-a-dataset) längre fram i den här artikeln.

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="Bearbeta inte-alternativet":::

### <a name="new-project-from-an-existing-dataset"></a>Nytt projekt från en befintlig datauppsättning

Skapa ett nytt tabellprojekt i Visual Studio genom att importera metadata från en befintlig datauppsättning i en Power BI Premium-arbetsyta stöds inte. Du kan dock ansluta till datauppsättningen genom att använda SQL Server Management Studio, skripta ut metadata och återanvänd det i andra tabellprojekt.

## <a name="migrating-a-dataset-to-power-bi"></a>Migrera en datauppsättning till Power BI

Vi rekommenderar att du anger kompatibilitetsnivån på 1500 (eller högre) för tabellmodeller. Den här kompatibilitetsnivån stöder de flesta kompatibiliteter och typer av datakällor. Senare kompatibilitetsnivåer är bakåtkompatibla med tidigare nivåer.

### <a name="supported-data-providers"></a>Dataleverantörer som stöds

Vid kompatibilitetsnivå 1500 stöder Power BI följande datakällstyper:

- Leverantörsdatakällor (äldre med en anslutningssträng i modellens metadata).
- Strukturerade datakällor (som introducerades med kompatibilitetsnivå 1400).
- Infogade M-deklarationer för datakällor (som Power BI Desktop deklarerar dem).

Vi rekommenderar att du använder strukturerade datakällor som Visual Studio skapar som standard när du går igenom Importera data-flödet. Men om du planerar att migrera en befintlig modell till Power BI som använder en providers datakälla, kontrollerar du att providerns datakälla förlitar sig på en dataleverantör som stöds. Mer specifikt OLE DB-drivrutinen för SQL Server och eventuella ODBC-drivrutiner från tredje part. För OLE DB-drivrutiner för SQL Server så måste du byta datakällans definition till .NET Framework Data Provider för SQL Server. För ODBC-drivrutiner från tredje part som kanske inte är tillgängliga i Power BI-tjänsten så måste du växla till en strukturerad datakällsdefinition i stället.

Det rekommenderas även att du byter ut den utdaterade Microsoft OLE DB-drivrutinen för SQL Server (SQLNCLI11) i dina SQL Server-datakällsdefinitioner mot .NET Framework Data Provider för SQL Server.

Följande tabell ger ett exempel där en .NET Framework Data Provider för SQL Server-anslutningssträng ersätter en motsvarande anslutningssträng för OLE DB-drivrutinen för SQL Server.

|OLE DB-drivrutin för SQL Server  |.NET Framework Data Provider för SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>Korsreferera partitionskällor

Precis som det finns flera typer av datakällor så finns det också flera olika partitionskälltyper som en tabellmodell kan innehålla för att importera data till en tabell. Mer specifikt kan en partition använda en frågepartitionskälla eller en M-partitionskälla. De här partitionstyperna kan i sin tur referera till providerdatakällor eller strukturerade datakällor. Medan tabellmodeller i Azure Analysis Services stöder korsreferenser till dessa olika datakäll- och partitionstyper, framtvingar Power BI en mer strikt relation. Frågepartitionskällor måste referera till providerns datakällor och M-partitionens källor måste referera till strukturerade datakällor. Andra kombinationer stöds inte i Power BI. Om du vill migrera en korsrefererande datauppsättning beskriver följande tabell de konfigurationer som stöds:  

|Datakälla   |Partitionskälla   |Kommentarer   |Stöds i Power BI Premium med XMLA-slutpunkt   |
|---------|---------|---------|---------|
|Providerdatakälla      |   Frågepartitionskälla      |   AS-motorn använder den kassettbaserade anslutningsstacken för att komma åt datakällan.       |     Ja     |
|Providerdatakälla      |   M-partitionskälla       |   AS-motorn översätter providerdatakällan till en generisk strukturerad datakälla och använder sedan mashup-motorn för att importera data.       |    Nej     |
|Strukturerad datakälla      |     Frågepartitionskälla     |    AS-motorn omsluter den interna frågan på partitionskällan till ett M-uttryck och använder sedan mashup-motorn för att importera data.      |    Nej     |
|Strukturerad datakälla      |    M-partitionskälla      |     AS-motorn använder mashup-motorn för att importera data.     |   Ja      |

## <a name="refreshing-a-dataset"></a>Uppdatera en datauppsättning

Med XMLA-slutpunkter kan du utföra uppdateringsåtgärder mot tabellmodeller samt datauppsättningar som skapats i Power BI Desktop. För att stödja den senare, se till att du anger inställningen förbättrat lagringsformat. Den här inställningen krävs om du vill utföra bearbetning eller andra läs-/skrivåtgärder med hjälp av XMLA-slutpunkten. Du hittar inställningen i Power BI Desktop under förhandsfunktionergranskningsfunktioner. När du har angett det så publicerar du PBIX-lösningen igen till din Power BI Premium-arbetsyta.  

Power BI returnerar följande fel om du kör en uppdatering via XMLA-slutpunkten mot en modell utan förbättrade metadata: ”Åtgärden stöds bara för modellen med egenskapen DefaultPowerBIDataSourceVersion inställd till PowerBI_V3 i Power BI Premium.”

### <a name="data-sources-and-impersonation"></a>Datakällor och personifiering

Personifieringsinställningarna som du kan definiera för providerdatakällorna är inte relevanta för Power BI. Power BI använder en annan mekanism baserat på datauppsättningsinställningarna för att hantera autentiseringsuppgifter för datakällan. Därför bör du kontrollera att du väljer **Tjänstkonto** om du skapar en providerdatakälla.

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="Personifiera tjänstkonto":::

### <a name="fine-grained-processing"></a>Detaljerad bearbetning

När du utlöser en schemalagd uppdatering eller uppdatering på begäran i Power BI så uppdaterar Power BI vanligtvis hela datauppsättningen. I många fall är det mer effektivt att utföra uppdateringar mer selektivt. Du kan utföra detaljerade bearbetningsuppgifter i SQL Server Management Studio (SSMS) som visas nedan eller med hjälp av verktyg eller skript från tredje part.

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="Bearbeta tabeller i SSMS":::

### <a name="overrides-in-refresh-tmsl-command"></a>Åsidosättningar i uppdatera-kommandot för TMSL

Med åsidosättningar i [uppdatera-kommandot (TMSL)](https://docs.microsoft.com/analysis-services/tmsl/refresh-command-tmsl) kan användare välja en annan partitionsfrågedefinition eller datakälldefinition för uppdateringsåtgärden. **Åsidosättningar stöds för närvarande inte** i Power BI Premium. Ett fel – ”Filslutsbindningar kan inte användas i Power BI Premium. Mer information finns i ”support för XMLA-läsa/skriva” i produktdokumentationen.” returneras.

## <a name="see-also"></a>Se även

[Anslutning av datauppsättning med XMLA-slutpunkten](service-premium-connect-tools.md)   
[Automatisera Premium arbetsyte- och datauppsättningsåtgärder med hjälp av tjänstens huvudnamn](service-premium-service-principal.md)   
[Felsöka Analysera i Excel](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)   
[Distribution av lösning för tabellmodell](https://docs.microsoft.com/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current)
