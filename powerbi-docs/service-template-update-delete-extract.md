---
title: Uppdatera, ta bort och extrahera en Power BI-mallapp
description: Så här uppdaterar du, tar bort och extraherar en mallapp.
author: teddybercovitz
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/10/2019
ms.author: tebercov
ms.openlocfilehash: 273734493c761739f9780e6a7fe6e781900723f9
ms.sourcegitcommit: 7d52401f50944feaaa112c84113ee47f606dbf68
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/13/2019
ms.locfileid: "67125888"
---
# <a name="update-delete-and-extract-template-app"></a>Uppdatera, ta bort och extrahera en mallapp

Nu när appen är i produktion kan börja du om i testfasen, utan att det påverkar appen i produktion.
## <a name="update-your-app"></a>Uppdatera din app


1. Välj **Skapa app** i fönstret **Versionshantering**.
2. Börja om skapandeprocessen.
3. När du har angett **Anpassning**, **Innehåll**, **Kontroll** och **Åtkomst** väljer du **Skapa app** på nytt.
4. Välj **Stäng** och gå tillbaka till **Versionshantering**.

   Nu kan du se att du har två versioner: Versionen som är i produktion, samt en ny version i testning.

    ![Två versioner av en mallapp](media/service-template-apps-update-extract-delete/power-bi-template-app-update.png)

5. När du är redo att flytta upp appen till förproduktion för ytterligare testning utanför klientorganisationen, går du tillbaka till versionshanteringsfönstret och väljer **Höj upp appen** bredvid **Testar**.
6. Länken är nu live. Skicka den igen till Cloud Partner Portal (CPP) genom att följa stegen i [Uppdatera ett Power BI-apperbjudande](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-update-existing-offer).
7. I CPP måste du **publicera** ditt erbjudande igen samt få det validerat igen.

>[!NOTE]
>Höj inte upp appen till produktion förrän den har godkänts i Cloud Partner Portal och du publicerar den.

## <a name="extract-workspace"></a>Extrahera arbetsyta
Att återgå till en tidigare version av en mallapp är nu enklare än någonsin med extraheringsfunktionen. Med följande steg kan du extrahera en specifik appversion från olika versionsstadier till en ny arbetsyta:

1. I versionshanteringsfönstret trycker du på mer **(...)**  och sedan på **Extrahera**.

    ![extrahera mallappsversion](media/service-template-apps-update-extract-delete/power-bi-template-app-extract.png) ![extrahera mallappsversion](media/service-template-apps-update-extract-delete/power-bi-template-app-extract-dialog.png)
2. I dialogrutan anger du namnet för den extraherade arbetsytan. En ny arbetsyta kommer att läggas till.

Din nya arbetsyteversion återställs och du kan fortsätta att utveckla och distribuera mallappen från den nyligen extraherade arbetsytan.

## <a name="delete-template-app-version"></a>Ta bort mallappsversion
En mallappsarbetsyta är källan till en aktiv distribuerad mallapp. För att skydda mallappsanvändarna går det inte att ta bort en arbetsyta utan att först ta bort alla skapade appversioner på arbetsytan.
Om du tar bort en appversion, tas även app-URL:en bort som inte längre fungerar.

1. I versionshanteringsfönstret trycker du på ellipsen **(...)**  och sedan på **Ta bort**.
 ![Ta bort mallappsversion](media/service-template-apps-update-extract-delete/power-bi-template-app-delete.png)
  ![Ta bort mallappsversion](media/service-template-apps-update-extract-delete/power-bi-template-app-delete-dialog.png)

>[!NOTE]
>Se till att du inte ta bort en appversion som används av kunder eller **AppSource**, då fungerar de inte längre.

## <a name="next-steps"></a>Nästa steg

Se hur dina kunder interagerar med din mallapp i [Installera, anpassa och distribuera mallappar i organisationen](service-template-apps-install-distribute.md).

Se [Power BI Application offer](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) (Power BI-programerbjudande) för mer information.
