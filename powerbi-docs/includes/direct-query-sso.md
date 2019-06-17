---
title: inkludera fil
description: inkludera fil
services: powerbi
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 05/31/2019
ms.author: mblythe
ms.openlocfilehash: 94b6959b6bcbf250e54a353e8b725b6c9e5a2e30
ms.sourcegitcommit: c539726c9c180e899a8a34443e3fda2b9848beb2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66448390"
---
## <a name="single-sign-on"></a>Enkel inloggning

När du har publicerat en Azure SQL DirectQuery-datauppsättning till tjänsten, kan du aktivera enkel inloggning (SSO) via Azure Active Directory (AD Azure) OAuth2 för dina slutanvändare.

Om du vill aktivera enkel inloggning går du till datauppsättningens inställningar, öppnar fliken **Datakällor** och markerar rutan för enkel inloggning.

![Konfigurera Azure SQL DQ-dialogrutan](media/direct-query-sso/sso-dialog.png)

När alternativet för enkel inloggning är aktiverat och dina användares åtkomstrapporter har skapats ovanpå datakällan skickar Power BI deras autentiserade Azure AD-autentiseringsuppgifter i frågorna till Azure SQL-databasen eller informationslagret. Detta möjliggör för Power BI att respektera säkerhetsinställningarna som är konfigurerade på datakällsnivå.

Alternativet för enkel inloggning börjar fungera för alla datauppsättningar som använder den här datakällan. Autentiseringsmetoden som används för importscenarier påverkas inte.

> [!Note]
> Azure Multi-Factor Authentication (MFA) stöds inte. Användare som vill använda enkel inloggning med Azure SQL DirectQuery måste undantas från MFA.