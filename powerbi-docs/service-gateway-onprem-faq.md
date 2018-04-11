---
title: Vanliga frågor och svar om lokal datagateway
description: Det här är vanliga frågor och svar om lokal datagateway. Här samlar vi vanliga frågor om gateway.
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 152a5ffe0c209be7251bd4dd4e94cf1769c10d79
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2018
---
# <a name="on-premises-data-gateway-faq"></a>Vanliga frågor och svar om lokal datagateway
<!-- Shared FAQ shared Include -->
[!INCLUDE [gateway-onprem-faq-shared-include](./includes/gateway-onprem-faq-shared-include.md)]

## <a name="analysis-services"></a>Analysis Services
**Fråga:** Kan jag använda msdmpump.dll för att skapa anpassade effektiva användarnamnsmappningar för Analysis Services?  
**Svar:** Nej. Det finns inte stöd för att detta för tillfället.

**Fråga:** Kan jag använda gatewayen för att ansluta till en flerdimensionell (OLAP)-instans.  
**Svar:** Ja! Lokala datagateway har stöd för live-anslutningar till Analysis Services tabellmodeller och flerdimensionella modeller.

**Fråga:** Vad händer om jag installerar gatewayen på en dator i en annan domän än min lokala server som använder Windows-autentisering?  
**Svar:** Inga garantier här. Det beror helt på förtroenderelationen mellan de två domänerna. Om två olika domäner finns i en betrodd domänmodell, kan gatewayen ansluta till Analysis Services-servern och det effektiva användarnamnet kan lösas. Annars kan ett inloggningsfel uppstå.

**Fråga:** Hur tar jag reda på vilket effektivt användarnamn som skickas till min lokala Analysis Services-server?  
**Svar:** Vi svarar på detta i [Felsökningsartikeln](service-gateway-onprem-tshoot.md).

**Fråga:** Jag har 25 databaser i Analysis Services, går det att aktivera alla för gatewayen på en gång?  
**Svar:** Nej. Svar: Det är en av våra planer men vi har inte en tidslinje för detta.

## <a name="administration"></a>Administration
**Fråga:** Kan jag har fler än en administratör för en gateway?  
**Svar:** Ja! När du hanterar en gateway går du till administratörsfliken för att lägga till ytterligare administratörer.

**Fråga:** Måste gateway-administratören vara administratör på datorn där gatewayen är installerad?  
**Svar:** Nej. Gateway-administratören används för att hantera gatewayen från tjänsten.

**Fråga:** Kan jag hindra användare i min organisation från att skapa en gateway?  
**Svar:** Nej. Svar: Det är en av våra planer men vi har inte en tidslinje för detta.

**Fråga:** Kan jag få användningsinformation och statistik om mina gatewayar?  
**Svar:** Nej. Svar: Det är en av våra planer men vi har inte en tidslinje för detta.

## <a name="power-bi"></a>Power BI
**Fråga:** Måste jag uppgradera min personliga gateway?
**Svar:** Nej, du kan fortsätta att använda en personlig gateway för Power BI.

**Fråga:** Hur ofta uppdateras panelerna på en instrumentpanel i Power BI när de är anslutna till en lokal datagateway?  
**Svar:** Cirka var tionde minut. DirectQuery-anslutningar använder direkta frågor. Detta innebär inte att en panel skickar en fråga till den lokala servern och visar nya data var tionde minut.

**Fråga:** Går det att överföra Excel-arbetsböcker med Power Pivot-datamodeller som ansluter till lokala datakällor? Behöver jag en gateway för det här scenariot?  
**Svar:** Ja, du kan ladda upp arbetsboken. Och nej, du behöver inte en gateway. Men eftersom data kommer att finnas i Excel-datamodellen kommer rapporter i Power BI baserat på Excel-arbetsboken inte att uppdateras live. För att kunna uppdatera rapporter i Power BI måste du överföra en uppdaterad arbetsbok varje gång. Eller använda en gateway med schemalagd uppdatering.

**Fråga:** Om användare delar instrumentpaneler med en DirectQuery-anslutning, kommer dessa andra användare att kunna se data även om de kanske inte har samma behörigheter.  
**Svar:** Användare kan endast se de data som de har åtkomst till för instrumentpaneler som är anslutna till Analysis Services. Om användarna inte har samma behörigheter, kan de inte finns några data. För andra datakällor kommer alla användare att dela de autentiseringsuppgifter som angetts av administratören för datakällan.

**Fråga:** Varför kan inte ansluta till Oracle-server?  
**Svar:** Du kan behöva installera Oracle-klienten och konfigurera filen tnsnames.ora med rätt serverinformation för att ansluta till Oracle-servern. Det här är en separat installation utanför gatewayen. Mer information finns i [Installera Oracle-klienten](service-gateway-onprem-manage-oracle.md#installing-the-oracle-client).

**Fråga:** Kommer gatewayen att fungera med ExpressRoute?  
**Svar:** Ja! Mer information om ExpressRoute och Power BI finns i [Power BI och ExpressRoute](service-admin-power-bi-expressroute.md).

## <a name="next-steps"></a>Nästa steg
[Lokal datagateway](service-gateway-onprem.md)  
[Lokal datagateway – på djupet](service-gateway-onprem-indepth.md)  
[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

