---
title: Använd Power BI frågor och svar att utforska och skapa visuella objekt
description: Hur du använder Power BI frågor och svar för att skapa nya visualiseringar på instrumentpaneler och rapporter.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: c6fd8967a49515af4d0614653b3d7550c335052f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625521"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>Använd Power BI frågor och svar för att utforska dina data och skapa visuella objekt

Ibland är det snabbaste sättet att få svar från dina data att ställa en fråga med hjälp av naturligt språk. Funktionen frågor och svar i Power BI kan du utforska dina data med egna ord.  Den första delen av den här artikeln visar hur du använder frågor och svar i instrumentpaneler i Power BI-tjänsten. Den andra delen visar vad du kan göra med frågor och svar när du skapar rapporter i Power BI-tjänsten eller Power BI Desktop. Mer bakgrundsinformation finns i den [frågor och svar för konsumenter](consumer/end-user-q-and-a.md) artikeln. 

[Frågor och svar i Power BI-mobilapparna](consumer/mobile/mobile-apps-ios-qna.md) och [frågor och svar med Power BI Embedded](developer/qanda.md) täcks i separata artiklar. 

Frågor och svar är interaktivt och även roliga. Ofta leder en fråga till andra när visualiseringarna avslöjar intressanta spår att följa upp. Titta när Amanda demonstrerar frågor och svar för att skapa visuella objekt, detaljgranska dem och fästa dem till instrumentpaneler.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>Del 1: Använd frågor och svar på en instrumentpanel i Power BI-tjänsten

En instrumentpanel innehåller paneler som fästs från en eller flera datauppsättningar så du kan ställa frågor om data finns i någon av de datauppsättningarna i Power BI-tjänsten (app.powerbi.com). Om du vill se vilka rapporter och datauppsättningar som användes för att skapa instrumentpanelen, **Visa relaterade** på menyraden.

