---
title: inkludera fil
description: inkludera fil
services: powerbi
author: davidiseminger
ms.service: powerbi
ms.topic: include
ms.date: 04/28/2020
ms.author: davidi
ms.openlocfilehash: d56988986cfd994bb21c9bc25d024903719472cf
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82255839"
---
## <a name="single-sign-on"></a>Enkel inloggning

När du har publicerat en Azure SQL DirectQuery-datauppsättning till tjänsten, kan du aktivera enkel inloggning (SSO) via Azure Active Directory (AD Azure) OAuth2 för dina slutanvändare.

Om du vill aktivera enkel inloggning går du till datauppsättningens inställningar, öppnar fliken **Datakällor** och markerar rutan för enkel inloggning.

![Konfigurera Azure SQL DQ-dialogrutan](media/direct-query-sso/sso-dialog.png)

När alternativet för enkel inloggning är aktiverat och dina användares åtkomstrapporter har skapats ovanpå datakällan skickar Power BI deras autentiserade Azure AD-autentiseringsuppgifter i frågorna till Azure SQL-databasen eller informationslagret. Detta alternativ möjliggör för Power BI att respektera säkerhetsinställningarna som är konfigurerade på datakällsnivå.

Alternativet för enkel inloggning börjar fungera för alla datauppsättningar som använder den här datakällan. Autentiseringsmetoden som används för importscenarier påverkas inte.

