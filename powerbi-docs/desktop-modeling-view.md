---
title: Använda modelleringsvyn i Power BI Desktop (förhandsversion)
description: Använd modelleringsvyn för att se komplexa datauppsättningar i ett visuellt format i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/13/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 67a04f1ae1bd5858aa4413c77a6d98ac5a04d32f
ms.sourcegitcommit: 6a6f552810a596e1000a02c8d144731ede59c0c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51620181"
---
# <a name="modeling-view-in-power-bi-desktop-preview"></a>Modelleringsvyn i Power BI Desktop (förhandsversion)

Med **Modelleringsvyn** i **Power BI Desktop** kan du visa och arbeta med komplexa datauppsättningar som innehåller många tabeller. Med modelleringsvyn kan du göra följande:


## <a name="enabling-the-modeling-view-preview-feature"></a>Aktivera förhandsfunktionen Modelleringsvy

Modelleringsvyfunktionen är i förhandsversion och måste aktiveras i **Power BI Desktop**. Aktivera modelleringsvyn genom att välja **Arkiv > Alternativ och inställningar > Alternativ > Förhandsfunktioner** och därefter välja kryssrutan **Modelleringsvy** i som det visas i följande bild.

![Aktivera förhandsfunktionen Modelleringsvy i Power BI Desktop](media/desktop-modeling-view/modeling-view_01.png)

Du kommer att behöva starta om **Power BI Desktop** för att förhandsfunktionen ska aktiveras. 

![Starta om Power BI Desktop för att aktivera förhandsfunktioner](media/desktop-modeling-view/modeling-view_01b.png)

## <a name="using-modeling-view"></a>Använda Modelleringsvyn

Om du vill komma åt Modelleringsvyn så väljer du Modelleringsvy-ikonen som visas på vänster sida av **Power BI Desktop** som det visas i följande bild.

![Modelleringsvy-ikonen i Power BI Desktop](media/desktop-modeling-view/modeling-view_02.png)

## <a name="creating-separate-diagrams"></a>Skapa separata diagram

Med Modelleringsvyn så kan du skapa diagram över din modell som endast innehåller en delmängd av tabellerna i din modell. Det kan ge en bättre uppfattning av de tabeller som du vill arbeta med och underlätta arbete med komplexa datauppsättningar. Skapa ett nytt diagram med endast en delmängd av tabellerna genom att klicka på tecknet **+** bredvid fliken **Alla tabeller** längst ned i Power BI Desktop-fönstret.

![Skapa ett nytt diagram genom att klicka på +-tecknet under flikar](media/desktop-modeling-view/modeling-view_03.png)

Du kan sedan dra en tabell från listan **Fält** till diagramytan. Högerklicka på tabellen och välj sedan **Lägg till relaterade tabeller** från menyn som visas.

![Högerklicka på en tabell och välj Lägg till relaterade tabeller](media/desktop-modeling-view/modeling-view_04.png)

När du gör det så visas tabeller som är relaterade till den ursprungliga tabellen i det nya diagrammet. Följande bild visar hur relaterade tabeller visas när du har valt menyalternativet **Lägg till relaterade tabeller**.

![Visa relaterade tabeller](media/desktop-modeling-view/modeling-view_05.png)

## <a name="setting-common-properties"></a>Ställ in gemensamma egenskaper

Du kan välja flera objekt på samma gång i modelleringsvyn genom att hålla ned **Ctrl**-tangenten och klicka på flera tabeller. När du väljer flera tabeller så markeras de i Modelleringsvyn. När flera tabeller är markerade så blir ändringar som tillämpas i **Egenskaper**-fönstret gällande för alla valda tabeller.

Du kan till exempel ändra den [lagringsläge](desktop-storage-mode.md) för flera tabeller i din diagramvy genom att hålla ned **Ctrl**-tangenten, markera tabeller och därefter ändra inställningen för lagringsläge i **Egenskaper**-fönstret.

![Välj flera tabeller genom att hålla in Ctrl och markera gemensamma egenskaper för alla markerade tabeller](media/desktop-modeling-view/modeling-view_06.png)


## <a name="next-steps"></a>Nästa steg

Följande artiklar beskriver mer om datamodeller och beskriver även DirectQuery i detalj.

* [Sammansättningar i Power BI Desktop (förhandsversion)](desktop-aggregations.md)
* [Sammansatta modeller i Power BI Desktop (förhandsversion)](desktop-composite-models.md)
* [Lagringsläge i Power BI Desktop (förhandsversion)](desktop-storage-mode.md)
* [Många-till-många-relationer i Power BI Desktop (förhandsversion)](desktop-many-to-many-relationships.md)


DirectQuery-artiklar:

* [Använd DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery i Power BI](desktop-directquery-data-sources.md)
