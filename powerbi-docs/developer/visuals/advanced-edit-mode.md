---
title: Avancerat redigeringsläge i visuella Power BI-objekt
description: Den här artikeln beskriver hur du anger avancerade UI-kontroller i visuella Power BI-objekt.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: da72cf603027bc97060e7a00ed4a4e959a3a92e2
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71194465"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Avancerat redigeringsläge i visuella Power BI-objekt

Om du behöver avancerade UI-kontroller i ditt visuella Power BI-objekt kan du använda de avancerade redigeringsläget. När du är i rapportredigeringsläge väljer du knappen **Redigera** för att ange redigeringsläget till **Avancerat**. Det visuella objektet kan använda flaggan `EditMode` för att bestämma huruvida det ska visa denna UI-kontroll.

Som standard har det visuella objektet inte stöd för avancerat redigeringsläge. Om ett annat beteende krävs kan du uttryckligen ange detta i det visuella objektets *capabilities.json*-fil genom att ange egenskapen `advancedEditModeSupport`.

Möjliga värden är:

- `0` – NotSupported

- `1` – SupportedNoAction

- `2` – SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>Öppna avancerat redigeringsläge

Knappen **Redigera** visas om:

* Egenskapen `advancedEditModeSupport` anges i filen *capabilities.json* till antingen `SupportedNoAction` eller `SupportedInFocus`.

* Det visuella objektet visas i rapportredigeringsläge.

Om egenskapen `advancedEditModeSupport` saknas i filen *capabilities.json* eller har angetts till `NotSupported` visas inte knappen **Redigera**.

![Växla till redigeringsläge](./media/edit-mode.png)

När du väljer **Redigera** får det visuella objektet ett anrop av update() med redigeringsläget angett till `Advanced`. Beroende på det värde som anges i filen *capabilities.json* utförs följande åtgärder:

* `SupportedNoAction`: Ingen ytterligare åtgärd krävs av värden.
* `SupportedInFocus`: Värden visar det visuella objektet i fokusläge.

## <a name="exit-advanced-edit-mode"></a>Avsluta avancerat redigeringsläge

Knappen **Tillbaka till rapport** visas om:

* Egenskapen `advancedEditModeSupport` anges i filen *capabilities.json* till `SupportedInFocus`.