![Visa relaterade rapporter och datauppsättningar](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Frågerutan frågor och svar finns i det övre vänstra hörnet på instrumentpanelen, där du skriver din fråga med naturligt språk. Ser du frågor och svar? Se [överväganden och felsökning](consumer/end-user-q-and-a.md#considerations-and-troubleshooting) i den **frågor och svar för konsumenter** artikeln.  Frågor och svar kan du identifiera de ord du skriver och räknat ut var (i vilken datauppsättning) för att hitta svaret. Frågor och svar hjälper dig också att formulera din fråga med automatisk komplettering, omformulering och andra textbaserade och visuella hjälpmedel.

![Frågor och svar](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

Svaret på din fråga visas som en interaktiv visualisering och uppdateras allteftersom du ändrar frågan.

1. Öppna en instrumentpanel och placera din markör i frågerutan. I det övre högra hörnet väljer **nya frågor och svar en upplevelse**.

    ![Power BI nya Q & en upplevelse](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. Innan du ens börjar skriva, visar frågor och svar en ny skärm med förslag för att hjälpa dig formulera din fråga. Du ser fraser och fullständiga frågor som innehåller namnen på tabellerna i de underliggande datauppsättningarna och kan även se fullständiga frågor listade om datauppsättningens ägare har skapat [aktuella frågor](service-q-and-a-create-featured-questions.md),

   ![Frågor och svar förslag på frågor](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   Du kan välja någon av de här frågorna som en startpunkt och fortsätta att förfina frågan för att hitta ett visst svar. Eller Använd ett tabellnamn för att uttrycka en ny fråga.

2. Välj i listan med frågor, eller börja skriva en egen fråga och välj från förslagen i listrutan.

   ![Välj en fråga i listan](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. När du skriver en fråga väljer frågor och svar den bästa visualiseringen att visa ditt svar.

   ![Frågor och svar hur många lagrar efter delstat](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. Visualiseringen ändras medan du ändrar frågan.

   ![Frågor och svar hur många lagrar efter delstat som liggande diagram](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. Medan du skriver en fråga, letar Power BI efter det bästa svaret i alla datauppsättningar som har en panel på den instrumentpanelen.  Om alla paneler är från *datauppsättning A* så kommer ditt svar att komma från *datauppsättning A*.  Om det finns paneler från *datauppsättning a* och *datauppsättning b*, sedan frågor och svar söker efter det bästa svaret från de 2 datauppsättningarna.

   > [!TIP]
   > Så var försiktig, om du bara har en panel från *datauppsättning A* och du tar bort den från instrumentpanelen, kommer frågor och svar inte längre att ha åtkomst till *datauppsättning A*.
   >

5. När du är nöjd med resultatet, Fäst visualiseringen på en instrumentpanel genom att välja fästikonen i det övre högra hörnet. Om instrumentpanelen har delats med dig, eller är en del av en app, kan du inte fästa.

   ![Frågor och svar fästa det visuella objektet](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Del 2: Använd frågor och svar i en rapport i Power BI-tjänsten eller Power BI Desktop

Använd frågor och svar för att utforska dina datauppsättningar och lägga till visualiseringar i rapporten och instrumentpanelerna. En rapport är baserad på en enda datauppsättning och kan vara helt tom eller innehålla mängder av sidor med visualiseringar. Men bara för att en rapport är tom, behöver det inte betyda att det inte finns några data som du kan utforska – datauppsättningen är länkad till rapporten och väntar på att du ska utforska den och skapa visualiseringar.  Om du vill se vilken datauppsättning som används för att skapa en rapport så öppnar du rapporten i Power BI-tjänstens läsvy och väljer **Visa relaterade** från menyraden.

![Visa relaterade datauppsättningar](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Om du vill använda frågor och svar i rapporter, måste du ha behörighet att redigera rapporten och underliggande datauppsättningen. I den [frågor och svar för konsumenter](consumer/end-user-q-and-a.md) artikel, som vi refererar till detta som en *creator* scenario. Om du är i stället *förbrukar* en rapport som har delats med dig, frågor och svar är inte tillgänglig.

1. Öppna en rapport i redigeringsvyn (Power BI-tjänsten) eller rapportvyn (Power BI Desktop) och välj **Ställ en fråga** på menyraden.

    **Power BI Desktop**    
    ![Välj Ställ en fråga i Power BI Desktop](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Tjänsten**    
    ![Välj Ställ en fråga i Power BI-tjänsten](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. En frågor och svar-frågeruta visas på din rapportarbetsyta. I exemplet nedan visas frågerutan ovanpå en annan visualisering. Det fungerar, men det kan vara bättre att lägga till en tom sida i rapporten innan du ställer en fråga.

    ![Frågor och svar](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Placera markören i frågerutan. När du skriver, visar frågor och svar förslag för att hjälpa dig att skapa din fråga.

   ![Skriv i frågor och svar](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. Allteftersom du skriver in en fråga så väljer frågor och svar den bästa [visualiseringen ](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)för att visa ditt svar. Visualiseringen ändras dynamiskt medan du ändrar frågan.

   ![Frågor och svar skapar en visualisering](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. När du har den visualiseringen som du vill ha, väljer du RETUR. Om du vill spara visualiseringen rapporten, väljer du **Fil > Spara**.

6. Interagera med den nya visualiseringen. Det spelar ingen roll hur du skapade visualiseringen – samma interaktivitet, formatering och funktioner finns tillgängliga oavsett.

   ![Interagera med visualiseringen](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Om du skapade visualiseringen i Power BI-tjänsten, kan du till och med [fästa den på en instrumentpanel](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Berätta för Frågor och svar vilket visuellt objekt som ska användas
Med frågor och svar, kan du inte bara be dina data att tala för sig själva, du kan säga hur Power BI ska visa svaret. Lägg bara till som en <visualization type> i slutet av din fråga.  Till exempel visa lagervolymer efter anläggning som en karta och visa totalt lager som ett kort.  Prova själv.

## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning
- Om du har anslutit till en datauppsättning med en live-anslutning eller gateway, behöver frågor och svar vara [aktiverat för den datauppsättningen](service-q-and-a-direct-query.md).

- Du har öppnat en rapport och ser inte frågor och svar-alternativet. Om du använder Power BI-tjänsten, se till att du öppnar rapporten i Redigeringsvyn. Om du inte kan öppna redigeringsvyn innebär det att du inte har behörighet att redigera rapporten och du kan använda frågor och svar med just den rapporten.

## <a name="next-steps"></a>Nästa steg

- [Frågor och svar för konsumenter](consumer/end-user-q-and-a.md)   
- [Tips för att ställa frågor i frågor och svar](consumer/end-user-q-and-a-tips.md)   
- [Förbered en arbetsbok för frågor och svar](service-prepare-data-for-q-and-a.md)  
- [Förbered en lokal datauppsättning för frågor och svar](service-q-and-a-direct-query.md)   
- [Fäst en panel på instrumentpanelen från frågor och svar](service-dashboard-pin-tile-from-q-and-a.md)
