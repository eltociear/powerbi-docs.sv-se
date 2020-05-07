---
title: Uppgradera Power BI-rapportservern
description: Lär dig mer om att uppgradera Power BI-rapportservern.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.custom: ''
ms.date: 09/05/2017
ms.openlocfilehash: eac019bc31396359b7520e057f2384adce386a96
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73873966"
---
# <a name="upgrade-power-bi-report-server"></a>Uppgradera Power BI-rapportservern

Lär dig mer om att uppgradera Power BI-rapportservern.

 **Ladda ned** ![ladda ned](media/upgrade/download.png "ladda ned")

Om du vill ladda ned Power BI-rapportservern och Power BI Desktop som är optimerat för Power BI-rapportserver, går du till [Lokal rapportering med Power BI-rapportserver](https://powerbi.microsoft.com/report-server/).

## <a name="before-you-begin"></a>Innan du börjar

Innan du uppgraderar en rapportserver, rekommenderas att du utför följande steg för att säkerhetskopiera rapportservern.

### <a name="backing-up-the-encryption-keys"></a>Säkerhetskopiera krypteringsnycklarna

Du bör säkerhetskopiera krypteringsnycklarna när du konfigurerar installationen av en rapportserver initialt. Du bör även säkerhetskopiera nycklarna varje gång du ändrar identiteten för tjänstkonton eller byter namn på datorn. Mer information finns i [Säkerhetskopiera och återställa Reporting Services krypteringsnycklar](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys).

### <a name="backing-up-the-report-server-databases"></a>Säkerhetskopiera databaser för rapportservern

Eftersom en rapportserver är en autonom server, lagras alla programdata i databaserna **reportserver** och **reportservertempdb** databaser som körs på en instans av SQL Server Database Engine. Du kan säkerhetskopiera databaserna **reportserver** och **reportservertempdb** med någon av metoderna som stöds för att säkerhetskopiera SQL Server-databaser. Följande rekommendationer är specifika för rapportserverdatabaser:

* Använd den fullständiga återställningsmodellen när du säkerhetskopierar databasen **reportserver**.
* Använd den förenklade återställningsmodellen när du säkerhetskopierar databasen **reportservertempdb**.
* Du kan använda olika scheman för säkerhetskopiering för varje databas. Skälet till att säkerhetskopiera **reportservertempdb** är så att du inte behöver skapa den på nytt om det skulle inträffa ett maskinvarufel. I händelse av maskinvarufel är det inte nödvändigt att återställa data i **reportservertempdb**, men du behöver tabellstrukturen. Om du förlorar **reportservertempdb** är det enda sättet att få tillbaka den är återskapa rapportserverdatabasen. Om du återskapar **reportservertempdb** är det viktigt att den har samma namn som den primära rapportserver-databasen.

Mer information om säkerhetskopiering och återställning av relationsdatabaser i SQL Server finns i [Säkerhetskopiera och återställa SQL Server-databaser](https://docs.microsoft.com/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases).

### <a name="backing-up-the-configuration-files"></a>Säkerhetskopiera konfigurationsfiler

Power BI-rapportservern använder konfigurationsfiler för att lagra programinställningar. Du bör säkerhetskopiera filerna när du först konfigurerar servern och efter att du distribuerar anpassade tillägg. Filer för säkerhetskopiering inkluderar:

* config.json
* RSHostingService.exe.config
* Rsreportserver.config
* Rssvrpolicy.config
* Reportingservicesservice.exe.config
* Web.config för Report Server ASP.NET-program
* Machine.config för ASP.NET

## <a name="upgrade-the-report-server"></a>Uppgradera en rapportserver

Det är enkelt att uppgradera Power BI-rapportservern. Det krävs endast några få steg för att installera filerna.

1. Hitta platsen för PowerBIReportServer.exe och starta installationsprogrammet.

2. Välj **Uppgradera Power BI-rapportserver**.

    ![Uppgradera Power BI-rapportservern](media/upgrade/reportserver-upgrade1.png "Uppgradera Power BI-rapportservern")

3. Läs och godkänn licensvillkoren och välj sedan **Uppgradera**.

    ![Licensavtal](media/upgrade/reportserver-upgrade-eula.png "Licensavtal")

4. När uppgraderingen är slutförd, kan du välja **Konfigurera rapportserver** för att starta konfigurationshanteraren för rapporttjänster eller **Stäng** att avsluta installationsprogrammet.

    ![Uppgradera konfiguration](media/upgrade/reportserver-upgrade-configure.png)

## <a name="upgrade-power-bi-desktop"></a>Uppgradera Power BI Desktop

När rapportservern har uppgraderats är det lämpligt att kontrollera att alla Power BI-rapportförfattare har uppgraderats till versionen av Power BI Desktop som har optimerats för Power BI-rapportservern som motsvarar servern.

## <a name="next-steps"></a>Nästa steg

* [Administratörsöversikt](admin-handbook-overview.md)  
* [Installera Power BI Desktop optimerad för Power BI-rapportserver](install-powerbi-desktop.md)  
* [Verifiera en Reporting Services-installation](https://docs.microsoft.com/sql/reporting-services/install-windows/verify-a-reporting-services-installation)  
* [Konfigurera tjänstkontot för rapportservern](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager)  
* [Konfigurera rapportserverns URL:er](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager)  
* [Konfigurera en databasanslutning för rapportservern](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager)  
* [Initiera en rapportserver](https://docs.microsoft.com/sql/reporting-services/install-windows/ssrs-encryption-keys-initialize-a-report-server)  
* [Konfigurera SSL-anslutningar på en rapportserver](https://docs.microsoft.com/sql/reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server)  
* [Konfigurera Windows-tjänstekonton och -behörigheter](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)  
* [Webbläsarstöd för Power BI-rapportserver](browser-support.md)

Fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)