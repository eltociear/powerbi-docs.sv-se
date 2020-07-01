---
title: Modellvy i Power BI Desktop
description: Modellvy i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 1c580d403ef33f1c61d5fcd0707d78b4b331da5d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239866"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>Arbeta med modellvyn i Power BI Desktop

*Modellvyn* visar alla tabeller, kolumner och relationer i din modell. Den här vyn är särskilt användbar om modellen har komplexa relationer mellan många tabeller.

Välj **modellikonen** nära kanten av fönstret om du vill visa en vy över den befintliga modellen. Håll muspekaren över en relationslinje om du vill visa de kolumner som används.

![Modellvy i Power BI Desktop](media/desktop-relationship-view/model-view-full-screen.png)

På bilden ovan har tabellen *Stores* en *StoreKey*-kolumn som är relaterad till tabellen *Sales* som också har en *StoreKey*-kolumn. Dessa två tabeller har en *många-till-en-relation* (\*:1). Pilen i mitten av linjen visar i filterkontextens riktning. Dubbelpilen betyder att korsfilterriktningen har angetts till *Båda*.

Om du dubbelklickar på en relation öppnas den i dialogrutan **Redigera relation**. Läs mer om relationer i [Skapa och hantera relationer i Power BI Desktop](desktop-create-and-manage-relationships.md).
