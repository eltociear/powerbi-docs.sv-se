---
title: Så här konfigurerar du arbetsbelastningar i Power BI Premium
description: Lär dig att konfigurera arbetsbelastningar i en Power BI Premium-kapacitet.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/14/2019
LocalizationGroup: Premium
ms.openlocfilehash: 7d94c5d3531576cd36688591b55aaf4a49de51aa
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831304"
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

Som standard är datamängdernas arbetsbelastning aktiverad och kan inte inaktiveras. Använd nedanstående inställningar för att styra arbetsbelastningsbeteendet. Det finns ytterligare användningsinformation under tabellen för några av inställningarna.

| Inställningsnamn | Beskrivning |
|---------------------------------|----------------------------------------|
| **Maximalt minne (%)** | Den maximala procentandelen tillgängligt minne som datamängder kan använda i en kapacitet. |
| **XMLA-slutpunkt** | Anger att anslutningar från klientprogram följer medlemsuppsättningen för säkerhetsgrupper på nivåerna för arbetsyta och app. Mer information finns i [Ansluta till datamängder med klientprogram och verktyg](service-premium-connect-tools.md). |
| **Maximalt antal mellanliggande raduppsättningar** | Det maximala antalet mellanliggande rader som returneras av DirectQuery. Standardvärdet är 1 000 000 och det tillåtna intervallet är mellan 100 000 och 2 147 483 647. |
| **Maximal storlek för offlinedatamängd (GB)** | Maximal storlek för offlinedatamängden i minnet. Detta är den komprimerade storleken på disken. Standardvärdet anges av SKU:n och det tillåtna intervallet är 0,1–10 GB. |
| **Maximalt antal resultatraduppsättningar** | Det maximala antalet rader som returneras i en DAX-fråga. Standardvärdet är -1 (ingen gräns) och det tillåtna intervallet är mellan 100 000 och 2 147 483 647. |
| **Minnesgräns för frågor (%)** | Den maximala procentandelen tillgängligt minne som kan användas för tillfälliga resultat i en fråga eller ett DAX-mått. |
| **Tidsgräns för frågor (sekunder)** | Maximal tid innan tidsgränsen för frågan uppnås. Standardvärdet är 3 600 sekunder (en timme). Värdet 0 anger att frågorna inte har någon tidsgräns. |
| **Automatisk siduppdatering (förhandsversion)** | På/av växlar funktionen för automatisk siduppdatering i Premium-arbetsytor. |
| **Minsta uppdateringsintervall** | Om automatisk siduppdatering är aktiverat, är detta det minsta intervall som tillåts för siduppdatering. Standardvärdet är fem minuter och det lägsta tillåtna värdet är en sekund. |
|  |  |  |

#### <a name="max-intermediate-row-set-count"></a>Maximalt antal mellanliggande raduppsättningar

Använd inställningen för att styra påverkan från resursintensiva eller bristfälligt utformade rapporter. Om en fråga till en DirectQuery-datauppsättning resulterar i ett mycket stort resultat från källdatabasen kan det uppstå en topp i minnes- och processoranvändningen. Det kan göra att andra användare och rapporter får brist på resurser. Med den här inställningen kan kapacitetsadministratören justera hur många rader en enskild fråga kan hämta från datakällan.

Om kapaciteten har stöd för mer än standardinställningen på 1 000 000 rader, och du har en stor datauppsättning, kan du öka den här inställningen om du vill hämta fler rader.

