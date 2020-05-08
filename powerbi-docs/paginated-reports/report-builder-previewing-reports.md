---
title: Förhandsgranska rapporter i Power BI Report Builder
description: När du skapar en sidnumrerad rapport i Report Builder är det användbart att förhandsgranska rapporten ofta för att kontrollera att den visar det du vill.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: afbc31e3ece8bc72ad52bb2fe7c3d871b2f68e1b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "78922952"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Förhandsgranska rapporter i Power BI Report Builder
  När du skapar en sidnumrerad rapport i Report Builder är det användbart att förhandsgranska rapporten ofta för att kontrollera att den visar det du vill. Du förhandsgranskar rapporten genom att klicka på **Kör**. Rapporten renderas i förhandsgranskningsläge.  
  
 Report Builder förbättrar funktionen för förhandsgranskning med hjälp av redigeringssessioner när den är ansluten till en rapportserver. Redigeringssessionen skapar en datacache och tillgängliggör datamängderna i cacheminnet för upprepade rapportförhandsgranskningar. En redigeringssession är inte en funktion som du interagerar med direkt, men om du vet när den cachelagrade datamängden uppdateras blir det enklare att förbättra prestanda när du förhandsgranskar en rapport och förstå varför rapporten renderas snabbare eller långsammare.  

  
> [!NOTE]  
> Det finns några skillnader mellan att förhandsgranska i Report Builder och visa i en webbläsare. Till exempel är en kalenderkontroll, som läggs till i en rapport när du anger en datum/tid-parametertyp, annorlunda i Report Builder och i en webbläsare. 
  
## <a name="improving-preview-performance"></a>Förbättra prestanda för förhandsgranskning  
 Hur du skapar och uppdaterar rapporter påverkar hur snabbt rapporten renderas i en förhandsgranskning. Första gången du förhandsgranskar en rapport som förlitar sig på en serverreferens skapas en redigeringssession, och de data som används när rapporten körs läggs till i en datacache som lagras. När du gör ändringar i rapporten som inte påverkar data används den cachelagrade kopian av data av rapporten. Det innebär att du inte ser dataändringar varje gång du förhandsgranskar rapporten. Om du vill se nya data klickar du på knappen **Uppdatera** i menyfliksområdet.  
  
 Följande åtgärder gör att cachen uppdateras och gör rapportåtergivningen långsammare nästa gång du förhandsgranskar rapporten:  
  
-   Lägg till, ändra eller ta bort en datamängd. Den cachelagrade datamängden innehåller alla datamängder som en rapport använder, och ändringar av någon datamängd gör den cachelagrade datamängden ogiltig. Detta omfattar att ändra namn, fråga eller fält i datamängden.  
  
    > [!NOTE]  
    >  Om datamängden har ett stort antal fält som du inte räknar med att använda bör du uppdatera datamängden så att de fälten inte tas med. Även om detta skapar en ny redigeringssession och den första förhandsversionen av rapporten blir långsammare är den mindre cachelagrade datamängden totalt sett till gagn för rapportserverns prestanda.  
  
-   Lägg till, ändra eller ta bort en datakälla. Detta omfattar att ändra namnet eller egenskaper för datakällan, datatillägget för datakällan eller egenskaperna för anslutningen till datakällan.  
  
-   Ändra den datakälla som rapporten använder till en annan datakälla.  
  
-   Ändra språket i rapporten.  
  
-   Ändra de sammansättningar eller den anpassade kod som rapporten använder.  
  
-   Lägga till, ändra eller ta bort frågeparametrarna i rapporten eller parametervärdena.  
  
 Ändringar av rapportlayouten och dataformateringen påverkar inte den cachelagrade datamängden. Du kan vidta följande åtgärder utan att uppdatera den cachelagrade datamängden:  
  
-   Lägga till eller ta bort dataområden såsom tabeller, matriser eller diagram.  
  
-   Lägga till eller ta bort kolumner från rapporten. Alla fält i datamängden är tillgängliga för användning i rapporten. Tillägg eller borttagning av fält i rapporten påverkar inte datamängden.  
  
-   Ändra ordning på fälten i tabeller och matriser.  
  
-   Lägga till, ändra eller ta bort radgrupper och kolumngrupper.  
  
-   Lägga till, ändra eller ta bort formatering av datavärden i fält.  
  
-   Lägga till, ändra eller ta bort bilder, linjer eller textrutor.  
  
-   Ändra sidbrytningar.  
  
Redigeringssessionen skapas första gången du förhandsgranskar en rapport. Som standard varar en redigeringssession 7 200 sekunder (2 timmar). Sessionen återställs till två timmar varje gång du kör rapporten. När redigeringssessionen upphör tas datacachen bort. Om redigeringssessionen upphör skapas en till automatiskt nästa gång du förhandsgranskar rapporten.
  
Som standard kan datacachen innehålla upp till fem datamängder. Om du använder många olika kombinationer av parametervärden kan rapporten behöva mer data. Detta kräver att cachen uppdateras och rapporten renderas långsammare nästa gång du förhandsgranskar den. 
  
## <a name="concurrency-of-report-updates"></a>Samtidighet för rapportuppdateringar  
Ofta förhandsgranskar du en rapport som ett steg i att uppdatera och sedan spara en rapport i Power BI-tjänsten. När du uppdaterar en rapport är det möjligt att någon annan uppdaterar och sedan sparar rapporten samtidigt. Den rapport som sparas sist är den version av rapporten som är tillgänglig för framtida visning och uppdatering. Det innebär att den version av rapporten som du förhandsgranskade kanske inte är den version du öppnar igen. Du har möjligheten att spara rapporten med ett nytt namn med hjälp av alternativet **Spara som** på Report Builder-menyn.  
  
## <a name="external-report-items"></a>Externa rapportobjekt  
 Rapporten kan innehålla objekt såsom externa bilder som lagras separat från rapporten. Eftersom objekten lagras separat är det möjligt att de kan flyttas till en annan plats eller tas bort. Om detta inträffar kan rapporten misslyckas med att förhandsgranskas. Du kan antingen uppdatera rapporten för att ange objektets uppdaterade plats eller, om objektet togs bort, ersätta det med ett befintligt objekt eller ta bort referensen till objektet från rapporten.  
  
## <a name="next-steps"></a>Nästa steg

- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
  
