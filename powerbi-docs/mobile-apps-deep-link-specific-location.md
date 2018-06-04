---
title: Skapa en länk till en specifik plats i Power BI-mobilapparna
description: Lär dig hur du skapar en djuplänk till en specifik instrumentpanel, panel eller rapport i Power BI-mobilappen med en URI (Uniform Resource Identifier).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 3be6882219e23a2d22ee03e6805ce3a1e8e08b8f
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34297732"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Skapa en länk till en specifik plats i Power BI-mobilapparna
Du kan skapa och använda en URI (Uniform Resource Identifier) för att länka till en specifik plats (en *djuplänk*) i Power BI-mobilapparna på alla mobila plattformar: iOS, Android-enheter och Windows 10.

URI-länkar kan peka direkt på instrumentpaneler, paneler och rapporter.

Målet för djuplänken anger formatet på URI:n. Följ dessa steg om du vill skapa djuplänkar till olika platser. 

## <a name="open-the-power-bi-mobile-app"></a>Öppna Power BI-mobilappen
Använd den här URI:n för att öppna Power BI-mobilappen på alla enheter:

    mspbi://app/


## <a name="open-to-a-specific-dashboard"></a>Öppna till en specifik instrumentpanel
Den här URI:n öppnar Power BI-mobilappen i en specifik instrumentpanel:

    mspbi://app/OpenDashboard?DashboardObjectId=<36-character-dashboard-id>

Gå till den specifika instrumentpanelen i Power BI-tjänsten (https://powerbi.com) för att hitta objekt-ID:t på 36 tecken i instrumentpanelen. Exempel finns i det markerade avsnittet under följande URL:

https://powerbi.com/groups/me/dashboards/**61b7e871-cb98-48ed-bddc-6572c921e270**

Om instrumentpanelen finns i en annan grupp än Min arbetsyta kan du lägga till `&GroupObjectId=<36-character-group-id>` före eller efter instrumentpanelens ID. Exempel: 

mspbi://app/OpenDashboard?DashboardObjectId=e684af3a-9e7f-44ee-b679-b9a1c59b5d60 **&GroupObjectId=8cc900cc-7339-467f-8900-fec82d748248**

Observera et-tecknet (&) mellan de två.

## <a name="open-to-a-specific-tile-in-focus"></a>Öppna med en specifik panel i fokus
URI:n öppnar en specifik panel i fokus i Power BI-mobilappen:

    mspbi://app/OpenTile?DashboardObjectId=<36-character-dashboard-id>&TileObjectId=<36-character-tile-id>

Gå till den specifika instrumentpanelen i Power BI-tjänsten (https://powerbi.com) för att hitta objekt-ID:n på 36 tecken för instrumentpanel och panel och öppna panelen i fokusläge. Exempel finns i avsnitten som är markerade för den här URL:n:

https://powerbi.com/groups/me/dashboards/**3784f99f-b460-4d5e-b86c-b6d8f7ec54b7**/tiles/**565f9740-5131-4648-87f2-f79c4cf9c5f5**/infocus

För den här panelen är URI:n:

    mspbi://app/OpenTile?DashboardObjectId=3784f99f-b460-4d5e-b86c-b6d8f7ec54b7&TileObjectId=565f9740-5131-4648-87f2-f79c4cf9c5f5

Observera et-tecknet (&) mellan de två.

Om instrumentpanelen finns i en annan grupp än Min arbetsyta lägger du till `&GroupObjectId=<36-character-group-id>`

## <a name="open-to-a-specific-report"></a>Öppna till en specifik rapport
URI:n öppnar en specifik rapport i Power BI-mobilappen:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>

Gå till den specifika rapporten i Power BI-tjänsten (https://powerbi.com) för att hitta objekt-ID:t på 36 tecken i rapporten. Exempel finns i det markerade avsnittet under följande URL:

https://powerbi.com/groups/me/reports/**df9f0e94-31df-450b-b97f-4461a7e4d300**

## <a name="open-to-a-specific-report-page"></a>Öppna till en viss rapportsida
URI:n öppnar en specifik rapportsida i Power BI-mobilappen:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>&reportPage=ReportSection<number>

Rapportsidan har namnet ”ReportSection” följt av ett tal. Öppna återigen rapporten i Power BI-tjänsten (https://powerbi.com) och gå till den specifika rapportsidan. 

Exempel finns i det markerade avsnittet under följande URL:

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**ReportSection11**

## <a name="open-in-full-screen-mode"></a>Öppna i helskärmsläge
Lägg till parametern i fetstil för att öppna en specifik rapport i helskärmsläge:

    mspbi://app/OpenReport?ReportObjectId=<36-character-report-id>**&openFullScreen=true**

Exempel: 

mspbi://app/OpenReport?ReportObjectId=500217de-50f0-4af1-b345-b81027224033&openFullScreen=true

## <a name="add-context-optional"></a>Lägg till kontext (valfritt)
Du kan också lägga till kontext i strängen. Om du behöver kontakta oss kan vi använda denna kontext för att filtrera våra data till din app. Lägg till `&context=<app-name>` i länken

Exempel finns i det markerade avsnittet under följande URL: 

https://powerbi.com/groups/me/reports/df9f0e94-31df-450b-b97f-4461a7e4d300/**&context=SlackDeepLink**

## <a name="next-steps"></a>Nästa steg
Din feedback hjälper oss att bestämma vad som ska implementeras i framtiden, så glöm inte att rösta för andra funktioner som du skulle vilja se i Power BI-mobilapparna. 

* [Power BI-appar för mobila enheter](mobile-apps-for-mobile-devices.md)
* Följ @MSPowerBI på Twitter
* Delta i konversationen i [Power BI Community](http://community.powerbi.com/)
* [Kom igång med Power BI](service-get-started.md)

