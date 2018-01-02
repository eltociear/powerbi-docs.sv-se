---
title: "Datakällor som stöds av DirectQuery i Power BI"
description: "Hämta en lista över vilka datakällor som kan använda DirectQuery."
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/26/2017
ms.author: davidi
ms.openlocfilehash: 9817011491f65f84201c4d26ee04aa5cd8704ab1
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2017
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Datakällor som stöds av DirectQuery i Power BI
**Power BI Desktop** och **Power BI-tjänsten** har flera datakällor som du kan ansluta till och få åtkomst till data. Den här artikeln beskriver vilka datakällor för Power BI stöder anslutningsmetoden **DirectQuery**. Läs mer om DirectQuery i [**DirectQuery i Power BI**](desktop-directquery-about.md).

Följande datakällor stöds av DirectQuery i Power BI:

* Amazon Redshift
* Azure HDInsight Spark (beta)
* Azure SQL Database
* Azure SQL Data Warehouse
* Google BigQuery (beta)
* IBM Netezza (beta)
* Impala (version 2.x)
* Oracle Database (version 12 och senare)
* SAP Business Warehouse (beta)
* SAP HANA
* Snowflake
* Spark (beta) (version 0.9 och senare)
* SQL Server
* Teradata-databas
* Vertica (beta)

Datakällor som har **(beta)** eller **(förhandsversion)** efter namnet kan ändras och stöds inte för användning i produktion. Det är också möjligt att de inte stöds efter att en rapport har publicerats i **Power BI-tjänsten**, vilket innebär att fel kan uppstå när en publicerad rapport öppnas eller utforskas.

Den enda skillnaden mellan datakällor i **(beta)** och **(förhandsversion)** är att källor i **(förhandsversion)** måste aktiveras som en förhandsversionsfunktion innan de blir tillgängliga för användning. Så här aktiverar du en dataanslutning till en **(förhandsversion)**. Öppna **Power BI Desktop** och gå till **Arkiv > Alternativ och inställningar** och sedan **Inställningar > Alternativ > Förhandsversionsfunktioner**.

## <a name="on-premises-gateway-requirements"></a>Krav för lokal gateway
I följande tabell anger om en **lokal datagateway** krävs för att ansluta till den angivna datakällan när du har publicerat en rapport till **Power BI-tjänsten**.

| Källa | Gateway krävs? |
| --- | --- |
| SQL Server |Ja |
| Azure SQL Database |Nej |
| Azure SQL Data Warehouse |Nej |
| SAP HANA |Ja |
| Oracle-databas |Ja |
| Teradata-databas |Ja |
| Amazon Redshift |Nej |
| Impala (version 2.x) |Ja |
| Snowflake (förhandsversion) |Stöds inte än i **Power BI-tjänsten** |
| Spark (beta) version 0.9 och senare |Stöds inte än i **Power BI-tjänsten** |
| Azure HDInsight Spark (beta) |Stöds inte än i **Power BI-tjänsten** |
| IBM Netezza (beta) |Stöds inte än i **Power BI-tjänsten** |
| SAP Business Warehouse (beta) |Stöds inte än i **Power BI-tjänsten** |

## <a name="next-steps"></a>Nästa steg
Mer information om DirectQuery finns i följande resurser:

* [DirectQuery i Power BI](desktop-directquery-about.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [Lokal datagateway](service-gateway-onprem.md)

