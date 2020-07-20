---
title: 'Project Online: anslut till data via Power BI Desktop'
description: 'Project Online: Ansluta till data via Power BI Desktop'
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 04/01/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 807ba59066508d063dba2e2f921eff19cf018bc5
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214598"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>Ansluta till Project Online-data via Power BI Desktop
Du kan ansluta till data i Project Online via Power BI Desktop.

## <a name="step-1-download-power-bi-desktop"></a>Steg 1: Ladda ner Power BI Desktop
1. [Ladda ner Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521662), kör sedan installationsprogrammet för att hämta **Power BI Desktop** på din datorn.

## <a name="step-2-connect-to-project-online-with-odata"></a>Steg 2: Anslut till Project Online med OData
1. Öppna **Power BI Desktop**.
2. På *välkomstskärmen* väljer du **Hämta data**.
3. Välj **OData-flöde** och välj **Anslut**.
4. Ange adressen för ditt OData-flöde i URL-rutan och klicka sedan på OK.
   
   Om adressen till Project Web App-webbplatsen liknar *https://\<tenantname\>.sharepoint.com/sites/pwa* så blir den adress du anger för OData-flödet *https://\<tenantname\>.sharepoint.com/sites/pwa\_api/Projectdata*.
   
   I det här exemplet använder vi:

    `https://contoso.sharepoint.com/sites/pwa/default.aspx`

5. Power BI Desktop ber dig att autentisera med ditt arbets- eller skolkonto. Välj organisationskonto och ange dina autentiseringsuppgifter.
   
   ![Skärmbild av Power BI Desktop som visar uppmaningen att ange autentiseringsuppgifter för att ansluta.](media/desktop-project-online-connect-to-data/image.png)

Det konto som du använder för att ansluta till OData-flödet måste minst ha åtkomst genom portföljvyn för Project Web App-webbplatsen. 

Härifrån kan du välja vilka tabeller du vill ansluta till och skapa en fråga.  Vill du ha en uppfattning om hur du kommer igång?  Följande blogginlägg visar hur du skapar ett burndown-diagram från dina Project Online-data.  Blogginlägget refererar till att använda Power Query för att ansluta till Project Online, men detta gäller även för Power BI Desktop.

[Skapa burndown-diagram för projekt med hjälp av Power Pivot och Power Query](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

