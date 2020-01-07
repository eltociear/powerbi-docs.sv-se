---
title: 'Snabbstart: ansluta till data'
description: Anslut till en datakälla i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 1366a5281a36293a484f08c12ab9f8891e29123d
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2020
ms.locfileid: "73876218"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Snabbstart: Ansluta till datakällor i Power BI Desktop

I den här snabbstarten ansluter du till data med hjälp av **Power BI Desktop**, vilket är det första steget för att skapa datamodeller och rapporter.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Om du inte har registrerat dig för Power BI [registrerar du dig för en kostnadsfri utvärderingsversion](https://app.powerbi.com/signupredirect?pbi_source=web) innan du börjar.

## <a name="prerequisites"></a>Förutsättningar

För att slutföra stegen i den här artikeln behöver du följande:
* Hämta och installera **Power BI Desktop**, som är ett kostnadsfritt program som körs på den lokala datorn. Du kan [hämta **Power BI Desktop**](https://powerbi.microsoft.com/desktop) direkt eller så kan du hämta det från [**Microsoft Store**](https://aka.ms/pbidesktopstore).
* [Hämta exemplet på en Excel-arbetsbok](https://go.microsoft.com/fwlink/?LinkID=521962) och skapa en mapp med namnet *C:\PBID-qs* där du kan spara Excel-filen. Efterföljande steg i den här snabbstarten förutsätter att detta är sökvägen för den hämta Excel-arbetsboken.

## <a name="launch-power-bi-desktop"></a>Starta Power BI Desktop

När du har installerat **Power BI Desktop** startar du programmet så att det körs på den lokala datorn. Du ser en självstudie för Power BI. Gå igenom självstudien eller klicka bort den och börja med en tom arbetsyta, där du kan skapa visuella objekt och rapporter från data som du ansluter till. 

![Power BI Desktop – tom arbetsyta](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Ansluta till data

Med **Power BI Desktop** kan du ansluta till många olika typer av data. Du kan ansluta till grundläggande datakällor som en Microsoft Excel-fil och du kan ansluta till onlinetjänster som innehåller alla möjliga olika typer av data som Salesforce, Microsoft Dynamics, Azure Blob Storage och många andra.

Du kan ansluta till data från **menyfliksområdet** genom att välja **Hämta data**.

![Hämta data](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Fönstret **Hämta data** visas, där du kan välja mellan de olika datakällor som **Power BI Desktop** kan ansluta till. I den här snabbstarten använder vi den Excel-arbetsbok som du hämtade och som beskrivs i avsnittet *Förutsättningar* i början av den här artikeln.

![Hämta data](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Eftersom det här är en Excel-fil, väljer vi **Excel** i fönstret **Hämta data** och väljer sedan knappen **Anslut**.

Vi uppmanas att ange platsen för Excel-filen som vi vill ansluta till. Den hämtade filen heter *Finansiellt exempel*. Vi markerar filen och väljer sedan **Öppna**.

![Hämta data](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

**Power BI Desktop** läser sedan in arbetsboken och läser innehållet och visar tillgängliga data i filen med fönstret **Navigatör** där du kan välja vilka data som du vill läsa in till Power BI Desktop. Du markerar tabellerna genom att markera kryssrutorna bredvid varje tabell som du vill importera. I det här fallet ska vi importera båda de tillgängliga tabellerna.

![Hämta data](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

När du har gjort dina val väljer du **Läs in** för att importera dessa data till Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Visa data i fönstret Fält

När du har läst in tabellerna visas dina data i fönstret **Fält**. Du kan expandera varje tabell genom att välja triangeln bredvid dess namn. I följande bild har *ekonomitabellen* expanderats så att vart och ett av fälten visas. 

![Hämta data](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Och sedan är du klar! Du har anslutit till data i **Power BI Desktop**, läst in dessa data och nu kan du se alla tillgängliga fält i de här tabellerna.

## <a name="next-steps"></a>Nästa steg

Det finns en mängd olika saker du kan göra med **Power BI Desktop** när du har anslutit till data, till exempel skapa visuella objekt och rapporter. Titta närmare på följande resurs för att komma igång:

* [Guiden Komma igång för Power BI Desktop](desktop-getting-started.md)
