---
title: Var finns min Power BI-klient?
description: Lär dig var din Power BI-klient finns och hur den platsen har valts. Detta är viktigt att lära dig eftersom det kan påverka interaktioner som du har med tjänsten.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 05/03/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 06b7ba4bfc68358887af28bd2595b442df90d334
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "65710487"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Var finns min Power BI-klient?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Lär dig var din Power BI-klient finns och hur den platsen har valts. Learning platsen är viktig, eftersom det kan påverka interaktioner som har du med tjänsten.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Så här fastställer du var Power BI-klient finns

Följ dessa steg för att hitta den region som din klient finns i.

1. I Power BI-tjänsten på den översta menyn väljer du hjälp ( **?** ) och sedan **Om Power BI**.

1. Leta efter värdet bredvid **dina data lagras i**. Det är den region där din klient finns. Värdet är också den region där dina data lagras, om du inte använder dedikerad kapacitet i olika regioner för dina arbetsytor.

    ![Dataområde](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Så här väljs dataregionen

Dataområdet baseras på det land som du väljer när du skapar klienten. Markeringen gäller för att registrera dig för både Office 365 och Power BI, eftersom den här informationen delas. Om det är en ny klient väljer du rätt land i listan när du registrerar dig.

![Val av land](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Powerbi hämtar ett dataområde som är närmast ditt val som bestämmer var data lagras för din klient.

> [!IMPORTANT]
> Du kan inte ändra valet när du har skapat klienten.

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

