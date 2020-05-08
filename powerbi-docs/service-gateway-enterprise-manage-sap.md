---
title: Hantera din datakälla – SAP HANA
description: Hantera den lokala datagatewayen och datakällorna som tillhör denna gateway. Den här artikeln är specifik för SAP HANA.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/16/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: 6c944b52deb72e556506d88f4358af2c816b46fc
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "74698174"
---
# <a name="manage-your-data-source---sap-hana"></a>Hantera din datakälla – SAP HANA

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

När du har [installerat den lokala datagatewayen](/data-integration/gateway/service-gateway-install) behöver du [lägga till datakällor](service-gateway-data-sources.md#add-a-data-source) som kan användas med gatewayen. Den här artikeln handlar om hur du kan arbeta med gatewayer och SAP HANA-datakällor som används för antingen schemalagd uppdatering eller DirectQuery.

## <a name="add-a-data-source"></a>Lägga till en datakälla

Mer information om hur du lägger till en datakälla finns i [Lägga till en datakälla](service-gateway-data-sources.md#add-a-data-source). Välj **SAP HANA** under **Typ av datakälla**.

![Lägga till SAP HANA-datakällan](media/service-gateway-enterprise-manage-sap/datasourcesettings2-sap.png)

När du har valt SAP HANA-datakälltypen fyller du i uppgifterna om **Server**, **Användarnamn** och **Lösenord** för datakällan.

> [!NOTE]
> Alla frågor till datakällan kommer att köras med dessa autentiseringsuppgifter. Mer information om hur autentiseringsuppgifter lagras finns i [Lagra krypterade autentiseringsuppgifter i molnet](service-gateway-data-sources.md#store-encrypted-credentials-in-the-cloud).

![Fylla i inställningarna för datakälla](media/service-gateway-enterprise-manage-sap/datasourcesettings3-sap.png)

När du har fyllt i allt väljer du **Lägg till**. Du kan nu använda datakällan för schemalagd uppdatering eller DirectQuery mot en lokal SAP HANA-server. *Anslutningen lyckades* visas om anslutningen lyckades.

![Visa anslutningsstatus](media/service-gateway-enterprise-manage-sap/datasourcesettings4.png)

### <a name="advanced-settings"></a>Avancerade inställningar

Om du vill kan du konfigurera sekretessnivån för datakällan. Den här inställningen styr hur data kan kombineras. Den används endast vid schemalagd uppdatering. Sekretessnivåinställningen gäller inte för DirectQuery. Mer information om sekretessnivåer för datakälla finns i [Sekretessnivåer (Power Query)](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540).

![Ange sekretessnivån](media/service-gateway-enterprise-manage-sap/datasourcesettings9.png)

## <a name="use-the-data-source"></a>Använda datakällan

När du har skapat datakällan går den att använda med DirectQuery eller med schemalagd uppdatering.

> [!NOTE]
> Server- och databasnamnen måste överensstämma mellan Power BI Desktop och datakällan i den lokala datagatewayen.

Länken mellan din datauppsättning och datakällan i gatewayen är baserad på servernamnet och databasnamnet. Dessa namn måste matcha. Om du exempelvis anger en IP-adress för servernamnet i Power BI Desktop måste du använda den IP-adressen för datakällan i gatewaykonfigurationen. Om du använder *SERVER\INSTANS* i Power BI Desktop, måste du använda den i den datakälla som konfigureras för gatewayen.

Det här kravet gäller både DirectQuery och schemalagd uppdatering.

### <a name="use-the-data-source-with-directquery-connections"></a>Använda datakällan med DirectQuery-anslutningar

Se till att server- och databasnamnen överensstämmer mellan Power BI Desktop och den konfigurerade datakällan för gatewayen. Du behöver även kontrollera att användaren finns med på fliken **Användare** för datakällan för att DirectQuery-datamängder ska kunna publiceras. Valet för DirectQuery uppstår i Power BI Desktop när du importerar data första gången. Mer information om hur DirectQuery används finns i [Använda DirectQuery i Power BI Desktop](desktop-use-directquery.md).

När du har publicerat, antingen från Power BI Desktop eller **Hämta Data**, borde dina rapporter fungera. Det kan ta ett par minuter efter att du har skapat datakällan i gatewayen innan anslutningen kan användas.

### <a name="use-the-data-source-with-scheduled-refresh"></a>Använda datakällan med schemalagd uppdatering

Om du finns med på fliken **Användare** för den datakälla som konfigurerats i gatewayen, och om servernamnet och databasnamnet matchar, visas gatewayen som ett alternativ för användning med schemalagd uppdatering.

![Visa användarna](media/service-gateway-enterprise-manage-sap/powerbi-gateway-enterprise-schedule-refresh.png)

## <a name="next-steps"></a>Nästa steg

* [Felsökning av den lokala datagatewayen](/data-integration/gateway/service-gateway-tshoot)
* [Felsöka gatewayer – Power BI](service-gateway-onprem-tshoot.md) 

Fler frågor? Fråga [Power BI Community](https://community.powerbi.com/).

