---
title: Så här konfigurerar du arbetsbelastningar i Power BI Premium
description: Lär dig att konfigurera arbetsbelastningar i en Power BI Premium-kapacitet.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: 49a1f02e5aa327c2704b6c2d789934a43b760ad0
ms.sourcegitcommit: 0e50ebfa8762e19286566432870ef16d242ac78f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2019
ms.locfileid: "68962018"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Konfigurera arbetsbelastningar i en Premium-kapacitet

I den här artikeln beskrivs aktivering och konfigurering av arbetsbelastningar för Power BI Premium-kapaciteter. Som standard stöder kapaciteterna endast arbetsbelastningen som är associerad med att köra Power BI-frågor. Du kan också aktivera och konfigurera ytterligare arbetsbelastningar för **[AI (Cognitive Services)](service-cognitive-services.md)**, **[Dataflöden](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** och **[Sidnumrerade rapporter](paginated-reports-save-to-power-bi-service.md)**.

## <a name="default-memory-settings"></a>Standardinställningar för minne

Frågearbetsbelastningar är optimerade för och begränsade av resurser som bestäms av din Premium-kapacitets SKU. Premium-kapaciteter har också stöd för ytterligare arbetsbelastningar som kan använda din kapacitets resurser. Standardminnet för dessa arbetsbelastningar baseras på tillgängliga kapacitetsnoder för din SKU. De maximala minnesinställningarna är inte kumulativa. Minnet upp till det högsta värde som har angetts allokeras dynamiskt för AI och dataflöden, men allokeras statiskt för sidnumrerade rapporter.

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>Microsoft Office-SKU:er för SaaS-scenarier (programvara som en tjänst)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | Saknas | Saknas | 20 % standard, 20 % minimum | 20 % standard, 10 % minimum | 20 % standard, 5 % minimum |
| Dataflöden | Saknas |20 % standard, 12 % minimum  | 20 % standard, 5 % minimum  | 20 % standard, 3 % minimum | 20 % standard, 2 % minimum  |
| Sidnumrerade rapporter | Saknas |Saknas | 20 % standard, 10 % minimum | 20 % standard, 5 % minimum | 20 % standard, 2,5 % minimum |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>Microsoft Azure-SKU:er för PaaS-scenarier (plattform som en tjänst)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | Saknas                      | 20 % standard, 100 % minimum                     | 20 % standard, 50 % minimum                     | 20 % standard, 20 % minimum | 20 % standard, 10 % minimum | 20 % standard, 5 % minimum |
| Dataflöden         | 40 % standard, 40 % minimum | 24 % standard, 24 % minimum | 20 % standard, 12 % minimum | 20 % standard, 5 % minimum  | 20 % standard, 3 % minimum | 20 % standard, 2 % minimum   |
| Sidnumrerade rapporter | Saknas                      | Saknas                      | Saknas                     | 20 % standard, 10 % minimum | 20 % standard, 5 % minimum | 20 % standard, 2,5 % minimum |
| | | | | | |

## <a name="workload-settings"></a>Inställningar för arbetsbelastning

### <a name="ai-preview"></a>AI (förhandsversion)

Utöver inställningen **Max minne** har AI-arbetsbelastningen ytterligare en inställning, **Tillåt användning från Power BI Desktop**. Standard är **Av**. Den här inställningen är reserverad för framtida användning och visas kanske inte i alla klientorganisationer.

### <a name="datasets-preview"></a>Datamängder (förhandsversion)

Som standard är arbetsbelastningen Datamängder aktiverad och kan inte inaktiveras. Den här arbetsbelastningen innehåller ytterligare en inställning för _XMLA-slutpunkten_ och en uppsättning med prestandarelaterade inställningar. Den här inställningen för **XMLA-slutpunkt** anger att anslutningar från klientprogram följer det medlemsuppsättningen för säkerhetsgrupp på nivåerna för arbetsyta och app. Mer information finns i [Ansluta till datamängder med klientprogram och verktyg](service-premium-connect-tools.md).

De prestandarelaterade inställningarna beskrivs i följande tabell.

| Inställningsnamn | Beskrivning | Användning |
|---------------------------------|----------------------------------------|----------------------------------------|
| **Maximalt antal mellanliggande raduppsättningar** | Det maximala antalet mellanliggande rader som returneras av DirectQuery. Standardvärdet är angett till 1000000, och det tillåtna intervallet är mellan 100000 och 2147483647 | Kontrollerar påverkan från resursintensiva eller dåligt utformade rapporter. |
| **Maximal storlek för offlinedatamängd (GB)** | Maximal storlek för offlinedatamängden i minnet. Detta är den komprimerade storleken på disken. Standardvärdet anges av SKU, och det tillåtna intervallet är 0,1–10 GB | Förhindra att rapportskapare publicerar en stor datamängd som kan påverka kapaciteten negativt. |
| **Maximalt antal resultatraduppsättningar** | Definierar det maximala antalet rader som returneras i en DAX-fråga. Standardvärdet är angett till 1 (ingen gräns), och det tillåtna intervallet är mellan 100000 och 2147483647 | Kontrollerar påverkan från resursintensiva eller dåligt utformade rapporter. |
| **Minnesgräns för frågor (%)** | Gäller endast för DAX-mått och frågor. Anges i % och begränsar hur mycket minne som kan användas av tillfälliga resultat under en fråga. | Kontrollerar påverkan från resursintensiva eller dåligt utformade rapporter. |
| **Tidsgräns för frågor (sekunder)** | Ett heltal som definierar tidsgränsen, i sekunder, för frågor. Standardvärdet är 3600 sekunder (det vill säga 60 minuter). Noll (0) anger att det inte finns någon tidsgräns för frågor. | Ha bättre kontroll över tidskrävande frågor. |
|  |  |  |

### <a name="dataflows"></a>Dataflöden

Utöver inställningen **Max minne** har arbetsbelastningen Dataflöden ytterligare en inställning, **Containerstorlek**. Med den här inställningen kan du optimera prestanda för dataflödesarbetsbelastning för bearbetning av mer komplexa, beräkningsintensiva dataflöden.

Vid uppdatering av ett dataflöde skapar dataflödesarbetsbelastningen en container för varje entitet i dataflödet. Varje container kan ta minne upp till den volym som anges i inställningen Containerstorlek. Standardvärdet för alla SKU:er är **700 MB**. Den här inställningen bör kanske ändras om:

- Dataflöden tar för lång tid att uppdateras eller om uppdatering av dataflöde misslyckas med överskriden tidsgräns.
- Dataflödesentiteter omfattar beräkningssteg, till exempel en koppling.  

Vi rekommenderar att du använder appen [Kapacitetsmått för Power BI Premium](service-admin-premium-monitor-capacity.md) för att analysera prestanda för dataflödesarbetsbelastning. 

I vissa fall förbättras kanske inte prestandan av att containerstorleken ökas. Om dataflödet till exempel bara hämtar data från en källa utan att utföra betydande beräkningar hjälper det förmodligen inte att öka containerstorleken. Ökning av containerstorleken kan vara till hjälp om det gör att dataflödesarbetsbelastningen kan allokera mer minne för åtgärder för entitetsuppdatering. Genom att ha mer allokerat minne kan den tid det tar att uppdatera kraftigt beräknade entiteter minskas.

Värdet för Containerstorlek kan inte överskrida det maximala minnet för dataflödesarbetsbelastningen. Till exempel har en P1-kapacitet 25 GB minne. Om Maximalt minne för dataflödesarbetsbelastning (%) anges till 20 % kan Containerstorlek (MB) inte överstiga 5000. I samtliga fall kan containerstorleken inte överskrida Max minne, även om du anger ett högre värde.

### <a name="paginated-reports-preview"></a>Sidnumrerade rapporter (förhandsversion)

Sidnumrerade rapporter gör att anpassad kod kan köras vid rendering av en rapport. Det kan till exempel gälla dynamisk ändring av textfärg baserat på innehåll, vilket kan kräva ytterligare minne. I Power BI Premium körs sidnumrerade rapporter i ett inneslutet område inom kapaciteten. Det Max minne som anges används *oavsett huruvida* arbetsbelastningen är aktiv. Om du ändrar inställningen Max minne från standardvärdet ska du se till att ange det lågt nog så att det inte påverkar andra arbetsbelastningar negativt.

I vissa fall kan arbetsbelastningen Sidnumrerade rapporter bli otillgänglig. I det här fallet visar arbetsbelastningen ett feltillstånd i administratörsportalen, och användarna ser överskridna tidsgränser vid rendering av rapporter. För att lösa det här problemet kan du inaktivera arbetsbelastningen och sedan aktivera den igen.

## <a name="configure-workloads"></a>Konfigurera arbetsbelastningar

Maximera din kapacitets tillgängliga resurser genom att aktivera arbetsbelastningar endast om de ska användas. Ändra endast minnet och andra inställningar när du har fastställt att standardinställningarna inte uppfyller dina kapacitetskrav för resursen.

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Konfigurera arbetsbelastningar i Power BI-administratörsportalen

1. I **Kapacitetsinställningar** > **PREMIUM-KAPACITETER** väljer du en kapacitet.

1. Under **FLER ALTERNATIV** expanderar du **Arbetsbelastningar**.

1. Aktivera en eller flera arbetsbelastningar och ange ett värde för **Max minne** och andra inställningar.

1. Välj **Tillämpa**.

### <a name="rest-api"></a>REST-API

Arbetsbelastningar kan aktiveras och tilldelas till en kapacitet med hjälp av [Kapaciteter](https://docs.microsoft.com/rest/api/power-bi/capacities) REST API:er.

## <a name="monitoring-workloads"></a>Övervaka arbetsbelastningar

[Power BI Premium-appen för kapacitetsmått](service-admin-premium-monitor-capacity.md) ger mått på datauppsättning, dataflöden och sidnumrerade rapporter för att övervaka arbetsbelastningar som aktiverats för din kapacitet. 

## <a name="next-steps"></a>Nästa steg

[Optimera Power BI Premium-kapaciteter](service-premium-capacity-optimize.md)     
[Dataförberedelser med självbetjäning i Power BI med dataflöden](service-dataflows-overview.md)   
[Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)