---
title: Azure SQL Database med DirectQuery
description: Azure SQL Database med DirectQuery
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
ms.date: 08/10/2017
ms.author: asaxton
ms.openlocfilehash: 83613f0ed915a03b65b90d4bf61e37568b922182
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="azure-sql-database-with-directquery"></a>Azure SQL Database med DirectQuery
Här kan du lära dig hur du kan ansluta direkt till Azure SQL Database och skapa rapporter med realtidsdata. Du kan hålla dina data vid källan och inte i Power BI.

Med DirectQuery skickas frågor tillbaka till din Azure SQL Database medan du utforskar dessa data i rapportvyn. Den här användningen föreslås för användare som är bekanta med databaser och de enheter som de ansluter till.

**OBS:**

* Ange det fullständigt kvalificerade servernamnet vid anslutning (se nedan för mer information)
* Se till att brandväggsreglerna för databasen är konfigurerade för ”[Tillåt åtkomst till Azure-tjänster](https://msdn.microsoft.com/library/azure/ee621782.aspx)”.
* Varje åtgärd, som att markera en kolumn eller lägga till ett filter, skickar en fråga tillbaka till databasen
* Panelerna uppdateras med ungefär 15 minuters mellanrum (uppdatering behöver inte schemaläggas). Detta kan justeras i Avancerade inställningar när du ansluter.
* Frågor och svar är inte tillgänglig för DirectQuery-datauppsättningar
* Schemaändringar plockas inte upp automatiskt

Dessa begränsningar och anteckningar kan ändras när vi fortsätter att förbättra upplevelsen. Stegen för att ansluta beskrivs nedan. 

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop och DirectQuery
För att ansluta till Azure SQL Database med DirectQuery, behöver du använda Power BI Desktop. Den här metoden erbjuder ytterligare flexibilitet och funktioner. Rapporter som skapas med Power BI Desktop kan senare publiceras i Power BI-tjänsten. Du kan lära dig mer om hur du ansluter till [Azure SQL Database med DirectQuery](desktop-use-directquery.md) i Power BI Desktop. 

## <a name="connecting-through-power-bi"></a>Ansluta via Power BI
Du kan inte längre ansluta till Azure SQL Database direkt från Power BI-tjänsten. När du väljer [Azure SQL Database-anslutningsprogrammet](https://app.powerbi.com/getdata/bigdata/azure-sql-database-with-live-connect) blir du ombedd att upprätta anslutningen i Power BI Desktop. Du kan sedan publicera dina Power BI Desktop-rapporter i Power BI-tjänsten. 

![](media/service-azure-sql-database-with-direct-connect/azure-sql-database-in-power-bi.png)

### <a name="finding-parameter-values"></a>Hitta parametervärden
Det fullständigt kvalificerade servernamnet och databasnamnet återfinns i Azure Portal.

![](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

## <a name="next-steps"></a>Nästa steg
[Använda DirectQuery i Power BI Desktop](desktop-use-directquery.md)  
[Kom igång med Power BI](service-get-started.md)  
[Hämta data för Power BI](service-get-data.md)  
Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

