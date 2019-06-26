---
title: Skapa mallappar i Power BI (förhandsversion)
description: Hur du skapar mallappar i Power BI som du kan distribuera till Power BI-kunder.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: maggies
ms.openlocfilehash: 2dc9ae7eb7ecd82cdd6c9ea7ddbc6aa1fc70ca8b
ms.sourcegitcommit: 81ba3572531cbe95ea0b887b94e91f94050f3129
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751183"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Skapa en mallapp i Power BI (förhandsversion)

Med de nya Power BI-*mallapparna* kan Power BI-partner skapa Power BI-appar med lite eller ingen kodning och sedan distribuera dem till Power BI-kunder.  Den här artikeln innehåller stegvisa instruktioner för hur du skapar en mallapp i Power BI.

Om du kan skapa rapporter och instrumentpaneler i Power BI kan du även bli en *mallapputvecklare* som skapar och paketerar analytiskt innehåll i en *app*. Du kan distribuera appen till andra Power BI-klientorganisationer via valfri tillgänglig plattform, till exempel AppSource, eller genom att använda den i din egen webbtjänst. Som utvecklare kan du skapa ett skyddat analyspaket för distribution.

Power BI-klientadministratörer styr vem i organisationen som kan skapa mallappar och vem som kan installera dem. Användare med behörighet kan installera din mallapp och sedan ändra den och distribuera den till Power BI-kunder i sin egen organisation.

## <a name="prerequisites"></a>Förutsättningar

Här följer kraven för att skapa en mallapp:  

- En [Power BI Pro-licens](service-self-service-signup-for-power-bi.md)
- En [installation av Power BI Desktop](desktop-get-the-desktop.md) (valfritt)
- Kunskap om [grundläggande begrepp i Power BI](service-basic-concepts.md)
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

