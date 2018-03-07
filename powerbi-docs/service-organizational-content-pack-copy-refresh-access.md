---
title: "Organisationsinnehållspaket: få åtkomst och kopiera"
description: "Läs mer om att skapa kopior av och felsöka åtkomst till organisationsinnehållspaket i Power BI"
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 328edd6f7bc1d7e0e2550eff2c34b97b5fd6442d
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="organizational-content-packs-copy-refresh-and-get-access"></a>Organisationsinnehållspaket: kopiera, uppdatera och få åtkomst
> [!NOTE]
> Har du hört talas om de nya *apparna* ännu? Appar är det nya sättet att distribuera innehåll till stora målgrupper i Power BI. Du skapar appar på *app-arbetsytor*, som ersätter grupper och grupparbetsytor. Vi rekommenderar att du använder appar istället för organisationsinnehållspaket eller skrivskyddade arbetsytor. Läs [mer om appar](service-install-use-apps.md).
> 
> 

När ett organisationsinnehållspaket publiceras, visas alla mottagare samma instrumentpanel, rapporter, Excel-arbetsböcker, datauppsättningar och data (om det inte rör sig om en SQL Server Analysis Services-datakälla).  [Endast innehållspaketets skapare kan redigera och publicera](service-organizational-content-pack-manage-update-delete.md) innehållspaketet.  Alla mottagare kan dock spara en kopia av innehållspaketet som kan existera tillsammans med originalet.

Att skapa innehållspaket skiljer sig från att dela instrumentpaneler eller samarbeta om dem i en grupp. Läs [Hur ska jag samarbeta kring och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md) för att välja det bästa alternativet för din situation.

## <a name="create-a-copy-of-an-organizational-content-pack"></a>Skapa en kopia av ett organisationsinnehållspaket
Skapa din egen kopia av innehållspaketet som inte är synligt för andra.

1. Välj ellipsen (...) bredvid innehållspaketets instrumentpanel > Gör en kopia.
   
    ![](media/service-organizational-content-pack-copy-refresh-access/power-bi-create-copy-organizational-content-pack.png)
2. Välj **Spara**.  

Nu har du en kopia som du kan ändra. Ingen annan kommer att se de ändringar du gör.

## <a name="help--i-can-no-longer-access-the-content-pack"></a>Hjälp!  Jag kan inte längre komma åt innehållspaketet
Detta kan bero på flera orsaker:

* **Medlemskapsändringar**: Innehållspaket publiceras för e-postdistributionsgrupper, säkerhetsgrupper och [Power BI-grupper baserat på Office 365](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9).  Om du har tagits bort från gruppen har du inte längre åtkomst till innehållspaketet.
* **Distributionsändringar**: Innehållspaketets skapare har ändrat distributionen. Om till exempel innehållspaketet ursprungligen publicerades för hela organisationen men skaparen publicerar det på nytt men nu för en mindre målgrupp, kanske du inte längre ingår i den.
* **Säkerhetsinställningar ändras**: Om instrumentpanelen och rapporterna ansluter till lokala SSAS-datakällor och ändringar görs i säkerhetsinställningarna, kan din behörighet till servern återkallas.

## <a name="how-are-organizational-content-packs-refreshed"></a>Hur uppdateras organisationsinnehållspaket?
När innehållspaketet skapas ärvs uppdateringsinställningarna från datauppsättningen.  När du skapar en kopia av innehållspaketet, behåller den nya versionen en länk till den ursprungliga datauppsättningen och dess uppdateringsschema. 

Se [Hantera, uppdatera och ta bort organisationsinnehållspaket](service-organizational-content-pack-manage-update-delete.md).

## <a name="next-steps"></a>Nästa steg
* [Introduktion till organisationsinnehållspaket](service-organizational-content-pack-introduction.md)
* [Skapa en grupp i Power BI](service-create-distribute-apps.md)
* Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

