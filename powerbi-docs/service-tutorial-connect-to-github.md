---
title: 'Självstudie: Ansluta till en GitHub-lagringsplats med Power BI'
description: I den här självstudien ska du ansluta till verkliga data i GitHub-tjänsten med Power BI, så skapar Power BI automatiskt instrumentpaneler och rapporter.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 04/19/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 3aeb1fc16ae200399125a2366a8993d45aad34c4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578636"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Självstudie: Ansluta till en GitHub-lagringsplats med Power BI
I den här självstudien ska du ansluta till verkliga data i GitHub-tjänsten med Power BI, så skapar Power BI automatiskt instrumentpaneler och rapporter. Du ansluter till Power BI content offentliga lagringsplats (kallas även en *repo*) och se svar på frågor som: Hur många personer bidrar till det offentliga Power BI-innehållet? Vem bidrar med mest innehåll? Vilken dag i veckan har flest bidrag? Och andra frågor. 

![GitHub-rapporten i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

I den här självstudien går du igenom följande steg:

> [!div class="checklist"]
> * Registrera dig för ett GitHub-konto om du inte redan har ett 
> * Logga in på ditt Power BI-konto, eller registrera dig om du inte redan har ett konto
> * Öppna Power BI-tjänsten
> * Leta upp GitHub-appen
> * Ange informationen för den offentliga GitHub-lagringsplatsen för Power BI
> * Visa instrumentpanelen och rapporten med GitHub-data
> * Rensa resurser genom att ta bort appen

Om du inte har registrerat dig för Power BI [registrerar du dig för en kostnadsfri utvärderingsversion](https://app.powerbi.com/signupredirect?pbi_source=web) innan du börjar.

## <a name="prerequisites"></a>Förutsättningar

I den här kursen behöver du ett GitHub-konto om du inte redan har ett. 

- Registrera dig för en [GitHub-konto](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Så här ansluter du
1. Logga in till Power BI-tjänsten (https://app.powerbi.com). 
2. Välj **Appar** i det vänstra navigeringsfönstret och välj sedan **Hämta appar**.
   
   ![Hämta appar i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Välj **appar**, typ **GitHub** i sökrutan > **Hämta nu**.
   
   ![Hämta GitHub i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. I **installera den här Power BI-appen?** Välj **installera**.
5. I **din nya app är klar**väljer **gå till app**.
6. I **Kom igång med din nya app**väljer **Anslut data**.

    ![Kom igång med din nya app](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

7. Ange lagringsplatsens namn och ägare. URL:en för den här lagringsplatsen är https://github.com/MicrosoftDocs/powerbi-docs. **Lagringsplatsägare** är alltså **MicrosoftDocs** och **Lagringsplats** är **powerbi-docs**. 
   
    ![GitHub-lagringsplats i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Ange autentiseringsuppgifterna för GitHub som du skapade. Power BI kan hoppa över det här steget om du redan är inloggad i GitHub i din webbläsare. 

6. För **autentiseringsmetod**, hålla **oAuth2** valda \> **logga In**.

7. Följ autentiseringsskärmarna i GitHub. Ge Power BI behörighet till GitHub-data.
   
   Nu kan Power BI ansluta till GitHub och till informationen.  Data uppdateras en gång om dagen.

8. När Power BI har importerat data, kan du se innehållet i den nya GitHub-arbetsytan. 
9. Välj pilen bredvid namnet på arbetsytan i det vänstra navigeringsfältet. Du ser arbetsytan som innehåller en instrumentpanel och en rapport. 

    ![App i det vänstra navigeringsfönstret](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Välj ellipsen (...) bredvid instrumentpanelens namn > **Byt namn på** > typ **GitHub-instrumentpanel**.
 
    ![GitHub-panel i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Minimera vänster navigeringsfönster så att du får mer plats genom att välja ikonen för global navigering.

    ![Ikon för global navigering](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Välj din GitHub-instrumentpanelen.
    
    GitHub-instrumentpanelen innehåller realtidsdata, så de värden som du ser kan vara olika.

    ![GitHub-instrumentpanel i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Ställ en fråga

1. Placera markören i **Ställ en fråga om dina data**. Power BI erbjuder **frågor för att komma igång**. 

1. Välj **hur många användare är det**.
 
    ![Hur många användare är det](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Mellan **hur många** och **användare finns det**, typ **pull-begäranden per**. 

     Powerbi skapar ett stapeldiagram som visar hur många pull-begäranden per person.

    ![Hur många pull-begäranden per användare är det](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Välj PIN-koden och Fäst det på instrumentpanelen, sedan **avsluta frågor och svar**.

## <a name="view-the-github-report"></a>Visa GitHub-rapporten 

1. I GitHub-instrumentpanelen väljer du stapeldiagrammet **Pull-begäranden per månad** att öppna den tillhörande rapporten.

    ![Hämtningsbegäranden per månad stående stapeldiagram](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Välj ett användarnamn i den **Totalt antal hämtningsbegäranden av användaren** diagram. I det här exemplet vi kan se de flesta av timmarna som fanns i februari.

    ![Markering i GitHub-rapport i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Visa nästa sida i rapporten genom att välja fliken **Punch Card** (Hålkort). 
 
    ![Punch Card (Hålkort) i GitHub-rapport i Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Uppenbarligen tisdagen klockan 15 är mest vanliga tid och veckodag för *förbinder*, när användare söker i sitt arbete.

## <a name="clean-up-resources"></a>Rensa resurser

Nu när du är klar med självstudien kan du ta bort GitHub-appen. 

1. Välj **Appar** i det vänstra navigeringsfältet.
2. Hovra över GitHub-ikonen och välj papperskorgen (**Ta bort**).

    ![Ta bort GitHub-appen](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Nästa steg

I den här självstudien har du anslutit till en offentlig GitHub-lagringsplats och hämtat data, som konverterades till en instrumentpanel och en rapport i Power BI. Du har besvarat några frågor om informationen genom att utforska instrumentpanelen och rapporten. Nu kan du läsa mer om hur du ansluter till andra tjänster, till exempel Salesforce, Microsoft Dynamics och Google Analytics. 
 
> [!div class="nextstepaction"]
> [Ansluta till onlinetjänster som du använder](service-connect-to-services.md)


