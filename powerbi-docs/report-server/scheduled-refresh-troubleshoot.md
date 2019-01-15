---
title: Felsöka schemalagd uppdatering i Power BI Report Server
description: I den här artikeln beskrivs de resurser som är tillgängliga för att felsöka problem genom schemalagd uppdatering i Power BI-rapportservern.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 3aa4047f5a4b0146c534a5734d8d13a42c46fe58
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54287817"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>Felsöka schemalagd uppdatering i Power BI Report Server
I den här artikeln beskrivs de resurser som är tillgängliga för att felsöka problem genom schemalagd uppdatering i Power BI-rapportservern.

I takt med att nya problem dyker upp, så uppdateras den här artikeln med information som kan vara till hjälp.

## <a name="common-issues"></a>Vanliga problem
Här följer några vanliga problem som du lär stöta på när du försöker schemalägga rapportuppdatering. 

### <a name="driver-related-problems"></a>Drivrutinsrelaterade problem
Att ansluta till olika datakällor kan kräva drivrutiner från tredje part som måste installeras för att det ska gå att ansluta. Inte nog med att du skulle behöva installera dem på den dator som du använder Power BI Desktop på, utan du måste också kontrollera att drivrutinen har installerats på rapportservern.

Drivrutinen kan förekomma i både 32- och 64-bitarsversion. Se till att du installerar 64-bitarsdrivrutinen, eftersom Power BI-rapportservern är 64-bitars.

Läs tillverkarens information om hur du ska installera och konfigurera drivrutiner från tredje part.

### <a name="memory-pressure"></a>Minnesbelastning
Minnesbelastning kan inträffa när rapporter kräver mer minne för att de ska kunna bearbetas och återges. Schemaläggning av rapportuppdateringar kan kräva mycket minne på datorn. Detta gäller i synnerhet större rapporter. Minnesbelastning kan resultera i rapportfel samt i värsta fall till att rapportservern kraschar.

Om du påträffar minnesbelastning vid upprepade tillfällen, kan det vara värt att titta på en utskalad distribution av rapportservern, så att belastningen sprids över flera resurser. Du kan också ange att en viss rapportserver ska användas för datauppdatering med inställningen `IsDataModelRefreshService` i rsreportserver.config. Med den här inställningen kan du definiera att en eller flera servrar ska fungera som frontserver och hantera rapporter på begäran, och att en annan uppsättning servrar endast ska användas för schemalagd uppdatering.

