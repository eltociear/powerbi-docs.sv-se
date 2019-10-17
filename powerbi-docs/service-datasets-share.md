---
title: Dela en datauppsättning (förhandsversion)
description: Som datamängdsägare kan du skapa och dela dina datamängder så att andra kan använda dem. Läs hur du delar dem.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c490228a1dfa1e6c842db3c41ab077a99f35f975
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72021124"
---
# <a name="share-a-dataset-preview"></a>Dela en datauppsättning (förhandsversion)

Som skapare av *datamodeller* i Power BI Desktop, skapar du *datauppsättningar* som du kan distribuera i Power BI-tjänsten. Andra rapportskapare kan därefter använda dina datauppsättningar som grund för sina egna rapporter. I den här artikeln får du lära dig hur du delar dina datauppsättningar. Information om hur du ger och tar bort åtkomst till dina delade datauppsättningar finns i [Skapa-behörighet](service-datasets-build-permissions.md).

## <a name="steps-to-sharing-your-dataset"></a>Steg för att dela datamängden

1. Du börja med att skapa en .pbix-fil med en datamodell i Power BI Desktop. Om du planerar att erbjuda den här datamängden till andra så att de kan skapa rapporter så skapar du kanske inte ens en rapport i .pbix-filen.

    Det är bästa praxis att spara .pbix-filen i en Office 365-grupp.

1. Publicera .pbix-filen till en [arbetsyta med den nya funktionen](service-create-the-new-workspaces.md) i Power BI-tjänsten.
    
    Andra medlemmar i den här arbetsytan kan redan skapa rapporter på andra arbetsytor baserat på den här datamängden.

1. Du kan även [publicera en app](service-create-distribute-apps.md) från den här arbetsytan. När du gör det kan du på sidan **Behörigheter** ange vilka som har behörigheter och vad de kan göra.

    > [!NOTE]
    > Om du väljer **Hela organisationen** får ingen i organisationen skapa-behörighet. Det här problemet är redan känt. I stället anger du e-postadresser i **Specific individuals or groups** (Specifika personer eller grupper).  Om du vill att hela organisationen ska ha skapa-behörighet anger du ett e-postalias för hela organisationen.

    ![Ange appbehörigheter](media/service-datasets-build-permissions/power-bi-dataset-app-permission-new-look.png)

1. Välj **Publicera app**, eller **Uppdatera app** om den redan har publicerats.

## <a name="track-your-dataset-usage"></a>Spåra datamängdsanvändningen

När du har en delad datamängd på din arbetsyta kan du behöva veta vilka rapporter på andra arbetsytor som baseras på den.

1. I listvyn Datamängder väljer du **Visa relaterade**.

    ![Ikonen Visa relaterade](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. Dialogrutan **Relaterat innehåll** visar alla relaterade objekt. I den här listan visas de relaterade objekten på den här arbetsytan och på **Andra arbetsytor**.
 
    ![Dialogrutan Relaterat innehåll](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Nästa steg

- [Använda datamängder mellan arbetsytor (förhandsversion)](service-datasets-across-workspaces.md)
- Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
