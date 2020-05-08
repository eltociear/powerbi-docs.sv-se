---
title: Uppdatera, ta bort och extrahera en Power BI-mallapp
description: Så här uppdaterar du, tar bort och extraherar en mallapp.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/04/2020
ms.author: painbar
ms.openlocfilehash: 26587969263dc403dbc86c1ba4290f75f1ad1c41
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82781396"
---
# <a name="update-delete-and-extract-template-app"></a>Uppdatera, ta bort och extrahera en mallapp

Nu när appen är i produktion kan börja du om i testfasen, utan att det påverkar appen i produktion.
## <a name="update-your-app"></a>Uppdatera din app

Om du har gjort ändringarna i Power BI Desktop börjar du med steg (1). Om du inte har gjort ändringarna i Power BI Desktop börjar du med steg (4).

1. Ladda upp den uppdaterade datauppsättningen och skriv över datauppsättningen. **Se till att använda exakt samma datauppsättningsnamn**. Om du använder ett annat namn skapas en nu datauppsättning för användare som uppdaterar appen.
![skriv över datauppsättning](media/service-template-apps-update-extract-delete/power-bi-template-app-upload-dataset.png)
1. Importera pbix-filen från datorn.
![skriv över datauppsättning](media/service-template-apps-update-extract-delete/power-bi-template-app-upload-dataset2.png)
1. Bekräfta överskrivningen.
![skriv över datauppsättning](media/service-template-apps-update-extract-delete/power-bi-template-app-upload-dataset3.png)

1. Välj **Skapa app** i fönstret **Versionshantering**.
1. Börja om skapandeprocessen.
1. När du har angett **Anpassning**, **Innehåll**, **Kontroll** och **Åtkomst** väljer du **Skapa app** på nytt.
1. Välj **Stäng** och gå tillbaka till **Versionshantering**.

   Nu kan du se att du har två versioner: Versionen som är i produktion, samt en ny version i testning.

    ![Två versioner av en mallapp](media/service-template-apps-update-extract-delete/power-bi-template-app-update1.png)

1. När du är redo att flytta upp appen till förproduktion för ytterligare testning utanför klientorganisationen, går du tillbaka till versionshanteringsfönstret och väljer **Höj upp appen** bredvid **Testar**.

   Nu har du en version i produktion och en version i förproduktion.

   ![Två versioner av en mallapp, höj upp nedtonat](media/service-template-apps-update-extract-delete/power-bi-template-app-update2.png)

   Länken är nu live. **Observera att knappen Höj upp appen är nedtonad i förproduktionssteget**. Det här görs för att förhindra att du råkar skriva över länken till den aktuella appversionen innan Cloud Partner Portal har verifierat och godkänt den nya appversionen.

1. Skicka länken igen till Cloud Partner Portal (CPP) genom att följa stegen i [Uppdatera ett Power BI-apperbjudande](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer). Du måste **publicera** ditt erbjudande igen i Cloud Partner Portal och få det validerat.

   När ditt erbjudande godkänns aktiveras knappen Höj upp appen igen. 
1. Höj upp din app till produktionssteget.
   
### <a name="update-behavior"></a>Uppdateringsfunktioner

1. Om du uppdaterar appen kan installationsprogrammet för mallappen [uppdatera en mallapp](service-template-apps-install-distribute.md#update-a-template-app) på den redan installerade arbetsytan utan att förlora anslutningskonfigurationen.
1. Se installationens [överskrivningsfunktioner](service-template-apps-install-distribute.md#overwrite-behavior) för att få reda på hur ändringar i datauppsättningen påverkar den installerade mallappen.
1. När du uppdaterar (skriver över) en mallapp återgår den först till exempeldata och ansluter automatiskt igen till användarens konfiguration (parametrar och autentisering). Innan uppdateringen har slutförts visas exempeldatabanderollen för rapporter, instrumentpaneler och organisationsappen.
1. Om du har lagt till en ny frågeparameter till den uppdaterade datauppsättningen som kräver indata från användaren måste du markera kryssrutan *obligatoriskt*. Detta anger anslutningssträngen för installationsprogrammet när appen har uppdaterats.
 ![obligatoriska parametrar](media/service-template-apps-update-extract-delete/power-bi-template-app-upload-dataset4.png)

## <a name="extract-workspace"></a>Extrahera arbetsyta
Att återgå till en tidigare version av en mallapp är nu enklare än någonsin med extraheringsfunktionen. Med följande steg kan du extrahera en specifik appversion från olika versionsstadier till en ny arbetsyta:

1. I versionshanteringsfönstret trycker du på mer **(...)**  och sedan på **Extrahera**.

    ![extrahera mallappsversion](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![extrahera mallappsversion](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. I dialogrutan anger du namnet för den extraherade arbetsytan. En ny arbetsyta kommer att läggas till.

Din nya arbetsyteversion återställs och du kan fortsätta att utveckla och distribuera mallappen från den nyligen extraherade arbetsytan.

## <a name="delete-template-app-version"></a>Ta bort mallappsversion
En mallarbetsyta är källa till en aktiv distribuerad mallapp. För att skydda mallappsanvändarna går det inte att ta bort en arbetsyta utan att först ta bort alla skapade appversioner på arbetsytan.
Om du tar bort en appversion, tas även app-URL:en bort som inte längre fungerar.

1. I versionshanteringsfönstret trycker du på ellipsen **(...)**  och sedan på **Ta bort**.
 ![Ta bort mallappsversion](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
 ![Ta bort mallappsversion](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>Se till att du inte ta bort en appversion som används av kunder eller **AppSource**, då fungerar de inte längre.

## <a name="next-steps"></a>Nästa steg

Se hur dina kunder interagerar med din mallapp i [Installera, anpassa och distribuera mallappar i organisationen](service-template-apps-install-distribute.md).

Se [Power BI Application offer](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) (Power BI-programerbjudande) för mer information.
