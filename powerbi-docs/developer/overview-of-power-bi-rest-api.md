---
title: Vad kan jag göra med Power BI-API
description: Vad kan jag göra med Power BI-API
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 05/25/2018
ms.author: maghan
ms.openlocfilehash: 3b19740616e7b9a390a883fde2fd96320de7b94a
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2018
ms.locfileid: "45973596"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>Vad kan utvecklare göra med Power BI-API?

Power BI visar instrumentpaneler som är interaktiva och som kan skapas och uppdateras från många olika datakällor i realtid. Du kan skapa appar som integreras med en Power BI-instrumentpanel i realtid med alla programmeringsspråk som har stöd för REST-anrop. Du kan också integrera Power BI-paneler och -rapporter i appar.

Utvecklare kan också skapa egna datavisualiseringar som kan användas i interaktiva rapporter och instrumentpaneler.

Här följer några av de saker som du kan göra med Power BI-API:er.

| **Om du vill** | **Gå hit** |
| --- | --- |
| Bädda in instrumentpaneler, rapporter och paneler för Power BI-användare och icke-Power BI-användare (appen äger data) |[Hur du bäddar in dina Power BI-instrumentpaneler, -rapporter och -paneler](embedding-content.md) |
| Utöka ett befintligt business-arbetsflöde för att skicka viktiga data till en Power BI-instrumentpanel. |[Skicka data till en instrumentpanel](walkthrough-push-data.md) |
| Autentisera till Power BI. |[Autentisera till Power BI](get-azuread-access-token.md) |
| Skapa ett anpassat visuellt objekt. |[Använd utvecklarverktyg för att skapa ett anpassat visuellt objekt](../service-custom-visuals-getting-started-with-developer-tools.md) |

> [!NOTE]
> Power BI-API:er refererar fortfarande till apparbetsytor som grupper. Alla referenser till grupper innebär att du arbetar med apparbetsytor.

## <a name="power-bi-developer-samples"></a>Power BI Developer-exempel

Power BI Developer-exempel innehåller objekt för att bädda in instrumentpaneler, rapporter och paneler.

[Power BI Developer-exempel](https://github.com/Microsoft/PowerBI-Developer-Samples)

* Exempel inom **App äger data** är avsedda för inbäddning med användare utan Power BI.
* Exempel inom **Användaren äger data** är avsedda för inbäddning med användare utan Power BI.

## <a name="github-repositories"></a>GitHub-databaser

* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)
* [Anpassade visuella objekt](https://github.com/Microsoft/PowerBI-visuals)

## <a name="developer-tools"></a>Utvecklarverktyg

Följande är ett verktyg som du kan använda för att underlätta när du utvecklar Power BI-objekt.

Med [verktyget för inbäddningskonfiguration](https://aka.ms/embedsetup) kommer du snabbt igång och kan ladda ned ett exempelprogram som beskriver hur du bäddar in Power BI-innehåll.

Välj den lösning som passar dig:

* [Inbäddning för dina kunder](embedding.md#embedding-for-your-customers) ger dig möjlighet att bädda in instrumentpaneler och rapporter för användare som inte har något Power BI-konto. Kör lösningen [Embed for your customers](https://aka.ms/embedsetup/AppOwnsData) (Bädda in för dina kunder).

* [Inbäddning för din organisation](embedding.md#embedding-for-your-organization) låter dig utöka Power BI-tjänsten. Kör lösningen [Embed for your organization](https://aka.ms/embedsetup/UserOwnsData) (Bädda in för din organisation).

Du kan använda ett fullständigt exempel i JavaScript API i [Playground-verktyget](https://microsoft.github.io/PowerBI-JavaScript/demo). Det här verktyget är ett snabbt sätt att leka med olika typer av Power BI Embedded-exempel. Du kan också få mer information om API:et för JavaScript genom att besöka wiki-sidan för [PowerBI-JavaScript](https://github.com/Microsoft/powerbi-javascript/wiki).

## <a name="push-data-into-power-bi"></a>Skicka data till Power BI

Du kan använda Power BI-API:et för skicka data till en datauppsättning. Den här funktionen låter dig lägga till en rad i en tabell i en datauppsättning. Den nya informationen kan sedan återspeglas i panelerna på en instrumentpanel och i visuella objekt i rapporten.

![Dataexempel på push-överföring](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Nästa steg

[Skicka data till en datauppsättning](walkthrough-push-data.md)  
[Komma igång med utvecklarverktyg för anpassade visuella objekt](../service-custom-visuals-getting-started-with-developer-tools.md)  
[Power BI REST API-referens](https://docs.microsoft.com/rest/api/power-bi/)  

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)
