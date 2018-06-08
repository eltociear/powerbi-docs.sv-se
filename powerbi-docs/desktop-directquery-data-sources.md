---
title: Datakällor som stöds av DirectQuery i Power BI
description: Hämta en lista över vilka datakällor som kan använda DirectQuery.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 06/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 55d6259c3ae044d395bd0b077577856dd88ff43c
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34720775"
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
* SAP Business Warehouse Application Server
* SAP Business Warehouse Message Server (beta)
* SAP HANA
* Snowflake
* Spark (beta) (version 0.9 och senare)
* SQL Server
* Teradata-databas
* Vertica (beta)

Datakällor som har **(beta)** eller **(förhandsversion)** efter namnet kan ändras och stöds inte för användning i produktion. Det är också möjligt att de inte stöds efter att en rapport har publicerats i **Power BI-tjänsten**, vilket innebär att fel kan uppstå när en publicerad rapport öppnas eller utforskas.

Den enda skillnaden mellan datakällor i **(beta)** och **(förhandsversion)** är att källor i **(förhandsversion)** måste aktiveras som en förhandsversionsfunktion innan de blir tillgängliga för användning. Så här aktiverar du en dataanslutning till en **(förhandsversion)**. Öppna **Power BI Desktop** och gå till **Arkiv > Alternativ och inställningar > Alternativ** och välj sedan **Förhandsversionsfunktioner**.

> [!NOTE]
> DirectQuery-frågor till SQL Server kräver autentisering med aktuella Windows-autentiseringsuppgifter eller databasautentiseringsuppgifter för att åtkomsten ska beviljas. Alternativa autentiseringsuppgifter stöds inte.
>

## <a name="on-premises-gateway-requirements"></a>Krav för lokal gateway
I följande tabell anges om en **lokal datagateway** krävs för att ansluta till den angivna datakällan när du har publicerat en rapport till **Power BI-tjänsten**.

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
| Snowflake |Ja |
| Spark (beta) version 0.9 och senare |Stöds inte än i **Power BI-tjänsten** |
| Azure HDInsight Spark (beta) |Nej |
| IBM Netezza |Ja |
| SAP Business Warehouse Application Server |Ja |
| SAP Business Warehouse Message Server |Stöds inte än i **Power BI-tjänsten** |
| Google BigQuery |Nej |


## <a name="next-steps"></a>Nästa steg
Mer information om DirectQuery finns i följande resurser:

* [DirectQuery i Power BI](desktop-directquery-about.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [Lokal datagateway](service-gateway-onprem.md)

