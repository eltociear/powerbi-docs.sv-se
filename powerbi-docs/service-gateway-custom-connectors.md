---
title: Använda anpassade dataanslutningar med den lokala datagatewayen
description: Du kan använda anpassade dataanslutningar med den lokala datagatewayen.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 074a8dd876e0612f87c220f9fb077b60b2b85c88
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271816"
---
# <a name="use-custom-data-connectors-with-the-on-premises-data-gateway"></a>Använda anpassade dataanslutningar med den lokala datagatewayen

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Med dataanslutningar för Power BI kan du ansluta till och komma åt data från ett program, en tjänst eller en datakälla. Du kan utveckla anpassade dataanslutningar och använda dem i Power BI Desktop.

Mer information om hur du skapar anpassade dataanslutningar för Power BI finns på [GitHub-sidan för Data Connector SDK](http://aka.ms/dataconnectors). Den här webbplatsen innehåller information och exempel för att komma igång med Power BI och Power Query.

När du skapar rapporter i Power BI Desktop som använder anpassade dataanslutningar kan du använda den lokala datagatewayen för att uppdatera dessa rapporter från Power BI-tjänsten.

## <a name="how-to-enable-and-use-this-capability"></a>Så aktiverar och använder du den här funktionen

När du installerar versionen av lokal datagateway från juli 2018 eller senare kan du se fliken **Anslutningar** i appen för lokal datagateway. Där finns ett alternativ för att välja en mapp varifrån anpassade dataanslutningar läses in. Välj en mapp som kan nås av den användare som kör gatewaytjänsten (som standard är det *NT SERVICE\PBIEgwService*). Gatewayen läser automatiskt in de filer med anpassade anslutningar som finns i mappen, och du ser dem i listan med dataanslutningar.

![Anpassad anslutning 1](media/service-gateway-custom-connectors/gateway-onprem-customconnector1.png)

Om du använder lokal datagateway (personligt läge) kan du i detta läge ladda upp Power BI-rapporten till Power BI-tjänsten och använda gatewayen för att uppdatera den.

För den lokala datagatewayen behöver du fortfarande skapa en datakälla för din anpassade anslutning. När du väljer gatewayklustret på sidan för gatewayinställningar i Power BI-tjänsten bör du se ett nytt alternativ som du kan använda för att tillåta användningen av anpassade anslutningar med klustret. För att det här alternativet ska vara tillgängligt måste uppdateringen för juli 2018 eller en senare uppdatering vara installerad på alla gatewayer i klustret. Välj alternativet för att tillåta användning av anpassade anslutningar med det här klustret.

![Anpassad anslutning 2](media/service-gateway-custom-connectors/gateway-onprem-customconnector2.png)

När det här alternativet är aktiverat visas dina anpassade anslutningar som tillgängliga datakällor som du kan skapa under gatewayklustret. När du har skapat en datakälla med hjälp av den nya anpassade anslutningen kan du uppdatera Power BI-rapporter med hjälp av den anpassade anslutningen i Power BI-tjänsten.

![Anpassad anslutning 3](media/service-gateway-custom-connectors/gateway-onprem-customconnector3.png)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

* Kontrollera att mappen som du skapar är tillgänglig för gatewaytjänsten som körs i bakgrunden. Normalt kan mappar under din användares Windows-mapp eller systemmappar inte nås. Appen för lokal datagateway visar ett meddelande om mappen inte kan nås (detta gäller inte för den personliga versionen av gatewayen)
* För att anpassade anslutningar ska fungera med den lokala datagatewayen måste de implementera ett ”TestConnection”-avsnitt i den anpassade anslutningens kod. Detta krävs inte när du använder anpassade anslutningar med Power BI Desktop. Det betyder att du kan ha en som fungerar med Desktop, men inte med gatewayen. Information om hur du implementerar ett TestConnection-avsnitt finns i [den här dokumentationen](https://github.com/Microsoft/DataConnectors/blob/master/docs/m-extensions.md#implementing-testconnection-for-gateway-support).

## <a name="next-steps"></a>Nästa steg

* [Hantera din datakälla – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
* [Hantera din datakälla – SAP HANA](service-gateway-enterprise-manage-sap.md)  
* [Hantera din datakälla – SQL Server](service-gateway-enterprise-manage-sql.md)  
* [Hantera din datakälla – Oracle](service-gateway-onprem-manage-oracle.md)  
* [Hantera din datakälla – Import/schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md)  

* [Konfigurera proxyinställningar för den lokala datagatewayen](/data-integration/gateway/service-gateway-proxy)  
* [Använda Kerberos för SSO (enkel inloggning) från Power BI till lokala datakällor](service-gateway-sso-kerberos.md)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
