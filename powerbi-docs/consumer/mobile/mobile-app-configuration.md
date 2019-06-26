---
title: Konfigurationsinställningar för Power BI-appen för iOS
description: Så här anpassar du Power BI för iOS med hjälp av MDM-verktyget
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: a0883927f3a0a09bbe4d1ed618b7d5f708807464
ms.sourcegitcommit: 206806d8ddb6bdfc322c1a46fb34a1b0678acba2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66817017"
---
# <a name="remotely-configure-power-bi-ios-app-using-mobile-device-management-mdm-tool"></a>Konfigurera Power BI-appen för iOS via fjärranslutning med MDM-verktyget (mobile device management)

Power BI-appen för iOS har stöd för appinställningar som gör att administratörer för Office 365 och MDM-verktyg som Intune kan anpassa hur appen fungerar.

Power BI-mobilappen för iOS har stöd för följande konfigurationsscenarier:

- Rapportserverkonfiguration
- Inställningar för dataskydd

## <a name="report-server-configuration"></a>Rapportserverkonfiguration

Med Power BI-appen för iOS kan administratörer ”push-överföra” rapportserverkonfigurationer till registrerade enheter.

| Nyckel | Typ | Beskrivning |
|---|---|---|
| com.microsoft.powerbi.mobile.ServerURL | Sträng | Webbadress till rapportservern.<br><br>Ska börja med http eller https.|
| com.microsoft.powerbi.mobile.ServerUsername | Sträng | [valfritt]<br><br>Användarnamnet som ska användas för att ansluta servern.<br><br>Om det inte finns, uppmanas användaren att ange användarnamn för anslutningen i appen.|
| com.microsoft.powerbi.mobile.ServerDisplayName | Sträng | [valfritt]<br><br>Standardvärdet är ”Rapportserver”<br><br>Ett eget namn som används i appen för att representera servern. |
| com.microsoft.powerbi.mobile.OverrideServerDetails | Boolesk | [valfritt]<br><br>Standardvärdet är True. När värdet är True åsidosätts eventuella rapportserverdefinitioner som redan finns på den mobila enheten. Befintliga servrar som redan är konfigurerade tas bort. Genom att sätta Åsidosätt till True förhindras också att användaren tar bort konfigurationen.<br><br>Om värdet är False läggs de överförda värdena till eventuella befintliga värden. Om samma serveradress redan är konfigurerad i mobilappen lämnas konfigurationen i befintligt skick. Användaren uppmanas inte att logga in på nytt för samma server. |

## <a name="data-protection-setting"></a>Inställningar för dataskydd

Med Power BI-appen för iOS kan administratörer anpassa standardkonfigurationen av säkerhets- och sekretessinställningar. Du kan tvinga användarna att använda ansiktsigenkänning eller fingeravtryck för att öppna Power BI-appen.

| Nyckel | Typ | Beskrivning |
|---|---|---|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolesk | Standardvärdet är False. <br><br>Biometrik, som fingeravtryck eller ansiktsigenkänning, kan krävas för att användare ska kunna öppna appen på sin enhet. Om det behövs kan biometrik användas utöver vanlig autentisering.<br><br>Om du använder principer för appskydd rekommenderar Microsoft att du inaktiverar den här inställningen för att förhindra dubbla inloggningar. |

## <a name="deploying-app-configuration-settings"></a>Distribuera konfigurationsinställningar för appen

Med följande steg kan du skapa en appkonfigurationsprincip. När du har skapat konfigurationsprincipen kan du tilldela inställningarna till grupper av användare.

1. Anslut ditt MDM-verktyg.

2. Skapa och namnge en ny appkonfigurationsprincip.

3. Välj vilka användare som appkonfigurationsprincipen ska distribueras till.

4. Skapa nyckel/värde-par för den inställning som du vill push-överföra till användarna.

Med Intune-portalen kan administratörer enkelt distribuera de här inställningarna till Power BI-appen för iOS via appkonfigurationsprinciper.
Du kan även använda valfri MDM-provider. Om du inte använder Intune måste du läsa om hur du distribuerar de här inställningarna i MDM-dokumentationen.

## <a name="next-steps"></a>Nästa steg

* Hämta [Power BI-mobilappen för iPhone](http://go.microsoft.com/fwlink/?LinkId=522062)
* Följ [@MSPowerBI på Twitter](https://twitter.com/MSPowerBI)
* Delta i samtalet i [Power BI Community](http://community.powerbi.com/)
