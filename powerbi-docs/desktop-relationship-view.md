---
title: Relationsvy i Power BI Desktop
description: Relationsvy i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 178f3cd9015af503ff12875548822ba1ab5365c3
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54272776"
---
# <a name="relationship-view-in-power-bi-desktop"></a>Relationsvy i Power BI Desktop
**Relationsvyn** visar alla tabeller, kolumner och relationer i din modell. Det kan vara särskilt användbart när modellen har komplexa relationer mellan många tabeller.

Låt oss ta en titt.

![](media/desktop-relationship-view/relationshipview_fullscreen.png)

**A.**  Ikon för relationen – Klicka här för att visa din modell i relationsvyn

**B.** Relation – Du kan hålla muspekaren över en relation för att visa de använda kolumnerna. Dubbelklicka på en relation för att öppna den i dialogrutan **Redigera relation**. 

I bilden ovan kan du se att tabellen *Stores* har en *StoreKey*-kolumn som är relaterad till tabellen *Sales* som också har en *StoreKey*-kolumn. Det finns en *många-till-en-relation* (\*: 1) och ikonen mitt i raden visar att korsfilterriktningen är inställd på *båda*. Pilen på ikonen visar i vilken riktning kontextfiltret flödar.

Läs mer om relationer i [Skapa och hantera relationer i Power BI Desktop](desktop-create-and-manage-relationships.md).

