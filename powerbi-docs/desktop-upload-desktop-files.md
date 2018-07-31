---
title: Publicera från Power BI Desktop
description: Publicera från Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/17/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: d513c68dba27bb6e37a158eaad4059b24bc8db6a
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34482002"
---
# <a name="publish-from-power-bi-desktop"></a>Publicera från Power BI Desktop
När du publicerar en **Power BI Desktop**-fil till **Power BI-tjänsten** publiceras data i modellen och de rapporter som du skapade i **Rapportvyn** till Power BI-arbetsytan. En ny datamängd med samma namn och eventuella rapporter visas i navigatorfältet för arbetsytan.

Publicering från **Power BI Desktop** har samma effekt som att använda **Hämta Data** i Power BI för att ansluta till och ladda upp en **Power BI Desktop**-fil.

> [!NOTE]
> De ändringar du gör i rapporten i Power BI, till exempel om du lägger till, tar bort eller ändrar visualiseringar i rapporten, sparas inte i den ursprungliga **Power BI Desktop**-filen.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Så här publicerar du en Power BI Desktop-datauppsättning och rapporter
1. I Power BI Desktop \> **Arkiv** \> **Publicera** \> **Publicera till Power BI** eller klicka på **Publicera**i menyfliksområdet.  

   ![Knappen Publicera](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Logga in i Power BI.
3. Välj målet.

   ![Välj publiceringsmålet](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

När du är klar visas en länk till rapporten. Öppna rapporten på din Power BI-plats genom att klicka på länken.

![Dialogruta som anger att publiceringen lyckades](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="re-publish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Publicera eller ersätta en datamängd som har publicerats från Power BI Desktop
När du publicerar en **Power BI Desktop**-fil överförs datauppsättningen och alla rapporter som du skapade i **Power BI Desktop** till Power BI-platsen. När du publicerar **Power BI Desktop**-filen ersätts datamängden i Power BI-platsen med den uppdaterade datauppsättningen från **Power BI Desktop**-filen.

Processen är tydlig, men det finns ett par saker som du bör känna till:

* Om du redan har två eller fler datauppsättningar i Power BI med samma namn som **Power BI Desktop**-filen kan publiceringen misslyckas. Kontrollera att du bara har en datauppsättning i Power BI med samma namn. Du kan också byta namn på filen och publicera den, vilket skapar en ny datauppsättning med samma namn som filen.
* Om du byter namn på eller ta bort en kolumn eller ett mått kan alla visualiseringar som du redan har i Power BI med fältet skadas. 
* Power BI ignorerar vissa formatändringar av befintliga kolumner. Till exempel om du ändrar formatet för en kolumn från 0,25 till 25 %.
* Om du har ett uppdateringsschema som har konfigurerats för en befintlig datauppsättning i Power BI och du lägger till nya datakällor i filen och sedan publicerar, måste du logga in till dem i *Hantera datakällor* före nästa schemalagda uppdatering.

