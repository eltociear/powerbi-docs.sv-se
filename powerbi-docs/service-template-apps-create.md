---
title: Skapa mallappar i Power BI (förhandsversion)
description: Hur du skapar mallappar i Power BI som du kan distribuera till Power BI-kunder.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: maggies
ms.openlocfilehash: c08b7e60777b720aa4fc2489b02c212bdd3e7169
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56250035"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Skapa en mallapp i Power BI (förhandsversion)

Med de nya Power BI-*mallapparna* kan Power BI-partner skapa Power BI-appar med lite eller ingen kodning och sedan distribuera dem till Power BI-kunder.  Den här artikeln innehåller stegvisa instruktioner för hur du skapar en mallapp i Power BI. 

Om du kan skapa rapporter och instrumentpaneler i Power BI kan du även bli en *mallapputvecklare* som skapar och paketerar analytiskt innehåll i en *app*. Du kan sedan distribuera appen till andra Power BI-klientorganisationer genom valfri tillgänglig plattform, till exempel AppSource, eller genom att använda den i din egen webbtjänst. Som utvecklare kan du skapa ett skyddat analyspaket för distribution. 

Power BI-klientadministratörer styr vem i organisationen som kan skapa mallappar och vem som kan installera dem. De som har behörighet kan installera din mallapp och sedan ändra den och distribuera den till Power BI-kunder i deras organisation.

## <a name="prerequisites"></a>Förutsättningar 

Här följer kraven för att skapa en mallapp:  

