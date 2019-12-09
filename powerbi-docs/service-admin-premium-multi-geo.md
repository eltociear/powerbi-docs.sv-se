---
title: Multi-Geo-stöd för Power BI Premium
description: Lär dig hur du kan distribuera innehåll till datacentra i andra regioner än Power BI-klientorganisationens hemregion.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 27e4bbd1437f59b7cf213333d9df27019aaadcd4
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74698864"
---
# <a name="configure-multi-geo-support-for-power-bi-premium"></a>Konfigurera Multi-Geo-stöd för Power BI Premium

Multi-Geo är en Power BI Premium-funktion som hjälper multinationella kunder att adressera kraven på regional, branschspecifik eller organisationsrelaterad dataplacering. Som Power BI Premium-kund kan du distribuera innehåll till datacentra i andra regioner än Power BI-klientorganisationens hemregion. Ett geografiskt område (geografi) kan innehålla mer än en region. USA är t.ex. ett geografiskt område och USA, västra centrala och USA, södra centrala är regioner i USA. Du kan välja att distribuera innehåll till någon av följande platser:

- USA
- Kanada
- Storbritannien
- Brasilien
- Europa
- Japan
- Indien
- Asien och stillahavsområdet
- Australien
- Afrika

Multi-Geo är inte tillgängligt för Power BI Tyskland, Power BI Kina, drivet av 21Vianet, eller Power BI för amerikanska myndigheter.

Multi-Geo finns nu även i Power BI Embedded. Läs mer i [Multi-Geo-stöd för Power BI Embedded](developer/embedded-multi-geo.md).

## <a name="enable-and-configure"></a>Aktivera och konfigurera

Aktivera Multi-Geo genom att välja en annan region än standardregion i listrutan om du vill ha nya kapaciteter.  Varje tillgänglig kapacitet visar i vilken region där den för närvarande finns, t.ex. **USA, västra centrala**.

![Kapacitetsstorlek: välj en region. Power BI med Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-capacity-size.png)

När du har skapat en kapacitet finns den kvar i den regionen, och alla arbetsytor som skapats får sitt innehåll sparat i den regionen. Du kan migrera arbetsytor från en region till en annan via listrutan på skärmen för arbetsyteinställningar.

![Redigera arbetsyta: Välj en tillgänglig kapacitet. Power BI med Multi-Geo](media/service-admin-premium-multi-geo/power-bi-multi-geo-edit-workspace.png)

Det här meddelandet visas så att du kan bekräfta ändringen.

![Bekräftelse av ändring av tilldelad arbetsyta](media/service-admin-premium-multi-geo/power-bi-multi-geo-change-assigned-workspace-capacity.png)

Du behöver inte återställa gatewayens autentiseringsuppgifter under en migrering just nu.  När de har lagrats i Premium-kapacitetsregionen måste du återställa dem vid migrering.

Under migreringen misslyckas vissa åtgärder, t.ex. publicering av nya datauppsättningar eller schemalagd datauppdatering.  

Följande objekt lagras i Premium-regionen när Multi-Geo har aktiverats:

- Modeller (.ABF-filer) för import och DirectQuery-datauppsättningar
- Frågecache
- R-avbildningar

De här objekten finns kvar i klientorganisationens hemregion:

- Push-datauppsättningar
- Excel-arbetsböcker
- Metadata för instrumentpanel/rapport: t.ex. panelnamn, panelfrågor
- Service Bus för gatewayfrågor eller schemalagda uppdateringsjobb
- Behörigheter
- Autentiseringsuppgifter för datauppsättning

## <a name="view-capacity-regions"></a>Visa kapacitetsregioner

Du kan visa alla kapaciteter för din Power BI-klientorganisation i administrationsportalen och de regioner där de för närvarande är placerade.

![Visa premiumkapaciteter](media/service-admin-premium-multi-geo/power-bi-multi-geo-premium-capacities.png) 

## <a name="change-the-region-for-existing-content"></a>Ändra region för befintligt innehåll

Om du behöver ändra regionen för befintligt innehåll har du två alternativ.

- Skapa en andra kapacitet och flytta arbetsytor. Ej betalande användare upplever inga avbrott så länge som klientorganisationen har extra v-kärnor.
- Om skapandet av en andra kapacitet inte är något alternativ kan du tillfälligt flytta innehållet till delad kapacitet från Premium. Du behöver inte några extra v-kärnor, men ej betalande användare kan uppleva vissa avbrott.

## <a name="move-content-out-of-multi-geo"></a>Flytta bort innehåll från Multi-Geo  

Du kan ta bort arbetsytor från Multi-Geo-kapaciteten på något av följande två sätt:

- Ta bort den aktuella kapaciteten där arbetsytan finns.  Då flyttas arbetsytan tillbaka till delad kapacitet i hemregionen.
- Migrera enskilda arbetsytor tillbaka till Premium-kapacitet som finns i startklientorganisationen.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

- Bekräfta att varje förflyttning du upprättar mellan regioner följer alla företags- och myndighetskrav innan du påbörjar dataöverföringen.
- En cachelagrad fråga som lagras i en avlägsen region kvar i den regionen i vila. Andra data under överföring kan dock flyttas fram och tillbaka mellan flera geografiska områden.
- När du flyttar data från en region till en annan i en Multi-Geo-miljö kan källdata finnas kvar i upp till 30 dagar i den region från vilken data har flyttats. Under den tiden har slutanvändare inte åtkomst till den. Den tas bort från den här regionen och förstörs under 30-dagarsperioden.
- Multi-Geo resultera inte i bättre prestanda i allmänhet. Att läsa in rapporter och instrumentpaneler involverar fortfarande förfrågningar om metadata från hemregionen.
- Funktionen för [dataflöden](service-dataflows-overview.md) stöds inte med Multi-GEO just nu.

## <a name="next-steps"></a>Nästa steg

- [Vad är Power BI Premium?](service-premium-what-is.md)
- [Multi-Geo för Power BI Embedded-kapaciteter](developer/embedded-multi-geo.md)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
