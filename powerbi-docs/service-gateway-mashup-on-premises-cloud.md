---
title: Slå ihop eller lägga till lokala och molnbaserade datakällor
description: Använd den lokala datagatewayen för att slå ihop eller lägga till lokala och molnbaserade datakällor i samma fråga.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 39f5a01a396e45207777b1a5e58e73808ddf3f88
ms.sourcegitcommit: a58461fe7dfa65c751490b52de5fc73f8e69a17f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68352167"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>Slå ihop eller lägga till lokala och molnbaserade datakällor

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Med den lokala datagatewayen kan du sammanslå eller lägga till lokala och molnbaserade datakällor i samma fråga. Detta är praktiskt om du vill kombinera data från flera källor utan att använda separata frågor.

>[!NOTE]
>Den här artikeln gäller endast datamängder som har molnbaserade och lokala datakällor som sammanslagits eller lagts till i en enda fråga. För datamängder som innehåller separata frågor – en som ansluter till en lokal källa plats och en annan som ansluter till en molndatakälla – körs inte den fråga som använder molndatakällan via gatewayen.

## <a name="prerequisites"></a>Förutsättningar

- En [gateway som har installerats](/data-integration/gateway/service-gateway-install) på en lokal dator.
- En Power BI Desktop-fil med frågor som kombinerar lokala och molnbaserade datakällor.

>[!NOTE]
>För att få åtkomst till molndatakällor måste du se till att gatewayen har åtkomst till de datakällorna.

1. Välj kugghjulsikonen ![Inställningar](media/service-gateway-mashup-on-premises-cloud/icon-gear.png) > **Hantera gatewayer** i det övre högra hörnet av Power BI-tjänsten.

    ![Hantera gatewayer](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. Välj den gateway som du vill konfigurera.

3. Välj **Tillåt att användarens datakällor i molnet uppdateras via det här gatewayklustret** > **Använd** under **Inställningar för gatewaykluster**.

    ![Uppdatera via gatewayklustret](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. Lägg till [lokala datakällor](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source) som används i dina frågor under gatewayklustret. Du behöver inte lägga till de molnbaserade datakällorna här.

5. Ladda upp Power BI Desktop-filen med frågorna som kombinerar lokala och molnbaserade datakällor till Power BI-tjänsten.

6. På sidan **Datamängdsinställningar** för den nya datauppsättningen:

   - Som lokal källa väljer du gatewayen som associeras med den här datakällan.

   - Redigera autentiseringsuppgifterna för den molnbaserade datakällan efter behov under **Autentiseringsuppgifter för datakälla**.

    Se till att sekretessnivåer för både molndatakällor och lokala datakällor är korrekt inställda för att säkerställa att kopplingarna hanteras på ett säkert sätt.

     ![Datamängdsinställningar](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

7. När du har angett autentiseringsuppgifter för molnet kan du uppdatera datauppsättningen med hjälp av alternativet **Uppdatera nu**, eller schemalägga en regelbunden uppdatering.

## <a name="next-steps"></a>Nästa steg

Mer information om datauppdatering för gateways finns i [Använda datakällan med schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md#using-the-data-source-for-scheduled-refresh).
