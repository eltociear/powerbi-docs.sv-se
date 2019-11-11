---
title: Konfigurera mobilappar med Microsoft Intune
description: Så här konfigurerar du Power BI-mobilappar med Microsoft Intune. Detta omfattar att lägga till och distribuera programmet. Och hur du skapar den mobila programprincipen för att kontrollera säkerheten.
author: mgblythe
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: abbbceb6734ecb70469efa198b6e85fce4c3e840
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73857354"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>Konfigurera mobilappar med Microsoft Intune

Microsoft Intune låter organisationer hantera enheter och program. Power BI-mobilappar för iOS och Android integreras med Intune. Med den här integrationen kan du hantera program på dina enheter och kontrollera säkerheten. Genom konfigurationsprinciper kan du kontrollera objekt och kräva en PIN-kod för åtkomst, styra hur data hanteras av programmet och även kryptera programdata när appen inte används.

## <a name="general-mobile-device-management-configuration"></a>Konfiguration av allmän mobilenhetshantering

Den här artikeln förutsätter att Intune är korrekt konfigurerat och att du har enheter som registrerats med Intune. Den här artikeln är inte avsedd som en fullständig konfigurationsguide för Microsoft Intune. Mer information om Intune finns i [Vad är Intune?](/intune/introduction-intune/).

Microsoft Intune kan finnas tillsammans med hantering av mobilenheter (MDM) i Office 365. Om du använder MDM visar enheten registrerade inom MDM, men är tillgänglig för hantering i Intune.

> [!NOTE]
> När du har konfigurerat Intune stängs datauppdateringar i bakgrunden av för Power BI-mobilappen på din iOS- eller Android-enhet. När du använder appen uppdaterar Power BI data från Power BI-tjänsten på webben.

## <a name="step-1-get-the-url-for-the-application"></a>Steg 1: Hämta URL:en för programmet

Innan vi skapar programmet i Intune måste vi hämta URL:er för apparna. För iOS får vi detta från iTunes. För Android, kan du få det från Power BI-mobilsidan.

Spara URL:en då du kommer att behöva den när vi skapar programmet.

### <a name="get-ios-url"></a>Hämta iOS-URL

Om du vill hämta appens URL för iOS måste du hämta den från iTunes.

1. Öppna iTunes.

1. Sök efter *Power BI*.

1. Du bör se **Microsoft Power BI** listat under **iPhone-appar** och **iPad-appar**. Du kan använda vilken som eftersom de ger samma URL.

1. Välj listrutan **hämta** och välj **kopiera länk**.

    ![URL för iTunes-app](media/service-admin-mobile-intune/itunes-url.png)

Det bör se ut ungefär så här: *https://itunes.apple.com/us/app/microsoft-power-bi/id929738808?mt=8* .

### <a name="get-android-url"></a>Hämta Android-URL

