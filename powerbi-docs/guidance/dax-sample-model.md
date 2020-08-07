---
title: DAX-exempelmodell
description: DAX-exempelmodell som stöder referensartiklar.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/25/2020
ms.author: v-pemyer
ms.openlocfilehash: 6e2fe331fa274305447266321893204dddcc3148
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87537468"
---
# <a name="dax-sample-model"></a>DAX-exempelmodell

**Adventure Works DW 2020** Power BI Desktop-exempelmodell som är utformad för att stödja din DAX-utbildning. Modellen baseras på [Adventure Works-informationslagerexempel](/sql/samples/adventureworks-install-configure#data-warehouse-downloads) för AdventureWorksDW2017, men dessa data har ändrats för att passa exempelmodellens mål.

## <a name="scenario"></a>Scenario

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="En bild av Adventure Works företagslogotyp visas.":::

Företaget Adventure Works representerar en cykeltillverkare som säljer cyklar och tillbehör till globala marknader. Företaget lagrar sina informationslagerdata i en Azure SQL Database.

## <a name="model-structure"></a>Modellstruktur

Modellen har sju tabeller:

|Tabell|Beskrivning|
|-----|-------|
|**Kund**|Beskriver kunder och deras geografiska plats. Kunderna köper produkter online (Internet-försäljning).|
|**Datum**|Det finns tre relationer mellan tabellerna **Datum** och **Försäljning**, för speditionsdatum, leveransdatum respektive förfallodatum. Orderdatumets relation är aktiv. Företagets försäljningsrapporter har ett räkenskapsår som börjar den 1 juli varje år. Tabellen har markerats som en datumtabell med hjälp av kolumnen **Datum**.|
|**Produkt**|Lagrar endast färdiga produkter.|
|**Återförsäljare**|Beskriver återförsäljare och deras geografiska plats. Återförsäljare om att sälja produkter till sina kunder.|
|**Försäljning**|Lagrar rader på försäljningsorderns radintervall. Alla ekonomiska värden anges i amerikanska dollar (USD). Det tidigaste orderdatumet är 1 juli 2017 och det senaste orderdatumet är 15 juni 2020.|
|**Försäljningsorder**|Beskriver försäljningsorder och orderradsnummer, och även försäljningskanalen, som antingen är **Återförsäljare** eller **Internet**. Den här tabellen har en 1-till-1-relation med tabellen **Försäljning**.|
|**Säljområde**|Säljområdena är indelade i grupper (Nordamerika, Europa och Stilla havsområdet), länder och regioner. Endast USA säljer produkter på regional nivå.|

Modellen innehåller inte några DAX-beräkningar.

## <a name="download-sample"></a>Ladda ned exempel

Du kan ladda ned den färdiga Power BI Desktop-exempelfilen [här](https://aka.ms/dax-docs-sample-file).

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Data Analysis uttryck (DAX)-referens](/dax/)
- Utbildningsväg: [Använda DAX i Power BI Desktop](https://docs.microsoft.com/learn/paths/dax-power-bi/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com)
