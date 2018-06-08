---
title: Hur administratörer kan hantera inloggningsformuläret för Power BI Desktop
description: Lär dig hur du kan hantera det första inloggningsformuläret när Power BI Desktop öppnas.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/02/2018
ms.author: davidi
ms.openlocfilehash: f35553acd65aeea2c1bf02b04fcbd665af4b99ea
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34721097"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Hur administratörer kan hantera inloggningsformuläret för Power BI Desktop
Första gången Power BI Desktop startas visas ett inloggningsformulär. Informationen kan vara ifylld. Annars loggar du in i Power BI för att fortsätta. Administratörer kan hantera det här formuläret med hjälp av en registernyckel. 

![Första inloggningsformuläret för Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Administratörer använder följande registernyckel för att inaktivera inloggningsformuläret. Åtgärden kan även tillämpas i hela företaget med hjälp av globala principer.

```
Key: HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Power BI Desktop
valueName: ShowLeadGenDialog
```

Värdet 0 inaktiverar dialogrutan.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

