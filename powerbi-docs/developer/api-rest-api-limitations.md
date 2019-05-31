---
title: Begränsningar för Power BI REST API:t
description: Power BI REST API har följande begränsningar
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 6699167cecebea5085eff4621c077096fd4c6c2e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61385153"
---
# <a name="power-bi-rest-api-limitations"></a>Begränsningar för Power BI REST API:t  
  
**För POST-rader**
  
* Max 75 kolumner
* Max 75 tabeller
* Max 10 000 rader per enskild POST-radsförfrågning  
* 1 000 000 rader läggs till per timme per datauppsättning  
* Max 5 väntande POST-radsförfrågningar per datauppsättning  
* 120 POST-radsförfrågningar per minut per datauppsättning
* Om tabellen har 250 000 rader eller fler, 120 POST-radsförfrågningar per timme per datauppsättning
* Max 200 000 rader lagras per tabell i FIFO-datauppsättning
* Max 5 000 000 rader lagras per tabell i datauppsätting utan bevarandeprincip  
* 4 000 tecken per värde för strängkolumn i POST-radsåtgärd
  
## <a name="see-also"></a>Se också

[Azure AD-tjänsten gränser och begränsningar](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Översikt över Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)