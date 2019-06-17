---
title: Skapa och dela datamängder (förhandsversion) – Power BI
description: Som datamängdsägare kan du skapa och dela dina datamängder så att andra kan använda dem. Lär dig hur du kontrollerar vem som har åtkomst till data med hjälp av skapa-behörighet.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 22339b3d5062c01b3795086eede24ed6a8e7d7e7
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461774"
---
# <a name="create-and-share-datasets-preview"></a>Skapa och dela datamängder (förhandsversion)

Som skapare av *datamodeller* i Power BI Desktop kan du dela dem som *datamängder* i Power BI-tjänsten. Rapportskapare kan sedan enkelt upptäcka och återanvända de datamängder som du har delat. Lär dig hur du delar dem och hur du kontrollerar vem som har åtkomst till data med hjälp av skapa-behörighet.

## <a name="steps-to-sharing-your-dataset"></a>Steg för att dela datamängden

1. Du börja med att skapa en .pbix-fil med en datamodell i Power BI Desktop. Om du planerar att erbjuda den här datamängden till andra så att de kan skapa rapporter så skapar du kanske inte ens en rapport i .pbix-filen.

    Det är bästa praxis att spara .pbix-filen i en Office 365-grupp.

1. Publicera .pbix-filen till en [arbetsyta med den nya funktionen](service-create-the-new-workspaces.md) i Power BI-tjänsten.
    
    Andra medlemmar i den här arbetsytan kan redan skapa rapporter på andra arbetsytor baserat på den här datamängden.

1. Nu kan du [skapa en app](service-create-distribute-apps.md) från den här arbetsytan. När du gör det kan du på sidan **Behörigheter** ange vilka som har behörigheter och vad de kan göra.

    > [!NOTE]
    > Om du väljer **Hela organisationen** får ingen i organisationen skapa-behörighet. Det här problemet är redan känt. I stället anger du e-postadresser i **Specific individuals or groups** (Specifika personer eller grupper).  Om du vill att hela organisationen ska ha skapa-behörighet anger du ett e-postalias för hela organisationen.

    ![Ange appbehörigheter](media/service-datasets-build-permissions/power-bi-dataset-app-permissions.png)

1. Välj **Publicera app**, eller **Uppdatera app** om den redan har publicerats.

## <a name="build-permissions-for-shared-datasets"></a>Skapa-behörighet för delade datamängder

Skapa-behörighetstypen är endast relevant för datamängder. Med den kan användare skapa nytt innehåll i en datamängd, till exempel rapporter, instrumentpaneler, fästa paneler från Frågor och svar samt Insights Discovery. De kan även skapa nytt innehåll på datamängden utanför Power BI, till exempel Excel-blad via Analysera i Excel, XMLA och exportera.

Användare får skapa-behörighet på olika sätt:

- En medlem i den arbetsyta där datamängden finns kan tilldela behörigheten till specifika användare eller säkerhetsgrupper i behörighetscentret. Välj ellipsen (…) intill en datamängd > **Hantera behörigheter**.

    ![Välj ellipsen](media/service-datasets-build-permissions/power-bi-dataset-manage-permissions.png)

    Då öppnas behörighetscentret för den datamängden, där du kan ange och ändra behörigheter.

    ![Behörighetscentret](media/service-datasets-build-permissions/power-bi-dataset-permissions.png)

- En administratör eller medlem i den arbetsyta där datamängden finns kan under publicering av app bestämma att användare med behörighet för den appen även får skapa-behörighet för de underliggande datamängderna. Mer information finns i [Steg för att dela datamängden](#steps-to-sharing-your-dataset).

- Anta att du har vidaredelnings- och skapa-behörigheter för en datamängd. När du delar en rapport eller instrumentpanel som skapats ovanpå den datamängden kan du ange att mottagarna även får skapa-behörighet för den underliggande datamängden.

    ![Skapa-behörighet](media/service-datasets-build-permissions/power-bi-share-report-allow-users.png)

Du kan ta bort personers skapa-behörighet för en datamängd. Om du gör det kan de fortfarande se den rapport som skapats på den delade datamängden, men de kan inte längre redigera den.

## <a name="more-granular-permissions"></a>Mer granulära behörigheter

Power BI introducerade skapa-behörigheten i juni 2019 som ett komplement till de befintliga behörigheterna Läsa och Dela vidare. Alla användare som redan hade läsbehörighet för datamängder via appbehörigheter, delning eller arbetsyteåtkomst vid den tidpunkten fick även skapa-behörighet för samma datamängder. De fick skapa-behörighet automatiskt eftersom läsbehörighet redan gav den rätt att skapa nytt innehåll ovanpå datamängden med hjälp av Analysera i Excel eller export.

Med den här mer granulära skapa-behörigheten kan du välja vilka som endast kan se innehållet i den befintliga rapporten eller instrumentpanelen samt vilka som kan skapa innehåll som är kopplat till de underliggande datamängderna.

Om din datamängd används av en rapport utanför datamängdens arbetsyta kan du inte ta bort den datamängden. I stället visas ett felmeddelande.

Du kan ta bort skapa-behörigheter. Om du gör det kan de personer vars behörigheter du har återkallat fortfarande se rapporten, men de kan inte längre redigera den.

## <a name="track-your-dataset-usage"></a>Spåra datamängdsanvändningen

När du har en delad datamängd på din arbetsyta kan du behöva veta vilka rapporter på andra arbetsytor som baseras på den.

1. I listvyn Datamängder väljer du **Visa relaterade**.

    ![Ikonen Visa relaterade](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. Dialogrutan **Relaterat innehåll** visar alla relaterade objekt. I den här listan visas de relaterade objekten på den här arbetsytan och på **Andra arbetsytor**.
 
    ![Dialogrutan Relaterat innehåll](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="next-steps"></a>Nästa steg

- [Använda datamängder mellan arbetsytor (förhandsversion)](service-datasets-across-workspaces.md)
- Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
