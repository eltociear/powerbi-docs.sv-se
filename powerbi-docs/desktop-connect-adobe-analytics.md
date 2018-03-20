---
title: "Ansluta till Adobe Analytics i Power BI Desktop (förhandsversion)"
description: "Anslut enkelt till och använd Adobe Analytics i Power BI Desktop"
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
ms.date: 03/09/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: efd6d066e2f98f86248730917c2f4aa0c8a39983
ms.sourcegitcommit: 4217430c3419046c3a90819c34f133ec7905b6e7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2018
---
# <a name="connect-to-adobe-analytics-in-power-bi-desktop-preview"></a>Ansluta till Adobe Analytics i Power BI Desktop (förhandsversion)
I **Power BI Desktop** kan du ansluta till **Adobe Analytics** och använda underliggande data precis som andra datakällor i Power BI Desktop. 

![Hämta data från Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

## <a name="enable-the-adobe-analytics-connector-preview"></a>Aktivera förhandsversionen av Adobe Analytics-anslutningsappen 
Eftersom **Adobe Analytics**-anslutningsappen för närvarande finns som förhandsversion måste du aktivera förhandsversionsfunktionen för att anslutningsappen ska vara tillgänglig i fönstret **Hämta data**. Aktivera förhandsversionen av anslutningsappen genom att välja **Arkiv > Alternativ och inställningar > Alternativ > Förhandsversionsfunktioner** i Power BI Desktop och markera kryssrutan bredvid **Bokmärken**. 

![Aktivera förhandsversionen av Adobe Analytics-anslutningsappen i Alternativ](media/desktop-connect-adobe-analytics/connect-adobe-analytics_02.png)

Du måste starta om **Power BI Desktop** när du har gjort valet för att aktivera förhandsversionen av Adobe Analytics-anslutningsappen.

## <a name="connect-to-adobe-analytics-data"></a>Ansluta till Adobe Analytics-data
Om du vill ansluta till **Adobe Analytics**-data väljer du **Hämta data** på menyfliken **Start** i Power BI Desktop. Välj **Onlinetjänster** bland kategorierna till vänster för att visa **Adobe Analytics-anslutningsapp**.

![Hämta data från Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_01.png)

I **Adobe Analytics**-fönstret som visas väljer du knappen **Logga in** och anger dina autentiseringsuppgifter för att logga in på ditt Adobe Analytics-konto. Adobe-inloggningsfönstret visas, enligt följande bild.

![Logga in på Adobe Analytics](media/desktop-connect-adobe-analytics/connect-adobe-analytics_03.png)

När du uppmanas, ange ditt användarnamn och lösenord. När anslutningen har upprättats kan du förhandsgranska och välja flera dimensioner och mått i dialogrutan **Navigatör** i Power BI för att skapa enskilda tabellutdata. Du kan också ange nödvändiga indataparametrar som krävs för de valda objekten. 

![Välja data med Navigatör](media/desktop-connect-adobe-analytics/connect-adobe-analytics_04.png)

Du kan **Hämta** den markerade tabellen, vilket öppnar hela tabellen i **Power BI Desktop**, eller så kan du **Redigera** frågan, vilket öppnar **frågeredigeraren** så att du kan filtrera och begränsa uppsättningen av data som du vill använda och läsa in en förfinad datauppsättning till **Power BI Desktop**.

![Läsa in eller redigera data i Navigatör](media/desktop-connect-adobe-analytics/connect-adobe-analytics_05.png)


## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Komma igång med Power BI Desktop](desktop-getting-started.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

