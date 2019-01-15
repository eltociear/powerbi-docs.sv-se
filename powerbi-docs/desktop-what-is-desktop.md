---
title: Vad är Power BI Desktop?
description: Läs om vad Power BI Desktop är och hur du kommer igång med det
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: overview
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: d687e9ed9fac38dabf539a4f2fffbc89cf3a2bbb
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54296143"
---
# <a name="what-is-power-bi-desktop"></a>Vad är Power BI Desktop?

**Power BI Desktop** är ett kostnadsfritt program som du kan installera på din lokala dator som låter dig ansluta till, transformera och visualisera dina data. Med **Power BI Desktop**, kan du ansluta till flera olika datakällor och kombinera dem (kallas ofta för modellering) till en datamodell som låter dig skapa visuell information och samlingar av visuell information som du kan dela som rapporter med andra personer i din organisation. De flesta användare som arbetar i Business Intelligence-projekt använder **Power BI Desktop** för att skapa rapporter och använder sedan **Power BI-tjänsten** för att dela sina rapporter med andra.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

De vanligaste användningarna för **Power BI Desktop** är följande:

* Ansluta till data
* Transformera och rensa dessa data för att skapa en datamodell
* Skapa visuell information, till exempel diagram som ger visuella representationer av data
* Skapa rapporter som är samlingar av visuell information på en eller flera rapportsidor
* Dela rapporter med andra med hjälp av **Power BI-tjänsten**

Personer som oftast ansvarar för sådana uppgifter anses ofta vara *dataanalytiker* (ibland bara *analytiker*) eller Business Intelligence-tekniker (kallas ofta för *rapportskapare*). Men många som inte anser sig vara analytiker eller rapportskapare använder sig av **Power BI Desktop** för att skapa övertygande rapporter eller för att hämta data från olika källor och skapa datamodeller som de kan dela med sina medarbetare och organisationer.

Med **Power BI Desktop** kan du skapa komplexa och visuellt omfattande rapporter med hjälp av data från flera källor i en enda rapport som du kan dela med andra i din organisation. 

## <a name="connect-to-data"></a>Ansluta till data
Det första steget för att komma igång med **Power BI Desktop** är att ansluta till data. Det finns alla möjliga sorters datakällor du kan ansluta till med **Power BI Desktop**. För att ansluta till data, markerar du bara menyfliksområdet **Start** och väljer sedan **Hämta data > Mer**. Följande bild visar fönstret **Hämta data** som visas med de olika kategorier som Power BI Desktop kan ansluta till.

![Hämta data i Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_02.png)

När du väljer en datatyp, uppmanas du att ange information, till exempel URL och autentiseringsuppgifter som krävs för att Power BI Desktop ska kunna ansluta till datakällan för din räkning.

![Anslut till en SQL Server-databas i Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_03.png)

När du ansluter till en eller flera datakällor, kanske du vill omvandla data så att de är användbara för dig.

## <a name="transform-and-clean-data-create-a-model"></a>Transformera och rensa data, skapa en modell

I Power BI Desktop, kan du rensa och transformera data med hjälp av den inbyggda **Frågeredigeraren**. Med frågeredigeraren, kan du göra ändringar i dina data, till exempel ändra datatyp, ta bort kolumner eller kombinera data från flera källor. Det är lite som att skulptera. Du börjar med en stor klump lera (eller data) och filar sedan bort olika bitar och lägger till andra tills dess att dina data har den form som du är ute efter. 

![Frågeredigeraren i Power BI Desktop](media/desktop-getting-started/designer_gsg_editquery.png)

Varje steg du tar när du transformerar data (till exempel när du byter namn på en tabell, transformerar datatypen eller tar bort kolumner) registreras av **Frågeredigeraren** och varje gång den här frågan ansluter till datakällan utförs dessa steg så att data alltid utformas på det sätt som du anger.

Följande bild visar fönstret **Frågeinställningar** för en fråga som har formats och omvandlats till en modell.

 ![](media/desktop-getting-started/shapecombine_querysettingsfinished.png)

När dina data är som du vill ha dem så kan du skapa visuell information. 

## <a name="create-visuals"></a>Skapa visuella objekt 

När du har en datamodell, kan du dra *fält* till rapportarbetsytan och skapa *visuell information*. En *visuell information* är en grafisk representation av data i din modell. Följande visuella information visar ett enkelt stapeldiagram. 

![Visuell information i Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_04.png)

Det finns många olika typer av visuell information att välja mellan i Power BI Desktop. Om du vill skapa eller ändra visuell information, väljer du bara ikonen visuell information från den fönstret **Visualiseringar**. Om du har visuell information markerad på rapportarbetsytan så ändras den markerade visuella informationen till den typ du valt. Om ingen visuell information har valts, skapas ny visuell information baserat på ditt val.

![Fönstret visualiseringar i Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_05.png)

## <a name="create-reports"></a>Skapa rapporter

Vanligare är att du vill skapa en samling visuell information som visar olika aspekter av de data som du har använt för att skapa din modell i Power BI Desktop. En samling med visuell information i en Power BI Desktop-fil kallas en *rapport*. En rapport kan innehålla en eller flera sidor, precis som en Excel-fil kan ha ett eller flera kalkylblad. I följande bild visas den första sidan i en Power BI Desktop-rapport med namnet översikt (du kan se fliken längst ned i bilden). Det finns tio sidor i den här rapporten.

![Power BI Desktop-rapport med tio sidor](media/desktop-what-is-desktop/what-is-desktop_01.png)

## <a name="share-reports"></a>Dela rapporter

När en rapport är redo att delas med andra, kan du **Publicera** rapporten till **Power BI-tjänster** och göra den tillgänglig för alla i din organisation som har en Power BI-licens. Om du vill publicera en Power BI Desktop-rapport väljer du **Publicera**-knappen från menyfliksområdet **Start** i Power BI Desktop.

![Publicera en rapport från Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_06.png)

När du har valt **Publicera**, ansluter Power BI Desktop dig till **Power BI-tjänsten** med ditt Power BI-konto och ber dig välja var i Power BI-tjänsten som du vill dela rapporten, till exempel din arbetsyta, en team-arbetsyta eller en annan plats i Power BI-tjänsten. Du måste ha en Power BI-licens för att dela rapporter till Power BI-tjänsten.


## <a name="next-steps"></a>Nästa steg

Om du vill komma igång med **Power BI Desktop** är det första du behöver göra att ladda ned och installera programmet. Det finns två sätt att hämta **Power BI Desktop**:

* [Hämta Power BI Desktop från webben](desktop-get-the-desktop.md)
* [Hämta Power BI Desktop från Windows Store](http://aka.ms/pbidesktopstore)
