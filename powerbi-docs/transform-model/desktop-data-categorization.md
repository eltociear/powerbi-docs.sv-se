---
title: Datakategorisering i Power BI Desktop
description: Datakategorisering i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 414f58338a53ce9ff24f193acd3cee0da2c30658
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86215334"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>Ange datakategorier i Power BI Desktop
I Power BI Desktop kan du ange *datakategori* för en kolumn så att Power BI Desktop vet hur den ska hantera dess värden i en visualisering.

När Power BI Desktop importerar data erhålls även annan information än dessa data, till exempel tabell- och kolumnnamn och om data är en primärnyckel. Med denna information gör Power BI Desktop några antaganden om hur du ska få en bra standardupplevelse när du skapar en visualisering.
Om en kolumn till exempel innehåller numeriska värden vill du förmodligen aggregera den på något sätt, så Power BI Desktop placerar den i området **Värden** i rutan **Visualiseringar**. För en kolumn med datum/tid-värden i ett linjediagram antar Power BI Desktop å andra sidan att du förmodligen vill använda den som en tidshierarkiaxel.

Men det finns vissa fall som är lite mer utmanande, t.ex. geografiska platser. Titta på följande tabell från ett Excel-kalkylblad:

![Skärmbild av Excel och tabelldata som ska importeras till Power BI Desktop.](media/desktop-data-categorization/datacategorizationtable.png)

Ska Power BI Desktop behandla koderna i kolumnen **GeoCode** som en förkortning för ett land eller en amerikansk delstat?  Det är oklart eftersom en kod som denna kan innebära båda sakerna. AL kan till exempel betyda Alabama eller Albanien, AR kan innebära Arkansas eller Argentina och CA kan vara Kalifornien eller Kanada. Det är viktigt att veta när vi ska göra ett diagram av GeoCode-fältet på en karta. 

Ska Power BI Desktop visa en bild av världen med markerade länder? Eller visa en bild av USA med markerade delstater?  Du kan ange en datakategori för data som dessa. Ytterligare datakategorisering förfinar informationen som Power BI Desktop kan använda för att ge bra visualiseringar.  

**Ange en datakategori**

1. Gå till **rapportvyn** eller **datavyn**, och i listan **Fält** väljer du de fält som du vill sortera med en annan kategorisering.
2. I området **Egenskaper** på fliken **Modellering** i menyfliksområdet väljer du listrutan bredvid **Datakategori**.  Därmed visas de datakategorier som du kan välja för kolumnen. Vissa alternativ kan vara inaktiverade om de inte fungerar för kolumnens aktuella datatyp.  Om en kolumn exempelvis är av datatypen datum eller tid kan du inte välja geografiska datakategorier i Power BI Desktop. 
3. Välj den kategori som du vill använda.

   ![Skärmbild av Power BI Desktop med filtret Datakategori.](media/desktop-data-categorization/desktop-data-categorization.png)

Du kanske vill veta mer om [geografisk filtrering för Power BI-mobilappar](desktop-mobile-geofiltering.md).