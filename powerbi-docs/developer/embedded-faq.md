---
title: Vanliga frågor och svar om Power BI Embedded
description: Bläddra i en lista med vanliga frågor och svar om Power BI Embedded.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/27/2019
ms.openlocfilehash: 7670f8147af54f3b3a6c2c0eba34bb3ca7843eda
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74264067"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Vanliga frågor och svar om Power BI Embedded

* Om du har andra frågor [kan du fråga Power BI Community](https://community.powerbi.com/).
* Har du fortfarande problem? Besök [Power BI-supportsidan](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Allmänt

### <a name="what-is-power-bi-embedded"></a>Vad är Power BI Embedded?

Med [Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) kan programutvecklare bädda in snygga och helt interaktiva rapporter i sina program utan att behöva skapa egna datavisualiseringar och kontroller från grunden.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Vem kan använda Power BI Embedded?

Utvecklare och programvaruföretag, som ofta kallas för oberoende programvaruleverantörer (ISV, independent software vendors), som kodar appar.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Hur skiljer sig Power BI Embedded från Power BI-tjänsten?

Power BI är en analyslösning som tillhandahålls som tjänst och som ger organisationen en enhetlig vy över sina viktigaste affärsdata.

Microsoft har utvecklat Power BI Embedded för ISV:er som vill bädda in visuella objekt i sina appar, som hjälper kunderna att fatta analytiska beslut. Det här gör att ISV:erna inte behöver skapa egna analyslösningar. [Inbäddade analysverktyg](embedding.md) gör att företagsanvändare får tillgång till företagsdata och kan köra frågor mot dem för att skapa insikter direkt i appen.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Vad är skillnaden mellan Power BI Premium och Power BI Embedded?

Power BI Premium är kapacitet som riktar sig till företag som behöver en fullständig BI-lösning med en enhetlig översikt över organisationen, partners, kunder och leverantörer. Power BI Premium hjälper din organisation att fatta beslut. Power BI Premium är en SaaS-produkt där användarna konsumerar innehåll via mobilappar, internt utvecklade appar eller via Power BI-portalen.

Power BI Embedded är avsett för ISV:er som vill bädda in visuella objekt i sina appar. Power BI Embedded hjälper dina kunder fatta beslut eftersom Power BI Embedded har utvecklats för programutvecklare. Kunder som använder appen kan använda innehåll som lagras på Power BI Embedded, oavsett om de är inom eller utanför organisationen. Du kan inte dela innehåll i Power BI Embedded-kapaciteter till webben eller publicera det på SharePoint med ett enda klick.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Vad rekommenderar Microsoft när en kund vill köpa antingen Power BI Premium eller Power BI Embedded?

Microsoft rekommenderar att företag köper Power BI Premium, som är en egenhanterad BI-molnlösning i företagsklass. Vi rekommenderar att ISV:er köper Power BI Embedded för dess molndrivna, inbäddade analyskomponenter. Det finns dock inga begränsningar för vilken produkt kunderna köper.

Det kan finnas tillfällen där en ISV (vanligtvis stor), förutom att bädda in objekt i appar, vill använda en P-SKU för dra nytta av ytterligare fördelar med den kompletta Power BI-tjänsten i organisationen. Vissa företag kan välja att använda A-SKU:er i Azure om de bara är intresserade av att bygga program för affärsverksamheten och bädda in analysverktyg i dem och inte är intresserade av att använda den kompletta Power BI-tjänsten.

### <a name="how-many-embed-tokens-can-i-create"></a>Hur många inbäddningstoken kan jag skapa?

Inbäddningstoken med PRO-licenser är avsedda för utvecklingstestning, så ett Power BI-huvudkonto eller [tjänstens huvudnamn](embed-service-principal.md) kan bara generera ett begränsat antal inbäddningstoken. [Köp en kapacitet](#technical) för inbäddning i en produktionsmiljö. Det finns ingen gräns för att hur många inbäddningstoken du kan generera när du köper en kapacitet. Gå till [Tillgängliga funktioner](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) för att kontrollera användningsvärdet som anger aktuell inbäddad användning i procent.

## <a name="technical"></a>Teknik

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Vad är skillnaden mellan A-SKU:er i Azure och EM-SKU:er i Office 365?

PowerBI.com är en SaaS-lösning för företag med många funktioner, som socialt samarbete, e-postprenumerationer och många andra. På PowerBI.com kan ISV:er hantera sin inbäddade analyslösning och inställningar för olika klientorganisationer.

Power BI Embedded är PaaS-tjänst med en uppsättning API:er som utvecklare kan använda för att skapa inbäddade analyslösningar.

Här är en ofullständig lista med skillnader.

| Visning av aktuellt objekt | Power BI Embedded | Power BI Premium-kapacitet | Power BI Premium-kapacitet |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | A SKUs-Azure-kapacitet | EM SKUs-O365-kapacitet | P SKUs-O365-kapacitet |
| Bädda in artefakter från en Power BI-arbetsyta | Ja | Ja | Ja |
| Förbruka Power BI-rapporter i ett inbäddat program – SaaS | Nej | Ja | Ja |
| Förbruka Power BI-rapporter i ett inbäddat program – PaaS | Ja | Ja | Ja |
| Använda Power BI-rapporter i SharePoint | Nej | Ja | Ja |
| Använda Power BI-rapporter i Dynamics | Nej | Ja | Ja |
| Använda Power BI-rapporter i Teams (gäller inte mobilapp) | Nej | Ja | Ja |
| Få åtkomst till innehåll i Powerbi.com och Power BI Mobile med en kostnadsfri Power BI-licens | Nej | Nej | Ja |
| Få åtkomst till innehåll som är inbäddat i MS Office-appar med en kostnadsfri Power BI-licens | Nej | Ja | Ja |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Power BI erbjuder tre SKU:er för inbäddning: A SKU, EM SKU och P SKU. Vilken ska jag beställa för mitt scenario?

|  |A SKU (Power BI Embedded)  |EM SKU (Power BI Premium)  |P SKU (Power BI Premium)  |
|---------|---------|---------|---------|
|Köp  |Azure Portal |Office |Office |
|Användningsfall | Bädda in innehåll i ditt eget program | <li> Bädda in innehåll i ditt eget program <br><br><br> <li> Bädda in innehåll i MS Office-program: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (gäller inte mobilapp)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) | <li> Bädda in innehåll i ditt eget program <br><br><br> <li> Bädda in innehåll i MS Office-program: <br> - [SharePoint](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/) <br> - [Teams (gäller inte mobilapp)](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/) <br> - [Dynamics 365](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard) <br><br><br> <li> Dela innehåll med Power BI-användare via [Power BI-tjänsten](https://powerbi.microsoft.com/)  |
|Fakturering |Varje timma |Varje månad |Varje månad |
|Bindningstid  |Ingen bindningstid |Varje år  |Varje månad/varje år |
|Skillnad |Fullständig elasticitet. Kan skapa upp/ner, pausa/återuppta resurser i Azure Portal eller med API  |Du kan använda det här till att bädda in innehåll i SharePoint Online och Microsoft Teams (gäller inte mobilappar) |Kombinera att bädda in i applikationer och använda Power BI-tjänsten i samma utsträckning |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Vilka är kraven för att skapa en PBIE-kapacitet i Azure?

* Logga in i organisationskatalogen (Microsoft-konton stöds inte).
* Du måste ha en Power BI-klientorganisation, så minst en användare i katalogen måste vara registrerad för Power BI. 
* Du måste ha en Azure-prenumeration i din organisationskatalog.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Hur övervakar jag Power BI Embedded-kapacitetsförbrukning?

* Använda [Power BI-administratörsportalen](../service-admin-portal.md#power-bi-embedded).

* Ladda ned [måttappen](https://docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) i Power BI.

* Använda [diagnostikloggning i Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Kan min kapacitet skalas om automatiskt i förhållande till hur mycket min app används?

Automatisk skalanpassning finns inte för tillfället men alla API:er kan spalanpassas när som helst.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Varför placeras kapaciteten i pausat läge när den skapas/skalas/återupptas?

Etableringen av kapacitet kan misslyckas (skalning/återupptagning/skapande). Du kan använda API:et för att hämta information om du vill kontrollera ProvisioningState för en kapacitet: [Kapaciteter – hämta information](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Kan jag bara skapa Power BI Embedded-kapaciteter i en viss region?

Med funktionen [Multi-geo (förhandsversion)](embedded-multi-geo.md) kan du köpa en [Power BI Embedded-kapacitet](azure-pbie-create-capacity.md) i en annan region än hemplatsen för Power BI-klientorganisationen

### <a name="why-cant-i-see-a-workspace-although-i-have-permissions"></a>Varför kan jag inte se en arbetsyta trots att jag har behörighet?

När en användare ges behörigheter till en arbetsyta, app eller artefakt kanske den inte blir tillgängligt via API-anrop med en gång.
Resultatet kan antingen vara att artefakten saknas i ett GET-API-svar eller så kan det uppstå ett fel om du försöker använda artefakten.
Du kan lösa det här problemet genom att anropa [refreshUserPermissions API](https://docs.microsoft.com/rest/api/power-bi/users/refreshuserpermissions), som uppdaterar användarbehörigheterna.


### <a name="how-can-i-find-my-pbi-tenant-region"></a>Hur hittar jag regionen för min PBI-klientorganisation?

Du kan använda PBI-portalen för att ta reda på regionen för din PBI-klientorganisation.

[https://app.powerbi.com/](https://app.powerbi.com/ ) > ? > Om Power BI

![Om Power BI](media/embedded-faq/about-01.png)
![Klientorganisationsregion](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>Vad har Cloud Solution Provider-kanalen (CSP) stöd för?

* Du kan skapa PBIE för din klientorganisation med prenumerationstypen CSP.
* Ett partnerkonto kan logga in på en kundklientorganisation och köpa PBIE för kundklientorganisationen, och ange en användare hos kundklientorganisationen som Power BI-kapacitetsadministratör

### <a name="why-do-i-get-an-unsupported-account-message"></a>Varför visas ett meddelande om att kontot inte stöds?

Power BI kräver att du registrerar dig med ett organisationskonto. Du kan inte registrera dig för Power BI med ett Microsoft-konto.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Kan jag använda API:er till att skapa och hantera Azure-kapaciteter?

Ja, det finns PowerShell-cmdletar och REST-API:er för Azure Resource Manager som du kan använda till att skapa och hantera PBIE-resurser.

* [Rest-API:er](https://docs.microsoft.com/rest/api/power-bi-embedded/) 
* [PowerShell-cmdletar](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Vad är den dedikerade kapacitetsrollen för PBI Embedded i en PBI Embedded-lösning?

När du ska [höja upp din lösning till produktion](embed-sample-for-customers.md#move-to-production) måste du tilldela Power BI-innehållet (arbetsytan) som appen använder till en Power BI Embedded-kapacitet (A SKU).

### <a name="in-what-azure-regions-is-pbi-embedded-available"></a>I vilka Azure-regioner är PBI Embedded tillgängligt?

[PAM](https://ecosystemmanager.azurewebsites.net/home) (EcoManager) – Se Ansvarig för produkttillgänglighet

Tillgängliga regioner (16 – samma regioner som Power BI)

* USA (6) – USA, östra, USA, östra 2, USA, norra centrala, USA, södra centrala, USA, västra, USA, västra 2
* Europa (2) – Europa, norra, Europa, västra
* Asien och stillahavsområdet (2) – Asien, sydöstra, Asien, östra
* Brasilien (1) – Brasilien, södra
* Japan (1) – Japan, östra
* Australien (1) – Australien, sydöstra
* Indien (1) – Indien, västra
* Kanada (1) – Kanada, centrala
* Storbritannien (1) – Storbritannien, södra

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Vilken autentiseringsmodell används i Power BI Embedded?

Power BI Embedded fortsätter att använda Azure AD för autentisering av masteranvändaren (en licensierad utsedd Power BI Pro-användare), eller med [tjänstens huvudnamn](embed-service-principal.md), för autentisering av appen i Power BI.  

 En ISV kan implementera egen autentisering och auktorisering för sina appar.

Du kan använda en befintlig katalog om du redan har en Azure AD-klientorganisation. Du kan också skapa en ny Azure AD-klientorganisation som skydd för ditt inbäddade appinnehåll.

Du kan skaffa en AAD-token genom att använda något av [Azure Active Directory-autentiseringsbiblioteken](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Det finns klientbibliotek för flera plattformar.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Mitt program använder redan AAD för användarautentisering. Hur kan den här identiteten användas vid Power BI-autentisering i ett scenario där ”användaren äger data”?

Det är standard OAuth on-behalf-of-flöde (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Du måste konfigurera appen så att den kräver behörighet för Power BI-tjänsten (med nödvändiga omfång). När du har en användartoken till din app kan du helt enkelt anropa ADAL-API:et AcquireTokenAsync med hjälp av användartoken och ange webbadressen till Power BI-resursen som resurs-ID:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>Vilket objekt-ID används för tjänstens huvudnamn?

*Objekt-ID:t* från huvudskärmen i en registrerad app är objekt-ID för appen.

Objekt-ID:t i avsnittet *Hanterad app i den lokala katalogen > Egenskaper* är det objekt-ID för tjänsten huvudnamn som du måste använda. Det här objekt-ID:t används till att referera till ett huvudnamn för tjänsten vid åtgärder eller när du vill göra ändringar i objekt-ID:t för tjänstens huvudnamn. Ett exempel är om du lägger till tjänstens huvudnamn som administratör på en arbetsyta.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Hur skiljer sig Power BI Embedded från övriga Azure-tjänster?

Du måste ha ett Power BI-konto innan du köper Power BI Embedded i Azure. Distributionsregionen för Power BI Embedded avgör ditt Power BI-konto. Hantera din Power BI Embedded-resurs i Azure för att:

* Skalanpassa upp/ned
* Lägga till kapacitetsadministratörer
* Pausa/återuppta tjänsten

Använd PowerBI.com om du vill tilldela/ångra tilldelning av arbetsytor i din Power BI Embedded-kapacitet.

### <a name="what-content-pack-data-types-can-you-embed"></a>Vilka datatyper och innehållspaketet kan du bädda in?

Du kan *inte* bädda in **instrumentpaneler** eller **paneler** som bygger på datamängder i innehållspaket. Men du *kan* bädda in **rapporter** som bygger på en datamängd i ett innehållspaket.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Vad är skillnaden mellan att använda säkerhet på radnivå (RLS) och JavaScript-filter?

Det råder en viss förvirring kring när det är lämpligt att använda RLS och när JavaScript-filter passar bättre. Den ena metoden handlar om att styra vad en viss användare kan se och den andra om hur du optimerar användarens vy.

För RLS styr ISV-utvecklaren datafiltreringen som en del av modellskapandet och genereringen av inbäddningstoken. Slutanvändaren ser bara vad ISV-utvecklaren låter användaren se. I det här fallet kan användaren välja att se mindre än det som filtreras, men kan inte kringgå RLS-konfigurationen och se mer än vad som är tillåtet.

När det gäller filtrering på klientsidan (JavaScript) kan ISV-utvecklaren bestämma vad användaren ska se i den ursprunglig vyn, men sedan kan de inte styra ändringar som användaren själv gör i vyn. Eftersom Javascript-klientkod från användaren kan utlösa datafiltrering på serversidan kan den inte betraktas som säker.

Mer information finns i [Använda RLS jämfört med JavaScript-filter](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Hur hanterar jag behörigheter för tjänsthuvudnamn med Power BI?

Om du aktiverar [tjänstens huvudnamn](embed-service-principal.md) för användning med Power BI gäller inte längre appens AD-behörigheter. Programmets behörigheter hanteras då via Power BI-administrationsportalen.

Tjänsthuvudnamn ärver behörigheterna för alla Power BI-klientinställningar för deras säkerhetsgrupp. Begränsa behörigheterna genom att skapa en dedikerad säkerhetsgrupp för tjänstens huvudkonton och lägg till den i listan **Förutom vissa säkerhetsgrupper** för de relevanta, aktiverade Power BI-inställningarna.

Den här situationen spelar roll när du lägger till tjänstens huvudnamn som **administratör** för den nya arbetsyta. Du kan hantera den här uppgiften via [API:erna](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) eller med Power BI-tjänsten.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>När du använder ett program-ID jämfört med ett objekt-ID för tjänstens huvudnamn?

**[Program-ID:t](embed-sample-for-customers.md#application-id)** används för att skapa åtkomsttoken när program-ID:t skickas för autentisering.

För att referera ett tjänsthuvudnamn för åtgärder eller för att göra ändringar använder du **[objekt-ID för tjänstens huvudnamn](embed-service-principal.md#how-to-get-the-service-principal-object-id)** – till exempel tillämpa en tjänsthuvudnamn som administratör för en arbetsyta.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Kan du hantera en lokal datagateway med tjänstens huvudnamn?

Du kan inte hantera en lokal datagateway (datagateway) med hjälp av [tjänstens huvudnamn](embed-service-principal.md) som du kan göra med ett huvudkonto.

Med ett huvudkonto kan du installera en datagateway, lägga till användare i gatewayen, ansluta till datakällor och gör andra administrativa uppgifter.

Med tjänstens huvudnamn kan du konfigurera [säkerhet på radnivå (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal) med hjälp av en lokal SQL Server Analysis Services-datakälla (SSAS) med liveanslutning. På så sätt kan du hantera användare och deras åtkomst till data i SSAS vid integrering med **Power BI Embedded** med tjänstens huvudnamn.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Kan du logga in på Power BI-tjänsten med tjänstens huvudnamn?

Du kan inte logga in på Power BI med tjänstens huvudnamn.

Du kan inte använda innehåll som extern användare i externa program (SaaS-inbäddning), bara när du genererar en inbäddningstoken.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Vad är bästa praxis för att förbättra prestanda?

[Power BI Embedded-prestanda](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licensiering

### <a name="how-do-i-purchase-power-bi-embedded"></a>Hur köper jag Power BI Embedded?

Power BI Embedded är tillgänglig via Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Vad händer om jag redan har köpt Power BI Premium och vill ha några av fördelarna hos Power BI Embedded i Azure?

Kunder fortsätter att betala för alla befintliga Power BI Premium-inköp tills de aktuella avtalen har löpt ut och kan sedan ändra sina Power BI Premium-köp efter behov.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Måste jag köpa Power BI Premium för att få åtkomst till Power BI Embedded?

Nej, Power BI Embedded inkluderar den Azure-baserade kapaciteten som du behöver för att distribuera din lösning till dina kunder.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Vilka inköpsåtaganden gäller för Power BI Embedded?

Kunder kan ändra sin användning per timme. Det finns inget månatligt eller årligt åtagande för Power BI Embedded-tjänsten.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Hur visas användningen av Power BI Embedded på min faktura?

Power BI Embedded faktureras enligt en förutsägbar timavgift baserat på antalet distribuerade noder. Du debiteras så länge resursen är aktiv, även om den inte används. Du måste pausa resursen för att stoppa debiteringen.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Vem behöver en Power BI Pro-licens för Power BI Embedded och varför?

Du behöver en Power BI Pro-licens eller [tjänstens huvudnamn](embed-service-principal.md) för att använda REST-API:er. En analytiker som vill lägga till rapporter på en Power BI-arbetsyta måste antingen ha en Power BI Pro-licens eller använda tjänstens huvudnamn. Klientadministratörer som ska hantera Power BI-klientorganisationen och dess kapaciteter måste ha en Power BI Pro-licens.

Eftersom Power BI Embedded tillåter användning av Power BI-portalen för att hantera och verifiera inbäddat innehåll krävs en Power BI Pro-licens för att autentisera appen på PowerBI.com för att få tillgång till rapporterna i rätt databaser.

Men för att [skapa/redigera inbäddade rapporter](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) i ditt program behöver slutanvändaren inte en Pro-licens eftersom användaren inte behöver vara en Power BI-användare alls.

### <a name="can-i-get-started-for-free"></a>Kan jag komma igång gratis?

Ja, du kan använda din [Azure-kredit](https://azure.microsoft.com/free/) för Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Kan jag få en testperiod för Power BI Embedded i Azure?

Eftersom Power BI Embedded är en del av Azure kan du använda tjänsten med de [200 USD som du fick i kredit när du registrerade dig för Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Finns Power BI Embedded för nationella moln (US Government, Tyskland, Kina)?

Power BI Embedded är också tillgängligt för [nationella moln](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Är Power BI Embedded tillgängligt för ideella organisationer och högskolor?

Det finns inga särskilda Azure-priser för ideella organisationer och högskolor.

## <a name="power-bi-workspace-collection"></a>Power BI-arbetsytesamling

### <a name="what-is-power-bi-workspace-collection"></a>Vad är Power BI-arbetsytesamling?

**Power BI-arbetsytesamling** (**Power BI Embedded** version 1) är en lösning som baseras på Azure-resursen **Power BI-arbetsytesamling**. Med den här lösningen kan du skapa **Power BI Embedded**-program för dina kunder med Power BI-innehåll under **Power BI-arbetsytesamling**, dedikerade API:er och arbetsytesamlingsnycklar för att Power BI ska kunna autentisera programmet.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Kan jag migrera från Power BI-arbetsytesamling till Power BI Embedded?

1. Du kan använda migreringsverktyget för att klona **Power BI-arbetsytesamling**-innehåll till Power BI – https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Börja med **Power BI Embedded**-programmet POC som använder Power BI-innehåll.

3. När du är redo för produktion köper du en **Power BI Embedded**-dedikerad kapacitet och tilldelar ditt Power BI-innehåll (arbetsytan) till den kapaciteten.

    > [!Note]
    > Du kan fortsätta att använda **Power BI-arbetsytesamling** samtidigt som du bygger parallellt med en **Power BI Embedded**-lösning. När du är klar kan du flytta kunden till den nya **Power BI Embedded**-lösningen och dra tillbaka **Power BI-arbetsytesamlingen**.

Mer information finns i [Så här migrerar du innehåll från Power BI Embedded-arbetsytesamlingar till Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded).

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>Håller Power BI-arbetsytesamling på att bli inaktuell?

Ja, men kunder som redan använder **Power BI-arbetsytesamling** kan fortsätta att använda lösningen tills den är inaktuell. Kunder kan också skapa nya arbetsytesamlingar och eventuella **Power BI Embedded**-program som fortfarande använder **Power BI-arbetsytesamling**.

Men det innebär också att inga nya funktioner läggs till i lösningar som bygger på **Power BI-arbetsytesamling**. Vi rekommenderar våra kunder börjar planera migreringen till den nya lösningen **Power BI Embedded**.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>När kommer supporten för Power BI-arbetsytesamling att utgå?

Kunder som redan använder **Power BI-arbetsytesamlingar** kan fortsätta att använda det fram till slutet av juni 2018 eller till slutet av deras supportavtal.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>I vilka regioner kan jag skapa PBI-arbetsytesamling?

De tillgängliga regionerna är sydöstra Australien, södra Brasilien, centrala Kanada, USA, östra 2, östra Japan, norra centrala USA, Nordeuropa, södra centrala USA, Sydostasien, södra Storbritannien, Västeuropa, västra Indien och västra USA.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Varför bör jag migrera från PBI-arbetsytesamling till Power BI Embedded?

Det finns en del nya funktioner i **Power BI Embedded**-lösningen som du inte kan använda i **Power BI-arbetsytesamling**.

Detta är några av funktionerna:
* Alla PBI-datakällor stöds. Endast två datakällor för **Power BI-arbetsytesamling** stöds. 
* Nya funktioner, som frågor och svar, uppdatera, bokmärken, instrumentpanels- och panelinbäddning, anpassade menyer osv. stöds endast i **Power BI Embedded**-lösningen.
* Kapacitetsfaktureringsmodell.

## <a name="embedding-setup-tool"></a>Konfigurationsverktyget för inbäddning

### <a name="what-is-the-embedding-setup-tool"></a>Vad är konfigurationsverktyget för inbäddning?

Med [konfigurationsverktyget för inbäddning](https://aka.ms/embedsetup) kommer du snabbt igång och kan ladda ned ett exempelprogram och börja integrera med Power BI.

### <a name="which-solution-should-i-choose"></a>Vilken lösning ska jag välja?

* [Inbäddning för dina kunder](embedding.md#embedding-for-your-customers) ger dig möjlighet att bädda in instrumentpaneler och rapporter för användare som inte har något Power BI-konto. Kör lösningen [Embed for your customers](https://aka.ms/embedsetup/AppOwnsData) (Bädda in för dina kunder).
* [Inbäddning för din organisation](embedding.md#embedding-for-your-organization) låter dig utöka Power BI-tjänsten. Kör lösningen [Embed for your organization](https://aka.ms/embedsetup/UserOwnsData) (Bädda in för din organisation).

### <a name="ive-downloaded-the-sample-app-which-solution-do-i-choose"></a>Jag har laddat ned exempelappen. Vilken lösning ska jag välja?

Om du arbetar med upplevelsen **Embed for your customers** (Bädda in för dina kunder) börjar du med att spara och packa upp filen *PowerBI-Developer-Samples.zip*. Öppna sedan mappen *PowerBI-Developer-Samples-master\App Owns Data* och kör filen *PowerBIEmbedded_AppOwnsData.sln*.

Om du arbetar med upplevelsen **Embed for your organization** (Bädda in för din organisation) börjar du med att spara och packa upp filen *PowerBI-Developer-Samples.zip*. Öppna sedan mappen *PowerBI-Developer-Samples-master\User Owns Data\integrate-report-web-app* och kör filen *pbi-saas-embed-report.sln*.

### <a name="how-can-i-edit-my-registered-application"></a>Hur kan jag redigera mitt registrerade program?

Information om hur du redigerar Azure AD-registrerade program finns i [Snabbstart: Uppdatera ett program i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-update-azure-ad-app).

### <a name="how-can-i-edit-my-power-bi-user-profile-or-data"></a>Hur kan jag redigera min Power BI-användarprofil eller mina Power BI-data?

Mer information om hur du redigerar dina Power BI-data finns [här](https://docs.microsoft.com/power-bi/service-basic-concepts).

Mer information finns i artikeln om att [felsöka ditt inbäddade program](embedded-troubleshoot.md).

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
