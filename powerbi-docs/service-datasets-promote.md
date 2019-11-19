---
title: Höja upp din datamängd (förhandsversion) – Power BI
description: Lär dig hur du höjer upp din datamängd för att vägleda företagsanvändare till tillförlitliga, högkvalitativa datamängder.
author: maggiesMSFT
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 379249ac50f61df07c4adaffe53e0df29a311086
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877120"
---
# <a name="promote-your-dataset-preview"></a>Höja upp din datamängd (förhandsversion)

Dina Power BI-rapportskapare kan nu ha åtkomst till många olika datamängder. Därför behöver företag vägleda dem till tillförlitliga, högkvalitativa datamängder. Power BI erbjuder två sätt att *rekommendera* datamängder:

- **Upphöjning**: Som datamängdsägare kan du höja upp dina egna datamängder när de är redo för generell användning. Alla medlemmar i arbetsytan med skrivbehörighet kan flytta upp en datauppsättning. Det finns inga begränsningar som kan flytta upp en datauppsättning. Upphöjning stöder en samarbetsinriktade spridningen av datamängder i organisationer. Den här artikeln handlar om att höja upp din datamängd.
- **Certifiering**: Du kan begära certifiering för en upphöjd datamängd. En utvald grupp med användare som definieras i klientorganisationsadministratörens inställningen **Datamängdscertifiering** avgör vilka datamängder som ska certifieras. Mer information finns i [Certifiera datamängder (förhandsversion)](service-datasets-certify.md).

## <a name="promote-a-dataset"></a>Höja upp en datamängd

Datamängden måste finnas på arbetsyta med den nya arbetsytefunktionen i Power BI-tjänsten när du är redo att höja upp den.

1. Gå till listan över datamängder på arbetsytan.
 
1. Välj **Fler alternativ** (...) och sedan **Inställningar**.

    ![Välj ellipsen intill datamängden](media/service-datasets-certify-promote/power-bi-dataset-settings.png)

1. Expandera **Endorsement** (Rekommendation) > välj **Promoted** (Upphöjd).

    ![Välj Promoted (Rekommenderad) och Apply (Verkställ)](media/service-datasets-certify-promote/power-bi-dataset-promoted-endorsement.png)

1. Välj **Tillämpa**.

## <a name="request-dataset-certification"></a>Begära datamängdscertifiering

Din klientorganisationsadministratör har identifierat personer i din organisation som kan certifiera datamängder. Du kan be dem att certifiera din datamängd.

1. Ge certifieraren medlemsbehörighet för den arbetsyta där datamängden finns.

1. I avsnittet **Endorsement** (Rekommendation) i **Inställningar** är **Certifierad** nedtonad.

1. Välj länken **Läs mer**.

    Power BI-klientorganisationsadministratören kan konfigurera länken **Läs mer** så att den leder till en angiven plats med information om certifieringsprocessen i din klientorganisation.   Om administratören inte har anpassad länken **Läs mer** pekar den som standard på artikeln [datamängdscertifiering](service-datasets-certify.md).

## <a name="next-steps"></a>Nästa steg

* Läs avsnittet [Använda datamängder mellan arbetsytor](service-datasets-across-workspaces.md)
* Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
