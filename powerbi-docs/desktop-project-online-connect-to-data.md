---
title: 'Project Online: anslut till data via Power BI Desktop'
description: 'Project Online: anslut till data via Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b0dc84d7b2d8da0df8a9e61a43f35898d197c188
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513768"
---
# <a name="project-online-connect-to-data-through-power-bi-desktop"></a>Project Online: anslut till data via Power BI Desktop
Du kan ansluta till data i Project Online via Power BI Desktop.

## <a name="step-1-download-power-bi-desktop"></a>Steg 1: Ladda ner Power BI Desktop
1. [Ladda ner Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521662), kör sedan installationsprogrammet för att hämta **Power BI Desktop** på din datorn.

## <a name="step-2-connect-to-project-online-with-odata"></a>Steg 2: Anslut till Project Online med OData
1. Öppna **Power BI Desktop**.
2. På *välkomstskärmen* väljer du **Hämta data**.
3. Välj **OData-flöde** och välj **Anslut**.
4. Ange adressen för ditt OData-flöde i URL-rutan och klicka sedan på OK.
   
   Om adressen till din Project Web App-webbplats liknar *https://\<tenantname\>.sharepoint.com/sites/pwa*, så är den adress som du anger för ditt OData-flöde är *https://\<tenantname\>.sharepoint.com/sites/pwa/\_api/Projectdata*.
   
   I det här exemplet använder vi https://contoso.sharepoint.com/sites/pwa/default.aspx
5. Power BI Desktop ber dig att autentisera med ditt Office 365-konto. Välj organisationskonto och ange dina autentiseringsuppgifter.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

Det konto som används för att ansluta till OData-feed måste minst ha åtkomst genom Portföljvyn för Project Web App-webbplatsen. 

Härifrån kan du välja vilka tabeller du vill ansluta till och skapa en fråga.  Vill du ha en uppfattning om hur du kommer igång?  Följande blogginlägg visar hur du skapar en bränna ned diagram från dina Project Online-data.  Blogginlägget refererar till att använda Power Query för att ansluta till Project Online, men detta gäller även för Power BI Desktop.

[Skapa bränna ned diagram för projekt med hjälp av Power Pivot och Power Query](http://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

