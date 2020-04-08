---
ms.openlocfilehash: 26f4b82301915524b65d9d2d6b39d61b54ed0321
ms.sourcegitcommit: 8eeb784fd46321680367ac913ef976aeedaa7766
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80621573"
---
Tjänstens huvudnamn är en autentiseringsmetod som kan användas för att ge Azure AD-program åtkomst till Power BI-tjänstinnehåll och API:er.

När du skapar en Azure Active Directory-app (Azure AD) skapas ett [huvudobjekt för tjänsten](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object). Huvudobjektet för tjänsten, som också är känt som *tjänstens huvudnamn*, gör att Azure AD kan autentisera din app. Efter autentisering kan appen komma åt Azure AD-klientens resurser.

För att autentisera använder tjänstens huvudnamn Azure AD-appens *program-ID* och något av följande:
* Apphemlighet
* Certifikat