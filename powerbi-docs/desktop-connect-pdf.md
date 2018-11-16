---
title: Ansluta till en PDF-fil i Power BI Desktop (förhandsversion)
description: Anslut enkelt till och använd data från PDF-filer i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/13/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 2ecd4b8e6295431f520dea61454bbf868bfab254
ms.sourcegitcommit: 6a6f552810a596e1000a02c8d144731ede59c0c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51619688"
---
# <a name="connect-to-a-pdf-file-in-power-bi-desktop-preview"></a>Ansluta till en PDF-fil i Power BI Desktop (förhandsversion)
I Power BI Desktop kan du ansluta till en **PDF-fil** och använda inkluderade data från filen precis som andra datakällor i Power BI Desktop.

![Ansluta till data i PDF-filer](media/desktop-connect-pdf/connect-pdf_04.png)

Följande avsnitt beskriver hur du ansluter till en **PDF-fil**, väljer data och börjar använda dessa data i **Power BI Desktop**.

## <a name="enable-the-pdf-connector"></a>Aktivera PDF-anslutningsappen
PDF-anslutningsappen är en förhandsversion för **Power BI Desktop** och måste aktiveras. Aktivera PDF-anslutningsappen genom att välja **Arkiv > Alternativ och inställningar > Alternativ > Förhandsversionsfunktioner** och markera kryssrutan bredvid **Hämta data från PDF-filer**. 

![Aktivera PDF-anslutningsappen från Alternativ > Förhandsgranskningsfunktioner](media/desktop-connect-pdf/connect-pdf_01.png)

Du måste starta om **Power BI Desktop** när du har gjort valet.

När du använder **PDF (beta)**-anslutningsappen får du en varning om att PDF-anslutningsappen fortfarande är under utveckling och att den kan ändras i framtiden. Välj **Fortsätt** om du vill använda anslutningsappen.

Vi rekommenderar alltid att du uppgraderar till den senaste versionen av **Power BI Desktop**, som du kan hämta från en länk i avsnittet [Hämta Power BI Desktop](desktop-get-the-desktop.md). 

## <a name="connect-to-a-pdf-file"></a>Ansluta till en PDF-fil
Om du vill ansluta till en **PDF**-fil väljer du **Hämta Data** från **Start**-menyfliksområdet i Power BI Desktop. Välj **Fil** från kategorierna till vänster så ser du **PDF (beta)**.

![Välj PDF från Hämta data](media/desktop-connect-pdf/connect-pdf_01.png)

Du uppmanas att ange platsen för PDF-filen som du vill använda. När du anger filens sökväg och PDF-filen läses in så visas ett **navigeringsfönster** med data som är tillgängliga från filen, där du kan välja ett eller flera element att importera och använda i **Power BI Desktop**.

![Ansluta till data i PDF-filer](media/desktop-connect-pdf/connect-pdf_04.png)

Om du markerar en kryssruta bredvid de identifierade elementen i PDF-filen visas de i den högra rutan. När du vill importera väljer du knappen **Läs in** för att importera data till **Power BI Desktop**.

Från och med November 2018-versionen av **Power BI Desktop** så kan du ange **Start page** och **End page** som valfria parametrar för PDF-anslutningen. Du kan även ange dessa parametrar i M-formelspråket, med följande format:

`Pdf.Tables(File.Contents("c:\sample.pdf"), [StartPage=10, EndPage=11])`


## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

