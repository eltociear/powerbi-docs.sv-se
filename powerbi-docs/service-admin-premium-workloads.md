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
ms.date: 08/21/2019
LocalizationGroup: Premium
ms.openlocfilehash: 2d2eb51c5aad44572f1b427248fd85ef19a6306f
ms.sourcegitcommit: e62889690073626d92cc73ff5ae26c71011e012e
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "69985697"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Konfigurera arbetsbelastningar i en Premium-kapacitet

I den här artikeln beskrivs aktivering och konfigurering av arbetsbelastningar för Power BI Premium-kapaciteter. Som standard stöder kapaciteterna endast arbetsbelastningen som är associerad med att köra Power BI-frågor. Du kan också aktivera och konfigurera ytterligare arbetsbelastningar för **[AI (Cognitive Services)](service-cognitive-services.md)** , **[Dataflöden](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** och **[Sidnumrerade rapporter](paginated-reports-save-to-power-bi-service.md)** .

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

Med AI-arbetsbelastningen kan du använda Cognitive Services och automatiserad Machine Learning i Power BI. Använd nedanstående inställningar för att styra arbetsbelastningsbeteendet.

| Inställningsnamn | Beskrivning |
|---------------------------------|----------------------------------------|
| **Maximalt minne (%)** | Den maximala procentandelen tillgängligt minne som AI-processer kan använda i en kapacitet. |
| **Tillåt användning från Power BI Desktop** | Den här inställningen är reserverad för framtida användning och syns kanske inte i alla klientorganisationer. |
| **Tillåt byggandet av maskininlärningsmodeller** | Anger om affärsanalytiker kan träna, verifiera och anropa maskininlärningsmodeller direkt i Power BI. Mer information finns i [Automatiserad Machine Learning i Power BI (förhandsversion)](service-machine-learning-automated.md). |
| **Aktivera parallellitet för AI-begäranden** | Anger om AI-begäranden kan köras parallellt. |
|  |  |

### <a name="datasets"></a>Datauppsättningar

Som standard är datamängdernas arbetsbelastning aktiverad och kan inte inaktiveras. Använd nedanstående inställningar för att styra arbetsbelastningsbeteendet.

| Inställningsnamn | Beskrivning |
|---------------------------------|----------------------------------------|
| **Maximalt minne (%)** | Den maximala procentandelen tillgängligt minne som datamängder kan använda i en kapacitet. |
| **XMLA-slutpunkt** | Anger att anslutningar från klientprogram följer medlemsuppsättningen för säkerhetsgrupper på nivåerna för arbetsyta och app. Mer information finns i [Ansluta till datamängder med klientprogram och verktyg](service-premium-connect-tools.md). |
| **Maximalt antal mellanliggande raduppsättningar** | Det maximala antalet mellanliggande rader som returneras av DirectQuery. Standardvärdet är 1 000 000 och det tillåtna intervallet är mellan 100 000 och 2 147 483 647. Använd inställningen för att styra påverkan från resursintensiva eller bristfälligt utformade rapporter. |
| **Maximal storlek för offlinedatamängd (GB)** | Maximal storlek för offlinedatamängden i minnet. Detta är den komprimerade storleken på disken. Standardvärdet anges av SKU:n och det tillåtna intervallet är 0,1–10 GB. Använd inställningen till att förhindra att rapportskapare publicerar en stor datamängd som kan påverka kapaciteten negativt. |
| **Maximalt antal resultatraduppsättningar** | Det maximala antalet rader som returneras i en DAX-fråga. Standardvärdet är -1 (ingen gräns) och det tillåtna intervallet är mellan 100 000 och 2 147 483 647. Använd inställningen för att styra påverkan från resursintensiva eller bristfälligt utformade rapporter. |
| **Minnesgräns för frågor (%)** | Den maximala procentandelen tillgängligt minne som kan användas för tillfälliga resultat i en fråga eller ett DAX-mått. Använd inställningen för att styra påverkan från resursintensiva eller bristfälligt utformade rapporter. |
| **Tidsgräns för frågor (sekunder)** | Maximal tid innan tidsgränsen för frågan uppnås. Standardvärdet är 3 600 sekunder (en timme). Värdet 0 anger att frågorna inte har någon tidsgräns. Använd inställningen till att få bättre kontroll över tidskrävande frågor. |
|  |  |  |

### <a name="dataflows"></a>Dataflöden

I dataflödenas arbetsbelastning kan du använda den självbetjänade dataförberedelsen för dataflöden till att mata in, transformera, integrera och utöka data. Använd nedanstående inställningar för att styra arbetsbelastningsbeteendet.

| Inställningsnamn | Beskrivning |
|---------------------------------|----------------------------------------|
| **Maximalt minne (%)** | Den maximala procentandelen tillgängligt minne som dataflöden kan använda i en kapacitet. |
| **Förbättrad beräkningsmotor för dataflöden (förhandsversion)** | Aktivera det här alternativet för upp till 20 gånger snabbare beräkning av beräknade entiteter när du arbetar med storskaliga datavolymer. **Du måste starta om kapaciteten för att aktivera den nya motorn.** Mer information finns i [Förbättrad beräkningsmotor för dataflöden.](#enhanced-dataflows-compute-engine) |
| **Containerstorlek** | Den maximala storleken på den container som dataflöden använder för varje entitet i dataflödet. Standardvärdet är 700 MB. Mer information finns i [Containerstorlek](#container-size). |
|  |  |

#### <a name="enhanced-dataflows-compute-engine"></a>Förbättrad beräkningsmotor för dataflöden

Du kan använda den nya beräkningsmotorn till att dela upp datan i separata dataflöden och skicka omvandlingslogik till beräknade entiteter i olika dataflöden. Den här metoden rekommenderas eftersom beräkningsmotorn används på dataflöden som refererar till ett befintligt dataflöde. Den fungerar inte på inmatningsdataflöden. Genom att följa den här vägledningen säkerställer du att den nya beräkningsmotorn hanterar omvandlingssteg, till exempel kopplingar och sammanfogningar, för bästa prestanda.

#### <a name="container-size"></a>Containerstorlek

Vid uppdatering av ett dataflöde skapar dataflödesarbetsbelastningen en container för varje entitet i dataflödet. Varje container kan använda minne upp till den volym som anges i inställningen **Containerstorlek. Standardvärdet för alla SKU:er är 700 MB. Den här inställningen bör kanske ändras om:

- Dataflöden tar för lång tid att uppdateras eller om uppdatering av dataflöde misslyckas med överskriden tidsgräns.
- Dataflödesentiteter omfattar beräkningssteg, till exempel en koppling.  

Vi rekommenderar att du använder appen [Kapacitetsmått för Power BI Premium](service-admin-premium-monitor-capacity.md) för att analysera prestanda för dataflödesarbetsbelastning.

I vissa fall förbättras kanske inte prestandan av att containerstorleken ökas. Om dataflödet till exempel bara hämtar data från en källa utan att utföra betydande beräkningar hjälper det förmodligen inte att öka containerstorleken. Ökning av containerstorleken kan vara till hjälp om det gör att dataflödesarbetsbelastningen kan allokera mer minne för åtgärder för entitetsuppdatering. Genom att ha mer allokerat minne kan den tid det tar att uppdatera kraftigt beräknade entiteter minskas.

Värdet för Containerstorlek kan inte överskrida det maximala minnet för dataflödesarbetsbelastningen. Till exempel har en P1-kapacitet 25 GB minne. Om Maximalt minne för dataflödesarbetsbelastning (%) anges till 20 % kan Containerstorlek (MB) inte överstiga 5000. I samtliga fall kan containerstorleken inte överskrida Max minne, även om du anger ett högre värde.

### <a name="paginated-reports"></a>Sidnumrerade rapporter

Med arbetsbelastningens sidnumrerade rapporter kan du köra sidnumrerade rapporter, baserat på standardformatet för SQL Server Reporting Services i Power BI-tjänsten. Använd följande inställning för att styra arbetsbelastningsbeteendet.

| Inställningsnamn | Beskrivning |
|---------------------------------|----------------------------------------|
| **Maximalt minne (%)** | Den maximala procentandelen tillgängligt minne som sidnumrerade rapporter kan använda i en kapacitet. |
|  |  |

Sidnumrerade rapporter gör att anpassad kod kan köras vid rendering av en rapport. Det kan till exempel gälla dynamisk ändring av textfärg baserat på innehåll, vilket kan kräva ytterligare minne. I Power BI Premium körs sidnumrerade rapporter i ett inneslutet område inom kapaciteten. Det Max minne som anges används *oavsett huruvida* arbetsbelastningen är aktiv. Om du ändrar inställningen Max minne från standardvärdet ska du se till att ange det lågt nog så att det inte påverkar andra arbetsbelastningar negativt.

I vissa fall kan arbetsbelastningens sidnumrerade rapporter bli otillgängliga. I det här fallet visar arbetsbelastningen ett feltillstånd i administratörsportalen, och användarna ser överskridna tidsgränser vid rendering av rapporter. För att lösa det här problemet kan du inaktivera arbetsbelastningen och sedan aktivera den igen.

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