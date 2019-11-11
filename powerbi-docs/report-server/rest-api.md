---
title: Utveckla med REST-API:er för Power BI-rapportservern
description: REST-API:n ger programmatisk åtkomst till objekten i en Power BI-rapportserverkatalog.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 05/25/2018
ms.openlocfilehash: 9b8e795c4a55f9efd6fd534d92d95b36c93cf2c0
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73874064"
---
# <a name="develop-with-the-rest-apis-for-power-bi-report-server"></a>Utveckla med REST-API:er för Power BI-rapportservern

Power BI-rapportservern stöder API:er med REST (Representational State Transfer). REST-API:er är tjänsteslutpunkter som stöder en uppsättning http-åtgärder (metoder) som ger åtkomst till att skapa, hämta, uppdatera eller ta bort resurser i en rapportserver.

REST-API:n ger programmatisk åtkomst till objekten i en Power BI-rapportserverkatalog. Exempel på objekt är mappar, rapporter, KPI:er, datakällor, datauppsättningar, uppdateringsplaner, prenumerationer och annat. Med hjälp av REST-API:n kan du som exempel navigera i mapphierarkin, identifiera innehållet i en mapp eller ladda ned en rapportdefinition. Du kan också skapa, uppdatera och ta bort objekt. Exempel på hur man kan arbeta med objekt är överföra en rapport, verkställa en uppdateringsplan, ta bort en mapp och så vidare.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-hybrid-note.md)]

## <a name="components-of-a-rest-api-requestresponse"></a>Komponenter i REST-API-begäran/-svar

Ett REST API-begäran/-svarspar kan delas in i fem komponenter:

* Aktuell **begärande-URI**, som består av: `{URI-scheme} :// {URI-host} / {resource-path} ? {query-string}`. Även om URI-begäran ingår i begärandets meddelandehuvud, redovisar vi den separat här eftersom de flesta språk eller ramverk kräver att du skickar den separat från begärandemeddelandet.
  
  * URI-schema: Anger det protokoll som används för att överföra begäran. Till exempel `http` eller `https`.
  * URI-värd: Anger domännamnet eller IP-adressen för servern där REST-tjänstslutpunkten finns, som `myserver.contoso.com`.
  * Resursens sökväg: Anger resursen eller resurssamlingen, vilket kan inkludera flera segment som används av tjänsten för att fastställa valet av dessa resurser. Till exempel: `CatalogItems(01234567-89ab-cdef-0123-456789abcdef)/Properties` Kan användas för att hämta de angivna egenskaperna för CatalogItem.
  * Frågesträng (valfritt): Ger ytterligare enkla parametrar, till exempel API-version eller resursurvalskriterier.
* Huvudfält för HTTP-begärandemeddelande:
  
  * En nödvändig [HTTP-metod](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html) (kallas även åtgärd eller verb) som talar om för tjänsten vilken typ av åtgärd som du begär. Reporting Services REST-API:er stöder metoderna DELETE, GET, HEAD, PUT, POST, och PATCH.
  * Valfria ytterligare huvudfält efter vad som krävs av den angivna URI- och HTTP-metoden.
* Valfria brödtextsfält för HTTP-**begärandemeddelande** till stöd för URI- och HTTP-åtgärder. Som exempel innehåller POST-åtgärder MIME-kodade objekt som skickas som komplexa parametrar. För POST- eller PUT-åtgärder måste MIME-kodningstypen för brödtexten anges även i `Content-type` begärandehuvudet. Vissa tjänster kräver att du använder en specifik MIME-typ, som `application/json`.
* **Huvudfält för HTTP-svarsmeddelande**:
  
  * En [HTTP-statuskod](https://www.w3.org/Protocols/HTTP/HTRESP.html) som sträcker sig från 2xx lyckade koder till 4xx eller 5xx felkoder. Som alternativ kan också en tjänstedefinierad statuskod returneras, i enlighet med beskrivningen i API-dokumentationen.
  * Valfria ytterligare huvudfält efter vad som krävs för att stödja svaret på begäran, som ett svarshuvud av formen `Content-type`.
* Valfria fält för **HTTP-svarsmeddelandets brödtext**:
  
  * MIME-kodade svarsobjekt returneras i HTTP-svarsbrödtexten som till exempel ett svar från en GET-metod som returnerar data. Normalt sett returneras dessa objekt i ett strukturerat format, till exempel JSON eller XML, enligt vad som anges av svarshuvudet av formen `Content-type` .

## <a name="api-documentation"></a>API-dokumentation

En modern REST-API behöver modern API-dokumentation. REST-API:n bygger på OpenAPI-specifikationen (kallas även swagger-specifikation) och dokumentationen finns på [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0). Utöver dokumentationen för API:n hjälper SwaggerHub även till och genererar ett klientbibliotek på önskat språk – JavaScript, TypeScript, C#, Java, Python, Ruby och andra.

## <a name="testing-api-calls"></a>Testa API-anrop

Ett verktyg för att testa HTTP-begäranden/svarsmeddelanden är [Fiddler](https://www.telerik.com/fiddler). Fiddler är en gratis proxy för felsökning av webbplatser som kan komma åt dina REST-begäranden, vilket gör det enkelt att diagnostisera HTTP-begärans-/svarsmeddelanden.

## <a name="next-steps"></a>Nästa steg

Granska de tillgängliga API:erna på [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/PBIRS/2.0).

Exempel finns på [GitHub](https://github.com/Microsoft/Reporting-Services). Exemplet innehåller en HTML5-app som bygger på TypeScript, React och Webpack och ett PowerShell-exempel.

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)