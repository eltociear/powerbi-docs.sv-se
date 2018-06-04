---
title: Optimera ett visuellt Power BI-objekt oavsett storlek
description: Lär dig hur du optimerar visuella objekt i befintliga rapporter i Power BI Desktop och Power BI-tjänsten för Power BI-mobilapparna.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2018
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: a6e683318c00a800f69334f90ce3a71d74489030
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34290532"
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Optimera ett visuellt Power BI-objekt oavsett storlek
När du skapar en ny rapport är de visuella objekten som standard *dynamiska*: De ändras dynamiskt så att maximal mängd data och insikter kan visas, oavsett skärmstorlek. När det gäller äldre rapporter kan du konfigurera deras visuella objekt så att även de ändrar storlek dynamiskt.

När ett visuellt objekt får en annan storlek prioriterar Power BI datavyn, genom att till exempel ta bort utfyllnad och flytta förklaringen överst i det visuella objektet automatiskt, så att objektet förblir informativt även när det blir mindre. Svarstiden är särskilt användbar i visuella objekt i Power BI-mobilappen på telefoner.

![Dynamisk storleksändring av visuella objekt](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

Alla visuella objekt med X- och Y-axlar, och utsnitt, kan ändra storlek dynamiskt.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Aktivera svarstider i Power BI Desktop
1. I äldre rapporter i Power BI Desktop går du till fliken **Visa** och kontrollerar att du befinner dig i **Skrivbordslayout**.
   
    ![Ikonen Skrivbordslayout](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Välj ett visuellt objekt och i fönstret **Visualiseringar** väljer du avsnittet **Format**.
3. Expandera **Allmänt** > och dra **Dynamisk** till **På**.
   
    ![Dynamisk är aktiverat](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Nu när du [skapar en rapport som är optimerad för telefonen](desktop-create-phone-report.md) och lägger till det här visuella objektet, ändras storleken på ett smidigt sätt.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Aktivera svarstider i Power BI-tjänsten
Du kan aktivera svarstiden för ett visuellt objekt i en äldre rapport i Power BI-tjänsten. Du måste kunna redigera rapporten.

1. Välj **Redigera rapport** i en rapport i Power BI-tjänsten ([https://powerbi.com](https://powerbi.com)).
2. Välj ett visuellt objekt och i fönstret **Visualiseringar** väljer du avsnittet **Format**.
3. Expandera **Allmänt** > och dra **Dynamisk** till **På**.
   
    ![Dynamisk är aktiverat](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Nu när du [skapar en telefonvy av den här rapporten](desktop-create-phone-report.md) och lägger till det här visuella objektet så ändras storleken på ett smidigt sätt.

## <a name="next-steps"></a>Nästa steg
* [Skapa rapporter som är optimerade för Power BI-telefonappar](desktop-create-phone-report.md)
* [Visa Power BI-rapporter som är optimerade för din telefon](mobile-apps-view-phone-report.md)
* Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

