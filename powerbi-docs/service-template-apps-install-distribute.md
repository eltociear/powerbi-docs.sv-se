---
title: Installera och distribuera mallappar i organisationen – Power BI
description: Läs mer om att installera, anpassa och distribuera mallappar i din organisation i Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 03/15/2020
ms.author: painbar
ms.openlocfilehash: 08aadc3027c5b265194e4239b150ea5d27fe2e43
ms.sourcegitcommit: abc8419155dd869096368ba744883b865c5329fa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436121"
---
# <a name="install-and-distribute-template-apps-in-your-organization"></a>Installera och distribuera mallappar i organisationen

Är du Power BI-analytiker? I så fall kan du läsa den här artikeln om att installera [mallappar](service-template-apps-overview.md) och ansluta dem till många av de tjänster du använder i verksamheten, som Salesforce, Microsoft Dynamics och Google Analytics. Du kan sedan modifiera mallappens inbyggda instrumentpanel och rapporter enligt organisationens behov och sedan distribuera dem till dina kollegor som [appar](consumer/end-user-apps.md). 

![Installerade Power BI-appar](media/service-template-apps-install-distribute/power-bi-get-apps.png)

Om du är intresserad av att skapa mallappar som du själv kan distribuera utanför organisationen, kan du läsa [Skapa en mallapp i Power BI](service-template-apps-create.md). Power BI-partner kan skapa Power BI-appar nästan helt utan kodning och distribuera dem till Power BI-kunder. 

## <a name="prerequisites"></a>Förutsättningar  

Om du vill installera, anpassa och distribuera en mallapp behöver du: 

* En [Power BI Pro-licens](service-self-service-signup-for-power-bi.md).
* Behörighet att installera mallappar på klientorganisationen.
* En giltig installationslänk för appen, som du får antingen från AppSource eller från appskaparen.
* Kunskap om [grundläggande begrepp i Power BI](service-basic-concepts.md).

## <a name="install-a-template-app"></a>Installera en mallapp

1. Välj **Appar** > **Hämta appar** i navigeringsfönstret i Power BI-tjänsten.

    ![Hämta appar](media/service-template-apps-install-distribute/power-bi-get-apps-arrow.png)

1. I AppSource-fönstret som visas väljer du **Appar**. Bläddra eller sök efter appen du vill använda och välj sedan **Hämta nu**.

    ![Söka i AppSource](media/service-template-apps-install-distribute/power-bi-appsource.png)

