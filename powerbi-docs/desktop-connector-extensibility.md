---
title: Utökningsbara kopplingar i Power BI
description: Utökningsbara kopplingar, funktioner, säkerhetsinställningar och certifierade kopplingar
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: c63357df043ff6a646562d398a07d8042dd5a0ee
ms.sourcegitcommit: 7fb0b68203877ff01f29724f0d1761d023075445
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39256599"
---
# <a name="connector-extensibility-in-power-bi"></a>Utökningsbarhet av anslutningsprogram i Power BI

I Power BI kan kunder och utvecklare utöka de datakällor som de kan ansluta till på flera sätt, t.ex. genom att använda befintliga kopplingar och generiska datakällor (t.ex. ODBC, OData, Oledb, Web, CSV, XML och JSON). Förutom dessa datakällor kan utvecklare skapa datatillägg, så kallade **anpassade anslutningar**, och certifiera kopplingar så att de blir **certifierade kopplingar**.

I tidigare versioner av Power BI användes en funktionsväxel för att aktivera funktionen för **anpassade anslutningar**. Nu finns det en meny där du på ett säkert sätt kan styra i hur hög grad anpassad kod ska tillåtas att köra i ditt system: alla anpassade anslutningar eller endast kopplingar som har certifierats och distribuerats av Microsoft i dialogrutan **Hämta data**.

## <a name="custom-connectors"></a>Anpassade anslutningar

**Anpassade anslutningar** inbegriper många möjligheter – från små API:er som är viktiga för din verksamhet, till stora branschspecifika tjänster som Microsoft inte har implementerat. De flesta sådana kopplingar distribueras av leverantören, och om du behöver en specifik datakoppling bör du kontakta en leverantör.

Om du vill använda en **anpassad anslutning** lägger du till den i mappen *\[Dokument\\Power BI Desktop\\Anpassade anslutningsprogram* och justerar säkerhetsinställningarna genom att följa anvisningarna i avsnitten nedan.

Du behöver inte ändra säkerhetsinställningarna för att använda **certifierade kopplingar**.

## <a name="data-extension-security"></a>Säkerhetsinställningar för datatillägg

Om du vill ändra säkerhetsinställningarna för datatillägg går du till **Power BI Desktop** och väljer **Arkiv > Alternativ och inställningar > Alternativ > Säkerhet**.

![Välj om du vill läsa in anpassade anslutningar med säkerhetsalternativ för datatillägg](media/desktop-connector-extensibility/data-extension-security-1.png)

Under **Datatillägg** kan du välja mellan två säkerhetsnivåer:

* (Rekommenderas) Tillåt att endast certifierade filnamnstillägg läses in
* (Rekommenderas inte) Tillåt att alla tillägg läses in utan varning

Om du vill använda **anpassade anslutningar** eller kopplingar som du eller en tredje part har utvecklat och distribuerat måste du välja **(Not Recommended) Allow any extension to load without warning** ((Rekommenderas inte) Tillåt att alla tillägg läses in utan varning). Vi rekommenderar inte den här säkerhetsinställningen såvida du inte planerar att köra **anpassade anslutningar**.

Om du använder säkerhetsinställningen **(Rekommenderas)** och det finns anpassade anslutningar i systemet visas ett fel som beskriver de kopplingar som inte kan läsa in av säkerhetsskäl.

![En dialogruta beskriver anpassade anslutningar som inte kan läsas in på grund av säkerhetsinställningarna, i det här fallet TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

För att åtgärda problemet så att du kan använda dessa anslutningar måste du ändra säkerhetsinställningarna till inställningen **(Rekommenderas inte)** som beskrivs ovan och sedan starta om **Power BI Desktop**.

## <a name="certified-connectors"></a>Certifierade kopplingar

En begränsad deluppsättning av datatilläggen betraktas som **certifierade**. Sådana certifierade kopplingar är tillgängliga via dialogrutan **Hämta Data**, men den part som ansvarar för underhåll och support är fortfarande tredjepartsutvecklaren som skapade anslutningen. Även om Microsoft distribuerar dessa kopplingar ansvarar vi inte för deras prestanda eller funktioner.

Be din leverantör att kontakta Microsoft om du vill att en anpassad anslutning ska certifieras.
