---
title: Använda en alternativ e-postadress
description: Använda en alternativ e-postadress
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 41b3a0b1032616045b854e4a4776ba82bffffe47
ms.sourcegitcommit: 0611860a896e636ceeb6e30ce85243bfd8e7b61d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2018
ms.locfileid: "50909436"
---
# <a name="using-an-alternate-email-address"></a>Använda en alternativ e-postadress

När du registrerar dig för Power BI kan du ange en e-postadress. Som standard använder Power BI den här adressen för att skicka uppdateringar om aktivitet i tjänsten. Om någon skickar en inbjudan skickas den till den här adressen.

I vissa fall vill du kanske att dessa e-postmeddelanden ska skickas till en alternativ e-postadress istället för den du registrerade dig med. Den här artikeln förklarar hur du anger en alternativ e-postadress i Office 365 och i PowerShell. Den här artikeln beskriver också hur en e-postadress matchas i Azure Active Directory (AD Azure).

> [!NOTE]
> Om du anger en alternativ adress påverkas inte vilken e-postadress som använder Power BI för uppdateringar av tjänsten, nyhetsbrev och andra erbjudanden.  Dessa meddelanden skickas alltid till den e-postadress som du använde när du registrerade dig för Power BI.

## <a name="use-office-365"></a>Använda Office 365

Följ dessa steg om du vill ange en alternativ e-postadress i Office 365.

1. Öppna [sidan personlig information i Office 365](https://portal.office.com/account/#personalinfo). Logga in med din e-postadress och lösenord för Power BI om du uppmanas.

1. På menyn till vänster väljer du **Personlig information**.

1. Klicka på **Redigera** på området **kontaktinformation**.

    Om du inte redigerar din information innebär det att din e-postadress hanteras av din Office 365-administratör. Kontakta administratören om du vill uppdatera din e-postadress.

    ![Kontaktinformation](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. Ange den e-postadress som du vill att Power BI-uppdateringar ska skickas till i fältet **Alternativ e-postadress**.

## <a name="use-powershell"></a>Använd PowerShell

Om du vill ange en alternativ e-postadress i PowerShell använder du kommandot [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/).

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>E-postadressmatchning i Azure AD

När du samlar in en Azure AD-inbäddningstoken för Power BI kan du använda tre olika typer av e-postadresser:

* Den huvudsakliga e-postadressen som är kopplad till en användares Azure AD-konto

* UPN-e-postadressen (UserPrincipalName)

* Matrisattributet för *den andra e-postadressen*

Power BI väljer vilken e-postadress som ska användas baserat på följande sekvens:

1. Om e-postattributet i Azure AD-klientens användarobjekt finns använder Power BI det e-postattributet för e-postadressen.

1. Om UPN-e-postadressen *inte* finns inom domänen **\*.onmicrosoft.com** (informationen efter \@-symbolen) använder Power BI det e-postattributet för e-postadressen.

1. Om matrisattributet för *annan e-postadress* i Azure AD-användarobjektet finns används den första e-postadressen i den listan (eftersom det kan finnas en lista över e-postadresser i det här attributet).

1. Om inget av ovanstående villkor uppfylls används UPN-adressen.

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

