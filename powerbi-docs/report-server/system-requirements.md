---
title: Maskin- och programvarukrav för att installera Power BI-rapportservern
description: Här hittar du minimikraven för maskin- och programvara för installation och körning av Power BI-rapportservern.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: 2963dbe2a5d1109e4396568624e16bf49d98da10
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>Maskin- och programvarukrav för att installera Power BI-rapportservern
Här hittar du minimikraven för maskin- och programvara för installation och körning av Power BI-rapportservern.

## <a name="processor-memory-and-operating-system-requirements"></a>Krav på processor, minne och operativsystem
| Komponent | Krav |
| --- | --- |
| .NET Framework |4.6<br><br>Du kan manuellt installera .NET Framework från [Microsoft .NET Framework 4.6 (webbinstallationsprogram) för Windows](http://support.microsoft.com/kb/3045560).<br/><br/> Mer information, rekommendationer och vägledning för .NET Framework 4.6 finns i [.NET Framework Deployment Guide for Developer (.NET Framework-distributionsguiden för utvecklare)](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).<br/><br/>Windows 8.1 och Windows Server 2012 R2 kräver [KB2919355](http://support.microsoft.com/kb/2919355) innan du installerar .NET Framework 4.6. |
| Hårddisk |Power BI-rapportservern kräver minst 1 GB ledigt utrymme på hårddisken.<br><br>Ytterligare utrymme krävs på den databasserver som är värd för rapportserverdatabasen. |
| Minne |**Minst:** 1 GB<br/><br/> **Rekommenderat:** Minst 4 GB |
| Processorhastighet |**Minst:** x64-processor: 1,4 GHz<br/><br/> **Rekommenderat:** 2,0 GHz eller snabbare |
| Processortyp |x64.processor: AMD Opteron, AMD Athlon 64, Intel Xeon med Intel EM64T-stöd, Intel Pentium IV med EM64T-stöd |
| Operativsystem |Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows Server 2012 R2 Datacenter<br><br>Windows Server 2012 R2 Standard<br><br>Windows Server 2012 R2 Essentials<br><br>Windows Server 2012 R2 Foundation<br><br>Windows Server 2012 Datacenter<br><br>Windows Server 2012 Standard<br><br>Windows Server 2012 Essentials<br><br>Windows Server 2012 Foundation<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br><br>Windows 8.1<br><br>Windows 8.1 Pro<br><br>Windows 8.1 Enterprise<br><br>Windows 8<br><br>Windows 8 Pro<br><br>Windows 8 Enterprise |

> [!NOTE]
> Installation av Power BI-rapportservern stöds endast på x64-processorer.
> 
> 

## <a name="database-server-version-requirements"></a>Databasserverns versionskrav
SQL Server används som värd för rapportserverdatabaserna. SQL Server Database Engine-instansen kan vara en lokal eller fjärransluten instans. Följande är de versioner av SQL Server Database Engine som stöds och kan användas som värd för rapportserverdatabaserna:

* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012
* SQL Server 2008 R2
* SQL Server 2008

Om du vill skapa rapportserverdatabasen på en fjärrdator måste du konfigurera anslutningen för att använda ett domänanvändarkonto eller ett tjänstkonto som har åtkomst till nätverket. Om du vill använda en fjärrinstans av SQL Server, ska du noga överväga vilka autentiseringsuppgifter som rapportservern ska använda för att ansluta till SQL Server-instansen. Mer information finns i [Konfigurera en databasanslutning för rapportservern](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager).

## <a name="considerations"></a>Att tänka på:
Power BI-rapportservern installerar standardvärden för att konfigurera de grundläggande inställningar som krävs för att göra en rapportserver driftklar. Den har följande krav:

* En SQL Server Database Engine måste vara tillgänglig efter installationen och innan du konfigurerar databasen för rapportservern. Database Engine-instansen ska vara värd för den rapportserverdatabas som Report Services-konfigurationshanteraren skapar. Database Engine krävs inte för det faktiska installationsförloppet.
* Det användarkonto som används för att köra installationsprogrammet måste vara medlem i den lokala administratörsgruppen.
* Användarkontot som används för Report Services-konfigurationshanteraren måste ha behörighet att komma åt och skapa databaser på Database Engine-instansen som är värd för rapportserverdatabaserna.
* Installationsprogrammet måste kunna använda standardvärdena för att reservera de URL:er som ger åtkomst till rapportservern och webbportalen. Dessa värden är port 80, ett starkt jokertecken, och de virtuella katalognamnen i formatet **Rapportserver** och **Rapporter**.

## <a name="read-only-domain-controller-rodc"></a>Skrivskyddad domänkontrollant (RODC)
 Rapportservern kan installeras i en miljö som har en skrivskyddad domänkontrollant (RODC) men Reporting Services behöver åtkomst till en domänkontrollant som inte är skrivskyddad för att fungera korrekt. Om Reporting Services bara har åtkomst till en RODC, kan det uppstå fel när du försöker administrera tjänsten.

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Power BI-rapporter och realtidsanslutningar för Analysis Services
Du kan använda en realtidsanslutning för tabell- eller flerdimensionella instanser. Analysis Services-servern måste vara av rätt version och utgåva för att fungera korrekt.

| **Serverversion** | **Obligatorisk SKU** |
| --- | --- |
| 2012 SP1 CU4 eller senare |Business Intelligence och Enterprise SKU |
| 2014 |Business Intelligence och Enterprise SKU |
| 2016 och senare |Standard-SKU eller högre |

## <a name="next-steps"></a>Nästa steg
[Användarhandbok](user-handbook-overview.md)  
[Handbok för administratör](admin-handbook-overview.md)  
[Installera Power BI-rapportserver](install-report-server.md)  
[Installera Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Ladda ned SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

