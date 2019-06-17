---
title: Certifiera datamängder (förhandsversion) – Power BI
description: Lär dig hur du vägleder företagsanvändare till tillförlitliga, högkvalitativa datamängder.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: e790afee5b57b73a756ca3c1afd564b00e778186
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461337"
---
# <a name="certify-datasets-preview"></a>Certifiera datamängder (förhandsversion)

Din organisation kan certifiera datamängder som är den auktoritativa källan till viktig information. Dessa datamängder är viktiga när rapportdesigners börjar skapa en rapport och leta efter tillförlitliga data. Certifiering kan vara en mycket selektiv process där endast de mest värdefulla datamängderna certifieras. Power BI-klientorganisationsadministratörer har en ny inställning så att de noggrant kan kontrollera vem som kan certifiera datamängder. Därmed kan administratörer säkerställa att certifiering av datamängder resulterar i tillförlitliga och auktoritativa datamängder som kan användas i hela organisationen.

Power BI-användare kan nu ha åtkomst till många olika datamängder. Därför behöver företag vägleda dem till tillförlitliga, högkvalitativa datamängder. Power BI erbjuder två sätt att *rekommendera* datamängder:

- **Upphöjning**: Ägare av datamängder kan höja upp sina egna datamängder när de är redo för generell användning. Mer information finns i [Höja upp din datamängd](service-datasets-promote.md). 
- **Certifiering**: Ägare av datamängder kan begära certifiering av en upphöjd datamängd. En utvald grupp med användare som definieras i klientorganisationsadministratörens inställningen **Datamängdscertifiering** avgör vilka datamängder som ska certifieras.

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
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)
