---
title: Dimensionering av lokal datagateway
description: Vägledning för dimensionering av den lokala datagatewayen.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: e1a24d8d15881bf8a1948d91758c7592f75ea7ac
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214202"
---
# <a name="on-premises-data-gateway-sizing"></a>Dimensionering av lokal datagateway

Den här artikeln riktar sig till Power BI-administratörer som behöver installera och hantera en [lokal datagateway](../connect-data/service-gateway-onprem.md).

Gatewayen krävs när Power BI behöver få åtkomst till data som inte är direkt tillgängliga via Internet. Den kan installeras på en lokal server eller en VM-baserad infrastruktur som en tjänst (IaaS).

## <a name="gateway-workloads"></a>Gateway-arbetsbelastningar

Den lokala datagatewayen stöder två arbetsbelastningar. Det är viktigt att du först förstår dessa arbetsbelastningar innan vi diskuterar gatewaydimensionering och rekommendationer.

### <a name="cached-data-workload"></a>Cachelagrad dataarbetsbelastning

Arbetsbelastningen _Cachelagrade data_ hämtar och transformerar källdata för inläsning till Power BI-datamängder. Den gör detta i tre steg:

1. **Anslutning**: Gatewayen ansluter till källdata
1. **Datahämtning och transformering**: Data hämtas och transformeras när så behövs. Närhelst det är möjligt skickar Power Query-kombinationsmotorn transformeringssteg till datakällan. Detta kallas _[frågedelegering](power-query-folding.md)_ . När det inte är möjligt måste transformeringarna göras av gatewayen. I det här fallet förbrukar gatewayen mer processor- och minnesresurser.
1. **Överföring**: Data överförs till Power BI-tjänsten – en tillförlitlig och snabb Internet-anslutning är viktig, särskilt för stora datavolymer

![Diagram med cachedata som visar hur den lokala datagatewayen ansluter till lokala källor.](media/gateway-onprem-sizing/gateway-onprem-workload-cached-data.png)

### <a name="live-connection-and-directquery-workloads"></a>Live-anslutning och DirectQuery-arbetsbelastningar

_Live-anslutningen och DirectQuery_-arbetsbelastningen fungerar huvudsakligen i genomgångsläge. Power BI-tjänsten skickar frågor och gatewayen svarar med frågeresultat. Frågeresultaten är vanligtvis små till storleken.

