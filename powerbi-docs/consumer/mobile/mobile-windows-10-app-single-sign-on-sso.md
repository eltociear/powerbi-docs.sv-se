---
title: Enkel inloggning i Windows-mobilappen för Power BI
description: Läs om Enkel inloggning (SSO) i Windows-mobilappen för Power BI. Enkel inloggning innebär att du har åtkomst till alla program och resurser du behöver för att göra affärer genom att bara en gång, logga in med ett enda användarkonto.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: f62237e0aa0ac31d63fee4b980db2991206ddf4d
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240317"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Enkel inloggning i Windows-mobilappen för Power BI

Läs om Enkel inloggning (SSO) i Windows-mobilappen för Power BI. Enkel inloggning innebär att du har åtkomst till alla program och resurser du behöver för att göra affärer genom att bara en gång, logga in med ett enda användarkonto. När du har loggat in, kan du komma åt dessa program utan att behöva autentisera igen. 

Eftersom Power BI Windows-appen är integrerad i Azure Active Directory så kan du använda ditt primära organisationskonto för att inte bara logga in på dina domänanslutna enheter utan även logga in på Power BI-tjänsten. Om du visar Power BI på Windows-phone kan du kontrollera att det konto som används för Power BI är konfigurerat som ett arbets- eller skolkonto i enhetsinställningarna.  

Enkel inloggning är enbart aktiverat för Windows-enheter som hanteras av Windows Azure Active Directory.

>[!NOTE]
>Stöd för Power BI-mobilappen för **telefoner som använder Windows 10 Mobile** kommer att upphöra den 16 mars 2021. [Läs mer](https://go.microsoft.com/fwlink/?linkid=2121400)

## <a name="sign-in-with-sso"></a>Logga in med enkel inloggning

För att förenkla inloggningsprocessen så försöker en app automatiskt autentisera dig mot Power BI-tjänsten med enkel inloggning när du installerar appen för första gången. Det är bara om den här processen inte lyckas som appen ber dig att ange dina autentiseringsuppgifter för Power BI.  

Om du redan använder Power BI-mobilappen för Windows, kan du också använda enkel inloggning när du uppgraderar till den nya versionen av appen. Logga ut från appen, stäng den och öppna den igen. När appen öppnas igen så försöker den automatiskt att använda dina aktuella Windows-autentiseringsuppgifter för att autentisera mot Power BI-tjänsten. 

Om du inte vill använda autentiseringsuppgifterna för din aktiva Windows-session för att logga in på Power BI så kan du gå till **Inställningar**, logga ut och logga in med andra autentiseringsuppgifter. 
 
## <a name="next-steps"></a>Nästa steg

- [Kom igång med Power BI-mobilappen för Windows 10](mobile-windows-10-phone-app-get-started.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)

