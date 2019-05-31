---
title: Använd detaljinformation för cross-rapport i Power BI Desktop
description: Lär dig hur du detaljgranska från en rapport till en annan i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375196"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Använd detaljinformation för cross-rapport i Power BI Desktop

Med funktionen drillthrough för cross-rapport i Power BI Desktop kan hoppa du sammanhangsmässigt från en rapport till en annan rapport. Detta gäller så länge rapporterna är i samma arbetsyta eller app i Microsoft Power BI-tjänsten. Använda drillthrough för cross-rapport att ansluta två eller flera rapporter som har relaterat innehåll och för att skicka filterkontext tillsammans med anslutningen mellan-rapport. I den här artikeln lär du hur du ställer in en Drillthrough-åtgärd för cross-rapport för Power BI-rapporter och vad användarna uppleva när de använder cross-rapport drillthrough för sig själva.

![Skärmbild av Power BI Desktop drillthrough-alternativet](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Följande definitioner är viktigt att förstå, innan vi börja konfigurera och använda cross-rapport visning av detaljerad information:

* **Källobjektet:** Det visuella objektet som anropar drillthrough-åtgärd med hjälp av visual snabbmenyn.
* **Källrapporten:** Den rapport som innehåller visuellt källinformationen för visning av detaljerad information mellan-rapport.
* **Målsida:** Sidan som en användare hamnar på när du initierar en drillthrough-åtgärd.
* **Målrapporten:** Den rapport som innehåller målsidan för visning av detaljerad information mellan-rapport.

## <a name="enable-cross-report-drillthrough"></a>Aktivera visning av detaljerad information mellan-rapport

Om du vill aktivera en rapport för att användas som mål för en Drillthrough-åtgärd för cross-rapport, måste du aktivera funktionen för rapporten i den **alternativ** fönster. Gå till **filen** > **alternativ och inställningar** > **alternativ**, och gå till **rapportera inställningar** nära den längst ned på sidan till vänster.

Välj den **Tillåt visuella objekt i den här rapporten för att använda drillthrough mål från andra rapporter** kryssruta, enligt följande bild.

![Skärmbild av alternativ fönster, med rapportinställningar markerat](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Cross-rapport drillthrough är nu aktiverat.

## <a name="set-up-cross-report-drillthrough"></a>Ställ in drillthrough för cross-rapport

Konfigurera cross-rapport drillthrough liknar hur du konfigurerar drillthrough inom en rapport. Visning av detaljerad information är aktiverat på målsidan, så att andra visuella objekt att fokusera på sidan aktiverad för visning av detaljerad information. Anvisningar om hur du skapar drillthrough inom en enda rapport finns i [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md).

Om du vill starta installationsprocessen, måste du vidta några åtgärder för inledande:

* Ställ in en drillthrough-målsida som sedan kan kommas åt från andra rapporter i arbetsytan eller app.
* Tillåt en rapport för att se drillthrough sidor från utanför sin egen rapport.

Hitta alternativ för visning av detaljerad information i den **fält** delen av den **visualiseringar** som visas i följande bild.

![Skärmbild av visualiseringsfönstret, med Drillthrough-alternativ som markerats](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Det första steget i att aktivera visning av detaljerad information för en sida är att verifiera datamodeller för käll- och -rapporter. Se till att: 

* Fält som du vill skicka finns i båda datamodeller.
* Namnen på fälten och namnen på tabellerna som de tillhör, är identiska (strängarna måste även matcha och är skiftlägeskänsliga).

Exempel: Om du vill skicka ett filter på fältet *land* i tabell *geografi*, båda modellerna måste ha en *geografi* tabellen, och en *land* fältet i den tabellen. Om inte, måste du uppdatera det fältnamn eller tabellnamnet i den underliggande modellen. Genom att uppdatera fälten visningsnamn fungerar inte korrekt för visning av detaljerad information mellan-rapport. (Observera att scheman i varje rapport inte behöver vara exakt samma.)

För att komma igång med installationen, måste du förbereda målsidan. I Power BI Desktop, gå till sidan och kontrollera att den **Cross-rapport** drillthrough växlingsknappen är **på**. 

![Skärmbild av Cross-rapport växla aktiverat](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Dra sedan de fält som du vill använda som detaljinformationsmål till arbetsytan. Välj om du vill att fältet som ska användas som en kategori eller sammanfattas som ett mått. Nu kan du välja om du vill inaktivera den **Behåll alla filter** växlingsknappen för det visuella objektet. Om du inte vill skicka andra filter från källan visual mål-Drillthrough visual väljer **av**.

> [!NOTE]
> Om du använder sidan för cross-rapport drillthrough endast, bör du ta bort den **tillbaka** knapp som läggs till automatiskt. Den **tillbaka** knappen fungerar bara för nagivation inom en enda rapport. 

När du har konfigurerat det visuella objektet, kontrollera att du sparar rapporten om du befinner dig i Power BI-tjänsten eller spara och publicera rapporten om du använder Power BI Desktop.

Föregående avsnitt beskrivs hur du aktiverar drillthrough för cross-rapport för Power BI Desktop (i den **alternativ** fönster). Om du använder Power BI-tjänsten för att skapa en cross-rapport detaljinformationsmål om du vill aktivera visning av detaljerad information mellan-rapport måste du: 

1. Markera arbetsytan där din målrapporten och källrapporten finns.
2. Välj **rapporter**.
3. Välj den **inställningar** ikon för källrapporten.
4. Kontrollera att växlingsknappen cross-rapport drillthrough är **på**.
5. Spara din rapport.

Och sedan är du klar. Rapporten är klar för cross-rapport drillthrough-upplevelse. 

I nästa avsnitt ta vi en titt på upplevelsen ur användarens perspektiv.

## <a name="cross-report-drillthrough-experience"></a>Cross-rapport drillthrough-upplevelse

När du konfigurerar flera-rapport drillthrough-upplevelsen för en rapport kan placera du funktionen du ska använda.

Välj källrapporten i Power BI-tjänsten och välj sedan ett visuellt objekt som använder det eller de fält på det sätt som du angav när du ställer in målsidan. Högerklicka sedan på en datapunkt för att öppna menyn visuell kontext och välja **Drillthrough**.

![Skärmbild av källrapporten i Power BI-tjänsten med Drillthrough markerat](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Sedan visas resultaten i mål cross-rapport drillthrough-sidan, precis som du konfigurerar dem när du skapade målet. Resultaten filtreras drillthrough-inställningar.

> [!IMPORTANT]
> Powerbi cachelagrar cross-rapport drillthrough-mål. Om du gör ändringar, måste du uppdatera din webbläsare om du inte ser drillthrough-mål som förväntat. 

Cross-rapport mål är formaterad på följande sätt: 

`Target Page Name [Target Report Name]`

När du har valt målsidan som du vill visa detaljerad information går Power BI till den sidan. Den skickar längs filterkontext baserat på inställningarna för målsidan. 

Filterkontext från det visuella källobjektet kan innefatta följande: 

* Rapporten, sida och filter på visuell nivå påverkar visuellt källinformationen. 
* Korsfiltrering och korsmarkering som påverkar visuellt källinformationen. 
* Utsnitt på sidan och synkronisera utsnitt.
* URL-parametrar.

När du hamnar på målrapporten för visning av detaljerad information gäller Power BI endast filter för fält som påträffas exakta strängen matchar för fältnamn och tabellnamn. Powerbi använda inte Fäst filter från målrapporten. Den, men gäller din personliga standardkatalogen för bokmärken om en sådan finns. Exempel: om din personliga standardkatalogen för bokmärken innehåller ett filter på rapportnivå för *land = USA*, Power BI tillämpas filtret först innan du tillämpar Filterkontexten från det visuella källobjektet. 

För cross-rapport drillthrough skickar Power BI Filterkontexten till alla sidor i målrapporten. Powerbi Skicka inte filterkontext för knappbeskrivning sidor, eftersom knappbeskrivning sidor filtreras baserat på det visuella källobjektet som anropar knappbeskrivningen.

Om du vill gå tillbaka till källrapporten efter cross-rapport drillthrough-åtgärd, använder du webbläsarens **tillbaka** knappen. 

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Använda utsnitt i Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md)

