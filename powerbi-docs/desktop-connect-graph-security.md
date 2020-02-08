---
title: Anslut till Säkerhets-API för Microsoft Graph i Power BI Desktop
description: Anslut enkelt till Säkerhets-API för Microsoft Graph i Power BI Desktop
author: preetikr
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: preetikr
LocalizationGroup: Connect to data
ms.openlocfilehash: ef8e874c1f1a47d65845b87dccd441746651a68b
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "74999800"
---
# <a name="connect-to-the-microsoft-graph-security-api-in-power-bi-desktop"></a>Anslut till Säkerhets-API för Microsoft Graph i Power BI Desktop

Använd Microsoft Graph Security-anslutningen i Power BI Desktop för att ansluta till [Säkerhets-API för Microsoft Graph](https://aka.ms/graphsecuritydocs). Du kan sedan skapa instrumentpaneler och rapporter som ger dig insikt i dina säkerhetsrelaterade [aviseringar](https://docs.microsoft.com/graph/api/resources/alert?view=graph-rest-1.0) och [säkerhetspoäng](https://docs.microsoft.com/graph/api/resources/securescores?view=graph-rest-beta).

Säkerhets-API för Microsoft Graph ansluter [flera säkerhetslösningar](https://aka.ms/graphsecurityalerts) från Microsoft och dess ekosystempartners för att underlätta korrelation av aviseringar. Den här kombinationen ger tillgång till omfattande kontextinformation och förenklar automatisering. Det gör det möjligt för organisationer att snabbt få insikter och agera i flera säkerhetsprodukter, samtidigt som det minskar kostnaden och komplexiteten.

## <a name="prerequisites-to-use-the-microsoft-graph-security-connector"></a>Krav för att använda anslutningsappen för Microsoft Graph-säkerhet

Om du vill använda anslutningsappen för Microsoft Graph-säkerhet måste du *uttryckligen* få användarens tillstånd av klientadministratören för Azure Active Directory (AD Azure). Se [autentiseringskrav för Microsoft Graph Security](https://aka.ms/graphsecurityauth).
Medgivande kräver anslutningsappens program-ID och namn, som har citerats här och är tillgängliga i [Azure-portalen](https://portal.azure.com):

| Egenskap | Värde |
|----------|-------|
| **Programnamn** | `MicrosoftGraphSecurityPowerBIConnector` |
| **Program-ID** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
|||

Din Azure AD-innehavaradministratör kan använda någon av de här metoderna för att ge sitt medgivande för anslutningsappen:

* [Ge medgivande för Azure AD-program](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent)

* Svara på en begäran som logikappen skickar under sin första genomgång av [programtillåtelsen](https://docs.microsoft.com/azure/active-directory/develop/application-consent-experience)
   
Det användarkonto som används för att logga in till anslutningsappen för Microsoft Graph-säkerhet måste vara tilldelad rollen Säkerhetsläsare i Azure AD, **om** användaren inte är medlem i rollen *Säkerhetsadministratör*. Se avsnittet om att [tilldela Azure AD-roller till användare](https://docs.microsoft.com/graph/security-authorization#assign-azure-ad-roles-to-users).

## <a name="using-the-microsoft-graph-security-connector"></a>Med anslutningsappen för Microsoft Graph-säkerhet

Följ stegen nedan för att använda anslutningsappen:

1. Välj **Hämta data** > **Mer** från menyfliksområdet **Start** i Power BI Desktop.
2. Välj **Onlinetjänster** från kategorilistan till vänster i fönstret.
3. Välj **Microsoft Graph Security (Beta)** .

    ![Dialogrutan Hämta data](media/desktop-connect-graph-security/GetData.PNG)
    
4. I fönstret **Microsoft Graph Security** väljer du vilken Microsoft Graph API-version du vill skicka frågor till: **v1.0** eller **beta**.

    ![Dialogrutan Välj version](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Logga in på ditt Azure Active Directory-konto vid uppmaning. Det här kontot måste ha rollen *Säkerhetsläsare* eller *Säkerhetsadministratör*, som vi nämnde i föregående avsnitt.

    ![Logga in](media/desktop-connect-graph-security/SignIn.PNG) 
    
6. Om du är innehavaradministratör *och* om du ännu inte har gett ditt medgivande till Power BI-anslutningsappen för Microsoft Graph-säkerhet visas följande dialogruta. Välj **Samtyck åt din organisation**.

    ![Dialogrutan Administratörsmedgivande](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. När du har loggat in ser du följande dialogruta som indikerar att du har autentiserats. Välj **Anslut**.

    ![Dialogrutan ”Du är inloggad”](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. När du har anslutit visar fönstret **Navigatör** aviseringarna, säkerhetspoängen och andra entiteter som är tillgängliga i [Säkerhets-API för Microsoft Graph](https://aka.ms/graphsecuritydocs) för den version som du valde i steg 4. Välj en eller flera entiteter att importera och använda i Power BI Desktop. Välj **Läsa in** för att hämta resultatvyn som visas efter steg 9.

    ![Navigeringsdialogruta](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Om du vill använda en avancerad fråga med Säkerhets-API för Microsoft Graph väljer du **Specify custom Microsoft Graph Security URL to filter results** (Ange anpassad URL för Microsoft Graph-säkerhet för att filtrera resultat). Använd den här funktionen för att skapa en [OData.Feed](https://docs.microsoft.com/power-bi/desktop-connect-odata)-fråga till Säkerhets-API för Microsoft Graph med den behörighet som krävs.

   I följande exempel används `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'` *serviceUri*. Om du vill se hur du skapar frågor för att filtrera, sortera eller hämta de senaste resultaten kan du läsa [OData system query options](https://docs.microsoft.com/graph/query-parameters) (OData-systemfrågealternativ).

   ![OdataFeed-exempel](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   När du väljer **Anropa** anropar **OData.Feed**-funktionen API:et, som öppnar frågeredigeraren. Du kan filtrera och begränsa uppsättningen av data som du vill använda. Läs sedan in dina data i Power BI Desktop.

Här är resultatfönstret för Microsoft Graph Security-entiteter som vi frågade efter:

   ![Exempel på frågefönster](media/desktop-connect-graph-security/Result.PNG)
    

Nu är du redo att använda den importerade informationen från Microsoft Graph Security-anslutningsappen i Power BI Desktop. Du kan skapa grafik och rapporter. Eller så kan du interagera med andra data som du importerar från Excel-arbetsböcker, databaser eller andra datakällor.

## <a name="next-steps"></a>Nästa steg
* Kolla in Power BI-exempel och mallar som använder den här anslutningsappen på [Power BI-exempel i GitHub för Microsoft Graph-säkerhet](https://aka.ms/graphsecuritypowerbiconnectorsamples).

* Användarscenarier och ytterligare information finns i [blogginlägget om Power BI-anslutningsappen för Microsoft Graph-säkerhet](https://aka.ms/graphsecuritypowerbiconnectorblogpost).

* Du kan ansluta till en mängd olika typer av data Power BI Desktop. Mer information finns i följande källor:

    * [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
    * [Datakällor i Power BI Desktop](desktop-data-sources.md)
    * [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
    * [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)
    * [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
