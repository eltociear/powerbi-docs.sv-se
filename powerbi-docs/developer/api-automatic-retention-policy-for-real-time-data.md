---
title: Power BI API:er som använder principer för automatiskt bevarande av realtidsdata
description: Lär dig mer om principer för automatiskt bevarande i Power BI-tjänsten
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: e2d81ac67ea5c070f31315a381b42e3a1379a49b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73865078"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>Princip för automatiskt bevarande av realtidsdata

Principen för automatiskt bevarande i Power BI-tjänsten är en frågesträngsparameter som gör att en standardmässig kvarhållningsprincip automatiskt rensar gamla data samtidigt som en konstant flödet av nya data kommer in till din instrumentpanel. Den första bevarandeprincipen kallas för *först in först ut (FIFO)* . När den är aktiverad samlas data i en tabell tills den uppgår till 200 000 rader. När data överskrider 200 000 rader tas de äldsta raderna bort från datauppsättningen. Detta upprätthåller mellan 200 000 och 210,000 rader med endast den senaste informationen.  
  
<center>

![bevarandeprincip](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

Bevarandeprinciperna aktiveras när du skapar dina datauppsättningar. Allt du behöver göra är att lägga till frågeparametern för ”standardprincip för bevarande” i ditt anrop till POST-datauppsättningar och ställa in den på *basicFIFO*.  
  
    POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}