---
title: Felsöka schemalagd uppdatering för Azure SQL-databaser
description: Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 9439ac6bd0b4df568b964f548372fb94d2fd0b26
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34238536"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI
Detaljerade anvisningar om hur du konfigurerar schemalagd uppdatering finns att läsa i [Uppdatera data i Power BI](refresh-data.md).

Försök att ställa in en lämplig brandväggsregel när du ställer in en schemalagd uppdatering för Azure SQL-databasen, om du ser ett fel med felkod 400 när du redigerar autentiseringsuppgifterna:

1. Logga in på Azure Management Portal
2. Gå till Azure SQL-servern som du konfigurerar uppdateringar för
3. Aktivera 'Windows Azure-tjänster ”i området tillåtna tjänster

![](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

