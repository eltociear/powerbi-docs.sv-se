---
title: Visuell tabell och poster i visuella Power BI Desktop-objekt
description: Använda funktionerna för visuell tabell och datapunkttabell i Power BI Desktop för att öka detaljnivån
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/21/2020
ms.author: davidi
LocalizationGroup: Learn more
ms.openlocfilehash: f9fa3ee1c1e0f757eb3b464785c8cb3fe3ab6e78
ms.sourcegitcommit: e8ed3d120699911b0f2e508dc20bd6a9b5f00580
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/11/2020
ms.locfileid: "86264728"
---
# <a name="use-visual-table-and-data-point-table-in-power-bi-desktop"></a>Använda visuell tabell och datapunkttabell i Power BI Desktop
I **Power BI Desktop** kan du visa detaljer om en visualisering och se textrepresentationer av underliggande data eller enskilda dataelement för den valda visualiseringen. De här funktionerna kallas ibland för *klicka igenom*, *detaljerad information* eller *gå in på detaljnivå*.

Du kan använda en **visuell tabell** för att visa data i ett visuellt objekt som en tabell eller använda en **datapunkttabell** för att visa en tabell över de data som används för att beräkna en enskild datapunkt. 

![Visuell tabell och datapunkttabell](media/desktop-see-data-see-records/see-data-record.png)

>[!IMPORTANT]
>**Visuell tabell** och **datapunkttabell** har endast stöd för följande visualiseringstyper:
>  - Stapeldiagram
>  - Kolumndiagram
>  - Ringdiagram
>  - Ifylld karta
>  - Tratt
>  - Karta
>  - Cirkeldiagram
>  - Trädkarta

## <a name="use-visual-table-in-power-bi-desktop"></a>Använda Visuell tabell i Power BI Desktop

**Visuell tabell** visar de data som ligger under en visualisering. **Visuell tabell** visas på fliken **Data/detaljgranska** i avsnittet **Visa** i menyfliksområdet när ett visuellt objekt väljs.

![Visuell tabell i menyfliksområdet](media/desktop-see-data-see-records/visual-table-01.png)

Du kan också visa data genom att högerklicka på en visualisering och sedan välja **Visa data** från menyn som visas, eller genom att välja **Fler alternativ** (...) uppe till höger i en visualisering och sedan **Visa som tabell**.

![Högerklicka på Visa data](media/desktop-see-data-see-records/visual-table-02.png)&nbsp;&nbsp;![Fler alternativ för Visa data](media/desktop-see-data-see-records/visual-table-03.png)

> [!NOTE]
> Du måste hovra över en datapunkt i visualiseringen för att snabbmenyn ska vara tillgänglig.

När du väljer **Visuell tabell** eller **Datapunkttabell**, visar Power BI Desktop-arbetsytan både en visuell och en textrepresentation av dina data. I *vågrät vy* visas visualiseringen på den övre delen av arbetsytan och data visas på den nedre halvan. 

![vågrät vy](media/desktop-see-data-see-records/visual-table-04.png)

Du kan växla mellan vågrät vy och *lodrät vy* genom att välja ikonen i det övre högra hörnet av arbetsytan.

![växla till lodrät vy](media/desktop-see-data-see-records/visual-table-05.png)

Gå tillbaka till rapporten genom att markera **< Tillbaka till rapporten** i det övre vänstra hörnet på arbetsytan.

![Tillbaka till rapporten](media/desktop-see-data-see-records/visual-table-06.png)

## <a name="use-data-point-table-in-power-bi-desktop"></a>Använda Datapunkttabell i Power BI Desktop

Du kan också fokusera på en datapost i en visualisering och gå in på detaljnivå på bakomliggande data. För att använda en **datapunkttabell** väljer du en visualisering och sedan **Datapunkttabell** på fliken **Data/detaljgranska** i avsnittet **Visuella verktyg** i menyfliksområdet och sedan en datapunkt eller rad i visualiseringen. 

![Datapunkttabell i menyfliksområdet](media/desktop-see-data-see-records/visual-table-07.png)

> [!NOTE]
> Om knappen **Datapunkttabell** i menyfliksområdet är inaktiverad och nedtonad, betyder det att den valda visualiseringen inte har stöd för funktionen **Datapunkttabell**.

Du kan också högerklicka på ett dataelement och välja **Datapunkttabell** från menyn som visas.

![Datapunkttabell genom att högerklicka](media/desktop-see-data-see-records/visual-table-08.png)

När du väljer **Datapunkttabell** för ett dataelement, visar Power BI Desktop-arbetsytan alla data som är associerade med det valda elementet. 

![Skärmbild av en arbetsyta som visar alla data som är associerade med det valda elementet när du väljer Datapunktstabell.](media/desktop-see-data-see-records/visual-table-09.png)

Gå tillbaka till rapporten genom att markera **< Tillbaka till rapporten** i det övre vänstra hörnet på arbetsytan.


> [!NOTE]
>**Datapunkttabell** har följande begränsningar:
> - Du kan inte ändra data i vyn **Datapunkttabell** och sedan spara dem i rapporten igen.
> - Du kan inte använda **Datapunktstabell** när ditt visuella objekt använder ett beräknat mått i en (flerdimensionell) måttgrupp.
> - Du kan inte använda **Datapunkttabell** när du är ansluten till en flerdimensionell livemodell.

## <a name="next-steps"></a>Nästa steg
Det finns en massa sorters rapportformatering och funktioner för datahantering i **Power BI Desktop**. Kolla in följande resurser för några exempel:

* [Använd gruppering och diskretisering i Power BI Desktop](desktop-grouping-and-binning.md)
* [Använd stödlinjer, fäst till rutnät, z-ordning, justering och distribution i Power BI Desktop-rapporter](desktop-gridlines-snap-to-grid.md)