2. I **Skapa en app-arbetsyta**, i **Förbättrade arbetsytor i förhandsversion**, väljer du **Prova nu**.

    ![Prova nya arbetsytor](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

3. Ange ett namn, en beskrivning (valfritt) och en logotypbild (valfritt) för din apparbetsyta.

4. Välj **Utveckla en mallapp**.

    ![Utveckla en mallapp](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Välj **Spara**.
>[!NOTE]
>Du behöver behörighet från Power BI-administratören för att sprida mallappar.

## <a name="create-the-content-in-your-template-app"></a>Skapa innehållet i din mallapp

Som med en vanlig Power BI-apparbetsyta är nästa steg att skapa innehållet på arbetsytan.  I förhandsversionen av mallapparna stöder vi bara en av varje typ: en datauppsättning, en rapport och en instrumentpanel.

- [Skapa ditt Power BI-innehåll](power-bi-creator-landing.md) på apparbetsytan.

Om du använder parametrar i Power Query måste du se till att de har korrekt definierad typ (till exempel Text). Typerna Any och Binary stöds inte.

I [Tips för att skapa mallappar i Power BI (förhandsversion)](service-template-apps-tips.md) finns förslag på saker du kan överväga när du skapar rapporter och instrumentpaneler för din mallapp.

## <a name="create-the-test-template-app"></a>Skapa en testmallapp

Nu när du har innehåll på arbetsytan är du redo att paketera det i en mallapp. Det första steget är att skapa en testmallapp som endast är tillgänglig inom din organisation i din klientorganisation.

1. Välj **Skapa app** på arbetsytan för mallappen.

    ![Skapa app](media/service-template-apps-create/power-bi-create-app.png)

    Här fyller du i ytterligare alternativ för mallappen i fem kategorier:

    **Anpassning**

    ![Anpassning](media/service-template-apps-create/power-bi-create-branding.png)
    - Appnamn
    - Beskrivning
    - Supportwebbplats (länken visas under appinformationen när mallappen har distribuerats om som en organisationsapp)
    - Applogotyp (filen får vara max 45 kB, den ska ha bildförhållandet 1:1 och formaten .png, .jpg och .jpeg stöds)
    - Appens temafärg

    **Innehåll**

    **Applandningssida:** Definiera en rapport eller instrumentpanel som ska vara appens landningssida. Med en landningssida får användaren rätt intryck av appen:

    ![Innehåll](media/service-template-apps-create/power-bi-create-content.png)

    **Kontroll**

    Ange vilka innehållsbegränsningar som ska gälla för appanvändarna. På det här sättet kan du skydda immateriell egendom i appen.

    ![Kontroll](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >Export till .pbix-format är alltid blockerad för användare som installerar appen.

    **Parametrar**

    Använd den här kategorin till att hantera parametrarnas beteende vid anslutning till datakällor. Läs mer om att [skapa frågeparametrar](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/).

    ![Parametrar](media/service-template-apps-create/power-bi-create-parameters.png)
    - **Värde**: parameterns standardvärde.
    - **Krävs**: ange det här om den som installerar måste ange ett användarspecifikt värde.
    - **Lås**: låsning förhindrar att installationsprogrammet uppdaterar en parameter.
    - **Statisk**: aktivera om appen *endast* innehåller exempeldata. När du väljer **Statisk** uppmanas inte användaren att ansluta någon datakälla i installationsguiden.

    **Åtkomst**: under testfasen kan du avgöra vilka personer i organisationen som ska kunna installera och testa appen. Oroa dig inte, du kan alltid gå tillbaka och ändra de här inställningarna senare (inställningarna påverkar inte åtkomsten till den distribuerade mallappen).

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

Webbadressen ändras inte när du växlar mellan olika versionssteg. Upphöjning påverkar inte själva webbadressen.

Lås oss gå igenom de olika stegen:

1. Välj **Versionshantering** i arbetsytan för mallappen.

    ![Versionshanteringsikon](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Välj **Skapa app**.

    Om du skapade testappen i **Skapa testmallappen** ovan är den gula punkten bredvid **Testar** redan fylld och du behöver inte välja **Skapa app** här. Om du väljer den går du tillbaka till processen för att skapa en mallapp.

3. Välj **Hämta länk**.

    ![Skapa app, hämta länk](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)

4. Om du vill testa appinstallationsupplevelsen kopierar du länken i meddelandefönstret och klistrar in den i ett nytt webbläsarfönster.

    Därifrån följer du samma procedur som användarna följer. Se [Installera och distribuera mallappar i organisationen](service-template-apps-install-distribute.md) om du vill se deras version.

5. Välj **Installera** i dialogrutan.

    När installationen är klar visas ett meddelande om att den nya appen är klar.

6. Välj **Gå till app**.
7. I **Kom igång med din nya app** visas appen så som dina kunder kommer att se den.

    ![Kom igång med din app](media/service-template-apps-create/power-bi-template-app-get-started.png)
8. Välj **Utforska appen** att verifiera testappen med exempeldata.
9. Om du vill göra ändringar går du tillbaka till appen i den ursprungliga arbetsytan. Gör ändringar i testappen tills du är nöjd.
10. När du är redo att flytta upp appen till förproduktion för ytterligare testning utanför klientorganisationen går du tillbaka till fönstret **Versionshantering** och väljer**Höj upp appen**. 

    ![Höj upp appen till förproduktion](media/service-template-apps-create/power-bi-template-app-promote.png)

    >[!NOTE]
    > När appen höjs upp blir den allmänt tillgänglig utanför organisationen.

11. Välj **Höj en nivå** för att bekräfta ditt val.
12. Kopiera den nya URL:en så att du kan dela den för testning utanför din klientorganisation. Det är också den här länken du skickar för att börja distribuera app i AppSource genom att skapa ett [nytt Cloud Partner Portal-erbjudande](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-publish-offer). Skicka endast förproduktionslänkar till Cloud Partner Portal. När appen har godkänts och du får ett meddelande om att den publicerats i AppSource kan du flytta upp paketet till produktion i Power BI.
13. När appen är klar för produktion eller delning via AppSource går du tillbaka till fönstret **Versionshantering** och väljer **Höj upp appen** bredvid **Förproduktion**.
14. Välj **Höj en nivå** för att bekräfta ditt val.

    Nu är din app i produktion och klar för distribution.

    ![App i produktion](media/service-template-apps-create/power-bi-template-app-production.png)

Vi rekommenderar att du skickar appen till AppSource så att den blir allmänt tillgänglig för tusentals Power BI-användare runt om i världen. Se [Power BI Application offer](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) (Power BI-programerbjudande) för mer information.

## <a name="update-your-app"></a>Uppdatera din app

Nu när appen är i produktion kan börja du om i testfasen, utan att det påverkar appen i produktion.

1. Välj **Skapa app** i fönstret **Versionshantering**.
2. Börja om skapandeprocessen.
3. När du har angett **Anpassning**, **Innehåll**, **Kontroll** och **Åtkomst** väljer du **Skapa app** på nytt.
4. Välj **Stäng** och gå tillbaka till **Versionshantering**.

   Nu kan du se att du har två versioner: Versionen som är i produktion, samt en ny version i testning.

    ![Två versioner av en mallapp](media/service-template-apps-create/power-bi-template-app-2-versions.png)

5. När du är redo att flytta upp appen till förproduktion för ytterligare testning utanför klientorganisationen går du tillbaka till fönstret Versionshantering och väljer **Höj upp appen** bredvid **Testar**.
6. Länken fungerar nu. Skicka den igen till Cloud Partner Portal genom att följa stegen i [Uppdatera ett erbjudande med Power BI-appen](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).

>[!NOTE]
>Höj inte upp appen till produktion förrän den godkänts i Cloud Partner Portal och du har publicerat den.

## <a name="next-steps"></a>Nästa steg

Se hur dina kunder interagerar med din mallapp i [Installera, anpassa och distribuera mallappar i organisationen](service-template-apps-install-distribute.md).

Se [Power BI Application offer](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) (Power BI-programerbjudande) för mer information.