- En [Power BI Pro-licens](service-self-service-signup-for-power-bi.md)
- En [installation av Power BI Desktop](desktop-get-the-desktop.md) (valfritt)
- Bekanta dig med [grundläggande begrepp för Power BI ](service-basic-concepts.md)
- Behörighet att skapa en mallapp. Se [mallappinställningarna i Power BI-administratörsportalen](service-admin-portal.md#template-apps-settings-preview) för mer information.

## <a name="enable-app-developer-mode"></a>Aktivera läget för apputveckling

För att kunna skapa en mallapp som kan distribueras till andra Power BI-klienter måste du vara i läget för apputveckling. Annars skapar du bara en app för Power BI-användare i din organisation.
 
1. Öppna Power BI-tjänsten i en webbläsare.
2. Gå till **Inställningar** > **Allmänt** > **Utvecklare** > **Aktivera mallappens utvecklingsläge**.

    ![Skapa mallappar](media/service-template-apps-create/power-bi-dev-template-app.png)

    Om du inte ser det alternativet ber du Power BI-administratören ge dig [behörighet för mallapputveckling](service-admin-portal.md#template-apps-settings-preview) i administratörsportalen.

3. Välj **Tillämpa**.

## <a name="create-the-template-app-workspace"></a>Skapa en arbetsyta för mallappen

För att kunna skapa en mallapp som du kan distribuera till andra Power BI-klientorganisationer måste du skapa den i de nya apparbetsytorna. 
 
1. Välj **Arbetsytor** > **Skapa app-arbetsyta** i Power BI-tjänsten. 
 
    ![Skapa en apparbetsyta](media/service-template-apps-create/power-bi-new-workspace.png)

3. I **Skapa en app-arbetsyta**, i **Förbättrade arbetsytor i förhandsversion**, väljer du **Prova nu**.

    ![Prova nya arbetsytor](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

5. Ange ett namn, en beskrivning (valfritt) och en logotypbild (valfritt) för din apparbetsyta.

4. Välj **Utveckla en mallapp**.

    ![Utveckla en mallapp](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Välj **Spara**.

## <a name="create-the-content-in-your-template-app"></a>Skapa innehållet i din mallapp

Som med en vanlig Power BI-apparbetsyta är nästa steg att skapa innehållet på arbetsytan.  I förhandsversionen av mallapparna stöder vi bara en av varje typ: en datauppsättning, en rapport och en instrumentpanel.

- [Skapa ditt Power BI-innehåll](power-bi-creator-landing.md) på apparbetsytan.

Om du använder parametrar i Power Query måste du se till att de har korrekt definierad typ (till exempel Text). Typerna Any och Binary stöds inte. 

I [Tips för att skapa mallappar i Power BI (förhandsversion)](service-template-apps-tips.md) finns förslag på saker du kan överväga när du skapar rapporter och instrumentpaneler för din mallapp.

## <a name="create-the-test-template-app"></a>Skapa en testmallapp

Nu när du har innehåll på arbetsytan är du redo att paketera det i en mallapp. Det första steget är att skapa en testmallapp som endast är tillgänglig inom din organisation i din klientorganisation.

1. Välj **Skapa app** på arbetsytan för mallappen. 

    ![Skapa app](media/service-template-apps-create/power-bi-create-app.png)
 
    Här kan fylla du i ytterligare parametrar för din mallapp i fyra kategorier. 

    **Anpassning**

    - Appnamn 
    - Beskrivning
    - Applogotyp (valfritt)
    - Appfärg 

    **Innehåll** 

    - Applandningssida (valfritt): Ange en rapport eller instrumentpanel som ska vara landningssida för din app.  
    
    **Kontroll** 

    Bestäm flera begränsningar för vad användarna kan göra med innehållet i appen. Du kan använda den här kontrollen för att skydda immateriella rättigheter i appen.

    **Åtkomst**

    - I testfasen bestämmer du vilka personer i organisationen som ska kunna installera och testa appen.

    Oroa dig inte, du kan alltid komma tillbaka och ändra inställningarna senare.  

2. Välj **Skapa app**. 

    Ett meddelande om att testappen är klar visas med en länk som du kan kopiera och dela med apptestarna.

    ![Testappen är klar](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    Du har också gjort det första steget i versionshanteringsprocessen.

    

## <a name="manage-the-template-app-release"></a>Hantera publiceringen av mallappen

Innan du gör mallappen allmänt tillgänglig vill du försäkra dig om att den är klar. I Power BI finns ett versionshanteringsfönster där du kan följa och inspektera den fullständiga versionshanteringsvägen för appen. Du kan också utlösa övergången från steg till steg. De vanliga stegen är: 

- Skapa en testapp: endast för test inom organisationen. 
- Höj upp testpaketet till förproduktionssteget: testa utanför organisationen.
- Höj upp förproduktionspaketet till produktion: produktionsversion. 
- Ta bort alla paket eller börja om från föregående steg. 

Lås oss gå igenom stegen.

1. Välj **Versionshantering** i arbetsytan för mallappen.

    ![Versionshanteringsikon](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Välj **Skapa app**. 

    Om du skapade testappen i **Skapa testmallappen** ovan är den gula punkten bredvid **Testar** redan fylld och du behöver inte välja **Skapa app** här. Om du väljer den går du tillbaka till processen för att skapa en mallapp.
 
3. Välj **Hämta länk**.

    ![Skapa app, hämta länk](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)
 
9. Om du vill testa appinstallationsupplevelsen kopierar du länken i meddelandefönstret och klistrar in den i ett nytt webbläsarfönster. 

    Därifrån följer du samma procedur som användarna följer. Se [Installera och distribuera mallappar i organisationen](service-template-apps-install-distribute.md) om du vill se deras version.
 
10. Välj **Installera** i dialogrutan.

    När installationen är klar visas ett meddelande om att den nya appen är klar. 
 
11. Välj **Gå till app**.
 
12. I **Kom igång med din nya app** visas appen så som dina kunder kommer att se den. 

    ![Kom igång med din app](media/service-template-apps-create/power-bi-template-app-get-started.png)

13. Välj **Utforska appen** att verifiera testappen med exempeldata.

1. Om du vill göra ändringar går du tillbaka till appen i den ursprungliga arbetsytan. Gör ändringar i testappen tills du är nöjd.

9. När du är redo att flytta upp din app till förproduktion för ytterligare testning utanför din klientorganisation går du tillbaka till fönstret **Versionshantering** och väljer**Höj upp appen** bredvid **Testar**.
 
    ![Höj upp appen till förproduktion](media/service-template-apps-create/power-bi-template-app-promote.png)

11. Välj **Höj en nivå** för att bekräfta ditt val. 

12. Kopiera den nya URL:en så att du kan dela den för testning utanför din klientorganisation. Det är också den här länken du skickar för att börja distribuera din app i AppSource.

12. När appen är klar för produktion eller delning via AppSource går du tillbaka till fönstret **Versionshantering** och väljer **Höj upp appen** bredvid **Förproduktion**.
 
11. Välj **Höj en nivå** för att bekräfta ditt val. 

    Nu är din app i produktion och klar för distribution.

    ![App i produktion](media/service-template-apps-create/power-bi-template-app-production.png)

Vi rekommenderar att du skickar appen till AppSource så att den blir allmänt tillgänglig för tusentals Power BI-användare runt om i världen. Se [Power BI Application offer](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) (Power BI-programerbjudande) för mer information. 

## <a name="update-your-app"></a>Uppdatera din app

Nu när appen är i produktion kan börja du om i testfasen, utan att det påverkar appen i produktion. 

1. Välj **Skapa app** i fönstret **Versionshantering**.

1. Börja om skapandeprocessen. 
2. När du har angett **Anpassning**, **Innehåll**, **Kontroll** och **Åtkomst** väljer du **Skapa app** på nytt.
3. Välj **Stäng** och gå tillbaka till **Versionshantering**. 

    Nu kan du se att du har två versioner: Versionen som är i produktion, samt en ny version i testning. 

    ![Två versioner av en mallapp](media/service-template-apps-create/power-bi-template-app-2-versions.png)

## <a name="next-steps"></a>Nästa steg

Se hur dina kunder interagerar med din mallapp i [Installera, anpassa och distribuera mallappar i organisationen](service-template-apps-install-distribute.md).

Se [Power BI Application offer](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) (Power BI-programerbjudande) för mer information.





