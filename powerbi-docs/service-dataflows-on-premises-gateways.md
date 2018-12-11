---
title: Använda dataflöden med lokala datakällor
description: Lär dig hur du använder lokala data i dataflöden
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 82cc459bcfd33d2aa576529899b7f893b0854c37
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53180310"
---
# <a name="using-dataflows-with-on-premises-data-sources-preview"></a>Använda dataflöden med lokala datakällor (förhandsversion)

Med **dataflöden**, kan du skapa en samling av data från olika källor, rensa data, omvandla dem och sedan läsa in dem till Power BI-lagring. När du skapar dataflöde kan du använda lokala datakällor. Den här artikeln visar krav som är associerade med att skapa dataflöden och hur din **Företagsgateway** måste vara konfigurerad för att aktivera dessa anslutningar.

![Dataflöden och gatewayar](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

> [!NOTE]
> Funktionen dataflöden är en förhandsversion och kan komma att ändras och uppdateras innan den är allmänt tillgänglig.
 
## <a name="configuring-an-enterprise-gateway-for-use-with-dataflows"></a>Konfigurera en företagsgateway för användning med dataflöden

Om du vill använda en lokal datakälla i ett dataflöde, måste alla användare som skapar dataflödet ha en **Företagsgateway** installerad och konfigurerad. Den användare som skapar dataflödet måste också vara administratör för Företagsgatewayen för att kunna använda denna gateway för ett dataflöde.

> [!NOTE]
> Dataflöden stöds endast med företagsgateway.

## <a name="using-an-on-premises-data-source-in-a-dataflow"></a>Använda en lokal datakälla i ett dataflöde

När du skapar ett dataflöde, välj en lokal datakälla från listan över datakällor, såsom visas i följande bild.

![Välj en lokal datakälla](media/service-dataflows-onpremises-gateways/onpremises-gateways_02a.png)

När du har gjort dina val uppmanas du att ange anslutningsinformationen för den företagsgateway som ska användas för att få åtkomst till lokala data. Du måste välja gatewayen och ange autentiseringsuppgifter för den valda gatewayen. Endast gatewayar som användaren är administratör för visas i den nedrullningsbara listan.

![Ange anslutningsinformationen](media/service-dataflows-onpremises-gateways/onpremises-gateways_03.png)

## <a name="monitoring-your-gateway"></a>Övervaka din gateway

Du kan övervaka din företagsgateway för ett dataflöde på samma sätt som du övervakar gatewayer för en datauppsättning.

På skärmen för dataflödesinställningar i Power BI kan du övervaka status för en dataflödesgateway och tilldela en gateway till dataflödet, enligt följande bild.

![Övervaka gatewayen](media/service-dataflows-onpremises-gateways/onpremises-gateways_01.png)

## <a name="changing-a-gateway"></a>Ändra en gateway

Du kan ändra den företagsateway som används för ett viss dataflöde på två sätt:

1. **Från redigeringsverktyget** – Du kan ändra den gateway som tilldelats till alla dina frågor med hjälp av redigeringsverktyget för dataflödet.

    > [!NOTE]
    > Dataflödet försöker hitta eller skapa nödvändiga datakällor med hjälp av den nya gatewayen. Om den inte gör det, kan du inte ändra gatewayen förrän alla nödvändiga dataflöden är tillgängliga från den valda gatewayen.

2. **Från inställningsskärmen** – Du kan ändra den tilldelade gatewayen med hjälp av inställningsskärmen för dataflöde i Power BI-tjänsten.

Mer information om företagsgatewayer finns i [Lokal datagateway](service-gateway-onprem.md).

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Det finns några kända begränsningar för användning av företagsgatewayer och dataflöden:

* Varje dataflöde kan endast använda en gateway. Därmed måste alla frågor konfigureras med hjälp av samma gateway.
* Att ändra gatewayen påverkar hela dataflödet.
* Om flera gatewayar krävs är det bästa sättet att skapa flera dataflöden (ett för varje gateway) och använda funktionerna för beräkning eller entitetsreferens för att förena data.
* Dataflöden stöds endast med företagsgateway. Personliga gatewayer kan inte väljas i nedrullningsbara listor och inställningsskärmar.


## <a name="next-steps"></a>Nästa steg

Den här artikeln tillhandahåller information om hur du använder en lokal datakälla för dataflöden och hur du använder och konfigurerar gatewayer för att komma åt dessa data. Följande artiklar kan också vara till hjälp

* [Dataförberedelser med självbetjäning för dataflöden](service-dataflows-overview.md)
* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium (förhandsversion)](service-dataflows-computed-entities-premium.md)
* [Resurser för utvecklare för Power BI-dataflöden (förhandsversion)](service-dataflows-developer-resources.md)

Mer information om Power Query och schemalagd uppdatering finns i följande artiklar:
* [Frågeöversikt i Power BI Desktop](desktop-query-overview.md)
* [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md)

Mer information om Common Data Service finns i dess översiktsartikel:
* [Common Data Service – översikt ](https://docs.microsoft.com/powerapps/common-data-model/overview)

