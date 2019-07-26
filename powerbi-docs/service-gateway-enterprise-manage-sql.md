---
title: Hantera din datakälla – SQL
description: Hantera den lokala datagatewayen och datakällorna som tillhör denna gateway.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 7d9e670d2567181a0dc99c23997ac3bc2d35f3c9
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271611"
---
# <a name="manage-your-data-source---sql-server"></a>Hantera din datakälla – SQL Server

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

När du har [installerat den lokala datagatewayen](/data-integration/gateway/service-gateway-install) kan du [lägga till datakällor](service-gateway-data-sources.md#add-a-data-source) som kan användas med gatewayen. Den här artikeln handlar om hur du kan arbeta med gatewayer och SQL Server-datakällor som används för antingen schemalagd uppdatering eller DirectQuery.

## <a name="add-a-data-source"></a>Lägga till en datakälla

Information om hur du lägger till en datakälla finns i [Lägga till en datakälla](service-gateway-data-sources.md#add-a-data-source).

![Välja SQL Server-datakälla](media/service-gateway-enterprise-manage-sql/datasourcesettings2.png)

> [!NOTE]
> Om du använder DirectQuery har gatewayen endast stöd för **SQL Server 2012 SP1** och senare versioner.

Du kan fylla i informationen för datakällan med **Server** och **Databas**.  

Du behöver även välja en **Autentiseringsmetod**. Det kan antingen vara **Windows** eller **Grundläggande**. Du bör välja **Grundläggande** om du tänker använda SQL-autentisering i stället för Windows-autentisering. Ange sedan de autentiseringsuppgifter som ska användas för datakällan.

> [!NOTE]
> Alla frågor till datakällan kommer att köras med autentiseringsuppgifterna, såvida inte enkel inloggning (SSO) med Kerberos har konfigurerats och aktiverats för datakällan. Med enkel inloggning använder import av datamängder de lagrade autentiseringsuppgifterna, men DirectQuery-datamängder använder den aktuella Power BI-användaren för att köra frågorna med hjälp av enkel inloggning. Mer information om hur autentiseringsuppgifter lagras finns i [Lagra krypterade autentiseringsuppgifter i molnet](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud) samt i artikeln med beskrivning om [hur du använder Kerberos för enkel inloggning från Power BI till lokala datakällor](service-gateway-sso-kerberos.md).

![Fylla i inställningarna för datakälla](media/service-gateway-enterprise-manage-sql/datasourcesettings3.png)

Välj **Lägg till** när du har fyllt i allt. Nu kan du använda den här datakällan för schemalagd uppdatering, eller DirectQuery mot en lokal SQL Server. *Anslutningen lyckades* visas om anslutningen lyckades.

![Visa anslutningsstatus](media/service-gateway-enterprise-manage-sql/datasourcesettings4.png)

### <a name="advanced-settings"></a>Avancerade inställningar

Om du vill kan du konfigurera sekretessnivån för datakällan. Detta styr hur data kan kombineras. Det används endast vid schemalagd uppdatering. Det gäller inte för DirectQuery. Mer information om sekretessnivåer för datakälla finns i [Sekretessnivåer (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Ange sekretessnivån](media/service-gateway-enterprise-manage-sql/datasourcesettings9.png)

## <a name="using-the-data-source"></a>Använda datakällan

När du har skapat datakällan blir den tillgänglig för användning med antingen DirectQuery-anslutningar eller genom schemalagd uppdatering.

> [!NOTE]
> Server- och databasnamnen måste överensstämma mellan Power BI Desktop och datakällan i den lokala datagatewayen.

Länken mellan din datauppsättning och datakällan i gatewayen är baserad på servernamnet och databasnamnet. Dessa måste stämma överens. Om du exempelvis anger en IP-adress för servernamnet behöver du i **Power BI Desktop** använda den IP-adressen för datakällan i gatewaykonfigurationen. Om du använder *SERVER\INSTANS* i Power BI Desktop måste du använda samma i den datakälla som konfigureras för gatewayen.

Detta gäller både DirectQuery och schemalagd uppdatering.

### <a name="using-the-data-source-with-directquery-connections"></a>Använda datakällan med DirectQuery-anslutningar

Du behöver se till att server- och databasnamnet överensstämmer mellan **Power BI Desktop** och den konfigurerade datakällan för gatewayen. Du behöver även kontrollera att användaren finns med på fliken **Användare** för datakällan för att DirectQuery-datamängder ska kunna publiceras. Valet för DirectQuery inträffar i Power BI Desktop när du importerar data första gången. Mer information om hur DirectQuery används finns i [Använda DirectQuery i Power BI Desktop](desktop-use-directquery.md).

När du har publicerat, antingen från Power BI Desktop eller **Hämta Data**, borde dina rapporter fungera. Det kan ta ett par minuter efter att du har skapat datakällan i gatewayen innan anslutningen kan användas.

### <a name="using-the-data-source-with-scheduled-refresh"></a>Använda datakällan med schemalagd uppdatering

Om du finns med på fliken **Användare** för den datakälla som konfigurerats i gatewayen, och om server- och databasnamnen matchar, visas gatewayen som ett alternativ för användning med schemalagd uppdatering.

![Visa användarna](media/service-gateway-enterprise-manage-sql/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Nästa steg

* [Ansluta till lokala data i SQL Server](service-gateway-sql-tutorial.md)
* [Felsökning av den lokala datagatewayen](/data-integration/gateway/service-gateway-tshoot)
* [Felsöka gatewayer – Power BI](service-gateway-onprem-tshoot.md)
* [Använda Kerberos för SSO (enkel inloggning) från Power BI till lokala datakällor](service-gateway-sso-kerberos.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

