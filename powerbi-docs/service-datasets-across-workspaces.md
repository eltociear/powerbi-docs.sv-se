---
title: Introduktion till datamängder mellan arbetsytor (förhandsversion)
description: Lär dig hur du delar en datamängd med användare i organisationen. De kan sedan skapa rapporter baserat på din datamängd på sina egna arbetsytor.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/15/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 258dd735c5ba97122d9e93f888e65cf2030f01eb
ms.sourcegitcommit: 4d5166944fcc6fe4666cab055ae75e7a0a77866d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69530477"
---
# <a name="intro-to-datasets-across-workspaces-preview"></a>Introduktion till datamängder mellan arbetsytor (förhandsversion)

Business Intelligence är en samarbetsinriktad aktivitet. Det är viktigt att upprätta standardiserade datamängder som kan utgöra ”den enda källan till sanning”. Det viktigaste är att upptäcka och återanvända dessa standardiserade datamängder. När experter på datamodellering i din organisation skapar och delar optimerade datamängder kan rapportskapare börja med de datamängderna för att skapa korrekta rapporter. Sedan har organisationen konsekventa data för beslutsfattande och en välfungerande datakultur.

![Välja en delad datamängd](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

I Power BI kan datamängdsskapare kontrollera vem som har åtkomst till deras data med hjälp av [skapa-behörighet](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Datamängdsskapare kan även *certifiera* eller *höja upp* datamängder så att andra kan upptäcka dem. På så sätt kan rapportförfattare veta vilken datauppsättning har hög kvalitet och är officiella och de kan använda dessa datauppsättningar, oavsett var i Power BI de skriver. Klientorganisationsadministratörer har klientorganisationsinställning för att [styra användningen av datamängder mellan arbetsytor](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Delning av datamängder och den nya arbetsytefunktionen

Skapandet av rapporter baserat på datamängder på olika arbetsytor, och kopiering av rapporter till olika arbetsytor, hör nära samman med [den nya arbetsytefunktionen](service-create-the-new-workspaces.md):

- När du i tjänsten öppnar datamängdskatalogen från en ny arbetsytefunktion visar datamängdskatalogen datamängder som finns i Min arbetsyta och i arbetsytor med den nya arbetsytefunktionen. 
- När du öppnar datamängdskatalogen från en klassisk arbetsyta ser du bara datamängderna på den arbetsytan, inte dem som finns på andra arbetsytor.
- I Power BI Desktop kan du publicera Live Connect-rapporter till olika arbetsytor förutsatt att deras datamängder finns på arbetsytor med den nya arbetsytefunktionen.
- Vid kopiering av rapporter mellan arbetsytor behöver målarbetsytan vara en arbetsyta med den nya arbetsytefunktionen.

## <a name="discover-datasets-preview"></a>Upptäcka datamängder (förhandsversion)

När en rapport skapas ovanpå en befintlig datamängd är det första steget att ansluta till datamängden via antingen Power BI-tjänsten eller Power BI Desktop. Läs avsnittet om att [upptäcka datamängder från olika arbetsytor (förhandsversion)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Kopiera en rapport

När du har hittat en rapport som du gillar på en arbetsyta eller i en app kan du göra en kopia av den och sedan anpassa den efter dina behov. Du behöver inte tänka på att skapa datamodellen. Den har redan skapats. Och det är mycket enklare att ändra en befintlig rapport än att börja från början. Läs mer om att [kopiera rapporter](service-datasets-copy-reports.md).

## <a name="build-permission-for-datasets"></a>Skapa-behörighet för datamängder

Med hjälp av skapa-behörighetstypen kan du bestämma vem i organisationen som kan skapa nytt innehåll i dina datamängder, förutsatt att du är datamängdsskapare. Personer med skapa-behörighet kan även skapa nytt innehåll på datamängden utanför Power BI, till exempel Excel-blad via Analysera i Excel, XMLA och exportera. Läs mer om [skapa-behörighet](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="promotion-and-certification"></a>Upphöjning och certifiering

Om du skapar datamängder kan du, om du skapar en som andra kan dra nytta av, göra det enklare för andra att upptäcka den genom att [höja upp datamängden](service-datasets-promote.md). Du kan även begära att experter i din organisation [certifierar datamängden](service-datasets-certify.md).

## <a name="licensing"></a>Licensiering

Specifika funktioner som bygger på funktionaliteten hos delade datamängder licensieras enligt deras befintliga scenarier. Till exempel:

- I allmänhet är upptäckt av och anslutning till delade datamängder tillgängligt för alla. Dock kan användare utan Pro-licens endast ansluta till datamängder som finns i deras personliga Min arbetsyta.
- I Power BI Desktop kan användare utan Pro-licens endast se datamängder från deras Min arbetsyta.
- Kopiering av rapporter mellan arbetsytor kräver en Pro-licens.
- Kopiering av rapporter från en app kräver en Pro-licens, liksom det krävdes för organisationsinnehållspaket.
- Befordring och certifiering av datamängder kräver en Pro-licens.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

- Skapande av en rapport ovanpå en datamängd på en annan arbetsyta kräver den nya arbetsytefunktionen på båda sidor: Både rapporten och datamängden måste finnas på en arbetsyta med den nya arbetsytefunktionen.
- Anta att du skapar en rapport på Arbetsyta A som baseras på en datamängd på Arbetsyta B. När du skapar en app för Arbetsyta A kan du bara inkludera den rapporten i Arbetsyta A-appen om du även är medlem för Arbetsyta B.
- På en klassisk arbetsyta visar funktionen för datamängdsupptäckt endast datamängder på den arbetsytan.
- Om du vill lägga till en rapport baserat på en delad datamängd till en app måste du vara medlem i den datamängdens arbetsyta. Det här är ett känt problem.
- ”Publicera på webben” fungerar inte för en rapport som baseras på en delad datamängd. Det här är avsiktligt.
- Om två personer är medlemmar i en arbetsyta som har åtkomst till en delad datamängd är det möjligt att endast en av dem kan se den relaterade datamängden på arbetsytan. Endast personer med minst läsbehörighet till datamängden kan se den delade datamängden. 

## <a name="next-steps"></a>Nästa steg

- [Höja upp datamängder](service-datasets-promote.md)
- [Certifiera datamängder](service-datasets-certify.md)
- [Styra användningen av datamängder mellan arbetsytor](service-datasets-admin-across-workspaces.md)
- Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
