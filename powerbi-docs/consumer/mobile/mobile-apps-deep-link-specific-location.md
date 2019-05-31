---
title: Skapa en länk till en specifik plats i Power BI-mobilapparna
description: Lär dig hur du skapar en djuplänk till en specifik instrumentpanel, panel eller rapport i Power BI-mobilappen med en URI (Uniform Resource Identifier).
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: mshenhav
ms.openlocfilehash: 4e09b10e38b018f8e5572343b343a243ace3bf81
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906532"
---
# <a name="create-a-link-to-a-specific-location-in-the-power-bi-mobile-apps"></a>Skapa en länk till en specifik plats i Power BI-mobilapparna
Du kan använda länkar för direkt åtkomst till specifika objekt i Power BI: Rapporten, instrumentpanel och panel.

Det finns främst två scenarier för att använda länkar i Power BI Mobile: 

* Öppna Power BI från **utanför appen**, och mark på specifikt innehåll (rapporten/instrumentpanelen/app). Detta är vanligtvis en integreringsscenario när du vill öppna Power BI Mobile från andra appar. 
* Att **navigera** i Power BI. Detta är vanligtvis när du vill skapa en anpassad navigering i Power BI.


## <a name="use-links-from-outside-of-power-bi"></a>Använda länkar från utanför Power BI
När du använder en länk från utanför Power BI-appen du vill se till att den öppnas av appen, och om appen inte har installerats på enheten och sedan till att ge användaren för att installera den. Vi har skapat ett format för länken för att stödja just. Det här länkformatet kommer att se till att enheten använder appen för att öppna länken, och om appen inte har installerats på enheten, erbjuds användaren gå till butiken för att hämta den.

Länken ska börja med följande  
```html
https://app.powerbi.com/Redirect?[**QUERYPARAMS**]
```

> [!IMPORTANT]
> Om ditt innehåll finns i särskilda datacenter Government, Kina, t.ex. Länken ska börja med rätt Power BI-adressen som `app.powerbigov.us` eller `app.powerbi.cn`.   
>


Den **fråga PARAMS** är:
* **åtgärden** (obligatoriskt) = OpenApp / OpenDashboard / OpenTile / Öppna rapport
* **appId** = om du vill öppna en rapport eller instrumentpanel som ingår i en app 
* **groupObjectId** = om du vill öppna en rapport eller instrumentpanel som ingår i arbetsytan (men inte Min arbetsyta)
* **dashboardObjectId** = instrumentpanelen objekt-ID (om åtgärden är OpenDashboard eller OpenTile)
* **reportObjectId** = rapporten objekt-ID (om åtgärden är öppna rapport)
* **tileObjectId** = panel objekt-ID (om åtgärden är OpenTile)
* **reportPage** = om du vill öppna specifika rapportavsnittet (om åtgärden är öppna rapport)
* **ctId** = objekt organisations-ID (som är relevant för B2B-scenariot. Detta kan utelämnas om objektet som hör till användarens organisation).

**Exempel:**

* Öppna appen länk 
  ```html
  https://app.powerbi.com/Redirect?action=OpenApp&appId=appidguid&ctid=organizationid
  ```

* Öppna instrumentpanelen som ingår i en app 
  ```html
  https://app.powerbi.com/Redirect?action=OpenDashboard&appId=**appidguid**&dashboardObjectId=**dashboardidguid**&ctid=**organizationid**
  ```

* Öppna rapporten som ingår i en arbetsyta
  ```html
  https://app.powerbi.com/Redirect?Action=OpenReport&reportObjectId=**reportidguid**&groupObjectId=**groupidguid**&reportPage=**ReportSectionName**
  ```

### <a name="how-to-get-the-right-link-format"></a>Så här hämtar du rätt länkformat

#### <a name="links-of-apps-and-items-in-app"></a>Länkar för appar och objekt i appen

För **appar och rapporter och instrumentpanel som ingår i en app**, det enklaste sättet att hämta en länk är att gå till app-arbetsytan och välj ”Uppdatera app”. ”Publicera appupplevelsen” öppnas och du hittar i fliken åtkomst en **länkar** avsnittet. Expandera att avsnittet och du ser listan över appen och allt dess innehåll länkar som kan användas för att komma åt dem direkt.

![Powerbi publicera app länkar ](./media/mobile-apps-links/mobile-link-copy-app-links.png)

#### <a name="links-of-items-not-in-app"></a>Länkar för objekt inte i app 

För rapporter och instrumentpaneler som inte är en del av en app, måste du extrahera de ID: N från URL: en för objektet.

Till exempel vill hitta 36 tecken **instrumentpanelen** objekt-ID, navigera till den specifika instrumentpanelen i Power BI-tjänsten 

```html
https://app.powerbi.com/groups/me/dashboards/**dashboard guid comes here**?ctid=**organization id comes here**`
```

Att hitta 36 tecken **rapporten** objekt-ID, navigera till den specifika rapporten i Power BI-tjänsten.
Det här är ett exempel på rapport från ”Min arbetsyta”

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**`
```
URL: en ovan innehåller även viss rapportsida **”ReportSection3”** .

Det här är ett exempel på en rapport från en arbetsyta (inte Min arbetsyta)

```html
https://app.powerbi.com/groups/**groupid comes here**/reports/**reportid comes here**/ReportSection1?ctid=**organizationid comes here**
```

## <a name="use-links-inside-power-bi"></a>Använda länkar i Power BI

Länkar i Power BI fungerar i mobilapparna exakt som i Power BI-tjänsten.

Du kan bara kopiera objekt URL: en från adressfältet i webbläsaren om du vill lägga till länken i rapporten som pekar på ett annat objekt i Power BI. Läs mer om [hur du lägger till en hyperlänk i en textruta i en rapport](https://docs.microsoft.com/power-bi/service-add-hyperlink-to-text-box).

## <a name="use-report-url-with-filter"></a>Använd rapport-URL med filter
Samma som Power BI-tjänsten, Power BI Mobile-appar stöder även rapport-URL som innehåller en filter-fråga param. Du kan öppna en rapport i Power BI-appen och filtrera till specifika tillstånd. Exempelvis kan den här URL: en öppnas rapporten och filtrera per område

```html
https://app.powerbi.com/groups/me/reports/**report guid comes here**/ReportSection3?ctid=**organization id comes here**&filter=Store/Territory eq 'NC'
```

Läs mer om [Skapa fråga param att filtrera rapporter](https://docs.microsoft.com/power-bi/service-url-filters).

## <a name="next-steps"></a>Nästa steg
Din feedback hjälper oss att bestämma vad som ska implementeras i framtiden, så glöm inte att rösta för andra funktioner som du skulle vilja se i Power BI-mobilapparna. 

* [Power BI-appar för mobila enheter](mobile-apps-for-mobile-devices.md)
* Följ @MSPowerBI på Twitter
* Delta i konversationen i [Power BI Community](http://community.powerbi.com/)
* [Vad är Power BI?](../../power-bi-overview.md)

