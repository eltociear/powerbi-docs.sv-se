---
title: "Power BI Premium-stöd för stora datauppsättningar"
description: "Power BI Premium stöder nu datauppsättningar upp till 10 GB."
services: powerbi
documentationcenter: 
author: MarkMcGeeAtAquent
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
ms.date: 02/27/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: def06965692644c0328dae7a1d0ade8d13cc0d6c
ms.sourcegitcommit: 743e44fc8730fea0f7149916080b0c6d7eb6359d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/28/2018
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Power BI Premium-stöd för stora datauppsättningar

Power BI Premium stöder överföring av filer på Power BI Desktop (PBIX) som är upp till 10 GB i storlek. När du har överfört datauppsättningen kan du uppdatera den till en storlek på upp till 12 GB. Om du vill använda en stor datauppsättning, publicera den till en arbetsyta som har tilldelats Premium-kapacitet.
 
## <a name="best-practices"></a>Metodtips

Det här avsnittet beskriver metodtips för att arbeta med stora datauppsättningar.

**Stora modeller kan vara väldigt resursintensiva** vad gäller kapacitet. Vi rekommenderar minst en P1 SKU för alla modeller som är större än 1 GB. I följande tabell beskrivs rekommenderade SKU:er för olika storlekar på PBIX:


   |SKU  |Storlek på PBIX   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3    | upp till 10 GB   |



**PBIX-filerna representerar data i ett mycket komprimerat tillstånd**. Data kommer sannolikt att expandera flera gånger när de läses in i minnet och därifrån kan de expandera flera gånger under datauppdatering.

**Schemalagd uppdatering av stora datauppsättningar kan ta lång tid** och vara väldigt resursintensivt. Därför bör du inte schemalägga för många överlappande uppdateringar. Observera också att tidsgränsen för schemalagda uppdateringsjobb har dubblerats till fyra timmar för alla datauppsättningar i den här kapaciteten.

**Inledande rapportbelastning för stora datauppsättningar kan ta lång tid** om det var ett tag sedan datauppsättningen senast användes eftersom modellen läses in i minnet för Premium-kapaciteten. En inläsning för längre inläsningsrapporter visar belastningsförloppet.

**Om du tar bort arbetsytan från Premium-kapaciteten**, kommer modellen och alla associerade rapporter och instrumentpaneler inte att fungera.

**Då minnes- och tidsbegränsningarna per fråga är mycket högre i Premium-kapaciteten**, rekommenderar vi att du använder filter och utsnitt för att begränsa visuell information om du bara vill visa det som är nödvändigt.

## <a name="next-steps"></a>Nästa steg
[Power BI Premium – vad är det?](service-premium.md)  
[Viktig information om Power BI Premium](service-premium-release-notes.md)  
[Microsoft Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)  
[Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/pbienterprisedeploy)  
[Aktivering av utökad Pro-utvärderingsversion](service-extended-pro-trial.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
