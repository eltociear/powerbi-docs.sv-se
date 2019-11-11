---
title: Skydda Power BI-data med inbyggd enhetsidentifiering
description: Lär dig hur du konfigurerar iOS-appen så att det krävs ytterligare identifiering innan du kan komma åt dina Power BI-data
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: mshenhav
ms.openlocfilehash: a4ae7d7d61f4b377fe020fcc5f66f68ae7709ac7
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73870147"
---
# <a name="protect-power-bi-app-with-face-id-touch-id-or-passcode"></a>Skydda Power BI-appen med Face ID, Touch ID eller lösenord 

I många fall är de data som hanteras i Power BI konfidentiella och måste därför skyddas så att endast behöriga användare kommer åt dem. 

I Power BI-appen för iOS kan du skydda dina data genom att konfigurera ytterligare identifiering. Du måste då använda Face ID, Touch ID eller ett lösenord varje gång du startar appen, eller när du hämtar upp appen från bakgrunden.

| ![iPhone](./media/tutorial-mobile-apps-ios-qna/iphone-logo-50-px.png) | ![iPad](./media/tutorial-mobile-apps-ios-qna/ipad-logo-50-px.png) |
|:--- |:--- |
| iPhone-telefoner |iPad-surfplattor |

## <a name="turn-on-face-id-touch-id-or-passcode-in-app-setting"></a>Aktivera Face ID, Touch ID eller lösenord i appinställningarna

Om du vill använda ytterligare identifiering för Power BI går du till appinställningarna under **Sekretess och säkerhet**. Du ser alternativet för att aktivera Face ID, Touch ID eller lösenord baserat på enhetens funktioner.

![Inställningssida för Power BI-appen för iOS](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-setting.png)

När du har aktiverat inställningen måste du identifiera dig varje gång du startar Power BI eller hämtar upp appen från bakgrunden. 

Beslutet att fråga efter Face ID, Touch ID eller lösenord görs av iOS baserat på enhetens funktioner. Om enheten har stöd för Face ID måste du använda Face ID. Om enheten har stöd för Touch ID måste du använda Touch ID. Om inget av de här alternativen stöds måste du ange ett lösenord.

![Face ID för Power BI i iOS](./media/mobile-ios-native-secure-access/mobile-ios-native-secured-faceid.png)

## <a name="use-mdm-to-enforce-face-id-touch-id-or-passcode"></a>Använda MDM till att tvinga användningen av Face ID, Touch ID eller lösenord

En del organisationer har säkerhetsprinciper och efterlevnadskrav där det krävs ytterligare identifiering innan du kan komma åt känsliga affärsdata. 

I Power BI-appen för IOS kan administratörer styra den här inställningen genom att push-överföra appens konfigurationsinställningar från Microsoft Intune eller någon annan MDM-lösning. Administratörer kan använda appskyddsprincipen för att aktivera den här inställningen för alla användare eller för en grupp användare.

|Nyckel  |Typ  |Beskrivning  |
|---------|---------|---------|
| com.microsoft.powerbi.mobile.ForceDeviceAuthentication | Boolesk | Standardvärdet är False. <br>När värdet är True tvingas appanvändarna att identifiera sig med Face ID, Touch ID eller lösenord innan de kan visa Power BI-data i appen. Användare som inte har Face ID, Touch ID eller ett lösenord konfigurerat på enheten måste konfigurera detta innan de kan använda Power BI.  |

## <a name="next-steps"></a>Nästa steg

[Använda MDM till att konfigurera Power BI-appen för iOS via fjärranslutning](mobile-app-configuration.md)
