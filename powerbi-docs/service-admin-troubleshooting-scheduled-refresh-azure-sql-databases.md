---
title: Felsöka schemalagd uppdatering för Azure SQL-databaser
description: Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 6d71a1202ba996b70c7477a33ccab936bebbfc5e
ms.sourcegitcommit: e5cf19e16112c7dad1591c3b38d232267ffb3ae1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/17/2019
ms.locfileid: "72542796"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI

Detaljerad information om uppdatering finns i [Uppdatera data i Power BI](refresh-data.md) och [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md).

Om det uppstår ett fel med felkod 400 när du redigerar autentiseringsuppgifter vid konfiguration av schemalagd uppdatering för Azure SQL-databas kan du prova följande för att ange rätt brandväggsregel:

1. Logga in på [Azure-portalen](https://portal.azure.com).

1. Gå till den Azure SQL-databas som du konfigurerar uppdateringen för.

1. Längst upp i bladet **Översikt** väljer du **Konfigurera serverns brandvägg**.

1. På bladet **Brandväggsinställningar** ser du till att **Tillåt åtkomst till Azure-tjänster** är angett till **PÅ**.

    ![Tjänster som tillåts av Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
