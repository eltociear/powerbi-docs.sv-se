---
title: Redigera parameterinställningar i Power BI-tjänsten
description: Frågeparametrar skapas i Power BI Desktop men kan granskas och uppdateras i Power BI-tjänsten
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 08/04/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 3b64c1dd502fd16199fbff9f64cd2c017006d1f1
ms.sourcegitcommit: a7227f6d3236e6e0a7bc1f83ff6099b5cd58bff3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87768484"
---
# <a name="edit-parameter-settings-in-the-power-bi-service"></a>Redigera parameterinställningar i Power BI-tjänsten
Rapportskapare lägger till i frågeparametrar till rapporter i Power BI Desktop. Med parametrar kan de göra så att delar av en rapport är beroende av en eller flera *parametervärden*. Rapportens skapare kan till exempel skapa en parameter som begränsar data till ett land/en region, eller en parameter som definierar godkända format för fält som datum, tid och text.

![Start-fliken med alternativet Hantera parametrar i Desktop](media/service-parameters/power-bi-manage-parameters.png)

## <a name="review-and-edit-parameters-in-power-bi-service"></a>Granska och redigera parametrar i Power BI-tjänsten

Som rapportskapare definierar du parametrar i Power BI Desktop. När du [publicerar rapporten till Power BI-tjänsten](../create-reports/desktop-upload-desktop-files.md) flyttas parameterinställningar och val med den. Du kan granska och redigera parameterinställningar i Power BI-tjänsten, men inte skapa dem.

1. Välj kugghjulsikonen i Power BI-tjänsten ![kugghjulsikon](media/service-parameters/power-bi-cog.png) för att öppna **Inställningar**.

2. Välj fliken **Datauppsättningar** och markera en datauppsättning i listan. 
    
    ![Fönstret Inställningar med fliken Datauppsättningar markerad](media/service-parameters/power-bi-select-dataset2.png)

3. Expandera **Parametrar**.  Om den valda datamängden inte har några parametrar visas ett meddelande med en länk till mer information om frågeparametrar. Om datamängden har parametrar visas de när du expanderar rubriken **Parametrar**. 

    ![Fönstret Inställningar med Parametrar expanderat](media/service-parameters/power-bi-settings.png)

    Granska parameterinställningarna och gör ändringar om det behövs. Nedtonade fält kan inte redigeras. 


## <a name="next-steps"></a>Nästa steg
Ett ad hoc-sätt att lägga till enkla parametrar är att [ändra URL:en](../collaborate-share/service-url-filters.md).
