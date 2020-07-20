---
title: Konfigurationsinställningar för Power BI-appen
description: Så här anpassar du Power BI med hjälp av MDM-verktyget
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 07/14/2020
ms.author: painbar
ms.openlocfilehash: f9b6efd07aad3d2058e49f81ae21095b618123ee
ms.sourcegitcommit: d8acf2fb0318708a3e8e1e259cb3747b0312b312
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86385939"
---
# <a name="remotely-configure-power-bi-app-using-mobile-device-management-mdm-tool"></a>Konfigurera Power BI-appen via fjärranslutning med verktyget för hantering av mobilenheter (MDM)

Power BI Mobile-appen för iOS och Android har stöd för appinställningar som innebär att administratörer av MDM-tjänster, till exempel Intune, kan anpassa appen.

Power BI Mobile-appen har stöd för följande konfigurationsscenarier:

* Konfiguration av rapportserver (iOS och Android)
* Inställningar för dataskydd (iOS och Android)
* Inaktivera enkel inloggning (iOS och Android)
* Inställningar för interaktion (iOS och Android)

## <a name="report-server-configuration-ios-and-android"></a>Konfiguration av rapportserver (iOS och Android)

Med Power BI-appen för iOS och Android kan administratörer fjärrstyra push-överföring av rapportserverkonfigurationen till registrerade enheter.

| Nyckel | Typ | Beskrivning |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Sträng | Webbadress till rapportservern.<br><br>Ska börja med http eller https.|
| com.microsoft.powerbi.mobile.ServerUsername | Sträng | [valfritt]<br><br>Användarnamnet som ska användas för att ansluta servern.<br><br>Om det inte finns, uppmanas användaren att ange användarnamn för anslutningen i appen.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Sträng | [valfritt]<br><br>Standardvärdet är ”Rapportserver”<br><br>Ett eget namn som används i appen för att representera servern. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolesk | [valfritt]<br><br>Standardvärdet är True. När värdet är True åsidosätts eventuella rapportserverdefinitioner som redan finns på den mobila enheten. Befintliga servrar som redan är konfigurerade tas bort. Genom att sätta Åsidosätt till True förhindras också att användaren tar bort konfigurationen.<br><br>Sätt värdet till False för att lägga till de push-överförda värdera, vilket bevarar de befintliga inställningarna. Om samma server-URL redan har konfigurerats i mobilappen, lämnas den konfigurationen i befintligt skick. Användaren uppmanas inte att logga in på nytt för samma server. |

## <a name="data-protection-settings-ios-and-android"></a>Inställningar för dataskydd (iOS och Android)

Med Power BI-mobilappen för iOS och Android kan administratörer anpassa standardkonfigurationen av säkerhets- och sekretessinställningar. För iOS kan du tvinga användarna att använda ansiktsigenkänning, fingeravtryck eller lösenord när de öppnar Power BI-mobilappen. För Android kan du tvinga användarna att använda biometrisk autentisering (fingeravtrycks-ID).

| Nyckel | Typ | Beskrivning |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolesk | Standardvärdet är False. <br><br>Biometrisk autentisering med Touch ID eller Face ID (iOS) eller fingeravtrycks-ID (Android) kan krävas när användarna ska öppna appen på sin enhet. Om det behövs kan biometrik användas utöver vanlig autentisering.<br><br>Om du använder principer för appskydd rekommenderar Microsoft att du inaktiverar den här inställningen för att förhindra dubbla inloggningar. |

>[!NOTE]
>Inställningarna för dataskydd tillämpas endast på Android-enheter som stöder biometrisk autentisering.

## <a name="disable-single-sign-on-ios-and-android"></a>Inaktivera enkel inloggning (iOS och Android)

Som standard kan en användare välja enkel inloggning i Power BI-mobilappen och därmed inte behöva ange användarnamn och lösenord vid varje inloggning. Den här funktionen för enkel inloggning baseras på antagandet att enheten är användarens personliga enhet, och att det bara är en person som använder enheten och apparna på den.

Administratörer kan aktivera inställningen **DisableSingleSignOn** i appens konfigurationsfil för att inaktivera enkel inloggning och uttryckligen fråga efter användarens lösenord vid varje inloggning.

Det här är en administratörsinställning som konfigureras via fjärrkonfiguration. Slutanvändaren kan inte ändra den här inställningen.

| Nyckel | Typ | Beskrivning |
|---|---|---|
| com.microsoft.powerbi.mobile.DisableSingleSignOn | Boolesk | Standardvärdet är False.<br><br>När en användare loggar ut återanvänder inte appen befintliga autentiseringsuppgifter, utan uppmanar nästa användare att ange ett lösenord för autentisering och anslutning till Power BI-tjänsten.
 |

## <a name="interaction-settings-ios-and-android"></a>Inställningar för interaktion (iOS och Android)

Power BI-appen för iOS och Android ger administratörer möjlighet att konfigurera interaktionsinställningar om det fastställs att standardinteraktionsinställningarna måste ändras mellan grupper av användare i en organisation.

>[!NOTE]
>Alla interaktioner stöds inte för närvarande på alla enheter. Se [Konfigurera inställningar för rapportinteraktion](mobile-app-interaction-settings.md) för ett diagram som visar tillgängligheten för alla enheter.

| Nyckel | Typ | Värden | Beskrivning |
|---|---|---|---|
| com.microsoft.powerbi.mobile.ReportTapInteraction | Sträng |  <nobr>enkelknackning</nobr><br><nobr>dubbelknackning</nobr> | Konfigurera om ett tryck på ett visuellt objekt även markerar en datapunkt. |
| com.microsoft.powerbi.mobile.EnableMultiSelect | Boolesk |  <nobr>True</nobr><br><nobr>False</nobr> | Ange om ett tryck på en datapunkt ska ersätta den aktuella markeringen eller läggas till i den aktuella markeringen. |
| com.microsoft.powerbi.mobile.RefreshAction | Sträng |  <nobr>dra nedåt för att uppdatera</nobr><br>knapp | Konfigurera om användaren ska ha en knapp för att uppdatera rapporten eller ska använda dra nedåt för att uppdatera. |
| com.microsoft.powerbi.mobile.FooterAppearance | Sträng |  dockad<br>dynamisk | Konfigurera om rapportfoten ska vara fäst längst ned i rapporten eller döljas automatiskt. |

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