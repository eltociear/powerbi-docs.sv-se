---
title: Använd visning av detaljerad information mellan rapporter i Power BI Desktop
description: Lär dig mer om visa detaljerad information från en rapport till en annan i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 7189ef77446446b56b1dcb55b43b022d0fc5c057
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73868784"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Använd visning av detaljerad information mellan rapporter i Power BI Desktop

Med funktionen för ökad detaljnivå i Power BI Desktop kan du gå från en rapport till en annan baserat på sammanhang. Detta är sant förutsatt att rapporterna befinner sig i samma arbetsyta eller app i Power BI-tjänsten. Använd detaljnivå mellan rapporter för att ansluta två eller flera rapporter som har relaterat innehåll och för att skicka filterkontexten tillsammans med anslutningen mellan rapporterna. I den här artikeln får du lära dig hur du konfigurerar detaljnivå mellan rapporter för Power BI och vad användarna ser när använder detaljinformationsfunktionen mellan olika rapporter.

![Skärmbild på alternativ för detaljnivå i Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Det är viktigt att förstå följande definitioner innan vi börjar konfigurera och använda detaljnivå mellan rapporter:

* **Visuellt källobjekt:** Det visuella objektet som anropar detaljnivååtgärden via det visuella objektets snabbmeny.
* **Källrapport:** Rapporten som innehåller det visuella objektet för detaljnivå mellan rapporter.
* **Målsida:** Sidan som användaren hamnar på efter att en detaljnivååtgärd har utförts.
* **Målrapport:** Rapporten som innehåller målsidan för detaljnivå mellan rapporter.


> [!NOTE]
> Med funktionen för ökad detaljnivå i Power BI Desktop kan du gå från en rapport till en annan baserat på sammanhang. Detta är sant förutsatt att rapporterna befinner sig i samma arbetsyta eller app i Power BI-tjänsten. Detta gäller inte vid åtkomst till enskilda delade rapporter i *Min arbetsyta* ([Delat med mig-rapporter](service-share-dashboards.md#share-a-dashboard-or-report)). I stället kommer du åt rapporten på den arbetsyta som den ursprungligen delades från.


## <a name="enable-cross-report-drillthrough"></a>Aktivera detaljerad information mellan rapporter

Om du vill göra det möjligt för att rapport att vara mål för detaljerad information mellan rapporter måste du aktivera funktionen för rapporten i fönstret **Alternativ**. Gå till **Filalternativ och inställningar** > **Alternativ** och gå sedan till **Rapportinställningar** längst ner till vänster på sidan.

Markera kryssrytan **Tillåt att visuella objekt i den här rapporten använder mål för visning av detaljerad information från andra rapporter** enligt följande bild.

![Skärmbild av fönstret Alternativ med markerade rapportinställningar](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Detaljerad information mellan rapporter har nu aktiverats.

## <a name="set-up-cross-report-drillthrough"></a>Konfigurera detaljerad information mellan rapporter

Att ställa in detaljerad information mellan rapporter påminner om att konfigurera detaljerad information inom en rapport. Detaljerad information har aktiverats på målsidan så att andra visuella objekt kan rikta in sig på den aktiverade sidan för detaljerad information. Anvisningar om hur du skapar detaljerad information i en enda finns i [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md).

För att starta processen måste du utföra ett par inledande steg:

* Konfigurera en målsida för detaljerad information som sedan kan nås av andra rapporter i arbetsytan eller appen.
* Tillåt att en rapport visar sidor med detaljerad information utanför sin egen rapport.

Hitta alternativ för detaljerad information området **Fält** i fönstret **Visuella objekt** som visas på följande sida.

![Skärmbild av fönstret Visuella objekt där alternativet Detaljerad information har markerats](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Det första steget i att aktivera detaljerad information för en sida är att godkänna datamodellerna för käll- och målrapporter. Kontrollera att: 

* Fält som du vill skicka finns i båda datamodellerna.
* Namnen på fälten och namnen på de tabeller som de tillhör är identiska (strängarna måste också matcha är skiftlägeskänsliga).

Till exempel, om du vill skicka ett filter för fältet *Land* i tabellen *Geografi* måste båda modeller ha tabellen *Geografi* och fältet *Land* i denna tabell. Annars måste du uppdatera fältnamnet eller tabellnamnet i den underliggande modellen. Det räcker inte att endast uppdatera visningsnamnen för fälten om du vill använda detaljerad information mellan rapporter. (Observera att scheman i varje rapport inte måste vara likadana.)

För att komma igång med konfigurationen måste du färdigställa målsidan. I Power BI Desktop går du till sidan och kontrollerar att alternativet **detaljerad information mellan rapporter** är **På**. 

![Skärmbild där alternativet detaljerad information mellan rapporter är På](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Dra sedan de fält som du vill använda som mål för detaljerad information till arbetsytan. Välj om du vill att fältet ska användas som en kategori eller sammanfattas som ett mått. Här kan du välja om du vill inaktivera alternativet **Behåll alla filter** för det visuella objektet. Om du inte vill skicka andra tillämpade filter från källans visuella objekt till det visuella målobjektet för kan du välja **Av**.

> [!NOTE]
> Om du bara använder sidan för detaljerad information mellan rapporter bör du ta bort knappen **Tillbaka** som har lagts till automatiskt. Knappen **Tillbaka** fungerar bara för navigering i en enda rapport. 

När du har konfigurerat det visuella objektet måste du spara rapporten om du använder Power BI-tjänsten eller spara och publicera rapporten om du använder Power BI Desktop.

I föregående avsnitt beskrivs hur du aktiverar detaljerad information mellan rapporter för Power BI Desktop (i fönstret **Alternativ**). Om du använder Power BI-tjänsten för att skapa ett mål för detaljerad information mellan rapporter måste du göra följande för att aktivera detaljerad information mellan rapporter: 

1. Välj den arbetsyta där målrapporten och källrapporten finns.
2. Välj **Rapporter**.
3. Välj ikonen **Inställningar** för källrapporten.
4. Se till att alternativet för detaljerad information mellan rapporter är **På**.
5. Spara rapporten.

Och sedan är du klar. Rapporten är klar för detaljerad information mellan rapporter. 

I nästa avsnitt tar vi en titt på upplevelsen från användarens perspektiv.

## <a name="cross-report-drillthrough-experience"></a>Upplevelsen av detaljerad information mellan rapporter

När du har konfigurerat detaljerad information mellan rapporter för en rapport kan du börja använda funktionen.

Välj källrapporten i Power BI-tjänsten och välj ett visuellt objekt som använder fältet eller fälten på sättet som du angav när du ställde upp målsidan. Högerklicka sedan på en datapunkt för att öppna den visuella snabbmenyn och välj **Detaljerad information**.

![Skärmbild av källrapporten i Power BI-tjänsten där Detaljerad information har markerats](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Du kommer att se resultaten i målsidan för detaljerad information mellan rapporter, precis som du konfigurerade dem när du skapade målet. Resultaten filtreras enligt inställningarna för detaljerad information.

> [!IMPORTANT]
> Power BI cachelagrar mål för detaljerad information mellan rapporter. Om du gör ändringar måste du uppdatera din webbläsare om du inte ser målen för detaljerad information som förväntat. 

Mål för övergripande rapporter formateras på följande sätt: 

`Target Page Name [Target Report Name]`

När du har valt målsidan där du vill öka detaljnivån går Power BI dit. Den medför filterkontexten baserat på målsidans inställningar. 

Filterkontexten från det visuella källobjektet kan innehålla följande: 

* Filter för rapporter, sidor och visuella objekt som påverkar det visuella källobjektet. 
* Korsfiltrering och korsmarkering som påverkar det visuella källobjektet. 
* Utsnitt på sidan och synkroniseringsutsnitt.
* URL-parametrar.

När du landar på målrapporten för detaljerad information använder Power BI endast filter för fält där den hittar exakta strängmatchningar för fältnamn och tabellnamn. Power BI använder inte fästa filter från målrapporten. Det tillämpar dock ditt personliga standardbokmärke om du har ett sådant. Till exempel, om ditt personliga standardbokmärke innehåller ett rapportnivåfilter för *land = US* använder Power BI det filtret först innan filterkontexten från det visuella källobjektet tillämpas. 

För standard överför Power BI filterkontexten till alla standardsidor i målrapporten. Power BI filtrerar inte filterkontexten för knappbeskrivningssidor eftersom sidor med verktygstips filtreras baserat på det visuella källobjektet som anropar knappbeskrivningen.

Använd webbläsarens **Bakåt**-knapp om du vill återgå till källrapporten efter åtgärden för detaljerad information mellan rapporter. 

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Använda utsnitt i Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md)

