---
title: Länka entiteter mellan dataflöden i Power BI
description: Lär dig hur du länkar entiteter i dataflöden i Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 4331878aee591f9e3939c0bb1c239eca160ee61d
ms.sourcegitcommit: 80961ace38ff9dac6699f81fcee0f7d88a51edf4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/13/2019
ms.locfileid: "56223661"
---
# <a name="link-entities-between-dataflows-in-power-bi-preview"></a>Länka entiteter mellan dataflöden i Power BI (förhandsversion)

Med dataflöden i Power BI kan du ha en enda organisatorisk datalagringskälla där affärsanalytiker kan förbereda och hantera sina data en gång och sedan återanvända dem mellan olika analyseringsappar i organisationen. 

När du länkar enheter mellan dataflöden kan du återanvända entiteter som redan har matats in, rensade och omvandlade av andra dataflöden som ägs av andra utan att behöva underhålla dessa data. De länkade entiteterna pekar helt enkelt på entiteter i andra dataflöden och kopierar eller duplicerar *inte* data.

![Länkade entiteter i Power BI](media/service-dataflows-linked-entities/linked-entities_00.png)

Länkade entiteter är **skrivskyddade**. Om du vill skapa transformationer för en länkad entitet, måste du skapa en ny beräknad entitet som refererar till den länkade entiteten.

## <a name="linked-entity-availability"></a>Tillgänglighet till länkad entitet

Länkade entiteter kräver en [Power BI Premium](service-premium.md)-prenumeration för att uppdatera. Länkade entiteter är tillgängliga i alla dataflöden på en arbetsyta som finns i Power BI Premium-kapacitet. Det finns inga begränsningar i källdataflödet.

Länkade entiteter fungerar endast korrekt i nya Power BI-arbetsytor. Du kan läsa mer om [nya Power BI-arbetsytor](service-create-the-new-workspaces.md). Alla länkade dataflöden måste finnas i nya arbetsytor för att fungera korrekt.

> [!NOTE]
> Entiteter varierar beroende på om de är standardentiteter eller beräknade entiteter. Standardentiteter (kallas ofta bara entiteter) frågar en extern datakälla, till exempel en SQL-databas. Beräknade entiteter kräver Premium-kapacitet i Power BI och kör sina transformationer på data som redan finns i Power BI-lagring. 
>
>Om ditt dataflöde inte är i en arbetsyta för Premium-kapacitet, kan du fortfarande referera till en enskild fråga eller kombinera två eller flera frågor så länge omvandlingarna inte är definierade som transformationer som lagras. Sådana referenser anses vara standardentiteter. Du gör detta genom att stänga av alternativet **Aktivera inläsning** för de refererade frågorna för att förhindra att data materialiseras och matas in i lagring. Därifrån kan du kan referera till dessa frågor **Aktivera inläsning = false** och ställa in **Aktivera inläsning** till **På** bara för de resulterade frågor som du vill materialisera.


## <a name="how-to-link-entities-between-dataflows"></a>Så här länkar du entiteter mellan dataflöden

Det finns ett antal sätt att länka enheter mellan dataflöden i Power BI. Du kan välja **Lägg till länkade entiteter** från redigeringsverktyget för dataflöden såsom visas i följande bild. 

![Länkade entiteter i Power BI](media/service-dataflows-linked-entities/linked-entities_00.png)

Du kan också välja **Lägg till länkade entiteter** från menyalternativet **Lägg till entiteter** i Power BI-tjänsten.

![Länkade entiteter i Power BI](media/service-dataflows-linked-entities/linked-entities_01.png)

Om du vill länka entiteter, måste du logga in med dina Power BI-autentiseringsuppgifter.

Ett **Navigator**-fönster öppnas och du kan välja en uppsättning entiteter som du kan ansluta. De entiteter som visas är enheter som du har behörighet till, över alla arbetsytor i Power BI-klienten. 

När dina länkade entiteter har valts, visas de i listan över entiteter för ditt dataflöde i redigeringsverktyget, med en särskild ikon som identifierar dem som länkade entiteter.

Du kan också visa källdataflödet från dataflödesinställningarna för den länkade entiteten.

## <a name="refresh-logic-of-linked-entities"></a>Uppdateringslogik för länkade entiteter
Standarduppdateringslogiken för länkade entiteter ändras baserat på om källdataflödet finns i samma arbetsyta som måldataflödet. I följande avsnitt beskrivs beteendet för var och en.

### <a name="links-between-workspaces"></a>Länkar mellan arbetsytor

Uppdatering för länkar från entiteter i olika arbetsytor fungerar som en extern datakälla. När dataflödet uppdateras, tar den de senaste data för entiteten från källdataflödet. Om källdataflödet uppdateras, påverkar det inte automatiskt data i måldataflödet.

### <a name="links-in-the-same-workspace"></a>Länkar i samma arbetsyta

När uppdatering av data för en datakälla sker, utlöser händelsen automatiskt en uppdateringsprocess för beroende entiteter i alla måldataflöden i samma arbetsyta, inklusive alla beräknade entiteter som baseras på dem. Alla andra entiteter i måldataflödet uppdateras enligt dataflödeschemat. Entiteter som är beroende av mer än en källa uppdaterar sina data när deras källor har uppdaterats korrekt.

Det är bra att observera att hela uppdateringsprocessen sker på samma gång. Om uppdateringen av måldataflödet inte går att uppdatera, misslyckas därmed källdataflödet samt dess uppdatering.

## <a name="permissions-when-viewing-reports-from-dataflows"></a>Behörigheter för visning av rapporter från dataflöden

När du skapar en Power BI-rapport som innehåller data baserade på ett dataflöde, kan användarna se alla länkade entiteter endast när användaren har åtkomst till källdataflödet.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden

Det finns några begränsningar att tänka på när du arbetar med länkade entiteter:

* Det finns en maxgräns på högst fem refererande hopp
* Cykliska beroenden med länkade entiteter är inte tillåtna
* Dataflödet måste finnas i en [ny Power BI-arbetsyta](service-create-the-new-workspaces.md)


## <a name="next-steps"></a>Nästa steg

Följande artiklar kan vara användbara när du skapar eller arbetar med dataflöden. 

* [Dataförberedelser med självbetjäning i Power BI (förhandsversion)](service-dataflows-overview.md)
* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Använda beräknade entiteter i Power BI Premium (förhandsversion)](service-dataflows-computed-entities-premium.md)
* [Använda dataflöden med lokala datakällor (förhandsversion)](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI-dataflöden (förhandsversion)](service-dataflows-developer-resources.md)

Mer information om Power Query och schemalagd uppdatering finns i följande artiklar:
* [Frågeöversikt i Power BI Desktop](desktop-query-overview.md)
* [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md)

Mer information om Common Data Service finns i dess översiktsartikel:
* [Common Data Service – översikt ](https://docs.microsoft.com/powerapps/common-data-model/overview)

