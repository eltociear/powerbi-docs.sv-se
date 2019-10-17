---
title: Skapa de nya arbetsytorna – Power BI
description: Lär dig hur du skapar nya arbetsytor, samlingar av instrumentpaneler, rapporter och sidnumrerade rapporter som skapats för att förse din organisation med viktiga mått.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/02/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 7d53acc0dc8c669026665347de9593fa1df84c62
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020156"
---
# <a name="create-the-new-workspaces-in-power-bi"></a>Skapa de nya arbetsytorna i Power BI

Power BI introducerar en ny miljö för arbetsytor. Arbetsytor är fortfarande platser för samarbete med kollegor för att skapa samlingar med instrumentpaneler, rapporter och sidnumrerade rapporter. Du kan sedan paketera samlingarna i *appar* och distribuera dem till hela organisationen eller till vissa personer eller grupper. 

Detta har ändrats. Med de nya arbetsytorna kan du:

- Tilldela arbetsyteroller till användargrupper: säkerhetsgrupper, distributionslistor, Office 365-grupper och enskilda användare.
- Skapa en arbetsyta i Power BI utan att skapa en Office 365-grupp.
- Använda mer detaljerade arbetsyteroller för mer flexibel hantering av behörigheter på en arbetsyta.

> [!NOTE]
> Om du vill inför säkerhet på radnivå (RLS) för Power BI Pro-användare som bläddrar i innehållet i en arbetsyta, kan du tilldela användarna läsarrollen.

Mer bakgrundsinformation finns i artikeln om [nya arbetsytor](service-new-workspaces.md).

## <a name="create-one-of-the-new-workspaces"></a>Skapa en av de nya arbetsytorna

1. Börja med att skapa arbetsytan. Välj **Arbetsytor** > **Skapa arbetsyta**.
   
     ![Skapa arbetsyta](media/service-create-the-new-workspaces/power-bi-workspace-create.png)

2. Du skapar en uppgraderad arbetsyta automatiskt om du inte väljer att **återgå till klassiskt**.
   
     ![Ny arbetsyteupplevelse](media/service-create-the-new-workspaces/power-bi-new-workspace.png)
     
     Om du väljer **återgå till klassiskt**skapar du en [arbetsyta som baseras på en Office 365-grupp](service-create-workspaces.md). 

2. Ge arbetsytan ett namn. Om namnet inte är tillgängligt kan du redigera det för att få fram ett unikt namn.
   
     Appen för arbetsytan kommer att ha samma namn och ikon som arbetsytan.
   
