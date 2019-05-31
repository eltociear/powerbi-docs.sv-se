---
title: Ansluta till en Amazon Redshift-databas i Power BI Desktop
description: Anslut enkelt till en Amazon Redshift-databas i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b92935bb9f4b9ad3738151cb2f671af96283f625
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513625"
---
# <a name="connect-to-amazon-redshift-in-power-bi-desktop"></a>Ansluta till Amazon Redshift i Power BI Desktop
I **Power BI Desktop** kan du ansluta till en **Amazon Redshift**-databas och använda underliggande data precis som andra datakällor i Power BI Desktop.

## <a name="connect-to-an-amazon-redshift-database"></a>Ansluta till en Amazon Redshift-databas
Om du vill ansluta till en **Amazon Redshift**-databas, väljer du **Hämta data** från **Start**-menyfliksområdet i Power BI Desktop. Välj **Databas** från kategorierna till vänster så ser du **Amazon Redshift**.

![](media/desktop-connect-redshift/connect_redshift_3.png)

I fönstret **Amazon Redshift** som visas skriver eller klistrar du inte namnet på din **Amazon Redshift**-server och -databas i rutan. Som en del av fältet *Server* kan användarna ange en port i följande format: *ServerURL:Port*

![](media/desktop-connect-redshift/connect_redshift_4.png)

När du uppmanas, ange ditt användarnamn och lösenord. Använd servernamnet som exakt matchar SSL-certifikatet för att undvika fel. 

![](media/desktop-connect-redshift/connect_redshift_5.png)

När du har anslutit, visas ett **navigator**-fönster som visar data som är tillgängliga på servern, där du kan välja ett eller flera element att importera och använda i **Power BI Desktop**.

![](media/desktop-connect-redshift/connect_redshift_6.png)

När du väljer från fönstret **Navigator** kan du antingen **Hämta** eller **Redigera** data.

* Om du väljer att **Hämta** data får du en fråga om du vill använda läget *Importera* eller *DirectQuery* för att läsa in data. Mer information finns i den här [artikeln som förklarar DirectQuery](desktop-use-directquery.md).
* Om du väljer att **Redigera** data, visas **Frågeredigeraren** där du kan använda alla typer av omvandlingar och filter för data som tillämpas på den underliggande **Amazon Redshift** databasen (om detta stöds).

## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

