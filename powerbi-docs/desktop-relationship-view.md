---
title: Relationsvy i Power BI Desktop
description: Relationsvy i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: cd9671b8c38cb2aa1502c3aa00a871d125f819b1
ms.sourcegitcommit: 97597ff7d9ac2c08c364ecf0c729eab5d59850ce
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760490"
---
# <a name="work-with-relationship-view-in-power-bi-desktop"></a>Arbeta med relationsvyn i Power BI Desktop
**Relationsvyn** visar alla tabeller, kolumner och relationer i din modell. Det kan vara särskilt användbart när modellen har komplexa relationer mellan många tabeller.

Låt oss ta en titt.

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Ikon för relationen – Klicka här för att visa din modell i relationsvyn

**B.** Relation – Du kan hålla muspekaren över en relation för att visa de använda kolumnerna. Dubbelklicka på en relation för att öppna den i dialogrutan **Redigera relation**. 

I bilden ovan kan du se att tabellen *Stores* har en *StoreKey*-kolumn som är relaterad till tabellen *Sales* som också har en *StoreKey*-kolumn. Det finns en *många-till-en-relation* (\*: 1) och ikonen mitt i raden visar att korsfilterriktningen är inställd på *båda*. Pilen på ikonen visar i vilken riktning kontextfiltret flödar.

Läs mer om relationer i [Skapa och hantera relationer i Power BI Desktop](desktop-create-and-manage-relationships.md).

