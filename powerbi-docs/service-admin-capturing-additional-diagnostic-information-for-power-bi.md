---
title: Samla in ytterligare diagnostikinformation
description: I dessa anvisningar finns två möjliga alternativ för att samla in ytterligare diagnostikinformation från Power BI-webbklienten manuellt.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/17/2019
ms.author: kfollis
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 670373afb5cb890c87a24a129cd43fde7bd5d892
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698910"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Samla in ytterligare diagnostikinformation för Power BI

Den här artikeln innehåller instruktioner för manuell insamling av ytterligare diagnostikinformation för Power BI-webbklienten.

1. Bläddra till [Power BI](https://app.powerbi.com) med Microsoft Edge eller Internet Explorer.

1. Tryck på **F12** för att öppna utvecklarverktygen för Microsoft Edge.

   ![Skärmbild av fliken Element i utvecklarverktygen för Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Välj fliken **Nätverk**. Den visar en lista över trafik som redan har samlats in.

   ![Skärmbild av fliken Nätverk i utvecklarverktygen för Microsoft Edge.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Du kan:

    * Bläddra i fönstret och återskapa alla problem som du stöter på.

    * Dölj och visa fönstret för utvecklarverktyg när som helst under sessionen genom att trycka på F12.

1. När du vill sluta profilera sessionen kan du välja den röda rutan på fliken **Nätverk** i området för utvecklarverktyg.

   ![Skärmbild av fliken Nätverk i utvecklarverktygen för Microsoft Edge med knappen Stoppa framhävd.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Välj diskettikonen för att exportera data som en HTTP-arkivfil (HAR).

   ![Skärmbild av fliken Nätverk i utvecklarverktygen för Microsoft Edge med diskettikonen framhävd.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Ange ett filnamn och spara HAR-filen.

    HAR-filen innehåller all information om nätverksbegäranden mellan webbläsarfönstret och Power BI, däribland:

    * Aktivitets-ID:n för varje begäran.

    * Den exakta tidsstämpeln för varje begäran.

    * All felinformation som returneras till klienten.

    Den här spårningen innehåller även data som används för att fylla i de visuella objekt som visas på skärmen.

1. Du kan skicka HAR-filen till supporten för granskning.

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
