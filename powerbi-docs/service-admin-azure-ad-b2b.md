---
title: "Distribuera Power BI-innehåll till externa gästanvändare med Azure Active Directory B2B"
description: "Power BI kan integreras med Azure Active Directory Business-to-business (Azure AD B2B) för att tillåta säker distribution av Power BI-innehåll till gästanvändare utanför organisationen."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/14/2017
ms.author: asaxton
ms.openlocfilehash: 5dabaa09923203c31572b413f8674b76028b7483
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuera Power BI-innehåll till externa gästanvändare med Azure Active Directory B2B

Power BI kan integreras med Azure Active Directory Business-to-business (Azure AD B2B) för att tillåta säker distribution av Power BI-innehåll till gästanvändare utanför organisationen, medan kontroll över interna data bibehålls.

> [!VIDEO https://www.youtube.com/embed/xxQWEQ1NnlY]

## <a name="invite-guest-users"></a>Bjud in gästanvändare

Det finns två sätt att bjuda in gästanvändare till Power BI-klienten: planerad inbjudan eller ad hoc-inbjudan. Inbjudningar krävs endast första gången en extern användare bjuds in till din organisation.

### <a name="planned-invites"></a>Planerad inbjudan

En planerad inbjudan utförs i Microsoft Azure Portal i Azure AD eller med hjälp av PowerShell. Det här är alternativet du ska använda om du vet vilka användare som ska bjudas in. 

**För att skapa gästanvändare i Azure Active Directory-portalen måste du vara innehavaradministratör.**

1. Gå till [Azure Portal](https://portal.azure.com) och välj **Azure Active Directory**.

2. Gå till **Användare och grupper** > **Alla användare** > **Nya gästanvändare**.

    ![Azure Active Directory-portalen – ny gästanvändare](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

3. Ange **e-postadress** och **personligt meddelande**.

    ![Azure Active Directory-portalen – inbjudningsmeddelande till ny gästanvändare](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

4. Välj **Bjud in**.

Använd PowerShell för att bjuda in fler än en gästanvändare. Mer information finns i [Azure Active Directory B2B-samarbetskod och PowerShell-exempel](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-code-samples).

Gästanvändaren behöver välja **Kom igång** i e-postinbjudan hen tar emot. Gästanvändaren läggs sedan till i klientorganisationen.

![E-postinbjudan till gästanvändaren](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Ad hoc-inbjudningar

Om du vill göra en inbjudan när som helst, lägger du till den externa användaren i åtkomstlistan för en app när du publicerar den.

![Externa användare har lagts till i listan över appåtkomst](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

Gästanvändaren får ett e-postmeddelande som anger att appen har delats med dem.

![E-post för appen som delas med gästanvändare](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

Gästanvändaren måste logga in med sin organisations e-postadress. De uppmanas att tacka ja till inbjudan efter inloggningen. Efter inloggningen dirigeras gästanvändare om till appinnehållet. Märk länken med ett bokmärke eller spara e-postmeddelandet om du vill återgå till appen.

## <a name="licensing"></a>Licensiering

Gästanvändaren måste ha korrekt licensiering för att se appen som delats. Det finns tre alternativ att åstadkomma detta.

### <a name="use-power-bi-premium"></a>Använda Power BI Premium

Genom att tilldela app-arbetsytan till Power BI Premium-kapacitet kan gästanvändaren använda appen utan att behöva en Power BI Pro-licens. Power BI Premium kan även användas för appar för att dra nytta av andra funktioner som ökade uppdateringsintervall, dedikerad kapacitet och stora modellstorlekar.

![Använda Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-power-bi-pro-license-to-guest-user"></a>Tilldela Power BI Pro-licens till gästanvändaren

Genom att tilldela en Power BI Pro-licens till gästanvändaren i din klientorganisation kan gästanvändaren se innehållet.

> [!NOTE]
> En Power BI Pro-licens från din klientorganisation används endast för gästanvändare när de har åtkomst till innehåll i din klientorganisation.

![Tilldela Pro-licens från din klientorganisation](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>Gästanvändare tar med sin egen Power BI Pro-licens

Gästanvändaren har redan en Power BI Pro-licens i klientorganisationen.

![Gästanvändare tar med sin egen licens](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="next-steps"></a>Nästa steg

Mer detaljerad information, inklusive hur säkerhet på radnivå fungerar, hittar du i [white paper](https://aka.ms/powerbi-b2b-whitepaper).

Mer information om Azure Active Directory B2B finns i [Vad är Azure AD B2B-samarbete?](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b)