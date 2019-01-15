---
title: Komma igång med Power BI – vanliga frågor och svar
description: Kom igång med Frågor och svar i Power BI-tjänsten med hjälp av exemplet Detaljhandelsanalys
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 87783b928fdec1cadf5318ae184858c37daa4acc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279261"
---
# <a name="get-started-with-power-bi-qa"></a>Komma igång med Power BI – vanliga frågor och svar

Ibland är det snabbaste sättet att få svar från dina data att ställa en fråga med hjälp av naturligt språk.  I den här snabbstarten ska vi titta på två olika sätt att skapa samma visualisering: bygga den i en rapport och därefter ställa en fråga med Frågor och svar. Vi använder Power BI-tjänsten, men processen är nästan identisk med Power BI Desktop.

Om du vill följa med, måste du använda en rapport som du kan redigera så vi använder ett av de exempel som finns tillgängliga i Power BI.

## <a name="create-a-visual-in-the-report-editor"></a>Skapa ett visuellt objekt i rapportredigeraren

1. Välj **Hämta data** \> **Exempel** \> **Exempel på detaljhandelsanalys**  >   **Anslut** från din Power BI-arbetsyta.
   
2. Instrumentpanelen innehåller en ytdiagramspanel för ”förra årets försäljning och det här årets försäljning”.  Välj den här panelen. Om den här panelen skapades med Frågor och svar, öppnas Frågor och svar om du väljer den. Men den här panelen skapades i en rapport så rapporten öppnas på den sida som innehåller den här visualiseringen.

    ![Instrumentpanelen för Exempel på detaljhandelsanalys](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Öppna rapporten i redigeringsvyn genom att välja **Redigera rapport**.  Om du inte är ägare till en rapport kan du inte öppna den i redigeringsvyn.
   
    ![Knappen Redigera rapport](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Välj ytdiagrammet och granska inställningarna i **Fält**-fönstret.  Rapportskaparen byggde det här diagrammet genom att välja dessa tre värden (**Tid > FiscalMonth (Räkenskapsmånad)**, **Försäljning > This Year Sales (Årets försäljning)**, **Försäljning > Last Years Sales (Förra årets försäljning) > Värde**) och ordna dem i områdena **Axel** och **Värden**.
   
    ![Visualiseringsfönster](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="create-the-same-visual-with-qa"></a>Skapa samma visuella objekt med frågor och svar

Hur skapar vi samma linjediagram med Frågor och svar?

![Ställa fråga i en frågeruta](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Gå tillbaka till instrumentpanelen för Exempel på detaljhandelsanalys.
2. Med hjälp av naturligt språk skriver du in något i stil med följande i frågerutan:
   
   **hur såg årets och förra årets försäljning ut per månad som ytdiagram**
   
   När du skriver din fråga väljer Frågor och svar den bästa visualiseringen för att visa ditt svar och visualiseringen ändras dynamiskt när du ändrar frågan. Frågor och svar hjälper dig också formatera din fråga med förslag, automatisk komplettering och stavningskorrigeringar.
   
   När du har skrivit klart frågan är resultatet exakt samma diagram som vi såg i rapporten.  Men det gick mycket snabbare att skapa det på det här viset!
   
   ![Exempel på fråga](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. På liknande sätt som när du arbetar med rapporter, har du i Frågor och svar också åtkomst till fönstren Visualiseringar, Filter och Fält.  Öppna dessa fönster för att utforska och ändra ditt visuella objekt ytterligare.
4. Välj fästikonen för att fästa diagrammet på din instrumentpanel ![Fästikon](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png).

## <a name="next-steps"></a>Nästa steg
[Frågor och svar i Power BI](consumer/end-user-q-and-a.md)

[Få dina data att fungera bra med Frågor och svar i Power BI](service-prepare-data-for-q-and-a.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

