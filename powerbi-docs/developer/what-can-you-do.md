---
title: Vad kan utvecklare göra med Power BI?
description: Power BI erbjuder en mängd olika alternativ för utvecklare. Allt från inbäddning till anpassad visuell information och strömning av datauppsättningar.
author: markingmyname
ms.author: maghan
ms.date: 05/03/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: ee9f5b2e89a1746267090da3485076d67a99d6f9
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34290578"
---
# <a name="what-can-developers-do-with-power-bi"></a>Vad kan utvecklare göra med Power BI?

Utvecklare har olika alternativ som försöker inkludera Power BI-innehåll i program. Dessa alternativ inkluderar **bädda in med Power BI**, **anpassad visuell information**, och **skicka data till Power BI**.

## <a name="embedding"></a>Bädda in
Power BI-tjänsten (SaaS) och Power BI Embedded-tjänsten i Azure (PaaS) har API:er för inbäddning av dina instrumentpaneler och rapporter. Det innebär att du kommer att ha en uppsättning funktioner och tillgång till de senaste funktionerna i Power BI när du bäddar in innehåll, till exempel instrumentpaneler, gatewayer och apparbetsytor.

![PBIE-exempel](media/what-can-you-do/what-can-you-do-01.png)

## <a name="develop-custom-visuals"></a>Utveckla anpassad visuell information
Med anpassade visuell objekt kan du skapa egna visuell objekt för användning i Power BI-rapporter. Anpassad visuell information skrivs i TypeScript som är en supermängd till JavaScript. TypeScript stöder vissa avancerade funktioner och snabb åtkomst till ES6-/ES7-funktioner. Visual formatering hanteras med sammanhängande formatmallar (CSS). För din bekvämlighet använder vi förkompileraren Less som stöder avancerade funktioner, som kapsling, variabler, villkor, slingor med mera. Du kan bara skriva vanlig CSS i Less-filen om du inte vill använda någon av dessa funktioner.

![CV-exempel](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Skicka data till Power BI
Du kan använda Power BI-API:et för skicka data till en datauppsättning. På så sätt kan du lägga till en rad i en tabell i en datauppsättning. Den nya informationen kan sedan återspeglas i panelerna på en instrumentpanel och i visuella objekt i rapporten.

![Dataexempel på push-överföring](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Nästa steg
[Bädda in med Power BI](embedding.md)  
[Publicera anpassade visuella objekt i Office Store](office-store.md)  
[Skicka data till en instrumentpanel](walkthrough-push-data.md)
