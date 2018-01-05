---
title: "Uppdatera en datauppsättning som skapats från en Power BI Desktop-fil – lokalt"
description: "Uppdatera en datauppsättning som skapats från en Power BI Desktop-fil på en lokal disk"
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
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 3ed7e6dfafe439671d0890154e6b02e1ce81c812
ms.sourcegitcommit: b3ee37e1587f1269ee7dd9daf1685a06dea3b50c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2017
---
# <a name="refresh-a-dataset-created-from-a-power-bi-desktop-file-on-a-local-drive"></a>Uppdatera en datauppsättning som skapats från en Power BI Desktop-fil på en lokal disk
## <a name="whats-supported"></a>Vad stöds?
I Power BI stöds Uppdatera nu och Schemalägg uppdatering för datauppsättningar som skapas från Power BI Desktop-filer som importerats från en lokal enhet där Hämta data/Frågeredigeraren används för att ansluta till och läsa in data från någon av följande datakällor:

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
* Alla datakällor online som visas i Hämta data och Frågeredigeraren i Power BI Desktop.
* Alla lokala datakällor som visas i Hämta data och Frågeredigeraren i Power BI Desktop, förutom Hadoop-filer (HDFS) och Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

> [!NOTE]
> En gateway måste vara installerad och köras för att Power BI ska kunna ansluta till lokala datakällor och uppdatera datauppsättningen.
> 
> 

Du kan utföra manuell engångsuppdatering direkt i Power BI Desktop genom att välja Uppdatera på menyfliken Start. När du väljer Uppdatera här kommer data i *filens* modell att uppdateras med uppdaterade data från den ursprungliga datakällan. Den här typen av uppdatering sker helt inom Power BI Desktop programmet och skiljer sig från manuell eller schemalagd uppdatering i Power BI och det är viktigt att förstå skillnaden.

![](media/refresh-desktop-file-local-drive/pbix-refresh.png)

När du importerar Power BI Desktop-fil från en lokal enhet, läses data, tillsammans med annan information om modellen, in i en datauppsättning i Power BI-tjänsten. I Power BI-tjänsten, inte Power BI Desktop, kan du behöva uppdatera data i datauppsättningen eftersom det är dessa som dina rapporter i Power BI-tjänsten bygger på. Eftersom datakällorna är externa kan du manuellt uppdatera datauppsättningen genom att använda **Uppdatera nu**. Du kan också konfigurera ett uppdateringsschema med hjälp av **Schemalägg uppdatering**.

När du uppdaterar datauppsättningen ansluter Power BI inte till filen på den lokala enheten för att fråga efter uppdaterade data. Den använder informationen i datauppsättningen för att ansluta direkt till datakällor för att söka efter uppdaterade data som den sedan läser in i datauppsättningen.

> [!NOTE]
> Uppdaterade data i datauppsättningen synkroniseras inte tillbaka till filen på den lokala enheten.
> 
> 

## <a name="how-do-i-schedule-refresh"></a>Hur gör jag för att schemalägga uppdateringar?
När du konfigurerar ett uppdateringsschema, ansluter Power BI direkt till datakällorna med anslutningsinformationen och autentiseringsuppgifterna i datauppsättningen för att fråga efter uppdaterade data, och läser sedan in uppdaterade data i datauppsättningen. Även alla visualiseringar i rapporter och på instrumentpaneler baserade på den datauppsättningen i Power BI-tjänsten uppdateras.

Mer information om hur du konfigurerar schemalagda uppdateringar finns i [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Om något går fel
Om något går fel beror det vanligtvis på att Power BI inte kan logga in till datakällor, eller att gatewayen är offline om datauppsättningen ansluter till en lokal datakälla. Kontrollera att Power BI kan logga in till datakällor. Om det lösenord som du använder för att logga in till en datakälla ändras eller om Power BI loggas ut från en datakälla, bör du försöka logga in till dina datakällor igen i datakällans autentiseringsuppgifter.

Se till att lämna **Skicka ett e-postmeddelande till mig om uppdateringen misslyckas** markerat. Du vill veta direkt om en schemalagd uppdatering misslyckas.

## <a name="troubleshooting"></a>Felsökning
Ibland går det inte som förväntat att uppdatera data. Vanligtvis rör problemet en gateway. Ta en titt på artiklarna för gatewayfelsökning där du hittar verktyg och information om kända problem.

[Felsökning av den lokala datagatewayen](service-gateway-onprem-tshoot.md)

[Felsöka Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

