---
title: Lokal datagateway
description: Den här artikeln visar en översikt över den lokala datagatewayen för Power BI. Du kan använda den här gatewayen för att arbeta med DirectQuery-datakällor. Du kan också använda den för att uppdatera molndatauppsättningar med lokala data.
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Gateways
ms.date: 07/15/2019
ms.openlocfilehash: 1d91792d544854d5a98b1966b2561196249ff7c8
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83302861"
---
# <a name="what-is-an-on-premises-data-gateway"></a>Vad är en lokal datagateway?

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

En lokal datagateway fungerar som en brygga med snabb och säker dataöverföring mellan lokala data (data som inte finns i molnet) och flera molntjänster från Microsoft. Dessa molntjänster omfattar Power BI, Power Apps, Power Automate, Azure Analysis Services och Azure Logic Apps. Genom att använda en gateway kan organisationer förvara databaser och andra datakällor i sina lokala nätverk, men ändå använda dessa lokala data i molntjänster.

## <a name="how-the-gateway-works"></a>Så här fungerar gatewayen

![Gatewayöversikt](media/service-gateway-onprem/on-premises-data-gateway.png)

Mer information om hur gatewayen fungerar finns i [Arkitektur för lokal datagateway](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="types-of-gateways"></a>Typer av gatewayer

Det finns två olika typer av gatewayer för varsitt scenario:

* **Lokal datagateway** – flera användare kan ansluta till flera lokala datakällor. Du kan använda en lokal datagateway med alla tjänster som stöds, men en enda gatewayinstallation. Den här gatewayen är väl lämpad för komplexa scenarier där flera personer har åtkomst till flera olika datakällor.

* **Lokal datagateway (personligt läge)** – en användare kan ansluta till källor och kan inte delas med andra. En lokal datagateway (personligt läge) kan bara användas med Power BI. Den här gatewayen är väl lämpad för scenarier där du är den enda personen som skapar rapporter och du inte behöver datakällor med andra.

## <a name="use-a-gateway"></a>Använda en gateway

Det finns fyra huvudsakliga steg för att använda en gateway.

1. [Ladda ned och installera gatewayen](/data-integration/gateway/service-gateway-install) på en lokal dator.
1. [Konfigurera](/data-integration/gateway/service-gateway-app) gatewayen utifrån brandväggen och andra nätverkskrav.
1. [Lägg till gatewayadministratörer](/data-integration/gateway/service-gateway-manage) som också kan hantera och administrera andra nätverkskrav.
1. [Använd gatewayen](service-gateway-sql-tutorial.md) till att uppdatera en lokal datakälla.
1. [Felsök](service-gateway-onprem-tshoot.md) gatewayen i händelse av fel.

## <a name="next-steps"></a>Nästa steg

* [Installera den lokala datagatewayen](/data-integration/gateway/service-gateway-install)

Fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
