---
title: Ansluta till GitHub med Power BI
description: GitHub för Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: b0f2bd53f1d8b82b70072446723c2ca3723eeacd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65608424"
---
# <a name="connect-to-github-with-power-bi"></a>Ansluta till GitHub med Power BI
Den här artikeln beskriver hur du hämtar data från ditt GitHub-konto med en mall för Power BI-appen. Appen mallen genererar en arbetsyta med en instrumentpanel, en rapportuppsättning och en datauppsättning att utforska dina GitHub-data. GitHub-appen för Power BI visar insikter om GitHub-databasen, även kallat lagringsplatsen med data kring bidrag, ärenden, pull-begäranden och aktiva användare.

När du har installerat appen mall, kan du ändra instrumentpanelen och rapporterna. Du kan sedan distribuera den som en app till kollegor i din organisation.

Ansluta till den [GitHub mallapp](https://app.powerbi.com/getdata/services/github) eller Läs mer om den [GitHub-integreringen](https://powerbi.microsoft.com/integrations/github) med Power BI.

Du kan också prova den [GitHub självstudien](service-tutorial-connect-to-github.md). Den installerar verkliga GitHub-data om den offentliga lagringsplatsen för Power BI-dokumentationen.

>[!NOTE]
>Mall-appen kräver GitHub-konto att ha åtkomst till lagringsplatsen. Mer information om kraven finns nedan.

## <a name="how-to-connect"></a>Så här ansluter du
[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]
   
3. Välj **GitHub** \> **Hämta nu**.
4. I **installera den här Power BI-appen?** Välj **installera**.
4. I den **appar** väljer den **GitHub** panelen.

    ![GitHub-panel i Power BI](media/service-connect-to-github/power-bi-github-tile.png)

6. I **Kom igång med din nya app**väljer **Anslut data**.

    ![Kom igång med din nya app](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

5. Ange lagringsplatsens namn och ägare. Se information om att [hitta parametrarna](#FindingParams) nedan.
   
    ![GitHub-lagringsplats i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Ange dina autentiseringsuppgifter för GitHub (det här steget kan hoppas över om du redan har loggat in med din webbläsare). 
6. Som **autentiseringsmetod** väljer du **oAuth2** \> **Logga in**. 
7. Följ autentiseringsskärmarna i GitHub. Ge GitHub för Power BI-mall appen behörighet till GitHub-data.
   
   ![Auktorisera GitHub för Power BI](media/service-connect-to-github/github_authorize.png)
   
    Powerbi ansluter till GitHub och dina data.  Data uppdateras en gång om dagen. När Power BI har importerat data, kan du se innehållet i den nya GitHub-arbetsytan.

## <a name="modify-and-distribute-your-app"></a>Ändra och distribuera din app

Du har installerat appen GitHub mall. Det innebär att du har också skapat GitHub app-arbetsytan. I arbetsytan kan du ändra rapporten och instrumentpanelen och sedan distribuera den som en *app* till kollegor i din organisation. 

1. Välj pilen bredvid namnet på arbetsytan i det vänstra navigeringsfältet. Du ser arbetsytan som innehåller en instrumentpanel och en rapport.

    ![App i det vänstra navigeringsfönstret](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

8. Välj den nya [GitHub-instrumentpanel](https://powerbi.microsoft.com/integrations/github).    
    ![GitHub-instrumentpanel i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

3. Om du vill visa hela innehållet i den nya GitHub-arbetsytan i det vänstra navigeringsfältet, väljer **arbetsytor** > **GitHub**.
 
   ![GitHub-arbetsyta i det vänstra navigeringsfönstret](media/service-connect-to-github/power-bi-github-left-nav.png)

    Den här vyn är listan med innehåll för arbetsytan. I det övre högra hörnet ser du **uppdatera app**. När du är redo att distribuera appen till dina kollegor, är det där du börjar. 

    ![GitHub innehållslistan](media/service-connect-to-github/power-bi-github-content-list.png)

2. Välj **rapporter** och **datauppsättningar** så att andra element på arbetsytan.

    Läs mer om [distribuera appar](service-create-distribute-apps.md) till dina kollegor.

## <a name="whats-included-in-the-app"></a>Vad ingår i appen
Följande data finns tillgängliga från GitHub i Power BI:     

| Tabellnamn | Beskrivning |
| --- | --- |
| Bidrag |I bidragstabellen finns i totalt antal tillägg, borttagningar och incheckningar som har godkänts av deltagaren, aggregerade per vecka. De 100 främsta deltagarna ingår. |
| Problem |En lista med alla problem för den valda lagringsplatsen med beräkningar som summa och genomsnittlig tid för att stänga ett problem, totalt antal öppna problem och totalt antal stängda problem. Den här tabellen är tom om det inte finns några problem med lagringsplatsen. |
| Pull-begäranden |Den här tabellen innehåller alla pull-begäranden för lagringsplatsen samt vem som hämtade begäran. Den innehåller också beräkningar för hur många öppna, stängda och totala pull-begäranden, hur lång tid det tog för att hämta begärandena och hur lång tid tog genomsnittlig pull-begäran. Den här tabellen är tom om det inte finns några problem med lagringsplatsen. |
| Användare |Den här tabellen innehåller en lista med GitHub-användare eller deltagare som har bidragit, arkiverat problem eller löst Pull-begäranden för den valda lagringsplatsen. |
| Milstolpar |Den innehåller alla milstolpar för valda lagringsplatsen. |
| DateTable |Den här tabellen innehåller datum från idag och i år tidigare så att du kan analysera dina GitHub-data efter datum. |
| ContributionPunchCard |Den här tabellen kan användas som ett stanskort för bidrag på den valda lagringsplatsen. Den visar incheckningar per veckodag och timme. Tabellen är inte ansluten till andra tabeller i modellen. |
| RepoDetails |Den här tabellen innehåller information om den valda lagringsplatsen. |

## <a name="system-requirements"></a>Systemkrav
* GitHub-kontot som har åtkomst till lagringsplatsen.  
* Behörighet som beviljats till Power BI för GitHub-appen vid första inloggningen. Se nedan för information om att återkalla åtkomst.  
* Hur många tillräckliga API-anrop som finns tillgängliga för att hämta och uppdatera data.  

### <a name="de-authorize-power-bi"></a>Ta bort auktoriseringen för Power BI
Om du vill ta bort auktoriseringen för Power BI från att vara ansluten till GitHub-lagringsplatsen, kan du återkalla åtkomsten i GitHub. Se den här [GitHub-hjälp](https://help.github.com/articles/keeping-your-ssh-keys-and-application-access-tokens-safe/#reviewing-your-authorized-applications-oauth) avsnittet för information.

<a name="FindingParams"></a>
## <a name="finding-parameters"></a>Hitta parametrar
Du kan se ägare och lagringsplats genom att titta på lagringsplatsen i själva GitHub:

![Lagringsplatsen namn och ägare](media/service-connect-to-github/github_ownerrepo.png)

Den första delen ”Azure” är ägare och den andra delen ”azure-sdk-for-php” är själva lagringsplatsen.  Du ser samma två objekt i URL-adressen för lagringsplatsen:

    <https://github.com/Azure/azure-sdk-for-php> .

## <a name="troubleshooting"></a>Felsökning
Om det behövs kan du verifiera dina autentiseringsuppgifter för GitHub.  

1. Gå till GitHub-webbplatsen i ett nytt webbläsarfönster och logga in på GitHub. Du ser att du är inloggad i det övre högra hörnet på GitHub-webbplatsen.    
2. I GitHub går du till webbadressen för den lagringsplats som du vill ha åtkomst till i Power BI. Till exempel: https://github.com/dotnet/corefx.  
3. Tillbaka i Power BI försöker du ansluta till GitHub. I dialogrutan Konfigurera GitHub använder du namnen på lagringsplatsen och lagringsplatsens ägare för samma lagringsplats.  

## <a name="next-steps"></a>Nästa steg

* [Självstudier: Ansluta till en GitHub-lagringsplats med Power BI](service-tutorial-connect-to-github.md)
* [Skapa nya arbetsytor i Power BI](service-create-the-new-workspaces.md)
* [Installera och använda appar i Power BI](consumer/end-user-apps.md)
* [Ansluta till Power BI-appar för externa tjänster](service-connect-to-services.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

