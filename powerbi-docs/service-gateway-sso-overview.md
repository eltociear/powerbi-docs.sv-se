---
title: Översikt över enkel inloggning (SSO) för gatewayer i Power BI
description: Konfigurera din gateway för att aktivera enkel inloggning (SSO) från Power BI till lokala datakällor.
author: mgblythe
ms.author: mblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 43394e8f09327ebcb858ff5644b30daee1793444
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73872385"
---
# <a name="overview-of-single-sign-on-sso-for-gateways-in-power-bi"></a>Översikt över enkel inloggning (SSO) för gatewayer i Power BI

Du kan få en smidig anslutning med enkel inloggning så att rapporter och instrumentpaneler i Power BI kan uppdateras med lokala data i realtid, genom att du konfigurerar din lokala datagateway. Du kan välja att konfigurera din gateway med antingen [Kerberos](service-gateway-sso-kerberos.md)-begränsad delegering eller Security Assertion Markup Language ([SAML](service-gateway-sso-saml.md)). Den lokala datagatewayen har stöd för enkel inloggning med hjälp av [DirectQuery](desktop-directquery-about.md), som ansluter till lokala datakällor.

Power BI har stöd för följande datakällor:

* SQL Server (Kerberos)
* SAP HANA (Kerberos och SAML)
* SAP BW Application Server (Kerberos)
* SAP BW Message Server (Kerberos) – offentlig förhandsversion
* Oracle (Kerberos) – offentlig förhandsversion
* Teradata (Kerberos)
* Spark (Kerberos)
* Impala (Kerberos)

Enkel inloggnings stöds för närvarande inte för [M-tillägg](https://github.com/microsoft/DataConnectors/blob/master/docs/m-extensions.md).

När en användare interagerar med en DirectQuery-rapport i Power BI-tjänsten så kan varje åtgärd relaterad till korsfiltrering, utsnitt, sortering och rapportredigering resultera i frågor som körs i realtid mot den underliggande lokala datakällan. När du konfigurerar enkel inloggning för datakällan körs frågorna under identiteten för den användare som interagerar med Power BI (det vill säga via webbläsaren eller Power BI-mobilappen). Det innebär att alla användare ser precis de data från den underliggande datakällan som de har behörighet för. När enkel inloggning är konfigurerad delas ingen cachelagring av data mellan olika användare.

## <a name="query-steps-when-running-sso"></a>Frågesteg vid körning av enkel inloggning

En fråga som körs med SSO (enkel inloggning) består av tre steg, vilket visas i följande diagram.

![Frågesteg med enkel inloggning](media/service-gateway-sso-overview/sso-query-steps.png)

Här visas mer information om respektive steg:

1. För varje fråga inkluderar Power BI-tjänsten *användarens huvudnamn (UPN)* , som är det fullständiga kvalificerade namnet för användaren som för närvarande är inloggad i Power BI-tjänsten, när en frågebegäran skickas till den konfigurerade gatewayen.

2. Gatewayen måste mappa UPN-namnet i Microsoft Azure Active Directory till en lokal Active Directory-identitet:

   a. Om Azure AD DirSync (även kallat *Azure AD Connect*) har konfigurerats fungerar mappningen automatiskt i gatewayen.

   b.  I annat fall kan gatewayen söka upp och mappa Microsoft Azure AD UPN:en till en lokal AD-användare genom att utföra en sökning mot den lokala Active Directory-domänen.

3. Gatewaytjänstprocessen personifierar den mappade lokala användaren, öppnar anslutningen till den underliggande databasen och skickar sedan frågan. Du behöver inte installera gatewayen på samma dator som databasen.

## <a name="next-steps"></a>Nästa steg

Nu när du förstår grunderna angående att aktivera enkel inloggning via gatewayen kan du läsa mer detaljerad information om Kerberos och SAML:

* [Enkel inloggning (SSO) – Kerberos](service-gateway-sso-kerberos.md)
* [Enkel inloggning (SSO) – SAML](service-gateway-sso-saml.md)
