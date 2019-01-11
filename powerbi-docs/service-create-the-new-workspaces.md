---
title: Skapa de nya arbetsytorna (förhandsversion) – Power BI
description: Lär dig hur du skapar de nya arbetsytorna, samlingar av instrumentpaneler och rapporter som skapats för att förse din organisation med statistik.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/19/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a93c676775fe6e826ea83cfad91498b7fe3e2103
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983610"
---
# <a name="create-the-new-workspaces-preview-in-power-bi"></a>Skapa de nya arbetsytorna (förhandsversion) i Power BI

Power BI introducerar en ny arbetsyta som en förhandsversion. Arbetsytor är fortfarande platser där du kan samarbeta med kollegor för att skapa samlingar av instrumentpaneler och rapporter, som du kan samla till *appar* och distribuera till hela organisationen eller till specifika personer eller grupper. 

![Förhandsversion av nya arbetsytor i Power BI](media/service-create-the-new-workspaces/power-bi-new-workspaces-preview.png)

Med förhandsversion av de nya arbetsytorna kan du nu:

- Tilldela arbetsyteroller till användargrupper: säkerhetsgrupper, distributionslistor, Office 365-grupper och enskilda användare.
- Skapa en arbetsyta i Power BI utan att skapa en Office 365-grupp.
- Använda mer detaljerade arbetsyteroller för mer flexibel hantering av behörigheter på en arbetsyta.

Mer bakgrund finns i artikeln om [nya arbetsytor (förhandsversion)](service-new-workspaces.md).

## <a name="create-one-of-the-new-app-workspaces"></a>Skapa en av de nya apparbetsytorna

1. Börja med att skapa apparbetsytan. Välj **Arbetsytor** > **Skapa apparbetsyta**.
   
     ![Skapa en apparbetsyta](media/service-create-the-new-workspaces/power-bi-create-app-workspace.png)

2. I **Förbättrade arbetsytor i förhandsversion** väljer du **Prova nu**.
   
     ![Förbättrade arbetsytor i förhandsversion](media/service-create-the-new-workspaces/power-bi-preview-improved-workspaces.png)

2. Ge arbetsytan ett namn. Om namnet inte är tillgängligt kan du redigera det för att få fram ett unikt ID.
   
     Appen får samma namn som arbetsytan.
   
1. Lägg till en bild om du vill. Filstorleken måste vara mindre än 45 KB.
 
    ![Ge arbetsytan ett namn och lägga till en bild](media/service-create-the-new-workspaces/power-bi-name-workspace.png)

1. Välj **Spara**.

    Här på **välkomstskärmen** för den nya arbetsytan kan du lägga till data. 

    ![Välkomstskärm för den nya arbetsytan](media/service-create-the-new-workspaces/power-bi-workspace-welcome-screen.png)

1. Välj exempelvis **Exempel** > **Kundlönsamhetsexempel**.

    I innehållslistan för arbetsytan visas nu **Förhandsgranskning av nya arbetsytor**. Eftersom du är administratör ser du även en ny åtgärd: **Åtkomst**.

    ![Innehållslista för förhandsversion av arbetsyta](media/service-create-the-new-workspaces/power-bi-workspaces-preview-content-list.png)

1. Välj **Åtkomst**.

1. Lägg till säkerhetsgrupper, distributionslistor, Office 365-grupper eller enskilda användare i dessa arbetsytor som medlemmar, deltagare eller administratörer. En förklaring av de olika rollerna finns i [Roller i de nya arbetsytorna](#roles-in-the-new-workspaces) senare i den här artikeln.

    ![Lägga till medlemmar, administratörer och deltagare i arbetsytor](media/service-create-the-new-workspaces/power-bi-access-add-members.png)

9. Välj **Lägg till** > **Stäng**.

1. Power BI skapar arbetsytan och öppnar den. Den visas i listan med arbetsytor som du är medlem i. Eftersom du är administratör kan du välja ellipsen (...) för att gå tillbaka och göra ändringar i inställningarna för arbetsytan, lägga till nya medlemmar eller ändra deras behörigheter.

     ![Redigera inställningar och åtkomst för en arbetsyta](media/service-create-the-new-workspaces/power-bi-edit-workspace.png)

## <a name="add-content-to-your-app-workspace"></a>Lägga till innehåll i din apparbetsyta

När du har skapat en apparbetsyta med det nya formatet är det dags att lägga till innehåll. Att lägga till nytt innehåll sker på ett liknande sätt i arbetsytorna med det nya och det gamla formatet, med ett undantag. När du befinner dig på endera apparbetsyta kan du ladda upp eller ansluta till filer, precis som på Min arbetsyta. I de nya arbetsytorna kan du inte ansluta till organisationsinnehållspaket eller innehållspaket från tredje part såsom Microsoft Dynamics CRM, Salesforce eller Google Analytics. I de aktuella arbetsytorna kan du ansluta till innehållspaket.

När du visar innehåll i innehållslistan på en apparbetsyta visas apparbetsytans namn som ägare.

### <a name="connecting-to-third-party-services-in-new-workspaces-preview"></a>Ansluta till tjänster från tredje part i nya arbetsytor (förhandsversion)

I de nya arbetsytorna gör vi en ändring för att fokusera på *appar*. Appar för tjänster från tredje part gör det enkelt för användare att hämta data från de tjänster som de använder, till exempel Microsoft Dynamics CRM, Salesforce eller Google Analytics.
Organisationsappar ger användarna de interna data de behöver. Vi planerar att lägga till funktioner i organisationsappar så att användare kan anpassa det innehåll de hittar i apparna. Den funktionen tar bort behovet av innehållspaket. 

Med förhandsversionen av de nya arbetsytorna kan du inte skapa eller använda innehållspaket för organisationen. Du kan i stället använda de appar som tillhandahålls för att ansluta till tjänster från tredje part eller be att dina egna team tillhandahåller appar för eventuella innehållspaket som du använder. 

## <a name="distribute-an-app"></a>Distribuera en app

När innehållet är färdigt kan du välja vilka instrumentpaneler och rapporter som du vill publicera, och sedan publicerar du det som en *app*. Du kan skapa en app från varje arbetsyta. Dina medarbetare kan få appen på ett par olika sätt. Du kan installera den automatiskt på dina medarbetares Power BI-konton om din Power BI-administratör ger dig behörighet. I annat fall kan de hitta och installera din app från Microsoft AppSource, eller så kan du skicka dem en direktlänk. De får uppdateringar automatiskt och du kan styra hur ofta dina data ska uppdateras. Information finns i [Publicera appar med instrumentpaneler och rapporter i Power BI](service-create-distribute-apps.md).

## <a name="convert-old-app-workspaces-to-new-app-workspaces"></a>Konvertera gamla apparbetsytor till nya apparbetsytor

Under förhandsversionsperioden kan du inte automatiskt konvertera dina gamla apparbetsytor till nya. Du kan dock skapa en ny apparbetsyta och publicera ditt innehåll till den nya platsen. 

När de nya arbetsytorna blir allmänt tillgängliga (GA, generally available) kan du välja att gå med för att migrera gamla automatiskt. Någon gång efter GA måste du migrera dem.

## <a name="next-steps"></a>Nästa steg
* Läs om att [organisera arbete i de nya arbetsytorna (förhandsversion) i Power BI](service-new-workspaces.md)
* [Skapa de aktuella arbetsytorna](service-create-workspaces.md)
* [Installera och använda appar i Power BI](service-create-distribute-apps.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
