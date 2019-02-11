---
title: Power BI API:er som använder principer för automatiskt bevarande av realtidsdata
description: Lär dig mer om principer för automatiskt bevarande i Power BI-tjänsten
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 246feb1cb15d1688cab044151b50ba62db45c453
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/06/2019
ms.locfileid: "55762408"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Princip för automatiskt bevarande av realtidsdata

Principen för automatiskt bevarande i Power BI-tjänsten är en frågesträngsparameter som gör att en standardmässig kvarhållningsprincip automatiskt rensar gamla data samtidigt som en konstant flödet av nya data kommer in till din instrumentpanel. Den första bevarandeprincipen kallas för *först in först ut (FIFO)*. När den är aktiverad samlas data i en tabell tills den uppgår till 200 000 rader. När data överskrider 200 000 rader tas de äldsta raderna bort från datauppsättningen. Detta upprätthåller mellan 200 000 och 210,000 rader med endast den senaste informationen.  
  
<center>

![bevarandeprincip](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Bevarandeprinciperna aktiveras när du skapar dina datauppsättningar. Allt du behöver göra är att lägga till frågeparametern för ”standardprincip för bevarande” i ditt anrop till POST-datauppsättningar och ställa in den på *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}