---
title: Power BI Premium-stöd för stora datauppsättningar
description: Power BI Premium stöder nu datauppsättningar upp till 10 GB.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 416f022ee3c413c69650e6f1736cc94edcd58f13
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641262"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Power BI Premium-stöd för stora datauppsättningar

Power BI Premium stöder överföring av filer på Power BI Desktop (PBIX) som är upp till 10 GB i storlek. När du har överfört datauppsättningen kan du uppdatera den till en storlek på upp till 12 GB. Om du vill använda en stor datauppsättning, publicera den till en arbetsyta som har tilldelats Premium-kapacitet. I den här artikeln beskrivs överväganden och bästa praxis för att arbeta med stora datamängder.

**Stora modeller kan vara väldigt resursintensiva** för kapaciteten. Vi rekommenderar minst en P1 SKU för alla modeller som är större än 1 GB. I följande tabell beskrivs rekommenderade SKU:er för olika storlekar på PBIX:

   |SKU  |Storlek på PBIX   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | upp till 10 GB |

**PBIX-filerna representerar data i ett mycket komprimerat tillstånd**. Data kommer sannolikt att expandera flera gånger när de läses in i minnet och därifrån kan de expandera flera gånger under datauppdatering.

**Schemalagd uppdatering av stora datauppsättningar kan ta lång tid** och vara väldigt resursintensivt. Därför bör du inte schemalägga för många överlappande uppdateringar. Observera också att tidsgränsen för schemalagda uppdateringsjobb har dubblerats till fyra timmar för alla datauppsättningar i den här kapaciteten. Vi rekommenderar att [inkrementell uppdatering](service-premium-incremental-refresh.md) eftersom det är snabbare, mer tillförlitligt och förbrukar färre resurser.

**Inledande rapportbelastning för stora datauppsättningar kan ta lång tid** om det var ett tag sedan datauppsättningen senast användes eftersom modellen läses in i minnet för Premium-kapaciteten. En inläsning för längre inläsningsrapporter visar belastningsförloppet.

**Om du tar bort arbetsytan från Premium-kapaciteten**, kommer modellen och alla associerade rapporter och instrumentpaneler inte att fungera.

**Eftersom minnes- och tidsbegränsningarna per fråga är mycket högre i Premium-kapacitet** rekommenderar vi att du använder filter och utsnitt för att begränsa visuell information så att bara det som är nödvändigt visas.

**Nästa steg**

[Vad är Power BI Premium?](service-premium.md)
[Viktig information om Power BI Premium](service-premium-release-notes.md)
[Microsoft Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)
[Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/pbienterprisedeploy)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
