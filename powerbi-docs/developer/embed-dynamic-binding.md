---
title: Dynamisk bindning
description: Lär dig hur du bäddar in en rapport med dynamisk bindning.
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 09/25/2019
ms.openlocfilehash: 8b42b397f726e492eda80a99eb730c215eb17ccb
ms.sourcegitcommit: 23ad768020a9daf129f69a462a2d46d59d2349d2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776247"
---
# <a name="dynamic-binding"></a>Dynamisk bindning

Med dynamisk bindning kan du dynamiskt välja en datamängd när du bäddar in en rapport. Rapporten och datamängden behöver inte ligga i samma arbetsyta. Slutanvändarna ser olika resultat beroende på vilken datamängd som väljs.

Båda arbetsytorna (den som innehåller rapporten och den som innehåller datamängden) måste tilldelas till en kapacitet.

Processen att bädda in en rapport med dynamisk bindning består av två steg:
1. Generera en token
2. Justera konfigurationsobjektet

## <a name="generating-a-token"></a>Generera en token
När du ska generera en token använder du [API:et för att generera en inbäddningstoken för flera objekt](embed-sample-for-customers.md#multiEmbedToken).

Dynamisk bindning stöds för båda inbäddningsscenarierna, *Inbäddning för din organisation* och *Inbäddning för dina kunder*.

| Lösning                   | Token                               | Krav                                                                                                                                                  |
|---------------------------------|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *Inbäddning för din organisation* | Åtkomsttoken för Power BI-användare     | Den användare vars Azure AD-token används måste ha tillräcklig behörighet för alla artefakter.                                                                    |
| *Inbäddning för dina kunder*    | Åtkomsttoken för användare utanför Power BI | Måste innehålla behörigheter både för rapporten och för den dynamiskt kopplade datamängden. Använd det nya API:et och generera en inbäddad token med stöd för flera artefakter. |

## <a name="adjusting-the-config-object"></a>Justera konfigurationsobjektet
Lägg till `datasetBinding` i konfigurationsobjektet. Använd exemplet längst ned på sidan som referens.

Om du inte har använt inbäddning i Power BI tidigare kan du läsa igenom de här självstudierna så att du får lära dig att bädda in Power BI-innehåll:
* [Bädda in Power BI-innehåll i ett program för dina kunder](embed-sample-for-customers.md)
* [Självstudier: Bädda in Power BI-innehåll i ett program för din organisation](embed-sample-for-your-organization.md)

 ### <a name="example"></a>Exempel
```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    /////////////////////////////////////////////
    // Adjustment required for dynamic binding //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // End of dynamic binding adjustment            //
    /////////////////////////////////////////////
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```