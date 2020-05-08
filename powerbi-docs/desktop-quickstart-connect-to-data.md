---
title: 'Snabbstart: Anslut till data i Power BI Desktop'
description: Så ansluter du till de datakällor som är tillgängliga i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: quickstart
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: quickstart
ms.openlocfilehash: 5aed52ec232d3e603d69bfe93640187401279ff6
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75885220"
---
# <a name="quickstart-connect-to-data-in-power-bi-desktop"></a>Snabbstart: Anslut till data i Power BI Desktop

I den här snabbstarten ansluter du till data med hjälp av Power BI Desktop, vilket är det första steget när du ska skapa datamodeller och rapporter.

![Power BI Desktop](media/desktop-what-is-desktop/what-is-desktop_01.png)

Om du inte har registrerat dig för Power BI [registrerar du dig för en kostnadsfri utvärderingsversion](https://app.powerbi.com/signupredirect?pbi_source=web) innan du börjar.

## <a name="prerequisites"></a>Förutsättningar

För att slutföra stegen i den här artikeln behöver du följande resurser:

* Ladda ned och installera Power BI Desktop som är ett kostnadsfritt program som körs på den lokala datorn. Du kan [hämta Power BI Desktop](https://powerbi.microsoft.com/desktop) direkt, eller så kan du hämta det från [Microsoft Store](https://aka.ms/pbidesktopstore).
* [Hämta exemplet på en Excel-arbetsbok](https://go.microsoft.com/fwlink/?LinkID=521962) och skapa en mapp med namnet *C:\PBID-qs* där du kan spara Excel-filen. I de senare stegen i snabbstarten förutsätts att detta är sökvägen för den Excel-arbetsbok du laddat ned.
* För många dataanslutningar i Power BI Desktop krävs Internet Explorer 10 (eller senare) för autentisering.

## <a name="launch-power-bi-desktop"></a>Starta Power BI Desktop

När du har installerat Power BI Desktop startar du programmet så att det körs lokalt i datorn. Du ser en självstudie för Power BI. Följ självstudiekursen eller stäng dialogrutan och börja med en tom arbetsyta. Det är på arbetsytan du skapar visuella objekt och rapporter från dina data.

![Power BI Desktop med en tom arbetsyta](media/desktop-quickstart-connect-to-data/qs-connect-data_01.png)

## <a name="connect-to-data"></a>Anslut till data

Med Power BI Desktop kan du ansluta till många olika typer av data. Det kan bland annat vara grundläggande datakällor som en Microsoft Excel-fil. Du kan ansluta till onlinetjänster som innehåller alla möjliga olika typer av data som Salesforce, Microsoft Dynamics, Azure Blob Storage och många andra.

Du kan ansluta till data från **menyfliksområdet** genom att välja **Hämta data**.

![Hämta data i menyfliksområdet Start](media/desktop-quickstart-connect-to-data/qs-connect-data_02.png)

Fönstret **Hämta data** visas. Du kan välja mellan de olika datakällor som Power BI Desktop kan ansluta till. I den här snabbstarten använder du Excel-arbetsboken du laddade ned under [Förutsättningar](#prerequisites).

![Hämta data alla källor](media/desktop-quickstart-connect-to-data/qs-connect-data_03.png)

Eftersom datakällan är en Excel-fil väljer du **Excel** i fönstret **Hämta data** och sedan knappen **Anslut**.

Power BI uppmanar dig att ange var Excel-filen du vill ansluta till finns. Den nedladdade filen heter *Financial Sample*. Markera filen och välj **Öppna**.

![Hämta data i Financial Sample](media/desktop-quickstart-connect-to-data/qs-connect-data_04.png)

Power BI Desktop läser in arbetsboken, läser innehållet och visar tillgängliga data i filen i fönstret **Navigatör**. Där kan du välja vilka data du vill läsa in i Power BI Desktop. Välj tabeller genom att markera kryssrutorna bredvid de tabeller du vill importera. Importera båda de tillgängliga tabellerna.

![Välj data i fönstret Navigatör](media/desktop-quickstart-connect-to-data/qs-connect-data_05.png)

När du har gjort dina val väljer du **Läs in** för att importera dessa data till Power BI Desktop.

## <a name="view-data-in-the-fields-pane"></a>Visa data i fönstret Fält

När du har läst in tabellerna visas dina data i fönstret **Fält**. Du kan expandera tabellerna genom att välja pilen bredvid namnet. I följande bild har *ekonomitabellen* expanderats så att vart och ett av fälten visas.

![Hämta data](media/desktop-quickstart-connect-to-data/qs-connect-data_06.png)

Och sedan är du klar! Du har anslutit till data i Power BI Desktop, läst in dessa data och nu kan du se alla tillgängliga fält i de här tabellerna.

## <a name="next-steps"></a>Nästa steg

Det finns en mängd olika saker du kan göra med Power BI Desktop när du har anslutit till data. Du kan skapa visualiseringar och rapporter. Titta närmare på följande resurs för att komma igång:

* [Kom igång med Power BI Desktop](desktop-getting-started.md)
