---
title: Se data och poster i Power BI Desktop-visualiseringar
description: "Använd funktionerna Se data och Se poster för Power BI Desktop för att gå in på detaljnivå"
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
ms.date: 02/22/2018
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: c44a5140fe40217aac170abb0b351197803b6299
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="use-see-data-and-see-records-in-power-bi-desktop"></a>Använd se Data och se poster i Power BI Desktop
I **Power BI Desktop** kan du gå in på detaljnivå för all visuell information och se en textrepresentation av data eller enskilda dataelement för en vald visualisering. De här funktionerna kallas ibland för *klicka igenom*, eller *detaljerad information* eller *gå in på detaljnivå*.

Du kan använda **Se poster** för att visa de underliggande raderna för ett valt dataelement från en visualisering eller använda **Se data** för att visa en textversion av de värden som används i visualiseringen. Det finns vissa begränsningar med att använda **Se data** och **Se poster**, vilka beskrivs i slutet av den här artikeln.

![](media/desktop-see-data-see-records/see-data-see-records_1.png)

## <a name="using-see-data-in-power-bi-desktop"></a>Använd Se data i Power BI Desktop
Knappen **Se data** finns i fliken **Data / detaljgranska** i avsnittet **Visuella verktyg** i menyfliksområdet.

![](media/desktop-see-data-see-records/see-data-see-records_2.png)

Du kan även **Se data** genom att högerklicka på en visualisering och sedan välja **Se data** från menyn som visas.

![](media/desktop-see-data-see-records/see-data-see-records_3.png)

> [!NOTE]
> Du måste hovra över en datapunkt i visualiseringen för att snabbmenyn ska vara tillgängliga.
> 
> 

När du väljer **Se data**, fokuserar **Power BI Desktop** på den visuella informationen och de data som du valt och dedikerar arbetsytan för att visa visualiseringen och textrepresentation av data. Den visuella informationen visas på den övre delen av arbetsytan och data visas på den nedre halvan, enligt följande bild. Det här är den *vågräta* vyn.

![](media/desktop-see-data-see-records/see-data-see-records_4.png)

Du kan också växla till en *lodrät vy* (eller tillbaka till *vågrät vy*), genom att välja ikonen i det övre högra hörnet.

![](media/desktop-see-data-see-records/see-data-see-records_5.png)

Gå tillbaka till rapporten genom att markera **< Tillbaka till rapporten** i det övre vänstra hörnet på arbetsytan.

![](media/desktop-see-data-see-records/see-data-see-records_6.png)

## <a name="using-see-records-in-power-bi-desktop"></a>Använd Se poster i Power BI Desktop
Du kan också fokusera på ett dataelement i en visualisering och gå in på detaljnivå på bakomliggande data. När en visualisering väljs det finns två sätt att använda **Se poster**: Du kan aktivera växlingsknappen **Se poster** i menyfliksområdet **Data / detaljgranska** och sedan klicka på ett dataelement, eller så kan du högerklicka på ett dataelement och välja **Se poster** från menyn som visas.

![](media/desktop-see-data-see-records/see-data-see-records_7.png)

> [!NOTE]
> Om den valda visualiseringen inte stöder **Se poster** så är knappen i menyfliksområdet nedtonad.
> 
> 

När **Se poster** har valts, fokuserar **Power BI Desktop** på det enskilda dataelementet och dedikerar arbetsytan till att visa data för det elementet som det visas i följande bild.

![](media/desktop-see-data-see-records/see-data-see-records_8.png)

> [!NOTE]
> Det går inte att spara ändringar av data som visas (eller ändras av användare) i vyn **Se poster** till en rapport.

Gå tillbaka till rapporten genom att markera knappen **Tillbaka till rapporten** i det övre vänstra hörnet på arbetsytan.

## <a name="limitations"></a>Begränsningar
Det finns några begränsningar att överväga när du använder **Se data** eller **Se poster**:

* Endast följande visualiseringstyper stöds:
  * **Stapel**
  * **Kolumn**
  * **Karta**
  * **Trädkarta**
  * **Ifylld karta**
  * **Cirkel**
  * **Toroid**
  * **Tratt**
* Du kan inte använda **Se poster** när din visualisering använder ett beräknat mått
* Du kan inte använda **Se poster** när du är ansluten till en live-flerdimensionell modell (MD)

## <a name="next-steps"></a>Nästa steg
Det finns en massa sorters rapportformatering och funktioner för datahantering i **Power BI Desktop**. Kolla in följande resurser för några exempel:

* [Använd gruppering och diskretisering i Power BI Desktop](desktop-grouping-and-binning.md)
* [Använd stödlinjer, fäst till rutnät, z-ordning, justering och distribution i Power BI Desktop-rapporter](desktop-gridlines-snap-to-grid.md)

