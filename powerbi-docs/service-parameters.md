---
title: Visa och redigera inställningar för datauppsättningsparametrar i Power BI-tjänsten
description: Frågeparametrar skapas i Power BI Desktop men kan granskas och uppdateras i Power BI-tjänsten
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: ac271e8013bce5824931153351a651644a716a2f
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965169"
---
# <a name="what-is-a-query-parameter"></a>Vad är en frågeparameter?
Frågeparametrar läggs till i Power BI Desktop av rapportskapare. Med parametrar kan de göra så att delar av en rapport är beroende av en eller flera *parametervärden*. Rapportens skapare kan till exempel skapa en parameter som begränsar data till ett land eller en region, eller en parameter som definierar godkända format för fält som datum, tid och text.

![Start-fliken med alternativet Hantera parametrar i Desktop](media/service-parameters/power-bi-manage-parameters.png)


## <a name="review-and-edit-parameters-in-power-bi-service"></a>Granska och redigera parametrar i Power BI-tjänsten

När parametrarna har definierats i Desktop följer parameterinställningarna och valda alternativ med när [rapporten publiceras till Power BI-tjänsten](desktop-upload-desktop-files.md). Vissa parameterinställningar kan granskas och redigeras i Power BI-tjänsten – inte parametrar som begränsar tillgängliga data, men däremot de parametrar som definierar och beskriver godkända värden.

1. Välj kugghjulsikonen i Power BI-tjänsten ![kugghjulsikon](media/service-parameters/power-bi-cog.png) för att öppna **Inställningar**.

2. Välj fliken **Datauppsättningar** och markera en datauppsättning i listan. 
    
    ![Fönstret Inställningar med fliken Datauppsättningar markerad](media/service-parameters/power-bi-select-dataset2.png)

3. Expandera **Parametrar**.  Om den valda datauppsättningen inte har några parametrar, visas ett meddelande med en länk till mer information om frågeparametrar. Om datauppsättningen har parametrar visas dessa när rubriken **Parametrar** expanderas. 

    ![Fönstret Inställningar med Parametrar expanderat](media/service-parameters/power-bi-settings.png)

    Granska parameterinställningarna och gör ändringar om det behövs. Gråtonade fält kan inte redigeras. 


## <a name="next-steps"></a>Nästa steg
Ett ad hoc-sätt att lägga till enkla parametrar är att [ändra URL:en](service-url-filters.md).