---
title: Ange rapportvyer för sidnumrerade rapporter – Power BI
description: I den här artikeln får du lära dig mer om de olika rapportvyerna för sidnumrerade rapporter i Power BI-tjänsten.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: ''
ms.topic: how-to
ms.date: 05/14/2020
ms.openlocfilehash: 5ed7f3a05be1e600fc67e5162b496309ce315f94
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85230955"
---
# <a name="set-report-views-for-paginated-reports-in-the-power-bi-service"></a>Ange rapportvyer för sidnumrerade rapporter i Power BI-tjänsten

När du visar en sidnumrerad rapport i Power BI-tjänsten är standardvyn HTML-baserad och interaktiv. Det nya alternativet Sidvisning är en annan rapportvy för fasta sidformat som PDF.

**Interaktiv vy (standard)**

![Standardvy](media/page-view/power-bi-paginated-default-view.png)

**Sidvisning**

![Sidvisning](media/page-view/power-bi-paginated-page-view.png)

I Sidvisning ser rapporten annorlunda ut jämfört med standardvyn. Vissa egenskaper och begrepp i sidnumrerade rapporter gäller endast för fasta sidor. Vyn ser ut ungefär som när rapporten skrivs ut eller exporteras. Du kan fortfarande ändra vissa element, till exempel parametervärden, men det finns inga andra interaktiva funktioner som sortering av kolumner eller växlingsknappar.

Sidvisning stöder alla funktioner som PDF-visningsprogrammet i webbläsaren stöder, till exempel zooma in, zooma ut och anpassa till sida.

## <a name="switch-to-page-view"></a>Växla till sidvisning

När du öppnar en sidnumrerad rapport visas den interaktiva vyn som standard. Om rapporten har parametrar väljer du parametrar och visar sedan rapporten.

1. Välj **Visa** i verktygsfältet > **Sidvisning**.

    ![Växla till sidvisning](media/page-view/power-bi-paginated-page-view-dropdown.png)

2. Du kan ändra inställningarna för sidvisning genom att välja **Sidinställningar** på **Visa**-menyn i verktygsfältet. 

    ![Välja Sidinställningar](media/page-view/power-bi-paginated-page-settings-dropdown.png)
    
    I dialogrutan **Sidinställningar** finns alternativ för att ange **sidstorlek** och **orientering** för sidvisningen. När du har tillämpat sidinställningarna gäller samma alternativ när du skriver ut sidan senare.
   
    ![Dialogrutan Sidinställningar](media/page-view/power-bi-paginated-page-settings-dialog.png)

3. Om du vill växla tillbaka till den interaktiva vyn väljer du **Standard** i listrutan **Visa**.

## <a name="browser-support"></a>Stöd för webbläsare

Sidvisning stöds i webbläsarna Google Chrome och Microsoft Edge. Kontrollera att visning av PDF-filer har aktiverats i webbläsaren. Det är standardinställningen för dessa webbläsare.

Sidvisning stöds inte i Internet Explorer och Safari, så alternativet är inaktiverat. Det stöds inte heller i webbläsare på mobila enheter eller i Power BI-mobilappar.  


## <a name="next-steps"></a>Nästa steg

- [Visa en sidnumrerad rapport i Power BI-tjänsten](../consumer/paginated-reports-view-power-bi-service.md)
- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
