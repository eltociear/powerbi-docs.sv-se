---
title: Hämta data från filer för Power BI
description: Lär dig hur du hämtar data från Excel-, Power BI Desktop- och CSV-filer till Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 8eeb8431f3f4e5fff15bb1eb2984826c73826b34
ms.sourcegitcommit: 10a87c016f497dbeba32f94ed1f3688a70816fea
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65511919"
---
# <a name="get-data-from-files-for-power-bi"></a>Hämta data från filer för Power BI
![](media/service-get-data-from-files/file_icons.png)

I Power BI, kan du ansluta till eller importera data och rapporter från tre typer av filer.

* Microsoft Excel (.xlsx eller .xlsm)
* Power BI Desktop (.pbix)
* Kommaavgränsade värden (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>Vad innebär det att hämta data från en fil?
I Power BI kommer data som du utforskar från en datauppsättning. Men för att få en datauppsättning, måste du först hämta några data. I den här artikeln ska vi fokusera på att hämta data från filer.

För att bättre förstå vikten av datauppsättningar och hur vi hämtar data för dem, kan vi ta en titt på en bil. Sätt dig i din bil och titta på instrumentpanelen. Det är ungefär så det är att sitta framför din dator och titta på en instrumentpanel i Power BI. Instrumentpanelen visar allt bilen gör. Den visar motorns rotation, temperaturen, vilken växel som är i, din hastighet, osv.

I Power BI är en datauppsättning som motorn i bilen. Datauppsättningen innehåller data, mått och information som visas i din Power BI-instrumentpanel. Naturligtvis behöver din motor eller datauppsättning bränsle. I Power BI är det bränslet data. Din bil har en bränsletank som ger motorn bränsle. På ett liknande sätt i Power BI, behöver du en bränsletank som har data som du kan mata till din datauppsättning. I vårt fall är den bränsletanken en Power BI Desktop-fil, en Excel-arbetsboksfil eller en .CSV-fil.

Vi kan till och med ta det ett steg längre. En bränsletank i en bil måste fyllas på med bränsle. Bränslet för vår Power BI Desktop-, Excel-, eller .CSV-fil är data från en annan datakälla. Vi hämtar data från en annan datakälla och placerar den i en Excel-, Power BI Desktop- eller .CSV-fil. Om det är en Excel-arbetsbok eller .CSV-fil kan vi manuellt ange rader med data. Eller så vi kan ansluta till en extern datakälla för att fråga och läs in data till vår fil. När vi har en fil med vissa data, kan hämta in den till Power BI som en datauppsättning.

> [!NOTE]
> Data i Excel-arbetsböcker måste vara i en tabell eller i datamodellen för att kunna importeras av Power BI.
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>Det spelar roll vart du sparar filen
**Lokalt** – Om du sparar din fil från Power BI till en lokal enhet på datorn eller en annan plats inom din organisation, kan du *importera* den till Power BI. Filen kommer att finnas kvar på den lokala enheten, så hela filen har i själva verket inte importerats till Power BI. Det som händer är att en ny datauppsättning skapas på din Power BI-webbplats samt att data och i vissa fall datamodellen läses in i datauppsättningen. Om din fil har några rapporter kommer de att visas på Power BI-webbplatsen under Rapporter.

**OneDrive företag**  – om du har OneDrive för företag och du loggar in med samma konto som du använder för Power BI, är detta det mest effektiva sättet att behålla ditt arbete i en Excel-, Power BI Desktop- eller .CSV-fil synkroniserat med din datauppsättning, dina rapporter och dina instrumentpaneler i Power BI. Eftersom både Power BI och OneDrive finns i molnet, ansluter Power BI till din fil på OneDrive ungefär en gång per timme. Om det finns ändringar uppdateras dina datauppsättningar, rapporter och instrumentpaneler i Power BI automatiskt.

**OneDrive – personlig** – Om du sparar filer på ditt eget OneDrive-konto får du många av de fördelar som du får med OneDrive för företag. Den största skillnaden är att när du första gången ansluter till din fil (med Hämta data > Filer > OneDrive – personlig) måste du logga in i OneDrive med ditt Microsoft-konto som vanligtvis skiljer sig från det konto du använder för att logga in i Power BI. När du loggar in i OneDrive med ditt Microsoft-konto, måste du markera alternativet Jag vill förbli inloggad. På så sätt kan Power BI ansluta till din fil ungefär en gång i timmen och kontrollera att din datauppsättning i Power BI är synkroniserad.

**SharePoint-gruppwebbplatser** – Du sparar Power BI Desktop-filer på SharePoint-gruppwebbplatser ungefär på samma sätt som på OneDrive för företag. Den största skillnaden är hur du ansluter till filen från Power BI. Du kan ange en URL eller ansluta till rotmappen.

## <a name="ready-to-get-started"></a>Är du redo att sätta igång?
Se följande artiklar för att lära dig mer om att få din fil till Power BI.

* [Hämta data från Excel-arbetsboksfiler](service-excel-workbook-files.md)
* [Hämta data från Power BI Desktop-filer](service-desktop-files.md)
* [Hämta data från filer med kommaavgränsade värden](service-comma-separated-value-files.md)

