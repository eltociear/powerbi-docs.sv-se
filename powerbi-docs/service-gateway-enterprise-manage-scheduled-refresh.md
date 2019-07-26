---
title: Hantera din datakälla – Import/schemalagd uppdatering
description: Hantera den lokala datagatewayen och datakällorna som tillhör denna gateway. Den här artikeln är specifik för datakällor som kan användas med import/schemalagd uppdatering.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2a3cdc3e6c4fc4f18613994a919f8ab733df5e14
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271662"
---
# <a name="manage-your-data-source---importscheduled-refresh"></a>Hantera din datakälla – Import/schemalagd uppdatering

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

När du har [installerat den lokala datagatewayen](/data-integration/gateway/service-gateway-install) behöver du [lägga till datakällor](service-gateway-data-sources.md#add-a-data-source) som kan användas med gatewayen. Den här artikeln handlar om hur du kan arbeta med gatewayer och datakällor som används för schemalagd uppdatering i stället för DirectQuery- eller live-anslutningar.

## <a name="add-a-data-source"></a>Lägga till en datakälla

Information om hur du lägger till en datakälla finns i [Lägga till en datakälla](service-gateway-data-sources.md#add-a-data-source).

Alla typer av datakällor som anges kan användas för schemalagd uppdatering med den lokala datagatewayen. Analysis Services, SQL Server och SAP HANA kan användas för schemalagd uppdatering eller DirectQuery-/live-anslutningar.

![Välja datakälla](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings2.png)

Du kan fylla i informationen för datakällan, inklusive källinformationen och de autentiseringsuppgifter som används för att få åtkomst till datakällan.

> [!NOTE]
> Alla frågor till datakällan kommer att köras med dessa autentiseringsuppgifter. Mer information om hur autentiseringsuppgifter lagras finns i [Lagra krypterade autentiseringsuppgifter i molnet](service-gateway-data-sources.md#storing-encrypted-credentials-in-the-cloud).

![Fylla i inställningarna för datakälla](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings3-oracle.png)

En lista över typer av datakällor som kan användas med schemalagd uppdatering finns i [Lista över tillgängliga typer av datakällor](service-gateway-data-sources.md#list-of-available-data-source-types).

Välj **Lägg till** när du har fyllt i allt. Nu kan du använda den här datakällan för schemalagd uppdatering med dina lokala data. *Anslutningen lyckades* visas om anslutningen lyckades.

![Visa anslutningsstatus](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings4.png)

### <a name="advanced-settings"></a>Avancerade inställningar

Om du vill kan du konfigurera sekretessnivån för datakällan. Detta styr hur data kan kombineras. Det används endast vid schemalagd uppdatering. Mer information om sekretessnivåer för datakälla finns i [Sekretessnivåer (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Ange sekretessnivån](media/service-gateway-enterprise-manage-scheduled-refresh/datasourcesettings9.png)

## <a name="using-the-data-source-for-scheduled-refresh"></a>Använda datakällan med schemalagd uppdatering

När du har skapat datakällan blir den tillgänglig för användning med antingen DirectQuery-anslutningar eller genom schemalagd uppdatering.

> [!NOTE]
> Server- och databasnamnen måste överensstämma mellan Power BI Desktop och datakällan i den lokala datagatewayen.

Länken mellan din datauppsättning och datakällan i gatewayen är baserad på servernamnet och databasnamnet. Dessa måste stämma överens. Om du exempelvis anger en IP-adress för servernamnet i Power BI Desktop måste du använda den IP-adressen för datakällan i gatewaykonfigurationen. Om du använder *SERVER\INSTANS* i Power BI Desktop måste du använda samma i den datakälla som konfigureras för gatewayen.

Om du finns med på fliken **Användare** för den datakälla som konfigurerats i gatewayen, och om server- och databasnamnen matchar, visas gatewayen som ett alternativ för användning med schemalagd uppdatering.

![Visa användarna](media/service-gateway-enterprise-manage-scheduled-refresh/powerbi-gateway-enterprise-schedule-refresh.png)

> [!WARNING]
> Om datamängden innehåller flera datakällor måste du lägga varje datakälla i gatewayen. Om en eller flera datakällor inte har lagts till i gatewayen visas inte gatewayen som tillgänglig för schemalagd uppdatering.

## <a name="limitations"></a>Begränsningar

OAuth är inte ett schema för autentiseringsmetoder som stöds med en lokal datagateway. Du kan inte lägga till datakällor som kräver OAuth. Om datamängden har en datakälla som kräver OAuth kan du inte använda gatewayen för schemalagd uppdatering.

## <a name="next-steps"></a>Nästa steg

* [Felsökning av den lokala datagatewayen](/data-integration/gateway/service-gateway-tshoot)
* [Felsöka gatewayer – Power BI](service-gateway-onprem-tshoot.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
