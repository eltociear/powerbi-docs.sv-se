---
title: "Vanliga frågor och svar om Power BI Embedded"
description: "Bläddra i en lista med vanliga frågor och svar om Power BI Embedded."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 03/07/2018
ms.author: maghan
ms.openlocfilehash: 52ff1095c063be867354a23e0e8e4908a4b4e1d7
ms.sourcegitcommit: ee5d044db99e253c27816e0ea6bdeb9e39a2cf41
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/08/2018
---
# <a name="frequently-asked-questions-about-power-bi-embedded"></a>Vanliga frågor och svar om Power BI Embedded

* Om du har andra frågor [kan du fråga Power BI Community](http://community.powerbi.com/).
* Har du fortfarande problem? Besök [Power BI-supportsidan](https://powerbi.microsoft.com/support/).

## <a name="general"></a>Allmänt

### <a name="what-is-power-bi-embedded"></a>Vad är Power BI Embedded?

Med Microsoft Power BI Embedded kan programutvecklare bädda in attraktiva och helt interaktiva rapporter, instrumentpaneler och paneler i program utan att ödsla den tid och de utgifter som medföljer när man skapar egna datavisualiseringar och kontroller från grunden.

### <a name="who-is-the-target-audience-for-power-bi-embedded"></a>Vem kan använda Power BI Embedded?

Utvecklare och programvaruföretag som utvecklar sina egna program kallas ofta oberoende programvaruleverantörer (ISV; independent software vendors).

### <a name="how-is-power-bi-embedded-different-from-power-bi-the-service"></a>Hur skiljer sig Power BI Embedded från Power BI-tjänsten?

Power BI Embedded är avsedd för oberoende programvaruleverantörer och utvecklare som skapar program och vill bädda in visuella objekt i dessa program, så att deras kunder kan fatta beslut utan att behöva skapa en analyslösning från grunden. Inbäddade analysverktyg låter företagsanvändare få tillgång till företagsdata och ställa frågor för att skapa insikter om sina data inom applikationen.

Power BI, å andra sidan, är en analyslösning som tillhandahålls som tjänst och som ger organisationen en enhetlig vy över sina viktigaste affärsdata.

### <a name="what-is-the-difference-between-power-bi-premium-and-power-bi-embedded"></a>Vad är skillnaden mellan Power BI Premium och Power BI Embedded?

Power BI Premium är kapacitet som riktar sig till företag som behöver en fullständig BI-lösning som ger en enhetlig översikt över organisationen, partners, kunder och leverantörer. Power BI Premium hjälper din organisation att fatta beslut. Power BI Premium är en SaaS-produkt och har stöd för användning av innehåll via Power BI-portalen, mobilappar samt internt utvecklade appar.

Power BI Embedded är avsett för programvaruleverantörer eller utvecklare som utformar appar och vill bädda in visuella objekt i dessa appar. Power BI Embedded hjälper dina kunder fatta beslut eftersom Power BI Embedded har utvecklats för programutvecklare. Kunder som använder appen kan använda innehåll som lagras på Power BI Embedded, oavsett om de är inom eller utanför organisationen. Power BI Embedded-innehåll kan inte delas till webben eller SharePoint med ett klick och har inte stöd för SSRS-rapporter.

### <a name="what-is-the-microsoft-recommendation-for-when-a-customer-should-buy-power-bi-premium-vs-power-bi-embedded"></a>Vad rekommenderar Microsoft när en kund vill köpa antingen Power BI Premium eller Power BI Embedded?

Microsoft rekommenderar att företag köper Power BI Premium, en molnlösning i företagsklass för BI och att programvaruleverantörer köper Power BI Embedded, en inbäddad analyskomponent i molnet. Kunden kan dock välja att köpa det system de föredrar.

Det kan finnas tillfällen där en ISV (vanligtvis stor) vill använda en P-SKU för dra nytta av ytterligare fördelar med den kompletta Power BI-tjänsten i organisationen samt att bädda in i sina program. Och självklart kan vissa företag välja att använda A-SKU:er i Azure om de bara är intresserad av att bygga program för affärsverksamheten och bädda in analysverktyg i dem och inte är intresserade av att använda den kompletta Power BI-tjänsten.

### <a name="how-many-embed-tokens-can-i-create"></a>Hur många inbäddningstoken kan jag skapa?

Inbäddningstoken med PRO-licenser är avsedda för utveckling och utvecklartestning, så antalet inbäddningstoken ett Power BI-huvudkonto kan generera är begränsat. Du måste [köpa en kapacitet](https://docs.microsoft.com/power-bi/developer/embedded-faq#technical) för inbäddning i en produktionsmiljö. Det finns ingen gräns för att hur många inbäddningstoken du kan generera när en kapacitet köps.

### <a name="when-will-power-bi-embedded-be-available-in-azure"></a>När kommer Power BI Embedded att vara tillgänglig i Azure?

Power BI Embedded är redan tillgänglig.

## <a name="technical"></a>Teknik

### <a name="what-is-the-difference-between-the-a-skus-in-azure-and-the-em-skus-in-office-365"></a>Vad är skillnaden mellan A-SKU:er i Azure och EM-SKU:er i Office 365?

PowerBI.com är en enterprise-lösning som innehåller många funktioner, till exempel socialt samarbete, e-postprenumeration osv. som programvara som tjänst (SaaS)

Power BI Embedded är en uppsättning API:er som utvecklare kan använda för att bädda in analytiska lösningar i en plattform som tjänst. För scenariot med inbäddade analysverktyg bör PowerBI.com användas för att hjälpa programvaruutvecklare att hantera sin inbäddade analyslösning och klientnivåinställningar.

Här är en lista över några skillnader som du kan använda de olika funktionerna.

|Visning av aktuellt objekt  |Power BI Embedded<br>(A SKU:er) |Power BI Premium-kapacitet<br>(A SKU:er)  |
|---------|---------|---------|
|Bädda in artefakter från Power BI-appens arbetsytor     |Azure-kapacitet |Office 365-kapacitet |
|Power BI-licens krävs för att använda rapporter |Nej  |Ja |
|Använda Power BI-rapporter i ett inbäddat program |Ja  |Ja |
|Använda Power BI-rapporter i SharePoint |Nej |Ja |
|Använda Power BI-rapporter i Teams |Nej |Ja |

### <a name="power-bi-now-offers-three-skus-for-embedding-a-skus-em-skus-and-p-skus-which-one-should-i-purchase-for-my-scenario"></a>Power BI erbjuder tre SKU:er för inbäddning: A SKU, EM SKU och P SKU. Vilken ska jag beställa för mitt scenario?

|  |A SKU (Power BI Embedded)  |EM SKU (Power BI Premium)  |P SKU (Power BI Premium)  |
|---------|---------|---------|---------|
|Köp     |Azure Portal |Office |Office |
|Användningsfall |* Bädda in innehåll i ditt eget program |* Bädda in innehåll i ditt eget program<br>* Dela innehåll med Power B-användare (kostnadsfri) utanför PowerBI.com och bädda in i andra SaaS-program (SharePoint, Teams) |* Bädda in innehåll i ditt eget program<br>* Dela innehåll med Power B-användare (kostnadsfri) utanför PowerBI.com och bädda in i andra SaaS-program (SharePoint, Teams)<br>* Dela innehåll med Power BI-användare (kostnadsfri) via PowerBI.com  |
|Fakturering |Varje timma |Varje månad |Varje månad |
|Bindningstid  |Ingen bindningstid |Varje år  |Varje månad/varje år |
|Skillnad |Fullständig elasticitet. Kan skapa upp/ner, pausa/återuppta resurser i Azure Portal eller med API  |Kan användas för att bädda in innehåll i SharePoint Online och Microsoft Teams |Kombinera att bädda in i applikationer och använda Power BI-tjänsten i samma utsträckning |

### <a name="what-are-the-prerequisites-to-create-a-pbie-capacity-in-azure"></a>Vilka är kraven för att skapa en PBIE-kapacitet i Azure?

- Du måste logga in i din organisationskatalog (MSA-konton stöds inte).
- Du måste ha en Power BI-klient. Minst en användare i din katalog måste alltså ha registrerat sig för Power BI. 
- Du måste ha en Azure-prenumeration i din organisationskatalog.

### <a name="how-can-i-monitor-capacity-consumption"></a>Hur kan jag övervaka kapacitetsförbrukningen?

Vi kommer snart att erbjuda övervakning via Azure. Azure-resursen, Power BI Embedded, kommer att ha KPI:er för tillstånd och användning.

### <a name="will-my-capacity-scale-automatically-to-adjust-to-the-consumption-of-my-app"></a>Kommer min kapacitet att anpassas automatiskt i förhållande till hur mycket min app används?

Automatisk skalanpassning finns inte för tillfället men alla API:er kan spalanpassas när som helst.

### <a name="what-is-the-authentication-model-for-power-bi-embedded"></a>Vilken autentiseringsmodell används för Power BI Embedded?

Power BI Embedded kommer att fortsätta att använda Azure AD för autentisering av masteranvändaren (en licensierad utsedd Power BI Pro-användare), d.v.s. autentisering av appen i Power BI.

Autentisering och auktorisering för det användarna kommer att implementeras av programvaruutvecklaren. Utvecklaren kan implementera sin egen autentisering.

Om du redan har en Azure AD-klient kan du använda en befintlig katalog och skapa en ny Azure AD-klient för att skydda ditt inbäddade innehåll.

### <a name="how-is-power-bi-embedded-different-from-other-azure-services"></a>Hur skiljer sig Power BI Embedded från övriga Azure-tjänster?

Utvecklaren måste ha ett Power BI-konto innan de köper Power BI Embedded i Azure. Distributionsregionen för Power BI Embedded avgörs av ditt Power BI-konto. Hantera din Power BI Embedded-resurs i Azure för att:

* Skalanpassa upp/ned
* Lägga till kapacitetsadministratörer
* Pausa/återuppta tjänsten

Använd PowerBI.com om du vill tilldela/ångra tilldelning av arbetsytor i din Power BI Embedded-kapacitet.

### <a name="what-deploy-regions-are-supported"></a>Vilka distributionsregioner stöds?

Sydöstra Australien, södra Brasilien, centrala Kanada, östra USA 2, västra Indien, östra Japan, norra centrala USA, Nordeuropa, södra centrala USA, Sydostasien, södra Storbritannien, Västeuropa, västra USA och västra USA 2.

### <a name="what-type-of-content-pack-data-can-be-embedded"></a>Vilken typ av data i innehållspaket kan bäddas in?

**Instrumentpaneler** och **paneler** som skapas utifrån datauppsättningar i innehållspaket *kan inte* bäddas in, men **rapporter** som skapas utifrån en datauppsättning i innehållspaket *kan* bäddas in.

## <a name="licensing"></a>Licensiering

### <a name="how-do-i-purchase-power-bi-embedded"></a>Hur köper jag Power BI Embedded?

Power BI Embedded är tillgänglig via Azure.

### <a name="how-power-bi-embedded-be-metered"></a>Hur debiteras Power BI Embedded?

Power BI Embedded mäts per timme.

### <a name="how-does-the-usage-of-power-bi-embedded-show-up-on-my-bill"></a>Hur visas användningen av Power BI Embedded på min faktura?

Power BI Embedded faktureras enligt en förutsägbar timavgift baserat på antalet distribuerade noder. Observera att du debiteras så länge en resurs är aktiv, även om den inte används. För att sluta bli debiterad måste du aktivt pausa din resurs. Du kan pausa via Azure eller ARM-API:er.

### <a name="what-happens-if-i-already-purchased-power-bi-premium-and-now-i-want-some-of-the-benefits-of-power-bi-embedded-in-azure"></a>Vad händer om jag redan har köpt Power BI Premium och vill ha några av fördelarna hos Power BI Embedded i Azure?

Kunder fortsätter att betala för alla befintliga Power BI Premium-inköp tills deras aktuella avtal har löpt ut och kan sedan ändra sina Power BI Premium efter behov.

### <a name="do-i-still-have-to-buy-power-bi-premium-to-get-access-to-power-bi-embedded"></a>Måste jag köpa Power BI Premium för att få åtkomst till Power BI Embedded?

Nej, Power BI Embedded inkluderar den Azure-baserade kapaciteten som du behöver för att distribuera din lösning till dina kunder.

### <a name="who-needs-a-power-bi-pro-license-for-power-bi-embedded-and-why"></a>Vem behöver en Power BI Pro-licens för Power BI Embedded och varför?

Analytiker som behöver lägga till rapporter till en Power BI-arbetsyta, alla utvecklare som behöver använda REST API:er, eventuella klientadministratörer som behöver hantera Power BI-klienten och kapaciteter måste en licens för Power BI Pro.

Eftersom Power BI Embedded tillåter användning av Power BI-portalen för att hantera och verifiera inbäddat innehåll, krävs en Power BI Pro-licens för att autentisera appen inuti PowerBI.com för att få tillgång till rapporterna i rätt databaser.

### <a name="can-i-get-started-for-free"></a>Kan jag komma igång gratis?

Ja, du kan använda din [Azure-kredit](https://azure.microsoft.com/free/) för Power BI Embedded.

### <a name="can-i-get-a-trial-experience-for-power-bi-embedded-in-azure"></a>Kan jag få en testperiod för Power BI Embedded i Azure?

Eftersom Power BI Embedded är en del av Azure är det möjligt att använda tjänsten med de [200 USD som du fick i kredit när du registrerade dig för Azure](https://azure.microsoft.com/free/).

### <a name="whats-the-purchase-commitment-for-power-bi-embedded"></a>Vilka inköpsåtaganden gäller för Power BI Embedded? 

Kunder kan ändra sin användning per timme. Det finns inget månatligt eller årligt åtagande för Power BI Embedded-tjänsten.

### <a name="where-is-power-bi-embedded-available-us-government-germany-china-what-is-the-timing"></a>Var är Power BI Embedded tillgängligt? Myndigheter i USA? Tyskland? Kina? Hur ser tidsplanen ut?

Power BI Embedded finns i kommersiella Azure-moln och i molnet för amerikanska myndigheter.  Tillgänglighet på moln för myndigheter för Tyskland och Kina kommer att läggas till i framtiden.

### <a name="is-power-bi-embedded-available-for-non-profits-and-educational"></a>Är Power BI Embedded tillgängligt för ideella organisationer och högskolor?

Ideella organisationer och högskolor kan köpa Azure. Det finns ingen särskild prissättning för dessa typer av kunder i Azure.

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
