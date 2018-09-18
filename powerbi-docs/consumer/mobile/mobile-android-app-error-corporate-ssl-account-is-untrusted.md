---
title: Åtgärda ”Företags SSL-certifikat är inte betrott”
description: När du loggar in till Android-appen för Power BI ser du kanske meddelandet ”Det gick inte att autentisera eftersom ditt företags SSL-certifikat inte är betrott
.": ''
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-mobile
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 494e148a62675aab1a6e799c4e4b61f022483d9f
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/12/2018
ms.locfileid: "44748160"
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
Om du använder en anpassad autentiseringsserver kanske SSL-certifikatet i företagets autentiseringsserver inte är giltigt. Be din organisations IT-administratör att hjälpa dig.

## <a name="next-steps"></a>Nästa steg
* [Hämta Android-appen](http://go.microsoft.com/fwlink/?LinkID=544867) från Android-appbutiken.
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

