---
title: Utökningsbara kopplingar i Power BI
description: Utökningsbara kopplingar, funktioner, säkerhetsinställningar och certifierade kopplingar
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 7d5d743dda31d05df0beb528648c5a43ffc6b335
ms.sourcegitcommit: 32a44dd17a44ccfd4a2d86a0d235251c2fda1c5c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68702119"
---
# <a name="connector-extensibility-in-power-bi"></a>Utökningsbarhet av anslutningsprogram i Power BI

I Power BI kan kunder och utvecklare utöka datakällorna som de ansluter till på många sätt. De använder befintliga anslutningsprogram och allmänna datakällor (till exempel ODBC, OData, OLEDB, Webb, CSV, XML, JSON). Eller så kan utvecklare skapa datatillägg, så kallade **anpassade anslutningsprogram**, och göra dem till **certifierade anslutningsprogram**.

För närvarande aktiverar du **anpassade anslutningsprogram** på en meny. Och du kan på ett säkert sätt styra nivån för anpassad kod som du vill ska få köras i ditt system. Du kan välja bland anpassade anslutningsprogram eller endast anslutningsprogram som certifierats och distribuerats av Microsoft i dialogrutan **Hämta data**.

## <a name="custom-connectors"></a>Anpassade anslutningar

**Anpassade anslutningsprogram** inbegriper många möjligheter – från små API:er som är viktiga för din verksamhet, till stora branschspecifika tjänster som Microsoft inte har publicerat ett anslutningsprogram för. Många anslutningsprogram distribueras av leverantören. Om du behöver ett särskilt dataanslutningsprogram bör du kontakta en leverantör.

Om du vill använda ett **anpassat anslutningsprogram** placerar du det i mappen *\[Dokument]\\Power BI Desktop\\Anpassade anslutningsprogram* och ändrar säkerhetsinställningarna enligt beskrivningen i följande avsnitt.

Du behöver inte ändra säkerhetsinställningarna för att använda **certifierade anslutningsappar**.

## <a name="data-extension-security"></a>Säkerhetsinställningar för datatillägg

Om du vill ändra säkerhetsinställningarna för datatillägg går du till **Power BI Desktop** och väljer **Arkiv > Alternativ och inställningar > Alternativ > Säkerhet**.

![Välj om du vill läsa in anpassade anslutningsprogram med säkerhetsalternativ för datatillägg](media/desktop-connector-extensibility/data-extension-security-1.png)

Under **Datatillägg** kan du välja mellan två säkerhetsnivåer:

* (Rekommenderas) Tillåt att endast certifierade filnamnstillägg läses in
* (Rekommenderas inte) Tillåt att alla tillägg läses in utan varning

Om du vill använda **anpassade anslutningsprogram** eller anslutningsprogram som du eller en tredje part har utvecklat och distribuerat, måste du välja **(Not Recommended) Allow any extension to load without warning** ((Rekommenderas inte) Tillåt att alla tillägg läses in utan varning). Vi rekommenderar att du inte använder den här säkerhetsinställningen såvida du inte litar till hundra procent på dina anpassade anslutningsprogram. Koden i dina anpassade anslutningsprogram kan hantera autentiseringsuppgifter, inklusive skicka dem via HTTP, och ignorera sekretessnivåer.

Om du använder säkerhetsinställningen som **rekommenderas** och det finns anpassade anslutningsprogram i ditt system får du ett felmeddelande om att ”anslutningsprogrammet inte har certifierats och att vi inte kan verifiera att det är säkert att använda” följt av en lista med anslutningsprograms om inte kan läsas in på ett säkert sätt.

![En dialogruta visas som beskriver de anpassade anslutningsprogram som inte kan läsas in på grund av säkerhetsinställningarna, i det här fallet TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Om du vill lösa felet utan att ändra säkerheten tar du bort de osignerade anslutningsprogrammen från mappen Anpassade anslutningsprogram.

För att åtgärda problemet så att du kan använda dessa anslutningsprogram måste du ändra säkerhetsinställningarna till inställningen **(Rekommenderas inte)** som beskrivs ovan. Sedan startar du om **Power BI Desktop**.

## <a name="certified-connectors"></a>Certifierade kopplingar

En begränsad delmängd av datatillägg betraktas som **certifierade**. Du kommer åt de certifierade anslutningsprogrammen i dialogrutan **Hämta data**. Men den tredjepartsutvecklare som har skapat anslutningsprogrammet ansvarar för underhåll och support. Även om vi (Microsoft) distribuerar dessa anslutningsprogram ansvarar vi inte för deras prestanda eller funktion.

Om du vill att en anpassad anslutningsapp ska certifieras ber du din leverantör att kontakta dataconnectors@microsoft.com.
