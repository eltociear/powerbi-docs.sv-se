---
title: Enkel inloggning i Windows-mobilappen för Power BI
description: Läs om Enkel inloggning (SSO) i Windows-mobilappen för Power BI. Enkel inloggning innebär att du har åtkomst till alla program och resurser du behöver för att göra affärer genom att bara en gång, logga in med ett enda användarkonto.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: mshenhav
ms.openlocfilehash: fdbdebacc2ae41cdfa8296eb6b0c06e52f149cac
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290968"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Enkel inloggning i Windows-mobilappen för Power BI

Läs om Enkel inloggning (SSO) i Windows-mobilappen för Power BI. Enkel inloggning innebär att du har åtkomst till alla program och resurser du behöver för att göra affärer genom att bara en gång, logga in med ett enda användarkonto. När du har loggat in, kan du komma åt dessa program utan att behöva autentisera igen. 

Eftersom Power BI Windows-appen är integrerad i Azure Active Directory så kan du använda ditt primära organisationskonto för att inte bara logga in på dina domänanslutna enheter utan även logga in på Power BI-tjänsten. Om du visar Power BI på Windows-phone kan du kontrollera att det konto som används för Power BI är konfigurerat som ett arbets- eller skolkonto i enhetsinställningarna.  

Enkel inloggning är enbart aktiverat för Windows-enheter som hanteras av Windows Azure Active Directory. 

## <a name="sign-in-with-sso"></a>Logga in med enkel inloggning

För att förenkla inloggningsprocessen så försöker en app automatiskt autentisera dig mot Power BI-tjänsten med enkel inloggning när du installerar appen för första gången. Det är bara om den här processen inte lyckas som appen ber dig att ange dina autentiseringsuppgifter för Power BI.  

Om du redan använder Power BI-mobilappen för Windows, kan du också använda enkel inloggning när du uppgraderar till den nya versionen av appen. Logga ut från appen, stäng den och öppna den igen. När appen öppnas igen så försöker den automatiskt att använda dina aktuella Windows-autentiseringsuppgifter för att autentisera mot Power BI-tjänsten. 

Om du inte vill använda autentiseringsuppgifterna för din aktiva Windows-session för att logga in på Power BI så kan du gå till **Inställningar**, logga ut och logga in med andra autentiseringsuppgifter. 
 
## <a name="next-steps"></a>Nästa steg

- [Kom igång med Power BI-mobilappen för Windows 10](mobile-windows-10-phone-app-get-started.md)
- Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

