---
title: Distribuera mallappar i organisationen – Power BI
description: Läs mer om att installera, anpassa och distribuera mallappar i din organisation i Power BI.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/14/2019
ms.author: tebercov
ms.openlocfilehash: 660fd7c623e8a195f937a3a2b468f758986411e1
ms.sourcegitcommit: e2de2e8b8e78240c306fe6cca820e5f6ff188944
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71195338"
---
# <a name="install-and-distribute-template-apps-in-your-organization---power-bi"></a>Installera och distribuera mallappar i organisationen – Power BI

Är du Power BI-analytiker? I så fall kan du läsa den här artikeln om att installera *mallappar* och ansluta dem till många av de tjänster du använder i verksamheten, som Salesforce, Microsoft Dynamics och Google Analytics. Du kan modifiera instrumentpaneler och rapporter enligt organisationens behov och sedan distribuera dem till dina kollegor som en *app*. 

![Installerade Power BI-appar](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Om du är intresserad av att skapa mallappar som du kan distribuera själv, kan du läsa [Skapa en mallapp i Power BI](service-template-apps-create.md). Power BI-partner kan skapa Power BI-appar nästan helt utan kodning och distribuera dem till Power BI-kunder. 

## <a name="prerequisites"></a>Förutsättningar  

Här följer kraven för att installera, anpassa och distribuera en mallapp: 

- A [Power BI Pro-licens](service-self-service-signup-for-power-bi.md)
- Bekanta dig med [grundläggande begrepp för Power BI ](service-basic-concepts.md)
- Giltigt installationslänk från den som skapat mallappen eller AppSource. 
- Behörighet att installera mallappar. 

## <a name="install-a-template-app"></a>Installera en mallapp

Du kan få en länk till en mallapp. Annars kan du söka på AppSource efter något som intresserar dig. När du har installerat appen kan du ändra den och distribuera den till din egen organisation.

### <a name="search-appsource-from-a-browser"></a>Söka i AppSource från en webbläsare

Välj den här länken i en webbläsare för att öppna AppSource filtrerat på Power BI-appar:

- https://appsource.microsoft.com/marketplace/apps?product=power-bi

### <a name="search-appsource-from-the-power-bi-service"></a>Söka på AppSource från Power BI-tjänsten

1. Välj **Appar** > **Hämta appar** i navigeringsfönstret till vänster i Power BI-tjänsten.

    ![Hämta appar](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

2. Välj **Appar** i AppSource.

    ![Söka i AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

3. Bläddra eller sök efter appen och välj sedan **Hämta nu**.

4. Välj **Installera** i dialogrutan.

    ![Installera app](media/service-template-apps-install-distribute/power-install-dialog.png)Om du har en Power BI Pro-licens installeras appen med dess tillhörande arbetsyta. Du kan anpassa appen i arbetsytan.

    När installationen är klar visas ett meddelande om att din nya app är klar.
4. Välj **Gå till app**.
5. I **Kom igång med din nya app** väljer du ett av följande tre alternativ:

    ![Kom igång med din app](media/service-template-apps-create/power-bi-template-app-get-started.png)

    - **Utforska appen**: Utforskning av data med grundläggande exempel. Börja här för att få en känsla av appen. 
    - **Anslut data**: Ändra datakällan från exempeldata till din egen datakälla. Du kan definiera om datauppsättningsparametrar och autentiseringsuppgifter för datakällan. Se [Kända begränsningar](service-template-apps-tips.md#known-limitations) i artikeln om tips för mallappar. 
    - **Gå till arbetsytan** (avancerat alternativ): du kan göra de ändringar som apputvecklaren tillåter.

    Eller så kan du hoppa över den här dialogrutan och gå direkt till den tillhörande arbetsytan via **Arbetsytor** i det vänstra navigeringsfönstret.
    >[!NOTE]
    >Vid installation av en mallapp installeras både en *organisationsapp* och en *apparbetsyta*. Läs mer om att [distribuera appar i Power BI](service-create-distribute-apps.md).
 
6. Innan du delar den med dina medarbetare ansluter du till dina egna data. Du kanske också vill ändra rapporten eller instrumentpanelen så att den passar din organisation. Du kan även lägga till andra rapporter eller instrumentpaneler i det här läget.

   Om du väljer en installationslänk för en app som inte finns i AppSource, visas dialogrutan för validering där du uppmanas att bekräfta valet.

   ![Installera app](media/service-template-apps-install-distribute/power-install-unvalidated-dialog.png)

   >[!NOTE]
   >Du måste begära behörighet från din administratör för att kunna installera mallappar som inte finns i AppSource. Se [mallappinställningarna i Power BI-administratörsportalen](service-admin-portal.md#template-apps-settings) för mer information.

## <a name="customize-and-publish-the-app"></a>Anpassa och publicera appen

När du har anpassat appen för din organisation är du redo att publicera den. Stegen är desamma som för publicering av andra appar.

1. När du är klar med anpassningen väljer du **Uppdatera app** längst upp till höger i listvyn för arbetsytan.  

    ![Starta appinstallationen](media/service-template-apps-install-distribute/power-bi-start-install-app.png)

2. I **Information** kan du ändra beskrivningen och bakgrundsfärgen.

   ![Ange beskrivning och färg för appen](media/service-template-apps-install-distribute/power-bi-install-app-details.png)

3. I **Navigering** kan du använda det nya navigeringsverktyget för appen eller välja instrumentpanelen eller rapporten för landningssidan. Se [Utforma appens navigeringsfunktion](service-create-distribute-apps.md#design-the-navigation-experience) för mer information.

   ![Ange landningssida för appen](media/service-template-apps-install-distribute/power-bi-install-app-content.png)

4. I **Åtkomst** ger du åtkomst till valda användare eller hela organisationen.  

   ![Ange åtkomst till appen](media/service-template-apps-install-distribute/power-bi-install-access.png)

5. Välj **Uppdatera app**. 

6. När den har publicerats kan du kopiera länken och dela den med de personer som du har beviljat åtkomst till. De som du delar länken med kan också se den på fliken **Min organisation** i AppSource.

## <a name="update-a-template-app"></a>Uppdatera en mallapp

Skapare av mallappar kan släppa nya versioner av sina mallappar via AppSource eller en direktlänk. När de gör de kan du uppdatera mallappen när du ominstallerar appen med samma eller en nyare version.

  >[!NOTE]
  >När du installerar en ny version skrivs alla ändringar du har gjort av rapporter och instrumentpaneler över. Om du vill behålla dina uppdaterade rapporter och instrumentpaneler kan du spara dem med ett annat namn eller på en annan plats innan du installerar.

- **Skriv över en befintlig version:** Skriver över den befintliga arbetsytan med den uppdaterade versionen av mallappen.

   ![Uppdatera mallappen](media/service-template-apps-install-distribute/power-bi-update-app-overwrite.png)

- **Installera på en ny arbetsyta:** Installerar en ny version av arbetsytan och appen som du måste konfigurera om

### <a name="overwrite-behavior"></a>Överskrivningsfunktioner

* Att skriva över uppdaterar rapporterna, instrumentpanelerna och datauppsättningen på *arbetsytan*, inte i appen. När du skriver över ändras inte appnavigeringen, konfigurationen och behörigheten.
* När du har uppdaterat arbetsytan måste du *uppdatera appen* för att tillämpa ändringar från arbetsytan till organisationsappen.
* Överskrivning behåller konfigurerade parametrar och autentisering. Efter uppdatering startar en automatisk uppdatering av datauppsättningen. Under den tiden visar organisationsappen, rapporter och instrumentpaneler gränssnittet för *exempeldata*.
  ![Exempeldata](media/service-template-apps-install-distribute/power-bi-sample-data.png)
* Vid överskrivning visas alltid exempeldata tills uppdateringen är klar. Om mallappens skapare har gjort ändringar av datauppsättningen eller parametrarna fortsätter användare av arbetsyta och appen att se gränssnittet för *exempeldata*.
* Överskrivning tar aldrig bort *nya* rapporter eller instrumentpaneler du har lagt till på arbetsytan. De ursprungliga rapporterna och instrumentpanelerna skrivs över med ändringar från den ursprungliga skaparen.

>[!IMPORTANT]
>Kom ihåg att [uppdatera appen](#customize-and-publish-the-app) efter överskrivning för att tillämpa ändringar på rapporterna och instrumentpanelen för användarna av organisationsappen.

## <a name="next-steps"></a>Nästa steg

[Skapa arbetsytor med dina kollegor i Power BI](service-create-workspaces.md)
