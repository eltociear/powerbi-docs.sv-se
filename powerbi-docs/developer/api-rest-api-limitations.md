---
title: Begränsningar för Power BI REST API:t
description: Power BI REST API har följande begränsningar
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 97745d93de771d4888dd97717a5e8a8d2d6f5c7c
ms.sourcegitcommit: c395fe83d63641e0fbd7c98e51bbab224805bbcc
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74265630"
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
  
## <a name="see-also"></a>Se även

[Azure AD-tjänsten gränser och begränsningar](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Översikt över Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)