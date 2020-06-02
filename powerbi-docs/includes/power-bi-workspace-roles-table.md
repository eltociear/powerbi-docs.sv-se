---
title: Power BI-arbetsyteroller
description: Tabell för Power BI-arbetsyteroller
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 05/26/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 708599eb3f39d4c627a11753cb964d6425f75640
ms.sourcegitcommit: a7b142685738a2f26ae0a5fa08f894f9ff03557b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84120439"
---
|Kapacitet   | Admin  | Medlem  | Deltagare  | Läsare |
|---|---|---|---|---|
| Uppdatera och ta bort arbetsytan.  |  |   |   |   | 
| Lägga till/ta bort personer, inklusive andra administratörer.  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Lägga till medlemmar eller andra med lägre behörighet.  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Publicera och uppdatera en app. |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Dela ett objekt eller dela en app.<sup>1</sup> |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Tillåta att andra delar objekt igen.<sup>1</sup> |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Framhäva appar på kollegors startsida |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Framhäva instrumentpaneler och rapporter på kollegors startsida |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| Skapa, redigera och ta bort innehåll på arbetsytan.  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Publicera rapporter till arbetsytan och ta bort innehåll.  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Skapa en rapport på en annan arbetsyta baserat på en datamängd på den aktuella arbetsytan.<sup>2</sup> |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Kopiera en rapport.<sup>2</sup> | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Schemalägg datauppdateringar via den lokala gatewayen.<sup>3</sup> | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Modifiera anslutningsinställningar för gateway.<sup>3</sup> | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Visa och interagera med ett objekt.<sup>4</sup> |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| Läs data som lagrats på arbetsytedataflöden | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> Deltagare och användare kan också dela objekt i en arbetsyta om de har omdelningsbehörighet.

<sup>2</sup> För att kunna kopiera en rapport och skapa en rapport i en annan arbetsyta baserat på en datauppsättning i den här arbetsytan behöver du behörigheten [Skapa för datauppsättningen](../connect-data/service-datasets-build-permissions.md). Personer med administratörs-, medlems- och deltagarroller har automatiskt behörigheten Skapa för datauppsättningar i den här arbetsytan via rollen för arbetsytan.

<sup>3</sup> Tänk på att du även behöver behörigheter på gatewayen. Dessa behörigheter hanteras någon annanstans, oberoende av arbetsytans roller och behörigheter. Mer information finns i [Manage an on-premises gateway](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) (Hantera en lokal gateway).

<sup>4</sup> Även om du inte har en Power BI Pro-licens kan du visa och interagera med objekt i Power BI-tjänsten om objekten finns i en arbetsyta i en Premium-kapacitet.

