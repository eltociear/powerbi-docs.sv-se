---
title: "Publicera från Power BI Desktop"
description: "Publicera från Power BI Desktop"
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
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1ac80fb4f355ba9199554ceb043cf7e8ff79ce54
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="publish-from-power-bi-desktop"></a>Publicera från Power BI Desktop
När du publicerar en **Power BI Desktop**-fil till **Power BI-tjänsten** publiceras data i modellen och de rapporter som du skapade i **Rapportvyn** till Power BI-arbetsytan. En ny datamängd med samma namn och eventuella rapporter visas i navigatorfältet för arbetsytan.

Publicering från **Power BI Desktop** har samma effekt som att använda **Hämta Data** i Power BI för att ansluta till och ladda upp en **Power BI Desktop**-fil.

> [!NOTE]
> Alla ändringar du gör i rapporten i Power BI, till exempel lägga till, ta bort eller ändra visualiseringar i rapporter, sparas inte i den ursprungliga **Power BI Desktop**-filen.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Så här publicerar du en Power BI Desktop-datauppsättning och rapporter
1. I Power BI Desktop \> **Arkiv** \> **Publicera** \> **Publicera till Power BI** eller klicka på **Publicera**i menyfliksområdet.  
   ![](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)
2. Logga in på Power BI.

När du är klar får du en länk för att öppna rapporten på Power BI-platsen.  
    ![](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Publicera eller ersätta en datamängd som har publicerats från Power BI Desktop
När du publicerar en **Power BI Desktop**-fil överförs datauppsättningen och alla rapporter som du skapade i **Power BI Desktop** till Power BI-platsen. När du publicerar **Power BI Desktop**-filen ersätts datamängden i Power BI-platsen med den uppdaterade datauppsättningen från **Power BI Desktop**-filen.

Detta är ganska tydligt men du bör veta om ett par saker:

* Om du redan har två eller fler datauppsättningar i Power BI med samma namn som **Power BI Desktop**-filen kan publiceringen misslyckas. Kontrollera att du bara har en datauppsättning i Power BI med samma namn. Du kan också byta namn på filen och publicera den, vilket skapar en ny datauppsättning med samma namn som filen.
* Om du byter namn på eller ta bort en kolumn eller ett mått kan alla visualiseringar som du redan har i Power BI med fältet skadas. 
* Power BI ignorerar vissa formatändringar av befintliga kolumner. Till exempel om du ändrar formatet för en kolumn från 0,25 till 25 %.
* Om du har ett uppdateringsschema som har konfigurerats för en befintlig datauppsättning i Power BI och du lägger till nya datakällor i filen och sedan publicerar, måste du logga in till dem i *Hantera datakällor* före nästa schemalagda uppdatering.

