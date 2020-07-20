---
title: Hantera datalagring i dina arbetsytor
description: Läs hur du hanterar datalagring individuellt eller på arbetsytan för att se till att du kan fortsätta publicera rapporter och datamängder.
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 02/25/2020
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: 50d3adef65791c3fecd1a2125f67318fb8ab0298
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86214254"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Hantera datalagring i Power BI-arbetsytor

Läs hur du hanterar datalagring individuellt eller på arbetsytan så att du kan fortsätta publicera rapporter och datamängder.

## <a name="capacity-limits"></a>Kapacitetsbegränsningar

Lagringsgränser för arbetsytan, vare sig det gäller min arbetsyta eller en apparbetsyta, beror på om arbetsytan har [delad eller premiumkapacitet](../fundamentals/service-basic-concepts.md#capacities).

### <a name="shared-capacity-limits"></a>Begränsningar för delad kapacitet
För arbetsytor i delad kapacitet: 

- Det finns en lagringsgräns per arbetsyta på 100 GB.
- För app-arbetsytor får den totala användningen inte överskrida klientlagringsgränsen på 10 GB multiplicerat med antalet Pro-licenser i klienten.

### <a name="premium-capacity-limits"></a>Begränsningar för premiumkapacitet
För arbetsytor med premiumkapacitet:
- Det finns en gräns på 100 TB per Premium-kapacitet.
- Det finns ingen lagringsgräns per användare.

Läs om andra funktioner i [Power BI-prismodellen](https://powerbi.microsoft.com/pricing).

## <a name="whats-included-in-storage"></a>Vad som ingår i lagringen

Din datalagring inkluderar dina egna datauppsättningar och Excel-rapporter och de objekt som någon har delat med dig. Datauppsättningar är alla datakällor du har laddat upp eller anslutit till. Dessa datakällor omfattar Power BI Desktop-filer och Excel-arbetsböcker du använder. Följande ingår även i din datakapacitet.

* Excel-intervall fästa på en instrumentpanel.
* Reporting Services lokala visualiseringar fästa på en Power BI-instrumentpanel.
* Överförda bilder.

Storleken på en instrumentpanel som du delar varierar beroende på vad som är fäst på den. Om du till exempel fäster objekt från två rapporter som ingår i två olika datauppsättningar, kommer storleken att inkludera bägge datauppsättningarna.

## <a name="manage-items-you-own"></a>Hantera objekt du äger

Se hur mycket lagringsutrymme du använder i ditt Power BI-konto och hantera ditt konto.

1. Om du vill hantera din lagring går du till **Min arbetsyta** i navigeringsfönstret.
   
    ![Skärmbild av navigeringsfönstret med Min arbetsyta framhävd.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)

2. Välj kugghjulsikonen uppe till höger ![kugghjulsikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) **Hantera personlig lagring**.
   
    Det översta fältet visar hur mycket av din lagringsgräns som du har använt.
   
    ![Skärmbild av Hantera lagring som visar hur mycket lagringsutrymme som används.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Datauppsättningarna och rapporterna avgränsas på två flikar:
   
    **Ägs av mig:** Du har laddat upp dessa rapporter och datauppsättningar till ditt Power BI-konto, inklusive tjänstedatauppsättningar som Salesforce och Dynamics CRM.  

    **Ägs av andra:** Andra har delat dessa rapporter och datauppsättningar med dig.
1. Om du vill ta bort en datauppsättning eller rapport, väljer du papperskorgsikonen ![papperskorgsikonen](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Tänk på att du eller någon annan kan ha rapporter och instrumentpaneler baserade på en datauppsättning. Om du tar bort datauppsättningen, fungerar dessa rapporter och instrumentpaneler inte längre.

## <a name="manage-your-workspace"></a>Hantera din arbetsyta
1. Välj pilen bredvid **Arbetsytor** och välj namnet på arbetsytan.
   
    ![Skärmbild av Arbetsytor med arbetsytan Säljgrupp.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Välj kugghjulsikonen uppe till höger ![kugghjulsikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) **Hantera grupplagring**.
   
    Det översta fältet visar hur mycket av din lagringsgräns som du har använt.
   
    ![Skärmbild av Hantera lagring som visar hur mycket lagringsutrymme som används för Säljgrupp.](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Datauppsättningarna och rapporterna avgränsas på två flikar:
   
    **Ägs av oss:** Du eller någon annan har laddat upp dessa rapporter och datauppsättningar till gruppens Power BI-konto, inklusive tjänstedatauppsättningar som Salesforce och Dynamics CRM.

    **Ägs av andra:** Andra har delat dessa rapporter och datauppsättningar med din grupp.

3. Om du vill ta bort en datauppsättning eller rapport, väljer du papperskorgsikonen ![papperskorgsikonen](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Tänk på att du eller någon annan i gruppen kan ha rapporter och instrumentpaneler baserade på en datauppsättning. Om du tar bort datauppsättningen, fungerar dessa rapporter och instrumentpaneler inte längre.
   
   Alla medlemmar i en arbetsyta med rollen administratör, medlem eller deltagare har behörighet att ta bort datamängder och rapporter från arbetsytan.

## <a name="dataset-limits"></a>Datauppsättningsgränser
Det finns en gräns på 1 GB, per datauppsättning som importeras till Power BI. Om du har valt att behålla Excel-upplevelsen istället för att importera data, är gränsen 250 MB för datauppsättningen.

## <a name="what-happens-when-you-reach-a-limit"></a>Vad händer när du når en gräns?
När du når datakapacitetsgränsen för vad du kan göra, får du meddelanden i tjänsten. 

När du väljer kugghjulsikonen ![Kugghjulsikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), ser du ett rött streck som anger att du har överskridit din datakapacitetsgräns.

![Skärmbild av lagringskapaciteten som visar att gränsen har uppnåtts.](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Den här gränsen visas också i **Hantera personlig lagring**.

 ![Skärmbild av den personliga lagringskapaciteten som visar att Janes gräns har uppnåtts.](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 När du försöker utföra en åtgärd som når någon av gränserna visas ett meddelande om att du är över gränsen. Du kan [hantera din lagring](#manage-items-you-own) för att minska ditt lagringsutrymme och komma förbi gränsen.

 ![Skärmbild av dialogrutan Över din lagringsgräns som visar att gränser har uppnåtts.](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 ## <a name="next-steps"></a>Nästa steg

 Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
