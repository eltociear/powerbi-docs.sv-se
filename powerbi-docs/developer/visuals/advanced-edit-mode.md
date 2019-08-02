---
title: Avancerat redigeringsläge
description: Visuella objekt för Power BI med avancerade gränssnittskontroller
author: shaym83
ms.author: shaym
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 625105aed773bce5cf70932f092faf60ea001c2c
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425561"
---
# <a name="advanced-edit-mode"></a>Avancerat redigeringsläge

Visuella objekt som kräver avancerade gränssnittskontroller kan deklarera stöd för Avancerat redigeringsläge.
Om det stöds, visas knappen `Edit` på det visuella objektets meny i rapportredigeringsläge.
När användaren klickar på knappen `Edit` anges EditMode till `Advanced`.
EditMode-flaggan kan användas i det visuella objektet för att bestämma om sådana gränssnittskontroller ska visas.

Som standard har det visuella objektet inte stöd för Avancerat redigeringsläge.
Om ett annat beteende krävs måste det uttryckligen anges i det visuella objektets `capabilities.json`-fil genom att ange egenskapen `advancedEditModeSupport`.

Möjliga värden är:

- 0 – NotSupported

- 1 – SupportedNoAction

- 2 – SupportedInFocus

## <a name="entering-advanced-edit-mode"></a>Växla till Avancerat redigeringsläge

Knappen `Edit` visas om:

 1 – Egenskapen `advancedEditModeSupport` har angetts till `SupportedNoAction` eller `SupportedInFocus` i capabilities.json.

 2 – Det visuella objektet visas i rapportredigeringsläge.

Om egenskapen `advancedEditModeSupport` saknas i capabilities.json eller har angetts till `NotSupported` försvinner redigeringsknappen.

![Växla till redigeringsläge](./media/edit-mode.png)

När användaren klickar på `Edit` får det visuella objektet ett update()-anrop med EditMode inställt på `Advanced`.
Enligt det värde som angetts i funktionerna utförs följande åtgärder:

* `SupportedNoAction` – Ingen ytterligare åtgärd av värden.
* `SupportedInFocus` – Värden visar det visuella objektet i fokusläge.

## <a name="exiting-advanced-edit-mode"></a>Avsluta Avancerat redigeringsläge

Knappen `Back to report` visas om:

1 – Egenskapen `advancedEditModeSupport` har angetts till `SupportedInFocus` i capabilities.json.
