---
title: Power BI – arkiverad arbetsyta
description: Power BI-arkiverad arbetsyta efter att du hanterat din Office 365-klient
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8636ec85cb56e87f28a93f9f1f89989ffcc097bb
ms.sourcegitcommit: d20f74d5300197a0930eeb7db586c6a90403aabc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2018
ms.locfileid: "50973153"
---
# <a name="power-bi-archived-workspace"></a>Power BI – arkiverad arbetsyta

Med Power BI, kan vem som helst registrera sig och börja använda tjänsten inom några minuter.  Senare kan din organisations IT-avdelning välja att ta över hanteringen av Power BI för användare i din organisation.  Om detta inträffar kan du dra nytta av central hantering av användare och behörigheter i din organisation. Du kanske också kan dra nytta av effektiviserad inloggning med samma användarnamn och lösenord för andra tjänster i din organisation.

Allt innehåll som du har skapat innan din IT-avdelning började hantera Power BI placeras i en Power BI-arkiverad arbetsyta, som kan nås från navigeringen till vänster i [Power BI](https://app.powerbi.com). Du bör skapa nytt Power BI-innehåll i min arbetsyta som är skyddad och hanteras av din organisations IT-avdelning.  Din arkiverade arbetsyta kommer att fortsätta finnas, men det finns begränsningar på de åtgärder som du kan utföra på innehållet i din arkiverade arbetsyta.  Om du vill ta bort dessa begränsningar, behöver du migrera innehållet från din arkiverade arbetsyta till min arbetsyta som hanteras av din IT-avdelning.

## <a name="restrictions-in-your-archived-workspace"></a>Begränsningar i din arkiverade arbetsyta

Power BI kommer inte att ta bort innehållet från din arkiverade arbetsyta. Du kan fortsätta att hämta data, skapa rapporter och instrumentpaneler och uppdatera datauppsättningar. Befintliga användare som du har delat innehåll med kommer fortfarande att kunna visa innehållet i sina arkiverade arbetsytor också. Det finns dock några begränsningar för innehållet i din arkiverade arbetsyta:

* **OneDrive för företag**: Du kommer inte längre att kunna hämta data eller uppdatera från OneDrive för företag för datauppsättningar i din arkiverade arbetsyta.  Om du försöker ansluta till den här källan, får du en varning.

* **Dela instrumentpaneler**: Du kan inte dela instrumentpaneler med andra användare från din arkiverade arbetsyta.  Alla användare som redan har tillgång kommer att fortsätta att kunna visa delade instrumentpaneler genom att gå in på sin arkiverade arbetsyta.

* **Skapa grupper**: Du kan inte skapa grupper i din arkiverade arbetsyta.

* **Åtkomst till mobilappar på Power BI**: Även om du fortfarande kan visas innehåll på webben i din arkiverade arbetsyta, kommer det här innehållet inte längre att visas i Power BI-mobilappar.

## <a name="migrating-content-in-your-archived-workspace"></a>Migrera innehåll i din arkiverade arbetsyta

Om du vill använda Power BI bör du skapa nytt innehåll i Min arbetsyta. Du bör också planera att migrera allt innehåll i din arkiverade arbetsyta till Min arbetsyta.  Hur du migrerar innehållet beror på vilken typ av innehåll det rör sig om:

* **Excel eller Power BI Desktop-datauppsättningar**: Migrera de här datauppsättningarna genom att växla från din arkiverade arbetsyta till min arbetsyta och ladda upp Excel eller Power BI Desktop-filen igen genom att välja knappen **Mina data**.  Om du ställer in schemalagd uppdatering, måste du konfigurera om inställningarna för den nya datauppsättningen i min arbetsyta.

* **Andra datauppsättningar**: Växla till min arbetsyta och välj sedan knappen **hämta data** för att återansluta till andra datauppsättningar som du skapat i din arkiverade arbetsyta.  Du kan behöva ange säkerhets- eller anslutningsinformationen igen.

* **Rapporter**: rapporter som finns i Excel- eller Power BI Desktop-filer återskapas automatiskt när du överför motsvarande Excel- eller Power BI Desktop-fil. Rapporter som installeras som en del av ett innehållspaket återskapas också när du återansluter till innehållspaketet. Om du skapade dina egna rapporter via Power BI-tjänsten behöver du återskapa de rapporterna i din Min arbetsyta.

* **Instrumentpaneler**: Instrumentpaneler som installeras som en del av innehållspaket återskapas automatiskt när du återansluter till innehållspaketet i min arbetsyta. Om du skapade dina egna instrumentpaneler via Power BI-tjänsten behöver du återskapa de instrumentpanelerna i Min arbetsyta.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

