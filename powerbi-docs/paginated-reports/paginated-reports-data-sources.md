---
title: Datakällor som stöds för sidnumrerade Power BI-rapporter
description: I den här artikeln lär du dig om datakällor som stöds för sidnumrerade rapporter i Power BI-tjänsten samt hur du ansluter till Azure SQL Database-datakällor.
author: onegoodsausage
ms.author: andremi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 07/27/2020
ms.openlocfilehash: fda04d3241db68f1ca8da66d999bfca6cef9e8cf
ms.sourcegitcommit: 13c4bec679313f2951f1833033316cb8176da8a1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88937457"
---
# <a name="supported-data-sources-for-power-bi-paginated-reports"></a>Datakällor som stöds för sidnumrerade Power BI-rapporter

Den här artikeln går igenom datakällor som stöds för sidnumrerade rapporter i Power BI-tjänsten samt hur du ansluter till Azure SQL Database-datakällor. Vissa datakällor har inbyggt stöd. Du kan ansluta till andra med hjälp av datagatewayer.

## <a name="natively-supported-data-sources"></a>Datakällor med inbyggt stöd

Sidnumrerade rapporter har inbyggt stöd för följande lista av datakällor:

| Datakälla | Autentisering | Anteckningar |
| --- | --- | --- |
| Azure SQL Database <br>Azure SQL Data Warehouse | Grundläggande, enkel inloggning, OAuth2 | Du kan använda en Enterprise Gateway med Azure SQL DB. Du får dock inte använda SSO eller oAuth2 för att autentisera i dessa scenarier.   |
| Azure SQL-hanterad instans | Grundläggande | via offentlig eller privat slutpunkt (privat slutpunkt måste dirigeras via Enterprise Gateway)  |
| Azure Analysis Services | Enkel inloggning, OAuth2 | AAS-brandväggen måste inaktiveras eller konfigureras så att alla IP-intervall i BlackForest-regionen tillåts. Det här gäller bara BlackForest-regionen.  Enkel inloggning från extern klientorganisation stöds inte. |
| Power BI-datamängd | Enkel inloggning | Premium-baserade och icke-Premium-baserade Power BI-datamängder. Kräver läs-behörighet |
| Premium Power BI-datamängd (XMLA) | Enkel inloggning | Power BI-datamängder stöds inte som datakälla för inbäddade sidnumrerade rapporter.  |
| Ange data | Saknas | Data bäddas in i rapporten. |

Förutom Azure SQL Database är alla data källor redo att användas när du har laddat upp rapporten till Power BI-tjänsten. Datakällorna använder som standard enkel inloggning (SSO) där det är tillämpligt. För Azure Analysis Services kan du ändra autentiseringstypen till OAuth2. Men när autentiseringstypen för en specifik datakälla har ändrats till OAuth2 går det inte att återgå till att använda SSO.  Dessutom gäller den här ändringen alla rapporter som använder datakällan på alla arbetsytor för en specifik klient.  Säkerhet på radnivå i sidnumrerade rapporter fungerar inte om användarna väljer SSO för autentiseringstyp.

För Azure SQL Database-datakällor behöver du ange mer information, enligt beskrivningen i avsnittet [Azure SQL Database-autentisering](#azure-sql-database-authentication).

## <a name="other-data-sources"></a>Andra datakällor

Utöver datakällorna med inbyggt stöd ovan kan följande datakällor nås via en [Power BI-datagateway](../connect-data/service-gateway-onprem.md):

- SQL Server
- SQL Server Analysis Services
- Oracle
- Teradata

För sidnumrerade rapporter kan Azure SQL Database och Azure Analysis Services för närvarande inte nås via en Power BI-datagateway.

## <a name="azure-sql-database-authentication"></a>Azure SQL Database-autentisering

För Azure SQL Database-datakällor behöver du ange en autentiseringstyp innan du kör rapporten. Detta gäller endast när du använder en datakälla för första gången på en arbetsyta. Första gången visas följande meddelande:

![Publicera i Power BI](media/paginated-reports-data-sources/power-bi-paginated-publishing.png)

Om du inte anger några autentiseringsuppgifter inträffar ett fel när du kör rapporten. Välj **Fortsätt** för att gå till sidan **Autentiseringsuppgifter för datakälla** för den rapport som du just laddade upp:

![Inställningar för Azure SQL Database](media/paginated-reports-data-sources/power-bi-paginated-settings-azure-sql.png)

Välj länken **Redigera autentiseringsuppgifter** för en specifik datakälla för att öppna dialogrutan **Konfigurera**:

![Konfigurera Azure SQL Database](media/paginated-reports-data-sources/power-bi-paginated-configure-azure-sql.png)

För Azure SQL Database-datakällor är följande de autentiseringstyper som stöds:

- Grundläggande (användarnamn och lösenord)
- Enkel inloggning
- OAuth2 (lagrad AAD-token)

För att enkel inloggning och OAuth2 ska fungera korrekt behöver den Azure SQL Database-server som datakällan ansluter till ha [AAD-autentiseringsstöd aktiverat](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure). För autentiseringsmetoden OAuth2 genererar AAD en token och lagrar den för framtida datakällsåtkomst. Om du vill använda [autentiseringsmetoden enkel inloggning](https://docs.microsoft.com/power-bi/service-azure-sql-database-with-direct-connect#single-sign-on) i stället väljer du alternativet för enkel inloggning direkt nedanför, **Slutanvändare använder sina egna OAuth2-autentiseringsuppgifter när de använder denna datakälla via DirectQuery**.
  
## <a name="next-steps"></a>Nästa steg

[Visa en sidnumrerad rapport i Power BI-tjänsten](../consumer/paginated-reports-view-power-bi-service.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

