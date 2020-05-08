---
title: Vägledning om automatisk datum/tid i Power BI Desktop
description: Vägledning till funktionen för automatiskt datum/tid i Power BI Desktop.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: a65b17c91640f6ea7fff1d762e8d5b71cc99575e
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "77154153"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Vägledning om automatisk datum/tid i Power BI Desktop

Den här artikeln vänder sig till datamodellerare som utvecklar importmodeller eller sammansatta modeller i Power BI Desktop. Den ger vägledning, rekommendationer och saker att tänka på när du använder Power BI Desktop _automatisk datumt/tid_ i vissa situationer. En översikt och allmän introduktion till _Automatiskt datum/tid_ finns i [Automatiskt datum/tid i Power BI Desktop](../desktop-auto-date-time.md).

Alternativet _Automatiskt datum/tid_ tillhandahåller praktisk, snabb och lättanvänd tidsinformation. Rapportförfattarna kan arbeta med tidsinformation när de filtrerar, grupperar och ökar detaljnivån i kalenderns tidsperioder.

## <a name="considerations"></a>Att tänka på

I följande punktlista beskrivs de överväganden – och eventuella begränsningar – som relaterar till alternativet _Automatiskt datum/tid_.

- **Gäller för alla eller ingen:** När alternativet _Automatiskt datum/tid-_ har aktiverats gäller det alla datumkolumner (förutom beräknade kolumner) i importtabeller som inte tillhör &quot;många&quot;-sidan i en relation. Du kan inte aktivera eller inaktivera det selektivt kolumn för kolumn.
- **Endast kalenderperioder:** Kolumnerna för år och kvartal relaterar till kalenderperioder. Det innebär att året börjar den 1 januari och slutar den 31 december. Det går inte att ändra datumen för årets början (eller slut).
- **Anpassning:** Det går inte att anpassa de värden som används för att beskriva tidsperioder. Dessutom går det inte att lägga till fler kolumner för som beskriver andra tidsperioder, t.ex. veckor.
- **Årsfiltrering:** Kolumnvärdena för**Kvartal**, **Månad** och **Dag** omfattar inte något värde för år. Kolumnen **Månad** innehåller t.ex. endast månadsnamn (januari, februari osv). Värdena är inte helt självbeskrivande, och i vissa rapportmodeller kan det hända att det inte går att kommunicera årsfiltreringskontexten.

    Det är därför det är viktigt att filtrering eller gruppering görs i kolumnen **År**. När du ökar detaljnivån med hjälp av hierarkin så filtreras året såvida inte nivån **År** har tagits bort avsiktligt. Om det inte finns något filter eller någon grupp på årsnivå, så skulle t.ex. en gruppering efter en viss månad summera värdena för just den månaden under alla år.
- **Datumfiltrering för enskild tabell:** Eftersom varje datumkolumn skapar en egen (dold) tabell för automatiskt datum/tid så går det inte att använda något tidsfilter i en enskild tabell och sprida det till flera modelltabeller. Att filtrera på det här sättet är ett vanligt modellkrav vid rapportering av flera ämnen (faktatypstabeller) som försäljning och försäljningsbudget. När rapportförfattaren använder automatiskt datum/tid måste hen använda filter för varje annan datumkolumn.
- **Modellstorlek:** För varje datumkolumn som genererar en dold tabell för automatiskt datum/tid så resulterar det i en ökad modellstorlek och en förlängd datauppdateringstid.
- **Andra rapportverktyg:** Du kan inte arbeta med tabeller med automatisk datum/tid dem när du använder [Analysera i Excel](../service-analyze-in-excel.md) eller när du ansluter till modellen via en annan rapportdesigner än Power BI.

## <a name="recommendations"></a>Rekommendationer

Vi rekommenderar att du behåller alternativet _Automatiskt datum/tid-_ aktiverat endast när du arbetar med kalendertidsperioder och när du har förenklade modellkrav när det gäller tid. Det kan också vara praktiskt att använda det här alternativet när du skapar ad hoc-modeller eller genomför datautforskning eller profilering.

När datakällan redan definierar en datumdimensionstabell, så ska du använda den här tabellen till att konsekvent definiera tid i din organisation. Det är verkligen fallet om din datakälla är ett informationslager. I annat fall kan du generera datumtabeller i modellen med hjälp av funktionerna DAX [CALENDAR](/dax/calendar-function-dax) eller [CALENDARAUTO](/dax/calendarauto-function-dax). Sedan kan du lägga till beräknade kolumner som stöder kända tidsfiltrering- och gruppkrav. Med den här designmetoden kan du skapa en enskild datumtabell som sprids till alla faktatypstabeller, vilket kan resultera i att en enskild tabell använder tidsfilter. Mer information om hur du skapar datumtabeller finns i artikeln [Konfigurera och använda datumtabeller i Power BI Desktop](../desktop-date-tables.md).

Om alternativet _Automatiskt datum/tid_ inte är relevant för dina projekt, så rekommenderar vi att du inaktiverar det globala alternativet _Automatiskt datum/tid_. Det garanterar att alla nya Power BI Desktop-filer som du skapar inte aktiverar alternativet _Automatiskt datum/tid_.

## <a name="next-steps"></a>Nästa steg

Mer information om ämnet i den här artikeln finns i följande resurser:

- [Automatisk datum/tid i Power BI Desktop](../desktop-auto-date-time.md)
- [Konfigurera och använda datumtabeller i Power BI Desktop](../desktop-date-tables.md)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
- Har du förslag? [Bidra till att förbättra Power BI](https://ideas.powerbi.com/)
