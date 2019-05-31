---
title: Samla in ytterligare diagnostikinformation
description: I dessa anvisningar finns två möjliga alternativ för att samla in ytterligare diagnostikinformation från Power BI-webbklienten manuellt.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100236"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Samla in ytterligare diagnostikinformation för Power BI

Den här artikeln innehåller anvisningar för att samla in ytterligare diagnostikinformation från Power BI-webbklienten manuellt.

1. Bläddra till [Power BI](https://app.powerbi.com) med Microsoft Edge eller Internet Explorer.

1. Tryck på **F12** att öppna Microsoft Edge-utvecklingsverktyg.

   ![Skärmbild av Microsoft Edge Developer tools element-fliken.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Välj fliken **Nätverk**. Den visar en lista över trafik som redan har samlats in.

   ![Skärmbild av Microsoft Edge Developer verktygsflik till nätverket.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Du kan:

    * Bläddra i fönstret och återskapa alla problem som du kan stöta på.

    * Dölja och visa utvecklaren fönstret när som helst under sessionen genom att trycka på F12.

1. Om du vill stoppa Profileringen sessionen, du kan välja den röda rutan på den **nätverk** fliken i utvecklarens verktyg området.

   ![Skärmbild av Microsoft Edge Developer tools fliken nätverk med ett anrop från stopp-knappen.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Välj fil att exportera data som en HTTP-Arkiv (HAR)-filen.

   ![Skärmbild av Microsoft Edge Developer tools fliken nätverk med en uppmaning av diskett-ikonen.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Ange ett filnamn och spara HAR-filen.

    HAR-filen innehåller all information om nätverksbegäranden mellan webbläsarfönstret och Power BI, inklusive:

    * Aktiviteten ID: N för varje begäran.

    * Exakt tidsstämpel för varje begäran.

    * Den felinformation som returnerats till klienten.

    Den här spårningen innehåller även data som används för att fylla i de visuella objekt som visas på skärmen.

1. Du kan skicka HAR-filen till supporten för granskning.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)
