---
title: "Lösa problem när du startar Power BI Desktop"
description: "Lösa problem när du startar Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 43263afb63fa0350a240cae602f4a2acf8ef8edd
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>Lösa problem när Power BI Desktop inte startas
I **Power BI Desktop** kan användare som har installerat och som kör tidigare versioner av den **lokala Power BI-datagatewayen** blockeras från att starta Power BI Desktop, på grund av administrativa principbegränsningar som den lokala Power BI-gatewayen har infört för namngivna pipes på den lokala datorn. 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Lösa problem med lokal datagateway och Power BI Desktop
Det finns tre alternativ för att lösa problemet som är kopplat till den lokala datagatewayen och göra det möjligt för Power BI Desktop att starta:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Lösning 1: Installera den senaste versionen av den lokala Power BI-datagatewayen
Den senaste versionen av den lokala Power BI-datagatewayen inför inte begränsningar för namngivna pipes på den lokala datorn och gör att Power BI Desktop kan starta korrekt. Om du behöver fortsätta använda den lokala Power BI-datagatewayen är detta den rekommenderade lösningen. Du kan ladda ned den senaste versionen av den lokala Power BI-datagatewayen från [den här platsen](https://go.microsoft.com/fwlink/?LinkId=698863). Observera att länken är en direkt nedladdningslänk till installationsprogrammet.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>Lösning 2: Avinstallera eller stoppa Windows-tjänsten för den lokala Power BI-datagatewayen
Om du inte längre behöver den lokala Power BI-datagatewayen kan du avinstallera den eller stoppa Windows-tjänsten för den lokala Power BI-datagatewayen, vilket tar bort principbegränsningen och gör att Power BI Desktop kan starta.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Lösning 3: Kör Power BI Desktop med administratörsprivilegier
Du kan också starta Power BI Desktop som administratör, vilket även låter Power BI Desktop starta. Vi rekommenderar ändå att du installerar den senaste versionen av den lokala Power BI-datagatewayen, vilket beskrivs tidigare i den här artikeln.

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>Hjälp med andra problem när du startar Power BI Desktop
Vi strävar efter att täcka så många problem med **Power BI Desktop** som möjligt. Vi tittar regelbundet på problem som kan påverka många kunder och inkluderar dem i våra artiklar.

Om problemet som uppstår när du startar **Power BI Desktop** inte är associerat med den lokala datagatewayen eller tidigare lösningar inte fungerar kan du skicka en händelserapport till [Power BI-supporten](https://support.powerbi.com) (https://support.powerbi.com) för att identifiera och lösa problemet.

För andra problem som kan uppstå i framtiden med **Power BI Desktop** (vi hoppas att inga eller ett fåtal uppstår) är det bra att aktivera spårning och samla in loggfiler för att bättre isolera och identifiera problemet. Om du vill aktivera spårning väljer du **Arkiv> Alternativ och inställningar> Alternativ** och välj sedan **Diagnostik**. Kontrollera sedan **Aktivera spårning** under *Diagnostikalternativ*. Vi förstår att **Power BI Desktop** måste köras för att ange detta alternativ, vilket är bättre för framtida problem som är associerade när du startar **Power BI Desktop**.

