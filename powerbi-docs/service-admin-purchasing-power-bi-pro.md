---
title: Köpa och tilldela Power BI Pro-licenser
description: Lär dig hur du köper och tilldelar Power BI Pro-användarlicenser så att användarna kan komma åt innehåll och samarbeta med kollegor i Power BI-tjänsten.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 12/18/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 01eb30857b0b76f96e7e18115d92fb1d68dbef0c
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223831"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Köpa och tilldela Power BI Pro-användarlicenser

Power BI Pro är en individuell användarlicens som gör det möjligt att läsa och interagera med rapporter och instrumentpaneler som andra användare har publicerat i Power BI-tjänsten, för att sedan dela innehållet och samarbeta med andra Power BI Pro-användare. Det är bara användare med en Power BI Pro-användarlicens som kan publicera och dela innehåll med andra användare samt använda innehåll som andra användare har skapat, om inte innehållet ligger i en Power BI Premium-kapacitet. Mer information finns i avsnittet _Jämförelse av Power BI-funktioner_ i [Power BI-prissättning](https://powerbi.microsoft.com/pricing/).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Köpa och tilldela Power BI Pro-användarlicenser

I den här artikeln förklaras hur du köper Power BI Pro-användarlicenser i administrationscentret för Microsoft 365. Sedan förklaras två alternativ som administratörer har för att tilldela dessa licenser till enskilda användare: i administrationscentret för Microsoft 365 eller i Azure-portalen (du väljer ett alternativ).

### <a name="prerequisites"></a>Förutsättningar

Om du vill köpa och tilldela licenser i administrationscentret för Microsoft 365 måste du ha rollen **[global administratör eller faktureringsadministratör](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** i Microsoft 365.

För att kunna tilldela licenser i Azure-portalen måste du vara ägare till den Azure-prenumeration som Power BI använder för sökningar i Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Köpa licenser i Microsoft 365

Så här köper du Power BI Pro-licenser i administrationscentret för Microsoft 365:

1. Öppna [Administrationscenter för Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. I navigeringsfönstret väljer du **Fakturering** och sedan **Prenumerationer**.

3. Klicka på **Lägg till prenumerationer** i det övre högra hörnet på sidan **Prenumerationer**.

4. Leta reda på önskat prenumerationserbjudande:

    - Välj **Office 365 Enterprise E5** under **Enterprise Suite**.

    - Välj **Power BI Pro** under **Andra alternativ**.

5. För pekaren över de tre punkterna ( **. . .** ) för den önskade prenumerationen och välj **Köp nu**.

6. Välj om du vill betala **per månad** eller **för ett helt år**.

7. Under **Hur många användare vill du ha?** anger du önskat antal licenser och väljer sedan **Checka ut nu** för att slutföra transaktionen.

8. Kontrollera att den köpta prenumerationen nu visas på sidan **Prenumerationer**.

9. Om du vill lägga till fler licenser efter det inledande köpet väljer du **Power BI Pro** på sidan **Prenumerationer** och sedan **Ändra licensantal**.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Tilldela licenser i administrationscentret för Microsoft 365

Information om tilldelning av licenser i administrationscentret för Microsoft 365 finns i [Tilldela licenser till användare](/office365/admin/manage/assign-licenses-to-users).

Information gällande gästanvändare finns i [Tilldela licenser till användare på sidan Licenser](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Innan du tilldelar gästanvändare Pro-licenser bör du kontakta din Microsoft-kontorepresentant och se till att du följer villkoren i ditt avtal med Microsoft.

### <a name="assign-licenses-in-the-azure-portal"></a>Tilldela licenser i Azure-portalen

Följ de här stegen om du vill tilldela Power BI Pro-licenser till enskilda användarkonton:

1. Gå till [Azure-portalen](https://portal.azure.com/).

2. Sök efter och välj **Azure Active Directory**.

3. Under **Azure Active Directory** väljer du **Licenser**.

4. Under **Licenser**, väljer du **Alla produkter** och väljer sedan **Power BI Pro** för att visa listan över licensierade användare.

5. Välj **Tilldela** för att lägga till en Power BI Pro-licens för ett användarkonto.

## <a name="next-steps"></a>Nästa steg

Nu när du har tilldelat licenser, kan du läsa mer om Power BI Pro.

[Power BI-licensiering i din organisation](service-admin-licensing-organization.md)

[Hitta Power BI-användare som har loggat in](service-admin-access-usage.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
