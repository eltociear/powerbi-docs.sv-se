---
title: Aviseringar om tjänstavbrott
description: Lär dig mer om hur du tar emot e-postaviseringar när det uppstår avbrott eller försämring i Power BI-tjänsten.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/23/2019
ms.author: mblythe
ms.openlocfilehash: 971b9d5aa42f7169eedcbc9ba28752db4a9d319a
ms.sourcegitcommit: c2197c3ad1d747b4ad490ab75771a0d32d0ae208
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/23/2019
ms.locfileid: "70008085"
---
# <a name="service-interruption-notifications"></a>Aviseringar om tjänstavbrott

Det är viktigt att få insyn i tillgängligheten för dina verksamhetskritiska affärs program. Power BI erbjuder incidentmeddelanden så att du kan välja att få e-post om det sker störningar eller försämring i tjänsten. Power BI-serviceavtalet på 99,9 % gör dessa händelser sällsynta, men vi vill ändå säkerställa att du informeras. Följande skärm bild visar den typ av e-post du får om du aktiverar meddelanden:

![E-postmeddelande om uppdatering](media/service-interruption-notifications/refresh-notification-email.png)

För tillfället skickar vi e-postmeddelanden för följande _tillförlitlighetsscenarier_:

- Tillförlitlighet för öppen rapport
- Tillförlitlighet för modelluppdatering
- Tillförlitlighet för frågeuppdatering

Exempel på dessa meddelanden är när användare upplever en utökad fördröjning i åtgärder såsom att öppna rapporter, uppdatera datamängder eller köra frågor. När en incident har lösts får du ett uppföljningsmeddelande via e-post.

> [!NOTE]
> Den här funktionen är för närvarande endast tillgänglig för dedikerade kapaciteter i Power BI Premium. Den är inte tillgänglig för delad eller inbäddad kapacitet.

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
