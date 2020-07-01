---
title: Uppdatera en datauppsättning som skapats från en Excel-arbetsbok – lokalt
description: Uppdatera en datauppsättning som skapats från en Excel-arbetsbok på en lokal enhet
author: davidiseminger
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: 806fb9fffccaffee62d8cafb00dc94b5ad7b0def
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85220895"
---
# <a name="refresh-a-dataset-created-from-an-excel-workbook-on-a-local-drive"></a>Uppdatera en datauppsättning som skapats från en Excel-arbetsbok på en lokal enhet
## <a name="whats-supported"></a>Vad stöds?
I Power BI stöds Uppdatera nu och Uppdatera schema för datauppsättningar som skapas från Excel-arbetsböcker som importerats från en lokal enhet där Power Query (Hämta & Transformera data i Excel 2016) eller Power Pivot används för att ansluta till någon av följande datakällor och läsa in data i Excel-datamodellen:  

### <a name="power-bi-gateway---personal"></a>Power BI Gateway – Personal
* Alla online-datakällor som visas i Power Query.
* Alla lokala datakällor som visas i Power Query förutom Hadoop-filer (HDFS) och Microsoft Exchange.
* Alla online-datakällor som visas i Power Pivot.\*
* Alla lokala datakällor som visas i Power Query förutom Hadoop-filer (HDFS) och Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](../includes/refresh-datasources.md)]

> **OBS:**  
> 
> * En gateway måste vara installerad och köras för att Power BI ska kunna ansluta till lokala datakällor och uppdatera datauppsättningen.
> * När du använder Excel 2013 måste du kontrollera att du har uppdaterat Power Query till den senaste versionen.
> * Uppdatering stöds inte för Excel-arbetsböcker som importerats från en lokal enhet där data bara finns i kalkylblad eller länkade tabeller. Uppdatering stöds för kalkylbladsdata om de lagras och importeras från OneDrive. Mer information finns i [Uppdatera en datauppsättning som skapas från en Excel-arbetsbok på OneDrive eller SharePoint Online](refresh-excel-file-onedrive.md).
> * När du uppdaterar en datauppsättning som skapats från en Excel-arbetsbok som har importerats från en lokal enhet, uppdateras bara de data som efterfrågas från datakällor. Om du ändrar strukturen för datamodellen i Excel eller Power Pivot, till exempel skapar ett nytt mått eller byter namn på en kolumn, kopieras inte dessa ändringar till datauppsättningen. Om du gör sådana ändringar, måste du överföra eller publicera arbetsboken på nytt. Om du förväntar dig att göra regelbundna ändringar i strukturen för din arbetsbok, och du vill att de ska visas i datauppsättningen i Power BI utan att behöva göra överföringen på nytt, bör du placera din arbetsbok på OneDrive. Power BI uppdaterar automatiskt både struktur och kalkylbladsdata från arbetsböcker som lagras och importeras från OneDrive.
> 
> 

## <a name="how-do-i-make-sure-data-is-loaded-to-the-excel-data-model"></a>Hur gör jag för att vara säker på att data har lästs in i Excel-datamodellen?
När du använder Power Query (Hämta & Transformera data i Excel 2016) för att ansluta till en datakälla, har du flera alternativ för var du vill läsa in dessa data. För att säkerställa att du läser in data i datamodellen, måste du välja alternativet **Lägg till dessa data i datamodellen** i dialogrutan **Läsa in till**.

> [!NOTE]
> De här bilderna visar Excel 2016.
> 
> 

I **Navigator** klickar du på **Läs in till ...**  
    ![](media/refresh-excel-file-local-drive/refresh_loadtodm_1.png)

Eller, om du klickar på **Redigera** i Navigator, så öppnas Frågeredigeraren. Där kan du klicka på **Stäng och läs in till ...**  
    ![](media/refresh-excel-file-local-drive/refresh_loadtodm_2.png)

I **Läs in till** måste du sedan kontrollera att du väljer **Lägg till dessa data i datamodellen**.  
    ![](media/refresh-excel-file-local-drive/refresh_loadtodm_3.png)

### <a name="what-if-i-use-get-external-data-in-power-pivot"></a>Vad händer om jag använder Hämta externa Data i Power Pivot?
Inga problem. När du använder Power Pivot för att ansluta till och fråga efter data från en lokal datakälla eller datakälla online, läses dina data in automatiskt till datamodellen.

## <a name="how-do-i-schedule-refresh"></a>Hur gör jag för att schemalägga uppdateringar?
När du konfigurerar ett uppdateringsschema, ansluter Power BI direkt till datakällorna med anslutningsinformationen och autentiseringsuppgifterna i datauppsättningen för att fråga efter uppdaterade data, och läser sedan in uppdaterade data i datauppsättningen. Även alla visualiseringar i rapporter och på instrumentpaneler baserade på den datauppsättningen i Power BI-tjänsten uppdateras.

Mer information om hur du konfigurerar schemalagda uppdateringar finns i [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Om något går fel
Om något går fel beror det vanligtvis på att Power BI inte kan logga in till datakällor, eller att gatewayen är offline om datauppsättningen ansluter till en lokal datakälla. Kontrollera att Power BI kan logga in till datakällor. Om det lösenord som du använder för att logga in på en datakälla ändras eller om Power BI loggas ut från en datakälla, bör du försöka logga in på dina datakällor igen i datakällans autentiseringsuppgifter.

Se till att lämna **Skicka ett e-postmeddelande till mig om uppdateringen misslyckas** markerat. Du vill veta direkt om en schemalagd uppdatering misslyckas.

>[!IMPORTANT]
>Uppdatering stöds inte för OData-flöden som ansluts till och efterfrågas från Power Pivot. Använd Power Query när du använder ett OData-flöde som datakälla.

## <a name="troubleshooting"></a>Felsökning
Ibland går det inte som förväntat att uppdatera data. Vanligtvis rör problemet en gateway. Ta en titt på artiklarna för gatewayfelsökning där du hittar verktyg och information om kända problem.

[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)

[Felsöka Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Nästa steg
Fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
