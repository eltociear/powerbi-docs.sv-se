---
title: Skapa nya arbetsytor – Power BI
description: Lär dig hur du skapar nya arbetsytor, samlingar av instrumentpaneler, rapporter och sidnumrerade rapporter som skapats för att leverera nyckelvärden för din organisation.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d0c0781ea5d3864f1cf3627cd42d53cca632102d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61142067"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Skapa nya arbetsytor i Power BI

Powerbi presenterar en ny arbetsyta-upplevelse. Arbetsytor är fortfarande där du samarbeta med kollegor för att skapa samlingar av instrumentpaneler, rapporter och sidnumrerade rapporter. Sedan kan du paketera den samlingen till en *app* och distribuera det till hela organisationen eller till specifika personer eller grupper. 

Här är vad som är annorlunda. I de nya arbetsytorna kan du:

- Tilldela arbetsyteroller till användargrupper: säkerhetsgrupper, distributionslistor, Office 365-grupper och enskilda användare.
- Skapa en arbetsyta i Power BI utan att skapa en Office 365-grupp.
- Använda mer detaljerade arbetsyteroller för mer flexibel hantering av behörigheter på en arbetsyta.

> [!NOTE]
> Om du vill framtvinga säkerhet på radnivå (RLS) för Power BI Pro-användare surfning innehållet i en arbetsyta måste fortsätta att använda [klassiska arbetsytor](service-create-workspaces.md). Välj den **medlemmar kan bara visa Power BI-innehåll** alternativet. Du kan också publicera en Power BI-app till de användarna eller Använd delning för att distribuera innehåll. Rollen kommande visningsprogrammet kan det här scenariot i framtiden i nya arbetsytor för arbetsyta-upplevelse.

Mer bakgrundsinformation finns i den [nya arbetsytor](service-new-workspaces.md) artikeln.

## <a name="create-one-of-the-new-app-workspaces"></a>Skapa en av de nya apparbetsytorna

1. Börja med att skapa apparbetsytan. Välj **Arbetsytor** > **Skapa apparbetsyta**.
   
     ![Skapa en apparbetsyta](media/service-create-the-new-workspaces/power-bi-create-app-workspace.png)

