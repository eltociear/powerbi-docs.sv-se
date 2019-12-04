---
title: Ansluta en rapport till en datamängd med hjälp av dynamisk bindning
description: Lär dig hur du bäddar in en rapport med dynamisk bindning.
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: f797dd55202ff4cba87cc3a15601d85091e94823
ms.sourcegitcommit: c839ef7437bc8fb8f7eeda23e59d05c7192a7fe8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164055"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>Ansluta en rapport till en datamängd med hjälp av dynamisk bindning 

När en rapport är ansluten till en datamängd kan du använda dynamisk bindning. Anslutningen mellan rapporten och datamängden kallas *bindning*. När bindningen fastställs vid inbäddningen, i stället för att vara fördefinierad från tidigare, kallas bindningen för en [dynamisk bindning](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FLate_binding&data=02%7C01%7CKesem.Sharabi%40microsoft.com%7C5d5b0d2d62cf4818f0c108d7635b151e%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C637087115150775585&sdata=AbEtdJvgy4ivi4v4ziuui%2Bw2ibTQQXBQNYRKbXn5scA%3D&reserved=0).
 
När du bäddar in en Power BI-rapport med *dynamisk bindning* kan du ansluta samma rapport till olika datamängder beroende på användarens autentiseringsuppgifter.
 
Det innebär att du kan använda en rapport och visa olika information beroende på den datamängd som rapporten är ansluten till. En rapport som visar en återförsäljares försäljningsvärden kan till exempel anslutas till olika datamängder för återförsäljaren och ge olika resultat beroende på den datamängd för återförsäljaren den är ansluten till.
 
Rapporten och datamängden behöver inte ligga i samma arbetsyta. Båda arbetsytorna (den som innehåller rapporten och den som innehåller datamängden) måste tilldelas till en [kapacitet](azure-pbie-create-capacity.md).

Se till att du som en del av inbäddningsprocessen *genererar en token med tillräckliga behörigheter*och *justerar konfigurationsobjektet*.


## <a name="generating-a-token-with-sufficient-permissions"></a>Generera en token med tillräckliga behörigheter

Dynamisk bindning stöds för både scenariot *Inbäddning för din organisation* och scenariot *Inbäddning för dina kunder*. I tabellen nedan beskrivs överväganden för respektive scenario.


|Scenario  |Dataägarskap  |Token  |Krav  |
|---------|---------|---------|---------|
|*Inbäddning för din organisation*    |Användaren äger data         |Åtkomsttoken för Power BI-användare         |Den användare vars Azure AD-token används måste ha tillräcklig behörighet för alla artefakter.         |
|*Inbäddning för dina kunder*     |Appen äger data         |Åtkomsttoken för användare utanför Power BI         |Måste innehålla behörigheter både för rapporten och för den dynamiskt kopplade datamängden. Använd [API:et för att generera en inbäddningstoken för flera objekt](embed-sample-for-customers.md#multiEmbedToken) om du vill generera en inbäddningstoken som stöder flera artefakter.         |

## <a name="adjusting-the-config-object"></a>Justera konfigurationsobjektet
Lägg till `datasetBinding` i konfigurationsobjektet. Använd exemplet nedan som referens.

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>Nästa steg

Om du inte har använt inbäddning i Power BI tidigare kan du läsa igenom de här självstudierna så att du får lära dig att bädda in Power BI-innehåll:
* [Självstudier: Bädda in Power BI-innehåll i ett program för dina kunder](embed-sample-for-customers.md)
* [Självstudier: Bädda in Power BI-innehåll i ett program för din organisation](embed-sample-for-your-organization.md)