---
title: Så här uppdaterar du dina innehållspaketautentiseringsuppgifter för Xero
description: Om du använder Xero Power BI-innehållspaketet kan du ha stött på ett problem med innehållspaketets dagliga uppdateringar på grund av en nyligen inträffad incident i Power BI-tjänsten.
author: SarinaJoan
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/10/2017
ms.author: sarinas
LocalizationGroup: Troubleshooting
ms.openlocfilehash: a1697bfce1db1ca92d50bfb83210d21b2820fdae
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86263697"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>Så här uppdaterar du dina innehållspaketautentiseringsuppgifter för Xero om uppdateringen misslyckades
Om du använder Xero Power BI-innehållspaketet kan du ha stött på problem med innehållspaketets dagliga uppdateringar på grund av en nyligen inträffad incident i Power BI-tjänsten.

Du kan se om ditt innehållspaket har uppdaterats genom att kontrollera den senaste uppdateringsstatusen för din Xero-datauppsättning som visas på skärmbilden nedan.

![Skärmbild av dialogrutan Xero med uppdateringsstatus för din Xero-datamängd.](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

Om du ser att uppdateringen har misslyckats, så förnya ditt innehållspakets autentiseringsuppgifter genom att följa dessa steg.

1. Klicka på **Fler alternativ** (...) bredvid Xero-datamängden och klicka sedan på **Schemalägg uppdatering**. Då öppnas inställningssidan för Xero-innehållspaketet.
   
    ![Skärmbild av dialogrutan Xero där Schemalägg uppdatering är valt.](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. Välj **Datakällans autentiseringsuppgifter** > **Redigera autentiseringsuppgifter** på sidan **Inställningar för Xero**.
   
    ![Skärmbild av dialogrutan Inställningar för Xero där Redigera autentiseringsuppgifter är valt.](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. Ange ditt organisationsnamn > **Nästa**.
   
    ![Skärmbild av dialogrutan Konfigurera Xero som visar organisationens namn.](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Logga in med ditt Xero-konto.
   
    ![Skärmbild av dialogrutan för inloggning i Xero som visar hur du loggar in på ditt Xero-konto.](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. Nu när dina autentiseringsuppgifter har uppdaterats, så kontrollera att uppdateringsschemat är inställt på att köras varje dag. Kontrollera detta genom att klicka på **Fler alternativ** (...) bredvid Xero-datauppsättningen och sedan klicka på **Schemalägg uppdatering** igen.
   
    ![Skärmbild av dialogrutan Schemalägg uppdatering som visar uppdateringsfrekvens och tidszon.](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. Du kan också välja att uppdatera datauppsättningen direkt. Klicka på **Fler alternativ** (...) bredvid Xero-datamängden och klicka sedan på **Uppdatera nu**.
   
    ![Skärmbild av dialogrutan Xero med Uppdatera nu valt.](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

Om du fortfarande har uppdateringsproblem så tveka inte att kontakta oss på [https://support.powerbi.com](https://support.powerbi.com) 

Om du vill veta mer om Xero-innehållspaketet för Power BI kan du besöka hjälpsidan för [Xero-innehållspaket](service-connect-to-xero.md).

### <a name="next-steps"></a>Nästa steg
* Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

