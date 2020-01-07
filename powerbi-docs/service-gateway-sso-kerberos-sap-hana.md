---
title: Använda Kerberos för enkel inloggning (SSO) till SAP HANA
description: Konfigurera din SAP HANA-server till att aktivera enkel inloggning från Power BI-tjänsten
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 9c2eb554a4e3b3ec90d3fe17145e0ec277298e1b
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2020
ms.locfileid: "74697507"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Använda Kerberos för enkel inloggning (SSO) till SAP HANA

I den här artikeln beskrivs hur du konfigurerar din SAP HANA-datakälla för att aktivera enkel inloggning från Power BI-tjänsten.

> [!NOTE]
> Innan du försöker uppdatera en SAP HANA-baserad rapport som använder enkel inloggning med Kerberos ska du slutföra både stegen i den här artikeln och stegen i [Konfigurera enkel inloggning med Kerberos](service-gateway-sso-kerberos.md).

## <a name="enable-sso-for-sap-hana"></a>Aktivera enkel inloggning för SAP HANA

För att aktivera enkel inloggning för SAP HANA följer du de här stegen:

1. Kontrollera att SAP HANA-servern har den lägsta version som krävs, vilket beror på nivån för SAP HANA-serverplattformen:
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. Installera den senaste SAP HANA ODBC-drivrutinen på gatewaydatorn. Den lägsta möjliga versionen är HANA ODBC version 2.00.020.00 från augusti 2017.

3. Kontrollera att SAP HANA-servern har konfigurerats för Kerberos-baserad enkel inloggning. Mer information om hur du konfigurerar enkel inloggning för SAP HANA med hjälp av Kerberos finns i [Enkel inloggning med Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) i säkerhetsguiden för SAP HANA. Se även länkarna på sidan, särskilt SAP-kommentaren 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

Vi rekommenderar även att du utför dessa ytterligare steg som kan ge en liten prestandaförbättring:

1. Sök efter och öppna den här konfigurationsfilen i gatewayens installationskatalog: Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config.

2. Leta rätt på egenskapen `FullDomainResolutionEnabled` och ändra värdet till `True`.

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

[Kör nu en Power BI-rapport](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Nästa steg

Du kan läsa mer om den lokala datagatewayen och DirectQuery i de här resurserna:

* [Vad är en lokal datagateway?](/data-integration/gateway/service-gateway-onprem)
* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
