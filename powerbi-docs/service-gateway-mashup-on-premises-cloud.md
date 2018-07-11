---
title: Slå ihop eller lägga till lokala och molnbaserade datakällor
description: Använd den lokala datagatewayen för att slå ihop eller lägga till lokala och molnbaserade datakällor i samma fråga.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 06/06/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2547be7f7bdadb7f991db54230d4fd791941838d
ms.sourcegitcommit: 127df71c357127cca1b3caf5684489b19ff61493
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37600077"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>Slå ihop eller lägga till lokala och molnbaserade datakällor

Med den lokala datagatewayen kan du slå ihop eller lägga till lokala och molnbaserade datakällor i samma fråga. Detta är praktiskt om du vill kombinera data från flera källor utan att använda separata frågor.

## <a name="prerequisites"></a>Förutsättningar

- En [gateway som har installerats](service-gateway-install.md) på en lokal dator.
- En Power BI Desktop-fil med frågor som kombinerar lokala och molnbaserade datakällor.

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

     ![Datamängdsinställningar](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

7. När du har angett autentiseringsuppgifter för molnet kan du uppdatera datauppsättningen med hjälp av alternativet **Uppdatera nu**, eller schemalägga en regelbunden uppdatering.


## <a name="next-steps"></a>Nästa steg

Mer information om datauppdatering för gateways finns i [Använda datakällan med schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md#using-the-data-source-for-scheduled-refresh).