---
title: Hur administratörer kan hantera inloggningsformuläret för Power BI Desktop
description: Lär dig hur du kan hantera det första inloggningsformuläret när Power BI Desktop öppnas.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/21/2019
ms.author: davidi
ms.openlocfilehash: 9e35bbffec40aa57d3097e122bd038659405dfed
ms.sourcegitcommit: 76772a361e6cd4dd88824b2e4b32af30656e69db
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/27/2019
ms.locfileid: "56892308"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Hur administratörer kan hantera inloggningsformuläret för Power BI Desktop
Första gången Power BI Desktop startas visas ett inloggningsformulär. Informationen kan vara ifylld. Annars loggar du in i Power BI för att fortsätta. Administratörer kan hantera det här formuläret med hjälp av en registernyckel. 

![Första inloggningsformuläret för Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Administratörer använder följande registernyckel för att inaktivera inloggningsformuläret. Åtgärden kan även tillämpas i hela företaget med hjälp av globala principer.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

Värdet 0 inaktiverar dialogrutan.

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

