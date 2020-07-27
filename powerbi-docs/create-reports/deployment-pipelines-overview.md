---
title: Översikt över distributionspipelines
description: Lär dig vad distributionspipelines i Power BI är
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 05/06/2020
ms.openlocfilehash: 5522d84cab235270a2eb368be02cfa0fb4e5eaa9
ms.sourcegitcommit: 10c5b6cd5e7070f96de8a9f1d9b95f3d242ac7f2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86557151"
---
# <a name="introduction-to-deployment-pipelines-preview"></a>Introduktion till distributionspipelines (förhandsversion)

I dagens värld är analyser en viktig del av beslutsfattandet i nästan alla organisationer. Den växande användningen av Power BI som ett analysverktyg kräver att detta verktyg använder mer data, att det ser tilltalande ut och är användarvänligt. Mer än allt annat måste dock Power BI alltid vara tillgängligt och tillförlitligt. Om de ska kunna uppfylla dessa krav måste BI-skaparna samarbeta effektivt.

Distributionspipelines är ett effektivt och användbart verktyg med vilket BI-skapare i ett företag med Premium-kapacitet kan hantera livscykeln för organisationens innehåll. På så sätt kan du utveckla och testa Power BI-innehåll som rapporter, instrumentpaneler och datamängder innan de används av slutanvändarna.

Verktyget är utformat som en pipeline i tre steg:

* **<a name="development"></a>Utveckling**
    
    Det här steget använder du för att utforma, bygga och ladda upp nytt innehåll tillsammans med andra skapare. Detta är det första distributionspipelinesteget.

* **<a name="test"></a>Test**

    När innehållet har laddats upp och alla ändringar har gjorts i utvecklingssteget kan du flytta innehållet till det här steget för testning. Här följer tre exempel på vad som kan göras i testmiljön:

    * Dela innehållet med testare och granskare

    * Läs in och kör tester med större datamängder

    * Testa din app så att du ser hur den ser ut för dina slutanvändare

* **<a name="production"></a>Produktion**

    När du har testat innehållet använder du produktionssteget för att dela den slutgiltiga versionen av ditt innehåll med företagsanvändare i hela organisationen.

![En skärmbild av en arbetsdistributionspipeline med alla tre stadier, utveckling, testning och produktion, ifyllda.](media/deployment-pipelines-overview/deployment-pipelines.png)

## <a name="next-steps"></a>Nästa steg

>[!div class="nextstepaction"]
>[Kom igång med distributionspipelines](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[Förstå distributionspipelineprocessen](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[Felsökning av distributionspipelines](deployment-pipelines-troubleshooting.md)

>[!div class="nextstepaction"]
>[Metodtips för distributionspipelines](deployment-pipelines-best-practices.md)