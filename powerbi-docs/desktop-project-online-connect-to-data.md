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
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a1f55d09de68d5ac29b81c72f3b1dc6cf98c1597
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54289956"
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
   
   Om adressen till din Project Web App-webbplats liknar https://\<tenantname\>.sharepoint.com/sites/pwa, är adressen du ska ange för ditt OData-flöde https://\<tenantname\>.sharepoint.com/sites/ pwa/\_api/Projectdata.
   
   I det här exemplet använder vi https://contoso.sharepoint.com/sites/pwa/default.aspx
5. Power BI Desktop ber dig att autentisera med ditt Office 365-konto. Välj organisationskonto och ange dina autentiseringsuppgifter.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

Observera att det konto som du använder för att ansluta till OData-flödet som minst måste ha åtkomst genom portföljvyn för Project Web App-webbplatsen. 

Härifrån kan du välja vilka tabeller du vill ansluta till och skapa en fråga.  Vill du ha en uppfattning om hur du kommer igång?  Följande blogginlägg visar hur du skapar ett burndown-diagram från dina Project Online-data.  Blogginlägget refererar till att använda Power Query för att ansluta till Project Online, men detta gäller även för Power BI Desktop.

[Skapa burndown-diagram för projekt med Power Pivot och Power Query](http://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

