---
title: Riktlinjer för visuella objekt för Power BI
description: Läs hur du kan publicera dina anpassade visuella objekt till Microsoft AppSource där andra kan upptäcka och använda dem via ett inköp.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 08/12/2020
ms.openlocfilehash: c9d6b10c05ac3e19c5ebdcb5a0f3a1ab9b989a10
ms.sourcegitcommit: 64139587061136a43c5aea3b6db4d1a94e4e7795
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/14/2020
ms.locfileid: "88204946"
---
# <a name="guidelines-for-power-bi-visuals"></a>Riktlinjer för visuella objekt för Power BI
Innan du [publicerar](office-store.md) ditt visuella Power BI-objekt till Microsoft AppSource så att andra kan upptäcka och använda det ska du se till att följa riktlinjerna så att användarna får en bra upplevelse.

## <a name="power-bi-visuals-with-additional-purchases"></a>Visuella Power BI-objekt med ytterligare köp

Du kan skicka in kostnadsfria visuella Power BI-objekt till Marketplace (Microsoft AppSource). Du kan även skicka in visuella Power BI-objekt till Microsoft AppSource som har en ”Ytterligare köp kan krävas”-prislapp. Visuella Power BI-objekt med prislappen ”Ytterligare köp kan krävas” liknar tillägg med köp via app (IAP) i Office Store. 

Som med kostnadsfria visuella Power BI-objekt kan även visuella Power BI-objekt med köp via app certifieras. Innan du skickar ditt visuella Power BI-objekt med köp via app för certifiering måste du försäkra dig om att det uppfyller [certifieringskraven](power-bi-custom-visuals-certified.md).

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>Vad är ett visuellt Power BI-objekt med IAP-funktioner?

Ett visuellt Power BI-objekt med köp via app är ett *kostnadsfritt* visuellt objekt som erbjuder *kostnadsfria funktioner*. Det har även vissa avancerade funktioner som kan kräva extra avgifter. I beskrivningen för det visuella Power BI-objektet måste utvecklare informera användarna om vilka funktioner som kräver ytterligare köp för att fungera. Microsoft tillhandahåller för närvarande inte inbyggda API:er för att stödja köp av appar och tilläggsprogram.