Information om hur du övervakar en Analysis Services-instans finns i [Övervaka en Analysis Services-instans](https://docs.microsoft.com/sql/analysis-services/instances/monitor-an-analysis-services-instance).

Information om inställningar för minne i Analysis Services finns i [Minnesegenskaper](https://docs.microsoft.com/sql/analysis-services/server-properties/memory-properties).

### <a name="kerberos-configuration"></a>Kerberos-konfiguration
Att ansluta till en datakälla med Windows-autentiseringsuppgifter kan kräva att du måste konfigurera Kerberos-begränsad delegering för att kunna upprätta en anslutning. Mer information om hur du konfigurerar Kerberos-begränsad delegering finns i [Konfigurera Kerberos för användning med Power BI-rapporter](configure-kerberos-powerbi-reports.md).

## <a name="known-issues"></a>Kända problem
Information om kända problem listas här när de blir tillgängliga.

## <a name="configuration-settings"></a>Konfigurationsinställningar
Du kan använda följande inställningar för att påverka schemalagd uppdatering. Inställningar som anges i SQL Server Management Studio (SSMS) gäller för alla rapportservrar i en utskalningsdistribution. Inställningar som konfigurerats i rsreportserver.config avser den specifika server där de har angetts.

**Inställningar i SSMS:**

| Inställning | Beskrivning |
| --- | --- |
| MaxFileSizeMb |Maximal storlek för överförda rapporter. Standardvärdet är 1 000 MB (1 GB). Högsta värdet är 2 000 MB (2 GB). |
| ModelCleanupCycleMinutes |Definierar hur ofta modellen kontrolleras för att ta bort den från minnet. Standardvärdet är 15 minuter. |
| ModelExpirationMinutes |Definierar hur länge det dröjer tills modellen förfaller baserat på den senaste gången den användes och avlägsnades. Standardvärdet är 60 minuter. |
| ScheduleRefreshTimeoutMinutes |Definierar hur länge datauppdateringen kan ta för ett läge. Standardvärdet är 120 minuter. Det finns ingen övre gräns. |

**Inställningar i rsreportserver.config:**

```
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>Verktyg för felsökning
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Loggar som är relevanta för schemalagd uppdatering i Power BI-rapporter
De loggfiler som innehåller information om schemalagd uppdatering är RSPowerBI_ logs. De finns i mappen LogFiles på platsen för din rapportserverinstallation. 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**Feltillstånd**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

***Lyckad uppdatering***

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

**Felaktiga autentiseringsuppgifter**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>Aktivera utförlig loggning
I Power BI Report Server innebär aktivering av utförlig loggning detsamma som för SQL Server Reporting Services.

1. Öppna `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`.
2. Ändra **DefaultTraceSwitch** till **4** under `<system.diagnostics>`.
3. Ändra **Components** till **all: 4** under `<RStrace>`. 

### <a name="executionlog"></a>ExecutionLog
Varje gång som en Power BI-rapport återges, eller en schemalagd uppdateringsplan körs, läggs nya poster till i körningsloggen i databasen. Dessa poster är tillgängliga i **ExecutionLog3**-vyn i rapportserverdatabasens katalog.

Körningsloggsposter för Power BI-rapporter skiljer sig från poster för andra rapporttyper.

* TimeRendering-kolumner är alltid 0. Återgivningen av Power BI-rapporter sker i webbläsaren, inte på servern.
* Det finns 2 förfrågningstyper och efterföljande åtgärder:
  * **Interactive**: varje gång som en rapport visas.
    * **ASModelStream**: när datamodellen strömmas till Analysis Services från katalogen.
    * **ConceptualSchema**: när användaren klickar för att visa rapporten.
    * **QueryData**: när data begärs från klienten.
  * **Refresh Cache**: när en schemauppdateringsplan har körts.
    * **ASModelStream**: när datamodellen strömmas till Analysis Services från katalogen.
    * **DataRefresh**: när data uppdateras från en eller flera datakällor.
    * **SaveToCatalog**: när datamodellen sparas i katalogen.

## <a name="analysis-services"></a>Analysis Services
Det kan finnas tilllfällen då du vill ändra Analysis Services när det gäller diagnosproblem eller när du vill justera minnesgränserna.

> [!IMPORTANT]
> De här inställningarna återställs nästa gång du uppgraderar rapportservern. Se till att behålla en kopia av dina ändringar och återtillämpa dem om det behövs.
> 
> 

### <a name="install-location"></a>Installationsplats
Standardplatsen för Power BI Report Server och Analysis Services är följande.

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>Konfigurera Analysis Services-inställningar (msmdsrv.ini)
I `<install directory>\PBIRS\ASEngine`-katalogen hittar du filen *msmdsrv.ini*, som du kan använda för att styra olika Analysis Services-inställningar. När du öppnar den här filen kommer du omedelbart att upptäcka att filen inte innehåller alla de inställningar som du förväntar dig i filen. 

Detta beror på att den faktiska Analysis Services-process som körs av Power BI Report Server har startats i `<install directory>\PBIRS\ASEngine\workspaces`. I den mappen hittar du hela den *msmdsrv.ini*-fil som du är van vid. Det är viktigt att du inte ändra filen i arbetsytemappen, eftersom den skrivs om varje gång som Analysis Services-processen startar. Om du vill kontrollera en inställning, så gör det genom att ändra msmdsrv.ini i `<install directory>\PBIRS\ASEngine`-katalogen.

Följande inställningar återställs varje gång som Analysis Services-processen startas. Alla ändringar du gör här ignoreras.

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>Profilera den lokala Analysis Services-processen
Du kan köra ett SQL Profiler-spår i den lokala Analysis Services-processen i diagnostiskt syfte. Anslut till den lokala Analysis Services-instansen genom att göra följande.

SQL Server Profiler-spåret ingår i [SQL Server Management Studio (SSMS)-nedladdningen](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

1. Starta **SQL Server Profiler** som administratör.
2. Välj knappen **Nytt spår**.
3. Markera **Analysis Services** i dialogrutan **Anslut till server** och ange **localhost:5132** som servernamn.
4. Markera de händelser som du vill fånga och välj **Kör** i dialogrutan **Spåra egenskaper**.

## <a name="lock-pages-in-memory-windows-privilege"></a>Windows-behörigheten Låsa sidor i minnet
Om du märker att det inte går att återge en Power BI-rapport kan det underlätta om du tilldelar det tjänstkonto som kör Power BI-rapportservern privilegiet **Låsa sidor i minnet**. Mer information om hur du konfigurerar **Låsa sidor i minnet** finns i [Windows-privilegier för Analysis Services-tjänstkontot](https://docs.microsoft.com/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv).

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

