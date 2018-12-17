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
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: d1cd68fbb995b7fac420a50f97a8930385086a10
ms.sourcegitcommit: 72c9d9ec26e17e94fccb9c5a24301028cebcdeb5
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53026073"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI
Detaljerade anvisningar om hur du konfigurerar schemalagd uppdatering finns att läsa i [Uppdatera data i Power BI](refresh-data.md).

Försök att ställa in en lämplig brandväggsregel när du ställer in en schemalagd uppdatering för Azure SQL-databasen, om du ser ett fel med felkod 400 när du redigerar autentiseringsuppgifterna:

1. Logga in på Azure Management Portal
2. Gå till Azure SQL-servern som du konfigurerar uppdateringar för
3. Aktivera 'Windows Azure-tjänster ”i området tillåtna tjänster

![Tjänster som tillåts av Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

