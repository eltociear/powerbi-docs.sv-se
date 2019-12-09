---
title: Köpa och tilldela Power BI Pro-licenser
description: Lär dig hur du köper och tilldelar Power BI Pro-användarlicenser så att användarna kan komma åt innehåll och samarbeta med kollegor i Power BI-tjänsten.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: quickstart
ms.date: 10/29/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: ebaf32bbf84dcbb8efd8516fd0a1ab01011f2d63
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698496"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Köpa och tilldela Power BI Pro-användarlicenser

Power BI Pro är en individuell användarlicens som gör det möjligt att läsa och interagera med rapporter och instrumentpaneler som andra användare har publicerat i Power BI-tjänsten, för att sedan dela innehållet och samarbeta med andra Power BI Pro-användare. Det är bara användare med en Power BI Pro-användarlicens som kan publicera och dela innehåll med andra användare samt använda innehåll som andra användare har skapat, om inte innehållet ligger i en Power BI Premium-kapacitet. Mer information finns i [Power BI-funktioner efter licenstyp](service-features-license-type.md).

## <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Köpa och tilldela Power BI Pro-användarlicenser

I den här artikeln förklaras hur du köper Power BI Pro-användarlicenser i administrationscentret för Microsoft 365. Sedan förklaras två alternativ som administratörer har för att tilldela dessa licenser till enskilda användare: i administrationscentret för Microsoft 365 eller i Azure-portalen (du väljer ett alternativ).

### <a name="prerequisites"></a>Förutsättningar

Om du vill köpa och tilldela licenser i administrationscentret för Microsoft 365 måste du ha rollen **[global administratör eller faktureringsadministratör](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)** i Microsoft 365.

För att kunna tilldela licenser i Azure-portalen måste du vara ägare till den Azure-prenumeration som Power BI använder för sökningar i Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Köpa licenser i Microsoft 365

Så här köper du Power BI Pro-licenser i administrationscentret för Microsoft 365:

1. Öppna [Administrationscenter för Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. Välj **Fakturering** > **Prenumerationer** i navigeringsfönstret.

    ![Navigeringsfönster](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-01.png)

3. Klicka på **Lägg till prenumerationer** i det övre högra hörnet på sidan **Prenumerationer**.

    ![Prenumeration](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-02.png)

4. Leta reda på önskat prenumerationserbjudande:

    Välj **Office 365 Enterprise E5** under **Enterprise Suite**.

    ![Office E5-prenumeration](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-03.png)

    Välj **Power BI Pro** under **Andra alternativ**.

    ![Power BI Pro-prenumeration](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-04.png)

5. För pekaren över de tre punkterna ( **. . .** ) för den önskade prenumerationen och välj **Köp nu**.

    ![Köp nu](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-05.png)

6. Välj om du vill betala **per månad** eller **för ett helt år**.

7. Under **Hur många användare vill du ha?** anger du önskat antal licenser och väljer sedan **Checka ut nu** för att slutföra transaktionen.

8. Kontrollera att den köpta prenumerationen nu visas på sidan **Prenumerationer**.

   ![Förvärvad prenumeration](media/service-admin-purchasing-power-bi-pro/service-purchasing-power-bi-pro-06.png)

9. Om du vill lägga till fler licenser efter det inledande köpet, väljer du **Power BI Pro** på sidan **Prenumerationer** och sedan **Lägg till/ta bort licenser**.

### <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Tilldela licenser i administrationscentret för Microsoft 365

Följ de här stegen om du vill tilldela Power BI Pro-licenser till enskilda användarkonton:

1. Öppna [Administrationscenter för Microsoft 365](https://portal.office.com/adminportal/home#/homepage).

2. Expandera **Användare** i navigeringsfönstret och välj sedan **Aktiva användare**.

    ![Aktiva användare](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-05.png)

3. Välj en användare och sedan **Redigera** under **Produktlicenser**.

    ![Redigera produktlicenser](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-06.png)

4. Under **Power BI Pro** ändrar du inställningen till **På** och klickar sedan på **Spara**.

    ![Produktlicenser På](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-07.png)

5. Under **Status** kontrollerar du att Power BI Pro-licensen har tilldelats för det valda kontot.

    ![Kontrollera licensstatus](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-08.png)

### <a name="assign-licenses-in-the-azure-portal"></a>Tilldela licenser i Azure-portalen

Följ de här stegen om du vill tilldela Power BI Pro-licenser till enskilda användarkonton:

1. Gå till [Azure-portalen](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/private/39bc3cf7-31a4-43f6-954c-f2d69ca2f0).

2. Välj **Azure Active Directory** i navigeringsfönstret.

    ![Azure Active Directory](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-01.png)

3. Under **Azure Active Directory** väljer du **Licenser**.

    ![Licenser](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-02.png)

4. Under **Licenser**, väljer du **Alla produkter** och väljer sedan **Power BI Pro** för att visa listan över licensierade användare.

    ![Licenser – Alla produkter](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-03.png)

5. Välj **Tilldela** för att lägga till en Power BI Pro-licens för ett användarkonto.

    ![Tilldela licens](media/service-admin-purchasing-power-bi-pro/service-assigning-power-bi-pro-licenses-04.png)

## <a name="next-steps"></a>Nästa steg

Nu när du har tilldelat licenser, kan du läsa mer om Power BI Pro.

[Power BI-licensiering i din organisation](service-admin-licensing-organization.md)

[Hitta Power BI-användare som har loggat in](service-admin-access-usage.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
