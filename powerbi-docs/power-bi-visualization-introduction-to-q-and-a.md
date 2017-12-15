---
title: "Kom igång med Frågor och svar i Power BI (självstudier)"
description: "Självstudier: Kom igång med Frågor och svar i Power BI-tjänsten med hjälp av Exempel på detaljhandelsanalys"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: 
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: 2038fb5bd4a21235c3026c8506ae30b8c3e287e4
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="get-started-with-power-bi-qa-tutorial"></a>Kom igång med Frågor och svar i Power BI (självstudier)
## <a name="tutorial-use-power-bi-qa-with-the-retail-analysis-sample"></a>Självstudier: Använda Frågor och svar för Power BI med Exempel på detaljhandelsanalys
Ibland är det snabbaste sättet att få svar från dina data att ställa en fråga med hjälp av naturligt språk.  I den här kursen ska vi titta på två olika sätt att skapa samma visualisering: bygga den i en rapport och ställa en fråga med Frågor och svar.  

## <a name="method-1-using-the-report-editor"></a>Metod 1: Använda rapportredigeraren
1. Välj **Hämta data** \> **Exempel** \> **Exempel på detaljhandelsanalys**  >   **Anslut** från din Power BI-arbetsyta.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)
2. Instrumentpanelen innehåller en ytdiagramspanel för ”förra årets försäljning och det här årets försäljning”.  Välj den här panelen. 
   
   * Om den här panelen skapades med Frågor och svar, öppnas Frågor och svar om du väljer den. 
   * Men den här panelen skapades i en rapport så rapporten öppnas på den sida som innehåller den här visualiseringen.
3. Öppna rapporten i redigeringsvyn genom att välja **Redigera rapport**.  Om du inte är ägare till en rapport kan du inte öppna den i redigeringsvyn.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Välj ytdiagrammet och granska inställningarna i **Fält**-fönstret.  Rapportskaparen byggde det här diagrammet genom att välja dessa tre värden (**Tid > FiscalMonth (Räkenskapsmånad)**, **Försäljning > This Year Sales (Årets försäljning)**, **Försäljning > Last Years Sales (Förra årets försäljning) > Värde**) och ordna dem i områdena **Axel** och **Värden**.
   
    ![](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="method-2-using-qa"></a>Metod 2: Använda Frågor och svar
Hur skapar vi samma linjediagram med Frågor och svar?

![](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Gå tillbaka till instrumentpanelen för Exempel på detaljhandelsanalys.
2. Med hjälp av naturligt språk skriver du in något i stil med följande i frågerutan:
   
   **hur såg årets och förra årets försäljning ut per månad som ytdiagram**
   
   När du skriver din fråga väljer Frågor och svar den bästa visualiseringen för att visa ditt svar och visualiseringen ändras dynamiskt när du ändrar frågan. Frågor och svar hjälper dig också formatera din fråga med förslag, automatisk komplettering och stavningskorrigeringar.
   
   När du har skrivit klart frågan är resultatet exakt samma diagram som vi såg i rapporten.  Men det gick mycket snabbare att skapa det på det här viset!
   
   ![](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. På liknande sätt som när du arbetar med rapporter, har du i Frågor och svar också åtkomst till fönstren Visualiseringar, Filter och Fält.  Öppna dessa fönster för att utforska och ändra ditt visuella objekt ytterligare.
4. Välj fästikonen ![](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) för att fästa diagrammet på din instrumentpanel.

## <a name="next-steps"></a>Nästa steg
[Vilken typ av frågor kan jag ställa i Frågor och svar?](service-q-and-a.md)

[Frågor och svar i Power BI](service-q-and-a.md)

[Få dina data att fungera bra med Frågor och svar i Power BI](service-prepare-data-for-q-and-a.md)

[Förbereda en arbetsbok för Frågor och svar](service-prepare-data-for-q-and-a.md)

Har du fler frågor? [Försök med att fråga Power BI Community](http://community.powerbi.com/)