- Mer information om Live-anslutning finns i [Datamängder i Power BI-tjänsten (externt värdbaserade modeller)](../connect-data/service-datasets-understand.md#external-hosted-models).
- Mer information om varje DirectQuery finns i artikeln [Datamängdslägen i Power BI-tjänsten (DirectQuery-läge)](../connect-data/service-dataset-modes-understand.md#directquery-mode).

Den här arbetsbelastningen kräver CPU-resurser för routning av frågor och frågeresultat. Vanligtvis är CPU-efterfrågan betydligt mindre än vad som krävs av cachedataarbetsbelastningen, i synnerhet när den måste transformera data för cachelagring.

En tillförlitlig, snabb och konsekvent anslutning är viktig för att säkerställa att rapportanvändarna får dynamiska upplevelser.

![Diagram med Live-anslutning och DirectQuery som visar hur den lokala datagatewayen ansluter till lokala källor.](media/gateway-onprem-sizing/gateway-onprem-workload-liveconnection-directquery.png)

## <a name="sizing-considerations"></a>Överväganden för dimensionering

Att fastställa rätt dimensionering för din gatewaydator kan bero på följande variabler:

- För cachedataarbetsbelastningar:
  - Antalet uppdateringar av samtidiga datamängder
  - Typer av datakällor (relationsdatabas, analysdatabas, dataflöden eller filer)
  - Den mängd data som ska hämtas från datakällor
  - Alla transformeringar som krävs av Power Query-kombinationsmotorn
  - Den mängd data som ska överföras till Power BI-tjänsten
- För live-anslutning och DirectQuery-arbetsbelastningar:
  - Antal samtidiga rapportanvändare
  - Antalet visuella objekt på rapportsidor (varje visuellt objekt skickar minst en fråga)
  - Frekvensen för uppdateringar av Power BI-instrumentpanelens frågecache
  - Antalet rapporter i realtid som använder funktionen [Automatisk siduppdatering](../create-reports/desktop-automatic-page-refresh.md)
  - Huruvida datamängder ska tvinga [säkerhet på radnivå (RLS)](../create-reports/desktop-rls.md) eller inte

Vanligtvis är CPU-kapaciteten tillräcklig för live-anslutning och DirectQuery-arbetsbelastningar, medan cachedataarbetsbelastningar kräver mer CPU-kraft och minne. Båda arbetsbelastningarna beror på en lämplig anslutning till Power BI-tjänsten och datakällorna.

> [!NOTE]
> Power BI-kapaciteterna begränsar modelluppdateringsparallellitet och dataflödet för live-anslutning och DirectQuery. Det finns ingen mening med att dimensionera dina gatewayar till mer än vad Power BI-tjänsten stöder. Gränserna skiljer sig från Premium-SKU:n (och lika stora A-SKU:n). Mer information finns i [Vad är Power BI Premium? (Kapacitetsnoder)](../admin/service-premium-what-is.md#capacity-nodes).

## <a name="recommendations"></a>Rekommendationer

Rekommendationerna för gatewaydimensionering beror på flera variabler. I det här avsnittet får du allmänna rekommendationer att överväga.

### <a name="initial-sizing"></a>Ursprunglig dimensionering

Det kan vara svårt att bedöma rätt storlek korrekt. Vi rekommenderar att du börjar med en dator med minst 8 CPU-kärnor, 8 GB RAM-minne och flera Gigabit-nätverkskort. Du kan sedan mäta en typisk gatewayarbetsbelastning genom att logga CPU- och minnessystemsräknare. Mer information finns i [Övervaka och optimera lokala datagatewayprestanda](/data-integration/gateway/service-gateway-performance).

### <a name="connectivity"></a>Anslutning

Planera för bästa möjliga anslutning mellan Power BI-tjänsten och din gateway, och mellan din gateway och datakällorna.

- Sträva efter tillförlitlighet, snabba hastigheter och låga konsekventa fördröjningar
- Eliminera – eller minska – datorhopp mellan gatewayen och dina datakällor
- Ta bort eventuella nätverksbegränsningar som införts av brandväggsproxyns lager. Mer information om Power BI-slutpunkter finns i [Lägg till Power BI-URL:er till listan över tillåtna](../admin/power-bi-whitelist-urls.md).
- Konfigurera [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) för att upprätta en privat, hanterad anslutning till Power BI
- När det gäller datakällor på virtuella Azure-datorer, så se till att de virtuella datorerna [samplaceras med Power BI-tjänsten](../admin/service-admin-where-is-my-tenant-located.md)
- När det gäller de live-anslutningsarbetsbelastningar till SQL Server Analysis Services (SSAS) som involverar dynamisk RLS, så säkerställ en lämplig anslutning mellan gatewaydatorn och Active Directory lokalt

### <a name="clustering"></a>Klustring

När det gäller storskaliga distributioner kan du skapa en gateway för klusterinstallationer. Kluster undviker enskilda felpunkter, och kan belastningsutjämna trafik mellan gatewayer. Du kan:

- Installera en eller flera gatewayar i ett kluster
- Isolera arbetsbelastningar till fristående gatewayar eller gatewayserverkluster

Mer information finns i [Hantera lokala datagatewaykluster med hög tillgänglighet och belastningsutjämning](/data-integration/gateway/service-gateway-high-availability-clusters).

### <a name="dataset-design-and-settings"></a>Datamängdsdesign och inställningar

Datamängdsdesignen och dess inställningar kan påverka gatewayarbetsbelastningar. Du kan minska gatewayarbetsbelastningen med hjälp av följande åtgärder.

För importdatamängder:

- Konfigurera mindre frekvent uppdatering av data
- Konfigurera [stegvis uppdatering](../admin/service-premium-incremental-refresh.md) så att mängden data som överförs minimeras
- Närhelst det är möjligt bör du se till att [frågedelegering](power-query-folding.md) äger rum
- I synnerhet när det gäller stora datavolymer, eller då det finns behov av resultat med låg latens, så konvertera designen till en DirectQuery-modell eller en [sammansatt](../connect-data/service-dataset-modes-understand.md#composite-mode) modell

För DirectQuery-datamängder:

- Optimera datakällor, modell och rapportdesign. Mer information finns i [DirectQuery-modellvägledning i Power BI Desktop](directquery-model-guidance.md)
- Skapa [aggregeringar](../transform-model/desktop-aggregations.md) om du vill cachelagra högnivåresultat och därmed minska antalet DirectQuery-begäranden
- Begränsa intervallerna för [automatisk siduppdatering](../create-reports/desktop-automatic-page-refresh.md) i rapportdesigner och kapacitetsinställningar
- I synnerhet när dynamisk RLS tillämpas, bör du begränsa uppdateringsfrekvensen för instrumentpanelens cache
- I synnerhet när det gäller mindre datavolymer eller beständiga data, så konvertera designen till en importmodell eller en [sammansatt](../connect-data/service-dataset-modes-understand.md#composite-mode) modell

För live-anslutningsdatamängder:

- I synnerhet när dynamisk RLS tillämpas, bör du begränsa uppdateringsfrekvensen för instrumentpanelens cache

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Vägledning för distribution av en datagateway för Power BI](../connect-data/service-gateway-deployment-guidance.md)
- [Konfigurera proxyinställningar för den lokala datagatewayen](/data-integration/gateway/service-gateway-proxy)
- [Övervaka och optimera lokala datagatewayprestanda](/data-integration/gateway/service-gateway-performance)
- [Felsöka gatewayer – Power BI](../connect-data/service-gateway-onprem-tshoot.md)
- [Felsöka den lokala datagatewayen](/data-integration/gateway/service-gateway-tshoot)
- [Vikten av frågedelegering](power-query-folding.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com)
