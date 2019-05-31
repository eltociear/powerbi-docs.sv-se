---
title: Skapa en visualisering med Power BI frågor och svar
description: Lär dig att skapa ett visuellt objekt med frågor och svar i Power BI-tjänsten med hjälp av exemplet på detaljhandelsanalys
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 580b387f8c763b0457bd32a71bfbccd90d4040a3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625256"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Skapa en visualisering med Power BI frågor och svar

Ibland är det snabbaste sättet att få svar från dina data att ställa en fråga med hjälp av naturligt språk.  I den här artikeln ska vi titta på två olika sätt att skapa samma visualisering: börja ställa en fråga med frågor och svar och andra: bygga den i en rapport. Vi använder Power BI-tjänsten för att skapa det visuella objektet i rapporten, men processen är nästan identisk med Power BI Desktop.

![Power BI fylls diagrammet](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Om du vill följa med, måste du använda en rapport som du kan redigera så vi använder ett av de exempel som finns tillgängliga i Power BI.

## <a name="create-a-visual-with-qa"></a>Skapa ett visuellt objekt med frågor och svar

Hur kan vi gå om hur du skapar det här linjediagrammet med frågor och svar?

1. Välj **Hämta data** \> **Exempel** \> **Exempel på detaljhandelsanalys**  >   **Anslut** från din Power BI-arbetsyta.

1. Öppna exempelinstrumentpanelen detaljhandelsanalys och placera markören i frågor och svar, **Ställ en fråga om dina data**.

    ![Placera markören i frågor och svar](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. I frågor och svar, skriver du något som liknar den här frågan:
   
    **årets försäljning och förra årets försäljning per månad som ytdiagram**
   
    När du skriver din fråga väljer Frågor och svar den bästa visualiseringen för att visa ditt svar och visualiseringen ändras dynamiskt när du ändrar frågan. Frågor och svar hjälper dig också formatera din fråga med förslag, automatisk komplettering och stavningskorrigeringar. Frågor och svar rekommenderar en liten formulering ändring ”: årets försäljning och förra årets försäljning per *månad* som ytdiagram”.  

    ![Frågor och svar korrigerad formulering](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Välj meningen att godkänna förslaget. 
   
   När du har skrivit din fråga, är resultatet samma diagram som visas i instrumentpanelen.
   
   ![Frågor och svar fyllda ytdiagram](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Välj fästikonen för att fästa diagrammet på din instrumentpanel ![Fästikon](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) i det övre högra hörnet.

## <a name="create-a-visual-in-the-report-editor"></a>Skapa ett visuellt objekt i rapportredigeraren

1. Gå tillbaka till instrumentpanelen för Exempel på detaljhandelsanalys.
   
2. Instrumentpanelen innehåller samma ytdiagramspanel för ”förra årets försäljning och årets försäljning”.  Välj den här panelen. Markera inte den panel som du skapade med frågor och svar. Om du väljer den öppnas frågor och svar. Den ursprungliga ytdiagramspanel skapades i en rapport så rapporten öppnas på den sida som innehåller den här visualiseringen.

    ![Instrumentpanelen för Exempel på detaljhandelsanalys](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Öppna rapporten i redigeringsvyn genom att välja **Redigera rapport**.  Om du inte är ägare till en rapport kan du inte öppna den i redigeringsvyn.
   
    ![Knappen Redigera rapport](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Välj ytdiagrammet och granska inställningarna i **Fält**-fönstret.  Rapportskaparen byggde det här diagrammet genom att välja dessa tre värden (**förra årets försäljning** och **försäljning detta år > värde** från den **försäljning** tabellen, och  **Räkenskapsmånad** från den **tid** tabellen) och ordna dem i den **axel** och **värden** källor.
   
    ![Visualiseringsfönster](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Du kan se de till slut med samma visuella objekt. När den skapades på så sätt inte var för komplicerad. Men när den skapades med frågor och svar har enklare!

## <a name="next-steps"></a>Nästa steg

- [Använd frågor och svar i instrumentpaneler och rapporter](power-bi-tutorial-q-and-a.md)  
- [Frågor och svar för konsumenter](consumer/end-user-q-and-a.md)
- [Få dina data att fungera bra med Frågor och svar i Power BI](service-prepare-data-for-q-and-a.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

