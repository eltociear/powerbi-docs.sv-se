---
title: Optimera ett visuellt Power BI-objekt oavsett storlek
description: "Lär dig hur du optimerar visuella objekt i Power BI Desktop och Power BI-tjänsten för Power BI-mobilapparna."
services: powerbi
documentationcenter: 
author: maggiesMSFT
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
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: a059c01d6e9e08851434f71a1f36ac096054e291
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Optimera ett visuellt Power BI-objekt oavsett storlek
Du kan ange att visuella objekt i din instrumentpanel eller rapport ska vara *dynamiska*, så att de ändras dynamiskt till att visa maximal mängd data och analyser, oavsett skärmstorlek.

När ett visuellt objekt får en annan storlek prioriterar Power BI datavyn, genom att till exempel ta bort utfyllnad och flytta förklaringen överst i det visuella objektet automatiskt, så att objektet förblir informativt även när det blir mindre. Svarstiden är särskilt användbar i visuella objekt i Power BI-mobilappen på telefoner.

![Dynamisk storleksändring av visuella objekt](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

Du kan aktivera svarstider för alla visuella objekt med X- och Y-axlarna samt utsnitt.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Aktivera svarstider i Power BI Desktop
1. I Power BI Desktop går du till fliken **Visa** och kontrollerar att du befinner dig i **Skrivbordslayout**.
   
    ![Ikonen Skrivbordslayout](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Välj ett visuellt objekt och i fönstret **Visualiseringar** väljer du avsnittet **Format**.
3. Expandera **Allmänt** > och dra **Dynamisk** till **På**.
   
    ![Dynamisk är aktiverat](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Nu när du [skapar en rapport som är optimerad för telefonen](desktop-create-phone-report.md) och lägger till det här visuella objektet, ändras storleken på ett smidigt sätt.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Aktivera svarstider i Power BI-tjänsten
Du kan aktivera svarstiden för ett visuellt objekt i en rapport i Power BI-tjänsten. Du måste kunna redigera rapporten.

1. I en rapport i Power BI-tjänsten ([https://powerbi.com](https://powerbi.com)) väljer du **Redigera rapport**.
2. Välj ett visuellt objekt och i fönstret **Visualiseringar** väljer du avsnittet **Format**.
3. Expandera **Allmänt** > och dra **Dynamisk** till **På**.
   
    ![Dynamisk är aktiverat](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Nu när du [skapar en telefonvy av en instrumentpanel](service-create-dashboard-mobile-phone-view.md) och lägger till det här visuella objektet, ändras storleken på ett smidigt sätt.

## <a name="next-steps"></a>Nästa steg
* [Skapa rapporter som är optimerade för Power BI-telefonappar](desktop-create-phone-report.md)
* [Skapa en telefonvy av en instrumentpanel i Power BI](service-create-dashboard-mobile-phone-view.md)
* [Visa Power BI-rapporter som är optimerade för din telefon](mobile-apps-view-phone-report.md)
* Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

