---
title: Hur administratörer kan hantera inloggningsformuläret för Power BI Desktop
description: Lär dig hur du kan hantera det första inloggningsformuläret när Power BI Desktop öppnas.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/15/2019
ms.author: davidi
ms.openlocfilehash: 5c31277b640b16882bef5c5f2cd9c56b441ede82
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61329891"
---
# <a name="how-administrators-can-manage-the-power-bi-desktop-sign-in-form"></a>Hur administratörer kan hantera inloggningsformuläret för Power BI Desktop
Första gången Power BI Desktop startas visas ett inloggningsformulär. Informationen kan vara ifylld. Annars loggar du in i Power BI för att fortsätta. Administratörer kan hantera det här formuläret med hjälp av en registernyckel. 

![Första inloggningsformuläret för Power BI Desktop](media/desktop-admin-sign-in-form/sign-in-form.png)

Administratörer använder följande registernyckel för att inaktivera inloggningsformuläret. Åtgärden kan även tillämpas i hela företaget med hjälp av globala principer.

```
Key: HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```
Du kan även prova följande nyckel, som har fungerat för vissa kunder baserat på deras konfigurationer:

```
Key: HKEY_CURRENT_USER\SOFTWARE\Microsoft\Microsoft Power BI Desktop
valueName: ShowLeadGenDialog
```

Värdet 0 inaktiverar dialogrutan.




Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

