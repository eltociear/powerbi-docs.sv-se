---
title: Ytterligare köp kan krävas – riktlinjer för visuella objekt i Power BI
description: Läs hur du kan publicera dina anpassade visuella objekt till AppSource där andra kan upptäcka och använda dem via ett inköp.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/26/2018
ms.openlocfilehash: 92d4320026164e523297cbe48ee87ce33d9ab2f7
ms.sourcegitcommit: 796bf513bf8669676e2a44627b56221b1629a6a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56826593"
---
# <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Riktlinjer för visuella objekt i Power BI med ytterligare inköp

Tills nyligen godkände endast Marketplace (AppSource) kostnadsfria visuella objekt i Power BI. Den här principen har ändrats så att du nu även kan skicka in visuella objekt till AppSource som har pristaggen ytterligare köp kan krävas. 

Visuella objekt där ytterligare köp kan krävas liknar tillägg med in-app köp (IAP) i Office Store. Utvecklare kan också skicka in dessa visuella objekt för certifiering efter att AppSource-teamet godkänt dem och efter att de sett till att de uppfyller certifieringskraven. Mer information om kraven finns i [Certifierade anpassade visuella objekt](../power-bi-custom-visuals-certified.md).

> [!NOTE]
> * Det visuella objektet måste inte ha åtkomst till externa tjänster eller resurser för att godkännas.
> * Alla kostnadsfria visuella objekt måste behålla de kostnadsfria funktioner som tidigare erbjudits. Du kan lägga till valfria avancerade betalfunktioner utöver de tidigare kostnadsfria funktionerna. Vi rekommenderar att du skickar in visuella IAP-objekt med de avancerade funktionerna som nya visuella objekt och inte uppdaterar de tidigare kostnadsfria versionerna.


## <a name="what-changed-in-the-submission-process"></a>Vad ändras i inlämningsprocessen?

Utvecklare laddar upp sina visuella IAP-objekt till AppSource via instrumentpanelen för försäljning, precis som med kostnadsfria visuella objekt. För att visa att det inlämnade visuella objektet har IAP-funktioner så ska utvecklare skriva följande i anteckningarna i säljarens instrumentpanel: ”Visual with in-app purchase” (Visuellt objekt med köp i appen). Utvecklare måste också ange en licensnyckel eller token så att verifieringsteamet kan validera IAP-funktioner. När det visuella objektet har verifierats och godkänts anger AppSource-listningen det visuella IAP-objektet ”Ytterligare köp kan krävas” under prissättningsalternativen.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>Vad är ett visuellt Power BI-objekt med IAP-funktioner?

Ett visuellt IAP-objekt är ett kostnadsfritt visuellt objekt som erbjuder kostnadsfria funktioner. Det har även vissa avancerade funktioner kan kräva extra avgifter för att använda. I beskrivningen för det visuella objektet så måste utvecklare meddela användare om vilka funktioner som kräver ytterligare köp för att fungera. Microsoft tillhandahåller för närvarande inte inbyggda API:er för att stödja köp av appar och tilläggsprogram.

Utvecklare kan använda valfritt betalningssystem från tredje part för dessa köp. Se vår [policy för marknadsplatsen](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads) för mer information.

> [!NOTE]
> Vattenstämplar tillåts inte på de kostnadsfria funktionerna. Utvecklare kan visa ett popup-fönster eller en vattenstämpel om de avancerade betalfunktionerna används utan giltig licens.  

## <a name="logo-guidelines"></a>Riktlinjer för logotyp

I det här avsnittet beskrivs specifikationerna för att lägga till logotyper och logotyper i visuella objekt.

> [!NOTE]
> Logotyper tillåts endast i redigeringsläge. Logotyper kan inte visas i visningsläge.

![Definitioner](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![Saker att tänka på](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![Saker att undvika](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![Storlek och format](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![Marginaler och storlekar](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![Redigeringsläge](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>Metodtips

### <a name="visual-landing-page"></a>Landningssida för visuellt objekt

Använd landningssidan för att klargöra för användarna hur de kan använda ditt visuella objekt och var de kan köpa licensen. Omfattar inte videor som utlöses automatiskt. Lägg bara till material som hjälper till att förbättra användarupplevelsen som information eller länkar till hur man köper en licens och hur man använder IAP-funktioner.

### <a name="license-key-and-token"></a>Licensnyckel och token

För att underlätta för användaren så kan du lägga till licensnyckeln eller tokenrelaterade fält överst i formatfönstret.

## <a name="faq"></a>Vanliga frågor och svar

Mer information om visuella objekt finns i [Vanliga frågor och svar om visuella objekt med ytterligare köp](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases).

## <a name="next-steps"></a>Nästa steg

Läs hur du kan publicera dina anpassade visuella objekt till [AppSource](office-store.md) där andra kan upptäcka och använda dem.
