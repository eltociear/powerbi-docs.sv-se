---
title: Konfigurationsinställningar för Power BI-appen
description: Så här anpassar du Power BI med hjälp av MDM-verktyget
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 11/07/2019
ms.author: painbar
ms.openlocfilehash: ccc7e3864590145309709d27774951c281b3ebdd
ms.sourcegitcommit: ef9ab7c0d84b926094c33e8aa2765cd43b844314
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/03/2020
ms.locfileid: "75622358"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Konfigurera Power BI-appen via fjärranslutning med verktyget för hantering av mobilenheter (MDM)

Power BI Mobile-appen för iOS och Android har stöd för appinställningar som innebär att administratörer av MDM-tjänster, till exempel Intune, kan anpassa appen.

Power BI Mobile-appen har stöd för följande konfigurationsscenarier:

- Konfiguration av rapportserver (iOS och Android)
- Inställningar för dataskydd (iOS)

## <a name="report-server-configuration-ios-and-android"></a>Konfiguration av rapportserver (iOS och Android)

Med Power BI-appen för iOS och Android kan administratörer fjärrstyra push-överföring av rapportserverkonfigurationen till registrerade enheter.

| Nyckel | Typ | Beskrivning |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Sträng | Webbadress till rapportservern.<br><br>Ska börja med http eller https.|
| com.microsoft.powerbi.mobile.ServerUsername | Sträng | [valfritt]<br><br>Användarnamnet som ska användas för att ansluta servern.<br><br>Om det inte finns, uppmanas användaren att ange användarnamn för anslutningen i appen.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Sträng | [valfritt]<br><br>Standardvärdet är ”Rapportserver”<br><br>Ett eget namn som används i appen för att representera servern. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolesk | [valfritt]<br><br>Standardvärdet är True. När värdet är True åsidosätts eventuella rapportserverdefinitioner som redan finns på den mobila enheten. Befintliga servrar som redan är konfigurerade tas bort. Genom att sätta Åsidosätt till True förhindras också att användaren tar bort konfigurationen.<br><br>Sätt värdet till False för att lägga till de push-överförda värdera, vilket bevarar de befintliga inställningarna. Om samma server-URL redan har konfigurerats i mobilappen, lämnas den konfigurationen i befintligt skick. Användaren uppmanas inte att logga in på nytt för samma server. |

## <a name="data-protection-settings-ios"></a>Inställningar för dataskydd (iOS)

Med Power BI-appen för iOS kan administratörer anpassa standardkonfigurationen av säkerhets- och sekretessinställningar. Du kan tvinga användarna att använda ansiktsigenkänning, fingeravtryck eller lösenord för att kunna öppna Power BI-appen.

| Nyckel | Typ | Beskrivning |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolesk | Standardvärdet är False. <br><br>Biometrik, som fingeravtryck eller ansiktsigenkänning, kan krävas för att användare ska kunna öppna appen på sin enhet. Om det behövs kan biometrik användas utöver vanlig autentisering.<br><br>Om du använder principer för appskydd rekommenderar Microsoft att du inaktiverar den här inställningen för att förhindra dubbla inloggningar. |

## <a name="deploying-app-configuration-settings"></a>Distribuera konfigurationsinställningar för appen

Med följande steg kan du skapa en appkonfigurationsprincip. När du har skapat konfigurationsprincipen kan du tilldela inställningarna till grupper av användare.

1. Anslut ditt MDM-verktyg.
2. Skapa och namnge en ny appkonfigurationsprincip.
3. Välj vilka användare som appkonfigurationsprincipen ska distribueras till.
4. Skapa nyckel/värde-par för den inställning som du vill push-överföra till användarna.

Med Intune-portalen kan administratörer enkelt distribuera de här inställningarna till Power BI-appen via appkonfigurationsprinciper. Du kan även använda valfri MDM-provider. Om du inte använder Intune måste du läsa om hur du distribuerar de här inställningarna i MDM-dokumentationen.

## <a name="next-steps"></a>Nästa steg

* Hämta Power BI-mobilappen från [App Store](https://apps.apple.com/app/microsoft-power-bi/id929738808) eller [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.powerbim&amp;amp;clcid=0x409)
* Följ [@MSPowerBI på Twitter](https://twitter.com/MSPowerBI)
* Delta i samtalet i [Power BI Community](https://community.powerbi.com/)
