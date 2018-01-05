---
title: "Felsöka schemalagd uppdatering för Azure SQL-databaser"
description: "Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI"
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
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: 0b2f5da3fccd1741cb5a9ea02a1aebbd8fbac96f
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/06/2017
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI
Detaljerade anvisningar om hur du konfigurerar schemalagd uppdatering finns att läsa i [Uppdatera data i Power BI](refresh-data.md).

Försök att ställa in en lämplig brandväggsregel när du ställer in en schemalagd uppdatering för Azure SQL-databasen, om du ser ett fel med felkod 400 när du redigerar autentiseringsuppgifterna:

1. Logga in på Azure Management Portal
2. Gå till Azure SQL-servern som du konfigurerar uppdateringar för
3. Aktivera 'Windows Azure-tjänster ”i området tillåtna tjänster

![](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

