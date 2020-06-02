---
title: Certifiera datamängder – Power BI
description: Lär dig hur du vägleder företagsanvändare till tillförlitliga, högkvalitativa datamängder.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/30/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a6d03521cd3962dcf9549d99076d8606b1142976
ms.sourcegitcommit: 5e5a7e15cdd55f71b0806016ff91256a398704c1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/22/2020
ms.locfileid: "83792944"
---
# <a name="certify-datasets---power-bi"></a>Certifiera datamängder – Power BI

Din organisation kan certifiera datamängder som är den auktoritativa källan till viktig information. Dessa datamängder är viktiga när rapportdesigners börjar skapa en rapport och leta efter tillförlitliga data. Certifiering kan vara en mycket selektiv process där endast de mest värdefulla datamängderna certifieras. Power BI-klientorganisationsadministratörer har en ny inställning så att de noggrant kan kontrollera vem som kan certifiera datamängder. Därmed kan administratörer säkerställa att certifiering av datamängder resulterar i tillförlitliga och auktoritativa datamängder som kan användas i hela organisationen.

Power BI-användare kan nu ha åtkomst till många olika datamängder. Därför behöver företag vägleda dem till tillförlitliga, högkvalitativa datamängder. Power BI erbjuder två sätt att *rekommendera* datamängder:

- **Upphöjning**: Ägare av datamängder och andra användare på arbetsytan kan höja upp sina egna datamängder när de är redo för generell användning. Mer information finns i [Höja upp din datamängd](service-datasets-promote.md). 
- **Certifiering**: Ägare av datamängder kan begära certifiering av en upphöjd datamängd. En utvald grupp med användare som definieras i klientorganisationsadministratörens inställningen **Datamängdscertifiering** avgör vilka datamängder som ska certifieras. Namnet på den person som certifierade en datauppsättning visas i en knappbeskrivning under utforskaren för datauppsättningen. Håll muspekaren över etiketten **Certifierad** så ser du den.

## <a name="certify-a-dataset"></a>Certifiera en datamängd

Klientorganisationsadministratören kan ange en URL för länken **Läs mer** på sidan för inställningen **Endorsement** (Rekommendation).  De kan länka till dokumentationen om certifieringsprocessen. Om de inte anger ett mål för länken **Läs mer** pekar den som standard på den här artikeln.

![Datamängdscertifiering Läs mer](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

Det innebär ett stort ansvar att få behörigheten att certifiera datamängder. När en datamängdsskapare kontaktar dig angående certifiering av en datamängd utgör det början av urvalsprocessen. När du anser att en datamängd bör certifieras följer de sista stegen här.

1. Datamängdsägaren behöver ge dig medlemsbehörighet för den arbetsyta där datamängden finns.
1. Om din klientorganisationsadministratör har gett dig behörighet att certifiera datamängder är alternativet **Certifierad** i avsnittet **Endorsement** (Rekommendation) i **Inställningar** för datamängden tillgängligt. Välj **Certifierad**.
1. Välj **Tillämpa**.

Läs mer om hur klientorganisationsadministratörer [kontrollerar användningen av datamängder mellan arbetsytor](service-datasets-admin-across-workspaces.md).

## <a name="next-steps"></a>Nästa steg

* Läs avsnittet [Använda datamängder mellan arbetsytor](service-datasets-across-workspaces.md)
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
