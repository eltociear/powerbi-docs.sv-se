---
title: "Hur administratörer kan hantera inloggningsformuläret för Power BI Desktop"
description: "Lär dig hur du kan hantera det första inloggningsformuläret när Power BI Desktop öppnas."
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 519f8b56b5086292addf577d969a707a6d6efcc8
ms.sourcegitcommit: 5e1f7d2673efe25c47b9b9f315011055bfe92c8f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/09/2018
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Hur administratörer kan hantera inloggningsformuläret för Power BI Desktop
Första gången Power BI Desktop startas visas ett inloggningsformulär. Antingen fylls informationen i eller så loggar man in på Power BI för att fortsätta. Administratörer kan hantera det här formuläret med en registernyckel. 

![Första inloggningsformuläret för Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Administratörer kan använda följande registernyckel för att inaktivera inloggningsformuläret. Det kan också skickas ut med globala principer till hela organisationen.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

Värdet 0 inaktiverar dialogrutan.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

