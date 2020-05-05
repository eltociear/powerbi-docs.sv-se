---
title: Power BI-arbetsyteroller
description: Tabell för Power BI-arbetsyteroller
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 04/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 9a6ca5abf3c26af876666ef45fe7ae192e69f2a3
ms.sourcegitcommit: 9ec2c608b90bf651df613f0714addd251a885039
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/24/2020
ms.locfileid: "82120371"
---
Här är funktionerna för de fyra rollerna: administratörer, medlemmar, deltagare och läsare. För alla dessa funktioner (utom visning och interaktion) krävs en Power BI Pro-licens.

|Kapacitet   | Admin  | Medlem  | Deltagare  | Läsare |
|---|---|---|---|---|
| Uppdatera och ta bort arbetsytan.  | X  |   |   |   | 
| Lägga till/ta bort personer, inklusive andra administratörer.  | X  |   |   |   |
| Lägga till medlemmar eller andra med lägre behörighet.  |  X | X  |   |   |
| Publicera och uppdatera en app. |  X | X  |   |   |
| Dela ett objekt eller dela en app.<sup>1</sup> |  X | X  |   |   |
| Tillåta att andra delar objekt igen.<sup>1</sup> |  X | X  |   |   |
| Framhäva appar på kollegors startsida |  X | X  |   |   |
| Framhäva instrumentpaneler och rapporter på kollegors startsida |  X | X  | X |   |
| Skapa, redigera och ta bort innehåll på arbetsytan.  |  X | X  | X  |   |
| Publicera rapporter till arbetsytan och ta bort innehåll.  |  X | X  | X  |   |
| Skapa en rapport på en annan arbetsyta baserat på en datamängd i den här arbetsytan.<sup>1</sup> |  X | X  | X  |   |
| Kopiera en rapport.<sup>2</sup> | X | X | X |  |
| Visa och interagera med ett objekt.<sup>3</sup> |  X | X  | X  | X  |
| Läs data som lagrats på arbetsytedataflöden | X | X | X | X |

1. Deltagare och användare kan dela objekt i en arbetsyta om de har omdelningsbehörighet.
2. För att kunna kopiera en rapport och skapa en rapport i en annan arbetsyta baserat på en datauppsättning i den här arbetsytan behöver du behörigheten Skapa för datauppsättningen. Personer med administratörs-, medlems- och deltagarroller har behörigheten Skapa för datauppsättningar i den här arbetsytan via rollen för arbetsytan.
3. Även om du inte har en Power BI Pro-licens kan du visa och interagera med objekt i Power BI-tjänsten om objekten finns i en arbetsyta i en Premium-kapacitet.

