---
title: Aviseringar om tjänstavbrott
description: Lär dig mer om hur du tar emot e-postaviseringar när det uppstår avbrott eller försämring i Power BI-tjänsten.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/19/2019
ms.author: mblythe
ms.openlocfilehash: 0bb78e29cc3e9b9792d5916050179703281aa01a
ms.sourcegitcommit: 850e7883e21190151684e32f4d957beecd08e959
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/20/2019
ms.locfileid: "68366759"
---
# <a name="service-interruption-notifications"></a>Aviseringar om tjänstavbrott

Det är viktigt att få insyn i tillgängligheten för dina verksamhetskritiska affärs program. Power BI erbjuder incidentmeddelanden så att du kan välja att få e-post om det sker störningar eller försämring i tjänsten. Power BI-serviceavtalet på 99,9 % gör dessa händelser sällsynta, men vi vill ändå säkerställa att du informeras. Följande skärm bild visar den typ av e-post du får om du aktiverar meddelanden:

![E-postmeddelande om uppdatering](media/service-interruption-notifications/refresh-notification-email.png)

För tillfället skickar vi e-postmeddelanden för följande _tillförlitlighetsscenarier_:

- Tillförlitlighet för öppen rapport
- Tillförlitlighet för modelluppdatering
- Tillförlitlighet för frågeuppdatering

När en incident har lösts får du ett uppföljningsmeddelande via e-post.

> [!NOTE]
> Den här funktionen är för närvarande endast tillgänglig för dedikerade kapaciteter i Power BI Premium. Den är inte tillgänglig för delad kapacitet.

## <a name="enable-notifications"></a>Aktivera meddelanden

En Power BI-klientorganisationsadministratör aktiverar meddelanden i administratörsportalen:

1. Identifiera eller skapa en e-postaktiverad säkerhetsgrupp som ska ta emot meddelanden.

1. I administratörsportalen väljer du **Klientorganisationsinställningar**. Under **Inställningar för hjälp och support** expanderar du **Få e-postmeddelanden om tjänstavbrott eller incidenter**.

1. Aktivera meddelanden, ange en säkerhetsgrupp och välj **Använd**.

    ![Aktivera tjänstmeddelanden](media/service-interruption-notifications/enable-notifications.png)

> [!NOTE]
> Power BI skickar meddelanden från kontot no-reply-powerbi@microsoft.com. Se till att det här kontot är tillåtet så att inga meddelanden hamnar i spam- eller skräppostmappen.

## <a name="next-steps"></a>Nästa steg

[Supportalternativ för Power BI Pro och Power BI Premium](service-support-options.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)