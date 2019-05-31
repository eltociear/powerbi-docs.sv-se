---
title: Vanliga frågor och svar om Power BI Embedded
description: Bläddra i en lista med vanliga frågor och svar om Power BI Embedded.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 05/22/2019
ms.openlocfilehash: 1bdc31d550573b926d45776307b8fcade95f0dc0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222179"
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Vanliga frågor och svar om Power BI Embedded

* Om du har andra frågor [kan du fråga Power BI Community](http://community.powerbi.com/).
* Har du fortfarande problem? Besök [Power BI-supportsidan](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Allmänt

### <a name="what-is-power-bi-embedded"></a>Vad är Power BI Embedded?

[Microsoft Power BI Embedded (PBIE)](azure-pbie-what-is-power-bi-embedded.md) kan utvecklare bädda in fantastiska, helt interaktiva rapporter i sina program utan att behöva skapa egna datavisualiseringar och kontroller från grunden.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Vem kan använda Power BI Embedded?

Utvecklare och programvaruföretag, även kallat oberoende programvaruleverantörer (ISV) som kodning program.

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Hur skiljer sig Power BI Embedded från Power BI-tjänsten?

Power BI är en analyslösning som tillhandahålls som tjänst och som ger organisationen en enhetlig vy över sina viktigaste affärsdata.

Microsoft har utvecklat Power BI Embedded för ISV: er som vill bädda in visuella objekt i sina program så att deras kunder fatta analytiska. Detta sparar ISV: er från att skapa sin egen analyslösning själva. [Inbäddade analyser](embedding.md) gör det möjligt för användare att komma åt företagets data och köra frågor mot den och generera insikter i programmet.


### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Vad är skillnaden mellan Power BI Premium och Power BI Embedded?

Power BI Premium är kapacitet som riktar sig till företag som vill ha en fullständig BI-lösning som ger en enda vy av dess organisation, partners, kunder och leverantörer. Power BI Premium hjälper din organisation att fatta beslut. Power BI Premium är en SaaS-produkt som tillåter användare att konsumera innehåll via mobilappar, internt utvecklade appar eller i Power BI-portalen.

Power BI Embedded är för ISV: er som vill bädda in visuella objekt i sina program. Power BI Embedded hjälper dina kunder fatta beslut eftersom Power BI Embedded har utvecklats för programutvecklare. Kunder som använder appen kan använda innehåll som lagras på Power BI Embedded, oavsett om de är inom eller utanför organisationen. Du kan inte dela Power BI Embedded innehåll med ett klick publicera på webben eller ett klick till SharePoint.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Vad rekommenderar Microsoft när en kund vill köpa antingen Power BI Premium eller Power BI Embedded?

Microsoft rekommenderar att företag köper Power BI Premium, en företagsklass, BI-lösning i molnet. Vi rekommenderar att programvaruleverantörer köper Power BI Embedded för dess molndrivna inbäddad analys-komponenter. En kund har dock ingen begränsning för vilken produkt att köpa.

Det kan finnas tillfällen där en ISV (vanligtvis stor), förutom app-inbäddning, vill använda en P-SKU för att få ytterligare fördelar av den kompletta Power BI-tjänsten i organisationen. Vissa företag kan välja att använda A-SKU:er i Azure om de bara är intresserade av att bygga program för affärsverksamheten och bädda in analysverktyg i dem och inte är intresserade av att använda den kompletta Power BI-tjänsten.

### <a name="how-many-embed-tokens-can-i-create"></a>Hur många inbäddningstoken kan jag skapa?

Bädda in med PRO-licenser är avsedda för Utvecklartestning, så en Power BI master-kontot eller [tjänstens huvudnamn](embed-service-principal.md) kan bara generera ett begränsat antal token. [Köp en kapacitet](#technical) för inbäddning i en produktionsmiljö. Det finns ingen gräns för hur många inbäddningstoken kan du skapa när du köper en kapacitet. Gå till [Tillgängliga funktioner](https://docs.microsoft.com/rest/api/power-bi/availablefeatures) för att kontrollera användningsvärdet som anger aktuell inbäddad användning i procent.

## <a name="technical"></a>Teknik

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Vad är skillnaden mellan A-SKU:er i Azure och EM-SKU:er i Office 365?

PowerBI.com är ett företag programvara som en tjänst (SaaS)-lösning med många funktioner, till exempel socialt samarbete, e-postprenumeration och andra funktioner. PowerBI.com hjälper oberoende programvaruleverantörer hantera sin inbäddade analyslösning innehåll och nivån klientinställningar.

Power BI Embedded är en plattform som en tjänst (PaaS) uppsättning API: er för utvecklare kan använda för att skapa en lösning för inbäddad analys.

Här är en lista över skillnaderna.

| Visning av aktuellt objekt | Power BI Embedded | Power BI Premium-kapacitet | Power BI Premium-kapacitet |
|----------------------------------------------------------------------------------|-------------------|---------------------------|---------------------------|
|   | (A SKU:er) | (EM SKU) | (P SKU) |
| Bädda in artefakter från en Power BI-apparbetsyta | Azure-kapacitet | Office 365-kapacitet | Office 365-kapacitet |
| Använda Power BI-rapporter i ett inbäddat program | Ja | Ja | Ja |
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
|Skillnad |Fullständig elasticitet. Kan skapa upp/ner, pausa/återuppta resurser i Azure Portal eller med API  |Du kan använda för att bädda in innehåll i SharePoint Online och Microsoft Teams (gäller inte mobila appar) |Kombinera att bädda in i applikationer och använda Power BI-tjänsten i samma utsträckning |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Vilka är kraven för att skapa en PBIE-kapacitet i Azure?

* Logga in i din organisationskatalog (Microsoft-konton inte stöds).
* Du måste ha en Power BI-klient, dvs, minst en användare i din katalog har registrerat sig för Power BI. 
* Du måste ha en Azure-prenumeration i din organisationskatalog.

### <a name="how-can-i-monitor-power-bi-embedded-capacity-consumption"></a>Hur övervakar jag Power BI Embedded-kapacitetsförbrukning?

* Använda [Power BI-administratörsportalen](../service-admin-portal.md#power-bi-embedded).

* Ladda ned [måttappen](https://review.docs.microsoft.com/power-bi/service-admin-premium-monitor-capacity) i Power BI.

* Använda [diagnostikloggning i Azure](azure-pbie-diag-logs.md).

### <a name="can-my-capacity-scale-automatically-to-adjust-to-my-app-consumption"></a>Kan min kapacitet kan skalas om automatiskt om du vill justera för app-förbrukning?

Eftersom det inte automatisk skalning nu kan är alla API: er kan spalanpassas när som helst.

### <a name="why-creatingscalingresuming-a-capacity-results-in-putting-the-capacity-into-a-suspended-state"></a>Varför placeras kapaciteten i pausat läge när den skapas/skalas/återupptas?

Kapacitet etablering (skala/återuppta/skapa) kan misslyckas. Du kan använda API: et för hämta information för att kontrollera en kapacitet ProvisioningState: [Kapaciteter – hämta information](https://docs.microsoft.com/rest/api/power-bi-embedded/capacities/getdetails).

### <a name="can-i-only-create-power-bi-embedded-capacities-in-a-specific-region"></a>Kan jag bara skapa Power BI Embedded-kapaciteter i en viss region?

Med funktionen [Multi-geo (förhandsversion)](embedded-multi-geo.md) kan du köpa en [Power BI Embedded-kapacitet](azure-pbie-create-capacity.md) i en annan region än hemplatsen för Power BI-klientorganisationen

### <a name="how-can-i-find-my-pbi-tenant-region"></a>Hur hittar jag min region för PBI-klient?

Du kan använda PBI-portalen för att hitta din region för PBI-klient.

[https://app.powerbi.com/](https://app.powerbi.com/) > ? > Om Power BI

![Om Power BI](media/embedded-faq/about-01.png)
![Klientorganisationsregion](media/embedded-faq/tenant-location-01.png)

### <a name="what-does-the-cloud-solution-provider-csp-channel-support"></a>Vad stöder Cloud Solution Provider (CSP) kanalen?

* Du kan skapa PBIE för din klientorganisation med prenumerationstypen CSP.
* Ett partnerkonto kan logga in på en kundklientorganisation och köpa PBIE för kundklientorganisationen, och ange en användare hos kundklientorganisationen som Power BI-kapacitetsadministratör

### <a name="why-do-i-get-an-unsupported-account-message"></a>Varför visas ett meddelande om att kontot inte stöds?

Power BI kräver att du registrerar dig med ett organisationskonto. Försök att registrera dig för Power BI med ett Microsoft-konto stöds inte.

### <a name="can-i-use-apis-to-create-and-manage-azure-capacities"></a>Kan jag använda API: er för att skapa och hantera Azure-funktionerna?

Ja, det är Powershell-cmdletar och Azure Resource Manager REST API: er kan använda för att skapa och hantera PBIE-resurser.

* [REST API: er](https://docs.microsoft.com/rest/api/power-bi-embedded/)
* [PowerShell-cmdletar](https://docs.microsoft.com/powershell/module/azurerm.powerbiembedded/)

### <a name="what-is-the-pbi-embedded-dedicated-capacity-role-in-a-pbi-embedded-solution"></a>Vad är den dedikerade kapacitetsrollen för PBI Embedded i en PBI Embedded-lösning?

Att [främja din lösning till produktion](embed-sample-for-customers.md#move-to-production), måste du tilldela Power BI-innehåll (apparbetsyta) används i ditt program till en Power BI Embedded (A SKU) kapacitet.

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

### <a name="what-is-power-bi-embeddeds-authentication-model"></a>Vad är Power BI Embedded 's autentiseringsmodellen?

Power BI Embedded fortsätter att använda Azure AD för autentisering av masteranvändaren (en utsedd Power BI Pro licensierade användare) eller med [tjänstens huvudnamn](embed-service-principal.md) för att autentisera appen i Power BI.  

 En ISV kan implementera sin egen autentisering och auktorisering för sina program.

Du kan använda en befintlig katalog om du redan har en Azure AD-klient. Du kan också skapa en ny Azure AD-klient för ditt inbäddade innehåll.

Du kan skaffa en AAD-token genom att använda något av [Azure Active Directory-autentiseringsbiblioteken](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries). Det finns klientbibliotek för flera plattformar.

### <a name="my-application-already-uses-aad-for-user-authentication-how-can-we-use-this-identity-when-authenticating-to-power-bi-in-a-user-owns-data-scenario"></a>Mitt program använder redan AAD för användarautentisering. Hur kan den här identiteten användas vid Power BI-autentisering i ett scenario där ”användaren äger data”?

Det är standard OAuth on-behalf-of-flöde (<https://docs.microsoft.com/azure/active-directory/develop/web-api>). Du måste konfigurera ditt program för att kräva Power BI-tjänsten (med nödvändiga omfång) behörigheter. När du har en användartoken till din app kan du helt enkelt anrop till ADAL API AcquireTokenAsync med hjälp av den användaråtkomsten-token och ange resurs-URL för Power BI som resurs-ID:

```csharp
var context = new AD.AuthenticationContext(authorityUrl);
var userAssertion = new AD.UserAssertion(userAccessToken);
var clientAssertion = new AD.ClientAssertionCertificate(MyAppId, MyAppCertificate)
var authenticationResult = await context.AcquireTokenAsync(resourceId, clientAssertion, userAssertion);
```

### <a name="what-object-id-is-the-service-principal-object-id"></a>Vad objekt-ID: T är tjänsten huvudnamn objekt-ID?

Den *objekt-ID* från huvudskärmen i en registrerad app är objekt-ID för appen.

Objektet med ID: T finns i den *hanterat program i den lokala katalogen > Egenskaper* avsnittet är tjänsten huvudnamn objekt-ID som du behöver använda. Objekt-ID är att referera till ett huvudnamn för tjänsten för åtgärder eller att göra ändringar i tjänstens huvudnamnsobjekt-ID. Till exempel använder ett huvudnamn för tjänsten som en administratör en arbetsyta.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Hur skiljer sig Power BI Embedded från övriga Azure-tjänster?

Du måste ha en Power BI-konto innan du köper Power BI Embedded i Azure. Din Power BI Embedded distribueras region anger Power BI-kontot. Hantera din Power BI Embedded-resurs i Azure för att:

* Skalanpassa upp/ned
* Lägga till kapacitetsadministratörer
* Pausa/återuppta tjänsten

Använd PowerBI.com om du vill tilldela/ångra tilldelning av arbetsytor i din Power BI Embedded-kapacitet.

### <a name="what-are-the-supported-deploy-regions"></a>Vad är stöds distribuera regioner?

Sydöstra Australien, södra Brasilien, centrala Kanada, USA, östra 2, västra Indien, östra Japan, norra centrala USA, Nordeuropa, södra centrala USA, Sydostasien, södra Storbritannien, Västeuropa, västra USA och USA, västra 2.

### <a name="what-content-pack-data-types-can-you-embed"></a>Vilka datatyper för Innehållspaketet kan du bädda in?

Du *kan inte* bädda in **instrumentpaneler** och **paneler** bygger på datauppsättningar i innehållspaket. Men du *kan* bädda in **rapporter** bygger på en datauppsättning i innehållspaket.

### <a name="what-is-the-difference-between-using-row-level-security-rls-vs-javascript-filters"></a>Vad är skillnaden mellan att använda jämfört med säkerhet på radnivå (RLS). JavaScript-filter?

Det finns ofta förvirring runt när du använder RLS jämfört med JavaScript-filter, eftersom en av metoderna om hur du styr vad en viss användare kan se och den andra är om hur du optimerar vyn.

För RLS styr ISV-utvecklaren datafiltreringen som en del av modellskapandet och genereringen av inbäddningstoken. Slutanvändaren ser bara vad ISV-utvecklaren låter användaren se. I det här fallet kan användaren välja att se mindre än det som filtreras, men kan inte kringgå RLS-konfigurationen och se mer än vad som är tillåtet.

Utvecklaren kan bestämma dig för vad användaren ser på den ursprungliga vyn för klientsidan filtrering (JavaScript), men de kan inte styra ändringar som användaren kan gälla för själva vyn. Eftersom användaren Javascript-klientkoden kan utlösa data filtrering på serversidan, den kan inte betraktas som säkra.

Mer information finns i [Använda RLS jämfört med JavaScript-filter](embedded-row-level-security.md#using-rls-vs-javascript-filters).

### <a name="how-do-i-manage-permissions-for-service-principals-with-power-bi"></a>Hur hanterar jag behörigheter för tjänsthuvudnamn med Power BI?

När du har aktiverat [tjänstens huvudnamn](embed-service-principal.md) för att använda med Power BI, AD programbehörigheter inte gälla längre. Programmets behörigheter hanteras då via Power BI-administrationsportalen.

Tjänsthuvudnamn ärver behörigheterna för alla Power BI-klientinställningar för deras säkerhetsgrupp. Om du vill begränsa behörighet, skapa en dedikerad säkerhetsgrupp för tjänstens huvudnamn och lägger till den i den **förutom specifika säkerhetsgrupper** för Power BI-inställningarna relevanta, aktiverad.

Den här situationen spelar roll när du lägger till tjänstens huvudnamn som **administratör** för den nya arbetsyta. Du kan hantera den här uppgiften via [API:erna](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser) eller med Power BI-tjänsten.

### <a name="when-to-use-an-application-id-vs-a-service-principal-object-id"></a>När du använder ett program-ID jämfört med ett objekt-ID för tjänstens huvudnamn?

**[Program-ID:t](embed-sample-for-customers.md#application-id)** används för att skapa åtkomsttoken när program-ID:t skickas för autentisering.

För att referera ett tjänsthuvudnamn för åtgärder eller för att göra ändringar använder du **[objekt-ID för tjänstens huvudnamn](embed-service-principal.md#how-to-get-the-service-principal-object-id)** – till exempel tillämpa en tjänsthuvudnamn som administratör för en arbetsyta.

### <a name="can-you-manage-an-on-premises-data-gateway-with-service-principal"></a>Kan du hantera en lokal datagateway med tjänstens huvudnamn?

Du kan inte hantera en lokal datagateway (datagateway) med hjälp av [tjänstens huvudnamn](embed-service-principal.md) som du kan göra med ett huvudkonto.

Med ett huvudkonto kan du installera en datagateway, lägga till användare i gatewayen, ansluta till datakällor och gör andra administrativa uppgifter.

Med tjänstens huvudnamn kan du konfigurera [säkerhet på radnivå (RLS)](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal-preview) med hjälp av en lokal SQL Server Analysis Services-datakälla (SSAS) med liveanslutning. På så sätt kan du hantera användare och deras åtkomst till data i SSAS vid integrering med **Power BI Embedded** med tjänstens huvudnamn.

### <a name="can-you-sign-into-the-power-bi-service-with-service-principal"></a>Kan du logga in på Power BI-tjänsten med tjänstens huvudnamn?

Du kan inte logga in på Power BI med tjänstens huvudnamn.

Du kan inte använda innehåll som extern användare i externa program (SaaS-inbäddning), bara när du genererar en inbäddningstoken.

### <a name="what-are-the-best-practices-to-improve-performance"></a>Vad är bästa praxis för att förbättra prestanda?

[Power BI Embedded-prestanda](embedded-performance-best-practices.md)

## <a name="licensing"></a>Licensiering

### <a name="how-do-i-purchase-power-bi-embedded"></a>Hur köper jag Power BI Embedded?

Power BI Embedded är tillgänglig via Azure.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-power-bi-embedded-in-azure-benefits"></a>Vad händer om jag redan har köpt Power BI Premium och vill ha några Power BI Embedded i Azure-förmåner?

Kunder fortsätter att betala för alla befintliga Power BI Premium-inköp tills deras aktuella avtal har löpt ut och, i det här läget kan sedan ändra sina Power BI Premium-inköp efter behov.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Måste jag köpa Power BI Premium för att få åtkomst till Power BI Embedded?

Nej, Power BI Embedded inkluderar den Azure-baserade kapaciteten som du behöver för att distribuera din lösning till dina kunder.

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Vilka inköpsåtaganden gäller för Power BI Embedded?

Kunder kan ändra sin användning per timme. Det finns inget månatligt eller årligt åtagande för Power BI Embedded-tjänsten.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Hur visas användningen av Power BI Embedded på min faktura?

Power BI Embedded faktureras enligt en förutsägbar timavgift baserat på antalet distribuerade noder. Du debiteras så länge en resurs är aktiv, även om det finns ingen användning. Du måste göra din resurs att stoppa debiteringen.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Vem behöver en Power BI Pro-licens för Power BI Embedded och varför?

Du behöver en Power BI Pro-licens eller [tjänstens huvudnamn](embed-service-principal.md) använder REST API: er. Om du vill lägga till rapporter till en Power BI-arbetsyta, måste en analytiker en Power BI Pro-licens eller tjänsten huvudnamn. För att hantera Power BI-klient och kapacitet, krävs en administratör har en Power BI Pro-licens.

Eftersom Power BI Embedded tillåter Power BI portal används för att hantera och verifiera inbäddat innehåll, krävs Power BI Pro-licens för att autentisera appen inuti PowerBI.com för att få tillgång till rapporterna i rätt databaser.

Men för att [skapa/redigera inbäddade rapporter](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Create-Report-in-Embed-View) i ditt program behöver slutanvändaren inte en Pro-licens eftersom användaren inte behöver vara en Power BI-användare alls.

### <a name="can-i-get-started-for-free"></a>Kan jag komma igång gratis?

Ja, du kan använda din [Azure-kredit](https://azure.microsoft.com/free/) för Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Kan jag få en testperiod för Power BI Embedded i Azure?

Eftersom Power BI Embedded är en del av Azure, är det möjligt att använda tjänsten med den [kredit på 200 USD som togs emot när du registrerar dig för Azure](https://azure.microsoft.com/free/).

### <a name="is-power-bi-embedded-available-for-national-clouds-us-government-germany-china"></a>Finns Power BI Embedded för nationella moln (US Government, Tyskland, Kina)?

Power BI Embedded är också tillgängligt för [nationella moln](embed-sample-for-customers-national-clouds.md).

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Är Power BI Embedded tillgängligt för ideella organisationer och högskolor?

Det finns inga särskilda priser för ideella organisationer och högskolor för Azure.

## <a name="power-bi-workspace-collection"></a>Power BI-arbetsytesamling

### <a name="what-is-power-bi-workspace-collection"></a>Vad är Power BI-arbetsytesamling?

**Power BI-Arbetsytesamling** (**Power BI Embedded** Version 1) är en lösning baserad på den **Power BI-Arbetsytesamling** Azure-resurs. Med den här lösningen kan du skapa **Power BI Embedded**-program för dina kunder med Power BI-innehåll under **Power BI-arbetsytesamling**, dedikerade API:er och arbetsytesamlingsnycklar för att Power BI ska kunna autentisera programmet.

### <a name="can-i-migrate-from-power-bi-workspace-collection-to-power-bi-embedded"></a>Kan jag migrera från Power BI-arbetsytesamling till Power BI Embedded?

1. Du kan använda migreringsverktyget för att klona **Power BI-arbetsytesamling**-innehåll till Power BI – https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded#content-migration.

2. Börja med **Power BI Embedded**-programmet POC som använder Power BI-innehåll.

3. När du är redo för produktion köper du en **Power BI Embedded**-dedikerad kapacitet och tilldelar ditt Power BI-innehåll (arbetsytan) till den kapaciteten.

    > [!Note]
    > Du kan fortsätta att använda **Power BI-arbetsytesamling** samtidigt som du bygger parallellt med en **Power BI Embedded**-lösning. När du är klar kan du flytta kunden till den nya **Power BI Embedded**-lösningen och dra tillbaka **Power BI-arbetsytesamlingen**.

Mer information finns i [Så här migrerar du innehåll från Power BI Embedded-arbetsytesamlingar till Power BI Embedded](https://docs.microsoft.com/power-bi/developer/migrate-from-powerbi-embedded).

### <a name="is-power-bi-workspace-collection-on-a-deprecation-path"></a>Är Power BI-Arbetsytesamling på en utfasning sökväg?

Ja, men kunder som redan använder den **Power BI-Arbetsytesamling** lösning kan fortsätta att använda den tills utfasningen. Kunder kan också skapa nya arbetsytesamlingar och eventuella **Power BI Embedded**-program som fortfarande använder **Power BI-arbetsytesamling**.

Men det innebär också att nya funktioner inte läggs till någon **Power BI-Arbetsytesamling** lösningar. Vi rekommenderar våra kunder att planera migreringen till den nya **Power BI Embedded** lösning.

### <a name="when-is-power-bi-workspace-collection-support-discontinued"></a>När kommer supporten för Power BI-arbetsytesamling att utgå?

Kunder som redan använder **Power BI-arbetsytesamlingar** kan fortsätta att använda det fram till slutet av juni 2018 eller till slutet av deras supportavtal.

### <a name="in-what-regions-can-i-create-a-pbi-workspace-collection"></a>I vilka regioner kan jag skapa en Arbetsytesamling för PBI?

De tillgängliga regionerna är sydöstra Australien, södra Brasilien, centrala Kanada, USA, östra 2, östra Japan, norra centrala USA, Nordeuropa, södra centrala USA, Sydostasien, södra Storbritannien, Västeuropa, västra Indien och västra USA.

### <a name="why-should-i-migrate-from-pbi-workspace-collection-to-power-bi-embedded"></a>Varför bör jag migrera från PBI-arbetsytesamling till Power BI Embedded?

Det finns vissa nya **Power BI Embedded** lösning funktioner och egenskaper som du inte kan göra med **Power BI-Arbetsytesamling**.

Detta är några av funktionerna:
* Alla PBI-datakällor som stöds. Bara två **Power BI-Arbetsytesamling** datakällor som stöds. 
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

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
