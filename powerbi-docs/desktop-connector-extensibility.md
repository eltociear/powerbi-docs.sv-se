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
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412994"
---
# <a name="connector-extensibility-in-power-bi"></a>Utökningsbarhet av anslutningsprogram i Power BI

I Power BI, kan kunder och utvecklare utöka datakällorna som de ansluter på många sätt. De använda befintliga kopplingar och generiska datakällor (till exempel ODBC, OData, Oledb, webb-, CSV, XML, JSON). Eller utvecklare skapa datatillägg kallas **anpassade anslutningar**, och gör dem **certifierade kopplingar**.

För närvarande kan du aktivera **anpassade Anslutningsappar** med hjälp av en meny där du kan på ett säkert sätt styra anpassad kod som du vill att köras på datorn. Du kan välja alla anpassade anslutningsappar eller bara anslutningar som är certifierade och distribueras av Microsoft i den **hämta Data** dialog.

## <a name="custom-connectors"></a>Anpassade anslutningar

**Anpassade Anslutningsappar** kan inkludera ett stort urval av möjligheter, sträcker sig från små API: er kritiska för verksamheten till stora branschspecifika tjänster som Microsoft har inte publicerat en koppling för. Många anslutningsappar distribueras av leverantören. Om du behöver för en specifik dataanslutning, bör du kontakta en leverantör.

Du använder en **-anpassad anslutning**, placerar den i den  *\[dokument]\\Power BI Desktop\\anpassade anslutningar* mappen och justera säkerhetsinställningar enligt beskrivningen i följande avsnitt.

Du behöver inte ändra säkerhetsinställningarna för att använda **certifierade anslutningsappar**.

## <a name="data-extension-security"></a>Säkerhetsinställningar för datatillägg

Ändra tillägget säkerhetsinställningar, i **Power BI Desktop** Välj **fil > Alternativ och inställningar > Alternativ > säkerhet**.

![Kontrollera om du vill läsa in anpassade anslutningsappar med Data tillägget säkerhetsalternativ](media/desktop-connector-extensibility/data-extension-security-1.png)

Under **Datatillägg** kan du välja mellan två säkerhetsnivåer:

* (Rekommenderas) Tillåt att endast certifierade filnamnstillägg läses in
* (Rekommenderas inte) Tillåt att alla tillägg läses in utan varning

Om du tänker använda **anpassade anslutningar** eller anslutningsappar som du eller en tredje part har utvecklat, måste du välja **”(Not Recommended) Tillåt alla tillägg att läsa in utan varning”** . Vi rekommenderar inte inställningen om du inte litar dina anpassade anslutningar. Eftersom koden i där kan hantera autentiseringsuppgifterna, till exempel skicka dem via HTTP, och ignorera sekretessnivåer.

På den **”(rekommenderas)”** security inställningen, om det finns anpassade anslutningsappar i systemet, visas ett fel som beskriver de kopplingar som det går inte att läsa in på grund av säkerhet.

![En dialogruta beskriver anpassade anslutningar som inte kan läsas in på grund av säkerhetsinställningar, i det här fallet videon Trippin'](media/desktop-connector-extensibility/data-extension-security-2.png)

För att lösa problemet och använda dessa anslutningar, ändra säkerhetsinställningarna för den **”(Not Recommended) Tillåt alla tillägg att läsa in utan varning”** som beskrivs tidigare. Starta sedan om **Power BI Desktop**.

## <a name="certified-connectors"></a>Certifierade kopplingar

En begränsad delmängd av datatillägg anses **Certified**. Få åtkomst till certifierade kopplingar i den **hämta Data** dialog. Men från tredje part utvecklaren som skapade anslutningen ansvarar för underhåll och support. Microsoft distribuerar kopplingar, men det är inte ansvarar för prestanda- eller fortsatt funktion är.

Om du vill att en anpassad anslutningsapp ska certifieras ber du din leverantör att kontakta dataconnectors@microsoft.com.