Utvecklare kan använda valfritt betalningssystem från tredje part för dessa köp. Se vår [policy för marknadsplatsen](https://docs.microsoft.com/legal/marketplace/certification-policies#11002-displaying-ads) för mer information.


>[!IMPORTANT]  
> Om du uppdaterar ditt visuella Power BI-objekt från kostnadsfritt till ”Ytterligare köp kan krävas” måste användarna få samma nivå av kostnadsfria funktioner som före uppdateringen. Du kan lägga till valfria avancerade betalfunktioner utöver de tidigare kostnadsfria funktionerna.

### <a name="watermarks"></a>Vattenstämplar

Du kan använda vattenstämplar så att kunderna kan fortsätta använda avancerade funktioner för köp via app utan att betala. 

Vattenstämplar kan användas för att demonstrera alla funktioner i det visuella Power BI-objektet före ett köp. 

* Vattenstämplar kan bara användas på betalda funktioner som används utan giltig licens.
* Vattenstämplar är inte tillåtna i virtuella Power BI-objekt som har en *kostnadsfri* prislapp.
* Vattenstämplar är inte tillåtna i visuella objekt med köp via app när användaren använder kostnadsfria funktioner. 

### <a name="pop-up-window"></a>Popup-fönster

Du kan använda ett popup-fönster för att förklara hur man köper en licens när en ogiltig (eller utgången) licens används med ditt visuella Power BI-objekt med köp via app.

### <a name="submission-process"></a>Insändningsprocess

Följ [sändningsprocessen](office-store.md#submitting-to-appsource) och gå sedan till fliken *produktkonfiguration* och markera kryssrutan *Produkten kräver köp av en tjänst*.

När det visuella Power BI-objektet har verifierats och godkänts står det ”Ytterligare köp kan krävas” under priset för det visuella Power BI-objektet med köp via app i Microsoft AppSource.

## <a name="context-menu"></a>Snabbmeny
Snabbmenyn är den högerklicksmeny som visas när användaren hovrar över ett visuellt objekt.
Alla visuella Power BI-objekt bör aktivera snabbmenyn för att ge en enhetlig upplevelse.
Information om hur du lägger till en snabbmeny finns i [den här artikeln](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md).

>[!div class="mx-imgBorder"]
>![En skärmbild av en visuell snabbmeny i Power BI.](media/guidelines-powerbi-visuals/context-menu.png)

## <a name="commercial-logo"></a>Kommersiell logotyp
I det här avsnittet beskrivs specifikationerna för att lägga till kommersiella logotyper i visuella Power BI-objekt. Kommersiella logotyper är inte obligatoriska. Om de läggs till måste de följa dessa riktlinjer.

> [!NOTE]
> * I den här artikeln avser ”kommersiell logotyp” valfri kommersiell företagsikon enligt beskrivningen i bilderna nedan.
> * Microsofts kommersiella logotyp används endast som exempel i den här artikeln. Använd din egen kommersiella logotyp med visuella Power BI-objekt.

> [!IMPORTANT]
> Kommersiella logotyper tillåts *endast i redigeringsläge*. Kommersiella logotyper *kan inte* visas i visningsläge.

### <a name="commercial-logo-type"></a>Kommersiell logotyp

Det finns tre typer av kommersiella logotyper:
* **Textlogotyp** – en textlogotyp består av två element som sitter ihop (en ikon och ett namn).

    ![En skärmbild av Microsoft-logotypen.](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **Symbol** – en bild utan text.

    ![En skärmbild av Microsoft-symbolen.](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **Logotyp** – en logotyp utan ikon, som endast består av text.

    ![En skärmbild av Microsoft-logotypen utan ikon.](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>Kommersiell logotypfärg

När du använder en kommersiell logotyp måste färgen på logotypen vara grå (hexkoden #C8C8C8). Lägg inte till effekter som övertoningar till den kommersiella logotypen.

* **Logotyp**

    ![En skärmbild av Microsoft-logotypen i grått.](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **Symbol** – en bild utan text.

    ![En skärmbild av Microsoft-symbolen i grått.](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **Logotyp** – en logotyp utan ikon, som endast består av text.

    ![En skärmbild av Microsoft-logotypen utan ikon i grått.](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * Om ditt visuella Power BI-objekt innehåller en bild kan du överväga att lägga till en vit bakgrund (med marginaler på 10 px) för din logotyp.
> * Överväg att lägga till skugga för din logotyp (30 % ogenomskinlig svart).

### <a name="commercial-logo-size"></a>Storlek på kommersiell logotyp

Ett visuellt Power BI-objekt måste ha två kommersiella logotyper, en för stora paneler och en för små paneler. Placera logotypen i en avgränsningsruta i det övre eller nedre högra hörnet, med marginaler på 4 px.

I följande tabell beskrivs storleksöverväganden för visuella Power BI-objekt.

|Inställningar  |Litet visuellt Power BI-objekt  |Stort visuellt Power BI-objekt  |
|---------|---------|---------|
|*Logotypens bredd*    |Upp till 240 px         |Större än 240 px         |
|*Logotypens höjd*     |Upp till 160 px         |Större än 160 px         |
|*Storlek på avgränsningsruta*     |40 x 15 px         |101 x 30 px         |
|*Exempel på kommersiell logotyp*     |![En skärmbild av en mindre version av Microsofts kommersiella logotyp.](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![En skärmbild av Microsofts kommersiella logotyp.](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|*Exempel på en avgränsningsruta*    |![En skärmbild av måtten för en liten logotyp.](media/guidelines-powerbi-visuals/small-logo-box.png)         |![En skärmbild av måtten för en stor logotyp.](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>Beteende för kommersiell logotyp

Kommersiella logotyper är endast tillåtna i redigeringsläge. En kommersiell logotyp kan den endast ha följande funktioner vid klick:

* Vid klick på den kommersiella logotypen omdirigeras användaren till din webbplats.

* Vid klick på den kommersiella logotypen öppnas ett popup-fönster med ytterligare information. Popup-fönstret ska vara indelat i två delar:
    * Ett marknadsföringsutrymme som kan omfatta den kommersiella logotypen, ett visuellt objekt och marknadsomdömen.
    * Ett informationsutrymme som kan innehålla information och länkar.    


### <a name="things-to-avoid"></a>Saker att undvika

* Kommersiella logotyper kan inte visas i visningsläge.

* En animerad kommersiell logotyp kan visa en animering i högst fem sekunder.

* Om det visuella Power BI-objektet innehåller informativa ikoner (i) i läsläge bör de överensstämma med färgen, storleken och platsen för den kommersiella logotypen, enligt beskrivningen ovan.

* Undvik en färgad eller svart kommersiell logotyp. Den kommersiella logotypen måste vara grå (hexkoden #C8C8C8).

    ![En skärmbild av en Microsoft-logotyp i otillåten färg.](media/guidelines-powerbi-visuals/no-color-logo.png) ![En skärmbild av en svart Microsoft-logotyp som inte är tillåten](media/guidelines-powerbi-visuals/black-logo.png)

* En kommersiell logotyp med effekter som övertoningar eller starka skuggor.

    ![En skärmbild av ett exempel på en Microsoft-logotyp i otillåtet format.](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>Bästa praxis

När du publicerar ett visuellt Power BI-objekt bör du tänka på följande rekommendationer för att ge användarna en bra upplevelse.

### <a name="visual-landing-page"></a>Landningssida för visuellt objekt

Använd landningssidan för att klargöra för användarna hur de kan använda ditt visuella Power BI-objekt och var de kan köpa licensen. Omfattar inte videor som utlöses automatiskt. Lägg bara till material som hjälper till att förbättra användarupplevelsen som information eller länkar till hur man köper en licens och hur man använder IAP-funktioner.

### <a name="license-key-and-token"></a>Licensnyckel och token

För att underlätta för användaren så kan du lägga till licensnyckeln eller tokenrelaterade fält överst i formatfönstret.

## <a name="faq"></a>VANLIGA FRÅGOR OCH SVAR

Mer information om visuella Power BI-objekt finns i [Vanliga frågor och svar om visuella Power BI-objekt med ytterligare köp](power-bi-custom-visuals-faq.md#visuals-with-additional-purchases).

## <a name="next-steps"></a>Nästa steg

Läs hur du kan publicera dina visuella Power BI-objekt till Microsoft AppSource där andra kan upptäcka och använda dem.

>[!div class="nextstepaction"]
>[Publicera visuella Power BI-objekt](office-store.md)