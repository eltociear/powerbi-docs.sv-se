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
ms.date: 10/17/2017
ms.author: davidi
ms.openlocfilehash: eabb59b32234fce1ba5669b95abb41c4f7e04aa2
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
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

