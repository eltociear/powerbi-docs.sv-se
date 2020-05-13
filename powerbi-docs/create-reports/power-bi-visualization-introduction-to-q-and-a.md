---
title: Skapa ett visuellt objekt med Frågor och svar i Power BI
description: Lär dig att skapa ett visuellt objekt med Frågor och svar i Power BI-tjänsten, med hjälp av exemplet Detaljhandelsanalys
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 1e1e56981d40c30d589ff39e561acf97ddca5ca2
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83280597"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Skapa ett visuellt objekt med Frågor och svar i Power BI

Ibland är det snabbaste sättet att få svar från dina data att ställa en fråga med hjälp av naturligt språk.  I den här artikeln ska vi titta på två olika sätt att skapa samma visualisering: först genom att ställa en fråga med Frågor och svar och därefter genom att skapa den i en rapport. Vi använder Power BI-tjänsten till att skapa det visuella objektet i rapporten, men processen är nästan identisk om man använder Power BI Desktop.

![Ifyllt diagram i Power BI](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Om du vill följa med, måste du använda en rapport som du kan redigera så vi använder ett av de exempel som finns tillgängliga i Power BI.

## <a name="create-a-visual-with-qa"></a>Skapa ett visuellt objekt med frågor och svar

Hur skapar vi linjediagrammet med Frågor och svar?

1. Från din Power BI-arbetsytan väljer du **Hämta data** \> **Exempel** \> **Exempel på detaljhandelsanalys** > **Anslut**.

1. Öppna instrumentpanelen i exemplet på detaljhandelsanalys och placera markören i rutan Frågor och svar, **Ställ en fråga om dina data**.

    ![Placera markören i rutan Frågor och svar](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Skriv en fråga som liknar nedanstående i rutan Frågor och svar:
   
    **årets försäljning och fjolårets försäljning per månad som ytdiagram**
   
    När du skriver din fråga väljer Frågor och svar den bästa visualiseringen för att visa ditt svar och visualiseringen ändras dynamiskt när du ändrar frågan. Frågor och svar hjälper dig också formatera din fråga med förslag, automatisk komplettering och stavningskorrigeringar. Frågor och svar rekommenderar en liten ändring av texten till ”årets försäljning och fjolårets försäljning per *tid månad* som ytdiagram”.  

    ![Korrigerad formulering i Frågor och svar](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Välj meningen för att acceptera förslaget. 
   
   När du har skrivit klart frågan visas samma diagram som du ser i instrumentpanelen.
   
   ![Ifyllt ytdiagram i Frågor och svar](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Välj fästikonen för att fästa diagrammet på din instrumentpanel ![Fästikon](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) i det övre högra hörnet.

## <a name="create-a-visual-in-the-report-editor"></a>Skapa ett visuellt objekt i rapportredigeraren

1. Gå tillbaka till instrumentpanelen för Exempel på detaljhandelsanalys.
   
2. Instrumentpanelen innehåller samma panel med ytdiagrammet för ”Fjolårets försäljning och årets försäljning”.  Välj den här panelen. Välj inte den panel som du skapade med Frågor och svar. När du väljer den öppnas Frågor och svar. Den ursprungliga panelen för ytdiagrammet skapades i en rapport, så rapporten öppnas på sidan med visualiseringen.

    ![Instrumentpanelen för Exempel på detaljhandelsanalys](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Öppna rapporten i redigeringsvyn genom att välja **Redigera rapport**.  Om du inte är ägare till en rapport kan du inte öppna den i redigeringsvyn.
   
    ![Knappen Redigera rapport](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Välj ytdiagrammet och granska inställningarna i **Fält**-fönstret.  Rapportskaparen gjorde diagrammet genom att välja dessa tre värden (**Fjolårets försäljning** och **Årets försäljning > Värde** från tabellen **Försäljning** och **FiscalMonth** från tabellen **Tid**) och organiserade dem i områdena för **Axel** och **Värden**.
   
    ![Visualiseringsfönster](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Som du ser resulterade det i samma visuella objekt. Det var inte särskilt svårt att skapa det på det här sättet. Men det var ännu enklare att göra det med Frågor och svar!

## <a name="next-steps"></a>Nästa steg

- [Använda Frågor och svar på instrumentpaneler och i rapporter](power-bi-tutorial-q-and-a.md)  
- [Frågor och svar för konsumenter](../consumer/end-user-q-and-a.md)
- [Få dina data att fungera bra med Frågor och svar i Power BI](service-prepare-data-for-q-and-a.md)

Fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
