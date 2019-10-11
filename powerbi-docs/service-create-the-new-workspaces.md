---
title: Skapa de nya arbetsytorna – Power BI
description: Lär dig hur du skapar nya arbetsytor, samlingar av instrumentpaneler, rapporter och sidnumrerade rapporter som skapats för att förse din organisation med viktiga mått.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/10/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5c50ec38da65573e085d9e27b0e31524256ac009
ms.sourcegitcommit: d04b9e1426b8544ce16ef25864269cc43c2d9f7b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/01/2019
ms.locfileid: "71715530"
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

1. Börja med att skapa arbetsytan. Välj  **Arbetsytor** > **Skapa arbetsyta**.
   
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

I den nya kontaktlistan för arbetsytan kan du ange vilka användare som ska informeras om problem som kan uppstå i arbetsytan. Som standard informeras alla användare och grupper som angetts som arbetsyteadministratör, men du kan justera listan. Användare eller grupper som finns med i kontaktlistan visas i användargränssnittet för att hjälpa användarna att få hjälp med arbetsytan.

1. Få åtkomst till den nya inställningen **Kontaktlista** på ett av två sätt:

    I fönstret **Skapa en arbetsyta** första gången du skapar den.

    I det vänstra navigeringsfönstret väljer du pilen intill **Arbetsytor**, välj ellipsen (…) intill namnet på din arbetsyta > **Inställningar för arbetsytan**. Fönstret **Inställningar** öppnas.

    ![Inställningar för arbetsyta](media/service-create-the-new-workspaces/power-bi-workspace-new-settings.png)

2. Godkänn **standardadministratörer för arbetsytan** eller lägg till en egen lista över **specifika användare eller grupper** i **Avancerat** > **Kontaktlista**. 
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

När du har konfigurerat OneDrive-platsen kan du komma åt den från några olika platser i arbetsytan:

- Välj **Arbetsytor** > *arbetsytans namn* > ellipsmenyn ( **...** ) > **Filer**. 

    ![Plats för arbetsytans filer](media/service-new-workspaces/power-bi-new-workspace-files.png)

- Välj ellipsmenyn ( **...** ) i det övre högra hörnet av arbetsytan > **Filer**.

    ![Plats för arbetsytans filer](media/service-create-the-new-workspaces/power-bi-new-workspace-files-ellipsis.png)
    
- I miljön **Hämta data** > **Filer**. Posten **OneDrive – företag** är din egen OneDrive för företag. Det andra OneDrive är den som du lade till.

    ![Plats för arbetsytans filer – hämta data](media/service-create-the-new-workspaces/power-bi-new-workspace-get-data-onedrive.png)

## <a name="add-content-to-your-workspace"></a>Lägga till innehåll i din arbetsyta

När du har skapat en ny arbetsyta är det dags att lägga till innehåll. Att lägga till innehåll liknar den nya och klassiska arbetsytan. Använd knappen Skapa eller Hämta data för att lägga till innehåll på din arbetsyta.

1. På **välkomstskärmen** för den nya arbetsytan kan du lägga till data. 

    ![Välkomstskärm för den nya arbetsytan](media/service-create-the-new-workspaces/power-bi-workspace-get-data.png)

1. Välj exempelvis **Exempel** > **Kundlönsamhetsexempel**.

> [!NOTE]
> Du kan inte lägga till organisations innehållspaket eller innehållspaket från tredje part i de nya arbetsytorna. Appar är tillgängliga för många innehållspaket från tredje part som du har använt tidigare. Använd klassiska arbetsytor om du behöver fortsätta använda innehållspaket. Innehållspaket är inaktuella, så det är en bra idé att använda appar i stället.

När du visar innehåll i innehållslistan på en arbetsyta visas arbetsytans namn som ägare.

### <a name="connecting-to-third-party-services-in-new-workspaces"></a>Anslut till tjänster från tredje part i nya arbetsytor

I de nya arbetsytorna gör vi en ändring för att fokusera på *appar*. Appar för tjänster från tredje part gör det enkelt för användare att hämta data från de tjänster som de använder, till exempel Microsoft Dynamics CRM, Salesforce eller Google Analytics.

Med de nya arbetsytorna kan du inte skapa eller använda innehållspaket för organisationen. Du kan i stället använda de appar som tillhandahålls för att ansluta till tjänster från tredje part eller be att dina egna team tillhandahåller appar för eventuella innehållspaket som du använder. 

## <a name="give-access-to-your-workspace"></a>Ge åtkomst till din arbetsyta

1. Eftersom du är administratör ser du en ny åtgärd, **åtkomst**, på arbetsytans innehållslista.

    ![Innehållslista för arbetsytor](media/service-create-the-new-workspaces/power-bi-new-workspace-files-ellipsis.png)

1. Välj **Åtkomst**.

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
