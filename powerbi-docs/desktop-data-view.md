---
title: Datavy i Power BI Desktop
description: Datavy i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: a403f8a115361a36fbd12c4a66ba1dd34cc3bdde
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52669990"
---
# <a name="data-view-in-power-bi-desktop"></a>Datavy i Power BI Desktop
**Datavyn** gör det enklare att inspektera, utforska och förstå data i **Power BI Desktop**-modellen. Det skiljer sig från hur du visar tabeller, kolumner och data i **frågeredigeraren**. I datavyn tittar du på dina data *efter* att de har lästs in i modellen.

När du utformar dina data, vill ibland du se vad som faktiskt finns i en tabell eller kolumn utan att skapa ett visuellt objekt på rapportarbetsytan, ofta på radnivå. Detta gäller särskilt när du skapar mått och beräknade kolumner eller om du behöver identifiera en datatyp eller datakategori.

Nu ska vi titta närmare på några av elementen i **datavyn**.

![Datavy i Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Ikon för datavy** – Välj den här ikonen för att öppna datavyn.

2. **Datarutnät** – Visar den valda tabellen och alla kolumner och rader i den. Kolumner som är dolda från **rapportvyn** är nedtonade. Du kan högerklicka på en kolumn för att visa fler alternativ.

3. **Menyfliksområdet Modellering** – Här kan du hantera relationer, skapa beräkningar, ändra datatyp, format och datakategori för en kolumn.

4. **Formelfält** – Ange DAX-formler för mått och beräknade kolumner.

5. **Sök** – Sök efter en tabell eller kolumn i modellen.

6. **Fältlista** – Välj en tabell eller kolumn som du vill visa i rutnätet.

## <a name="filtering-in-data-view"></a>Filtrering i datavyn

Du kan också filtrera och sortera data i **datavyn**. Varje kolumn har en ikon som anger sorteringsriktningen (om sortering används).

![Sortera och filtrera i datavyn i Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Du kan filtrera enskilda värden eller använda avancerad filtrering baserat på data i kolumnen. 

> [!NOTE]
> Om en Power BI-modell har skapats i en annan kultur än ditt aktuella gränssnitt (till exempel om modellen har skapats på engelska (USA) och du visar den på spanska), visas sökrutan i användargränssnittet för datavyn endast för textfält.
