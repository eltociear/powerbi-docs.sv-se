---
title: "Power BI kom igång med appar från tredje part"
description: "Power BI kom igång med appar från tredje part"
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
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 08/10/2017
ms.author: maghan
LocalizationGroup: Get started
ms.openlocfilehash: 1d1204c15e7f9cc0dae7685eae959ef2018b634a
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="get-started-with-third-party-apps"></a>Kom igång med appar från tredje part
Med Power BI, kan du använda en app som skapats av ett företag eller en annan individ än Microsoft. Du kan till exempel använda en tredjeparts-app som integrerar Power BI-paneler i ett anpassat webbprogram. När du använder en tredjeparts-app kan du blir ombedd att bevilja programmet vissa behörigheter för ditt Power BI-konto och resurser. Det är viktigt att endast bevilja behörigheter till program som du har känner och litar på. Behörigheter till ett program kan återkallas när som helst. Se [återkalla behörigheter för appar från tredje part](#revoke).

Här är de typer av åtkomst som en app kan begära.

## <a name="power-bi-app-permissions"></a>Power BI-appbehörigheter
* **Visa alla instrumentpaneler**
  
  * Den här behörigheten ger ett program möjligheten att visa alla instrumentpaneler som du har åtkomst till. Detta inkluderar instrumentpaneler som du äger, har tagit emot från innehållspaket och som har delats med dig och är i grupper som du tillhör. Programmet kan inte göra några ändringar på instrumentpanelen. Bland annat kan den här behörigheten användas av ett program för att bädda in ditt instrumentpanelinnehåll i dess erfarenheter.
* **Visa alla rapporter**
  
  * Den här behörigheten ger ett program möjligheten att visa alla rapporter som du har åtkomst till. Detta inkluderar rapporter som du äger, har tagit emot från innehållspaket och som är i grupper som du tillhör. En del av att visa rapporten, innebär att programmet också kan se data i den. Programmet kan inte göra några ändringar på själva rapporterna. Bland annat kan den här behörigheten användas av ett program för att bädda in rapportinnehåll i dess erfarenheter.
* **Visa alla datauppsättningar**
  
  * Den här behörigheten ger ett program möjligheten att lista alla datauppsättningar som du har åtkomst till. Detta inkluderar datauppsättningar som du äger, har tagit emot från innehållspaket och är i grupper som du tillhör. Ett program kan se namnen på alla datauppsättningar samt deras struktur, inklusive tabell- och kolumnnamn. Den här behörigheten ger behörighet att läsa data i en datauppsättning. Behörigheten ger inte programmet behörighet att lägga till eller göra ändringar i en datauppsättning.
* **Läsa och skriva alla datauppsättningar**
  
  * Den här behörigheten ger ett program möjligheten att lista alla datauppsättningar som du har åtkomst till. Detta inkluderar datauppsättningar som du äger, har tagit emot från innehållspaket och är i grupper som du tillhör. Ett program kan se namnen på alla datauppsättningar samt deras struktur, inklusive tabell- och kolumnnamn. Den här behörigheten ger behörighet att läsa och skriva data i en datauppsättning. Programmet kan även skapa nya datauppsättningar eller göra ändringar i befintliga. Detta används ofta av ett program för att skicka data direkt till Power BI.
* **Visa användarens grupper**
  
  * Den här behörigheten ger ett program möjligheten att lista alla grupper som du är medlem i. Det kan använda den här behörigheten tillsammans med några av de andra behörigheterna som listas för att visa eller uppdatera innehållet för den specifika gruppen. Programmet kan inte göra några ändringar i själva gruppen.

<a name="revoke"/>

## <a name="revoke-third-party-app-permissions"></a>Återkalla behörigheter för appar från tredje part
Du återkallar behörigheter för en tredjeparts-app genom att gå till webbplatsen Office 365 mina appar.

På webbplatsen **Office 365 mina appar**, gör du så här för att återkalla behörigheter från tredje part:

1. Gå till [webbplatsen Office 365 mina appar](https://portal.office.com/myapps).
2. På sidan **mina appar**, letar du upp appen från tredje part.
3. Hovra över apppanelen, klicka på **(...)**-knappen och klicka på **ta bort**.
   
   ![](media/service-power-bi-get-started-third-party-apps/remove.png)

