---
title: Ange utvalda tabeller i Power BI Desktop (förhandsversion)
description: Skapa aktuella tabeller i Power BI Desktop så att de visas i galleriet Datatyper i Excel.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 07/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: e39d2fe11a58691b259784c292fec6e5ee6cb322
ms.sourcegitcommit: 65025ab7ae57e338bdbd94be795886e5affd45b4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87254221"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>Ange utvalda tabeller i Power BI Desktop (förhandsversion)

I galleriet Datatyper i Excel kan användarna hitta data från *utvalda tabeller* i Power BI-datauppsättningar. I den här artikeln får du lära dig hur du ställer in tabeller som *aktuella* i dina datauppsättningar. Taggarna gör det enklare för användarna att lägga till företagsdata i sina Excel-blad. Här är de grundläggande stegen för att ställa in och dela aktuella tabeller.

1. Du [flyttar upp certifierar datauppsättningar i Power BI](../connect-data/service-datasets-promote.md). 
1. Du identifierar aktuella tabeller i dina datauppsättningar i Power BI Desktop (den här artikeln)
1. Du sparar datauppsättningarna med aktuella tabeller till någon av de nya arbetsytorna. Rapportskapare kan skapa rapporter med dessa aktuella tabeller. 
1. Resten av organisationen kan ansluta till de utvalda tabellerna, som kallas *datatyper* i Excel och få relevanta och uppdaterbara data. I artikeln [Åtkomst till Power BI-tabeller i Excel (förhandsversion)](service-excel-featured-tables.md) beskrivs användningen av dessa aktuella tabeller i Excel.

## <a name="turn-on-the-featured-table-preview"></a>Aktivera förhandsgranskning av aktuell tabell

1. I Power BI Desktop väljer du **Arkiv** > **Alternativ och inställningar** > **Alternativ** > **Förhandsvisningsfunktioner**.
2. Markera kryssrutan **Aktuella tabeller**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="Förhandsvisning av alternativet aktuella tabeller":::

## <a name="select-a-table"></a>Välj en tabell

1. Gå till modellvy i Power BI Desktop

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="Modellvy":::
 
2. Välj en tabell och ställ in **Är aktuell tabell** på **Ja**.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="Ställ in Är aktuell tabell på Ja":::

4. Ange de obligatoriska fälten i **Konfigurera den här aktuella tabellen**:

    - En **Beskrivning**: 
        > [!TIP]
        > Börja beskrivningen med ”aktuell tabell” för att hjälpa Power BI-rapportskapare att identifiera den.
    - Fältvärdet **radetikett** används i Excel så att användarna enkelt kan identifiera raden. Den visas som cellvärdet för en länkad cell i **dataväljarfönstret** och på kortet **Information**. 
    - **Nyckelkolumnen** fältvärde innehåller det unika ID:t för raden. Med det här värdet kan Excel länka en cell till en viss rad i tabellen.

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="Konfigurera aktuell tabell":::

1. När du har publicerat eller importerat datauppsättningen till Power BI-tjänsten visas den aktuella tabellen i galleriet Excel-datatyper. Du och andra rapportskapare kan även skapa rapporter som bygger på den här datauppsättningen.

1. I Excel: 
    - Excel cachelagrar listan med datatyper så att du måste starta om Excel för att se nyligen publicerade aktuella tabeller.
    - Vissa datauppsättningar stöds inte i förhandsversionen och aktuella tabeller som definierats i dessa datauppsättningar visas inte i Excel. I nästa avsnitt, Överväganden och begränsningar, finns mer information.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Här följer begränsningar för den inledande förhandsversionen.

- Aktuella tabeller i Power BI-datauppsättningar som använder följande funktioner visas inte i Excel: 

    - Datauppsättningar med säkerhet på radnivå.
    - Datauppsättningar med Microsoft Information Protection.
    - DirectQuery-datauppsättningar.
    - Datauppsättningar med en live-anslutning.

- Excel visar endast data i kolumner och beräknade kolumner i den aktuella tabellen. Följande har inte angetts i den första förhandsgranskningen:

    - Mått som definierats i funktionstabellen.
    - Mått som definierats för relaterade tabeller och införstådda mått som beräknas utifrån relationer.

- Excel visar bara aktuella tabeller som lagras i de nya Power BI-arbetsytorna. Aktuella tabeller som lagras i de klassiska arbetsytorna eller min arbetsyta visas inte som datatyper i Excel. Du kan [Uppgradera klassiska arbetsytor till de nya arbetsytorna](service-upgrade-workspaces.md) i Power BI.
- Se [Överväganden och begränsningar](service-excel-featured-tables.md#considerations-and-limitations) i artikeln Använda aktuella Power BI-tabeller i Excel för andra Excel-överväganden.

## <a name="next-steps"></a>Nästa steg

- [Åtkomst till Power BI-tabeller i Excel](service-excel-featured-tables.md)
- Läs om att använda [Excel-datatyper från Power BI](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9) i Excel-dokumentationen.
- Har du några frågor? [Prova Power BI Community](https://community.powerbi.com/)

