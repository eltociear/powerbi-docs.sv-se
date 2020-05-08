---
title: Sidnumrerad rapport datakällor i Power BI-rapportservern
description: Läs om datakällor som sidnumrerade rapporter (.rdl) kan ansluta till i Power BI-rapportservern.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: maggies
ms.openlocfilehash: 7cb5772e6ccdc1e4036d70f65a3a28210a4f6df1
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78260725"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Sidnumrerad rapport datakällor i Power BI-rapportservern
Sidnumrerade Reporting Services-rapporter i Power BI-rapportservern stöder samma datakällor som stöds i SQL Server Reporting Services. Se listan i [Datakällor som stöds av Reporting Services](https://docs.microsoft.com/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs).

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>Ansluta till Oracle-datakällor med UseInstalledUICulture

För att ansluta till Oracle-datakällor använder Power BI-rapportserver Oracle Data Provider för .NET (ODP.NET) som är NLS-oberoende.

Som standard använder rapportservern den första klientens gränssnittskultur för att läsa in ODP.NET.  Därför kommer alla efterföljande anslutningar till Oracle från rapportservern att finnas i den inledande användargränssnittskulturen tills omstart av tjänsten.  Den här metoden kan orsaka problem med att återge en rapport på grund av avvikelser i användargränssnittets kulturformat.

För att erbjuda en bättre upplevelse i Power BI-rapportserver har vi infört en konfigurationsinställning med namnet UseInstalledUICulture. När UseInstalledUICulture är inställt på True laddar rapportservern alltid ODP.NET i serverns gränssnittskultur istället för den första klientens kultur.
Den här inställningen är tillgänglig i Power BI-rapportserver från och med tjänstversionen i februari

Aktivera funktionen genom att ändra ORACLE-förlängningen rsreportserver.config-filen, som nedan.
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>Nästa steg
Nu när du har anslutit till din datakälla [skapar du en sidnumrerad rapport](quickstart-create-paginated-report.md).  


Fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
