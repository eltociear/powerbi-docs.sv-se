---
title: "Använda utsnitt i Power BI Desktop"
description: "Du kan använda utsnitt i Power BI Desktop för att filtrera, markera och anpassa rapporter"
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
ms.date: 02/05/2018
ms.author: davidi
ms.openlocfilehash: 107b4eace4e5b10b52900a4d15110c8acad0f462
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2018
---
# <a name="using-slicers-power-bi-desktop"></a>Använda utsnitt i Power BI Desktop

Du kan använda ett **utsnitt** i **Power BI Desktop** för att filtrera resultaten av visualiseringar på rapportsidan. Med utsnitt kan du enkelt ändra de filter som används genom att interagera med själva utsnittet. Du kan också ange alternativ för hur ditt utsnitt visas och hur du interagerar med det. Följande bild visar ett utsnitt med dess *typ* av listruta synlig. 

![](media/desktop-slicers/desktop-slicers_01.png)

Ett utsnitt kan visas från någon av flera olika typer:

* Lista
* Listruta
* Mellan
* Mindre än eller lika med
* Större än eller lika med

Du kan lägga till ett utsnitt i en rapport genom att klicka på visualiseringen **utsnitt** i fönstret **Visualiseringar**.

![](media/desktop-slicers/desktop-slicers_02.png)

Utsnitt fungerar på liknande sätt i både **Power BI Desktop** och **Power BI-tjänsten**. En självstudiekurs om hur du använder utsnitt finns [utsnitt i Power BI-tjänsten (självstudier)](power-bi-visualization-slicers.md).

## <a name="synchronize-slicers-across-report-pages"></a>Synkronisera utsnitt mellan rapportsidor

I **Power BI Desktop** kan du synkronisera utsnitt över flera rapportsidor. För att synkronisera utsnitt väljer du **synkronisera utsnitt** i rutan **Visa** i menyfliken. När du synkroniserar utsnitt, visas fönstret **Synkronisiera utsnitt** såsom det visas på följande bild.

![](media/desktop-slicers/desktop-slicers_03.png)

I fönstret **Synkronisera utsnitt** kan du ange hur utsnittet ska synkroniseras mellan rapportsidor. Du kan ange om varje utsnitt ska **tillämpas** på varje enskild rapportsida, och om utsnittet ska vara **synligt** på varje enskild rapportsida.

Du kan till exempel placera ett utsnitt på **sidan 2** i rapporten, enligt följande bild. Sedan kan du välja om det utsnittet bör *gälla* på alla valda sidor, och om det utsnittet ska vara *synligt* på alla valda sidor i rapporten. Du kan använda en valfri kombination av dessa för varje utsnitt. 

![](media/desktop-slicers/desktop-slicers_04.png)

Med länken **Lägg till i alla** i fönstret appliceras alla valda utsnitt på alla sidor i rapporten.

Observera att inställningarna som visas i fönstret **Synkronisera utsnitt** endast gäller för det *valda utsnittet*. Du kan använda flera utsnitt på olika sidor och använda fönstret för att definiera hur varje utsnitt tillämpas individuellt på olika sidor i rapporten. 

När valet av utsnitt kan synkroniseras, synkroniseras *inte* andra alternativ, såsom stil, redigera och ta bort. 

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Utsnitt i Power BI-tjänsten (självstudier)](power-bi-visualization-slicers.md)
* [Använd numeriska intervallutsnitt i Power BI Desktop](desktop-slicer-numeric-range.md)
* [Använda ett relativt datumutsnitt och filter i Power BI Desktop](desktop-slicer-filter-date-range.md)

