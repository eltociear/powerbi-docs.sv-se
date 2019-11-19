---
title: Begränsningar för Power BI Frågor och svar
description: Aktuella begränsningar för Power BI Frågor och svar
author: mohaali
manager: mohaali
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: mohaali
ms.openlocfilehash: fc4a605f1258bcd93e0b49b596cc3a1691ce2edb
ms.sourcegitcommit: 26123c6bb24c8174beb390f4e06fb938d31238ea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72717464"
---
# <a name="limitations-of-power-bi-qa"></a>Begränsningar för Power BI Frågor och svar

Power BI Frågor och svar har för närvarande vissa begränsningar.

## <a name="data-sources"></a>Datakällor

### <a name="supported-data-sources"></a>Datakällor som stöds

Power BI Frågor och svar har för närvarande stöd för följande konfiguration av datakällor i Power BI-tjänsten:

- Import-läge
- Direktanslutning till Azure Analysis Services
- Direktanslutning till SQL Server Analysis Services (via en gateway)
- Power BI-datamängder. Power BI Desktop rapporterar ett fel med Frågor och svar när du använder en Power BI-datamängd. När du publicerar rapporten till Power BI-tjänsten försvinner dock felet.

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

- "Land” som är ”USA”
- ”Land” som inte är ”USA”
- ”Vikt” > 2000
- ”Vikt” = 2000
- ”Vikt” < 2000

> [!NOTE]
> Verktygen i Frågor och svar har bara stöd för importläge. För närvarande saknas stöd för anslutning till en lokal datakälla eller en Azure Analysis Services-datakälla. Den här begränsningen kommer att försvinna i senare versioner av Power BI.

### <a name="statements-not-supported"></a>Instruktioner stöds inte

- Du kan för närvarande inte använda mått i villkor. Konvertera i stället måtten till beräknade kolumner så att de fungerar.
- Du kan inte använda flera villkor. En lösning är att skapa en beräknad DAX-kolumn som utvärderar ett booleskt uttryck med flera villkor och använder detta fält i stället.
- Om du inte anger något filtervillkor när Frågor och svar begär en delmängd data kan du inte spara definitionen, även om hela instruktionen saknar röda understrykningar.
