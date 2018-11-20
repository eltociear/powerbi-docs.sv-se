---
title: SQL Database Auditing-innehållspaketet
description: SQL Database Auditing-innehållspaketet för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/09/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: b3b461bedc9eb60607f56c82c5af8de0ed690c06
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507624"
---
# <a name="sql-database-auditing-content-pack-for-power-bi"></a>SQL Database Auditing-innehållspaketet för Power BI

> [!IMPORTANT]
> SQL Database Auditing-innehållspaketet är inaktuellt och inte längre tillgängligt.
 
Power BI-Innehållspaketet för Azure [SQL Database Auditing](/azure/sql-database/sql-database-auditing/) låter dig förstå din databasaktivitet och få insikter om avvikelser och fel som kan tyda på verksamhetsproblem eller misstänkta säkerhetsöverträdelser. 

Anslut till [SQL Database Auditing-innehållspaketet](https://app.powerbi.com/getdata/services/sql-db-auditing) för Power BI.

>[!NOTE]
>Innehållspaketet importerar data från alla tabeller som innehåller AuditLogs i sina namn och lägger till dem i en enda datamodell-tabell med namnet AuditLogs. De senaste 250k händelserna kommer att inkluderas och data uppdateras dagligen.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-azure-sql-database-auditing/pbi_getdata.png) 
2. I rutan tjänster väljer du Hämta.
   
   ![](media/service-connect-to-azure-sql-database-auditing/pbi_getservices.png) 
3. Välj **SQL Database Auditing** \> **hämta**.
   
   ![](media/service-connect-to-azure-sql-database-auditing/sqldbaudit.png)
4. I anslut till SQL Database Auditing-fönstret:
   
   - Ange kontonamn för Azure Table Storage eller URL:en där dina loggar lagras.
   
   - Ange namnet på den SQL-server som du är intresserad av. Ange \* för att läsa in granskningsloggar för alla servrar.
   
   - Ange namnet på den SQL-databas som du är intresserad av. Ange \* för att läsa in granskningsloggar för alla databaser.
   
   - Ange namnet på den Azure-tabell som innehåller de loggar som du är intresserad av. Ange \* för att läsa in granskningsloggar från alla tabeller som har AuditLogs i sina namn.
   
   >[!IMPORTANT]
   >Av prestandaskäl är det lämpligt att alltid ange ett explicit tabellnamn även om alla granskningsloggar lagras i en enda tabell.
   
   - Ange startdatum för de granskningsloggar som du är intresserad av. Ange \* för att läsa in granskningsloggar utan lägre tidsgräns eller 1d för att läsa in granskningsloggar från den senaste dagen.
   
   - Ange slutdatum för de granskningsloggar du är intresserad av. Ange \* för att läsa in granskningsloggar utan en övre tidsgräns.
   
   ![](media/service-connect-to-azure-sql-database-auditing/dbauditing_param.png)
5. Som autentiseringsmetod väljer du **nyckel**, anger din **kontonyckel** \> **logga in**.
   
   ![](media/service-connect-to-azure-sql-database-auditing/pbi_sqlauditing3.png)
6. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Nya objekt markeras med en gul asterisk \*.
   
   ![](media/service-connect-to-azure-sql-database-auditing/pbi_sqldbauditingnewdash.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="next-steps"></a>Nästa steg
[Hämta data för Power BI](service-get-data.md)
[Vad är Power BI?](power-bi-overview.md)
