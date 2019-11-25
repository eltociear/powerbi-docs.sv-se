---
title: Vad kan jag göra med Power BI-API
description: Vad kan jag göra med Power BI-API
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 03/25/2019
ms.openlocfilehash: bbca4e5bf52ee0d4674cfcdc28edd53e90033a98
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265229"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>Vad kan utvecklare göra med Power BI-API?

Med Power BI REST API kan du skapa appar som integreras med Power BI-rapporter, -instrumentpaneler och -paneler.

Med Power BI REST API är det möjligt att utföra hanteringsuppgifter på Power BI-objekt som rapporter, datauppsättningar och arbetsytor.

Här följer några av de saker som du kan göra med Power BI-API:er.

| **Läs mer** | **Använd följande information** |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| Bädda in rapporter, instrumentpaneler och paneler för Power BI-användare och icke-Power BI-användare. | [Så här bäddar du in dina instrumentpaneler, rapporter och paneler i Power BI ](embedding-content.md) |
| Utföra hanteringsuppgifter på Power BI-objekt. | [Power BI REST API-referens](https://docs.microsoft.com/rest/api/power-bi/) |
| Utöka ett befintligt business-arbetsflöde för att skicka viktiga data till en Power BI-instrumentpanel. | [Skicka data till en instrumentpanel ](walkthrough-push-data.md) |
| Autentisera till Power BI. | [Autentisera till Power BI ](get-azuread-access-token.md) |

> [!NOTE]
> I API:erna för Power BI kallas arbetsytor fortfarande för grupper. Referenser till grupper innebär att du arbetar med arbetsytor.

## <a name="api-developer-tools"></a>API-utvecklarverktyg

| Verktyg | Beskrivning |  |  |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| [Testplatsverktyg](https://microsoft.github.io/PowerBI-JavaScript/demo) | Se ett fullständigt exempel på hur du använder Power BI JavaScript-API:erna. Det här verktyget är också ett snabbt sätt att leka med olika typer av Power BI Embedded-exempel. |  |  |
| [Power BI JavaScript-wiki](https://github.com/Microsoft/powerbi-javascript/wiki) | Mer information om Power BI JavaScript-API:erna. |  |  |
| [Postman](https://www.getpostman.com/) | Köra begäranden, testa, felsöka, övervaka, köra automatiska tester och mycket mer. |

## <a name="push-data-into-power-bi"></a>Skicka data till Power BI

Du kan använda Power BI-API:et för att [skicka data till en datauppsättning](walkthrough-push-data.md). Den här funktionen låter dig lägga till en rad i en tabell i en datauppsättning. Den nya informationen återspeglas sedan i panelerna på en instrumentpanel och i visuella objekt i rapporten.

![Dataexempel på push-överföring](media/what-can-you-do/powerbi-push-data.png)

## <a name="github-repositories"></a>GitHub-databaser

* [Power BI Developer-exempel](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)

## <a name="next-steps"></a>Nästa steg

* [Skicka data till en datauppsättning](walkthrough-push-data.md)
* [Utveckla ett anpassat visuellt objekt i Power BI](visuals/custom-visual-develop-tutorial.md)
* [Power BI REST API-referens](rest-api-reference.md)
* [REST API:er för Power BI](https://docs.microsoft.com/rest/api/power-bi/)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
