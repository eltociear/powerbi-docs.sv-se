---
title: "Använda anpassade visuella objekt för organisationer i Power BI"
description: "Använda, hantera och skapa anpassade visuella objekt för organisationer i Power BI"
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
ms.date: 02/06/2018
ms.author: maghan
ms.openlocfilehash: 2c90ea4a7e95c354b6dfaec04cff7e5e4009b55f
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/09/2018
---
# <a name="using-organization-custom-visuals-in-power-bi-preview"></a>Använda anpassade visuella objekt för organisationer i Power BI (förhandsversion)

Du kan använda anpassade visuella objekt i Power BI om du vill skapa en unik form av skräddarsydd visuell information, eller de datainsikter som du försöker förmedla. Dessa anpassade visuella objekt skapas ofta av utvecklare, och de skapas ofta när flera av de visuella objekt som ingår i Power BI inte riktigt uppfyller deras behov. 

I vissa organisationer är anpassade visuella objekt ännu viktigare – de kan vara nödvändiga för att förmedla specifika data eller insikter som är unika för organisationen, de kan ha särskilda datakrav eller de kan lyfta fram privata affärsmetoder. Sådana organisationer behöver utveckla anpassade visuella objekt, dela dem i hela organisationen och se till att de är underhålls ordentligt. Med anpassade visuella objekt i Power BI (som nu finns i förhandsversion) kan organisationer göra just detta. 

I följande bild visas den process genom vilken organisationens anpassade visuella objekt (förhandsversion) i Power BI flödar från administratören, via utveckling och underhåll, för att slutligen hamna hos dataanalytikern.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

## <a name="how-to-enable-organizational-custom-visuals-preview"></a>Så här aktiverar du anpassade visuella objekt i en organisation (förhandsversion)

Funktionen för anpassade visuella objekt för organisationer finns för närvarande i förhandsversion, så måste du aktivera funktionen i Power BI Desktop. Du aktiverar den här förhandsversionsfunktionen för genom att gå till menyfliksområdet, välja Arkiv > Alternativ och inställningar > Alternativ. Sedan väljer du Förhandsversionsfunktioner i det vänstra fönstret, och därefter markerar du kryssrutan intill Min organisations anpassade visuella objekt, så som visas i följande bild.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-02.jpg)

Organisation Visuella objekt för organisationer distribueras och hanteras av Power BI-administratör från administrationsportalen. När de anpassade visuella objekten väl har distribuerats till organisationens databas, kan användarna i organisationen enkelt identifiera och importera dem till sina rapporter direkt från Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Använda anpassade visuella objekt i en organisation

Mer information om hur du använder anpassade visuella objekt i en organisation i rapporter som du har skapat finns i följande artikel: [Lär dig mer om att importera organisationens visuella objekt till dina rapporter](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Administrera anpassade visuella objekt i en organisation

Mer information om hur du administrerar, distribuerar och hanterar anpassade visuella objekt i din organisation finns i följande artikel: [Lär dig mer om att distribuera och hantera anpassade visuella objekt i en organisation](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Ett anpassat visuellt objekt kan innehålla kod som innebära säkerhets- eller integritetsrisker. Kontrollera att författaren eller källan till alla anpassade visuella objekt är tillförlitlig innan du distribuerar dem till organisationens databas. 
> 

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
 
Eftersom de anpassade visuella objekten är i förhandsversionen är det vissa överväganden du bör göra och vissa begränsningar du bör känna till och ta med i beräkningen.
 
Administration:

* Äldre anpassade visuella objekt (t.ex anpassade visuella objekt som inte har byggts ovanpå den nya versionens API:er) stöds inte

* Uppdatering på plats stöds inte ännu. Om du vill uppdatera ett visuellt objekt måste du överföra en ny version av det visuella objektet till organisationens databas (kontrollera också att det har samma visuella ID i PBIVIZ-filen). Rapportförfattarna kan sedan importera den nya versionen till sina rapporter och ersätta deras aktuella version av det visuella objektet på plats i rapporten.

* Om ett anpassat visuellt objekt tas bort från databasen upphör alla befintliga rapporter som använder det borttagna visuella objektet att återges. Det går inte att ångra borttagningen från databasen.
 
Slutanvändare:

* Att använda samma visuella objekt (samma visuella ID) från den offentliga marknaden (AppSource) och från organisationens databas stöds inte. I sådana fall används det senast importerade visuella objektet.

* Extern delning av organisationens visuella objekt på instrumentpaneler och i rapporter stöds inte. Användare utanför organisationen som visar en instrumentpanel med något av organisations anpassade visuella objekt ser bara ett tomt visuellt objekt. 

* Power BI-arbetsytesamling stöds inte för visuella objekt i organisationen

* Anpassade visuella objekts organisering i rapporter som publiceras på webben återges inte

* Visuella Visio-objekt, visuella PowerApps visual-objekt och visuella GlobeMap-objekt från AppSource-marknadsplatsen återges inte om de distribueras via organisationens databas

* Om administratören tar bort ett anpassat visuellt objekt från databasen och det visuella objektet används i en rapport, så stoppas det visuella objektet från att återges, och det måste tas bort från rapporten innan du kan spara den