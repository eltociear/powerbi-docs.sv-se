---
title: Standardmedlem i flerdimensionella modeller i Power BI
description: Lär dig hur Power BI fungerar när du arbetar med standardmedlemmar i flerdimensionella modeller
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/10/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: ea60400a4522dd496e19d508f13760581c0b2620
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75761259"
---
# <a name="work-with-multidimensional-models-in-power-bi"></a>Arbeta med flerdimensionella modeller i Power BI

Du kan ansluta till flerdimensionella modeller i Power BI och skapa rapporter som visualiserar olika typer av data i modellen. När du arbetar med flerdimensionella modeller tillämpar Power BI regler för hur det bearbetar data, baserat på vilken kolumn som har definierats som *standardmedlem*. 

När du arbetar med flerdimensionella modeller hanterar Power BI data från modellen baserat på var kolumnen som innehåller **DefaultMember** används. Attributet *DefaultMember* är inställt i CSDL (Conceptual Schema Definition Language) för en viss kolumn i en flerdimensionell modell. Du kan läsa mer om standardmedlemmen i [artikeln om dess attributsegenskaper](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/attribute-properties-define-a-default-member?view=sql-server-2017). När en DAX-fråga körs används automatiskt den standardmedlem som angetts i modellen.

Den här artikeln beskriver hur Power BI beter sig i olika situationer när du arbetar med flerdimensionella modeller, beroende på var *standardmedlemmen* finns. 

## <a name="working-with-filter-cards"></a>Arbeta med filterkort

När du skapar ett filterkort på ett fält med en standardmedlem markeras standardmedlemmens fältvärde automatiskt i filterkortet. Resultatet blir att alla visuella objekt som påverkas av filterkortet behåller sina standardmodeller i databasen. Värdena i sådana filterkort återspeglar den standardmedlemmen.

Om standardmedlemmen tas bort och du avmarkerar värdet, rensas det för alla visuella objekt som filterkortet tillämpas på och de värden som visas återspeglar inte standardmedlemmen.

Anta exempelvis att vi har kolumnen *Valuta* som har en standardmedlem inställd på *USD*:

* Om vi i det här exemplet har ett kort som visar *Total försäljning* kommer värdet att tillämpa standardmedlemmen och vi ser en försäljning som motsvarar ”USD”.
* Om vi drar *Valuta* till filterkortsfönstret ser vi *USD* som det valda standardvärdet. Värdet för *Total försäljning* förblir detsamma eftersom standardmedlemmen tillämpas.
* Men om vi avmarkerar värdet *USD* från filterkortet så rensas standardmedlemmen för *Valuta* och nu återspeglar *Total försäljning* alla valutor.
* När vi väljer ett annat värde i filterkortet (anta att vi väljer *EURO*), tillsammans med standardmedlem, återspeglar därför *Total försäljning* filtret *Valuta i {USD, EURO}* .

## <a name="grouping-behavior"></a>Grupperingsbeteende

När du grupperar ett visuellt objekt i Power BI på en kolumn som har en *standardmedlem* tar Power BI bort *standardmedlemmen* för kolumnen och sökvägen för dess attributrelation. Det säkerställer att det visuella objektet visar alla värden, i stället för bara standardvärdena.

## <a name="attribute-relationship-paths-arps"></a>Sökvägar för attributrelationer (ARP:er)

Sökvägar för attributrelationer (ARP:er) ger *standardmedlemmar* kraftfulla funktioner, men medför också en viss mängd komplexitet. När ARP:er påträffas följer Power BI sökvägen till ARP:erna för att rensa ytterligare standardmedlemmar för andra kolumner, för att tillhandahålla konsekvent och exakt hantering av data för visuella objekt.

Nu ska vi titta på ett exempel för att förstå beteendet. Tänk dig följande konfiguration av ARP:erna:

![ARP:er i en flerdimensionell modell](media/desktop-default-member-multidimensional-models/default-members_01.png)

Låt oss anta att följande *standardmedlemmar* anges för dessa kolumner:

* Stad > Seattle
* Stat > WA
* Land > USA
* Befolkning > Stor

Nu ska vi granska vad som händer när var och en av kolumnerna används i Power BI. När visuella objekt grupperas efter dessa kolumner blir resultatet:

* **Stad** – Power BI visar alla städer genom att avmarkera alla **standardmedlemmar** för *Stad*, *Stat* och *Land* men behåller **standardmedlemmen** för *Befolkning*; Power BI rensade hela ARP:n för *Stad*.
    > [!NOTE]
    > *Befolkning* hör inte till ARP-sökvägen till *Stad*, den är endast kopplad till *Stat* och därmed rensar inte Power BI den.
* **Stat** –- Power BI visar alla *Stater* genom att rensa alla **standardmedlemmar** för *Stad*, *Stat*, *Land* och *Befolkning*.
* **Land** – Power BI visar alla länder genom att avmarkera alla **standardmedlemmar** för *Stad*, *Stat* och *Land* men behåller **standardmedlemmen** för *Befolkning*.
* **Stad och Stat** – Power BI rensar alla **standardmedlemmar** för alla kolumner.

Grupper som visas i det visuella objektet får hela sin ARP-sökväg rensad. 

Om en grupp inte visas i det visuella objektet, men är en del av ARP-sökvägen till en annan kolumn som det grupperas enligt, gäller följande:

* Inte alla grenar i ARP-sökvägen rensas automatiskt.
* Den gruppen filtreras fortfarande utifrån den orensade **standardmedlemmen**.

### <a name="slicers-and-filter-cards"></a>Utsnitt och filterkort

När du arbetar med utsnitt eller filterkort, händer följande:

* När en utsnitt eller filterkort har lästs in med data, grupperar Power BI på kolumnen i det visuella objektet, så visningsbeteendet blir detsamma som beskrevs i föregående avsnitt.

Eftersom utsnitt och filterkort ofta används för att interagera med andra visuella objekt sker logiken för att rensa **standardmedlemmar** för de berörda visuella objekt enligt beskrivningen i följande tabell. 

I den här tabellen använder vi samma exempeldata som användes tidigare i den här artikeln:

![Beteende för när Power BI rensar standardmedlem med utsnitt och filterkort](media/desktop-default-member-multidimensional-models/default-members_02.png)

Följande regler gäller för hur Power BI agerar i dessa fall.

Power BI rensar en **standardmedlem** för en viss kolumn om:

* Power BI grupperar enligt den kolumnen
* Power BI grupperar enligt en kolumn som är relaterad till den kolumnen (var som helst i ARP, uppåt eller nedåt)
* Power BI filtrerar enligt en kolumn som ingår i ARP (uppåt eller nedåt)
* Kolumnen har ett filterkort med tillståndet *ALL*
* Kolumnen har ett filterkort med valfritt värde valt (Power BI tar emot ett filter för kolumnen)

Power BI rensar inte en **standardmedlem** för en viss kolumn om:

* Kolumnen har ett filterkort med standardtillstånd och Power BI grupperar enligt en kolumn i dess ARP.
* Kolumnen finns ovanför en annan kolumn i ARP och Power BI har ett filterkort för den andra kolumnen i standardtillstånd.


## <a name="next-steps"></a>Nästa steg

Den här artikeln beskriver hur Power BI agerar när du arbetar med standardmedlemmar i flerdimensionella modeller. Följande artiklar kan också vara av intresse för dig: 

* [Visa objekt utan data i Power BI](desktop-show-items-no-data.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
