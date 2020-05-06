---
title: Anslut till instrumentpanelen för regional akutrespons
description: Så här hämtar och installerar du mallappen Instrumentpanel för beslutsstöd för regional akutrespons för COVID-19, och ansluter till data
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/24/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 6af8568dc39544ce064643c8dfb80fa2932cf13a
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82149680"
---
# <a name="connect-to-the-regional-emergency-response-dashboard"></a>Anslut till instrumentpanelen för regional akutrespons
Instrumentpanelen för regional akutrespons är rapporteringskomponenten i [Microsoft Power Platforms lösning för regional akutrespons](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview). Regionala organisationsadministratörer kan visa instrumentpanelen i sin Power BI-klientorganisation, så att de snabbt kan visa viktiga data och mått som kan hjälpa dem att fatta effektiva beslut.

![Apprapport för Instrumentpanel för regional akutrespons](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-report.png)

Den här artikeln beskriver hur du installerar appen för regional akutrespons med hjälp av mallappen Instrumentpanel för regional akutrespons och hur du ansluter till datakällorna.

Detaljerad information om vad som visas på instrumentpanelen finns i [Få insikter](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights).

När du har installerat mallappen och anslutit till datakällorna kan du anpassa rapporten efter dina behov. Sedan kan du distribuera den som en app till medarbetare i din organisation.

## <a name="prerequisites"></a>Förutsättningar

Innan du installerar den här mallappen måste du först installera och konfigurera [lösningen Regional akutrespons](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy). När du installerar den här lösningen skapas de referenser till datakällor som behövs för att fylla appen med data.

Notera [URL:en för din Common Data Services-miljöinstans](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/deploy#step-5-configure-and-publish-power-bi-dashboard) när du installerar lösningen Regional akutrespons. Du behöver den för att ansluta mallappen till data.

## <a name="install-the-app"></a>Installera appen

1. Klicka på följande länk för att gå till appen: [Mallappen Instrumentpanel för regional akutrespons](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. På AppSource-sidan för appen väljer du [**Hämta nu**](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response).

    [![Appen Instrumentpanel för regional akutrespons i AppSource](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-appsource-get-it-now.png)](https://appsource.microsoft.com/product/power-bi/powerapps_cxo.regional_response)

1. Välj **installera**. 

    ![Installera appen Instrumentpanel för regional akutrespons](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-select-install.png)

    När appen har installerats visas den på sidan Appar.

   ![Appen Instrumentpanel för regional akutrespons på appsidan](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Anslut till datakällor

1. Välj ikonen på sidan Appar för att öppna appen.

1. På välkomstskärmen väljer du **Utforska**.

   ![Välkomstskärmen för mallappen](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-splash-screen.png)

   Appen öppnas och visar exempeldata.

1. Välj länken **Anslut dina data** på banderollen längst upp på sidan.

   ![Länken Anslut dina data i appen Instrumentpanel för regional akutrespons](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-connect-data.png)

1. I dialogrutan som visas skriver du [URL:en för din Common Data Service-miljöinstans](https://docs.microsoft.com/powerapps/sample-apps/emergency-response/deploy-configure#publish-the-power-bi-dashboard). Till exempel: https://[myenv].crm.dynamics.com. När du är klar klickar du på **Nästa**.

   ![URL-dialogrutan i appen Instrumentpanel för regional akutrespons](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-url-dialog.png)

1. I nästa dialogruta som visas anger du **OAuth2** som autentiseringsmetod. Du behöver inte göra något med sekretessnivåinställningen.

   Välj **Logga in**.

   ![Autentiseringsdialogrutan i appen Instrumentpanel för regional akutrespons](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-authentication-dialog.png)

1. Logga in på Power BI på Microsoft-inloggningsskärmen.

   ![Microsoft-inloggningsskärm](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-microsoft-login.png)

   När du har loggat in ansluter rapporten till datakällorna och fylls med aktuella data. Under den här tiden körs aktivitetsövervakaren.

   ![Uppdatering pågår i appen Instrumentpanel för regional akutrespons](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Schemalägga rapportuppdatering

När datauppdateringen har slutförts [skapar du ett uppdateringsschema](../refresh-scheduled-refresh.md) för att hålla rapportdata uppdaterade.

1. I det översta rubrikfältet väljer du **Power BI**.

   ![Dynamiska länkar i Power BI](media/service-connect-to-regional-emergency-response/service-regional-emergency-response-app-powerbi-breadcrumb.png)

1. I det vänstra navigeringsfönstret letar du reda på arbetsytan Instrumentpanel för regional akutrespons under **Arbetsytor** och följer anvisningarna i artikeln [Konfigurera schemalagd uppdatering](../refresh-scheduled-refresh.md).

## <a name="customize-and-share"></a>Anpassa och dela

Mer information finns i [Anpassa och dela appen](../service-template-apps-install-distribute.md#customize-and-share-the-app). Läs [friskrivningar för rapporter](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/overview#disclaimer) innan du publicerar eller distribuerar appen.

## <a name="next-steps"></a>Nästa steg
* [Förstå Instrumentpanelen för regional akutrespons](https://docs.microsoft.com/powerapps/sample-apps/regional-emergency-response/portals-admin-reporting#get-insights)
* [Konfigurera och läs mer om exempelmallen Kriskommunikation i Power Apps](https://docs.microsoft.com/powerapps/maker/canvas-apps/sample-crisis-communication-app)
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
* [Vad är Power BI-mallappar?](../service-template-apps-overview.md)
* [Installera och distribuera mallappar i din organisation](../service-template-apps-install-distribute.md)
