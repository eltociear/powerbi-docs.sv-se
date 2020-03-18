---
title: Frågor och svar i Power BI Embedded
description: Power BI Embedded ger dig ett sätt att ta med frågor och svar i ett program och tillåta dina användare att ställa frågor med naturligt språk.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 11/20/2017
ms.openlocfilehash: b7a86db04c37d40cef4b2578cd5f11a53a9bce9d
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79491236"
---
# <a name="qa-in-power-bi-embedded"></a>Frågor och svar i Power BI Embedded

Power BI Embedded ger dig ett sätt att ta med frågor och svar i ett program och tillåta att dina användare ställer frågor med naturligt språk och tar emot direkta svar i form av visuell information som diagram eller grafer.

![Frågor och svar interaktiv fråga i en inbäddad ram](media/qanda/embedded-qanda.gif)

Det finns två lägen för inbäddning av frågor och svar i ditt program: **interaktivt** och **enbart resultat**. **Interaktivt** läge låter dig skriva in frågor och få dem visade i den visuella informationen. Om du har en sparad fråga eller en fast fråga som du vill visa, kan du använda läget **endast resultat** genom att fylla i frågan i din inbäddningskonfiguration.

Här är en titt på hur JavaScript-koden ser ut.

```javascript
// Embed configuration used to describe the what and how to embed.
// This object is used when calling powerbi.embed within the JavaScript API.
// You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
var config= {
    type: 'qna',
    tokenType:   models.TokenType.Embed | models.TokenType.Aad,
    accessToken: access token value,
    embedUrl:    https://app.powerbi.com/qnaEmbed (groupId to be appended as query parameter if required),
    datasetIds:  array of requested data set ids (at the moment we support only one dataset),
    viewMode:    models.QnaMode.Interactive | models.QnaMode.ResultOnly,
    question:    optional parameter for Explore mode (QnaMode.Interactive) and mandatory for Render Result mode (QnaMode.ResultOnly)
};

// Get a reference to the embedded QNA HTML element
var qnaContainer = $('#qnaContainer')[0];

// Embed the QNA and display it within the div container.
var qna = powerbi.embed(qnaContainer, config);
```

## <a name="set-question"></a>Ställ in frågan

Om du använde **resultatläge** med en inställd fråga, kan du föra in ytterligare frågor i ramen och få dem besvarade direkt vilket ersätter det tidigare resultatet. En ny visuell information renderas som matchar den nya frågan.

Ett exempel på den här användningen är en lista över vanliga frågor och svar. Användaren kan då gå igenom frågorna och få dem besvarade inom samma inbäddade del.

**Kodfragment för användning i JS SDK:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

qna.setQuestion("This year sales")
    .then(function (result) {
        …….
    })
    .catch(function (errors) {
        …….
    });
```

## <a name="visual-rendered-event"></a>Visuellt renderad händelse

För **interaktivt** läge, kan programmet meddleas med en data ändrad händelse varje gång den renderade visuella informationen ändras för att matcha den uppdaterade frågan allteftersom den skrivs.

Om du lyssnar på händelsen *visualRendered* så kan du spara frågor för senare användning. 

**Kodfragment för användning i JS SDK:**  

```javascript
// Get a reference to the embedded Q&A HTML element
var qnaContainer = $('#qnaContainer')[0];

// Get a reference to the embedded Q&A.
qna = powerbi.get(qnaContainer);

// qna.off removes a given event listener if it exists.
qna.off("visualRendered");

// qna.on will add an event listener.
qna.on("visualRendered", function(event) {
     …….
});
```

## <a name="embed-token"></a>Inbäddningstoken

Skapa en inbäddningstoken från en datauppsättning för att starta en frågor och svar-del. Mer information finns i avsnittet [Generera token](https://docs.microsoft.com/rest/api/power-bi/embedtoken).

## <a name="next-steps"></a>Nästa steg

Om du vill göra ett försök med inbäddning av frågor och svar, kan du kolla [JavaScript-inbäddningsprov](https://microsoft.github.io/PowerBI-JavaScript/demo/).

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
