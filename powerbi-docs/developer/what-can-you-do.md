---
title: "Vad kan utvecklare göra med Power BI?"
description: "Power BI erbjuder en mängd olika alternativ för utvecklare. Allt från inbäddning till anpassad visuell information och strömning av datauppsättningar."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 07/20/2017
ms.author: maghan
ms.openlocfilehash: b310562ac31694f398a659018743b8fa7aa46e35
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2018
---
# <a name="what-can-developers-do-with-power-bi"></a>Vad kan utvecklare göra med Power BI?
Power BI erbjuder en mängd olika alternativ för utvecklare. Allt från inbäddning till anpassad visuell information och strömning av datauppsättningar.

## <a name="embedding"></a>Bädda in
Power BI-tjänsten och Power BI Embedded i Azure förenas i en enda API för inbäddning av dina instrumentpaneler och rapporter. Det innebär att du kommer att ha en API-yta, en konsekvent uppsättning funktioner och tillgång till de senaste funktionerna i Power BI när du bäddar in innehåll, till exempel instrumentpaneler, gatewayer och apparbetsytor. Mer information finns i [Inbäddning med Power BI](embedding.md).

![](media/what-can-you-do/powerbi-embed-sample.png)

## <a name="custom-visuals"></a>Anpassade visuella objekt
Med anpassade visuell objekt kan du skapa egna visuell objekt för användning i Power BI-rapporter. Visuella standardobjekt måste skrivas i TypeScript, vilket är en supermängd JavaScript som stöder mer avancerade funktioner och snabb åtkomst till ES6/ES7 funktioner. Visual formatering hanteras med sammanhängande formatmallar (CSS). För din bekvämlighet använder vi förkompileraren Less som stöder avancerade funktioner, som kapsling, variabler, mixins, villkor, slingor med mera. Du kan bara skriva vanlig CSS i Less-filen om du inte vill använda någon av dessa funktioner.

Mer information om att utveckla och publicera anpassade virtuella objekt finns i [Publicera anpassade visuella objekt i Office Store](office-store.md).

![](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Skicka data till Power BI
Du kan använda Power BI-API:et för skicka data till en datauppsättning. På så sätt kan du lägga till en rad i en tabell i en datauppsättning. Den nya informationen kan sedan återspeglas i panelerna på en instrumentpanel och i visuella objekt i rapporten.

Mer information finns i [skicka data till en instrumentpanel](walkthrough-push-data.md)

## <a name="next-steps"></a>Nästa steg
[Bädda in med Power BI](embedding.md)  
[Så här migrerar du innehåll från Power BI Embedded-arbetsytesamlingar till Power BI](migrate-from-powerbi-embedded.md)  
[JavaScript API Git Repo](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git Repo](https://github.com/Microsoft/PowerBI-CSharp)  
[Publicera anpassade visuella objekt i Office Store](office-store.md)  
[Power BI Visuals Gallery](https://github.com/Microsoft/PowerBI-visuals)  
[JavaScript-inbäddningsexempel](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

