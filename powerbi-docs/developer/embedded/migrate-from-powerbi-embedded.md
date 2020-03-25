---
title: Så här migrerar du innehåll från Power BI-arbetsytesamlingar till Power BI
description: Lär dig hur du migrerar från Power BI-arbetsytesamling till Power BI Embedded och utnyttjar nyheterna för inbäddning i appar.
author: KesemSharabi
ms.author: kesharab
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/30/2018
ms.openlocfilehash: 20546e0c9251f39ca49f6d713d5db48401937505
ms.sourcegitcommit: 2c798b97fdb02b4bf4e74cf05442a4b01dc5cbab
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80114415"
---
# <a name="how-to-migrate-power-bi-workspace-collection-content-to-power-bi-embedded"></a>Så här migrerar du innehåll från Power BI-arbetsytesamlingar till Power BI Embedded

Lär dig hur du migrerar från Power BI-arbetsytesamling till Power BI Embedded och utnyttjar nyheterna för inbäddning i appar.

Microsoft presenterade nyligen [Power BI Embedded](https://powerbi.microsoft.com/blog/power-bi-embedded-capacity-based-skus-coming-to-azure/), en ny kapacitetsbaserad licensieringsmodell som ökar flexibiliteten för hur användare får åtkomst till innehåll, och hur de kan dela och distribuera det. Erbjudandet ger också ytterligare skalbarhet och prestanda.

Med Power BI Embedded får du en API-yta, en konsekvent uppsättning funktioner och tillgång till de senaste funktionerna i Power BI när du bäddar in innehåll, som instrumentpaneler, gatewayer och arbetsytor. Framöver kommer du att kunna börja med Power BI Desktop och gå vidare till distribution med Power BI Embedded.

Nuvarande Power BI-arbetsytesamling fortsätter att vara tillgänglig under en begränsad tid. Kunder med ett Enterprise-avtal har åtkomst till dess att deras befintliga avtal förfaller. Kunder som anskaffat Power BI-arbetsytesamling genom direkt- eller CSP-kanaler har åtkomst i ett år efter den allmänt tillgängliga versionen av Power BI Embedded.  Den här artikeln ger dig anvisningar om hur du migrerar från Power BI-arbetsytesamling till den nya Power BI Embedded-miljön, och information om vilka förändringar du kan förvänta dig i ditt program.

> [!IMPORTANT]
> Medan migreringen har ett beroende i förhållande till Power BI Embedded, så finns det inget beroende gentemot Power BI för ditt programs användare när en **inbäddningstoken** används. De behöver inte registrera sig för Power BI om du vill visa ditt programs inbäddade innehåll. Du kan använda den här inbäddningsmetoden för Embedded-användare som inte använder Power BI.

![Bädda in flöde](media/migrate-from-powerbi-embedded/powerbi-embed-flow.png)

Innan du börjar migrera till nya Power BI Embedded kan du titta på en snabb genomgång som beskriver hur du konfigurerar den nya Power BI Embedded-miljön med hjälp av [konfigurationsverktyget för inbäddning](https://aka.ms/embedsetup).

Välj den lösning som passar dig:
* Lösningen **Embed for your customers** (Bädda in för dina kunder) – om du är intresserad av en [apps egna data](https://aka.ms/embedsetup/AppOwnsData). [Inbäddning för dina kunder](embedding.md#embedding-for-your-customers) ger dig möjlighet att bädda in instrumentpaneler och rapporter för användare som inte har något Power BI-konto. 

* Lösningen **Embed for your organization** (Bädda in för din organisation) – om du är intresserad av en [användares egna data](https://aka.ms/embedsetup/UserOwnsData). [Inbäddning för din organisation](embedding.md#embedding-for-your-organization) låter dig utöka Power BI-tjänsten.

## <a name="prepare-for-the-migration"></a>Förbereda för migrering

Det finns några saker du behöver göra för att förbereda migreringen från Power BI-arbetsytesamling till Power BI Embedded. Du behöver en tillgänglig klient och en användare med en Power BI Pro-licens.

1. Kontrollera att du har åtkomst till en Azure Active Directory (Azure AD)-klient.

    Du måste fastställa vilken klientkonfiguration som ska användas.

   * Vill du använda din befintliga Power BI-företagsklient?
   * Vill du använda en separat klient för ditt program?
   * Vill du använda en separat klient för varje kund?

     Mer information om hur du skapar en ny klient för ditt program eller för varje kund finns i [Skapa en Azure Active Directory-klient](create-an-azure-active-directory-tenant.md) eller [Skaffa en Azure Active Directory-klient](https://docs.microsoft.com/azure/active-directory/develop/active-directory-howto-tenant).
2. Skapa en användare i den nya klienten som ska fungera som ditt programs ”huvudkonto”. Detta konto måste registreras för Power BI och måste ha tilldelats en Power BI Pro-licens.

## <a name="accounts-within-azure-ad"></a>Konton i Azure AD

Följande konton måste finnas i din klient.

> [!NOTE]
> Dessa konton måste ha Power BI Pro-licenser för att kunna använda arbetsytor.

1. En klientadministratörsanvändare.

    Den här användaren bör vara medlem i alla arbetsytor som har skapats för inbäddning.

2. Konton för analytiker som skapar innehåll.

    Dessa användare ska tilldelas till arbetsytor efter behov.

3. Ett programs *huvudanvändarkonto* eller Embedded-konto.

    Programmets serverdel sparar kontots autentiseringsuppgifter och använder dem för att skaffa en Azure AD-token som kan användas med Power BI REST-API:er. Det här kontot används för att generera programmets inbäddningstoken. Kontot måste också vara administratör för de arbetsytor som skapats för inbäddning.

> [!NOTE]
> Detta är helt enkelt ett vanligt användarkonto i din organisation som används i inbäddningssyfte.

## <a name="app-registration-and-permissions"></a>Appregistrering och behörigheter

Du måste registrera ett program i Azure AD och bevilja det vissa behörigheter.

### <a name="register-an-application"></a>Registrera ett program

Du måste registrera ditt program med Azure AD för att kunna göra REST API-anrop. Detta inkluderar att gå till Azure Portal så att du kan göra ytterligare konfiguration utöver Power BI-appens registreringssida. Mer information finns i [Registrera en Azure AD-app för att bädda in Power BI-innehåll](register-app.md).

Du bör registrera programmet med programmets **huvudkonto**.

## <a name="create-workspaces-required"></a>Skapa arbetsytor (obligatoriskt)

Du kan använda arbetsytor för att få bättre isolering om programmet betjänar flera kunder. Instrumentpaneler och rapporter skulle isoleras mellan kunderna. Du kan sedan använda ett Power BI-konto per arbetsyta och därmed isolera användningen av programmet ytterligare mellan dina kunder.

> [!IMPORTANT]
> Du kan inte använda en personlig arbetsyta för att utnyttja inbäddningsmöjligheten för användare som inte är Power BI-användare.

Du behöver en användare som har en Pro-licens för att kunna skapa en arbetsyta i Power BI. Den Power BI-användare som skapar arbetsytan blir som standard arbetsytans administratör.

> [!NOTE]
> Programmets *huvudkonto* måste vara arbetsytans administratör.

## <a name="content-migration"></a>Innehållsmigrering

Migrering av innehållet från dina samlingar med arbetsytor till Power BI Embedded kan ske parallellt med din aktuella lösning och kräver inget driftstopp.

Det finns ett tillgängligt **migreringsverktyg** som du kan använda för att kopiera innehåll från Power BI-arbetsytesamling till Power BI Embedded. Särskilt om du har mycket innehåll. Mer information finns i [Migreringsverktyget för Power BI Embedded](migrate-tool.md).

Innehållsmigreringen förlitar sig i huvudsak på två API:er.

1. Hämta PBIX – detta API kan hämta PBIX-filer som har överförts till Power BI efter oktober 2016.
2. Importera PBIX – detta API överför valfri PBIX till Power BI.

Relaterade kodfragment beskrivs i [Kodfragment för migrering av innehåll från Power BI-arbetsytesamling](migrate-code-snippets.md).

### <a name="report-types"></a>Rapporttyper

Det finns flera typer av rapporter, som var och en kräver ett något annorlunda migreringsflöde.

#### <a name="cached-dataset--report"></a>Cachelagrad datauppsättning och rapport

Med cachelagrade datauppsättningar avses PBIX-filer som har importerade data istället för en live-anslutning eller DirectQuery-anslutning.

**Flow**

1. Anropshämta PBIX API från PaaS-arbetsytan.
2. Spara PBIX.
3. Anropsimportera PBIX till SaaS-arbetsytan.

#### <a name="directquery-dataset--report"></a>DirectQuery-datauppsättning och -rapport

**Flow**

1. Anropa GET https://api.powerbi.com/v1.0/collections/{collection_id}/workspaces/{wid}/datasets/{dataset_id}/Default.GetBoundGatewayDataSources och spara anslutningssträngen som tagits emot.
2. Anropshämta PBIX API från PaaS-arbetsytan.
3. Spara PBIX.
4. Anropsimportera PBIX till SaaS-arbetsytan.
5. Uppdatera anslutningssträngen genom att anropa – POST  https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.SetAllConnections
6. Hämta GW och datakällans identifierare genom att anropa – GET https://api.powerbi.com/v1.0/myorg/datasets/{dataset_id}/Default.GetBoundGatewayDataSources
7. Uppdatera användarens autentiseringsuppgifter genom att anropa – PATCH https://api.powerbi.com/v1.0/myorg/gateways/{gateway_id}/datasources/{datasource_id}

#### <a name="old-dataset--reports"></a>Gammal datauppsättning och rapporter

Dessa är datauppsättningar/rapporter som skapats före oktober 2016. PBIX-hämtningen stöder inte PBIX:er som hämtades före oktober 2016

**Flow**

1. Hämta PBIX från din utvecklingsmiljö (din interna källkontroll).
2. Anropsimportera PBIX till SaaS-arbetsytan.

#### <a name="push-dataset--report"></a>Push-överför datauppsättning och rapport

PBIX-hämtning stöder inte *Push API*-datauppsättningar. API-datauppsättningsdata för push-överföring API kan inte porteras från PaaS till SaaS.

**Flow**

1. Anropa API:et för att skapa datauppsättning med datauppsättnings-JSON för att skapa datauppsättningar på SaaS-arbetsytan.
2. Återskapa rapporten för den skapade datauppsättningen *.

Du kan använda vissa lösningar för att migrera push-API-rapporten från PaaS till SaaS genom att göra på följande sätt.

1. Ladda upp några dummy-PBIX:er till PaaS-arbetsytan.
2. Klona push-API-rapporten och bind den till dummy-PBIX:en från steg 1.
3. Hämta push-API-rapporten med dummy-PBIX:en.
4. Överför dummy-PBIX:en till SaaS-arbetsytan.
5. Skapa push-datauppsättning på din SaaS-arbetsyta.
6. Bind om rapporten till push-API-datauppsättningen.

## <a name="create-and-upload-new-reports"></a>Skapa och ladda upp nya rapporter

Utöver det innehåll du har migrerat från Power BI Workspace Collection kan du skapa rapporter och datamängder som använder Power BI Desktop och sedan publicera rapporterna på en arbetsyta. Användaren som publicerar rapporterna behöver en Power BI Pro-licens för att publicera till en arbetsyta.

## <a name="rebuild-your-application"></a>Återskapa ditt program

1. Du måste ändra ditt program om du vill kunna använda Power BI REST-API:erna och rapportplatsen på powerbi.com.
2. Återskapa din AuthN/AuthZ-autentisering med hjälp av ditt programs *huvudkonto*. Du kan utnyttja möjligheten att använda en [inbäddningstoken](https://docs.microsoft.com/rest/api/power-bi/embedtoken) så att användaren kan agera som ombud för andra användare.
3. Bädda in dina rapporter från powerbi.com i ditt program.

## <a name="map-your-users-to-a-power-bi-user"></a>Mappa dina användare till en Power BI-användare

I ditt program mappar du användare som du hanterar i programmet till ett Power BI- *huvudkontos* autentiseringsuppgifter. Autentiseringsuppgifterna för det här Power BI-*huvudkontot* lagras i ditt program och används för att skapa inbäddningstoken.

## <a name="what-to-do-when-you-are-ready-for-production"></a>Vad du ska göra när det är dags för produktion

När du är redo att gå vidare till produktion måste du göra följande.

* Om du använder en separat klientorganisation för utveckling så måste du kontrollera att dina arbetsytor, instrumentpaneler och rapporter är tillgängliga i produktionsmiljön. Du måste också kontrollera att du har skapat programmet i Azure AD för din produktionsklient och tilldelat rätt appbehörigheter, så som beskrivs i steg 1.
* Köp en kapacitet som passar dina behov. För att bättre förstå den mängd och typ av kapacitet du behöver, se [white paper om kapacitetsplanering för analys i Power BI Embedded](https://aka.ms/pbiewhitepaper). Du kan [köpa kapacitet](https://portal.azure.com/#create/Microsoft.PowerBIDedicated) i Azure.
* Redigera arbetsytan och tilldela den till en Premium-kapacitet under Avancerat.

    ![Premiumkapacitet](media/migrate-from-powerbi-embedded/powerbi-embedded-premium-capacity02.png)

* Distribuera ditt uppdaterade program till produktion och börja bädda in rapporter från Power BI Embedded.

## <a name="after-migration"></a>Efter migreringen

Rensa i Azure.

* Ta bort alla arbetsytor från den distribuerade lösningen i Azure Embedded för Power BI-arbetsytesamling.
* Ta bort eventuella arbetsytesamlingar från Azure.

## <a name="next-steps"></a>Nästa steg

[Bädda in med Power BI](embedding.md)  
[Migreringsverktyg för Power BI-arbetsytesamling](migrate-tool.md)  
[Kodfragment för migrering av innehåll från Power BI-arbetsytesamling](migrate-code-snippets.md)  
[Så här bäddar du in dina Power BI-instrumentpaneler, -rapporter och -paneler](embed-sample-for-your-organization.md)  
[Power BI Premium – vad är det?](../../service-premium-what-is.md)  
[JavaScript API Git Repo](https://github.com/Microsoft/PowerBI-JavaScript)  
[Power BI C# Git Repo](https://github.com/Microsoft/PowerBI-CSharp)  
[JavaScript-inbäddningsexempel](https://microsoft.github.io/PowerBI-JavaScript/demo/)  
[White paper om kapacitetsplanering för analys i arbetsytesamling](https://aka.ms/pbiewhitepaper)  
[Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