1. I dialogrutan som visas väljer du **Installera**.

    ![Installera app](media/service-template-apps-install-distribute/power-install-dialog.png)
    
    Appen installeras med en associerad arbetsyta. **Om du bestämmer dig för att anpassa appen gör du det i den associerade arbetsytan**.

    > [!NOTE]
    > Om du använder en installationslänk för en app som inte finns i AppSource, visas dialogrutan för validering där du uppmanas att bekräfta valet.
    >
    >För att kunna installera en mall som inte visas i AppSource, måste du begära relevanta behörigheter från din administratör. Se [Mallappinställningar](service-admin-portal.md#template-apps-settings) i Power BI-administratörsportalen för mer information.

    När installationen har slutförts visas ett meddelande som anger att din nya app är klar.

    ![Gå till app](media/service-template-apps-install-distribute/power-bi-go-to-app.png)

## <a name="connect-to-data"></a>Ansluta till data

1. Välj **Gå till app**. Fönstret **Kom igång med din nya app** visas.

   ![Kom igång med din app](media/service-template-apps-install-distribute/power-bi-template-app-get-started.png)

1. Klicka på **Anslut**.
    
    Då öppnas en dialogruta eller serie med dialogrutor där du kan ändra datakällan från exempeldata till din egen datakälla. Det betyder vanligtvis att du definierar om datauppsättningsparametrar och autentiseringsuppgifter för datakällan. Se [Kända begränsningar](service-template-apps-tips.md#known-limitations).
    
    I exemplet nedan involverar anslutningen till data två dialogrutor.

   ![Dialogrutor för Anslut till data](media/service-template-apps-install-distribute/power-bi-template-app-connect-to-data-dialogs.png)

    När du har fyllt i anslutningsdialogrutorna startar anslutningsprocessen. En banderoll informerar dig om att du visar exempeldata.

    ![Visar exempeldata](media/service-template-apps-install-distribute/power-bi-template-app-viewing-sample-data.png)

    Vänta tills data har anslutits och uppdaterats. Om du vill veta när den här processen är avslutad tittar du på förloppsindikatorn på datauppsättningsraden (nytt utseende) eller fliken (gammalt utseende).

   När anslutningen och datauppdateringen är klar ska du uppdatera webbläsaren. Banderollen informerar nu om att du behöver uppdatera appen för att tillämpa de ändringar du gör i appen och för att dela den.

    ![Anpassa och dela appen](media/service-template-apps-install-distribute/power-bi-template-app-customize-share.png)

## <a name="customize-and-share-the-app"></a>Anpassa och dela appen

När du har uppdaterat webbläsaren efter anslutning till data och datauppdatering, ser du nu arbetsytan som är associerad med appen. Nu kan du redigera alla artefakter där, precis som i alla arbetsytor. Kom dock ihåg att alla ändringar du gör kommer att skrivas över när du uppdaterar appen med en ny version, om du inte sparar de objekt som du har ändrat under olika namn. [Se information om att skriva över](#overwrite-behavior).

Information om hur du redigerar artefakter i arbetsytan finns i
* [Upptäck rapportredigeraren i Power BI](service-the-report-editor-take-a-tour.md)
* [Grundläggande begrepp för designers i Power BI-tjänsten](service-basic-concepts.md)

När du har gjort alla ändringar du vill för artefakterna i arbetsytan är du redo att publicera och dela appen. Se [Publicera din app](service-create-distribute-apps.md#publish-your-app) för att lära dig hur du gör detta.

## <a name="update-a-template-app"></a>Uppdatera en mallapp

Då och då släpper skapare av mallappar nya förbättrade versioner av sina mallappar, antingen via AppSource, direktlänk eller både och.

Om du ursprungligen laddade ned appen från AppSource, och en ny version av mallappen blir tillgänglig, visas en uppdateringsbanderoll i Power BI-tjänsten som informerar dig om att en ny appversion är tillgänglig.

  ![Uppdateringsmeddelande för mallapp](media/service-template-apps-install-distribute/power-bi-new-app-version-notification.png)

>[!NOTE]
>Om du ursprungligen fick appen via direktlänk i stället för via AppSource, kan du bara få reda på om en ny version är tillgänglig genom att kontakta skaparen av mallappen.

  Om du vill installera uppdateringen klickar du antingen på **Hämta** i meddelandebanderollen, eller söker efter appen igen i AppSource och väljer **Hämta nu**. Om du har en direktlänk för uppdateringen från den som skapat mallappen, klickar du bara på länken.
  
  Du får en fråga om du vill skriva över den aktuella versionen eller installera den nya versionen i en ny arbetsyta. Överskrivning är valt som standard.

  ![Uppdatera mallappen](media/service-template-apps-install-distribute/power-bi-update-app-overwrite.png)

- **Skriv över en befintlig version:** Skriver över den befintliga arbetsytan med den uppdaterade versionen av mallappen. [Se information om att skriva över](#overwrite-behavior).

- **Installera på en ny arbetsyta:** Installerar en ny version av arbetsytan och appen som du måste konfigurera om (det vill säga ansluta till data, definiera navigering och behörigheter).

### <a name="overwrite-behavior"></a>Överskrivningsfunktioner

* Att skriva över uppdaterar rapporterna, instrumentpanelerna och datauppsättningen på arbetsytan, inte i appen. När du skriver över ändras inte appnavigeringen, konfigurationen och behörigheterna.
* När du har uppdaterat arbetsytan **måste du uppdatera appen för att tillämpa ändringar från arbetsytan till appen**.
* Överskrivning behåller konfigurerade parametrar och autentisering. Efter uppdatering startar en automatisk uppdatering av datauppsättningen. **Under uppdateringen visas exempeldata i appen, rapporterna och på instrumentpanelerna**.

  ![Exempeldata](media/service-template-apps-install-distribute/power-bi-sample-data.png)

* Vid överskrivning visas alltid exempeldata tills uppdateringen är klar. Om mallappens skapare har gjort ändringar i datauppsättningen eller parametrarna kommer användare av arbetsytan och appen inte att se nya data förrän uppdateringen är klar. I stället kommer de fortfarande att se exempeldata under den här tiden.
* Överskrivning tar aldrig bort nya rapporter eller instrumentpaneler som du har lagt till i arbetsytan. De ursprungliga rapporterna och instrumentpanelerna skrivs endast över med ändringar från den ursprungliga skaparen.

>[!IMPORTANT]
>Kom ihåg att [uppdatera appen](#customize-and-share-the-app) efter överskrivning för att tillämpa ändringar på rapporterna och instrumentpanelen för användarna av organisationsappen.

## <a name="next-steps"></a>Nästa steg

[Skapa arbetsytor med dina kollegor i Power BI](service-create-workspaces.md)
