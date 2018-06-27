---
title: 'Organisationsinnehållspaket: få åtkomst och kopiera'
description: Läs mer om att skapa kopior av och felsöka åtkomst till organisationsinnehållspaket i Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ajayan
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/08/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: c2d7a878189542d8a477933f6c54390b2636787e
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34852243"
---
# <a name="organizational-content-packs-copy-refresh-and-get-access"></a>Organisationsinnehållspaket: kopiera, uppdatera och få åtkomst
> [!NOTE]
> Har du hört talas om de nya *apparna* ännu? Appar är det nya sättet att distribuera innehåll till stora målgrupper i Power BI. Eftersom organisationsinnehållspaket kommer att tas ur bruk inom kort rekommenderar vi att du använder appar i stället. Läs [mer om appar](service-install-use-apps.md).
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