Observera att den här inställningen endast påverkar DirectQuery-frågor, medan [Maximalt antal resultatraduppsättningar](#max-result-row-set-count) påverkar DAX -frågor.

#### <a name="max-offline-dataset-size"></a>Maxstorlek för offlinedatamängd

Använd inställningen till att förhindra att rapportskapare publicerar en stor datamängd som kan påverka kapaciteten negativt. Observera att Power BI inte kan fastställa den faktiska minnesstorleken förrän datauppsättningen har lästs in i minnet. Det är möjligt att en datauppsättning med en mindre offlinestorlek kan ha ett större fotavtryck för minnesanvändning än en datauppsättning med en större offlinestorlek.

Om du har en befintlig datauppsättning som är större än den storlek som du angett för den här inställningen går det inte att läsa in datauppsättningen när användaren försöker komma åt den.

#### <a name="max-result-row-set-count"></a>Maximalt antal resultatraduppsättningar

Använd inställningen för att styra påverkan från resursintensiva eller bristfälligt utformade rapporter. Om den här gränsen nås i en DAX-fråga visas följande fel för rapportanvändare. De bör kopiera felinformationen och kontakta en administratör.

![Det gick inte att läsa in data för det här visuellt objektet](media/service-admin-premium-workloads/could-not-load-data.png)

Observera att den här inställningen endast påverkar DAX-frågor, medan [Maximalt antal mellanliggande raduppsättningar](#max-intermediate-row-set-count) påverkar DirectQuery-frågor.

#### <a name="query-memory-limit"></a>Minnesgräns för frågor

Använd inställningen för att styra påverkan från resursintensiva eller bristfälligt utformade rapporter. Vissa frågor och beräkningar kan resultera i mellanliggande resultat som använder mycket minne i kapaciteten. Det kan göra att andra frågor körs mycket långsamt, att andra datauppsättningar tas bort från kapaciteten och att det uppstår minnesfel för andra som använder kapaciteten.

Den här inställningen gäller för datauppdatering och rapportåtergivning. Vid datauppdateringen utförs både uppdatering av data från datakällan och uppdatering av frågan, om inte frågeuppdateringen är inaktiverad. Om frågeuppdatering inte är inaktiverad gäller den här minnesgränsen även för dessa frågor. Eventuella misslyckade frågor gör att tillståndet för den schemalagda uppdateringen rapporteras som ett fel, även om det gick att utföra datauppdateringen.

#### <a name="query-timeout"></a>Tidsgräns för frågor

Använd den här inställningen om du vill ha bättre kontroll över långvariga frågor, som kan göra att rapporter läses in långsamt för användarna. Den här inställningen gäller för datauppdatering och rapportåtergivning. Vid datauppdateringen utförs både uppdatering av data från datakällan och uppdatering av frågan, om inte frågeuppdateringen är inaktiverad. Om frågeuppdateringen inte är inaktiverad gäller den här minnesgränsen även för dessa frågor.

Den här inställningen gäller för en enskild fråga och inte den tid det tar att köra alla frågor som är kopplade till uppdateringen av en datauppsättning eller rapport. Se följande exempel:

- **Tidsgräns för frågor** är inställd på 1200 (20 minuter).
- Det finns fem frågor och var och en tar 15 minuter att köra.

Den sammanlagda tiden för alla frågor är 75 minuter, men den inställda tidsgränsen har inte nåtts eftersom alla enskilda frågor tar mindre än 20 minuter att köra.

Observera att för Power BI-rapporter åsidosätts detta standardvärde med en mycket lägre tidsgräns för varje fråga till kapaciteten. Normalt är tidsgränsen för varje fråga ungefär tre minuter.

#### <a name="automatic-page-refresh-preview"></a>Automatisk siduppdatering (förhandsversion)

När den här inställningen är aktiverad kan användare i Premium-kapaciteten uppdatera sidor i rapporten till DirectQuery-källor med hjälp av automatisk siduppdatering. Som kapacitetsadministratör kan du göra följande:

1.  Aktivera och inaktivera automatisk siduppdatering
2.  Definiera ett minsta uppdateringsintervall

Följande bild visar platsen för inställningen av automatiskt uppdateringsintervall:

![administratörsinställning av automatiskt uppdateringsintervall](media/service-admin-premium-workloads/automatic-refresh-interval.png)

Frågor som har skapats vid automatisk siduppdatering skickas direkt till datakällan, så det är viktigt att tänka på tillförlitligheten och belastningen på dessa källor när du tillåter automatisk siduppdatering i din organisation. 

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

Sidnumrerade rapporter gör att anpassad kod kan köras vid rendering av en rapport. Det kan till exempel gälla dynamisk ändring av textfärg baserat på innehåll, vilket kan kräva ytterligare minne. I Power BI Premium körs sidnumrerade rapporter i ett inneslutet område inom kapaciteten. 

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
[Automatisk siduppdatering i Power BI Desktop (förhandsversion)](desktop-automatic-page-refresh.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
