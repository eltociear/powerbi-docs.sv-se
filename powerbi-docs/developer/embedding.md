---
title: Inbäddade analyser med Power BI
description: Power BI erbjuder API:er för att använda inbäddade analyser till dina instrumentpaneler och rapporter i program. Lär dig mer om inbäddning med Power BI både i en PaaS-miljö och en SaaS-miljö genom att använda programvara för inbäddad analys, inbäddade analysverktyg eller inbäddade Business Intelligence-verktyg.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: a212691f2af877e3b86e021a4f48644f4fa6e8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051075"
---
# <a name="embedded-analytics-with-power-bi"></a>Inbäddade analyser med Power BI

Power BI-tjänsten (SaaS) och Power BI Embedded-tjänsten i Azure (PaaS) har API:er för inbäddning av dina instrumentpaneler och rapporter. När du bäddar in innehåll, får det här du tillgång till de senaste Power BI-funktionerna, till exempel instrumentpaneler, gatewayer och apparbetsytor.

Med [konfigurationsverktyget för inbäddning](https://aka.ms/embedsetup) kommer du snabbt igång och kan ladda ned ett exempelprogram.

Välj den lösning som passar dig:

* [Inbäddning för din organisation](embedding.md#embedding-for-your-organization) låter dig utöka Power BI-tjänsten. Om du vill göra detta måste implementera de [bädda in för din organisation](https://aka.ms/embedsetup/UserOwnsData) lösning.
* [Inbäddning för dina kunder](embedding.md#embedding-for-your-customers) kan du bädda in instrumentpaneler och rapporter till användare som inte har en Power BI-konto. Om du vill göra detta måste implementera de [inbäddning för dina kunder](https://aka.ms/embedsetup/AppOwnsData) lösning.

![PBIE-exempel](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>Använd API: er

Det finns två huvudscenarier för att bädda in Power BI-innehåll:
- Inbäddning för din organisations användare (som har licenser för Power BI). 
 
- Inbäddning för dina användare och kunder som inte behöver Power BI-licenser. 

Den [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) tillåter båda scenarierna.

För kunder och användare utan Power BI-licenser, kan du kan bädda in instrumentpaneler och rapporter i ditt anpassade program, med samma API både till din organisation och dina kunder. Dina kunder Se program-hanterade data. Dessutom din organisations Power BI-användare har fler alternativ för att visa *sina data* direkt i Power BI eller i kontexten för det inbäddade programmet. Du kan dra full nytta av JavaScript och REST API:er för dina inbäddningsbehov.

Information om hur inbäddning fungerar finns i den [JavaScript-inbäddningsexempel](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inbäddning för din organisation

**Inbäddning för din organisation** låter dig utöka Power BI-tjänsten. Den här bäddar in kräver ditt programs användare som loggar in Power BI-tjänsten för att visa innehållet. När någon i din organisation loggar in kommer de endast att ha åtkomst till instrumentpaneler och rapporter som de äger eller som någon har delat med dem i Power BI-tjänsten.

Bädda in exempel för organisation inkluderar interna program, till exempel [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [Microsoft Teams-integrering (du måste ha administratörsrättigheter)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/), och [Microsoft Dynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Om du vill bädda in för din organisation, se [självstudien: Bädda in Power BI-innehåll i ett program för din organisation](embed-sample-for-your-organization.md).

Självbetjäningsfunktioner, som redigering, spara och mycket mer finns tillgängligt via [JavaScript API:t](https://github.com/Microsoft/PowerBI-JavaScript) vid inbäddning för Power BI-användare.

Du kan gå igenom den [bädda in installationsverktyget](https://aka.ms/embedsetup/UserOwnsData) att komma igång och ladda ned ett exempelprogram som vägleder dig genom att integrera en rapport för din organisation.

## <a name="embedding-for-your-customers"></a>Inbäddning för dina kunder

**Inbäddning för dina kunder** kan du bädda in instrumentpaneler och rapporter för användare som inte har en Power BI-konto. Den här inbäddning kallas även *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) är en **Microsoft Azure** tjänst som låter oberoende programvaruleverantörer (ISV) och utvecklare snabbt bädda in visuella objekt, rapporter och instrumentpaneler i ett program. Den här inbäddning görs via en kapacitetsbaserad, per timme förbrukade modell.

![Inbäddningsflöde för inbäddning för dina kunder](media/embedding/powerbi-embed-flow.png)

Power BI Embedded har fördelar för oberoende programvaruleverantörer, utvecklare och kunder. En ISV kan till exempel börja skapa visuella objekt utan kostnad med Power BI Desktop. Genom att minimera visuell analytisk utveckling, ISV: er för att uppnå kortare tid till marknad och skiljer sig från konkurrenterna med differentierade dataupplevelser. ISV: er kan också välja för att debitera en avgift för det ytterligare värde som de har skapat med inbäddad analys.

Med Power BI Embedded behöver dina kunder inte känna till något om Power BI. Du kan använda två olika metoder för att skapa ett inbäddat program:
- Power BI Pro-konto 
- Tjänstens huvudnamn 

Power BI Pro-kontot fungerar som huvudkonto för ditt program (se det som ett proxykonto). Det här kontot kan du generera inbäddningstokens som ger åtkomst till ditt programs Power BI-instrumentpaneler och rapporter.

[Tjänstens huvudnamn](embed-service-principal.md) kan bädda in Power BI-innehåll i ett program med en **appspecifik** token. Det också möjligt att generera inbäddningstokens som ger åtkomst till ditt programs Power BI-instrumentpaneler och rapporter.

Utvecklare som använder Power BI Embedded kan ägna tid på att skapa programmets kärnfunktioner snarare än utgiftsgränsen tid utveckla visuella objekt och analyser. De kan snabbt uppfylla kundens krav på rapportering och instrumentpaneler och enkelt bäddas in med fullständigt dokumenterade API: er och SDK: er. Med lättnavigerad datautforskning i apparna kan ISV:er göra det enklare för kunderna att fatta snabba, datadrivna och sammanhangsberoende beslut på valfri enhet.

> [!IMPORTANT]
> När du bäddar in kräver Power BI-tjänsten, behöver inte dina kunder har en Power BI-konto för att visa ditt programs inbäddade innehåll. 

När du är redo att flytta till produktion, måste din apparbetsyta tilldelas till en dedikerad kapacitet. Power BI Embedded i Microsoft Azure erbjuder [dedikerade kapaciteter](azure-pbie-create-capacity.md) att använda med dina program.

Bädda in information, se [hur du bäddar in Power BI-innehåll](embed-sample-for-customers.md).

## <a name="next-steps"></a>Nästa steg

Du kan nu försöka att bädda in Power BI-innehåll i ett program eller försöka bädda in Power BI-innehåll för dina kunder.

> [!div class="nextstepaction"]
> [Bädda in för din organisation](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [Vad är Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Bädda in för dina kunder](embed-sample-for-customers.md)

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)
