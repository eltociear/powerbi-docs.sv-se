---
title: Använda Prestandaanalys till att undersöka prestandan för rapportelement i Power BI Desktop
description: Ta reda på hur visuella objekt och rapportelement presterar avseende resursanvändning och svarstider
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/23/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 58cf8d2339663e4c02fda732fd4abd9c4c498576
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239111"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Använd Prestandaanalys till att undersöka prestandan för rapportelement

I **Power BI Desktop** kan du ta reda på hur dina olika rapportelement, till exempel visuella objekt och DAX-formler, presterar. Med hjälp av **Prestandaanalys** kan du visa och registrera loggar som mäter hur dina rapportelement presterar när användarna interagerar med dem, samt vilka delar av prestandan som är mest (eller minst) resursintensiv.

![Prestandaanalys](media/desktop-performance-analyzer/performance-analyzer-01.png)

Prestandaanalys kontrollerar och visar hur lång tid som krävs vid uppdatering av alla visuella objekt som användarinteraktionen initierar. Du får även information där du kan visa, öka detaljnivån eller exportera resultaten. Med Prestandaanalys kan du identifiera visuella objekt som påverkar rapporternas prestanda och du kan hitta orsaken till denna påverkan.

## <a name="displaying-the-performance-analyzer-pane"></a>Visa fönstret Prestandaanalys

I **Power BI Desktop** väljer du menyfliksområdet **Vy**. I området **Visa** i menyfliksområdet **Vy** markerar du kryssrutan bredvid **Prestandaanalys** för att visa fönstret Prestandaanalys.

![I menyfliksområdet Vy väljer du Prestandaanalys](media/desktop-performance-analyzer/performance-analyzer-02.png)

När du har valt det här alternativet visas Prestandaanalys i ett eget fönster, till höger om rapportarbetsytan.

## <a name="using-performance-analyzer"></a>Använda Prestandaanalys

Prestandaanalys mäter nödvändig bearbetningstid (inklusive tiden för att skapa eller uppdatera ett visuellt objekt) för att uppdatera rapportelement som initierats av en användarinteraktion där resultatet blir att en fråga körs. Om du till exempel justerar ett utsnitt måste utsnittets visuella objekt ändras, en fråga skickas till datamodellen och berörda visuella objekt uppdateras som ett resultat av de nya inställningarna. 

Om du vill att Prestandaanalys ska börja spela in väljer du helt enkelt **Starta inspelning**

![Starta inspelning](media/desktop-performance-analyzer/performance-analyzer-03.png)

Alla åtgärder som du utför i rapporten visas och loggas i fönstret Prestandaanalys, i den ordning som det visuella objektet läses in av Power BI. Till exempel kanske du har en rapport som användarna tycker tar lång tid att uppdatera. Eller att det tar lång tid att visa en del visuella objekt i en rapport när ett skjutreglage används. Prestandaanalys kan visa vilket visuellt objekt som är orsaken och vilka delar av det visuella objektet som tar längst tid att bearbeta. 

När du har startat inspelningen är knappen **Starta inspelning** nedtonad (inaktiv, eftersom du redan har börjat spela in) och knappen **Stopp** är aktiv. 

Prestandaanalys samlar in och visar information om prestandamätning i realtid. Det innebär att varje gång du klickar på ett visuellt objekt, flyttar ett utsnitt eller interagerar på annat sätt, visar Prestandaanalys omedelbart prestandaresultaten i sitt fönster.

Om det finns mer information i fönstret än vad som får plats, visas en rullningslist där du kan navigera till ytterligare information.

Varje interaktion har en avsnittsidentifierare i fönstret som beskriver den åtgärd som initierade loggposterna. I följande bild var interaktionen att användarna ändrade ett utsnitt.

![Avsnitten baserat på interaktionstyp](media/desktop-performance-analyzer/performance-analyzer-04.png)

Varje visuellt objekts logginformation inkluderar den tid som använts (varaktighet) för att slutföra följande uppgiftskategorier:

* **DAX-fråga** – Om en DAX-fråga krävdes, är detta tiden det tog från att det visuella objektet skickade frågan tills Analysis Services returnerade resultatet.
* **Visuell framställning** – Den tid det tog att rita det visuella objektet på skärmen, inklusive den tid som krävdes för att hämta eventuella webbilder eller geokodning. 
* **Övrigt** – Den tid som krävs av det visuella objektet för att förbereda frågor, vänta på att andra visuella objekt ska slutföras eller utföra annan bakgrundsbearbetning.

Värdena i **Varaktighet (ms)** anger skillnaden mellan en *start-* och *sluttidsstämpel* för varje åtgärd. De flesta arbetsytor och visuella åtgärder körs sekventiellt i en enda användargränssnittstråd, som delas av flera åtgärder. De rapporterade varaktigheterna innefattar tidsåtgång för kö medan andra åtgärder slutförs. [Prestandaanalys-exempel](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer) på GitHub och tillhörande [dokumentation](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx) ger information om hur visuella data ska frågas och hur de återges.


![element i logginformation](media/desktop-performance-analyzer/performance-analyzer-06.png)

När du har interagerat med de element i rapporten som du vill mäta med Prestandaanalys kan du välja knappen **Stopp**. Prestandainformationen som ska analyseras finns kvar i fönstret när du har valt **Stopp**.

Om du vill rensa informationen i fönstret Prestandaanalys väljer du **Rensa**. All information raderas och sparas inte när du väljer **Rensa**. I nästa avsnitt får du lära dig att spara informationen i loggarna. 

## <a name="refreshing-visuals"></a>Uppdatera visuella objekt

Du kan välja **Uppdatera visuella objekt** i fönstret Prestandaanalys för att uppdatera alla visuella objekt på den aktuella sidan i rapporten och därmed låta Prestandaanalys samla in information om alla sådana visuella objekt.

Du kan också uppdatera enskilda visuella objekt. När Prestandaanalys spelar in kan du välja **Uppdatera det här visuella objektet** i det övre högra hörnet av varje visuellt objekt, för att uppdatera det visuella objektet och samla in dess prestandainformation.

![uppdatera ett enskilt visuellt objekt](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Spara prestandainformation

Du kan spara informationen som Prestandaanalys skapar om en rapport genom att välja knappen **Exportera**. Om du väljer **Exportera** skapas en .json-fil med information från fönstret Prestandaanalys. 

![Spara loggfilen för prestandaanalysen](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Nästa steg
För mer information om **Power BI Desktop**, och hur du kommer igång, ta en titt i följande artiklar.

* [Vad är Power BI Desktop?](../fundamentals/desktop-what-is-desktop.md)
* [Frågeöversikt med Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datakällor i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Anslut till data i Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   

Information prestandaanalys-exemplet finns i följande resurser.

* [Prestandaanalys-exempel](https://github.com/microsoft/powerbi-desktop-samples/tree/master/Performance%20Analyzer)
* [Dokumentation om prestandaanalys-exempel](https://github.com/microsoft/powerbi-desktop-samples/blob/master/Performance%20Analyzer/Power%20BI%20Performance%20Analyzer%20Export%20File%20Format.docx)
