---
title: Använda datamängder mellan arbetsytor (förhandsversion) – Power BI
description: Lär dig hur du delar en datamängd med användare i organisationen. De kan sedan skapa rapporter baserat på din datamängd på sina egna arbetsytor.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d893088978d7a412d0e005ca7b3280824974c76c
ms.sourcegitcommit: 206806d8ddb6bdfc322c1a46fb34a1b0678acba2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816673"
---
# <a name="use-datasets-across-workspaces-preview"></a>Använda datamängder mellan arbetsytor (förhandsversion)

Business Intelligence är en samarbetsinriktad aktivitet. Det är viktigt att upprätta standardiserade datamängder som kan utgöra ”den enda källan till sanning”. Det viktigaste är att upptäcka och återanvända dessa standardiserade datamängder. När experter på datamodellering i din organisation skapar och delar optimerade datamängder kan rapportskapare börja med de datamängderna för att skapa korrekta rapporter. Sedan har organisationen konsekventa data för beslutsfattande och en välfungerande datakultur.

![Välja en delad datamängd](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

Power BI gör det enkelt för datamängdsskapare att certifiera eller rekommendera datamängder så att andra kan upptäcka dem. Sedan hittar rapportförfattare högkvalitativa, officiella datamängder som de kan använda var som helst i Power BI. Datamängdsägare kan kontrollera vem som har åtkomst till deras data med hjälp av [skapa-behörighet](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Klientorganisationsadministratörer har klientorganisationsinställning för att [styra användningen av datamängder mellan arbetsytor](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Delning av datamängder och den nya arbetsytefunktionen

Skapandet av rapporter baserat på datamängder på olika arbetsytor, och kopiering av rapporter till olika arbetsytor, hör nära samman med [den nya arbetsytefunktionen](service-create-the-new-workspaces.md):

- När du i tjänsten öppnar datamängdskatalogen från en ny arbetsytefunktion visar datamängdskatalogen datamängder som finns i Min arbetsyta och i arbetsytor med den nya arbetsytefunktionen. 
- När du öppnar datamängdskatalogen från en klassisk arbetsyta ser du bara datamängderna på den arbetsytan, inte dem som finns på andra arbetsytor.
- I Desktop kan du publicera Live Connect-rapporter till olika arbetsytor förutsatt att deras datamängder finns i arbetsytor med den nya arbetsytefunktionen.
- Vid kopiering av rapporter mellan arbetsytor behöver målarbetsytan vara en arbetsyta med den nya arbetsytefunktionen.

## <a name="build-permission-for-datasets"></a>Skapa-behörighet för datamängder

Med skapa-behörighet kan du tillåta andra i organisationen att skapa nytt innehåll såsom rapporter, instrumentpaneler och fästa paneler från Frågor och svar på en befintlig datamängd. De kan även skapa nytt innehåll på datamängden utanför Power BI, till exempel Excel-blad via Analysera i Excel, XMLA och exportera. Läs mer om [skapa-behörighet](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="discover-datasets-preview"></a>Upptäcka datamängder (förhandsversion)

När en rapport skapas ovanpå en befintlig datamängd är det första steget att ansluta till datamängden via antingen Power BI-tjänsten eller Power BI Desktop. Läs avsnittet om att [upptäcka datamängder från olika arbetsytor (förhandsversion)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Kopiera en rapport

När du har hittat en rapport som du gillar på en arbetsyta eller i en app kan du göra en kopia av den och sedan anpassa den efter dina behov. Du behöver inte tänka på att skapa datamodellen. Den har redan skapats. Och det är mycket enklare att ändra en befintlig rapport än att börja från början. Läs mer om att [kopiera rapporter](service-datasets-copy-reports.md).

## <a name="promotion-and-certification"></a>Upphöjning och certifiering

Om du skapar datamängder kan du, om du skapar en som andra kan dra nytta av, göra det enklare för andra att upptäcka den genom att [höja upp datamängden](service-datasets-promote.md). Du kan även begära att experter i din organisation [certifierar datamängden](service-datasets-certify.md).

## <a name="licensing"></a>Licensiering

Specifika funktioner som bygger på funktionaliteten hos delade datamängder licensieras enligt deras befintliga scenarier.  Till exempel:

- I allmänhet är upptäckt av och anslutning till delade datamängder tillgängligt för alla. Dock kan användare utan Pro-licens endast ansluta till datamängder som finns i deras personliga Min arbetsyta eller på Premium-arbetsytor.
- Upphöjning och certifiering av datamängder utanför personliga arbetsytor kräver en Pro-licens eftersom du behöver en Pro-licens för att vara medlem i en apparbetsyta.
- Kopiering av rapporter mellan arbetsytor kräver en Pro-licens eftersom du alltså behöver en Pro-licens för att vara medlem i en apparbetsyta.
- Kopiering av rapporter från en app kräver en Pro-licens, liksom det krävdes för organisationsinnehållspaket.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

- Skapande av en rapport ovanpå en datamängd på en annan arbetsyta kräver den nya arbetsytefunktionen på båda sidor: Både rapporten och datamängden måste finnas på en arbetsyta med den nya arbetsytefunktionen.
- På en klassisk arbetsyta visar funktionen för datamängdsupptäckt endast datamängder på den arbetsytan.
- Du kan skapa rapporter på apparbetsytor som baseras på datamängder på en annan arbetsyta. Du kan dock inte skapa en app för en arbetsyta som innehåller de datamängderna.
- Användare av den kostnadsfria versionen i Desktop ser endast datamängder från Min arbetsyta och från Premium-baserade arbetsytor.
- Om du vill lägga till en rapport baserat på en delad datamängd till en app måste du vara medlem i den datamängdens arbetsyta. Det här är ett känt problem.
- ”Publicera på webben” fungerar inte för en rapport som baseras på en delad datamängd. Det här är avsiktligt.
- Om två personer är medlemmar i en arbetsyta som har åtkomst till en delad datamängd är det möjligt att endast en av dem kan se den relaterade datamängden på arbetsytan. Endast personer med minst läsbehörighet till datamängden kan se den delade datamängden. 

## <a name="next-steps"></a>Nästa steg

- [Höja upp datamängder](service-datasets-promote.md)
- [Certifiera datamängder](service-datasets-certify.md)
- [Styra användningen av datamängder mellan arbetsytor](service-datasets-admin-across-workspaces.md)
- Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
