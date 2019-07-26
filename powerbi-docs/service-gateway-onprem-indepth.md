---
title: Lokal datagateway – på djupet
description: Den här artikeln ger en djupgående beskrivning av den lokala gatewayen. Här beskrivs hur tjänsten fungerar med Azure Active Directory och ditt lokala Active Directory när du arbetar med Analysis Services
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: de3400989e6d8fe62c03d6b21707559fac0fd7bf
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271447"
---
# <a name="on-premises-data-gateway-in-depth"></a>Lokal datagateway – på djupet

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

Vi har flyttat informationen från den här artikeln till flera artiklar i Power BI och allmänna dokument. Följ länkarna under varje rubrik för att hitta relevant innehåll.

## <a name="how-the-gateway-works"></a>Så här fungerar gatewayen

Se [Arkitektur för lokal datagateway](/data-integration/gateway/service-gateway-onprem-indepth).

## <a name="list-of-available-data-source-types"></a>Lista över tillgängliga typer av datakällor

Se [Hantera datakällor](service-gateway-data-sources.md).

## <a name="authentication-to-on-premises-data-sources"></a>Autentisering till lokala datakällor

Se [Autentisering till lokala datakällor](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources).

## <a name="authentication-to-a-live-analysis-services-data-source"></a>Autentisering till en levande Analysis Services-datakälla

Se [Autentisering till en levande Analysis Services-datakälla](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source).

## <a name="role-based-security"></a>Rollbaserad säkerhet

Se [Rollbaserad säkerhet](service-gateway-enterprise-manage-ssas.md#role-based-security).

## <a name="row-level-security"></a>Säkerhet på radnivå

Se [Säkerhet på radnivå](service-gateway-enterprise-manage-ssas.md#row-level-security).

## <a name="what-about-azure-active-directory"></a>Vad är Azure Active Directory?

Se [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory).

## <a name="how-do-i-tell-what-my-upn-is"></a>Hur vet jag vilken UPN jag har?

Se [Hur vet jag vilken UPN jag har?](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is).

## <a name="mapping-usernames-for-analysis-services-data-sources"></a>Mappa användarnamn för Analysis Services-datakällor

Se [Mappa användarnamn för Analysis Services-datakällor](service-gateway-enterprise-manage-ssas.md#mapping-usernames-for-analysis-services-data-sources).

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>Synkronisera ett lokalt Active Directory med Azure Active Directory

Se [Synkronisera ett lokalt Active Directory med Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory).

## <a name="what-to-do-next"></a>Vad är nästa steg?

Se artiklarna om datakällor:

[Hantera datakällor](service-gateway-data-sources.md)
[Hantera din datakälla – Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[Hantera din datakälla – SAP HANA](service-gateway-enterprise-manage-sap.md)  
[Hantera din datakälla – SQL Server](service-gateway-enterprise-manage-sql.md)  
[Hantera din datakälla – Oracle](service-gateway-onprem-manage-oracle.md)  
[Hantera din datakälla – Import/schemalagd uppdatering](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>Var saker kan gå fel

Se [Felsöka den lokala datagatewayen](/data-integration/gateway/service-gateway-tshoot) och [Felsöka gatewayer – Power BI](service-gateway-onprem-tshoot.md).

## <a name="sign-in-account"></a>Inloggningskonto

Se [Inloggningskonto](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account).

## <a name="windows-service-account"></a>Windows-tjänstkonto

Se [Ändra det lokala tjänstkontot för datagatewayen](/data-integration/gateway/service-gateway-service-account).

## <a name="ports"></a>Portar

Se [Portar](/data-integration/gateway/service-gateway-communication#ports).

## <a name="forcing-https-communication-with-azure-service-bus"></a>Tvinga HTTPS-kommunikation med Azure Service Bus

Se [Tvinga HTTPS-kommunikation med Azure Service Bus](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus).

## <a name="support-for-tls-12"></a>Stöd för TLS 1.2

Se [TLS 1.2 för gatewaytrafik](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic).

## <a name="how-to-restart-the-gateway"></a>Starta om gatewayen

Se [Starta om en gateway](/data-integration/gateway/service-gateway-restart).

## <a name="next-steps"></a>Nästa steg

[Vad är den lokala datagatewayen?](service-gateway-onprem.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)