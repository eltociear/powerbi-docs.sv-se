---
title: 'Snabbstart: Installera Power BI-rapportserver'
description: Det går mycket snabbt att installera Power BI-rapportservern. Att hämta, installera och konfigurera tar bara några minuter.
services: powerbi
documentationcenter: ''
author: maggiesMSFT
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
ms.date: 03/19/2018
ms.author: maggies
ms.openlocfilehash: 625864384f73260ec0f62b74ff9a95e966289da0
ms.sourcegitcommit: 93e7362fc47319959b6992dfd037effdf831d010
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2018
---
# <a name="quickstart-install-power-bi-report-server"></a>Snabbstart: Installera Power BI-rapportserver
Det går mycket snabbt att installera Power BI-rapportservern. Att hämta, installera och konfigurera tar bara några minuter.

Det här är en snabbtitt på hur du installerar en rapportserver om du bara vill komma igång och köra en ny server. Mer detaljerad information om hur du installerar rapportservern finns i [Installera Power BI-rapportserver](install-report-server.md).

## <a name="video-install-power-bi-report-server"></a>Video: Installera Power BI-rapportserver

<iframe width="640" height="360" src="https://www.youtube.com/embed/zacaEb9A4F0?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="before-you-begin"></a>Innan du börjar
Innan du installerar Power BI-rapportservern rekommenderar vi att du granskar [maskin- och programvarukraven för att installera Power BI-rapportservern](system-requirements.md).

## <a name="step-1-download"></a>Steg 1: Ladda ned

Om du vill ladda ned Power BI-rapportservern och Power BI Desktop som är optimerad för Power BI-rapportservern går du till [Lokal rapportering med Power BI-rapportserver](https://powerbi.microsoft.com/report-server/) och väljer **Ladda ned kostnadsfri utvärderingsversion**.

Följ instruktionerna för att ladda ned installationsfilerna lokalt för Power BI-rapportservern. 

![Hämta Power BI-rapportserver](media/quickstart-install-report-server/download-pbireportserver.png)

## <a name="step-2-run-installer"></a>Steg 2: Kör installationsprogrammet
Kör PowerBIReportServer.exe-filen som du hämtade och gå igenom installationsskärmarna. Du har möjlighet att välja installationssökväg samt den version som du vill installera. Du kan välja mellan en utvärderingsversion som upphör att gälla inom 180 dagar, en utvecklarversion eller att ange en produktnyckel.

![Installera Power BI-rapportserver](media/quickstart-install-report-server/pbireportserver-install.png)

## <a name="step-3-configure-the-server"></a>Steg 3: Konfigurera servern
När du är klar med installationen kör du konfigurationshanteraren för att slutföra konfigurationen av servern. Du behöver skapa en databas till rapportserverkatalogen samt bekräfta URL:erna för webbportalen och webbtjänsten.

![Konfigurera Power BI-rapportserver](media/quickstart-install-report-server/pbireportserver-configure.png)

## <a name="step-4-browse-to-web-portal"></a>Steg 4: Bläddra till webbportalen
Nu när du har konfigurerat bör du kunna öppna en webbläsare till webbportalen för servern. Som standard blir detta `http://localhost/reports`. Du kommer även att kunna bläddra med namnet på datorn i stället för att ange localhost som standard under förutsättning att du inte blockeras av någon typ av brandvägg.

![Webbportalen för Power BI-rapportserver](media/quickstart-install-report-server/web-portal.png)

## <a name="next-steps"></a>Nästa steg
[Handbok för administratör](admin-handbook-overview.md)  
[Så här hittar du rapportserverns produktnyckel](find-product-key.md)  
[Installera Power BI-rapportserver](install-report-server.md)  
[Installera Power BI Desktop som har optimerats för Power BI-rapportservern](install-powerbi-desktop.md)  
[Webbläsarstöd för Power BI-rapportserver](browser-support.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

