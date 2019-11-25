---
title: Power BI-behörigheter
description: Power BI-behörigheter
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 51c43a19613381d39e0397864e55baed2022663c
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74263993"
---
# <a name="power-bi-permissions"></a>Power BI-behörigheter

## <a name="permission-scopes"></a>Behörighetsomfattning

Med Power BI:s behörigheter kan ett program vidta vissa åtgärder åt en användare. Alla behörigheter måste godkännas av användaren för att vara giltiga.

| Visningsnamn | Beskrivning | Omfattningsvärde |
| --- | --- | --- |
| Visa alla datauppsättningar |Appen kan visa alla datauppsättningar för den inloggade användaren och datauppsättningar som användaren har åtkomst till. |Dataset.Read.All |
| Läs och skriv till alla datauppsättningar |Appen kan visa och skriva till alla datauppsättningar för den inloggade användaren och de datauppsättningar som användaren har åtkomst till. |Dataset.ReadWrite.All |
| Lägga till data i en användares datauppsättning |Ger en app åtkomst för att lägga till eller ta bort en användares datauppsättningsrader. Den här behörigheten ger inte appen åtkomst till användarens data. |Data.Alter_Any |
| Skapa innehåll |Appen kan automatiskt skapa innehåll och datauppsättningar för en användare. |Content.Create |
| Visa användarens grupper |Appen kan visa alla grupper som den inloggade användaren tillhör. |Group.Read |
| Visa alla grupper |Appen kan visa alla grupper som den inloggade användaren tillhör. |Group.Read.All |
| Läsa och skriva till alla grupper |Appen kan visa och skriva till den inloggade användarens alla grupper och de grupper som användaren har åtkomst till. |Group.ReadWrite.All |
| Visa alla instrumentpaneler |Appen kan visa alla instrumentpaneler för den inloggade användaren och de instrumentpaneler som användaren har åtkomst till. |Dashboard.Read.All |
| Visa alla rapporter |Appen kan visa alla rapporter för den inloggade användaren och rapporter som användaren har åtkomst till. Appen kan också se data i rapporterna samt deras struktur. |Report.Read.All |
| Läsa och skriva till alla rapporter |Appen kan visa och skriva till alla rapporter för den inloggade användaren och de rapporter som användaren har åtkomst till. Detta ger inte behörighet att skapa en ny rapport. |Report.ReadWrite.All |
| Läsa och skriva till alla kapaciteter |Appen kan visa och skriva till den inloggade användarens alla kapaciteter och de kapaciteter som användaren har åtkomst till. Detta ger inte behörighet att skapa en ny kapacitet. |Capacities.ReadWrite.All |
| Läsa alla kapaciteter |Appen kan visa och skriva till den inloggade användarens alla kapaciteter och de kapaciteter som användaren har åtkomst till. Detta ger inte behörighet att skapa en ny kapacitet. |Capacities.Read.All |
| Läsa och skriva allt innehåll i klienten |Appen kan visa och skriva till alla artefakter, till exempel grupper, rapporter, instrumentpaneler och datamängder i Power BI. Förutsatt att den inloggade användaren är en Power BI-tjänstadministratör. |Tenant.ReadWrite.All |
| Visa allt innehåll i klienten |Appen kan visa alla artefakter, till exempel grupper, rapporter, instrumentpaneler och datamängder i Power BI. Förutsatt att den inloggade användaren är en Power BI-tjänstadministratör. |Tenant.Read.All |

Ett program kan begära behörighet när den först försöker logga in på en användares sida genom att skicka begärda behörigheter i omfattningsparametern för anropet. Om behörigheten beviljas returneras en åtkomsttoken till appen som kan användas på framtida API-anrop. Åtkomsten kan endast användas med ett visst program.

> [!NOTE]
> I API:erna för Power BI kallas arbetsytor fortfarande för grupper. Referenser till grupper innebär att du arbetar med arbetsytor.

## <a name="requesting-permissions"></a>Begära behörighet

Även om du kan anropa API:n för att autentisera med ett användarnamn och lösenord för att vidta åtgärder åt en annan användare, kommer de att behöva begära behörighet som användaren sedan godkänner och sedan skicka resulterande åtkomsttoken för alla framtida anrop. För den här processen följer vi standardprotokollet [OAuth 2.0](https://oauth.net/2/). Även om den faktiska implementeringen kan variera har flödet för OAuth för Power BI följande element:

* **Inloggnings-UI** – Detta är ett gränssnitt som utvecklare kan använda för att begära behörighet. Det kräver att användaren loggar in om den inte redan gjort det. Användaren måste också godkänna de behörigheter som programmet begär. Inloggningsfönstret skickar antingen tillbaka en åtkomstkod eller ett felmeddelande till en omdirigerings-URL som har angetts.
  * En standardomdirigerings-URL måste anges av Power BI för användning av interna program.
* **Auktoriseringskod** – Auktoriseringskoder returneras till webbprogram efter inloggning via URL-parametrar i omdirigerings-URL:en. Eftersom de finns i parametrar finns det en säkerhetsrisk. Webbprogram måste byta auktoriseringskod för en auktoriseringstoken
* **Auktoriseringstoken** – Används för att autentisera API-anrop åt en annan användare. De kommer att tillhöra ett visst program. Tokens har en angiven livslängd och när de upphör att gälla kommer de behöva uppdateras.
* **Uppdateringstoken** – När tokens upphör sker en process för att uppdatera dem.

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)