---
title: Använda Kerberos för enkel inloggning (SSO) till SAP HANA
description: Konfigurera din SAP HANA-server till att aktivera enkel inloggning från Power BI-tjänsten
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 4e94781b3a424e894e0f0e2209ec48efb25c5db5
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106318"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>Använda Kerberos för enkel inloggning (SSO) till SAP HANA

I den här artikeln beskrivs hur du konfigurerar din SAP HANA-server för att aktivera enkel inloggning från Power BI-tjänsten.

> [!NOTE]
> Slutför stegen i den här artikeln utöver stegen i [Konfigurera enkel inloggning med Kerberos](service-gateway-sso-kerberos.md) innan du försöker uppdatera en SAP HANA-baserad rapport som använder enkel inloggning med Kerberos.

## <a name="enable-sso-for-sap-hana"></a>Aktivera enkel inloggning för SAP HANA

För att aktivera enkel inloggning för SAP HANA följer du de här stegen:

* Kontrollera att SAP HANA-servern har den lägsta version som krävs, vilket beror på nivån för SAP HANA-serverplattformen:
  * [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
  * [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
  * [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)
* Installera SAP:s senaste HANA ODBC-drivrutin på gatewaydatorn.  Den lägsta möjliga versionen är HANA ODBC version 2.00.020.00 från augusti 2017.

Kontrollera att SAP HANA-servern har konfigurerats för Kerberos-baserad enkel inloggning. Mer information om hur du konfigurerar enkel inloggning för SAP HANA med hjälp av Kerberos finns i [Enkel inloggning med Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html) i säkerhetsguiden för SAP HANA. Se även länkarna på sidan, särskilt SAP-kommentaren 1837331 – HOWTO HANA DBSSO Kerberos/Active Directory.

Vi rekommenderar även att du följer dessa ytterligare steg, som kan ge en liten prestandaförbättring.

1. Sök efter och öppna den här konfigurationsfilen i gatewayens installationskatalog: *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*.

2. Leta upp egenskapen *FullDomainResolutionEnabled* och ändra dess värde till *True* (Sant).

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

[Kör nu en Power BI-rapport](service-gateway-sso-kerberos.md#run-a-power-bi-report).

## <a name="next-steps"></a>Nästa steg

Mer information om den **lokala datagatewayen** och **DirectQuery** finns i följande resurser:

* [Vad är en lokal datagateway?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
