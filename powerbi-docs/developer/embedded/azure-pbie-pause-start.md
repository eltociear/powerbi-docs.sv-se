---
title: Pausa och starta din Power BI Embedded-kapacitet på Azure Portal | Microsoft Docs
description: Den här artikeln beskriver hur du pausar och startar en Power BI Embedded-kapacitet i Microsoft Azure.
services: power-bi-embedded
author: KesemSharabi
ms.author: kesharab
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 09/28/2017
ms.openlocfilehash: 07c9c12366b100936e03fe07358ee180e026dfc5
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114760"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>Pausa och starta din Power BI Embedded-kapacitet på Azure Portal

Den här artikeln beskriver hur du pausar och startar en Power BI Embedded-kapacitet i Microsoft Azure. Detta förutsätter att du har skapat en Power BI Embedded-kapacitet. Om du inte har gjort det läser du [Skapa Power BI Embedded-kapacitet på Azure Portal](azure-pbie-create-capacity.md) för att komma igång.

Om du inte har någon Azure-prenumeration kan du [skapa ett kostnadsfritt konto](https://azure.microsoft.com/free/) innan du börjar.

## <a name="pause-your-capacity"></a>Pausa din kapacitet

När du pausar din kapacitet debiteras du inte längre. Pausa din kapacitet om du inte behöver använda kapaciteten under en viss tidsperiod. Följ stegen nedan om du vill pausa din kapacitet.

> [!NOTE]
> Om du pausar en kapacitet kan det hända att innehåll inte är tillgängligt i Power BI. Ta bort tilldelningar av arbetsytor från din kapacitet innan du pausar kapaciteten för att förhindra avbrott.

1. Logga in på [Azure Portal](https://portal.azure.com/).

2. Visa dina kapaciteter genom att välja **Alla tjänster** > **Power BI Embedded**.

    ![Alla tjänster på Azure Portal](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Välj den kapacitet som du vill pausa.

    ![Lista över Power BI Embedded-kapaciteter på Azure Portal](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Välj **Pausa** i kapacitetsinformationen.

    ![Pausa din kapacitet](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. Välj **Ja** för att bekräfta att du vill pausa kapaciteten.

    ![Bekräfta att du vill pausa kapaciteten](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>Starta din kapacitet

Återuppta användningen genom att starta din kapacitet. När du startar din kapacitet startar även debiteringen igen.

1. Logga in på [Azure Portal](https://portal.azure.com/).

2. Visa dina kapaciteter genom att välja **Alla tjänster** > **Power BI Embedded**.

    ![Alla tjänster på Azure Portal](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. Välj den kapacitet som du vill starta.

    ![Lista över Power BI Embedded-kapaciteter på Azure Portal](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. Välj **Starta** i kapacitetsinformationen.

    ![Starta din kapacitet](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. Välj **Ja** för att bekräfta att du vill starta kapaciteten.

    ![Bekräfta att du vill starta kapaciteten](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

Om innehåll har tilldelats den här kapaciteten är det tillgängligt när kapaciteten har startats.

## <a name="next-steps"></a>Nästa steg

Om du vill skala upp eller ned din kapacitet läser du [Skala din Power BI Embedded-kapacitet](azure-pbie-scale-capacity.md).

Om du vill börja bädda in Power BI-innehåll i ditt program läser du [Bädda in Power BI-instrumentpaneler, -rapporter och -paneler](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)