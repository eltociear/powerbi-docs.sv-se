---
title: Var finns min Power BI-klient?
description: Lär dig var din Power BI-klient finns och hur den platsen har valts. Det här är viktigt att förstå eftersom det kan påverka interaktioner som du har med tjänsten.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e71844110eb3452cbcb3b224bbca9db57475367e
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54282182"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Var finns min Power BI-klient?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Lär dig var din Power BI-klient finns och hur den platsen har valts. Det är viktigt att förstå platsen eftersom det kan påverka dina interaktioner med tjänsten.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Så här fastställer du var Power BI-klient finns

Följ dessa steg för att hitta den region som din klient finns i.

1. I Power BI-tjänsten på den översta menyn väljer du hjälp (**?**) och sedan **Om Power BI**.

1. Leta efter värdet bredvid **dina data lagras i**. Det här är den region där din klient finns.

    ![Dataområde](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Så här väljs dataregionen

Dataområdet baseras på det land som du väljer när du skapar klienten. Detta gäller för Office 365-registreringen utöver Power BI eftersom den här informationen delas. Om det är en ny klient väljer du rätt land i listan när du registrerar dig.

![Val av land](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Power BI hämtar ett dataområde som är närmast det här alternativet som anger var data lagras för din klient.

> [!IMPORTANT]
> Du kan inte ändra det här alternativet när du har skapat klienten.

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

