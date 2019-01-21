---
title: Power BI API:er som använder principer för automatiskt bevarande av realtidsdata
description: Lär dig mer om principer för automatiskt bevarande i Power BI-tjänsten
author: markingmyname
manager: kfile
ms.author: maghan
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 9b5923c7bd92b1fe53ebb7ab9416aca8cece3cfa
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54294390"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Princip för automatiskt bevarande av realtidsdata

Principen för automatiskt bevarande i Power BI-tjänsten är en frågesträngsparameter som gör att en standardmässig kvarhållningsprincip automatiskt rensar gamla data samtidigt som en konstant flödet av nya data kommer in till din instrumentpanel. Den första bevarandeprincipen kallas för *Grundläggande först in först ut (FIFO)*. När den är aktiverad samlas data i en tabell tills den uppgår till 200 000 rader. När data överskrider 200 000 rader tas de äldsta raderna bort från datauppsättningen. Detta upprätthåller mellan 200 000 och 210,000 rader med endast den senaste informationen.  
  
<center>

![bevarandeprincip](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Bevarandeprinciperna aktiveras när du skapar dina datauppsättningar. Allt du behöver göra är att lägga till frågeparametern ”defaultRetentionPolicy” i ditt anrop till POST-datauppsättningar och ställa in den på *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}