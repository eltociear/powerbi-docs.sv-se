---
title: Azure SQL Database med DirectQuery
description: Azure SQL Database med DirectQuery
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 09/16/2019
LocalizationGroup: Data from databases
ms.openlocfilehash: f2d175896876bd6ea6f76b58b0eda0e5100dcfe1
ms.sourcegitcommit: d441d350504f8c6d9e100d229757add6237f0bef
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73060906"
---
# <a name="azure-sql-database-with-directquery"></a>Azure SQL Database med DirectQuery

Här kan du lära dig hur du kan ansluta direkt till Azure SQL Database och skapa rapporter med realtidsdata. Du kan hålla dina data vid källan och inte i Power BI.

Med DirectQuery skickas frågor tillbaka till din Azure SQL Database medan du utforskar dessa data i rapportvyn. Den här användningen föreslås för användare som är bekanta med databaser och de enheter som de ansluter till.

**OBS:**

* Ange det fullständigt kvalificerade servernamnet vid anslutning (se nedan för mer information).
* Se till att brandväggsreglerna för databasen är konfigurerade för ”[Tillåt åtkomst till Azure-tjänster](https://docs.microsoft.com/azure/sql-database/sql-database-networkaccess-overview#allow-azure-services)”.
* Varje åtgärd, som att markera en kolumn eller lägga till ett filter, skickar en fråga tillbaka till databasen.
* Panelerna uppdateras varje timme (uppdateringen behöver inte schemaläggas). Du kan justera hur ofta uppdateringen ska göras i Avancerade inställningar när du ansluter.
* Frågor och svar-rutan är inte tillgänglig för DirectQuery-datauppsättningar.
* Schemaändringar plockas inte upp automatiskt.

Dessa begränsningar och anteckningar kan ändras när vi fortsätter att förbättra upplevelsen. Stegen för att ansluta beskrivs nedan.

> [!Important]
> Vi har förbättrat anslutningen till Azure SQL Database.  Använd Power BI Desktop för bästa möjliga anslutning till din Azure SQL Database-datakälla.  När du har skapat din modell och rapport kan du publicera den till Power BI-tjänsten.  Direktanslutningen för Azure SQL Database i Power BI-tjänsten är nu inaktuell.

## <a name="power-bi-desktop-and-directquery"></a>Power BI Desktop och DirectQuery

För att kunna ansluta till Azure SQL Database med DirectQuery måste du använda Power BI Desktop. Den här metoden erbjuder ytterligare flexibilitet och funktioner. Rapporter som skapas med Power BI Desktop kan senare publiceras i Power BI-tjänsten. Du kan lära dig mer om hur du ansluter till [Azure SQL Database med DirectQuery](desktop-use-directquery.md) i Power BI Desktop.

## <a name="find-parameter-values"></a>Hitta parametervärden

Du hittar det fullständigt kvalificerade servernamnet och databasnamnet i Azure-portalen.

![Ny uppdatering av Azure-portalen](media/service-azure-sql-database-with-direct-connect/azureportnew_update.png)

![Uppdatering av Azure-portalen](media/service-azure-sql-database-with-direct-connect/azureportal_update.png)

[!INCLUDE [direct-query-sso](includes/direct-query-sso.md)]

## <a name="next-steps"></a>Nästa steg

* [Använda DirectQuery i Power BI Desktop](desktop-use-directquery.md)  
* [Vad är Power BI?](fundamentals/power-bi-overview.md)  
* [Hämta data för Power BI](service-get-data.md)  

Har du fler frågor? [Testa Power BI Community](http://community.powerbi.com/)
