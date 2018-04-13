---
title: Datakategorisering i Power BI Desktop
description: Datakategorisering i Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: cc66655e49860160b43afa5d1acb688c37468212
ms.sourcegitcommit: c80fbf5b12754ce217cb47a17cb5400b1036a8f2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/06/2018
---
# <a name="data-categorization-in-power-bi-desktop"></a>Datakategorisering i Power BI Desktop
I **Power BI Desktop** kan du ange datakategori för en kolumn så att Power BI Desktop vet hur den ska hantera dess värden i en visualisering.

När Power BI Desktop importerar data hämtas inte bara själva informationen, utan även information som tabell- och kolumnnamn, om det är en primär nyckel, osv.  Med denna information gör Power BI Desktop några antaganden om hur du ska få en bra standardupplevelse när du skapar en visualisering. 

Här är ett exempel: När Power BI Desktop upptäcker en kolumn som innehåller numeriska värden, vill du förmodligen sammanställa den på något sätt, så den placeras i området Värden. Eller, för en kolumn med datum/tid-värden förutsätts det att du förmodligen ska använda den som en tidshierarkiaxel i ett linjediagram.

Men det finns vissa fall som är lite mer utmanande, t.ex. geografiska platser. Titta på följande tabell från ett Excel-kalkylblad:

![](media/desktop-data-categorization/datacategorizationtable.png)

Ska Power BI Desktop behandla koderna i kolumnen GeoCode som en förkortning för ett land eller en amerikansk stat?  Det är oklart eftersom en kod som denna kan innebära båda sakerna.  AL kan till exempel betyda Alabama eller Albanien, AR kan innebära Arkansas eller Argentina och CA kan vara Kalifornien eller Kanada. Det är viktigt att veta när vi ska göra ett diagram av GeoCode-fältet på en karta.  Ska Power BI Desktop visa en bild av världen med länderna markerade, eller en bild av USA med staterna markerade?  Du kan ange en datakategori för data som dessa. Ytterligare datakategorisering förfinar informationen som Power BI Desktop kan använda för att ge bra visualiseringar.  

**Ange en datakategori**

1. Gå till rapport- eller datavyn i listan **Fält** och välj de fält som du vill sortera med en annan kategorisering.
2. På fliken **Modellering** i menyfliksområdet klickar du på listrutan **Datakategori:**.  Detta visar listan med datakategorier som du kan välja för kolumnen.  Vissa alternativ kan vara inaktiverade om de inte fungerar med den aktuella datatypen för kolumnen.  Om en kolumn exempelvis är av en binär datatyp kommer Power BI Desktop inte låta dig välja geografiska datakategorier. 

![](media/desktop-data-categorization/datacategorization.gif)

Och sedan är du klar!  Alla funktioner som normalt sett finns i visuella objekt fungerar nu automatiskt.  

Du kanske vill veta mer om [geografisk filtrering för Power BI-mobilappar](desktop-mobile-geofiltering.md).

