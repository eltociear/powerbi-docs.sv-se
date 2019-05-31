---
title: Ansluta till en PDF-fil i Power BI Desktop
description: Anslut enkelt till och använd data från PDF-filer i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0c63a62edfce62a5cee13bef3c68014027313e8b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514002"
---
# <a name="connect-to-a-pdf-file-in-power-bi-desktop"></a>Ansluta till en PDF-fil i Power BI Desktop
I Power BI Desktop kan du ansluta till en **PDF-fil** och använda inkluderade data från filen precis som andra datakällor i Power BI Desktop.

![Ansluta till data i PDF-filer](media/desktop-connect-pdf/connect-pdf_04.png)

Följande avsnitt beskriver hur du ansluter till en **PDF-fil**, väljer data och börjar använda dessa data i **Power BI Desktop**.

Vi rekommenderar alltid att du uppgraderar till den senaste versionen av **Power BI Desktop**, som du kan hämta från en länk i avsnittet [Hämta Power BI Desktop](desktop-get-the-desktop.md). 

## <a name="connect-to-a-pdf-file"></a>Ansluta till en PDF-fil
Om du vill ansluta till en **PDF**-fil väljer du **Hämta Data** från **Start**-menyfliksområdet i Power BI Desktop. Välj **Fil** från kategorierna till vänster så ser du **PDF (beta)** .

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

