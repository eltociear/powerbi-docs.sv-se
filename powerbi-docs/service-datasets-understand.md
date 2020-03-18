---
title: Datamängder i Power BI-tjänsten
description: Förstå hur Power BI-tjänstens datamängder representerar en källa med data som är redo för rapportering och visualisering.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/09/2019
ms.author: v-pemyer
ms.openlocfilehash: 6170217119e443a2eb24aac056623dce5070303e
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79208021"
---
# <a name="datasets-in-the-power-bi-service"></a>Datamängder i Power BI-tjänsten

Den här artikeln innehåller en teknisk förklaring av Power BI:s datamängder.

## <a name="dataset-types"></a>Datamängdstyper

Power BI-datauppsättningar representerar en källa av data som är redo för rapportering och visualisering. Det finns fem olika datamängdstyper som skapas på följande sätt:

- Ansluta till en befintlig datamodell som inte finns i någon Power BI-kapacitet
- Ladda upp en Power BI Desktop-fil som innehåller en modell
- Ladda upp en Excel-arbetsbok (med en eller flera Excel-tabeller och/eller en arbetsboksdatamodell), eller ladda upp en CSV-fil (kommaavgränsade värden)
- Använda Power BI-tjänsten för att skapa en [push-datamängd](developer/automation/walkthrough-push-data.md)
- Använda Power BI-tjänsten för att skapa en [direktuppspelande eller hybriduppspelande datamängd](service-real-time-streaming.md)

Förutom direktuppspelande datamängder, representerar datamängden en datamodell som använder modelleringstekniker från [Analysis Services](/analysis-services/analysis-services-overview).

> [!NOTE]
> I vår dokumentation används ibland termerna _datamängder_ och _modeller_ för samma sak. Ur ett Power BI-tjänsteperspektiv refereras det i allmänhet till som en **datamängd**, och ur ett utvecklingsperspektiv refereras det till som en **modell**. I vår dokumentation betyder de i stort sett samma sak.

### <a name="external-hosted-models"></a>Externt värdbaserade modeller

Det finns två typer av externt värdbaserade modeller: SQL Server Analysis Services och [Azure Analysis Services](/azure/analysis-services/analysis-services-overview).

Att ansluta till en SQL Server Analysis Services-modell innebär att installera den [lokala datagatewayen](service-gateway-onprem.md), oavsett om den är lokal eller finns som IaaS (infrastructure-as-a-service) på en virtuell dator. Azure Analysis Services kräver inte någon gateway.

Att ansluta till Analysis Services är ofta en bra idé när det finns befintliga modellinvesteringar, vilka normalt utgör en del av företagsinformationslagret. Power BI kan utföra en _direktanslutning_ till Analysis Services och tillämpa databehörigheter med hjälp av Power BI-rapportanvändarens identitet. SQL Server Analysis Services stöder både flerdimensionella modeller (kuber) och tabellmodeller. I följande bild visas en direktansluten datamängd som skickar frågor till externt värdbaserade modeller.

![En direktansluten datamängd skickar frågor till en externt värdbaserad modell](media/service-datasets-understand/live-connection-dataset.png)

### <a name="power-bi-desktop-developed-models"></a>Power BI Desktop-utvecklade modeller

Power BI Desktop – ett klientprogram avsett för utveckling av Power BI – kan användas för att utveckla en modell. Modellen blir en Analysis Services-tabellmodell. Modeller kan utvecklas genom att importera data från dataflöden, som sedan integreras med externa datakällor. Även om information om hur modellering kan ske ligger utom omfånget för denna artikel, är det viktigt att förstå att det finns tre olika typer, eller _lägen_, av modeller som kan utvecklas med hjälp av Power BI Desktop. Dessa lägen avgör om data har importerats till modellen, eller om de finns kvar i datakällan. Det finns tre lägen: Import, DirectQuery och Sammansatt. Mer information om varje läge finns i artikeln [Datamängdslägen i Power BI-tjänsten](service-dataset-modes-understand.md).

Externt värdbaserade modeller och Power BI Desktop-modeller kan tillämpa säkerhet på radnivå (RLS) för att begränsa vilka data som kan hämtas för en viss användare. Användare som tillhör säkerhetsgruppen **Säljare** kan till exempel bara se rapportdata för de försäljningsregioner som de har tilldelats. RLS-roller är _dynamiska_ eller _statiska_. Dynamiska roller filtreras av rapportanvändaren, medan statiska roller tillämpar samma filter för alla användare som tilldelats rollen. Mer information finns i [Säkerhet på radnivå (RLS) med Power BI](service-admin-rls.md).

### <a name="excel-workbook-models"></a>Excel-arbetsboksmodeller

När datamängder som baseras på [Excel-arbetsböcker](service-excel-workbook-files.md) eller [CSV-filer](service-comma-separated-value-files.md) skapas, resulterar det automatiskt i att en modell skapas. Excel-tabeller och CSV-data importeras för att skapa modelltabeller, medan en datamodell för en Excel-arbetsbok transponeras för att skapa en Power BI-modell. I samtliga fall importeras fildata till en modell.

## <a name="summary"></a>Sammanfattning

Åtskillnader kan sedan göras om Power BI-datauppsättningar som representerar modeller:

- De finns antingen i Power BI-tjänsten, eller externt hos Analysis Services.
- De kan lagra importerade data eller utfärda frågebegäranden till underliggande datakällor eller en blandning av båda.

Här är en sammanfattning av viktiga fakta om Power BI-datauppsättningar som representerar modeller:

- Modeller i SQL Server Analysis Services kräver en gateway för att kunna utföra direktanslutna frågor.
- Power BI-värdbaserade modeller som importerar data:
  - Måste vara helt inlästa i minnet för att kunna efterfrågas.
  - Kräver uppdatering för att hålla data aktuella och måste innefatta gatewayer när datakällan inte är tillgänglig direkt via Internet.
- Power BI-värdbaserade modeller som använder [DirectQuery](desktop-directquery-about.md)-lagringsläget, kräver en anslutning till datakällan. När modellen får en fråga, utfärdar Power BI frågor till källdata för att hämta aktuella data. Detta läge måste innefatta gatewayer när datakällan inte är tillgänglig direkt via Internet.
- Modeller kan tillämpa RLS-regler som använder filter för att begränsa dataåtkomsten för vissa användare.

## <a name="considerations"></a>Att tänka på

Om du vill distribuera och hantera Power BI, är det viktigt att förstå var modellerna finns, deras lagringsläge, eventuella beroenden för gatewayer, storleken på importerade data, samt uppdateringstyp och intervall. Alla de här konfigurationerna kan ha en betydande inverkan på Power BI-kapacitetens resurser. Dessutom kan själva modelldesignen, inklusive frågor för förberedelse av data, relationer och beräkningar också finnas bland övervägandena.

Det är viktigt att förstå att Power BI-värdbaserade importmodeller kan uppdateras enligt ett schema, eller utlösas på begäran av en användare i Power BI-tjänsten.

## <a name="next-steps"></a>Nästa steg

- [Datamängdslägen i Power BI-tjänsten](service-dataset-modes-understand.md)
- Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