1. Här följer några valfria objekt som du kan ställa in för din arbetsyta:

    Överför en **arbetsytebild**. Filerna kan vara i .png- eller .jpg-format. Filstorleken måste vara mindre än 45 KB.
    
    [Lägg till en **Kontaktlista**](#workspace-contact-list). Som standard är arbetsytans administratörer kontakter. 
    
    [Ange en **OneDrive för arbetsytan**](#workspace-onedrive) genom att endast skriva namnet på en befintlig Office 365-grupp, inte URL:en. Nu kan den här arbetsytan använda Office 365-gruppens fillagringsplats. 

    ![Ange en OneDrive-plats](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

    Om du vill tilldela arbetsytan till en **Dedikerad kapacitet** går du till fliken **Premium** och väljer **Dedikerad kapacitet**.
     
    ![Dedikerad kapacitet](media/service-create-the-new-workspaces/power-bi-workspace-premium.png)

1. Välj **Spara**.

    Power BI skapar arbetsytan och öppnar den. Den visas i listan med arbetsytor som du är medlem i. 

## <a name="workspace-contact-list"></a>Arbetsytans kontaktlista

Du kan ange vilka användare som ska informeras om problem som uppstår i arbetsytan. Som standard informeras alla användare och grupper som angetts som arbetsyteadministratör, men du kan anpassa listan genom att lägga till dem i *kontaktlista*. Användare eller grupper som finns med i kontaktlistan visas i användargränssnittet för att hjälpa användarna att få hjälp med arbetsytan.

1. Få åtkomst till den nya inställningen **Kontaktlista** på ett av två sätt:

    I fönstret **Skapa en arbetsyta** första gången du skapar den.

    I det vänstra navigeringsfönstret väljer du pilen intill **Arbetsytor**, välj ellipsen (…) intill namnet på din arbetsyta > **Inställningar för arbetsytan**. Fönstret **Inställningar** öppnas.

    ![Inställningar för arbetsyta](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Godkänn **standardadministratörer för arbetsytan** eller lägg till en egen lista över **specifika användare eller grupper** i **Avancerat** > **Kontaktlista**. 

    ![Arbetsytans kontakter](media/service-create-the-new-workspaces/power-bi-workspace-contacts.png)

3. Välj **Spara**.

## <a name="workspace-onedrive"></a>Arbetsytans OneDrive

Med arbetsytans OneDrive-funktion kan du konfigurera en Office 365-grupp vars fillagring för SharePoint-dokumentbiblioteket är tillgänglig för arbetsyteanvändarna. Du skapar gruppen först utanför Power BI. 

Power BI synkroniserar inte behörigheter för användare eller grupper, som är konfigurerade med arbetsyteåtkomst, med Office 365-gruppmedlemskapet. Det bästa sättet är att ge den Office 365-grupp vars fillagring du konfigurerar i den här inställningen [åtkomst till arbetsytan](#give-access-to-your-workspace). Hantera sedan åtkomst till arbetsytan genom att hantera medlemskap i Office 365-gruppen. 

1. Öppna den nya **OneDrive**-inställningen för arbetsytan på något av följande två sätt:

    I fönstret **Skapa en arbetsyta** första gången du skapar den.

    I det vänstra navigeringsfönstret väljer du pilen intill **Arbetsytor**, välj ellipsen (…) intill namnet på din arbetsyta > **Inställningar för arbetsytan**. Fönstret **Inställningar** öppnas.

    ![Inställningar för arbetsyta](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Under **Avancerat** > **OneDrive för arbetsytan** anger du namnet på den Office 365-grupp som du skapade tidigare. Power BI hämtar automatiskt OneDrive för gruppen.

    ![Ange en OneDrive-plats](media/service-create-the-new-workspaces/power-bi-new-workspace-onedrive.png)

3. Välj **Spara**.

### <a name="access-the-workspace-onedrive-location"></a>Åtkomst till arbetsytans OneDrive-plats

När du har konfigurerat OneDrive-platsen kommer du till den på samma sätt som du kommer till andra datakällor i Power BI-tjänsten.

1. I det vänstra navigeringsfönstret väljer du **Hämta data** och därefter väljer du **Hämta** i rutan **Filer**.

    ![Hämta data, hämta filer](media/service-create-the-new-workspaces/power-bi-get-data-files.png)

1.  Posten **OneDrive – företag** är din egen OneDrive för företag. Det andra OneDrive är den som du lade till.

    ![Plats för arbetsytans filer – hämta data](media/service-create-the-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>Anslut till tjänster från tredje part i nya arbetsytor

I de nya arbetsytorna gör vi en ändring för att fokusera på *appar*. Appar för tjänster från tredje part gör det enkelt för användare att hämta data från de tjänster som de använder, till exempel Microsoft Dynamics CRM, Salesforce eller Google Analytics.

Med de nya arbetsytorna kan du inte skapa eller använda innehållspaket för organisationen. Du kan i stället använda de appar som tillhandahålls för att ansluta till tjänster från tredje part eller be att dina egna team tillhandahåller appar för eventuella innehållspaket som du använder. 

## <a name="give-access-to-your-workspace"></a>Ge åtkomst till din arbetsyta

1. Eftersom du är administratör ser du en ny åtgärd, **åtkomst**, på arbetsytans innehållslista.

    ![Innehållslista för arbetsytor](media/service-create-the-new-workspaces/power-bi-workspace-access-icon.png)

1. Lägg till säkerhetsgrupper, distributionslistor, Office 365-grupper eller enskilda användare i dessa arbetsytor som medlemmar, deltagare eller administratörer. En förklaring av de olika rollerna finns i [Roller i de nya arbetsytorna](service-new-workspaces.md#roles-in-the-new-workspaces).

    ![Lägga till medlemmar, administratörer och deltagare i arbetsytor](media/service-create-the-new-workspaces/power-bi-workspace-add-members.png)

9. Välj **Lägg till** > **Stäng**.


## <a name="distribute-an-app"></a>Distribuera en app

Om du vill distribuera officiellt innehåll till en stor målgrupp i din organisation kan du publicera en app från din arbetsyta.  När innehållet är färdigt kan du välja vilka instrumentpaneler och rapporter som du vill publicera och sedan publicera det som en *app*. Du kan skapa en app från varje arbetsyta.

Läs om att [publicera en app från de nya arbetsytorna](service-create-distribute-apps.md)

## <a name="next-steps"></a>Nästa steg
* Läs om att [organisera arbete i de nya arbetsytorna i Power BI](service-new-workspaces.md)
* [Skapa klassiska arbetsytor](service-create-workspaces.md)
* [Publicera en app från de nya arbetsytorna i Power BI](service-create-distribute-apps.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
