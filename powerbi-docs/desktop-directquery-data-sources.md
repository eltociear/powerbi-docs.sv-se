---
title: Datakällor som stöds av DirectQuery i Power BI
description: Hämta en lista över vilka datakällor som kan använda DirectQuery.
author: davidiseminger
ms.author: davidi
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/04/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 59c55d2e9322b0b7d76a35f4eec0863efe4959e0
ms.sourcegitcommit: 09ee1b4697aad84d8f4c9421015d7e4dbd3cf25f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70302641"
---
# <a name="data-sources-supported-by-directquery-in-power-bi"></a>Datakällor som stöds av DirectQuery i Power BI

**Power BI Desktop** och **Power BI-tjänsten** har flera datakällor som du kan ansluta till och få åtkomst till data. Den här artikeln beskriver vilka datakällor för Power BI stöder anslutningsmetoden **DirectQuery**. Läs mer om DirectQuery i [**DirectQuery i Power BI**](desktop-directquery-about.md).

Följande datakällor stöds av DirectQuery i Power BI:

* Amazon Redshift
* AtScale (Beta)
* Azure Data Explorer
* Azure HDInsight Spark
* [Azure SQL Database](service-azure-sql-database-with-direct-connect.md)
* [Azure SQL Data Warehouse](service-azure-sql-data-warehouse-with-direct-connect.md)
* Denodo
* Google BigQuery
* HDInsight Interactive-fråga
* IBM DB2 (Microsoft-provider))
* IBM Netezza
* Impala (version 2.x)
* MarkLogic
* Oracle Database (version 12 och senare)
* Oracle Essbase
* PostgreSQL
* SAP Business Warehouse Application Server
* SAP Business Warehouse Message Server
* SAP HANA
* Snowflake
* Spark (version 0.9 och senare)
* SQL Server
* Teradata-databas
* Vertica

Datakällor som har **(beta)** eller **(förhandsversion)** efter namnet kan ändras och stöds inte för användning i produktion. Det kan också hända att de inte stöds efter att en rapport har publicerats i **Power BI-tjänsten**, vilket innebär att det kan uppstå fel när en publicerad rapport öppnas eller utforskas.

Den enda skillnaden mellan datakällor i **(beta)** och **(förhandsversion)** är att källor i **(förhandsversion)** måste aktiveras som en förhandsversionsfunktion innan de blir tillgängliga för användning. Så här aktiverar du en dataanslutning till en **(förhandsversion)** . Öppna **Power BI Desktop** och gå till **Arkiv > Alternativ och inställningar > Alternativ** och välj sedan **Förhandsversionsfunktioner**.

> [!NOTE]
> DirectQuery-frågor till SQL Server kräver autentisering med aktuella Windows-autentiseringsuppgifter eller databasautentiseringsuppgifter för att åtkomsten ska beviljas. Alternativa autentiseringsuppgifter stöds inte.
>

## <a name="on-premises-gateway-requirements"></a>Krav för lokal gateway
I följande tabell anges om en **lokal datagateway** krävs för att ansluta till den angivna datakällan när du har publicerat en rapport till **Power BI-tjänsten**.

| Källa | Gateway krävs? |
| --- | --- |
| Amazon Redshift |Nej |
| Azure HDInsight Spark (beta) |Nej |
| Azure SQL Database |Nej |
| Azure SQL Data Warehouse |Nej |
| Google BigQuery |Nej |
| IBM Netezza |Ja |
| IBM DB2 (IBM-provider) |Ja |
| IBM DB2 (Microsoft-provider) |Nej |
| IBM Informix-databas |Nej |
| Impala (version 2.x) |Ja |
| MySQL |Ja |
| ODBC |Ja |
| Oracle-databas |Ja |
| PostgreSQL |Ja |
| SAP Business Warehouse Application Server |Ja |
| SAP Business Warehouse Message Server |Stöds inte än i **Power BI-tjänsten** |
| SAP HANA |Ja |
| Snowflake |Ja |
| Spark (beta) version 0.9 och senare |Ja |
| SQL Server |Ja |
| Sybase |Ja |
| Teradata-databas |Ja |
| Vertica |Ja |


## <a name="single-sign-on-sso-for-directquery-sources"></a>Enkel inloggning (SSO) för DirectQuery-källor

När alternativet för enkel inloggning är aktiverat och dina användares åtkomstrapporter har skapats ovanpå datakällan skickar Power BI deras autentiserade Azure AD-autentiseringsuppgifter i frågorna till den underliggande datakällan. Detta möjliggör för Power BI att respektera säkerhetsinställningarna som är konfigurerade på datakällsnivå.

Alternativet för enkel inloggning börjar fungera för alla datauppsättningar som använder den här datakällan. Autentiseringsmetoden som används för importscenarier påverkas inte. Följande datakällor stöder enkel inloggning för anslutningar via DirectQuery:

- Azure SQL Database
- Azure SQL Data Warehouse
- Impala
- SAP HANA
- SAP BW
- Spark
- SQL Server
- Teradata

> [!Note]
> Azure Multi-Factor Authentication (MFA) stöds inte. Användare som vill använda enkel inloggning med DirectQuery måste undantas från MFA.

## <a name="next-steps"></a>Nästa steg
Mer information om DirectQuery finns i följande resurser:

* [DirectQuery i Power BI](desktop-directquery-about.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [Lokal datagateway](service-gateway-onprem.md)

