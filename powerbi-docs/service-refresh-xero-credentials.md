---
title: Så här uppdaterar du dina innehållspaketautentiseringsuppgifter för Xero
description: Om du använder Xero Power BI-innehållspaketet kan du ha stött på ett problem med innehållspaketets dagliga uppdateringar på grund av en nyligen inträffad incident i Power BI-tjänsten.
author: SarinaJoan
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: sarinas
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 0a7268c041976a3cab3316c91470c1378a3685f5
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73871662"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>Så här uppdaterar du dina innehållspaketautentiseringsuppgifter för Xero om uppdateringen misslyckades
Om du använder Xero Power BI-innehållspaketet kan du ha stött på problem med innehållspaketets dagliga uppdateringar på grund av en nyligen inträffad incident i Power BI-tjänsten.

Du kan se om ditt innehållspaket har uppdaterats genom att kontrollera den senaste uppdateringsstatusen för din Xero-datauppsättning som visas på skärmbilden nedan.

![](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

Om du ser att uppdateringen har misslyckats, så förnya ditt innehållspakets autentiseringsuppgifter genom att följa dessa steg.

1. Klicka på **Fler alternativ** (...) bredvid Xero-datamängden och klicka sedan på **Schemalägg uppdatering**. Då öppnas inställningssidan för Xero-innehållspaketet.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. Välj **Datakällans autentiseringsuppgifter** > **Redigera autentiseringsuppgifter** på sidan **Inställningar för Xero**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. Ange ditt organisationsnamn > **Nästa**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Logga in med ditt Xero-konto.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. Nu när dina autentiseringsuppgifter har uppdaterats, så kontrollera att uppdateringsschemat är inställt på att köras varje dag. Kontrollera detta genom att klicka på **Fler alternativ** (...) bredvid Xero-datauppsättningen och sedan klicka på **Schemalägg uppdatering** igen.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. Du kan också välja att uppdatera datauppsättningen direkt. Klicka på **Fler alternativ** (...) bredvid Xero-datamängden och klicka sedan på **Uppdatera nu**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

Om du fortfarande har uppdateringsproblem så tveka inte att kontakta oss på [https://support.powerbi.com](https://support.powerbi.com) 

Om du vill veta mer om Xero-innehållspaketet för Power BI kan du besöka hjälpsidan för [Xero-innehållspaket](service-connect-to-xero.md).

### <a name="next-steps"></a>Nästa steg
* Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

