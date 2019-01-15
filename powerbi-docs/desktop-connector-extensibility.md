---
title: Utökningsbara kopplingar i Power BI
description: Utökningsbara kopplingar, funktioner, säkerhetsinställningar och certifierade kopplingar
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: a5774fe6979516a0fe70364fea5dd91b7a2a48ae
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54275742"
---
# <a name="connector-extensibility-in-power-bi"></a>Utökningsbarhet av anslutningsprogram i Power BI

I Power BI kan kunder och utvecklare utöka de datakällor som de kan ansluta till på flera sätt, t.ex. genom att använda befintliga kopplingar och generiska datakällor (t.ex. ODBC, OData, Oledb, Web, CSV, XML och JSON). Förutom dessa datakällor kan utvecklare skapa datatillägg, så kallade **anpassade anslutningar**, och certifiera kopplingar så att de blir **certifierade kopplingar**.

För närvarande används en funktionsväxel för att aktivera funktionen för **anpassade anslutningsappar**. Innan vi flyttar den här funktionen från beta till allmän tillgänglighet har vi lagt till en meny där du på ett säkert sätt kan styra i hur hög grad anpassad kod ska tillåtas att köra i ditt system: alla anpassade anslutningar eller endast kopplingar som har certifierats och distribuerats av Microsoft i dialogrutan **Hämta data**.

## <a name="custom-connectors"></a>Anpassade anslutningar

**Anpassade anslutningsappar** inbegriper många möjligheter – från små API:er som är viktiga för din verksamhet, till stora branschspecifika tjänster som Microsoft inte har publicerat en anslutningsapp för. Många sådana kopplingar distribueras av leverantören, och om du behöver en specifik datakoppling bör du kontakta en leverantör.

Om du vill använda en **anpassad anslutning** lägger du till den i mappen *\[Dokument\\Power BI Desktop\\Anpassade anslutningsprogram* och justerar säkerhetsinställningarna genom att följa anvisningarna i avsnitten nedan.

Du behöver inte ändra säkerhetsinställningarna för att använda **certifierade anslutningsappar**.

## <a name="data-extension-security"></a>Säkerhetsinställningar för datatillägg

Om du vill ändra säkerhetsinställningarna för datatillägg går du till **Power BI Desktop** och väljer **Arkiv > Alternativ och inställningar > Alternativ > Säkerhet**.

![Välj om du vill läsa in anpassade anslutningar med säkerhetsalternativ för datatillägg](media/desktop-connector-extensibility/data-extension-security-1.png)

Under **Datatillägg** kan du välja mellan två säkerhetsnivåer:

* (Rekommenderas) Tillåt att endast certifierade filnamnstillägg läses in
* (Rekommenderas inte) Tillåt att alla tillägg läses in utan varning

Om du vill använda **anpassade anslutningsappar** eller anslutningsappar som du eller en tredje part har utvecklat och distribuerat måste du välja **(Not Recommended) Allow any extension to load without warning** ((Rekommenderas inte) Tillåt att alla tillägg läses in utan varning). Vi rekommenderar inte den säkerhetsinställningen om du inte absolut litar på dina anpassade anslutningsappar, eftersom koden där kan hantera autentiseringsuppgifter (inklusive att skicka dem visa HTTP) och ignorera sekretessnivåer.

Om du använder säkerhetsinställningen **(Rekommenderas)** och det finns anpassade anslutningar i systemet visas ett fel som beskriver de anslutningsappar som inte kan läsa in av säkerhetsskäl.

![En dialogruta beskriver anpassade anslutningar som inte kan läsas in på grund av säkerhetsinställningarna, i det här fallet TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

För att åtgärda problemet så att du kan använda dessa anslutningsappar måste du ändra säkerhetsinställningarna till inställningen **(Rekommenderas inte)** som beskrivs ovan och sedan starta om **Power BI Desktop**.

## <a name="certified-connectors"></a>Certifierade kopplingar

En begränsad deluppsättning av datatilläggen betraktas som **certifierade**. Sådana certifierade anslutningsappar är tillgängliga via dialogrutan **Hämta Data**, men den part som ansvarar för underhåll och support är fortfarande tredjepartsutvecklaren som skapade anslutningsappen. Även om Microsoft distribuerar dessa anslutningsappar ansvarar vi inte för deras prestanda eller funktioner.

Om du vill att en anpassad anslutningsapp ska certifieras ber du din leverantör att kontakta dataconnectors@microsoft.com.
