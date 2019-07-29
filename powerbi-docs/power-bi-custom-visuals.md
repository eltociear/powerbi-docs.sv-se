---
title: Visuella objekt i Power BI
description: Anpassade visualiseringar i Power BI
author: sranins
ms.author: rasala
manager: kfile
ms.reviewer: maghan
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 68048968bf6a3f85f2bc24e55fd1288073be1d56
ms.sourcegitcommit: 473d031c2ca1da8935f957d9faea642e3aef9839
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68415405"
---
# <a name="visuals-in-power-bi"></a>Visuella objekt i Power BI

När du skapar eller redigerar en Power BI-rapport finns det många olika typer av visuella objekt som du kan använda. Ikoner för dessa visuella objekt visas i fönstret **Visualiseringar**. De här visuella objekten ingår när du laddar ned [Power BI Desktop](https://powerbi.microsoft.com/desktop/) eller öppnar [Power BI-tjänsten](https://app.powerbi.com).

![visualiseringar](media/power-bi-custom-visuals/power-bi-visualizations.png)

Du är dock inte begränsad till den här uppsättningen med visuella objekt. Om du väljer ellipsen (...) längst ned på sidan blir en annan källa till visuella objekt för rapporter tillgänglig – *anpassade visuella objekt*.

Utvecklare skapar anpassade visuella objekt med hjälp av SDK:n för anpassade visuella objekt. Med de här visuella objekten kan företagsanvändare se sina data på ett sätt som passar verksamheten. Rapportförfattarna kan sedan importera filerna för anpassade visuella objekt till sina rapporter och använda dem på samma sätt som med andra visuella Power BI-objekt. Anpassade visuella objekt har högsta prioritet i Power BI och kan filtreras markeras, redigeras, delas och så vidare.

Anpassade visuella objekt distribueras på tre sätt:

* Filer för anpassade visuella objekt
* Visuella objekt för organisationer
* Visuella Microsoft Azure Marketplace-objekt

## <a name="custom-visual-files"></a>Filer för anpassade visuella objekt

Anpassade visuella objekt är paket som innehåller kod för att återge de data som de förses med. Alla kan skapa anpassade visuella objekt och paketera dem som enskilda `.pbiviz`-filer som sedan kan importeras till Power BI-rapporter.

> [!WARNING]
> Ett anpassat visuellt objekt kan innehålla kod som innebär säkerhets- eller integritetsrisker. Se till att du litar på författaren och källan för anpassade visuella objekt innan du importerar den till din rapport.

## <a name="organizational-visuals"></a>Visuella objekt för organisationer

Power BI-administratörer godkänner och distribuerar anpassade visuella objekt i organisationen, som rapportförfattare enkelt kan upptäcka, uppdatera och använda. Administratörer kan enkelt hantera (till exempel uppdatera version och aktivera/inaktivera) dessa visuella objekt.

 [Läs mer om visuella objekt för organisationen](power-bi-custom-visuals-organization.md).

## <a name="marketplace-visuals"></a>Visuella Microsoft Azure Marketplace-objekt

Både communitymedlemmar och Microsoft har bidragit med anpassade visuella objekt och publicerat dem för allmän tillgänglighet på [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)-marknadsplatsen. Du kan ladda ned dessa visuella objekt och lägga till dem i Power BI-rapporter. Microsoft har testat och godkänt dessa anpassade visuella objekt vad gäller funktionalitet och kvalitet.

Vad är [AppSource](developer/office-store.md)? Det är den plats där du hittar appar och tillägg till dina Microsoft-program. AppSource ger miljontals användare av produkter som Office 365, Azure, Dynamics 365, Cortana och Power BI tillgång till lösningar som hjälper dem att utföra sitt arbete ännu effektivare, insiktsfullare och snyggare än tidigare.

### <a name="certified-visuals"></a>Certifierade visuella objekt

Power BI:s certifierade visuella objekt är visuella marknadsplatsobjekt som har genomgått ytterligare rigorös kvalitetstestning och som stöds i extra scenarier såsom [e-postprenumerationer](service-report-subscribe.md) och [export till PowerPoint](service-publish-to-powerpoint.md).
Om du vill se en lista över certifierade anpassade visuella objekt, eller skicka dina egna, så hittar du information i [Certifierade anpassade visuella objekt](power-bi-custom-visuals-certified.md).

Är du webbutvecklare och intresserad av att skapa egna visualiseringar och lägga till dem i AppSource? Läs [Utveckla ett anpassat visuellt objekt i Power BI](developer/custom-visual-develop-tutorial.md) och lär dig hur du [publicerar anpassade visuella objekt till AppSource](developer/office-store.md).

### <a name="import-a-custom-visual-from-a-file"></a>Importera ett anpassat visuellt objekt från en fil

1. Välj ellipserna längst ned i fönstret **Visualiseringar**.

    ![visualiseringar2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Välj **Importera från fil** i listrutan.

    ![importera från fil](media/power-bi-custom-visuals/power-bi-custom-visual-import-from-file.png)

3. På menyn **Öppna** väljer du den `.pbiviz`-fil som du vill importera och väljer sedan **Öppna**. Ikonen för det anpassade visuella objektet läggs till längst ned i fönstret **Visualiseringar** och kan nu användas i rapporten.

    ![importerade cv](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="import-organizational-visuals"></a>Importera visuella objekt för organisationer

1. Välj ellipserna längst ned i fönstret **Visualiseringar**.

    ![visuell organisation 1](media/power-bi-custom-visuals/power-bi-visual-org-01.png)

2. Välj **Importera från marknadsplats i listrutan**.

    ![visuell organisation 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Välj **MIN ORGANISATION** på den översta flikmenyn.

    ![visuell organisation 3](media/power-bi-custom-visuals/power-bi-visual-org-03.png)

4. Hitta det visuella objekt du vill importera genom att söka igenom listan.

    ![visuell organisation 4](media/power-bi-custom-visuals/power-bi-visual-org-04.png)

5. Välj **Lägg till** för att importera det anpassade visuella objektet. Dess ikon läggs till längst ned i fönstret **Visualiseringar** och kan nu användas i rapporten.

    ![visuell organisation 5](media/power-bi-custom-visuals/power-bi-visual-org-05.png)

## <a name="download-or-import-custom-visuals-from-microsoft-appsource"></a>Hämta eller importera anpassade visuella objekt från Microsoft AppSource

Du har två alternativ för att ladda ned och importera anpassade visuella objekt: från Power BI och från [AppSource-webbplatsen](https://appsource.microsoft.com/).

### <a name="import-custom-visuals-from-within-power-bi"></a>Hämta anpassade visuella objekt från Power BI

1. Välj ellipserna längst ned i fönstret **Visualiseringar**.

    ![visualiseringar 2](media/power-bi-custom-visuals/power-bi-visualizations2.png)

2. Välj **Importera från marknadsplats i listrutan**.

    ![visuell organisation 2](media/power-bi-custom-visuals/power-bi-visual-org-02.png)

3. Hitta det visuella objekt du vill importera genom att söka igenom listan.

    ![importera visuellt objekt](media/power-bi-custom-visuals/power-bi-import-visual.png)

4. Om du vill veta mer om ett specifikt visuellt objekt, så markera och välj det.

    ![Välj](media/power-bi-custom-visuals/power-bi-select.png)

5. På den här informationssidan kan du visa skärmdumpar, videor, detaljerade beskrivningar och annat.

    ![Översikt](media/power-bi-custom-visuals/power-bi-synoptic.png)

6. Bläddra längst ned om du vill se granskningar.

    ![Recensioner](media/power-bi-custom-visuals/power-bi-reviews.png)

7. Välj **Lägg till** för att importera det anpassade visuella objektet. Dess ikon läggs till längst ned i fönstret **Visualiseringar** och kan nu användas i rapporten.

    ![importerade visuellt objekt](media/power-bi-custom-visuals/power-bi-custom-visual-imported.png)

### <a name="download-and-import-custom-visuals-from-microsoft-appsource"></a>Hämta och importera anpassade visuella objekt från Microsoft AppSource

1. Börja med [Microsoft AppSource](https://appsource.microsoft.com) och välj fliken **Appar**.

    ![AppSource](media/power-bi-custom-visuals/power-bi-appsource-apps.png)

2. Gå till [appresultatsidan](https://appsource.microsoft.com/marketplace/apps) där du kan visa de främsta apparna i varje kategori, inklusive *Power BI-appar*. Vi söker efter anpassade visuella objekt, så vi väljer **Visuella Power BI-objekt** från den vänstra navigeringslistan så att resultaten begränsas.

    ![Visuella AppSource-objekt](media/power-bi-custom-visuals/power-bi-appsource-visuals.png)

3. AppSource visar en panel för varje anpassat visuellt objekt.  Varje panel har en ögonblicksbild av det anpassade visuella objektet med en kort beskrivning och en nedladdningslänk. Markera panelen om du vill se mer information.

    ![Välj visuellt objekt](media/power-bi-custom-visuals/powerbi-custom-select-visual.png)

4. På den här informationssidan kan du visa skärmdumpar, videor, detaljerade beskrivningar och annat. Välj **Hämta nu** för att ladda ned det anpassade visuella objektet, och godkänn sedan användningsvillkoren.

    ![Skaffa AppSource](media/power-bi-custom-visuals/power-bi-appsource-get.png)

5. Välj länken för att hämta det anpassade visuella objektet.

    ![Ladda ned](media/power-bi-custom-visuals/powerbi-custom-download.png)

    Nedladdningssidan innehåller också anvisningar om hur du importerar det anpassade visuella objektet till Power BI Desktop och Power BI-tjänsten.

    Du kan också hämta en exempelrapport som innehåller det anpassade visuella objektet och visar dess funktioner.

    ![Testa exempel](media/power-bi-custom-visuals/powerbi-custom-try-sample.png)

6. Spara `.pbiviz`-filen och öppna sedan Power BI.

7. Importera `.pbiviz`-filen till din rapport. (Se avsnittet [Importera ett anpassat visuellt objekt från en fil](#import-a-custom-visual-from-a-file) ovan.)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

* Ett anpassat visuellt objekt läggs till i en specifik rapport när det importeras. Om du vill använda det visuella objektet i en annan rapport måste du importera det till den rapporten också. När en rapport med ett anpassat visuellt objekt sparas med alternativet **Spara som**, så sparas en kopia av det anpassade visuella objektet med den nya rapporten.

* Om du inte ser fönstret **Visualiseringar** innebär det att du inte har redigeringsbehörigheter för rapporten.  Du kan bara lägga till anpassade visuella objekt till rapporter som du kan redigera, inte till rapporter som endast delas med dig.

## <a name="troubleshoot"></a>Felsök

Information om felsökning finns i [Felsöka anpassade visuella objekt i Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>Vanliga frågor och svar

Mer information och svar på frågor finns i [Vanliga frågor och svar om anpassade visuella Power BI-objekt](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

## <a name="next-steps"></a>Nästa steg

* [Visualiseringar i Power BI-rapporter](visuals/power-bi-report-visualizations.md)

Har du fler frågor? [Testa Power BI Community](http://community.powerbi.com/).
