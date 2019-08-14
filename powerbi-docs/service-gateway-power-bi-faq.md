---
title: Vanliga frågor och svar om lokal datagateway – Power BI
description: Den här artikeln innehåller vanliga frågor och svar om lokal datagateway för Power BI. Här samlar vi vanliga frågor om gateway på ett och samma ställe för den gateway som används i Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: cd3afd0ed3ba1f5b734aab2106cbd70f65f29006
ms.sourcegitcommit: cc4b18d55b2dca8fdb1bef00f53a0a808c41432a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68867057"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>Vanliga frågor och svar om lokal datagateway – Power BI

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**Fråga:** Behöver jag uppgradera lokal datagateway (personligt läge)?

**Svar:** Nej, du kan fortsätta att använda gatewayen (personligt läge) för Power BI.

**Fråga:** Krävs det särskilda behörigheter för att installera gatewayen och hantera den i Power BI-tjänsten?

**Svar:** Det krävs inga särskilda behörigheter.

**Fråga:** Går det att överföra Excel-arbetsböcker med Power Pivot-datamodeller som ansluter till lokala datakällor? Behöver jag en gateway för det här scenariot? 

**Svar:** Ja, du kan ladda upp arbetsboken. Och nej, du behöver inte en gateway. Men eftersom data kommer att finnas i Excel-datamodellen kommer rapporter i Power BI baserat på Excel-arbetsboken inte att uppdateras live. För att kunna uppdatera rapporter i Power BI måste du överföra en uppdaterad arbetsbok varje gång. Eller använda en gateway med schemalagd uppdatering.

**Fråga:** Om användare delar instrumentpaneler med en DirectQuery-anslutning, kommer dessa andra användare att kunna se data även om de kanske inte har samma behörigheter. 

**Svar:** Användare kan endast se de data som de har åtkomst till för instrumentpaneler som är anslutna till Azure Analysis Services. Om användarna inte har samma behörigheter, kan de inte se några data. För andra datakällor kommer alla användare att dela de autentiseringsuppgifter som angetts av administratören för datakällan.

**Fråga:** Varför kan jag inte ansluta till min Oracle-server? 

**Svar:** Du kan behöva installera Oracle-klienten och konfigurera filen tnsnames.ora med rätt serverinformation om du ska kunna ansluta till Oracle-servern. Det här är en separat installation utanför gatewayen. Mer information finns i [Installera Oracle-klienten](service-gateway-onprem-manage-oracle.md#install-the-oracle-client).

**Fråga:** Kommer gatewayen att fungera med Azure ExpressRoute? 

**Svar:** Ja. Mer information om ExpressRoute och Power BI finns i [Power BI och ExpressRoute](service-admin-power-bi-expressroute.md).

**Fråga:** Jag använder R-skript. Stöds detta?

**Svar:** R-skript stöds endast för personligt läge.

## <a name="analysis-services-in-power-bi"></a>Analysis Services i Power BI

**Fråga:** Kan jag använda msdmpump.dll för att skapa anpassade effektiva mappningar av användarnamn för Analysis Services? 

**Svar:** Nej. Den här användningen stöds inte för tillfället.

**Fråga:** Kan jag använda gatewayen för att ansluta till en flerdimensionell (OLAP)-instans? 

**Svar:** Ja. Lokala datagateway har stöd för live-anslutningar till Analysis Services tabellmodeller och flerdimensionella modeller.

**Fråga:** Vad händer om jag installerar gatewayen på en dator i en annan domän än min lokala server som använder Windows-autentisering? 

**Svar:** Inga garantier här. Det beror helt på förtroenderelationen mellan de två domänerna. Om två olika domäner finns i en betrodd domänmodell, kan gatewayen ansluta till Analysis Services-servern och det gällande användarnamnet kan matchas. Annars kan ett inloggningsfel uppstå.

**Fråga:** Hur tar jag reda på vilket effektivt användarnamn som skickas till min lokala Analysis Services-server? 

**Svar:** Vi svarar på den här frågan i [felsökningsartikeln](service-gateway-onprem-tshoot.md).

## <a name="next-steps"></a>Nästa steg

* [Felsökning av den lokala datagatewayen](/data-integration/gateway/service-gateway-tshoot)

Har du fler frågor? Testa [Power BI Community](http://community.powerbi.com/).