2. Du automatiskt skapar en uppgraderad arbetsyta, såvida inte om du väljer att **återgå till klassisk**.
   
     ![Den nya arbetsytan upplevelsen](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Om du väljer **återgå till klassisk**, skapar du en arbetsyta som baseras på en Office 365-grupp. Använd det här alternativet om du behöver den **medlemmar kan bara visa Power BI-innehåll** alternativ för att tvinga säkerhet på radnivå (RLS) för arbetsytemedlemmar.

2. Ge arbetsytan ett namn. Om namnet inte finns kan du redigera det för att få fram ett unikt namn.
   
     Appen för arbetsytan har samma namn och ikon som arbetsytan.
   
1. Här följer några valfria objekt som du kan ange för din arbetsyta:

    Ladda upp en **arbetsytan bild**. Filer kan vara .png eller .jpg-format. Filstorleken måste vara mindre än 45 KB.
    
    [Lägg till en **kontaktlista**](#workspace-contact-list). Som standard är administratörer för arbetsytan kontakter. 
    
    [Ange en **arbetsytan OneDrive** ](#workspace-onedrive) genom att skriva endast namnet på en befintlig Office 365-grupp, inte URL: en. Den här arbetsytan kan nu använda Office 365 gruppens fillagringsplats. 

    ![Ange en plats i OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    Tilldela arbetsytan till en **dedikerade kapacitet**på den **Premium** fliken väljer **dedikerade kapacitet**.
     
    ![Dedikerad kapacitet](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Välj **Spara**.

    Power BI skapar arbetsytan och öppnar den. Den visas i listan med arbetsytor som du är medlem i. 

## <a name="workspace-contact-list"></a>Arbetsytan kontaktlista

Den nya arbetsyta kontaktlistan kan du ange vilka användare informeras om problem uppstår i arbetsytan. Som standard angetts en användare eller grupp som som en arbetsyta administratören meddelas, men du kan anpassa listan. Användare eller grupper som visas i listan visas i användargränssnittet (UI) för att användare kan få hjälp relaterade till arbetsytan.

1. Den nya **kontaktlista** i något av två sätt:

    I den **skapa en arbetsyta** fönstret när du skapar den.

    I det vänstra navigeringsfönstret väljer du pilen bredvid **arbetsytor**, Välj ellipsen (...) bredvid arbetsytans namn > **arbetsyteinställningarna**. Den **inställningar** öppnas fönstret.

    ![Inställningar för arbetsyta](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Under **Avancerat** > **kontaktlista**, acceptera standardinställningarna, **arbetsytesadministratörer**, eller Lägg till en egen lista över **specifika användare eller grupper**. 
3. Välj **Spara**.

## <a name="workspace-onedrive"></a>Workspace OneDrive

Arbetsytan OneDrive-funktionen kan du konfigurera en Office 365-grupp vars SharePoint-dokumentbibliotek file storage är tillgängligt för arbetsyteanvändare. Du skapa först grupp utanför Power BI. 

Powerbi Synkronisera inte behörigheterna för användare eller grupper som är konfigurerade med arbetsyteåtkomst med Office 365-gruppmedlemskap. Det bästa sättet är att ge samma Office 365-grupp, vars fillagring som du konfigurerar i den här för Office 365-inställningsgruppen [åtkomst till arbetsytan](#give-access-to-your-workspace). Sedan hantera åtkomst till arbetsytan genom att hantera medlemskapet för Office 365-grupp. 

1. Den nya **arbetsytan OneDrive** i något av två sätt:

    I den **skapa en arbetsyta** fönstret när du skapar den.

    I det vänstra navigeringsfönstret väljer du pilen bredvid **arbetsytor**, Välj ellipsen (...) bredvid arbetsytans namn > **arbetsyteinställningarna**. Den **inställningar** öppnas fönstret.

    ![Inställningar för arbetsyta](media/service-create-the-new-workspaces/power-bi-workspace-settings.png)

2. Under **Avancerat** > **arbetsytan OneDrive**, skriver du namnet på Office 365-grupp som du skapade tidigare. Powerbi hämtar automatiskt OneDrive för gruppen.

    ![Ange en plats i OneDrive](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Välj **Spara**.

### <a name="access-the-workspace-onedrive-location"></a>Öppna arbetsytan OneDrive-plats

När du har konfigurerat den OneDrive-platsen kan gå du direkt till enheten från ett par olika ställen i arbetsytan:

- Välj **arbetsytor** > *Arbetsytenamn* > de tre punkterna ( **...** ) menyn > **filer**. 

    ![Platsen för arbetsytan](media/service-new-workspaces/power-bi-new-workspace-files.png)

- Välj ellipsen ( **...** )-menyn i det övre högra hörnet av arbetsytan > **filer**.

    ![Platsen för arbetsytan](media/service-new-workspaces/power-bi-new-workspace-files-2.png)
    
- I den **hämta Data** > **filer** upplevelse. Den **OneDrive – företag** posten är ditt eget OneDrive för företag. Andra OneDrive är det du har lagt till.

    ![Platsen för arbetsytan - hämta data](media/service-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-app-workspace"></a>Lägga till innehåll i din apparbetsyta

När du har skapat en ny arbetsyta upplevelse arbetsyta, är det dags att lägga till innehåll. Lägga till nytt innehåll är liknande på nya och klassiska arbetsytor. Använd knappen Skapa eller hämta Data att lägga till innehåll till din arbetsyta.

1. I den **Välkommen** skärmen för den nya arbetsytan kan du lägga till innehåll. 

    ![Välkomstskärm för den nya arbetsytan](media/service-create-the-new-workspaces/power-bi-workspace-welcome-screen.png)

1. Välj exempelvis **Exempel** > **Kundlönsamhetsexempel**.

> [!NOTE]
> I de nya arbetsytorna använda du inte innehållspaket för organisationen eller tredje parts innehållspaket. Appar är tillgängliga för alla tredjepartsinnehåll hanteringspaket du tidigare använt. Använda klassiska arbetsytor om du vill fortsätta att använda innehållspaket. Innehållspaket är inaktuella, så det är en bra idé att använda appar i stället.

När du visar innehåll i innehållslistan på en apparbetsyta visas apparbetsytans namn som ägare.

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>Ansluta till tjänster från tredje part i nya arbetsytor

I de nya arbetsytorna gör vi en ändring för att fokusera på *appar*. Appar för tjänster från tredje part gör det enkelt för användare att hämta data från de tjänster som de använder, till exempel Microsoft Dynamics CRM, Salesforce eller Google Analytics.

Du kan inte skapa eller använda organisationsinnehållspaket i den nya upplevelsen i arbetsytan. Du kan i stället använda de appar som tillhandahålls för att ansluta till tjänster från tredje part eller be att dina egna team tillhandahåller appar för eventuella innehållspaket som du använder. 

## <a name="give-access-to-your-workspace"></a>Ge åtkomst till din arbetsyta

1. I arbetsytan innehållslistan, eftersom du är administratör visas en ny åtgärd **åtkomst**.

    ![Arbetsytor innehållslistan](media/service-create-the-new-workspaces/power-bi-workspace-content-list.png)

1. Välj **Åtkomst**.

1. Lägg till säkerhetsgrupper, distributionslistor, Office 365-grupper eller enskilda användare i dessa arbetsytor som medlemmar, deltagare eller administratörer. En förklaring av de olika rollerna finns i [Roller i de nya arbetsytorna](service-new-workspaces.md#roles-in-the-new-workspaces).

    ![Lägga till medlemmar, administratörer och deltagare i arbetsytor](media/service-create-the-new-workspaces/power-bi-access-add-members.png)

9. Välj **Lägg till** > **Stäng**.


## <a name="distribute-an-app"></a>Distribuera en app

Om du vill distribuera officiella innehåll till en stor publik i din organisation kan du publicera en app från din arbetsyta.  När innehållet är klar kan du välja vilka instrumentpaneler och rapporter som du vill publicera och sedan publicera den som en *app*. Du kan skapa en app från varje arbetsyta.

Läs mer om [publicera en app från de nya arbetsytorna](service-create-distribute-apps.md)

## <a name="next-steps"></a>Nästa steg
* Läs mer om [ordna arbete i den nya upplevelsen för arbetsytor i Power BI](service-new-workspaces.md)
* [Skapa klassiska arbetsytor](service-create-workspaces.md)
* [Publicera en app från de nya arbetsytorna i Power BI](service-create-distribute-apps.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
