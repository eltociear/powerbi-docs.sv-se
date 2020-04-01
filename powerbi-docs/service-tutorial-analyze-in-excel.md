---
title: 'Självstudie: Använda Power BI Analysera i Excel med start i Excel'
description: I den här självstudien börjar du i Excel och ansluter till Power BI-sidan Datamängder för att importera datamängder till Excel.
author: tejaskulkarni
ms.reviewer: davidiseminger
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 02/13/2020
ms.author: tekulka
LocalizationGroup: Connect to services
ms.openlocfilehash: 9a8dd1eb7aa6b239cc542884ab3fae3679997017
ms.sourcegitcommit: 3c51431d85793b71f378c4b0b74483dfdd8411b3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/31/2020
ms.locfileid: "80464615"
---
# <a name="tutorial-use-power-bi-analyze-in-excel-starting-in-excel"></a>Självstudie: Använda Power BI Analysera i Excel med start i Excel

Din organisation använder Power BI för att dela åtkomst till data. Du startar Power BI-funktionen Analysera i Excel från Excel för att skapa pivottabeller och pivotdiagram i Excel. De kan ge ytterligare kontext till din analys eller göra att det går snabbare att hitta och importera relevanta datamängder.

Kom igång med en Power BI-datamängd genom att välja ”Analysera i Excel” i Excel. Du får hjälp att skapa en pivottabell som använder dina data.  

Du kan hitta ytterligare datamängder som delas av din organisation genom att gå tillbaka till sidan Datamängder.

Om du får problem på vägen väljer du **Nej** i det aktuella steget i flödet nedan och ger feedback i det länkade formuläret.  

I de här självstudierna får du lära dig att

> [!div class="checklist"]
> * Ladda ned en ODC-fil från sidan Power BI-datamängder.
> * Aktivera åtkomst till din datamängd från Excel.
> * Börja använda datamängder när du vill skapa pivottabeller, diagram eller kalkylblad

## <a name="prerequisites"></a>Förutsättningar

För att slutföra den här kursen behöver du:

* Ett Power BI-konto. Om du inte har registrerat dig för Power BI [registrerar du dig för en kostnadsfri utvärderingsversion](https://app.powerbi.com/signupredirect?pbi_source=web) innan du börjar.

* Bekanta dig med alla de steg som listas i självstudien [Kom igång med Power BI-tjänsten](https://docs.microsoft.com/power-bi/service-get-started).

* Du behöver en Power BI Premium-datamängd och en Power BI Pro-licens. Mer information finns i [Vad är Power BI Premium?](https://docs.microsoft.com/power-bi/service-premium-what-is).

* Du hittar en fullständig lista över alla krav i dokumentet [Analysera i Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#requirements).

* En aktiv [Microsoft Office E5-prenumeration](https://www.microsoft.com/microsoft-365/business/office-365-enterprise-e5-business-software?activetab=pivot%3aoverviewtab)

## <a name="get-started"></a>Kom igång

Börja i Excel, välj alternativet att skapa pivottabeller med delade Power BI-data och navigera till sidan Power BI datamängder.

![Sidan Datamängder](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-01.png)

När du använder arbetsflödet Analysera i Excel får du flera meddelanden som hjälper dig i arbetet. Ange alltid när du har slutfört ett steg i processen innan du fortsätter. Om du stöter på något problem på vägen så välj **Nej** och ge feedback i formuläret.

![Arbetsflödesanvisningar](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-02.png)

## <a name="download-and-open-the-odc-file"></a>Ladda ned och öppna ODC-filen

Välj datamängd från listan och den tillhörande arbetsytan, och klicka sedan på Analysera i Excel. Power BI skapar en ODC-fil och laddar ned den från webbläsaren till din dator.

![Välja datamängd](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-03.png)

När du öppnar filen i Excel, visas en tom pivottabell och fältlista med tabeller, fält och mått från Power BI-datamängden. Du kan skapa pivottabeller och diagram och analysera din datauppsättning precis som om du arbetade med en lokal datauppsättning i Excel.

## <a name="enable-data-connections"></a>Aktivera dataanslutningar

För att kunna analysera Power BI-data i Excel kan det hända att du blir uppmanad om att lita på anslutningen. Administratörer för Power BI-klienter kan inaktivera användningen av Analysera i Excel med lokala datamängder i Analysis Services-databaser från Power Bi-administratörsportalen.

![Aktivera anslutningen](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-04.png)

## <a name="install-updates-and-authenticate"></a>Installera uppdateringar och autentisera

Du kan också behöva autentisera med ditt Power BI-konto första gången som du öppnar en ny ODC-fil.  Om du stöter på några problem kan du ta hjälp av det omfattande dokumentet [Analysera i Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#sign-in-to-power-bi ) om du vill ha mer information eller klicka på Nej under arbetsflödet.

![Aktivera anslutningen](media/service-tutorial-analyze-in-excel/tutorial-analyze-in-excel-05.png)

## <a name="analyze-away"></a>Analysera mera

På samma sätt som med andra lokala arbetsböcker så kan du med hjälp av Analysera i Excel skapa pivottabeller och diagram, lägga till data och skapa olika kalkylblad med vyer av dina data. Analysera i Excel visar alla data på detaljnivå för alla användare med behörighet till datamängden. Du kan spara den här arbetsboken, men inte publicera eller importera den till Power BI eller dela den med andra användare i din organisation. Mer information och andra användningsfall finns i [Analysera i Excel](https://docs.microsoft.com/power-bi/service-analyze-in-excel#analyze-away).

## <a name="clean-up-resources"></a>Rensa resurser

Interaktioner med sidan Power BI-tjänsten och datamängder bör begränsas till att ladda ned ODC-filen och klicka igenom arbetsflödet. Om du har problem med något av dessa steg, så ange **Nej** i det aktuella steget och ge feedback i det länkade formuläret. Formuläret innehåller en länk till mer information om problemet. Gå tillbaka till sidan Datamängder och försök göra om processen eller välj en annan datamängd.

## <a name="next-steps"></a>Nästa steg

Följande artiklar kan också vara av intresse för dig:

* [Använd visning av detaljerad information mellan rapporter i Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-cross-report-drill-through)

* [Använda utsnitt i Power BI Desktop](https://docs.microsoft.com/power-bi/visuals/power-bi-visualization-slicers)
