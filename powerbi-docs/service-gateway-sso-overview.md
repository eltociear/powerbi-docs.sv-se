---
title: Använda enkel inloggning (SSO) till lokala datakällor
description: Konfigurera din gateway för att aktivera enkel inloggning (SSO) från Power BI till lokala datakällor.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: b1379bb783b090362215eaf7c317bbea435d1eec
ms.sourcegitcommit: e533c65607bbba0f620fddabd6b107e5933772c1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/11/2019
ms.locfileid: "72259925"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Översikt över enkel inloggning (SSO) för gatewayer i Power BI

Du kan få en sömlös enkel inloggningsanslutning, vilket medför att Power BI-rapporter och -instrumentpaneler kan uppdateras i realtid från lokala data, genom att konfigurera din lokala datagateway med antingen Kerberos eller Security Assertion Markup Language (SAML). Den lokala datagatewayen stöder enkel inloggning med hjälp av DirectQuery, som används för att ansluta till lokala datakällor.

Vi stöder för närvarande följande datakällor:

* SQL Server ([Kerberos](service-gateway-sso-kerberos.md))
* SAP HANA ([Kerberos](service-gateway-sso-kerberos.md) och [SAML](service-gateway-sso-saml.md))
* SAP BW-programserver ([Kerberos](service-gateway-sso-kerberos.md))
* SAP BW-meddelandeserver ([Kerberos](service-gateway-sso-kerberos.md)) – Allmänt tillgänglig förhandsversion
* Oracle ([Kerberos](service-gateway-sso-kerberos.md)) – Allmänt tillgänglig förhandsversion
* Teradata ([Kerberos](service-gateway-sso-kerberos.md))
* Spark ([Kerberos](service-gateway-sso-kerberos.md))
* Impala ([Kerberos](service-gateway-sso-kerberos.md))

Vi stöder för närvarande inte enkel inloggning för [M-tillägg](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

När en användare interagerar med en DirectQuery-rapport i Power BI-tjänsten, kan varje åtgärd relaterad till korsfiltrering, sektor, sortering och rapportredigering resultera i frågor som körs i realtid mot den underliggande lokala datakällan. När enkel inloggning har konfigurerats för datakällan körs frågorna under identiteten för den användare som interagerar med Power BI (det vill säga via webbläsaren eller Power BI Mobile-appar). Därmed ser varje användare exakt de data som han eller hon har behörighet för i den underliggande datakällan – med enkel inloggning konfigurerad finns det ingen delad datacachelagring för olika användare.

## <a name="query-steps-when-running-sso"></a>Frågesteg vid körning av enkel inloggning

En fråga som körs med SSO (enkel inloggning) består av tre steg, vilket visas i följande diagram.

![Frågesteg med enkel inloggning](media/service-gateway-sso-overview/sso-query-steps.png)

Här finns mer information om de här stegen:

1. För varje fråga inkluderar **Power BI-tjänsten** *användarens huvudnamn* (UPN, dvs. det fullständiga kvalificerade namnet för användaren som för närvarande är inloggad i Power BI-tjänsten) när en frågebegäran skickas till den konfigurerade gatewayen.

2. Gatewayen måste mappa Microsoft Azure Active Directorys UPN till en lokal Active Directory-identitet.

   a.  Om Azure AD DirSync (även kallat *Azure AD Connect*) har konfigurerats fungerar mappningen automatiskt i gatewayen.

   b.  I annat fall kan gatewayen söka upp och mappa Microsoft Azure AD UPN:en till en lokal AD-användare genom att utföra en sökning mot den lokala Active Directory-domänen.

3. Gatewaytjänstprocessen personifierar den mappade lokala användaren, öppnar anslutningen till den underliggande databasen och skickar frågan. Gatewayen måste inte vara installerad på samma dator som databasen.

## <a name="next-steps"></a>Nästa steg

Nu när du förstår grunderna för enkel inloggning via gatewayen kan du läsa mer detaljerad information om Kerberos och SAML:

* [Enkel inloggning (SSO) – Kerberos](service-gateway-sso-kerberos.md)
* [Enkel inloggning (SSO) – SAML](service-gateway-sso-saml.md)