Du kan hämta URL:en för Google Play från [Power BI-mobilsidan](https://powerbi.microsoft.com/mobile/). Välj ikonen **Hämta från Google Play** så kommer du till appsidan. Du kan kopiera URL:en från adressfältet i webbläsaren. Det bör se ut ungefär så här: *https://play.google.com/store/apps/details?id=com.microsoft.powerbim* .

## <a name="step-2-create-a-mobile-application-management-policy"></a>Steg 2: Skapa en hanteringsprincip för mobilprogram

Principen för hantering av mobilprogram låter dig framtvinga sådant som en PIN-kod för åtkomst. Du kan skapa en i Intune-portalen.

Du kan skapa programmet eller principen först. Den ordning som de läggs till spelar ingen roll. Bägge två måste endast finnas för distributionssteget.

1. Välj **Princip** > **konfigurationsprinciper** på Intune-portalen.

    ![Intune-portalen](media/service-admin-mobile-intune/intune-policy.png)

1. Välj **Lägg till...** .

1. Under **programvara** kan du välja hantering av mobilprogram för Android eller iOS. Om du vill komma igång snabbt, kan du välja **skapa en princip med de rekommenderade inställningarna**, eller så kan du skapa en anpassad princip.

1. Redigera principen för att konfigurera de begränsningar du vill ha på programmet.

## <a name="step-3-create-the-application"></a>Steg 3: Skapa programmet

Programmet är en referens eller ett paket, som sparas i Intune för distribution. Vi behöver skapa ett program och referera till den app-URL som vi fick från Google Play eller iTunes.

Du kan skapa programmet eller principen först. Den ordning som de läggs till spelar ingen roll. Bägge två måste endast finnas för distributionssteget.

1. Gå till Intune-portalen och välj **appar** i den vänstra menyn.

1. Välj **lägg till app**. Det här startar programmet **lägg till programvara**.

### <a name="create-for-ios"></a>Skapa för iOS

1. Välj **hanterad iOS-App från App Store** i listrutan.

1. Ange den app-URL som vi fick från [Steg 1](#step-1-get-the-url-for-the-application) och välj **Nästa**.

    ![Programvaruinstallation: iOS](media/service-admin-mobile-intune/intune-add-software-ios1.png)

1. Ange **Publicerare**, **Namn** och **Beskrivning**. Du kan också bifoga en **ikon**. **Kategori** är för företagsportalappen. När du är klar, väljer du **Nästa**.

1. Du kan välja om du vill publicera appen som **alla** (standard), **iPad** eller **iPhone**. Som standard visas **alla** och den kommer att fungera för båda typer av enheter. Power BI-appen har samma URL för både iPhone och iPad. Välj **Nästa**.

1. Välj **Överför**.

1. Om du inte ser appen i listan bör du uppdatera sidan: Gå till **Översikt** och därefter tillbaka till **Appar**.

    ![Fliken appar](media/service-admin-mobile-intune/intune-add-software-ios2.png)

### <a name="create-for-android"></a>Skapa för Android

1. Välj **extern länk** i listrutan.

1. Ange den app-URL som vi fick från [Steg 1](#step-1-get-the-url-for-the-application) och välj **Nästa**.

    ![Programvaruinstallation: Android](media/service-admin-mobile-intune/intune-add-software-android1.png)

1. Ange **Publicerare**, **Namn** och **Beskrivning**. Du kan också bifoga en **ikon**. **Kategori** är för företagsportalappen. När du är klar, väljer du **Nästa**.

1. Välj **Överför**.

1. Om du inte ser appen i listan bör du uppdatera sidan: Gå till **Översikt** och därefter tillbaka till **Appar**.

    ![Fliken appar](media/service-admin-mobile-intune/intune-add-software-android2.png)

## <a name="step-4-deploy-the-application"></a>Steg 4: Distribuera programmet

När du har lagt till programmet, behöver du distribuera det så att det finns tillgängligt för dina slutanvändare. Detta är steget där du ska binda principen du skapade med appen.

### <a name="deploy-for-ios"></a>Distribuera för iOS

1. Välj den app som du skapade på Appar-skärmen. Välj sedan länken **Hantera distribution...** .

    ![Hantera distribuering](media/service-admin-mobile-intune/intune-deploy-ios1.png)

1. På skärmen **Välj grupper** kan du välja vilka grupper som du vill distribuera den här appen till. Välj **Nästa**.

1. På skärmen **Distributionsåtgärd** kan du välja hur du vill distribuera den här appen. Om du väljer **Tillgänglig installation** eller **Nödvändig installation** blir appen tillgänglig i företagsportalen för användare att installera på begäran. När du är klar med ditt val väljer du **Nästa**.

    ![Distributionsåtgärd](media/service-admin-mobile-intune/intune-deploy-ios2.png)

1. På skärmen **Hantering av mobilappar** väljer du den princip för hantering av mobilappar som vi skapade i [Steg 2](#step-2-create-a-mobile-application-management-policy). Det kommer som standard vara den princip som du skapade, om det är den enda iOS-principen som finns tillgänglig. Välj **Nästa**.

    ![Hantering av mobilappar](media/service-admin-mobile-intune/intune-deploy-ios3.png)

1. På skärmen **VPN-profil**, kan du välja en princip om du har en för din organisation. Som standard används **Ingen**. Välj **Nästa**.

1. På skärmen **konfiguration av mobilapp**, kan du välja en **appkonfigurationsprincip** om du har skapat en sådan. Som standard används **Ingen**. Det här krävs inte. Välj **Slutför**.

När du har distribuerat appen, bör du se **Ja** för distribuerad på appsidan.

### <a name="deploy-for-android"></a>Distribuera för Android

1. Välj den app som du skapade på Appar-skärmen. Välj sedan länken **Hantera distribution...** .

    ![Hantera distribuering](media/service-admin-mobile-intune/intune-deploy-android1.png)
1. På skärmen **Välj grupper** kan du välja vilka grupper som du vill distribuera den här appen till. Välj **Nästa**.

1. På skärmen **Distributionsåtgärd** kan du välja hur du vill distribuera den här appen. Om du väljer **Tillgänglig installation** eller **Nödvändig installation** blir appen tillgänglig i företagsportalen för användare att installera på begäran. När du är klar med ditt val väljer du **Nästa**.

    ![Distributionsåtgärd](media/service-admin-mobile-intune/intune-deploy-android2.png)

1. På skärmen **Hantering av mobilappar** väljer du den princip för hantering av mobilappar som vi skapade i [Steg 2](#step-2-create-a-mobile-application-management-policy). Det kommer som standard vara den princip som du skapade, om det är den enda Android-principen som finns tillgänglig. Välj **Slutför**.

    ![Hantering av mobilappar](media/service-admin-mobile-intune/intune-deploy-android3.png)

När du har distribuerat appen, bör du se **Ja** för distribuerad på appsidan.

## <a name="step-5-install-the-application-on-a-device"></a>Steg 5: Installera programmet på en enhet

Du installerar programmet via *företagsportalappen*. Om du inte har installerat företagsportalen, kan du hämta den via App Store på iOS- eller Android-plattformar. Du loggar in på företagsportalen med din organisations inloggning.

1. Öppna företagsportalappen.

1. Om du inte ser Power BI-appen listad som en viktig app, väljer du **företagsappar**.

    ![Företagsappar](media/service-admin-mobile-intune/intune-companyportal1.png)

1. Välj den Power BI-app som du har distribuerat.

    ![Power BI-app](media/service-admin-mobile-intune/intune-companyportal2.png)

1. Välj **installera**.

    ![Installera app](media/service-admin-mobile-intune/intune-companyportal3.png)

1. Om du är på iOS, pushas appen till dig. Välj **installera** i push-dialogrutan.

    ![Appinstallation](media/service-admin-mobile-intune/intune-companyportal5.png)

1. När appen har installerats ser du att den är **hanterad av ditt företag**. Om du har aktiverat åtkomst med en PIN-kod i principen, ser du följande.

    ![Ange PIN-kod](media/service-admin-mobile-intune/intune-powerbi-pin.png)

## <a name="next-steps"></a>Nästa steg

[Konfigurera och distribuera hanteringsprinciper för mobilprogram i Microsoft Intune-konsolen](/intune/app-protection-policies/)  

[Power BI-appar för mobila enheter](consumer/mobile/mobile-apps-for-mobile-devices.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)  
