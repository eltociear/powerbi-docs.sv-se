---
title: Power BI-arbetsyteroller
description: Tabell för Power BI-arbetsyteroller
services: powerbi
author: maggiesMSFT
ms.service: powerbi
ms.topic: include
ms.date: 06/23/2020
ms.author: maggies
ms.custom: include file
ms.openlocfilehash: 9ddf9df0feaed2a2a0177d11e9b36f34135801c6
ms.sourcegitcommit: caf60154a092f88617eb177bc34fb784f2365962
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365288"
---
|Kapacitet   | Admin  | Medlem  | Deltagare  | Läsare |
|---|---|---|---|---|
| Uppdatera och ta bort arbetsytan.  |  |   |   |   | 
| Lägga till/ta bort personer, inklusive andra administratörer.  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Tillåt deltagare att uppdatera appen för arbetsytan  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |   |   |   |
| Lägga till medlemmar eller andra med lägre behörighet.  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Publicera och ändra behörigheter för en app |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Uppdatera en app. |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |  Om tillåtet <sup>1</sup>  |   |
| Dela ett objekt eller dela en app.<sup>2</sup> |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Tillåta att andra delar objekt igen.<sup>2</sup> |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Framhäva appar på kollegors startsida |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |   |
| Framhäva instrumentpaneler och rapporter på kollegors startsida |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |   |
| Skapa, redigera och ta bort innehåll på arbetsytan.  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Publicera rapporter till arbetsytan och ta bort innehåll.  |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Skapa en rapport på en annan arbetsyta baserat på en datamängd på den aktuella arbetsytan.<sup>2</sup> |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |   |
| Kopiera en rapport.<sup>3</sup> | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Schemalägg datauppdateringar via den lokala gatewayen.<sup>4</sup> | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Modifiera anslutningsinställningar för gateway.<sup>4</sup> | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |  |
| Visa och interagera med ett objekt.<sup>5</sup> |  ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png)  |
| Läs data som lagrats på arbetsytedataflöden | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) | ![Ja-kryssmarkering](media/power-bi-workspace-roles-table/green-checkmark.png) |

<sup>1</sup> Om [arbetsytans administratör delegerar denna behörighet till deltagare](../collaborate-share/service-create-the-new-workspaces.md#security-settings) kan dessa uppdatera appens metadata, men inte publicera någon ny app eller ändra vem som har behörighet till appen.

<sup>2</sup> Deltagare och användare kan också dela objekt på en arbetsyta om de har omdelningsbehörigheter.

<sup>3</sup> För att kunna kopiera en rapport och skapa en rapport på en annan arbetsyta baserat på en datauppsättning på den här arbetsytan behöver du behörigheten [Skapa för datauppsättningen](../connect-data/service-datasets-build-permissions.md). Personer med administratörs-, medlems- och deltagarroller har automatiskt behörigheten Skapa för datauppsättningar i den här arbetsytan via rollen för arbetsytan.

<sup>4</sup> Tänk på att du även behöver behörigheter på gatewayen. Dessa behörigheter hanteras någon annanstans, oberoende av arbetsytans roller och behörigheter. Mer information finns i [Manage an on-premises gateway](https://docs.microsoft.com/data-integration/gateway/service-gateway-manage) (Hantera en lokal gateway).

<sup>5</sup> Även om du inte har en Power BI Pro-licens kan du visa och interagera med objekt i Power BI-tjänsten om objekten finns på en arbetsyta i en Premium-kapacitet.
