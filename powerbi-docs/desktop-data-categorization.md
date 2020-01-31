---
title: Datakategorisering i Power BI Desktop
description: Datakategorisering i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 218a05c41c3befed8f8600f6a584560f5be92a1f
ms.sourcegitcommit: a1409030a1616027b138128695b80f6843258168
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/24/2020
ms.locfileid: "76709578"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Ange datakategorier i Power BI Desktop
I Power BI Desktop kan du ange *datakategori* för en kolumn så att Power BI Desktop vet hur den ska hantera dess värden i en visualisering.

När Power BI Desktop importerar data erhålls även annan information än dessa data, till exempel tabell- och kolumnnamn och om data är en primärnyckel. Med denna information gör Power BI Desktop några antaganden om hur du ska få en bra standardupplevelse när du skapar en visualisering.
Om en kolumn har numeriska värden vill du förmodligen aggregera den på något sätt. Därför placerar Power BI Desktop den i området **Värden** i fönstret **Visualiseringar**. Eller om du har en kolumn med datum/tid-värden i ett linjediagram så antar Power BI Desktop att du förmodligen ska använda den som en tidshierarkiaxel.

Men det finns vissa fall som är lite mer utmanande, t.ex. geografiska platser. Titta på följande tabell från ett Excel-kalkylblad:

![](media/desktop-data-categorization/datacategorizationtable.png)

Ska Power BI Desktop behandla koderna i kolumnen **GeoCode** som en förkortning för ett land eller en amerikansk delstat?  Det är oklart eftersom en kod som denna kan innebära båda sakerna. AL kan till exempel betyda Alabama eller Albanien, AR kan innebära Arkansas eller Argentina och CA kan vara Kalifornien eller Kanada. Det är viktigt att veta när vi ska göra ett diagram av GeoCode-fältet på en karta. 

Ska Power BI Desktop visa en bild av världen med markerade länder? Eller visa en bild av USA med markerade delstater?  Du kan ange en datakategori för data som dessa. Ytterligare datakategorisering förfinar informationen som Power BI Desktop kan använda för att ge bra visualiseringar.  

**Ange en datakategori**

1. Gå till **rapportvyn** eller **datavyn**, och i listan **Fält** väljer du de fält som du vill sortera med en annan kategorisering.
2. I området **Egenskaper** på fliken **Modellering** i menyfliksområdet väljer du listrutan bredvid **Datakategori**.  Därmed visas de datakategorier som du kan välja för kolumnen. Vissa alternativ kan vara inaktiverade om de inte fungerar med den aktuella datatypen för kolumnen.  Om en kolumn exempelvis är av en binär datatyp kommer Power BI Desktop inte låta dig välja geografiska datakategorier. 
3. Välj den kategori som du vill använda.

   ![](media/desktop-data-categorization/desktop-data-categorization.png)

Du kanske vill veta mer om [geografisk filtrering för Power BI-mobilappar](desktop-mobile-geofiltering.md).

