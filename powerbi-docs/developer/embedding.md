---
title: Bädda in med Power BI
description: Power BI erbjuder API:er för att bädda in dina instrumentpaneler och rapporter i program.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 06/22/2018
ms.author: maghan
ms.openlocfilehash: 82a4c9c58567f5ace943363b7bed59fa744e85a5
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "36944110"
---
# <a name="embedding-with-power-bi"></a>Bädda in med Power BI
Power BI erbjuder API:er för att bädda in dina instrumentpaneler och rapporter i program. Power BI-API:erna ger dig en konsekvent uppsättning funktioner och tillgång till de senaste funktionerna i Power BI när du bäddar in funktioner som instrumentpaneler, gatewayer och apparbetsytor.

## <a name="a-single-api"></a>Ett enda API
Det finns två huvudscenarier när du bäddar in Power BI-innehåll.  Inbäddning för användare i din organisation (som har licenser för Power BI) och inbäddning för dina användare och kunder utan att de behöver ha licenser för Power BI. Power BI REST API tillåter båda scenarierna. 

För kunder och användare utan Power BI-licenser, kan du kan bädda in instrumentpaneler och rapporter i ditt anpassade program, med samma API både till din organisation och dina kunder. Kunderna ser de data som hanteras av programmet. Och för Power BI-användare i din organisation, har de fler alternativ för att visa *sina egna data* direkt i Power BI eller i kontext med det inbäddade programmet. Du kan dra full nytta av JavaScript och REST API:er för dina inbäddningsbehov.

Ett exempel på hur inbäddning fungerar finns i [JavaScript-inbäddningsexempel](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inbäddning för din organisation
Inbäddning för din organisation låter dig utöka Power BI-tjänsten. Detta kräver att slutanvändaren av ditt program loggar in på Power BI-tjänsten när de vill visa sitt innehåll. När någon i din organisation loggar in, kommer de endast att ha åtkomst till instrumentpaneler och rapporter som de äger eller som har delats med dem i Power BI-tjänsten. 

*Exempel på inbäddning för din organisation inkluderar interna webbprogram, webbdelen för SharePoint Online och [Microsoft Teams-integrering (du måste ha administratörsrättigheter)](https://powerbi.microsoft.com/en-us/blog/power-bi-teams-up-with-microsoft-teams/).*

Se följande för inbäddning för din organisation:

* [Integrera en rapport i en app](integrate-report.md)
* [Integrera en instrumentpanel i en app](integrate-dashboard.md)
* [Integrera en panel i en app](integrate-tile.md)

Självbetjäningsfunktioner, som redigering, spara och mycket mer finns tillgängligt via [JavaScript API:t](https://github.com/Microsoft/PowerBI-JavaScript) vid inbäddning för Power BI-användare.

Med [integrationsverktyget för inbäddning för din organisation](https://aka.ms/embedsetup/UserOwnsData) kommer du snabbt igång och kan ladda ned ett exempelprogram som steg för steg beskriver hur du integrerar en rapport för din organisation.

## <a name="embedding-for-your-customers"></a>Inbäddning för dina kunder
Inbäddning för dina kunder ger dig möjligheten att bädda in instrumentpaneler och rapporter till användare som inte har ett konto för Power BI. Dina kunder behöver inte känna till något om Power BI. Minst ett Power BI Pro-konto krävs för att skapa ett inbäddat program. Power BI Pro-kontot fungerar som ett huvudkonto för ditt program. Tänk på det som ett proxykonto. Power BI Pro-kontot låter dig även generera inbäddningstokens som ger åtkomst till instrumentpaneler och rapporter i Power BI-tjänsten som ägs/hanteras av ditt program. 

*Ett exempel på inbäddning för dina kunder är ett ISV-program som säljs till andra företag.*

![Inbäddningsflöde för inbäddning för dina kunder](media/embedding/powerbi-embed-flow.png)

Om du vill bädda in instrumentpaneler, rapporter och paneler, använder du samma API:er som du använder för att bädda in för din organisation.

> [!IMPORTANT]
> Även om inbäddning är beroende av Power BI-tjänsten så finns det inget beroende av Power BI för dina kunder. De behöver inte registrera sig för Power BI om du vill visa ditt programs inbäddade innehåll.
> 

När du är redo att flytta till produktion, måste din apparbetsyta tilldelas en kapacitet. Power BI Embedded i Microsoft Azure, erbjuder kapacitet för att använda med program.

Mer information om hur du bäddar in finns i [Så här bäddar du in dina Power BI-instrumentpaneler, rapporter och paneler](embedding-content.md).

Med [integrationsverktyget för inbäddning för dina kunder](https://aka.ms/embedsetup/AppOwnsData) kommer du snabbt igång och kan ladda ned ett exempelprogram som steg för steg beskriver hur du integrerar en rapport i ditt program.

Om du använder tjänsten Power BI-arbetsytesamlingar i Azure, se [Migrera innehåll från Azure-tjänsten Power BI-arbetsytesamlingar](migrate-from-powerbi-embedded.md) för information om hur du migrerar över ditt innehåll.

## <a name="next-steps"></a>Nästa steg
[Så här bäddar du in dina Power BI-instrumentpaneler, -rapporter och -paneler](embedding-content.md)  
[Så här migrerar du innehåll från Power BI Embedded-arbetsytesamlingar till Power BI](migrate-from-powerbi-embedded.md)  
[Power BI Premium – vad är det?](../service-premium.md)  
[JavaScript API Git Repo](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git Repo](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript-inbäddningsexempel](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[White paper om kapacitetsplanering för inbäddad analys](https://aka.ms/pbiewhitepaper)  
[Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

