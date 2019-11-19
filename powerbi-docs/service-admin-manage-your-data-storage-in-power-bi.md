---
title: Hantera datalagring i dina arbetsytor
description: Läs hur du hanterar datalagring individuellt eller på arbetsytan för att se till att du kan fortsätta publicera rapporter och datamängder.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: ea187de55eec2667abe2eed017481180910b7619
ms.sourcegitcommit: 8cc2b7510aae76c0334df6f495752e143a5851c4
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73431383"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Hantera datalagring i Power BI-arbetsytor

Läs hur du hanterar datalagring individuellt eller på arbetsytan för att se till att du kan fortsätta publicera rapporter och datamängder.

Användare och arbetsytor har egna datakapaciteter:

* Alla användare har upp till 10 GB datalagring.
* Användare med en Power BI Pro-licens kan skapa arbetsytor med upp till 10 GB lagring för varje.
* En arbetsyta på Premium-nivå räknas inte mot lagringen för en Power BI Pro-användare.

Den totala användningen får inte överstiga 10 GB per Pro-användare sett till alla Pro-användare och arbetsytor i en klientorganisation.

Läs om andra funktioner i [Power BI-prismodellen](https://powerbi.microsoft.com/pricing).

Din datalagring inkluderar dina egna datauppsättningar och Excel-rapporter och de objekt som någon har delat med dig. Datauppsättningar är alla datakällor du har laddat upp eller anslutit till. Dessa datakällor omfattar Power BI Desktop-filer och Excel-arbetsböcker du använder. Följande ingår även i din datakapacitet.

* Excel-intervall fästa till en instrumentpanel.
* Reporting Services lokala visualiseringar fästa på en Power BI-instrumentpanel.
* Överförda bilder.

Storleken på en instrumentpanel som du delar varierar beroende på vad som är fäst på den. Om du till exempel fäster objekt från två rapporter som ingår i två olika datauppsättningar, kommer storleken att inkludera bägge datauppsättningarna.

<a name="manage"/>

## <a name="manage-items-you-own"></a>Hantera objekt du äger

Se hur mycket lagringsutrymme du använder i ditt Power BI-konto och hantera ditt konto.

1. Om du vill hantera din lagring, går du till **min arbetsyta** i det vänstra navigeringsfönstret.
   
    ![Min arbetsyta](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Välj kugghjulsikonen ![Kugghjulsikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) i det övre högra hörnet \>  **hantera personlig lagring**.
   
    Det översta fältet visar hur mycket av din lagringsgräns som du har använt.
   
    ![Hantera lagringsgräns](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Datauppsättningarna och rapporterna avgränsas på två flikar:
   
    **Ägs av mig:** Du har laddat upp dessa rapporter och datauppsättningar till ditt Power BI-konto, inklusive tjänstedatauppsättningar som Salesforce och Dynamics CRM.  
    **Ägs av andra:** Andra har delat dessa rapporter och datauppsättningar med dig.
1. Om du vill ta bort en datauppsättning eller rapport, väljer du papperskorgsikonen ![papperskorgsikonen](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Tänk på att du eller någon annan kan ha rapporter och instrumentpaneler baserade på en datauppsättning. Om du tar bort datauppsättningen, fungerar dessa rapporter och instrumentpaneler inte längre.

## <a name="manage-your-workspace"></a>Hantera din arbetsyta
1. Välj pilen bredvid **Arbetsytor** \> välj namnet på arbetsytan.
   
    ![Välj en arbetsyta](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Välj kugghjulsikonen ![Kugghjulsikon](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) i det övre högra hörnet \>  **hantera grupplagring**.
   
    Det översta fältet visar hur mycket av din lagringsgräns som du har använt.
   
    ![Hantera lagring för arbetsytor](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Datauppsättningarna och rapporterna avgränsas på två flikar:
   
    **Ägs av oss:** Du eller någon annan har laddat upp dessa rapporter och datauppsättningar till gruppens Power BI-konto, inklusive tjänstedatauppsättningar som Salesforce och Dynamics CRM.
    **Ägs av andra:** Andra har delat dessa rapporter och datauppsättningar med din grupp.
3. Om du vill ta bort en datauppsättning eller rapport, väljer du papperskorgsikonen ![papperskorgsikonen](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Alla medlemmar med redigeringsbehörigheter för en arbetsyta har behörighet att ta bort datamängder och rapporter från arbetsytan.
   > 
   > 

Tänk på att du eller någon annan i gruppen kan ha rapporter och instrumentpaneler baserade på en datauppsättning. Om du tar bort datauppsättningen, fungerar dessa rapporter och instrumentpaneler inte längre.

## <a name="dataset-limits"></a>Datauppsättningsgränser
Det finns en gräns på 1 GB, per datauppsättning som importeras till Power BI. Om du har valt att behålla Excel-upplevelsen istället för att importera data, är gränsen 250 MB för datauppsättningen.

## <a name="what-happens-when-you-reach-a-limit"></a>Vad händer när du når en gräns?
När du når datakapacitetsgränsen för vad du kan göra, får du meddelanden i tjänsten. 

När du väljer kugghjulsikonen ![kugghjulsikonen](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), ser du ett rött streck som anger att du har överskridit din datakapacitetsgräns.

![Uppnådd lagringsgräns](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Den här gränsen visas också i **Hantera personlig lagring**.

 ![Hantera personlig lagring, lagringsgränsen har nåtts](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 När du försöker utföra en åtgärd som når någon av gränserna visas ett meddelande om att du är över gränsen. Du kan [hantera](#manage) din lagring för att minska ditt lagringsutrymme och komma förbi gränsen.

 ![Över din lagringsgräns](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

