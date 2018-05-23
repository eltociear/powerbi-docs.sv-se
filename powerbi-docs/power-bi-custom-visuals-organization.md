---
title: Använda anpassade visuella objekt för organisationer i Power BI
description: Använda, hantera och skapa anpassade visuella objekt för organisationer i Power BI
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 02/06/2018
ms.author: maghan
LocalizationGroup: Visualizations
ms.openlocfilehash: bc4dcc26ac2007e482b396139d572018c8a3acd3
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="using-organization-custom-visuals-in-power-bi"></a>Använda anpassade visuella objekt för organisationer i Power BI

Du kan använda anpassade visuella objekt i Power BI om du vill skapa en unik form av skräddarsydd visuell information, eller de datainsikter som du försöker förmedla. Dessa anpassade visuella objekt skapas ofta av utvecklare, och de skapas ofta när flera av de visuella objekt som ingår i Power BI inte riktigt uppfyller deras behov. 

I vissa organisationer är anpassade visuella objekt ännu viktigare – de kan vara nödvändiga för att förmedla specifika data eller insikter som är unika för organisationen, de kan ha särskilda datakrav eller de kan lyfta fram privata affärsmetoder. Sådana organisationer behöver utveckla anpassade visuella objekt, dela dem i hela organisationen och se till att de är underhålls ordentligt. Med anpassade visuella objekt i Power BI kan organisationer göra just detta.

I följande bild visas den process genom vilken organisationens anpassade visuella objekt i Power BI flödar från administratören, via utveckling och underhåll, för att slutligen hamna hos dataanalytikern.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Organisation Visuella objekt för organisationer distribueras och hanteras av Power BI-administratör från administrationsportalen. När de anpassade visuella objekten väl har distribuerats till organisationens databas, kan användarna i organisationen enkelt identifiera och importera dem till sina rapporter direkt från Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Använda anpassade visuella objekt i en organisation

Mer information om hur du använder anpassade visuella objekt i en organisation i rapporter som du har skapat finns i följande artikel: [Lär dig mer om att importera organisationens visuella objekt till dina rapporter](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Administrera anpassade visuella objekt i en organisation

Mer information om hur du administrerar, distribuerar och hanterar anpassade visuella objekt i din organisation finns i följande artikel: [Lär dig mer om att distribuera och hantera anpassade visuella objekt i en organisation](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Ett anpassat visuellt objekt kan innehålla kod som innebära säkerhets- eller integritetsrisker. Kontrollera att författaren eller källan till alla anpassade visuella objekt är tillförlitlig innan du distribuerar dem till organisationens databas. 
> 

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
 
Det finns flera överväganden och begränsningar som du behöver känna till.
 
Administration:

* Äldre anpassade visuella objekt (t.ex anpassade visuella objekt som inte har byggts ovanpå den nya versionens API:er) stöds inte

* Om ett anpassat visuellt objekt tas bort från databasen upphör alla befintliga rapporter som använder det borttagna visuella objektet att återges. Det går inte att ångra borttagningen från databasen. För att tillfälligt inaktivera anpassad visualisering, använder du funktionen ”inaktivera”.
 
Slutanvändare:

* Power BI-arbetsytesamling stöds inte för visuella objekt i organisationen

* Visuella Visio-objekt, visuella PowerApps visual-objekt och visuella GlobeMap-objekt från AppSource-marknadsplatsen återges inte om de distribueras via organisationens databas
