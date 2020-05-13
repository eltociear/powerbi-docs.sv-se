---
title: Ansluta till uppföljningsrapport för COVID-19 för USA
description: Så här hämtar och installerar du mallappen för fall av COVID-19 i USA och ansluter till data.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/05/2020
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 97e0a4f6e522997e6f132d1c3dbc493188ba66ba
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83275488"
---
# <a name="connect-to-the-covid-19-us-tracking-report"></a>Ansluta till uppföljningsrapport för COVID-19 för USA
I den här artikeln beskrivs hur du installerar mallappen för uppföljningsrapporten för COVID-19 och ansluter till datakällorna.

![COVID-19 – uppföljningsrapport för USA](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-title-screen.png)

Mer detaljerad information om själva rapporten, inklusive ansvarsfriskrivningar och information om data finns i [COVID–19-spårningsexempel för myndigheter i USA på lokal och delstatsnivå](../create-reports/sample-covid-19-us.md).

När du har installerat mallappen och anslutit till datakällorna kan du anpassa rapporten efter dina behov. Sedan kan du distribuera den som en app till medarbetare i din organisation.

## <a name="install-the-app"></a>Installera appen

1. Klicka på följande länk för att gå till appen: [Mallapp för uppföljningsrapport för COVID-19 för USA](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms)

1. När du är på appens AppSource-sida klickar du på [**Hämta nu**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms).

    [![Uppföljningsrapport för COVID-19 i AppSource](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-appsource-icon.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.covid19ms)

1. Klicka på **Installera** när du uppmanas att göra det. När appen har installerats visas den på sidan Appar.

   ![COVID-19 – uppföljningsrapport för USA på sidan Appar](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>Anslut till datakällor

1. Välj ikonen på sidan Appar för att öppna appen.

1. På välkomstskärmen som visas väljer du **Anslut**.

   ![Välkomstskärmen för mallappen](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-splash-screen.png)

1. Två dialogrutor för inloggning visas, den ena efter den andra. Ange sekretessnivån Offentlig i båda dialogrutorna.

   ![COVID-19 – uppföljningsrapport för USA – dialogruta för inloggning](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-signin-dialog.png)

   Rapporten ansluter till datakällorna och fylls med aktuella data. Under den här tiden körs aktivitetsövervakaren.

   ![Uppdatering pågår för uppföljningsrapporten för COVID-19 för USA](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>Schemalägga rapportuppdatering

När datauppdateringen har slutförts kommer du att vara i den arbetsyta som är associerad med appen. [Skapa ett uppdateringsschema](../connect-data/refresh-scheduled-refresh.md) för att hålla rapportdata uppdaterade.

## <a name="customize-and-share"></a>Anpassa och dela

Mer information finns i [Anpassa och dela appen](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app). Läs [friskrivningar för rapporter](../create-reports/sample-covid-19-us.md#disclaimers) innan du publicerar eller distribuerar appen.

## <a name="next-steps"></a>Nästa steg
* [COVID – 19 spårningsexempel för myndigheter i USA på lokal och delstatsnivå](../create-reports/sample-covid-19-us.md)
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
* [Vad är Power BI-mallappar?](../connect-data/service-template-apps-overview.md)
* [Installera och distribuera mallappar i din organisation](../connect-data/service-template-apps-install-distribute.md)
