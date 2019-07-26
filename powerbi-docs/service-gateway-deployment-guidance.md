---
title: Vägledning för distribution av en datagateway för Power BI
description: Läs om bästa praxis och överväganden för distribution av en gateway för Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 4351804330982b32582c4c782ef7c2fa0e92f197
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271708"
---
# <a name="guidance-for-deploying-a-data-gateway-for-power-bi"></a>Vägledning för distribution av en datagateway för Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Den här artikeln innehåller vägledning och överväganden för distribution av en datagateway för Power BI i din nätverksmiljö.

Information om hur du laddar ned, installerar, konfigurerar och hanterar den lokala datagatewayen finns i [Vad är en lokal datagateway](/data-integration/gateway/service-gateway-onprem). Du kan även få mer information om den lokala datagatewayen och Power BI genom att gå till [Microsoft Power-bloggen](https://powerbi.microsoft.com/blog/) och webbplatsen för [Microsoft Power BI-communityn](https://community.powerbi.com/).

## <a name="installation-considerations-for-the-on-premises-data-gateway"></a>Installationsöverväganden för lokal datagateway

Innan du installerar den lokala datagatewayen för Power BI-molntjänsten finns det några överväganden som du bör ha i åtanke. I följande avsnitt beskrivs dessa överväganden.

### <a name="number-of-users"></a>Antal användare

Antalet användare som använder en rapport som använder gatewayen är ett viktigt mått när du bestämmer var du vill installera gatewayen. Här följer några saker att tänka på:

* Använder användarna dessa rapporter vid olika tidpunkter på dagen?
* Vilka sorts anslutningar använder de (DirectQuery eller Importera)?
* Använder alla användare samma rapport?

Om alla användare kommer åt en viss rapport samma tid varje dag bör du installera gatewayen på en dator som kan hantera alla sådana begäranden (se följande avsnitt för prestandaräknare och minimikrav som kan hjälpa dig att fastställa detta).

Det finns en begränsning i **Power BI** som endast tillåter *en* gateway per *rapport*, så även om en rapport är baserad på flera datakällor måste alla dessa datakällor gå via samma gateway. Men om en instrumentpanel baseras på *flera* rapporter kan du använda en dedikerad gateway för varje bidragande rapport och därmed distribuera gateway-belastningen på flera rapporter som bidrar till en enda instrumentpanel.

### <a name="connection-type"></a>Anslutningstyp

**Power BI** har två typer av anslutningar: **DirectQuery** och **Importera**. Alla datakällor stöder inte båda anslutningstyper och det kan finnas många anledningar till att välja den ena över den andra, till exempel säkerhetskrav, prestanda, databegränsningar och storleken på datamodellen. Du kan lära dig mer om anslutningstyper och datakällor som stöds i avsnittet [lista med tillgängliga typer av datakällor](service-gateway-data-sources.md#list-of-available-data-source-types).

Beroende på vilken typ av anslutning som används kan gateway-användningen variera. Du bör till exempel försöka skilja **DirectQuery**-datakällor från datakällor med **Schemalagd uppdatering** när det är möjligt (förutsatt att de är i olika rapporter och kan delas upp). Därmed kommer gatewayen inte att ha tusentals DirectQuery-begäranden i kö vid samma tid som morgonens schemalagda uppdatering av en storskalig datamodell som används för företagets huvudinstrumentpanel. Tänk på följande för varje:

* För **Schemalagd uppdatering**: beroende på storleken på din fråga och antalet uppdateringar som utförs per dag, räcker det att vara inom de rekommenderade minimikraven för maskinvara eller uppgradera till en dator med bättre prestanda. Om en given fråga inte är vikt utförs omvandlingar på gatewaydatorn och därmed är det bra om gatewaydatorn har mer tillgängligt minne.

* För **DirectQuery**: en fråga skickas varje gång en användare öppnar rapporten eller tittar på data. Så om du tror att mer än 1 000 användare har åtkomst till data samtidigt måste datorn ha tåliga och högpresterande maskinvarukomponenter. Flera processorkärnor resulterar i bättre genomströmning för en **DirectQuery**-anslutning.

Kraven för den dator där du installerar finns i [installationskraven](/data-integration/gateway/service-gateway-install#requirements) för lokal datagateway.

### <a name="location"></a>Plats

Platsen för gatewayinstallationen kan ha stor inverkan på hur din fråga presterar. Kontrollera att din gateway, dina datakällor och Power BI-klienten befinner sig så nära varandra som möjligt för att minimera nätverksfördröjningen. Välj ikonen **?** i det övre högre hörnet Power BI-tjänsten för att fastställa platsen för din Power BI-klient och välj sedan **Om Power BI**.

![Fastställa platsen för din Power BI-klientorganisation](media/service-gateway-deployment-guidance/powerbi-gateway-deployment-guidance_02.png)

Om du tänker använda Power BI-gatewayen med Azure Analysis Services ska du även se till att dataområdena i båda två matchar. Titta på [den här videon](https://guyinacube.com/2018/01/power-bi-azure-analysis-services-gateway-data-region/) om du vill ha mer information om hur du anger dataområden för flera tjänster.

## <a name="next-steps"></a>Nästa steg

* [Konfigurera proxyinställningar](/data-integration/gateway/service-gateway-proxy)  
* [Felsöka gatewayer – Power BI](service-gateway-onprem-tshoot.md)  
* [Vanliga frågor och svar om lokal datagateway – Power BI](service-gateway-power-bi-faq.md)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

