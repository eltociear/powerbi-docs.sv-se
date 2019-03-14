---
title: Så här konfigurerar du arbetsbelastningar i Power BI Premium
description: Lär dig att konfigurera arbetsbelastningar i en Power BI Premium-kapacitet.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/11/2019
LocalizationGroup: Premium
ms.openlocfilehash: 0baab138ee98d2ec96bc9f47e6e727525a57ed3e
ms.sourcegitcommit: f176ba9d52d50d93f264eca21bb3fd987dbf934b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57757256"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Konfigurera arbetsbelastningar i en Premium-kapacitet

I den här artikeln beskrivs aktivering och konfigurering av arbetsbelastningar för Power BI Premium-kapaciteter. Som standard stöder kapaciteterna endast arbetsbelastningen som är associerad med att köra Power BI-frågor. Frågearbetsbelastningar är optimerade för och begränsade av resurser som bestäms av din Premium-kapacitets SKU. Premium-kapaciteter har också stöd för ytterligare arbetsbelastningar som kan använda kapacitetsresurser.

## <a name="configure-workloads"></a>Konfigurera arbetsbelastningar

Du kan aktivera och konfigurera ytterligare arbetsbelastningar för AI, [Dataflöden](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) och [Sidnumrerade rapporter](paginated-reports-save-to-power-bi-service.md). Standardminnet för dessa arbetsbelastningar baseras på tillgängliga kapacitetsnoder för din SKU. De maximala minnesinställningarna är inte kumulativa. Minnet upp till det högsta värde som har angetts allokeras dynamiskt för AI och dataflöden, men allokeras statiskt för sidnumrerade rapporter. 

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Konfigurera arbetsbelastningar i Power BI-administratörsportalen

1. I **Kapacitetsinställningar** > **PREMIUM-KAPACITETER** väljer du en kapacitet.

1. Under **FLER ALTERNATIV** expanderar du **Arbetsbelastningar**.

1. Aktivera en eller flera arbetsbelastningar och ange ett värde för **Max minne**.   

    
    ![Aktivera arbetsbelastningar](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Klicka på **Godkänn**.

> [!NOTE]
> Om arbetsbelastningen för sidnumrerade rapporter är aktiverad kommer de sidnumrerade rapporterna innebära att du kan köra din egen kod vid rendering av rapporter (till exempel ändra textfärg dynamiskt baserat på innehållet). I Power BI Premium körs sidnumrerade rapporter i ett inneslutet område inom kapaciteten. Det maximala minne som du anger till det här området används, oavsett om arbetsbelastningen är aktiv eller inte. Om du använder Power BI-rapporter eller dataflöden i samma kapacitet, bör du ange ett så lågt minne för de sidnumrerade rapporterna att det inte påverkar andra arbetsbelastningar negativt. I sällsynta fall kan arbetsbelastningen för sidnumrerade rapporter bli otillgänglig. I det här fallet visar arbetsbelastningen ett feltillstånd i administratörsportalen och användarna uppnår tidsgränser vid rapportåtergivning. För att lösa det här problemet kan du inaktivera arbetsbelastningen och sedan aktivera den igen.


### <a name="rest-api"></a>REST-API

Arbetsbelastningar kan aktiveras och tilldelas till en kapacitet med hjälp av [Kapaciteter](https://docs.microsoft.com/rest/api/power-bi/capacities) REST API:er.


## <a name="next-steps"></a>Nästa steg

[Resurshantering och optimering av Power BI Premium-kapacitet](service-premium-understand-how-it-works.md)   
[Dataförberedelser med självbetjäning i Power BI med dataflöden](service-dataflows-overview.md)   
[Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)