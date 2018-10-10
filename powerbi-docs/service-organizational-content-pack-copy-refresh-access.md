---
title: 'Organisationsinnehållspaket: få åtkomst och kopiera'
description: Läs mer om att skapa kopior av och felsöka åtkomst till organisationsinnehållspaket i Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/02/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 37cfca811b7e60bde832396e67b246933d4e0a8e
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/10/2018
ms.locfileid: "48908427"
---
# <a name="organizational-content-packs-copy-refresh-and-get-access"></a>Organisationsinnehållspaket: kopiera, uppdatera och få åtkomst

När ett organisationsinnehållspaket publiceras, visas alla mottagare samma instrumentpanel, rapporter, Excel-arbetsböcker, datauppsättningar och data (om det inte rör sig om en SQL Server Analysis Services-datakälla).  [Endast innehållspaketets skapare kan redigera och publicera](service-organizational-content-pack-manage-update-delete.md) innehållspaketet.  Alla mottagare kan dock spara en kopia av innehållspaketet som kan existera tillsammans med originalet.

Att skapa innehållspaket skiljer sig från att dela instrumentpaneler eller samarbeta om dem i en grupp. Läs [Hur ska jag samarbeta kring och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md) för att välja det bästa alternativet för din situation.

> [!NOTE]
> Du kan inte skapa eller installera innehållspaket för organisationen i förhandsversionen för den nya arbetsytan. Nu är ett bra tillfälle att uppgradera dina innehållspaket till appar, om du inte har börjat ännu. Lär dig [mer om den nya arbetsytan](service-create-the-new-workspaces.md).
> 

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

