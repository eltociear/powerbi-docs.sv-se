---
title: Begränsningar för Power BI Frågor och svar
description: Aktuella begränsningar för Power BI Frågor och svar
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/21/2020
ms.author: maggies
ms.openlocfilehash: b71fd2986fb79adf88493416ac8234f2656aefa9
ms.sourcegitcommit: a199dda2ab50184ce25f7c9a01e7ada382a88d2c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82866781"
---
# <a name="limitations-of-power-bi-qa"></a>Begränsningar för Power BI Frågor och svar

Power BI Frågor och svar har för närvarande vissa begränsningar.

## <a name="data-sources"></a>Datakällor

### <a name="supported-data-sources"></a>Datakällor som stöds

Power BI Frågor och svar har för närvarande stöd för följande konfiguration av datakällor i Power BI-tjänsten:

- Import-läge
- Direktanslutning till Azure Analysis Services
- Direktanslutning till SQL Server Analysis Services (via en gateway)
- Power BI-datamängder.

Alla de här konfigurationerna har även stöd för säkerhet på radnivå.

### <a name="data-sources-not-supported"></a>Datakällorna stöds inte

Power BI Frågor och svar saknar för närvarande stöd för följande konfigurationer:

- Säkerhet på objektnivå oavsett typen av datakälla
- DirectQuery mot alla typer av källor. En lösning är att använda direktanslutning till Azure Analysis Services, som använder DirectQuery.
- Sammansatta modeller
- Reporting Services 

## <a name="tooling-limitations"></a>Verktygsbegränsningar

I den nya verktygsdialogrutan kan användare anpassa och förbättra det naturliga språket i Frågor och svar. Läs mer om verktygen i [Introduktion till verktyg i Frågor och svar](q-and-a-tooling-intro.md).

## <a name="review-question-limitations"></a>Begränsningar för granskningsfrågor

I granskningsfrågorna lagras endast frågor som ställs mot datamodellen i upp till 28 dagar. När du använder den nya funktionen med granskningsfrågor kanske du märker att vissa frågor inte har registrerats. Det här är avsiktligt, eftersom motorn för naturligt språk utför olika rensningssteg så att inte användarens alla tangenttryckningar ska registreras eller visas.

En klientorganisations administratörer kan hantera möjligheten att lagra frågor i administratörsinställningarna. Behörigheter baseras på säkerhetsgrupper. 

Användarna kan även förhindra att frågor registreras genom att välja **Inställningar** > **Allmänt** och avmarkera **Tillåt att Frågor och svar registrerar mina talindata**. 

## <a name="teach-qa-limitations"></a>Begränsningar för Träna Frågor och svar

Med Träna Frågor och svar kan du åtgärda två typer av fel:

- Tilldela ett ord till ett fält.
- Tilldela ett ord till ett filtervillkor.

För närvarande saknas stöd för att definiera om en identifierad term eller att definiera andra typer av villkor eller fraser. När du definierar filtervillkor kan du bara använda en begränsad del av språket, bland annat följande:

- Land som är USA
- Land som inte är USA
- Produkter > 100
- Produkter som är större än 100
- Produkter = 100
- Produkter är 100
- Produkter < 100
- Produkter som är mindre än 100

> [!NOTE]
> Verktygen i Frågor och svar har bara stöd för importläge. För närvarande saknas stöd för anslutning till en lokal datakälla eller en Azure Analysis Services-datakälla. Den här begränsningen kommer att försvinna i senare versioner av Power BI.

### <a name="statements-not-supported"></a>Instruktioner stöds inte

- Du kan för närvarande inte använda mått i villkor. Konvertera i stället måtten till beräknade kolumner så att de fungerar.
- Du kan inte använda flera villkor. En lösning är att skapa en beräknad DAX-kolumn som utvärderar ett booleskt uttryck med flera villkor och använder detta fält i stället.
- Om du inte anger något filtervillkor när Frågor och svar begär en delmängd data kan du inte spara definitionen, även om hela instruktionen saknar röda understrykningar.

## <a name="next-steps"></a>Nästa steg

Det finns ett antal metodtips för att förbättra motorn för naturligt språk. Mer information finns i [Frågor och svar – metodtips](q-and-a-best-practices.md).