---
title: Samla in ytterligare diagnostikinformation
description: Samla in ytterligare diagnostikinformation
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 9aef989b4b61ce8c9d11fd4275d68c867791f644
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2018
---
# <a name="capturing-additional-diagnostic-information"></a>Samla in ytterligare diagnostikinformation
## <a name="capturing-additional-diagnostic-information-for-power-bi"></a>Samla in ytterligare diagnostikinformation för Power BI
I dessa anvisningar finns två möjliga alternativ för att samla in ytterligare diagnostikinformation från Power BI-webbklienten manuellt.  Du behöver bara använda ett av dessa alternativ.

## <a name="network-capture---edge--internet-explorer"></a>Nätverksklipp – Microsoft Edge och Internet Explorer
1. Bläddra till [Power BI](https://app.powerbi.com) med Microsoft Edge eller Internet Explorer.
2. Öppna utvecklingsverktygen i Microsoft Edge genom att trycka på F12.
3. Fönstret Utvecklingsverktyg öppnas: 
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)
4. Gå till fliken Nätverk. Den visar en lista över trafik som redan har samlats in. 
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)
5. Du kan bläddra i fönstret och återskapa alla problem som du hittar. Du kan dölja och visa fönstret Utvecklingsverktyg när som helst under sessionen genom att trycka på F12.
6. Markera den röda rutan på nätverksfliken i området för utvecklingsverktygen om du vill stoppa insamlingen.
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)
7. Välj diskettikonen för att **Exportera som HAR**
   
   ![](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)
8. Ange ett filnamn och spara HAR-filen.
   
    HAR-filen innehåller all information om nätverksbegäranden mellan webbläsarfönstret och Power BI.  Detta inkluderar aktivitets-ID:n för varje begäran, exakt tidsstämpel för varje begäran och eventuell felinformation som returnerats till klienten.  Den här spårningen innehåller även data som används för att fylla i de visuella objekt som visas på skärmen.
9. Du kan skicka HAR-filen till supporten för granskning.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

