---
title: Om du Använd Analysera prestanda för att undersöka rapportprestanda element i Power BI Desktop
description: Ta reda på hur visuella objekt och rapportelement fungerar när det gäller Resursanvändning och svarstider
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854423"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Om du Använd Analysera prestanda för att undersöka rapportprestanda element

I **Power BI Desktop** hittar du ut hur var och en av dina rapportelement, till exempel visuella objekt och DAX-formler fungerar. Med hjälp av den **Performance Analyzer**, du kan se och post loggar som mäter hur var och en av dina rapportelement utför när användare interagerar med dem och vilka aspekter av deras prestanda är mest (eller minst) resurskrävande.

![Analysera prestanda](media/desktop-performance-analyzer/performance-analyzer-01.png)

Analysera prestanda inspekterar och visar tid som krävs för uppdatering eller alla visuella objekt att initiera användarinteraktioner och presenteras information så att du kan visa, granska nedåt eller exportera resultaten. Analysera prestanda kan hjälpa dig att identifiera visuella objekt som påverkar prestanda för dina rapporter och identifiera orsaken till effekten.

## <a name="displaying-the-performance-analyzer-pane"></a>Visa fönstret Analysera prestanda

I **Power BI Desktop** väljer den **visa** menyfliksområdet. I den **visa** område i den **visa** menyfliksområdet som du kan markera kryssrutan bredvid **Performance Analyzer** att visa fönstret Analysera prestanda.

![Välj prestanda i menyfliksområdet visa](media/desktop-performance-analyzer/performance-analyzer-02.png)

När du valt, visas Analysera prestanda i sin egen rutan till höger i rapportarbetsytan.

## <a name="using-performance-analyzer"></a>Med Analysera prestanda

Prestandamått för analyzer bearbetningstid (inklusive det hög tid att skapa eller uppdatera ett visuellt objekt) krävs för att uppdatera rapportelement som initieras på grund av interaktion med användaren som resulterar i en fråga som körs. Till exempel kräver justera ett utsnitt utsnitt visuella objekt som ska ändras en fråga som ska skickas till datamodellen, och berörda visuella objekt som måste uppdateras till följd av de nya inställningarna. 

Om du vill att analysera prestanda börja spela in helt enkelt välja **börja spela in**

![Starta inspelning](media/desktop-performance-analyzer/performance-analyzer-03.png)

Alla åtgärder som du gör i rapporten visas och loggas i fönstret Analysera prestanda i den ordning som att det visuella objektet har lästs in av Power BI. Till exempel kanske har du en rapport som användare har sagt tar lång tid att uppdatera. Eller ta lång tid att visa när skjutreglaget justeras för vissa visuella objekt i en rapport. Analysera prestanda ser du vilket visuellt objekt som är orsaken och identifierar vilka aspekter av det visuella objektet tar den längsta varaktigheten att bearbeta. 

När du börjar spela in, den **börja spela in** knappen är nedtonad out (inaktiv, eftersom du har redan börjat inspelning) och **stoppa** knappen är aktiv. 

Analysera prestanda samlar in och visar mått prestandainformation i realtid. Så varje gång du klickar på ett visuellt objekt, flytta ett utsnitt eller interagera på något annat sätt visas Analysera prestanda omedelbart prestanda i dess rutan.

Om fönstret har mer än vad som kan visas, visas en rullningslist att navigera till ytterligare information.

Varje interaktion har en avsnittet identifierare i fönstret som beskriver den åtgärd som initierade loggposterna. I följande bild var interaktionen att användarna ändrats ett utsnitt.

![Avsnitt baserat på typen av interaktion](media/desktop-performance-analyzer/performance-analyzer-04.png)

Logginformation för varje visuellt objekt innehåller tidsåtgång (varaktighet) för att slutföra följande typer av uppgifter:

* **DAX-frågan** – om en DAX-frågan var krävs, detta är tiden mellan det visuella objektet skicka frågan och för Analysis Services för att returnera resultat.
* **Visuell** -tid som krävs för det visuella objektet att rita på skärmen, inklusive tid som krävs för att hämta alla webbilder eller geokodning. 
* **Andra** -tid som krävs med det visuella objektet för att förbereda frågor, väntar på andra visuella objekt för att slutföra eller utföra andra behandling i bakgrunden.

![element i logginformation](media/desktop-performance-analyzer/performance-analyzer-06.png)

När du har interagerat med element i rapporten som du vill mäta med Analysera prestanda, kan du välja den **stoppa** knappen. Prestandainformation finns kvar i fönstret när du har valt **stoppa** för dig att analysera.

Om du vill ta bort information i fönstret Analysera prestanda, Välj **Rensa**. All information som tas bort och sparas inte när du väljer **Rensa**. Se nästa avsnitt för att lära dig hur du sparar information i loggarna. 

## <a name="refreshing-visuals"></a>Uppdatera visuella objekt

Du kan välja **uppdatera visuella objekt** i fönstret Analysera prestanda för att uppdatera alla visuella objekt på den aktuella sidan i rapporten och därmed Performance Analyzer samla in information om alla sådana visualiseringar.

Du kan också uppdatera enskilda visuella objekt. När du analysera prestanda registrerar du kan välja **uppdatera det här visuella objektet** hittades i det övre högra hörnet av varje visuellt objekt att uppdatera det visuella objektet och dess prestanda-informationen.

![Uppdatera ett enskilt visuellt objekt](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Sparar prestandainformation

Du kan spara den information som Performance Analyzer skapar om en rapport genom att välja den **exportera** knappen. Att välja **exportera** skapar en JSON-fil med information från fönstret Analysera prestanda. 

![Spara loggfilen för prestanda](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Nästa steg
För mer information om **Power BI Desktop**, och hur du kommer igång, ta en titt i följande artiklar.

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Anslut till data i Power BI Desktop](desktop-connect-to-data.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)   

