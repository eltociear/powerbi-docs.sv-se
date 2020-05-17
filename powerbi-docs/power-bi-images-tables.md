---
title: Visa bilder i en tabell eller matris i en rapport
description: I Power BI Desktop skapar du en kolumn med hyperlänkar till bilder. I antingen Power BI Desktop eller Power BI-tjänst lägger du sedan till hyperlänkarna i en rapporttabell, -matris, -utsnitt eller -kort med flera rader för att visa bilden.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/11/2019
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 95b1dc1be3421f19fa8220629ca2003469658480
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "73874489"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>Visa bilder i en tabell, matris eller ett utsnitt i en rapport

Ett bra sätt att förbättra dina rapporter är att lägga till bilder i dem. Statiska bilder på sidan kan vara lämpliga i vissa fall. Men ibland vill du ha bilder som relaterar till data i rapporten. I det här avsnittet lär du dig hur du visar bilder i en tabell, matris, utsnitt eller ett kort med flera rader. 

![URL-bilder i en tabell](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>Lägg till bilder i rapporten

1. Skapa en kolumn med URL:er för bilderna. Se [överväganden](#considerations) senare i den här artikeln för krav.

1. Markera kolumnen. I menyfliksområdet **Modellering** väljer du **bild-URL** som **datakategori**.

    ![Ange bild-URL som datakategori](media/power-bi-images-tables/power-bi-set-url-image.png)

1. Lägg till kolumnen i en tabell, matris, utsnitt eller kort med flera rader.

    ![Utsnitt med bilder](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>Att tänka på:

- Bilderna måste vara i något av följande filformat: .bmp, .jpg, .jpeg, .gif, .png eller .svg
- URL:en måste vara tillgänglig anonymt, d.v.s. inte på en plats som kräver inloggning, till exempel SharePoint. Men om bilderna finns på SharePoint eller OneDrive kan du få en inbäddningskod som pekar direkt till dem. 


## <a name="next-steps"></a>Nästa steg

[Sidlayout och formatering](/learn/modules/visuals-in-power-bi/12-formatting)

[Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md)

Fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

