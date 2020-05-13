---
title: Starta om en Power BI Premium-kapacitet
description: Lär dig hur du startar om en Power BI Premium-kapacitet för att hantera prestandaproblem.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2020
LocalizationGroup: Premium
ms.openlocfilehash: fcf9dccef980413374e80fdecd028eb2a8bdc1e5
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83274545"
---
# <a name="restart-a-power-bi-premium-capacity"></a>Starta om en Power BI Premium-kapacitet

Som Power BI-administratör kan du behöva starta om en Premium-kapacitet. I den här artikeln beskrivs hur du startar om en kapacitet och hanterar flera frågor om omstart och prestanda.

## <a name="why-does-power-bi-provide-this-option"></a>Varför har Power BI det här alternativet?

Power BI ger användare möjligheten att utföra komplexa analyser på enorma mängder data. Tyvärr kan användare orsaka prestandaproblem genom att överbelasta Power BI-tjänsten med jobb, skriva för komplicerade frågor, skapa cirkelreferenser och så vidare.

Delad Power BI-kapacitet ger ett visst skydd mot sådant genom att tillämpa begränsningar på filstorlekar, uppdateringsscheman och andra aspekter av tjänsten. I en Power BI Premium-kapacitet är de flesta sådana begränsningar högre. Till följd av det kan en enda rapport med ett felaktigt DAX-uttryck eller en mycket komplex modell orsaka betydande prestandaproblem. När rapporten bearbetas kan den förbruka alla tillgängliga resurser i kapaciteten. 

Power BI förbättras ständigt när det gäller hur Premium-kapacitetsanvändare skyddas mot sådana problem. Vi ger även administratörer verktyg för att analysera när kapaciteter överbelastas och varför. Mer information finns i vår [korta utbildningssession](https://www.youtube.com/watch?v=UgsjMbhi_Bk&feature=youtu.be) och [längre utbildningssession](https://powerbi.tips/2018/07/). Samtidigt behöver du kunna åtgärda betydande problem när de inträffar. Det snabbaste sättet att åtgärda dessa problem är att starta om kapaciteten.

## <a name="is-the-restart-process-safe-will-i-lose-any-data"></a>Är omstarten säker? Förlorar jag data?

Alla sparade data, definitioner, rapporter och instrumentpaneler i kapaciteten förblir helt intakta efter omstart. När du startar om en kapacitet stoppas pågående schemalagda uppdateringar och ad hoc-uppdateringar tillfälligt av uppdateringsmotorn i de flesta fall. De startas sedan om på grund av den logik för uppdateringsomförsök som är inbyggd i Power BI. Tjänsten provar att göra nya försök med eventuella uppdateringar som påverkats när kapaciteten blir tillgänglig. Uppdateringarnas tillstånd kanske inte ändras i användargränssnittet under omstarten. 

Användare som interagerar med kapaciteten förlorar arbete som inte har sparats när omstartsprocessen körs. De bör uppdatera sina webbläsare när omstarten har slutförts.

## <a name="how-do-i-restart-a-capacity"></a>Hur startar jag om en kapacitet?

Starta om en kapacitet med hjälp av följande steg.

1. I Power BI-administrationsportalen, på fliken **Kapacitetsinställningar**, går du till din kapacitet. 

1. Lägg till **CapacityRestart**-*funktionsflaggan* i kapacitets-URL:en: `https://app.powerbi.com/admin-portal/capacities/<YourCapacityId>?capacityRestartButton=true`.

1. Under **Avancerade inställningar** > **KAPACITETSOMSTART** väljer du **Starta om kapaciteten**.

    ![Starta om kapaciteten](media/service-admin-premium-restart/restart-capacity.png)

1. I dialogrutan **Kapacitetsomstart** väljer du **Ja, starta om kapaciteten**.

    ![Bekräfta omstart](media/service-admin-premium-restart/confirm-restart.png)

## <a name="how-can-i-prevent-issues-from-happening-in-the-future"></a>Hur förhindrar jag problem i framtiden?

Det bästa sättet att förhindra problem är att utbilda användarna i effektiv datamodellering. Mer information finns i vår [utbildningssession](https://powerbi.tips/2018/07/).

Vi rekommenderar också att du [övervakar dina kapaciteter](service-admin-premium-monitor-capacity.md) regelbundet för att titta efter trender som visar på underliggande problem. Vi planerar regelbundna släpp av övervakningsappen och andra verktyg så att du kan övervaka och hantera kapaciteter effektivare.

## <a name="next-steps"></a>Nästa steg

[Vad är Power BI Premium?](service-premium-what-is.md)

Fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)
