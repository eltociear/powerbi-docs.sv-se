---
title: Power BI – arkiverad arbetsyta
description: Power BI-arkiverad arbetsyta efter att du hanterat din Office 365-klient
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 254857072df2b06fbdeb2af0a53d262e98f8f254
ms.sourcegitcommit: 8552a34df8e6141eb704314c1a019992901d6e78
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2018
---
# <a name="power-bi-archived-workspace"></a>Power BI – arkiverad arbetsyta
Med Power BI, kan vem som helst registrera sig och börja använda tjänsten inom några minuter.  Senare, kan din organisations IT-avdelning välja att ta över hanteringen av Power BI för användare i din organisation.  Om det övertaget inträffar, får du fördelarna av en central hantering av användare och behörigheter i din organisation och du kan dra nytta av effektiviserad inloggning med samma användarnamn och lösenord som du använder för andra tjänster i din organisation. 

Allt innehåll som du har skapat innan din IT-avdelning började hantera Power BI placeras i en Power BI-arkiverad arbetsyta, som kan nås från navigeringen till vänster i [Power BI](https://app.powerbi.com).  Du bör skapa nytt Power BI-innehåll i min arbetsyta som är skyddad och hanteras av din organisations IT-avdelning.  Din arkiverade arbetsyta kommer att fortsätta finnas, men det finns begränsningar på de åtgärder som du kan utföra på innehållet i din arkiverade arbetsyta.  Om du vill ta bort dessa begränsningar, behöver du migrera innehållet från din arkiverade arbetsyta till min arbetsyta som hanteras av din IT-avdelning.

## <a name="restrictions-in-your-archived-workspace"></a>Begränsningar i din arkiverade arbetsyta
Inget innehåll tas bort från din arkiverade arbetsyta.  Du kan fortsätta att hämta data, skapa rapporter och instrumentpaneler och uppdatera datauppsättningar.  Befintliga användare som du har delat innehåll med kommer fortfarande att kunna visa innehållet i sina arkiverade arbetsytor också.

Det finns dock några begränsningar för innehållet i din arkiverade arbetsyta:

* **OneDrive för företag.  ** Du kommer inte längre att kunna hämta data eller uppdatera från OneDrive för företag för datauppsättningar i din arkiverade arbetsyta.  Om du försöker ansluta till den här källan, får du en varning.
* **Dela instrumentpaneler.  ** Du kan inte dela instrumentpaneler med andra användare från din arkiverade arbetsyta.  Alla användare som redan har tillgång kommer att fortsätta att kunna visa delade instrumentpaneler genom att gå in på sin arkiverade arbetsyta.
* ** Skapa grupper.  ** Du kan inte skapa grupper i din arkiverade arbetsyta.
* **Åtkomst i Power BI-mobilappar.  **Även om du fortfarande kan visas innehåll på webben i din arkiverade arbetsyta, kommer det här innehållet inte längre att visas i Power BI-mobilappar.

## <a name="migrating-content-in-your-archived-workspace"></a>Migrera innehåll i din arkiverade arbetsyta
Om du vill fortsätta att använda Power BI, bör du skapa nytt innehåll i din min arbetsyta som hanteras av din IT-avdelning.   Du bör också planera att migrera allt innehåll i din arkiverade arbetsyta till din min arbetsyta.  Hur du migrerar innehållet beror på vilken typ av innehåll det rör sig om:

* **Datauppsättningar för Excel eller Power BI Desktop.  ** Migrera de här datauppsättningarna genom att växla från din arkiverade arbetsyta till min arbetsyta och ladda upp Excel eller Power BI Desktop-filen igen genom att klicka på knappen mina data.  Om du ställer in schemalagd uppdatering, måste du konfigurera om inställningarna för den nya datauppsättningen i min arbetsyta.
* **Övriga datauppsättningar.  ** Växla till min arbetsyta och klicka sedan på knappen hämta data för att återansluta till andra datauppsättningar som du skapat i din arkiverade arbetsyta.  Du kan behöva ange säkerhets- eller anslutningsinformationen igen.
* **Rapporter.  ** Rapporter som fanns i Excel- eller Power BI Desktop-filer eller rapporter som installerades som en del av innehållspaket, kommer att återskapas automatiskt när du laddar upp motsvarande Excel- eller Power BI Desktop-fil igen eller återansluter till innehållspaketet.  Om du skapade dina egna rapporter via Power BI-tjänsten, behöver du återskapa de rapporterna i din min arbetsyta.
* **Instrumentpaneler.  ** Instrumentpaneler som installeras som en del av innehållspaket, kommer att återskapas automatiskt när du återansluter till innehållspaketet i min arbetsyta.  Om du skapade dina egna instrumentpaneler via Power BI-tjänsten, behöver du återskapa de instrumentpanelerna i din min arbetsyta.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

