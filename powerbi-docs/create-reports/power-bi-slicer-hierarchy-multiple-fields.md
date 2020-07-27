---
title: Lägga till flera fält i ett hierarkiutsnitt
description: Läs hur du skapar ett hierarkiutsnitt som innehåller flera fält i en hierarki.
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 07/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 5fbaeaafb14fc935e26b4a2d13acf9dc09ea188f
ms.sourcegitcommit: 11deeccf596e9bb8f22615276a152614f7579f35
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2020
ms.locfileid: "86409588"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>Lägga till flera fält i ett hierarkiutsnitt

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

Om du vill filtrera flera relaterade fält inom ett enda utsnitt kan du göra det genom att skapa vad som kallas för ett *hierarki*utsnitt. Du kan skapa dessa utsnitt i antingen Power BI Desktop eller i Power BI-tjänsten.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Skärmbild av hierarkiutsnittet i Power BI.":::

När du lägger till flera fält i utsnittet visas som standard en pil, eller *sparr*, bredvid de objekt som kan expanderas för att visa objekten på nästa nivå.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Skärmbild av listrutan för hierarkiutsnittet i Power BI.":::
 
 
När du väljer en eller flera underordnade objekt för ett objekt visas en halv-vald cirkel för objektet på den översta nivån.
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Skärmbild av hierarkiutsnitt med enkel markering i Power BI.":::

## <a name="format-the-slicer"></a>Formatera utsnittet

Beteendet för utsnittet ändras inte. Du kan också formatera utsnittet hur du vill. Du kan till exempel ställa in det på enkel markering-läge. Du kan också växla mellan en lista och listmeny. 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="Skärmbild av hierarkiutsnittet formaterat som ett listruteutsnitt.":::

Du kan också göra följande formateringsändringar.

### <a name="change-the-title"></a>Ändra rubriken

Du kan redigera rubriker för alla utsnitt, men denna möjlighet är särskilt användbar för hierarkiutsnitt. Ett hierarkiutsnitts namn består som standard av en lista över fältnamnen i hierarkin.

I det här exemplet visar utsnittets rubrik de tre fälten i hierarkin: Typ, Plattform och Namn.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="Skärmbild av hierarkiutsnitt med fälten Typ, Plattform och Namn.":::

Om du vill ändra namnet, så markera utsnittet och välj sedan fönstret **Format**. Under **Utsnittshuvud** visas det aktuella namnet på utsnittet i rutan **Rubriktext**.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="Skärmbild av fönstret Format med den aktuella rubriken.":::

Markera texten och lägg till ett nytt namn.

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="Skärmbild av ny rubrik för hierarkiutsnittet.":::


### <a name="change-the-expandcollapse-icon"></a>Ändra ikonen för visa/minimera

Hierarkiutsnitt har några andra formateringsalternativ. Du kan ändra visa/minimera-ikonen från standardpilen till ett plus/minus-tecken, eller ett cirkumflex.

1. Välj utsnittet och välj sedan **format**.
1. Expandera **objekt** och välj **visa/minimera-ikon**.
1. Välj mellan **sparr**, **plus/minus** eller **cirkumflex**.
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="Skärmbild av Välj en visa/dölj-ikon för hierarkiutsnittet.":::
 
### <a name="change-the-indentation"></a>Ändra indrag

Om du har dåligt med utrymme i rapporten så kan du vilja minska indrag för underordnade objekt. Som standard är indraget 15 bildpunkter, men du kan öka eller minska det. 

1. Välj utsnittet och välj sedan **format**.
1. Expandera **objekt** och dra sedan **stegvis indrag** mindre eller större. Du kan också skriva in en siffra i rutan.

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="Skärmbild av Ange indrag för hierarkiutsnitt.":::

## <a name="next-steps"></a>Nästa steg

- [Utsnitt i Power BI](../visuals/power-bi-visualization-slicers.md)
- Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)