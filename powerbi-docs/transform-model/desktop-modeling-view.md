---
title: Använda modelleringsvyn i Power BI Desktop
description: Använd modelleringsvyn för att se komplexa datauppsättningar i ett visuellt format i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 27d601da2a3ef922c75aee6f52011ac22ca26336
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83280344"
---
# <a name="work-with-modeling-view-in-power-bi-desktop"></a>Arbeta med modelleringsvyn i Power BI Desktop

I **Modelleringsvyn** i **Power BI Desktop** kan du visa och arbeta med komplexa datauppsättningar som innehåller många tabeller.


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
* [Sammansatta modeller i Power BI Desktop](desktop-composite-models.md)
* [Lagringsläge i Power BI Desktop (förhandsversion)](desktop-storage-mode.md)
* [Många-till-många-relationer i Power BI Desktop](desktop-many-to-many-relationships.md)


DirectQuery-artiklar:

* [Använd DirectQuery i Power BI](../connect-data/desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery i Power BI](../connect-data/power-bi-data-sources.md)
