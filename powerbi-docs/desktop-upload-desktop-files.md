---
title: Publicera från Power BI Desktop
description: Publicera från Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 3a67c36b2594696e1c576693cc5808eb0227c1c7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76709631"
---
# <a name="publish-datasets-and-reports-from-power-bi-desktop"></a>Publicera datamängder och rapporter från Power BI Desktop
När du publicerar en Power BI Desktop-fil till Power BI-tjänsten publicerar du data i modellen till din Power BI-arbetsyta. Samma sak gäller för alla rapporter som du har skapat i **rapportvyn**. En ny datamängd med samma namn och eventuella rapporter visas i navigatorfältet för arbetsytan.

Publicering från Power BI Desktop har samma effekt som när du använder **Hämta data** i Power BI för att ansluta till och ladda upp en Power BI Desktop-fil.

> [!NOTE]
> Eventuella ändringar som du gör i rapporten i Power BI sparas inte i den ursprungliga Power BI Desktop-filen. Detta gäller även när du lägger till, tar bort eller ändrar visualiseringar i rapporter.
> 
> 

## <a name="to-publish-a-power-bi-desktop-dataset-and-reports"></a>Så här publicerar du en Power BI Desktop-datauppsättning och rapporter
1. I Power BI Desktop väljer du **Arkiv** \> **Publicera** \> **Publicera till Power BI**, eller väljer **Publicera** i menyfliksområdet.  

   ![Knappen Publicera](media/desktop-upload-desktop-files/pbid_publish_publishbutton.png)

2. Logga in på Power BI.
3. Välj målet.

   ![Välj publiceringsmålet](media/desktop-upload-desktop-files/pbid_publish_select_destination.png)

När publiceringen är klar visas en länk till rapporten. Öppna rapporten på din Power BI-plats genom att välja länken.

![Dialogruta som anger att publiceringen lyckades](media/desktop-upload-desktop-files/pbid_publish_success.png)

## <a name="republish-or-replace-a-dataset-published-from-power-bi-desktop"></a>Publicera på nytt eller ersätta en datauppsättning som har publicerats från Power BI Desktop
Datauppsättningen och alla rapporter som du har skapat i Power BI Desktop överförs till Power BI-platsen när du publicerar en Power BI Desktop-fil. När du publicerar Power BI Desktop-filen på nytt ersätts datamängden i Power BI-platsen med den uppdaterade datauppsättningen från Power BI Desktop-filen.

Processen är tydlig, men det finns ett par saker som du bör känna till:

* Om två eller fler datauppsättningar i Power BI har samma namn som Power BI Desktop-filen kan publiceringen misslyckas. Kontrollera att du bara har en datauppsättning i Power BI med samma namn. Du kan också byta namn på filen och publicera den, vilket skapar en ny datauppsättning med samma namn som filen.
* Om du byter namn på eller ta bort en kolumn eller ett mått kan alla visualiseringar som du redan har i Power BI med fältet skadas. 
* Power BI ignorerar vissa formatändringar av befintliga kolumner. Till exempel om du ändrar formatet för en kolumn från 0,25 % till 25 %.
* Anta att du har ett uppdateringsschema som har konfigurerats för din befintliga datauppsättning i Power BI. När du lägger till nya datakällor i filen och sedan publicerar på nytt måste du logga in på dem före nästa schemalagda uppdatering.
* När du återpublicerar en datauppsättning som har publicerats från Power BI Desktop och har ett definierat uppdateringsschema, startas en uppdatering av datauppsättningen så snart du publicerar igen. 

