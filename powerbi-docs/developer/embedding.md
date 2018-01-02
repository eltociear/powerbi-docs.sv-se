---
title: "Bädda in med Power BI"
description: "Power BI erbjuder API:er för att bädda in dina instrumentpaneler och rapporter i program."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/05/2017
ms.author: asaxton
ms.openlocfilehash: 36eb4231b6b3d3278d571722bde731051ffdf05e
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="embedding-with-power-bi"></a>Bädda in med Power BI
Power BI erbjuder API:er för att bädda in dina instrumentpaneler och rapporter i program. Power BI-API:erna ger dig en konsekvent uppsättning funktioner och tillgång till de senaste funktionerna i Power BI när du bäddar in funktioner som instrumentpaneler, gatewayer och apparbetsytor.

## <a name="a-single-api"></a>Ett enda API
Det finns två huvudscenarier när du bäddar in Power BI-innehåll. Bädda in för din organisation och bädda in för dina kunder. Power BI REST API tillåter båda scenarierna. Det här låter dig bädda in instrumentpaneler och rapporter i ditt anpassade program, med samma API antingen till din organisation eller dina kunder. Du kan dra full nytta av JavaScript och REST API:er för dina inbäddningsbehov.

Ett exempel på hur inbäddning fungerar finns i [JavaScript-inbäddningsexempel](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inbäddning för din organisation
Inbäddning för din organisation låter dig utöka Power BI-tjänsten. Detta kräver att slutanvändaren av ditt program loggar in på Power BI-tjänsten när du vill visa ditt innehåll. När någon i din organisation loggar in, kommer de endast att ha åtkomst till instrumentpaneler och rapporter som har delats med dem i Power BI-tjänsten. 

*Exempel på inbäddning för din organisation inkluderar interna webbprogram, webbdelen för SharePoint Online och Microsoft Teams-integrering.*

Se följande för inbäddning för din organisation:

* [Integrera en instrumentpanel i en app](integrate-dashboard.md)
* [Integrera en panel i en app](integrate-tile.md)
* [Integrera en rapport i en app](integrate-report.md)

Självbetjäningsfunktioner, som redigering, spara och mycket mer finns tillgängligt via [JavaScript API:t](https://github.com/Microsoft/PowerBI-JavaScript) vid inbäddning för Power BI-användare.

## <a name="embedding-for-your-customers"></a>Inbäddning för dina kunder
Inbäddning för dina kunder ger dig möjligheten att bädda in instrumentpaneler och rapporter till användare som inte har ett konto för Power BI. Dina kunder behöver inte känna till något om Power BI. Minst ett Power BI Pro-konto krävs. Power BI Pro-kontot fungerar som ett huvudkonto för ditt program. Tänk på det som ett proxykonto. Power BI Pro-kontot låter dig även generera inbäddningstokens som ger åtkomst till instrumentpaneler och rapporter i Power BI-tjänsten. 

*Ett exempel på inbäddning för dina kunder är ett ISV-program som säljs till andra företag.*

![Inbäddningsflöde för inbäddning för dina kunder](media/embedding/powerbi-embed-flow.png)

Om du vill bädda in instrumentpaneler, rapporter och paneler, använder du samma API:er som du använder för att bädda in för din organisation.

> [!IMPORTANT]
> Även om inbäddning har ett beroende på Power BI-tjänsten så finns det inga beroende på Power BI för dina kunder. De behöver inte registrera sig för Power BI för att visa det inbäddade innehållet i ditt program.
> 
> 

När du är redo att flytta till produktion, måste din apparbetsyta tilldelas en kapacitet. Power BI Embedded i Microsoft Azure, erbjuder kapacitet för att använda med program.

Mer information om hur du bäddar in finns i [Så här bäddar du in dina Power BI-instrumentpaneler, rapporter och paneler](embedding-content.md).

Om du använder tjänsten Power BI-arbetsytesamlingar i Azure, se [Migrera innehåll från Azure-tjänsten Power BI-arbetsytesamlingar](migrate-from-powerbi-embedded.md) för information om hur du migrerar över ditt innehåll.

## <a name="next-steps"></a>Nästa steg
[Så här bäddar du in dina Power BI-instrumentpaneler, -rapporter och -paneler](embedding-content.md)  
[Så här migrerar du innehåll från Power BI Embedded-arbetsytesamlingar till Power BI](migrate-from-powerbi-embedded.md)  
[Power BI Premium – vad är det?](../service-premium.md)  
[JavaScript API Git Repo](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git Repo](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript-inbäddningsexempel](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Vitbok om kapacitetsplanering för inbäddad analys](https://aka.ms/pbiewhitepaper)  
[Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

