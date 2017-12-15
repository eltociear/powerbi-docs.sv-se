---
title: Nyheter i Power BI-rapportserver
description: "Läs mer om nyheterna i Power BI-rapportserver. Detta omfattar de viktiga funktionsområdena och uppdateras när nya objekt släpps."
services: powerbi
documentationcenter: 
author: guyinacube
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
ms.date: 10/31/2017
ms.author: asaxton
ms.openlocfilehash: d351a117307e86c7b0750e9bcdf813b08b28bb0f
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="whats-new-in-power-bi-report-server"></a>Nyheter i Power BI-rapportserver
Läs mer om nyheterna i Power BI-rapportserver. Detta omfattar de viktiga funktionsområdena och uppdateras när nya objekt släpps.

Om du vill ladda ned Power BI-rapportservern och Power BI Desktop som är optimerat för Power BI-rapportserver, går du till [Lokal rapportering med Power BI-rapportserver](https://powerbi.microsoft.com/report-server/).

![tips](media/whats-new/fyi-tip.png "tips") Aktuell viktig information finns i [Power BI-rapportserver – viktig information](release-notes.md).

Relaterad information om nyheter finns i:

* [Nyheter i Power BI-tjänsten](../service-whats-new.md)
* [Nyheter i Power BI Desktop](../desktop-latest-update.md)
* [Nyheter i mobilapparna för Power BI](../mobile-whats-new-in-the-mobile-apps.md)
* [Power BI-teamets blogg](https://powerbi.microsoft.com/blog/)

## <a name="october-2017-release"></a>Version oktober 2017
### <a name="power-bi-report-data-sources"></a>Rapportdatakällor i Power BI
Power BI-rapporterna i Power BI-rapportserver kan ansluta till en mängd olika datakällor. Du kan importera data och schemalägga datauppdateringar, eller fråga efter det direkt med DirectQuery eller en live-anslutning till SQL Server Analysis Services. Se listan med datakällor som stöder schemalagd uppdatering och de som stöder DirectQuery i ”Power BI:s rapportdatakällor i Power BI-rapportserver”.

### <a name="scheduled-data-refresh-for-imported-data"></a>Schemalagd datauppdatering för importerade data
I Power BI-rapportserver kan du ställa in schemalagda datauppdateringar för att dina data ska vara uppdaterade i Power BI-rapporter med en inbäddad modell i stället för en live-anslutning eller DirectQuery. Med en inbäddad modell importerar du data, så den är inte ansluten till den ursprungliga datakällan. Den måste uppdateras för att hålla data uppdaterade och det gör man med en schemalagd uppdatering. Läs mer om ”schemalagd uppdatering för Power BI-rapporter i Power BI-rapportserver”.

### <a name="editing-power-bi-reports-from-the-server"></a>Redigera Power BI-rapporter från servern
Du kan öppna och redigera Power BI-rapportfiler (.pbix) från servern, men du kommer tillbaka till den ursprungliga fil som du överförde.  Det innebär att **om datan har uppdaterats av servern kommer den inte uppdateras när du först öppnar filen**. Du måste uppdatera den lokalt manuellt för att se ändringen.

### <a name="large-file-uploaddownload"></a>Uppladdning/nedladdning av stora filer
Du kan ladda upp filer upp till 2 GB i storlek, även om den här gränsen som standard är 1 GB i rapportserverinställningarna i SQL Server Management Studio (SSMS).  De här filerna lagras i databasen på samma sätt som för SharePoint och det krävs ingen särskild konfiguration för SQL Server-katalogen.  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>Åtkomst till delade datauppsättningar som OData-flöden
Du kan komma åt delade datauppsättningar från Power BI Desktop med ett OData-flöde. Mer information finns i [Åtkomst till delade datauppsättningar som OData-flöden i Power BI-rapportserver](access-dataset-odata.md).

### <a name="scale-out"></a>Utskalning
Den här versionen stöder utskalning. Använd en belastningsutjämnare och ange servertillhörighet för bästa möjliga resultat. Observera att scenariot ännu inte har optimerats för utskalning, så du kommer eventuellt se att modeller replikeras över flera noder. Scenariot fungerar utan Network Load Balancer och fästsessioner. Dock visas inte bara en överanvändning av minnet i noderna när modellen blir inläst N gånger, utan prestandan kommer att bli långsammare mellan anslutningarna eftersom modellen strömmas när den når en ny nod mellan begärandena.  

### <a name="administrator-settings"></a>Administratörsinställningar
Administratörer kan ange följande egenskaper i de avancerade SSMS-egenskaperna för servergruppen:

* EnableCustomVisuals: True/False
* EnablePowerBIReportEmbeddedModels: True/False
* EnablePowerBIReportExportData: True/False
* MaxFileSizeMb: Standardvärdet är nu 1 000
* ModelCleanupCycleMinutes: Hur ofta den kontrollerar att modeller tas bort från minnet
* ModelExpirationMinutes: Hur lång tid det tar innan modellen upphör att gälla och tas bort, baserat på senaste gången den användes
* ScheduleRefreshTimeoutMinutes: Hur lång tid datauppdateringen kan ta för en modell. Som standard är detta två timmar.  Det finns ingen fast övre gräns.

**Konfigurationsfilen rsreportserver.config**

```
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>Utvecklings-API
Utvecklings-API:n (REST API) som introducerades för SSRS 2017 har utökats för Power BI-rapportservern så att den fungerar med både Excel- och .pbix-filer. Ett användningsområde kan vara att programmässigt ladda ned filer från servern, uppdatera dem och sedan publicera dem igen. Detta är det enda sättet för att exempelvis uppdatera Excel-arbetsböcker med PowerPivot-modeller.

Observera att det finns en ny separat API för stora filer som kommer att uppdateras i Power BI-rapportserverversionen för Swagger. 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) och minnesfotavtryck för Power BI-rapportserver
Power BI-rapportservern är nu värd för SQL Server Analysis Services (SSAS) internt. Det är inte specifikt för schemalagd uppdatering. Att vara värd för SSAS kan avsevärt utöka minnesfotavtrycket för rapportservern. Konfigurationsfilen AS.ini är tillgänglig för servernoderna, så om du är bekant med SSAS kan du behöva uppdatera inställningarna, inklusive exempelvis maximal minnesgräns och diskcachelagring. Se [Serveregenskaper i Analysis Services](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services) för mer information.

### <a name="viewing-and-interacting-with-excel-workbooks"></a>Visa och interagera med Excel-arbetsböcker
Excel och Power BI innehåller en uppsättning verktyg som är unik i branschen. Tillsammans innebär de att affärsanalytiker enklare kan samla, utforma, analysera och utforska data visuellt. Förutom att kunna se Power BI-rapporter i webbportalen kan företagsanvändarna nu göra detsamma med Excel-arbetsböcker i Power BI-rapportservern, vilket ger dem en enda plats där de publicerar och ser sitt självbetjänade Microsoft BI-innehåll.

Vi har publicerat en [genomgång för hur du lägger till Office Online Server (OOS) i förhandsvisningsmiljön för Power BI-rapportservern](excel-oos.md). Kunder med ett volymlicensieringskonto kan ladda ned OOS från Volume License Service Center utan kostnad med skrivskyddade funktioner. När konfigurationen är klar kan användarna se och interagera med Excel-arbetsböcker som:

* Inte har några externa datakällberoenden
* Har en live-anslutning till en extern datakälla för SQL Server Analysis Services
* Har en PowerPivot-datamodell

### <a name="support-for-new-table-and-matrix-visuals"></a>Stöd för nya visuella tabell- och matrisobjekt
Power BI-rapportserver har nu stöd för den nya Power BI-tabellen och visuella matrisobjekt. Om du vill skapa rapporter med dessa visuella objekt behöver du en uppdaterad version av Power BI Desktop för oktober 2017-versionen. Den kan inte installeras sida-vid-sida med Power BI Desktop (juni 2017). Om du vill ladda ned den senaste versionen av Power BI Desktop går du till [nedladdningssidan för Power BI-rapportserver](https://powerbi.microsoft.com/report-server/) och väljer **Avancerade alternativ för nedladdning**.

## <a name="june-2017"></a>Juni 2017
* Power BI-rapportserver görs allmänt tillgänglig (GA).

## <a name="may-2017"></a>Maj 2017
* Förhandsvisningen av Power BI-rapportserver blir tillgänglig
* Möjlighet att publicera Power BI-rapporter lokalt
  * Stöd för anpassade visuella objekt
  * Stöd för live-anslutningar med Analysis Services för fler datakällor kommer.
  * Power BI-mobilappen uppdateras för att kunna visa Power BI-rapporter som finns i Power BI-rapportserver
* Förbättrat samarbete i rapporter med kommentarer

## <a name="next-steps"></a>Nästa steg
[Viktig information om Power BI-rapportserver](release-notes.md)  
[Användarhandbok](user-handbook-overview.md)  
[Handbok för administratör](admin-handbook-overview.md)  
[Snabbstart: Installera Power BI-rapportserver](quickstart-install-report-server.md)  
[Installera Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Ladda ned SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

