---
title: Bädda in en rapport i en säker portal eller webbplats
description: Power BI bäddar in funktionen kan användare enkelt och bädda in säkert rapporter i interna webbportalerna.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222241"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Bädda in en rapport i en säker portal eller webbplats

Med det nya **bädda in** alternativet för Power BI-rapporter, du kan enkelt och säkert bädda in rapporter i interna webbportalerna. Dessa portaler kan vara **molnbaserade** eller **lokala**, till exempel SharePoint 2019. Inbäddade rapporter respekterar alla behörigheter och data säkerhet via [rad säkerhet på radnivå (RLS)](service-admin-rls.md). De ger Kodlösa bädda in i valfri portal som accepterar en URL eller iFrame. 

Den **bädda in** alternativet stöder [URL-filter](service-url-filters.md) och URL-inställningar. Det kan du integrera med hanteringsportalen med hjälp av en metod för med lite kod som kräver endast grundläggande HTML och JavaScript kunskaper.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>**Bädda in** Power BI-rapporter i portaler

1. Det nya alternativet **Bädda in** finns på **Arkiv**-menyn i rapporter i Power BI-tjänsten.

    ![Listrutealternativet för säker inbäddning](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Välj den **bädda in** möjligheten att öppna en dialogruta som innehåller en länk och en iFrame som du kan använda för att bädda in rapporten på ett säkert sätt.

    ![Dialogruta med inbäddningsalternativ](media/service-embed-secure/secure-embed-code-dialog.png)

3. Om en användare öppnar en rapport-URL direkt, eller en inbäddad i en webbportal, kräver Rapportåtkomst användarautentisering. Följande skärm visas om en användare inte har loggat in till Power BI i webbläsarsession. När de väljer **inloggning**, ett nytt webbläsarfönster eller flik kan öppna. Låta dem efter popup-blockerare om de inte ska uppmanas att logga in.

    ![Visa den här rapporten genom att logga in](media/service-embed-secure/secure-embed-sign-in.png)

4. När användaren har loggat in öppnar rapporten, som visar data och låta Sidnavigering och filtret. Endast användare som har behörighet att visa kan se rapporten i Power BI. Alla [rad säkerhet på radnivå (RLS)](service-admin-rls.md) regler tillämpas också. Slutligen måste användaren även vara korrekt licensierad – antingen genom att ha en Power BI Pro-licens, eller så måste rapporten finnas på en arbetsyta som finns i en Power BI Premium-kapacitet. Användaren måste logga in varje gång de öppnar ett nytt webbläsarfönster. Men när du har loggat in, laddas andra rapporter automatiskt.

    ![Bädda in rapport](media/service-embed-secure/secure-embed-report.png)

5. När du använder en iFrame, kan du behöva redigera den **höjd** och **bredd** att den passar behoven i din portal webbsida.

    ![Ange höjd och bredd](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Bevilja åtkomst till rapporten

Den **bädda in** alternativet inte automatiskt att tillåta användare att visa rapporten. Visa behörigheter anges i Power BI-tjänsten.

I Power BI-tjänsten kan du dela inbäddade rapporter med användare som behöver åtkomst. Om du använder en Office 365-grupp, kan du lista användaren som en medlem i app-arbetsytan. Läs mer om hur du [hantera din apparbetsyta i Power BI och Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licensiering

Om du vill visa den inbäddade rapporten, behöver användare antingen en licens för Power BI Pro eller också måste innehållet finnas i en arbetsyta som är i en [Power BI Premium-kapacitet (EM eller P SKU)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>Anpassa den inbäddade upplevelsen med hjälp av URL-inställningar

Du kan anpassa användarupplevelsen med hjälp av inställningar för inbäddning-URL. Du kan uppdatera URL: er i den angivna iFrame **src** inställningar.

| Egenskap  | Beskrivning  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Du kan använda den **pageName** frågesträngparametern om du vill ange vilka rapportsidan för att öppna. Du hittar det här värdet slutet rapport-URL när du visar en rapport i Power BI-tjänsten enligt nedan. |  |  |  |
| URL-filter  | Du kan använda [URL-filter](service-url-filters.md) i bädda in URL: en som du fått från Power BI-Användargränssnittet för att filtrera bädda in innehåll. På så sätt kan du skapa integreringar som bara använder lite kod integreringar med enbart grundläggande HTML och JavaScript.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Ange vilken sida öppnas för en inbäddad rapport 

Du hittar den **pageName** värdet slutet rapport-URL när du visar en rapport i Power BI-tjänsten.

1. Öppna rapporten från Power BI-tjänsten i webbläsaren och kopiera sedan fältet Webbadress.

    ![Rapportavsnitt](media/service-embed-secure/secure-embed-report-section.png)

2. Lägg till inställningen **pageName** i URL:en.

    ![Lägg till pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtrera rapportinnehåll med hjälp av URL-filter 

Du kan använda [URL-filter](service-url-filters.md) att tillhandahålla olika rapportvyer. URL:en nedan filtrerar t.ex. rapporten för att visa data för energibranschen.

Att använda kombination av **pageName** och [URL-filter](service-url-filters.md) kan vara effektivt. Du kan skapa upplevelser med grundläggande HTML och JavaScript.

Här är till exempel en knapp som du kan lägga till en HTML-sida:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

När du väljer anropar knappen en funktion för att uppdatera iFrame med en uppdaterad Webbadress, som omfattar energi bransch filter.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filtrera](media/service-embed-secure/secure-embed-filter.png)

Du kan lägga till så många knappar du vill skapa en anpassad upplevelse med lite kod. 

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

* Stöder inte externa gästanvändare med Azure företag till företag (B2B).

* Säker inbäddning fungerar för rapporter som publicerats i Power BI-tjänsten.

* Användaren måste logga in att visa rapporten varje gång de öppnar ett nytt webbläsarfönster.

* Vissa webbläsare måste du uppdatera sidan efter inloggningen, särskilt när de använder InPrivate- eller Incognito-lägen.

* Få en enkel inloggning, använda inbäddade i SharePoint Online-alternativet eller skapa en anpassad integrering med hjälp av den [användaren äger data](developer/embed-sample-for-your-organization.md) bädda in metod. 

* Den automatiska autentiseringsfunktionen som tillhandahålls av alternativet **Bädda in** fungerar inte med Power BI JavaScript-API:et. Power BI JavaScript API använder den [användaren äger data](developer/embed-sample-for-your-organization.md) bädda in metod. 

## <a name="next-steps"></a>Nästa steg

* [Olika sätt att dela ditt arbete i Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtrera en rapport med parametrar för frågesträngen i Webbadressen](service-url-filters.md)

* [Bädda in med rapportwebbdel i SharePoint Online](service-embed-report-spo.md)

* [Publicera på webben från Powerbi](service-publish-to-web.md)