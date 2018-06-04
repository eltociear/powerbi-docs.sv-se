---
title: Power BI-behörigheter
description: Power BI-behörigheter
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: 4ba0e62dd8c9ba537f56c97489541591ec0bf2bc
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34289428"
---
# <a name="power-bi-permissions"></a>Power BI-behörigheter
## <a name="permission-scopes"></a>Behörighetsomfattning
Med Power BI:s behörigheter kan ett program vidta vissa åtgärder åt en användare. Alla behörigheter måste godkännas av användaren för att vara giltiga.

| Visningsnamn | Beskrivning | Omfattningsvärde |
| --- | --- | --- |
| Visa alla datauppsättningar |Appen kan visa alla datauppsättningar för den inloggade användaren och datauppsättningar som användaren har åtkomst till. |Dataset.Read.All |
| Läs och skriv till alla datauppsättningar |Appen kan visa och skriva till alla datauppsättningar för den inloggade användaren och de datauppsättningar som användaren har åtkomst till. |Dataset.ReadWrite.All |
| Lägg till data i en användares datauppsättning (förhandsgranskning) |Ger en app åtkomst för att lägga till eller ta bort en användares datauppsättningsrader. Den här behörigheten ger inte appen åtkomst till användarens data. |Data.Alter_Any |
| Skapa innehåll (förhandsgranskning) |Appen kan automatiskt skapa innehåll och datauppsättningar för en användare. |Content.Create |
| Visa användarens grupper |Appen kan visa alla grupper som den inloggade användaren tillhör. |Group.Read |
| Visa alla grupper |Appen kan visa alla grupper som den inloggade användaren tillhör. |Group.Read.All |
| Visa alla instrumentpaneler (förhandsgranskning) |Appen kan visa alla instrumentpaneler för den inloggade användaren och de instrumentpaneler som användaren har åtkomst till. |Dashboard.Read.All |
| Visa alla rapporter (förhandsgranskning) |Appen kan visa alla rapporter för den inloggade användaren och rapporter som användaren har åtkomst till. Appen kan också se data i rapporterna samt deras struktur. |Report.Read.All |
| Läsa och skriva till alla rapporter |Appen kan visa och skriva till alla rapporter för den inloggade användaren och de rapporter som användaren har åtkomst till. Detta ger inte behörighet att skapa en ny rapport. |Report.ReadWrite.All |

Ett program kan begära behörighet när den först försöker logga in på en användares sida genom att skicka begärda behörigheter i omfattningsparametern för anropet. Om behörigheten beviljas returneras en åtkomsttoken till appen som kan användas på framtida API-anrop. Åtkomsten kan endast användas med ett visst program.

> [!NOTE]
> Power BI-API:er refererar fortfarande till apparbetsytor som grupper. Alla referenser till grupper innebär att du arbetar med apparbetsytor.
> 
> 

## <a name="requesting-permissions"></a>Begära behörighet
Även om du kan anropa API:n för att autentisera med ett användarnamn och lösenord för att vidta åtgärder åt en annan användare, kommer de att behöva begära behörighet som användaren sedan godkänner och sedan skicka resulterande åtkomsttoken för alla framtida anrop. För den här processen följer vi standardprotokollet [OAuth 2.0](http://oauth.net/2/). Även om den faktiska implementeringen kan variera har flödet för OAuth för Power BI följande element:

* **Inloggnings-UI** – Detta är ett gränssnitt som utvecklare kan använda för att begära behörighet. Det kräver att användaren loggar in om den inte redan gjort det. Användaren måste också godkänna de behörigheter som programmet begär. Inloggningsfönstret skickar antingen tillbaka en åtkomstkod eller ett felmeddelande till en omdirigerings-URL som har angetts.
  * En standardomdirigerings-URL måste anges av Power BI för användning av interna program.
* **Auktoriseringskod** – Auktoriseringskoder returneras till webbprogram efter inloggning via URL-parametrar i omdirigerings-URL:en. Eftersom de finns i parametrar finns det en säkerhetsrisk. Webbprogram måste byta auktoriseringskod för en auktoriseringstoken
* **Auktoriseringstoken** – Används för att autentisera API-anrop åt en annan användare. De kommer att tillhöra ett visst program. Tokens har en angiven livslängd och när de upphör att gälla kommer de behöva uppdateras.
* **Uppdateringstoken** – När tokens upphör sker en process för att uppdatera dem.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

