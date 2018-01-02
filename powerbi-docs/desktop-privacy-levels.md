---
title: "Förstå sekretessnivåer i Power BI Desktop"
description: "Sekretessnivåer i Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
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
ms.date: 10/12/2017
ms.author: davidi
ms.openlocfilehash: 733e24f44c63b8887c3c8b00999f7cea22581a86
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="power-bi-desktop-privacy-levels"></a>Sekretessnivåer i Power BI Desktop
I **Power BI Desktop**, anger sekretessnivåer en isoleringsnivå som definierar hur en datakälla isoleras från andra datakällor. Även om en begränsande isoleringsnivå blockerar information från att utbytas mellan datakällor, kan det minska funktionaliteten och påverka prestandan.

I inställningen **Sekretessnivåer** som finns i **Fil > Alternativ och inställningar > Alternativ** och sedan **Aktuell fil > Sekretess** kan du avgöra om Power BI Desktop använder dina inställningar för sekretess när du kombinerar data. Den här dialogrutan inkluderar en länk till Power BI Desktop-dokumentationen om sekretessnivåer och sekretessnivåer (den här artikeln).

![](media/desktop-privacy-levels/desktop_privacylevels1.png)

 Inställningsdialogrutan **Sekretess** för varje datakälla hittas i **Fil > Alternativ och inställningar > Inställningar för datakälla**. Välj datakällan och välj sedan **Redigera**. Dialogrutan **Inställningar för datakälla** visas där du kan välja lämplig sekretessnivå från listrutan längst ned i dialogrutan som det visas i följande bild.

 ![](media/desktop-privacy-levels/desktop_privacylevels2.png)

> [!CAUTION]
> Du bör konfigurera en datakälla som innehåller mycket känsliga eller konfidentiella data som **Privat**.
> 
> 

## <a name="configure-a-privacy-level"></a>Konfigurera en sekretessnivå
Med inställningar för sekretessnivå kan du ange en isoleringsnivå som definierar hur en datakälla måste isoleras från andra datakällor.

| Inställning | Beskrivning | Exempeldatakällor |
| --- | --- | --- |
| **Privat datakälla** |En **Privat** datakälla innehåller känslig eller konfidentiell information och synligheten för datakällan kan begränsas till behöriga användare. En privat datakälla är helt isolerad från andra datakällor. |Facebook-data, en textfil som innehåller aktieersättning, eller en arbetsbok som innehåller information av granskning av anställda. |
| **Organisationsdatakällor** |En **Organisations**datakälla begränsar synligheten för en datakälla till en betrodd grupp med personer. En **Organisations**datakälla är isolerad från alla **Offentliga** datakällor, men är synlig för andra **Organisations**datakällor. |Ett **Microsoft Word**-dokument på en SharePoint-intranätsida med behörigheter som har aktiverats för en betrodd grupp. |
| **Offentlig datakälla** |En **Offentlig** datakälla ger alla synlighet för de data som finns i datakällan. Endast filer, Internet-datakällor eller arbetsboksdata kan markeras **Offentlig**. |Lediga data från Microsoft Azure Marketplace, data från en Wikipedia-sida eller en lokal fil som innehåller data som kopierats från en offentlig webbplats |

## <a name="configure-privacy-level-settings"></a>Konfigurera sekretessnivåinställningar
Inställningsdialogrutan **Sekretess** för varje datakälla hittas i **Fil > Alternativ och inställningar > Inställningar för datakälla**.

Om du vill konfigurera en sekretessnivå för datakällan, väljer du datakällan och därefter **Redigera**. Dialogrutan **Inställningar för datakälla** visas där du kan välja lämplig sekretessnivå från listrutan längst ned i dialogrutan som det visas i följande bild.

![](media/desktop-privacy-levels/desktop_privacylevels2.png)

> [!CAUTION]
> Du bör konfigurera en datakälla som innehåller mycket känsliga eller konfidentiella data som **Privat**.
> 

## <a name="configure-privacy-levels"></a>Konfigurera sekretessnivåer
**Sekretessnivåer** är en inställning som har angetts till att **Kombinera data enligt dina sekretessnivåinställningar för varje källa** som standard, vilket innebär att **Sekretessnivåer** inte har aktiverats.

| Inställning | Beskrivning |
| --- | --- |
| **Kombinera data i enlighet med dina sekretessnivåinställningar för varje källa** (på och standardinställningen) |Sekretessnivåinställningarna används för att fastställa nivån av isolering mellan datakällor när du kombinerar data. |
| **Ignorera sekretessnivåerna och förbättra eventuellt prestandan** (inaktiverat) |Sekretessnivåer beaktas inte när du kombinerar data, men prestandan och funktionaliteten för data kan förbättras. |

> **Säkerhetsmeddelande:** om du aktiverar **Sekretessnivåer** genom att välja **Ignorera sekretessnivåerna och förbättra eventuellt prestandan** i dialogrutan **Sekretessnivåer** kan det potentiellt exponera känsliga eller konfidentiella data för en obehörig person. Aktivera inte **Sekretessnivåer** om du inte är säker på att datakällan inte innehåller känsliga eller konfidentiella data.
> 
> 

**Konfigurera sekretessnivåer**

I Power BI Desktop eller Frågeredigeraren, väljer du **Fil > Alternativ och inställningar > Alternativ** och därefter **Aktuell fil > Sekretess**.

a. När **Kombinera data enligt dina sekretessnivåinställningar för varje källa** har valts, kommer data att kombineras enligt din sekretessnivåinställning. Om du sammanfogar data över sekretessisoleringszoner resulterar det i viss databuffring.

b. När **Ignorera sekretessnivåerna och förbättra eventuellt prestandan** är markerat, kombineras data och dina sekretessnivåer ignoreras, något som kan visa känslig eller konfidentiell information för obehöriga användare. Inställningen kan förbättra prestanda och funktionalitet.

> **Säkerhetsmeddelande:** om du väljer **Ignorera sekretessnivåer och förbättra eventuellt prestandan** kan du förbättra prestandan, men Power BI Desktop kan inte garantera säkerheten för de data som är sammanfogade i Power BI Desktop-filen.
> 
> 

