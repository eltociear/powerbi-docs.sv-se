---
title: Felsöka schemalagd uppdatering för Azure SQL-databaser
description: Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/04/2019
ms.author: maggies
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 292f80b4fec7da9ff6ce42e3611bf4d6353bae2d
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83280482"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Felsöka schemalagd uppdatering för Azure SQL-databaser i Power BI

Detaljerad information om uppdatering finns i [Uppdatera data i Power BI](refresh-data.md) och [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md).

Om det uppstår ett fel med felkod 400 när du redigerar autentiseringsuppgifter vid konfiguration av schemalagd uppdatering för Azure SQL-databas kan du prova följande för att ange rätt brandväggsregel:

1. Logga in på [Azure Portal](https://portal.azure.com).

1. Gå till den Azure SQL-databas som du konfigurerar uppdateringen för.

1. Längst upp i bladet **Översikt** väljer du **Konfigurera serverns brandvägg**.

1. På bladet **Brandväggsinställningar** ser du till att **Tillåt åtkomst till Azure-tjänster** är angett till **PÅ**.

    ![Tjänster som tillåts av Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
