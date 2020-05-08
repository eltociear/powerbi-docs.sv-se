---
title: Skapa en rapport för en SharePoint-lista
description: Den här självstudien visar hur du omvandlar dina SharePoint-listdata till en Power BI-rapport.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 01/10/2020
ms.author: davidi
LocalizationGroup: Visualizations
ms.openlocfilehash: 4fd350ae5d4a916e6753f7cd66e1fca52137efd5
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "75925645"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>Skapa en rapport för en SharePoint-lista

Många team och organisationer använder listor i SharePoint Online för att lagra data eftersom det är enkelt att konfigurera och enkelt för användare att uppdatera.  Ibland är det mycket enklare för användarna att förstå data i ett diagram i stället för att titta på själva listan. Den här självstudien visar hur du omvandlar dina SharePoint-listdata till en Power BI-rapport.

Titta på den här fem minuter långa självstudievideon, eller rulla nedåt om du vill se stegvisa instruktioner.

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>Del 1: Anslut till din SharePoint-lista

1. Ladda ned och installera [Power BI Desktop](https://powerbi.microsoft.com/desktop/), om du inte redan har gjort det.
2. Öppna Power BI Desktop, välj Start-fliken i menyfliksområdet och välj **Hämta data** > **Mer**.
3. Välj **Online Services**och välj sedan **SharePoint Online-lista**.  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="get data" width="350"/>

4. Välj **Anslut**.
4. Hitta adressen (kallas även URL) för SharePoint Online-webbplatsen som innehåller listan.  På en sida i SharePoint Online kan du vanligtvis få webbplatsadressen genom att välja **Start** i navigeringsfönstret eller ikonen för webbplatsen längst upp och sedan kopiera adressen från webbläsarens adressfält.

   Titta på en video om det här steget:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. I Power BI Desktop klistrar du in adressen i fältet **Webbplats-URL** i dialogrutan.

6. Det är inte säkert att du ser SharePoint-åtkomstskärmen på följande bild.  Om du inte ser den går du vidare till steg 10.  Om du ser den väljer du **Microsoft-konto** till vänster på sidan.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. Välj **Logga in** och ange det användarnamn och lösenord som du använder för att logga in på Microsoft Office 365.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. När du har loggat in väljer du **Anslut**.

9. Till vänster i navigatorn markerar du kryssrutan bredvid den SharePoint-lista som du vill ansluta till.

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="get data" width="450"/>

10. Välj **Läs in**.  Power BI läser in dina listdata i en ny rapport.

## <a name="part-2-create-a-report"></a>Del 2: Skapa en rapport

1. Till vänster väljer du ikonen **Data** för att bekräfta att dina SharePoint-listdata har lästs in.

2. Kontrollera att listkolumnerna visar ikonen för summa, eller sigma, i **fältpanelen** till höger.  För de kolumner som inte gör det väljer du kolumnrubriken i tabellvyn, väljer fliken **Modellering** och ändrar **Datatyp** till **Decimaltal** eller **Heltal**, beroende på dina data.  Om du uppmanas att bekräfta ändringen väljer du **Ja**.  Om ditt tal är ett specialformat, till exempel valuta, kan du också välja det genom att ange **Format**.

   Titta på en video om det här steget:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. Välj ikonen **Rapport** till vänster.
4. Markera de kolumner som du vill visualisera genom att markera kryssrutan bredvid dem i **fältpanelen** till höger.

   Titta på en video om det här steget:
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. Ändra visuell typ om det behövs.
6. Du kan skapa flera visualiseringar i samma rapport genom att avmarkera det befintliga visuella objektet och sedan markera kryssrutorna för andra kolumner i **fältpanelen**.
7. Välj **Spara** för att spara rapporten.
