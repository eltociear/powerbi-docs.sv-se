---
title: Vägledning för distribution av en datagateway för Power BI
description: Läs om bästa praxis och överväganden för distribution av en gateway för Power BI.
author: arthiriyer
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: arthii
LocalizationGroup: Gateways
ms.openlocfilehash: a9d30d1346bf2801cd6cba44cc7cc33d734fccbb
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699577"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Vägledning för distribution av en datagateway för Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Den här artikeln innehåller vägledning och överväganden för distribution av en datagateway för Power BI i din nätverksmiljö.

Information om hur du laddar ned, installerar, konfigurerar och hanterar den lokala datagatewayen finns i [Vad är en lokal datagateway?](/data-integration/gateway/service-gateway-onprem). Du kan även få mer information om den lokala datagatewayen och Power BI genom att gå till [Microsoft Power-bloggen](https://powerbi.microsoft.com/blog/) och webbplatsen för [Microsoft Power BI-communityn](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Installationsöverväganden för lokal datagateway

Innan du installerar den lokala datagatewayen för Power BI-molntjänsten finns det några överväganden som du bör ha i åtanke. I följande avsnitt beskrivs dessa överväganden.

### <a name="number-of-users"></a>Antal användare

Antalet användare som använder en rapport som använder gatewayen är ett viktigt mått när du bestämmer var du vill installera gatewayen. Här följer några saker att tänka på:

* Använder användarna dessa rapporter vid olika tidpunkter på dagen?
* Vilka sorts anslutningar använder de (DirectQuery eller Importera)?
* Använder alla användare samma rapport?

Om alla användare använder en viss rapport vid samma tidpunkt varje dag, ser du till att installera gatewayen på en dator som klarar av att hantera alla dessa begäranden. I följande avsnitt finns prestandaräknare och minimikrav som kan hjälpa dig att avgöra om en dator är tillräcklig.

I Power BI finns en begränsning som gör att du endast kan ha *en* gateway per *rapport*. Även om en rapport baseras på flera datakällor måste alla sådana datakällor gå igenom en enda gateway. Om en instrumentpanel har *flera* rapporter kan du använda en dedikerad gateway för varje rapport. På så sätt distribuerar du gateway-belastningen över flera rapporter som bidrar till den enskilda instrumentpanelen.

### <a name="connection-type"></a>Anslutningstyp

Power BI har två typer av anslutningar: DirectQuery och Importera. Alla datakällor stöder inte båda anslutningstyperna. Många faktorer kan påverka vilken typ du ska välja, till exempel säkerhetskrav, prestanda, datagränser och datamodellens storlek. Mer information om anslutningstyper och datakällor som stöds finns i [listan med tillgängliga typer av datakällor](service-gateway-data-sources.md#list-of-available-data-source-types).

Beroende på vilken typ av anslutning som används kan gateway-användningen variera. Försök till exempel att separera DirectQuery-datakällor från datakällor med schemalagd uppdatering när det är möjligt. Det förutsätter att de finns i olika rapporter och kan separeras. Genom att separera källorna kan du undvika att gatewayen får tusentals DirectQuery-förfrågningar i kö samtidigt som morgonens schemalagda uppdatering av en storskalig datamodell som används för företagets huvudinstrumentpanel. 

Tänk på följande för varje alternativ:

* **Schemalagd uppdatering**: Beroende på storleken på din fråga och antalet uppdateringar som utförs per dag, kan du välja att behålla de rekommenderade minimikraven för maskinvara eller uppgradera till en dator med bättre prestanda. Om en specifik fråga inte är vikt sker omvandlingarna på gatewaydatorn. Det gör att gatewaydatorn får mer tillgängligt RAM-minne.

* **DirectQuery**: En fråga skickas varje gång en användare öppnar rapporten eller tittar på data. Så om du tror att mer än 1 000 användare ska använda data samtidigt måste datorn ha tåliga och högpresterande maskinvarukomponenter. Flera processorkärnor resulterar i bättre genomströmning för en DirectQuery-anslutning.

Mer information om installationskrav finns i [installationskraven](/data-integration/gateway/service-gateway-install#requirements) för den lokala datagatewayen.

### <a name="location"></a>Plats

Gatewayinstallationens plats kan ha stor inverkan på frågeprestanda. Se till att din gateway, platsen för datakällorna och Power BI-klienten är så nära varandra som möjligt för att minimera nätverksfördröjningen. Välj ikonen **?** i det övre högre hörnet Power BI-tjänsten för att fastställa platsen för din Power BI-klient . Välj sedan **Om Power BI**.

![Fastställa platsen för din Power BI-klientorganisation](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Om du tänker använda Power BI-gatewayen med Azure Analysis Services ska du se till att dataområdena i båda två matchar. Titta på [den här videon](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/) om du vill ha mer information om hur du anger dataområden för flera tjänster.

## <a name="next-steps"></a>Nästa steg

* [Konfigurera proxyinställningar](/data-integration/gateway/service-gateway-proxy)  
* [Felsöka gatewayer – Power BI](service-gateway-onprem-tshoot.md)  
* [Vanliga frågor och svar om lokal datagateway – Power BI](service-gateway-power-bi-faq.md)  

Har du fler frågor? Testa [Power BI Community](https://community.powerbi.com/).

