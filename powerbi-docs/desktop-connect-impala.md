---
title: Anslut till en Impala-databas i Power BI Desktop
description: "Anslut enkelt till och använd en Impala-databas i Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/06/2017
ms.author: davidi
ms.openlocfilehash: 7b6abc7ee00668e8be305b52235a8c967d0c938e
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Anslut till en Impala-databas i Power BI Desktop
I Power BI Desktop kan du ansluta till en **Impala**-databas och använda underliggande data precis som andra datakällor i Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Anslut till en Impala-databas
Om du vill ansluta till en **Impala**-databas, väljer du **Hämta Data** från **Start**-menyfliksområdet i Power BI Desktop. Välj **Databas** från kategorierna till vänster så ser du **Impala**.

![](media/desktop-connect-impala/connect_impala_2.png)

I **Impala**-fönstret som visas, skriver eller klistrar du in namnet på din Impala-server i rutan och väljer **Ok**. Observera att du kan välja att **importera** data direkt i Power BI, eller så kan du använda **DirectQuery**. Du kan läsa mer om att [använda DirectQuery](desktop-use-directquery.md).

![](media/desktop-connect-impala/connect_impala_3a.png)

När du uppmanas, skriver du in ditt användarnamn och lösenord, eller ansluter anonymt, bägge alternativ stöds.

![](media/desktop-connect-impala/connect_impala_4.png)

> [!NOTE]
> När du anger ditt användarnamn och lösenord för en viss **Impala**-server, använder Power BI Desktop samma autentiseringsuppgifter i efterföljande anslutningsförsök. Du kan ändra autentiseringsuppgifterna genom att gå till **Arkiv > Alternativ och inställningar > Inställningar för datakälla**.
> 
> 

När du har anslutit, visas ett **navigator**-fönster som visar data som är tillgängliga på servern, där du kan välja ett eller flera element att importera och använda i **Power BI Desktop**.

![](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
Det finns några begränsningar och överväganden att tänka på med anslutningsappen för **Impala**:

* Framtida planer inkluderar att aktivera stöd för uppdatering med **Power BI Gateway**.

## <a name="next-steps"></a>Nästa steg
Det finns alla möjliga sorters data du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Komma igång med Power BI Desktop](desktop-getting-started.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

