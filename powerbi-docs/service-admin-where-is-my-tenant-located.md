---
title: Var finns min Power BI-klient?
description: "Lär dig var din Power BI-klient finns och hur den platsen har valts. Det här är viktigt att förstå eftersom det kan påverka interaktioner som du har med tjänsten."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 08/10/2017
ms.author: maghan
LocalizationGroup: Administration
ms.openlocfilehash: fa24689739cc3f38d3b0a5c70bdf6d865cf8f304
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="where-is-my-power-bi-tenant-located"></a>Var finns min Power BI-klient?
<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Lär dig var din Power BI-klient finns och hur den platsen har valts. Det här är viktigt att förstå eftersom det kan påverka interaktioner som du har med tjänsten.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Så här fastställer du var Power BI-klient finns
Om du vill hitta den region som din klient finns i, kan du göra följande.

1. Välj **?** inom Power BI-tjänsten.
2. Välj **om Power BI**.
3. Leta efter värdet bredvid **dina data lagras i**. Det här är den region som du befinner dig i.

![](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Så här väljs dataregionen
Dataregionen baseras på det land som valdes när klienten först skapades. Detta gäller för Office 365-registreringen utöver Power BI eftersom den här informationen delas. Om det här är en ny klient, visas listruta med länder när du registrerar dig.

![](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

Det här alternativet är det som styr var där dina data kommer att lagras. Power BI väljer en dataregion som är närmast det här valet.

> [!WARNING]
> Valet kan inte ändras!
> 
> 

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

