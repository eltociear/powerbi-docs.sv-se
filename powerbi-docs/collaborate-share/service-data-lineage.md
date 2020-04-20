---
title: Dataursprung (förhandsversion)
description: I moderna Business Intelligence-projekt kan det vara svårt för många kunder att förstå dataflödet från datakällan till målet.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.date: 02/27/2020
ms.author: painbar
LocalizationGroup: ''
ms.openlocfilehash: 165651beab2e20f033d20480e78a3876931ea806
ms.sourcegitcommit: 81407c9ccadfa84837e07861876dff65d21667c7
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/13/2020
ms.locfileid: "81267283"
---
# <a name="data-lineage-preview"></a>Dataursprung (förhandsversion)
I moderna Business Intelligence-projekt kan det vara svårt att förstå dataflödet från datakällan till målet. Det kan vara ännu svårare om du har byggt avancerade analysprojekt som omfattar flera datakällor, artefakter och beroenden. Frågor som ”vad händer om jag ändrar dessa data?” eller ”varför är inte den här rapporten uppdaterad?” kan vara svåra att svara på. Det kan krävas ett team av experter eller en djupgående undersökning för att hitta svaren. Vi har skapat en dataursprungsvy för att hjälpa dig att besvara dessa frågor.

![Ursprungsvyn i Power BI](media/service-data-lineage/service-data-lineage-view.png)
 
I Power BI finns flera artefakttyper, till exempel instrumentpaneler, rapporter, datauppsättningar och dataflöden. Många datauppsättningar och dataflöden ansluter till externa datakällor, till exempel SQL Server, och till externa datauppsättningar i andra arbetsytor. När en datauppsättning är extern i förhållande till en arbetsyta som du äger, kan den ingå i en arbetsyta som ägs av någon annan, till exempel någon på IT-avdelningen eller någon annan analytiker. Externa datakällor och datauppsättningar gör att det blir svårare att veta var data kommer från. Vi har introducerat ursprungsvyn för både komplexa och enkla projekt.

I ursprungsvyn visas ursprungsrelationerna mellan alla artefakter i en arbetsyta och alla deras externa beroenden. Den visar anslutningar mellan alla artefakter på arbetsytan, inklusive anslutningar till dataflöden, både uppströms och nedströms.

## <a name="explore-lineage-view"></a>Utforska ursprungsvyn

Alla arbetsytor, oavsett om de är nya eller klassiska, har automatiskt en ursprungsvy. Du behöver minst en deltagarroll på arbetsytan för att kunna visa den. Mer information finns under [Behörigheter](#permissions) i den här artikeln.

* Om du vill öppna ursprungsvyn går du till vyn med listan över arbetsytor. Tryck på pilen bredvid **Listvy** och välj **Ursprungsvy**.

   ![Växla till ursprungsvyn](media/service-data-lineage/service-data-lineage-view-select.png)

I den här vyn visas alla artefakter på arbetsytan och hur data flödar från en artefakt till en annan.

**Datakällor**

Du kan se de datakällor som datauppsättningar och dataflöden hämtar sina data från. På korten för datakällor visas mer information som kan hjälpa dig att identifiera källan. För Azure SQL Server visas till exempel även databasnamnet.

![Datakälla i ursprungsvyn utan gateway](media/service-data-lineage/service-data-lineage-data-source-card.png)
 
**Gatewayer**

Om en datakälla är ansluten via en lokal gateway läggs gatewayinformationen till på datakällans kort. Om du har behörigheter som antingen gatewayadministratör eller användare av en datakälla, kan du se mer information, som exempelvis gatewaynamnet.

![Datakälla i ursprungsvyn med gateway](media/service-data-lineage/service-data-lineage-data-gateway-card.png)

**Datauppsättningar och dataflöden**
 
För datamängder och dataflöden visas den senaste uppdateringstiden, samt om datamängden eller dataflödet är certifierat eller upphöjt.

![Upphöjda och certifierade datamängder i ursprungsvyn](media/service-data-lineage/service-data-lineage-promoted-certified.png)
 
Om en rapport på arbetsytan bygger på en datamängd eller ett dataflöde som finns på en annan arbetsyta visas källarbetsytans namn på kortet för den datamängden eller det dataflödet. Gå till källarbetsytans genom att välja dess namn.

* Välj **Fler alternativ** (...) för valfri artefakt om du vill visa alternativmenyn. Den innehåller samma åtgärder som finns på listvyn.

Om du vill se fler metadata för en artefakt väljer du själva artefaktkortet. Ytterligare information om artefakten visas på en sidopanel. På bilden nedan visas sidofönstret metadata för en vald datamängd.

![Sidopanelen med mer information](media/service-data-lineage/service-data-lineage-side-pane.png)
 
## <a name="show-lineage-for-any-artifact"></a>Visa ursprung för artefakter 

Anta att du vill se ursprunget för en specifik artefakt.

* Välj de dubbla pilarna under artefakten.

   ![Markera ursprung för en viss artefakt](media/service-data-lineage/service-data-lineage-specific-artifact.png)

   Power BI markerar alla artefakter som är relaterade till artefakten och resten tonas ned. 

## <a name="navigation-and-full-screen"></a>Navigering och helskärmsläge 

Ursprungsvyn är en interaktiv arbetsyta. Du kan använda musen och pekplattan för att navigera på arbetsytan och zooma in eller ut.

* Om du vill zooma in och ut kan du använda menyn i det nedre högra hörnet eller musen eller pekplattan.
* Om du vill ha mer utrymme för själva grafen använder du helskärmsalternativet i det nedre högra hörnet. 

    ![Zooma in eller ut eller helskärmsläge](media/service-data-lineage/service-data-lineage-zoom.png)

## <a name="permissions"></a>Behörigheter

* Du behöver en Power BI Pro-licens för att kunna visa ursprungsvyn.
* Ursprungsvyn är bara tillgänglig för användare som har åtkomst till arbetsytan.
* Användare måste ha en administratörs-, medlems- eller deltagarroll på arbetsytan. Användare med en visningsroll kan inte växla till ursprungsvyn.


## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

- Ursprungsvyn är inte tillgänglig i Internet Explorer. Mer information finns i [Webbläsare som stöds för Power BI](../power-bi-browsers.md).

## <a name="next-steps"></a>Nästa steg

* [Introduktion till datamängder mellan arbetsytor (förhandsversion)](../service-datasets-across-workspaces.md)
* [Påverkansanalys för en datamängd](service-dataset-impact-analysis.md)
