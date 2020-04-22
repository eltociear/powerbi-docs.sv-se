---
title: Använd visning av detaljerad information mellan rapporter i Power BI Desktop
description: Lär dig mer om visa detaljerad information från en rapport till en annan i Power BI Desktop
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/16/2019
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: 33d0b7850b5e396d8f03e80cbcb32768fb26bf6d
ms.sourcegitcommit: b2cb0b02bdc451bf11a92a68f2c4d560a811f563
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81439812"
---
# <a name="use-cross-report-drillthrough-in-power-bi"></a>Använda visning av detaljerad information mellan rapporter i Power BI

Med funktionen för *Visa detaljerad information mellan rapporter* i Power BI kan du gå från en rapport till en annan baserat på sammanhang i samma Power BI-arbetsyta eller app. Du kan använda visning av detaljerad information mellan rapporter för att ansluta två eller flera rapporter som har relaterat innehåll och för att skicka filterkontexten tillsammans med anslutningen mellan rapporterna. 

Om du vill initiera visning av detaljerad information mellan rapporter väljer du en datapunkt i ett *visuellt källobjekt* i en *källrapport*. Välj sedan målet för visning av **detaljerad information** mellan rapporter på snabbmenyn. 

![Alternativet Visa detaljerad information mellan rapporter i Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Åtgärden för visning av detaljerad information mellan rapporter öppnar *målsidan* i *målrapporten*. 

![Mål för visning av detaljerad information mellan rapporter i Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

Den här artikeln visar hur du konfigurerar och använder detaljerad visning av information mellan rapporter för Power BI-rapporter.

> [!NOTE]
> Du kan inte använda visning av detaljerad information mellan rapporter med [Delat med mig-rapporter](service-share-dashboards.md#share-a-dashboard-or-report) som delas enskilt inom **Min arbetsyta**. Om du vill använda visning av detaljerad information mellan rapporter måste du öppna rapporterna på den arbetsyta som de delas från.

## <a name="enable-cross-report-drillthrough"></a>Aktivera detaljerad information mellan rapporter

Det första steget i att aktivera visning av detaljerad information mellan rapporter är att godkänna datamodellerna för käll- och målrapporter. Även om scheman i varje rapport inte behöver vara samma måste fälten som du vill skicka finnas i båda datamodellerna. Namnen på fälten och namnen på de tabeller som de tillhör måste vara identiska. Strängarna måste matcha, och de är skiftlägeskänsliga.

Om du till exempel vill skicka ett filter för fältet **Delstat** i tabellen **Delstater i USA** måste båda modellerna ha tabellen **Delstater i USA** och fältet **Delstat** i denna tabell. Annars måste du uppdatera fältnamnet eller tabellnamnet i den underliggande modellen. Det räcker inte att endast uppdatera visningsnamnen för fälten om du vill använda detaljerad information mellan rapporter.

När du har verifierat dina modeller aktiverar du källrapporten för att använda visning av detaljerad information mellan rapporter. 

1. I Power BI Desktop går du till **Arkiv** > **Alternativ och inställningar** > **Alternativ**. 
1. I fönstret **Alternativ** i navigeringen till vänster längst ned i avsnittet **Aktuell fil** väljer du **Rapportinställningar**. 
1. Längst ned till höger under **Visa detaljerad information mellan rapporter** väljer du **Tillåt visuell information i den här rapporten för att använda mål för visning av detaljerad information från andra rapporter**. 
1. Välj **OK**. 
   
   ![Aktivera visning av detaljerad information mellan rapporter i Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Du kan också aktivera visning av detaljerad information mellan rapporter från Power BI-tjänsten.
1. I Power BI-tjänsten väljer du den arbetsyta som innehåller dina mål- och källrapporter.
1. Bredvid källrapportens namn i arbetsytelistan väljer du symbolen **Fler alternativ** och sedan **Inställningar**. 
1. Längst ned i fönstret **Inställningar**, under **Visa detaljerad information mellan rapporter**, väljer du **Tillåt visuell information i den här rapporten för att använda mål för visning av detaljerad information från andra rapporter**. Välj sedan **Spara**.
   
   ![Aktivera visning av detaljerad information mellan rapporter i Power BI-tjänsten](media/desktop-cross-report-drill-through/cross-report-drill-through-02a.png)

## <a name="set-up-a-cross-report-drillthrough-target"></a>Konfigurera ett mål för visning av detaljerad information mellan rapporter

Att konfigurera en målsida för visning av detaljerad information mellan rapporter påminner om att konfigurera visning av detaljerad information inom en rapport. Genom att aktivera visning av detaljerad information på målsidan kan andra visuella objekt använda sidan som mål för visning av detaljerad information. Läs [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md) om du vill skapa visning av detaljerad information i en enskild rapport.

Du kan konfigurera ett mål för visning av detaljerad information mellan rapporter i Power BI Desktop eller Power BI-tjänsten. 
1. Redigera målfilen. På målsidan för målrapporten väljer du sedan avsnittet **Fält** i fönstret **Visualiseringar**. 
1. Under **Visning av detaljerad information** anger du växlingsknappen **Korsrapport** till **På**. 
1. Dra fältet som du vill använda som mål för visning av detaljerad information till **Lägg till ett fält för visning av detaljerad information här**. För varje fält väljer du om du vill tillåta visning av detaljerad information när fältet används som en kategori eller när det sammanfattas som ett mått. 
1. Välj om du vill **behålla alla filter** för det visuella objektet. Om du inte vill skicka andra filter som används för källans visuella objekt till det visuella målobjektet väljer du **Av**.
   
   ![Skärmbild av fönstret Visualiseringar med alternativet Visning av detaljerad information markerat](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)
   
1. Om du bara använder sidan för detaljerad information mellan rapporter tar du bort knappen **Tillbaka** som har lagts till automatiskt på arbetsytan. Knappen **Tillbaka** fungerar bara för navigering inom en rapport. 
1. När du har konfigurerat målsidan ska du spara rapporten, (om du använder Power BI-tjänsten) eller spara och publicera rapporten (om du använder Power BI Desktop).

Och sedan är du klar. Nu kan du använda visning av detaljerad information mellan rapporter i rapporterna. 

## <a name="use-cross-report-drillthrough"></a>Använd detaljerad information mellan rapporter

Om du vill använda visning av detaljerad information mellan rapporter väljer du källrapporten i Power BI-tjänsten och ett visuellt objekt som använder fältet för visning av detaljerad information på sättet som du angav när du konfigurerade målsidan. Högerklicka sedan på en datapunkt för att öppna den visuella snabbmenyn och välj **Visning av detaljerad information** och sedan målet för visning av detaljerad information. Mål för visning av detaljerad information mellan rapporter formateras som **Sidnamn [Rapportnamn]** .

![Alternativet Visa detaljerad information mellan rapporter i Power BI](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Resultaten visas på målsidan för detaljerad information mellan rapporter, precis som du konfigurerade dem när du skapade målet. Resultaten filtreras enligt inställningarna för detaljerad information.

![Mål för visning av detaljerad information mellan rapporter i Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01a.png)

> [!IMPORTANT]
> Power BI cachelagrar mål för detaljerad information mellan rapporter. Om du gör ändringar måste du uppdatera din webbläsare om inte målen för detaljerad information visas som förväntat. 

Om du anger **Behåll alla filter** till **På** när du konfigurerar målsidan kan filterkontext från det visuella källobjektet innehålla följande: 

- filter för rapporter, sidor och visuella objekt som påverkar det visuella källobjektet 
- korsfiltrering och korsmarkering som påverkar det visuella källobjektet 
- utsnitt och synkroniseringsutsnitt på sidan.
- URL-parametrar

När du landar på målrapporten för detaljerad information använder Power BI endast filter för fält som har exakta strängmatchningar för fältnamn och tabellnamn. 

Power BI använder inte fästbara filter från målrapporten, men däremot ditt personliga standardbokmärke, om du har ett sådant. Om ditt personliga standardbokmärke till exempel innehåller ett rapportnivåfilter för *land = US* använder Power BI det filtret innan filterkontexten från det visuella källobjektet tillämpas. 

För visning av detaljerad information mellan rapporter överför Power BI filterkontexten till standardsidor i målrapporten. Power BI filtrerar inte filterkontexten för knappbeskrivningssidor eftersom sidor med verktygstips filtreras baserat på det visuella källobjektet som anropar knappbeskrivningen.

Använd webbläsarens **Bakåt**-knapp om du vill återgå till källrapporten efter åtgärden för detaljerad information mellan rapporter. 

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

- [Utsnitt i Power BI](visuals/power-bi-visualization-slicers.md)
- [Använd detaljinformation i Power BI Desktop](desktop-drillthrough.md)

