---
title: Översikt över tjänstens huvudnamn
description: Översikt över tjänstens huvudnamn
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 04/05/2020
ms.custom: include file
ms.openlocfilehash: 7fc4412a66602fe3a6548c3e1afb06de788da90d
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82616125"
---
Tjänstens huvudnamn är en autentiseringsmetod som kan användas för att ge Azure AD-program åtkomst till Power BI-tjänstinnehåll och API:er.

När du skapar en Azure Active Directory-app (Azure AD) skapas ett [huvudobjekt för tjänsten](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). Huvudobjektet för tjänsten, som också är känt som *tjänstens huvudnamn*, gör att Azure AD kan autentisera din app. Efter autentisering kan appen komma åt Azure AD-klientens resurser.

För att autentisera använder tjänstens huvudnamn Azure AD-appens *program-ID* och något av följande:
* Apphemlighet
* Certifikat