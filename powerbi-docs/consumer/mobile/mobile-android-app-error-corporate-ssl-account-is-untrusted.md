---
title: Åtgärda ”Företags SSL-certifikat är inte betrott”
description: När du loggar in till Android-appen för Power BI ser du kanske meddelandet ”Det gick inte att autentisera eftersom ditt företags SSL-certifikat inte är betrott
.": ''
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: 85e295b2320f8aecca2176149ce37c0a25ad2bd2
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85237462"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>Åtgärda ”Företagets SSL-certifikat är inte betrott” – Power BI
När du loggar in till Android-mobilappen för Microsoft Power BI ser du kanske meddelandet ”Det gick inte att autentisera eftersom ditt företags SSL-certifikat inte är betrott av den här enheten. Kontakta ditt företags IT-administratör.” 

Vad du behöver göra beror vanligtvis på din Android-enhets operativsystem, men det finns även några andra problem som kan orsaka det här felet.

## <a name="on-android-7-or-later"></a>På Android 7 eller senare
Leta efter en uppdatering för en app med namnet **Chrome** och installera uppdateringen.

## <a name="on-android-6-and-earlier"></a>På Android 6 och tidigare
Enheten behöver kanske en uppdaterad version av System Webview. Du kan installera den på enheten och behöver förmodligen bara klicka på **Uppdatera**.

Om System Webview inte har installerats på din enhet:

1. Stäng Power BI på Android-enheten.
2. Öppna Google Play Butik och sök efter **System Webview** från Google Inc.
3. Installera programmet.
4. Starta om Power BI-appen och logga in.

## <a name="time-zone-settings"></a>Tidszonsinställningar
Tidszon inställningarna på din enhet kan vara felaktiga. 

Kontrollera dem genom att gå till **Inställningar** > **System** > **Datum och tid**.

## <a name="custom-authentication-server"></a>Server för anpassad autentisering
Om du använder en anpassad autentiseringsserver kanske SSL-certifikatet i företagets autentiseringsserver inte är giltigt. Kontakta din organisations IT-avdelningen att testa serverkonfigurationen för företagsautentisering genom att följa riktlinjerna i [den här artikeln](https://support.microsoft.com/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce).

## <a name="next-steps"></a>Nästa steg
* [Hämta Android-appen](https://go.microsoft.com/fwlink/?LinkID=544867) från Android-appbutiken.
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/) 

