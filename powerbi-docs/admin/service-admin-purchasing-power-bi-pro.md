---
title: Köpa och tilldela Power BI Pro-licenser
description: Lär dig att köpa och tilldela Power BI Pro-användarlicenser så att användarna kan komma åt innehåll och samarbeta med andra i Power BI-tjänsten.
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 899055ea26d1f36592c426ba402aa363b65bfa15
ms.sourcegitcommit: 0d0ab427bb71b37c9e5170c515a8f274e1f20c17
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87878364"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>Köpa och tilldela Power BI Pro-användarlicenser

>[!IMPORTANT]
>Den här artikeln är till för administratörer. Är du en användare som är redo att uppgradera till en Power BI Pro-licens? Gå direkt till [Kom igång med Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro) för att konfigurera ditt konto.

Power BI Pro är en enskild användarlicens där användarna kan läsa och interagera med rapporter och instrumentpaneler som andra har publicerat i Power BI-tjänsten. Användare med den här licenstypen kan dela innehåll och samarbeta med andra Power BI Pro-användare. Det är bara Power BI Pro-användare som kan publicera och dela innehåll med andra användare samt använda innehåll som andra användare har skapat, om inte innehållet ligger i en Power BI Premium-kapacitet. Mer information om tillgängliga typer av licenser och prenumerationer finns i [Power BI-licensiering i din organisation](service-admin-licensing-organization.md).

## <a name="purchase-power-bi-pro-user-licenses"></a>Köpa Power BI Pro-användarlicenser

Den här artikeln beskriver hur du köper Power BI Pro-användarlicenser i Administrationscenter för Microsoft 365. När du har köpt licenser kan du tilldela dem till användare i antingen Administrationscenter för Microsoft 365 eller Azure-portalen.

> [!NOTE]
> Från och med 14 januari 2020 är funktionerna för självbetjäningsköp, prenumeration och licenshantering för Power Platform-produkter (Power BI, Power Apps och Power Automate) tillgängliga för kommersiella molnkunder. Mer information finns i [Vanliga frågor och svar om självbetjäningsköp](https://docs.microsoft.com/microsoft-365/commerce/subscriptions/self-service-purchase-faq). Om du vill aktivera eller inaktivera funktioner för självbetjäningsköp läser du [Aktivera eller inaktivera registrering och inköp via självbetjäning](/power-bi/admin/service-admin-disable-self-service).

### <a name="prerequisites"></a>Förutsättningar

Om du vill köpa och tilldela licenser i administrationscentret för Microsoft 365 måste du ha rollen [global administratör eller faktureringsadministratör](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d) i Microsoft 365.

För att kunna tilldela licenser i Azure-portalen måste du vara ägare till den Azure-prenumeration som Power BI använder för sökningar i Azure Active Directory.

### <a name="purchase-licenses-in-microsoft-365"></a>Köpa licenser i Microsoft 365

> [!NOTE]
> Om du vanligtvis köper licenser via ett volymlicensavtal, som ett Enterprise-avtal, och vill få en faktura i stället för att köpa med ett kreditkort eller ett bankkonto, måste du skicka beställningen på ett annat sätt. Kontakta din Microsoft-återförsäljare eller gå via Volume Licensing Service Center om du vill lägga till eller ta bort licenser. Mer information finns i [Hantera prenumerationslicenser](https://docs.microsoft.com/microsoft-365/commerce/licenses/buy-licenses?view=o365-worldwide).

Så här köper du Power BI Pro-licenser i administrationscentret för Microsoft 365:

1. Logga in på [Administrationscenter för Microsoft 365](https://admin.microsoft.com).

2. I navigeringsmenyn väljer du **Fakturering** > **Köptjänster**.

3. Sök eller bläddra för att hitta den prenumeration som du vill köpa. Du hittar **Power BI** under **Andra kategorier som kan intressera dig** nästan längst ned på sidan. Välj länken om du vill se de Power BI-prenumerationer som är tillgängliga för din organisation.

4. Välj **Power BI Pro**.

5. På sidan **Köptjänster** väljer du **Köp**.

6. Välj **Betala varje månad** eller **Betala för ett helt år**.

7. Under **Hur många användare vill du ha?** anger du önskat antal licenser och väljer sedan **Checka ut nu** för att slutföra transaktionen.

8. Bekräfta ditt köp genom att gå till **Fakturering** > **Produkter och tjänster** och leta efter **Power BI Pro**.

9. Om du vill lägga till fler licenser senare letar du upp **Power BI Pro** på sidan **Produkter och tjänster** och väljer sedan **Lägg till/ta bort licenser**.


## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>Tilldela licenser i administrationscentret för Microsoft 365

Information om tilldelning av licenser i administrationscentret för Microsoft 365 finns i [Tilldela licenser till användare](/office365/admin/manage/assign-licenses-to-users).

Information gällande gästanvändare finns i [Tilldela licenser till användare på sidan Licenser](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page). Innan du tilldelar Pro-licenser till gästanvändare, bör du kontakta din Microsoft-kontorepresentant och kontrollera att du följer villkoren i ditt avtal med Microsoft.

## <a name="assign-licenses-in-the-azure-portal"></a>Tilldela licenser i Azure-portalen

Följ de här stegen om du vill tilldela Power BI Pro-licenser till enskilda användarkonton:

1. Logga in på [Azure-portalen](https://portal.azure.com/).

2. Sök efter och välj **Azure Active Directory**.

3. Under **Hantera** på resursmenyn **Azure Active Directory** väljer du **Licenser**.

4. Välj **Alla produkter** i resursmenyn **Licenser – Översikt** och välj **Power BI Pro** för att se listan med licensierade användare.

5. Välj **+ Tilldela** i kommandofältet. På sidan **Tilldela licens** väljer du först en användare och sedan **Tilldelningsalternativ** för att aktivera en Power BI Pro-licens för det valda användarkontot.

## <a name="next-steps"></a>Nästa steg

- [Power BI-licensiering i din organisation](service-admin-licensing-organization.md)

 - [Hitta Power BI-användare som har loggat in](service-admin-access-usage.md)

 - [Registrera dig för Power BI (kostnadsfritt) som enskild person](../fundamentals/service-self-service-signup-for-power-bi.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
