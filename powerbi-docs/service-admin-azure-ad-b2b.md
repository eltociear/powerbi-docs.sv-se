---
title: Distribuera innehåll till externa gästanvändare med Azure Active Directory B2B
description: Power BI kan integreras med Azure Active Directory Business-to-business (Azure AD B2B) för att tillåta säker distribution av Power BI-innehåll till gästanvändare utanför organisationen.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: dee5c14d2ee714872409352b5e42d646e561c271
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507771"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuera Power BI-innehåll till externa gästanvändare med Azure Active Directory B2B

Power BI kan integreras med Azure Active Directory Business-to-business (Azure AD B2B) för att tillåta säker distribution av Power BI-innehåll till gästanvändare utanför organisationen, medan kontroll över interna data bibehålls.

## <a name="enable-access"></a>Aktivera åtkomst

Du måste aktivera funktionen [Inställningar för export och delning](service-admin-portal.md#export-and-sharing-settings) på Power BI-administratörsportalen innan du bjuder in gästanvändare.

## <a name="who-can-you-invite"></a>Vilka kan du bjuda in?

Du kan bjuda in gästanvändare som använder alla e-postadresser, även personliga konton som gmail.com, outlook.com och hotmail.com. I Azure AD B2B kallas de här adresserna *sociala identiteter*.

## <a name="invite-guest-users"></a>Bjud in gästanvändare

Inbjudningar krävs endast första gången en extern gästanvändare bjuds in till din organisation. Det finns två sätt att bjuda in användare: planerad inbjudan och ad hoc-inbjudan.

### <a name="planned-invites"></a>Planerad inbjudan

Använd en planerad inbjudan om du vet vilka användare du vill bjuda in. Du kan skicka inbjudan med hjälp av Azure-portalen eller PowerShell. Du måste vara klientadministratör för att bjuda in människor.

Följ dessa steg för att skicka en inbjudan i Azure-portalen.

1. Välj **Azure Active Directory** i [Azure-portalen](https://portal.azure.com).

1. Under **Hantera** går du till **Användare** > **Alla användare** > **Ny gästanvändare**.

    ![Azure Active Directory-portalen – ny gästanvändare](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. Ange en **e-postadress** och ett **personligt meddelande**.

    ![Azure Active Directory-portalen – inbjudningsmeddelande till ny gästanvändare](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. Välj **Bjud in**.

Använd PowerShell för att bjuda in fler än en gästanvändare. Mer information finns i [Azure AD B2B-samarbetskod och PowerShell-exempel](/azure/active-directory/b2b/code-samples/).

Gästanvändaren behöver välja **Kom igång** i e-postinbjudan hen tar emot. Gästanvändaren läggs sedan till i klientorganisationen.

![E-postinbjudan till gästanvändaren](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Ad hoc-inbjudningar

Utför en inbjudan när som helst genom att lägga till den externa användaren i din instrumentpanel eller rapport via delningsgränssnittet, eller din app via åtkomstsidan. Här är ett exempel på vad du gör när du bjuder in en extern användare att använda en app.

![Externa användare har lagts till i listan över appåtkomst](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

Gästanvändaren får ett e-postmeddelande som anger att appen har delats med dem.

![E-post för appen som delas med gästanvändare](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

Gästanvändaren måste logga in med sin organisations e-postadress. De uppmanas att tacka ja till inbjudan efter inloggningen. Efter inloggningen dirigeras gästanvändare om till appinnehållet. De kan märka länken med ett bokmärke eller spara e-postmeddelandet om de vill återgå till appen.

## <a name="licensing"></a>Licensiering

Gästanvändaren måste ha korrekt licensiering för att se appen som delats. Det finns tre alternativ för att åstadkomma detta: använda Power BI Premium; tilldela en licens för Power BI Pro; eller använda gästens Power BI Pro-licens.

### <a name="use-power-bi-premium"></a>Använda Power BI Premium

Genom att tilldela apparbetsytan till [Power BI Premium-kapacitet](service-premium.md) kan gästanvändaren använda appen utan att behöva en Power BI Pro-licens. Power BI Premium kan även användas för appar för att dra nytta av andra funktioner som ökade uppdateringsintervall, dedikerad kapacitet och stora modellstorlekar.

![Använda Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Tilldela Power BI Pro-licens till gästanvändaren

Genom att tilldela en Power BI Pro-licens till gästanvändaren i din klientorganisation kan gästanvändaren se innehållet i klienten.

![Tilldela Pro-licens från din klientorganisation](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>Gästanvändare tar med sin egen Power BI Pro-licens

Gästanvändaren har redan en Power BI Pro-licens i klientorganisationen.

![Gästanvändare tar med sin egen licens](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

* Externa B2B-gäster är begränsade till förbrukning av innehåll endast. Externa B2B-gäster kan visa appar, instrumentpaneler, rapporter, exportera data och skapa e-postprenumerationer för instrumentpaneler och rapporter. De kan inte komma åt arbetsytor eller publicera sitt eget innehåll.

* Den här funktionen är inte tillgänglig med Power BI-appar. Du kan visa Power BI-innehåll som delas med hjälp av Microsoft Azure Active Directory B2B i en webbläsare på en mobil enhet.

* Den här funktionen är inte tillgänglig med rapportwebbdelen för SharePoint Online i Power BI.

## <a name="next-steps"></a>Nästa steg

För mer detaljerad information, inklusive hur säkerhet på radnivå fungerar, kan du ta en titt på vitboken [distribuera Power BI-innehåll till externa gästanvändare med Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Mer information om Azure AD B2B finns i [Vad är Azure AD B2B-samarbete?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
