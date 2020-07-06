---
title: Lägga till flera fält i ett hierarkiutsnitt
description: Läs hur du skapar ett hierarkiutsnitt som innehåller flera fält i en hierarki.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/11/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 2b9c4a8f4695f8d701eba535180194d29dd8bdec
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85238186"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Lägga till flera fält i ett hierarkiutsnitt

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Om du vill filtrera flera relaterade fält inom ett enda utsnitt kan du göra det genom att skapa vad som kallas för ett *hierarki*utsnitt. Du kan skapa dessa utsnitt i antingen Power BI Desktop eller i Power BI-tjänsten.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Hierarkiutsnitt i Power BI":::

När du lägger till flera fält i utsnittet visas som standard en pil, eller *sparr*, bredvid de objekt som kan expanderas för att visa objekten på nästa nivå.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Listrutan Hierarkiutsnitt i Power BI":::
 
 
När du väljer en eller flera underordnade objekt för ett objekt visas en halv-vald cirkel för objektet på den översta nivån.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Hierarkiutsnitt med enkel markering i Power BI":::

## <a name="format-the-slicer"></a>Formatera utsnittet

Beteendet för utsnittet ändras inte. Du kan också formatera utsnittet hur du vill. Du kan till exempel ställa in det på enkel markering-läge. Du kan också växla mellan en lista och listmeny. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Hierarkiutsnitt formaterat som en listruta":::

### <a name="change-the-expandcollapse-icon"></a>Ändra ikonen för visa/minimera

Hierarkiutsnitt har några andra formateringsalternativ. Du kan ändra visa/minimera-ikonen från standardpilen till ett plus/minus-tecken, eller ett cirkumflex.

1. Välj utsnittet och välj sedan **format**.
1. Expandera **objekt** och välj **visa/minimera-ikon**.
1. Välj mellan **sparr**, **plus/minus** eller **cirkumflex**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Välj en visa/minimera-ikon för hierarkiutsnittet":::
 
### <a name="change-the-indentation"></a>Ändra indrag

Om du har dåligt med utrymme i rapporten så kan du vilja minska indrag för underordnade objekt. Som standard är indraget 15 bildpunkter, men du kan öka eller minska det. 

1. Välj utsnittet och välj sedan **format**.
1. Expandera **objekt** och dra sedan **stegvis indrag** mindre eller större. Du kan också skriva in en siffra i rutan.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Ange indrag för hierarkiutsnitt":::

## <a name="next-steps"></a>Nästa steg

- [Utsnitt i Power BI](../visuals/power-bi-visualization-slicers.md)
- Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)