---
title: Tips för att ställa frågor med Frågor och svar i Power BI
description: Tips för att ställa frågor med Frågor och svar i Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 01/18/2018
ms.author: jastru
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 0165eb7161e9ba931c336300f73316d215b1c88d
ms.sourcegitcommit: fbb7924603f8915d07b5e6fc8f4d0c7f70c1a1e1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/02/2018
ms.locfileid: "34247080"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Tips för att ställa frågor i Frågor och svar i Power BI
## <a name="words-and-terminology-that-qa-recognizes"></a>Ord och terminologi som Frågor och svar känner igen
Den här listan över nyckelord är inte komplett.  Det bästa sättet att se om Power BI identifierar ett nyckelord är att testa att skriva det i frågerutan.  Om ett ord eller en term är nedtonat känner Power BI inte igen det eller kan inte känna igen det i den aktuella kontexten.

Nedanstående lista använder presens men alla tempus kan kännas igen. Till exempel ”är” omfattar vara, var, kommer att vara, har varit, har, hade, kommer att ha, gör, gjorde, gjort.  Och ”sortera” innehåller sorterade och sortering.  Dessutom känner Power BI igen och inkluderar ord i singularis och pluralis. Till exempel, Power BI känner igen ”dag” och ”dagar”.

> [!NOTE]
> Frågor och svar finns också tillgängligt i [Microsoft Power BI-appen för iOS på iPad-, iPhone- och iPod Touch-enheter](mobile-apps-ios-qna.md).
> 
> 

Om du äger en datauppsättning kan du lägga till ordföljder och synonymer för att förbättra dina kunders resultat från frågor och svar.

**Aggregeringar**: total, summa, mängd, antal, kvantitet, sammanlagt, mest, minst, färre, större, högst, störst, max, maximum, lägst, mindre, minimum, min

**Artiklar**: en, ett

**Tomma och booleska**: tomt, tom, null, föregås av ”inte” eller ”icke-”, tom sträng, tom text, true, t, false, f

**Jämförelser**: vs, jämförd med, jämfört med, jämfört

**Konjunktioner**: och, eller, var och en av, med, jämfört med, &, och, men och inte heller, tillsammans med, förutom

**Förkortningar**: Frågor och svar identifierar nästan alla förkortningar, prova.  Här följer några exempel: t.ex., o.s.v., m.m., t.v., t.h, nr.

**Datum**: Power BI identifierar de flesta datumvillkoren (dag, vecka, månad, år, kvartal, decennium, osv.) och datum som skrivits i olika format (se nedan). Power BI identifierar också följande nyckelord: MonthName, dagar 1-31, decennium.

Exempel: 3 Januari 1995, januari 3 1995, jan 03 1995 3 januari 1995, den 3 januari, januari 1995, 1995 januari 1995-01, 01/1995, namn på månader.

**Relativa datum**: idag, just nu, aktuell tid, igår, i framtiden, aktuellt, därefter kommande, sista, tidigare, sedan, innan, nu, snabbare än, efter, senare än, från, på, på, från nu, efter nu, framtida, tidigare, sista, föregående, inom, över N dagar sedan, N dagar från nu, nästa, en gång, två gånger.

Exempel: Antal order under de senaste 6 dagarna.

**Likhet (intervall)**:, lika med, =, efter, är mer än, i, mellan, före

Exempel: Beställningsår är före 2012? Priset mellan 10 och 20? Är Johns ålder större än 40? Total försäljning i 200 300?

**Likhet (värde)**: är lika med, lika med, för, inom, finns på

Exempel: Vilka produkter är gröna? Beställningsdatum motsvarar 2012. Är John 40 år? Total försäljning som inte är lika med 200? Beställningsdatum motsvarar 1/1/2016. 10 i pris? Grön färg? 10 i pris?

**Namn**: om en kolumn i datauppsättningen innehåller frasen ”name” (t.ex. EmployeeName) förstår Frågor och svar att värden i kolumnen är namn och du kan ställa frågor som ”vilka anställda heter robert”.

**Pronomen**: han, honom, själv, hans, hon, sig själv, hennes, den, sig själv, dess, de, deras, dem själva, deras, den här, de här, detta, dessa

**Frågekommandon**: sorterade, sortera efter riktning, gruppera, gruppera efter, visa, lista, visa mig, namn, endast, ordna, rangordna, jämför, till, med, mot, alfabetiskt, stigande, fallande, ordning

**Intervall**: större, mer, högre, är över, >, mindre, lägre, färre, under, <, minst, mindre än, >=, mest, inte mer än, <=, i, mellan, i intervallet, från, senare, tidigare, snabbare, efter, vid, senare än, efter, sedan, från och med, börjar från, slutar med

**Tid**: am, pm, klockan, på dagen, midnatt, timme, minut, sekund, tt:mm:ss, tt.mm.ss

Exempel: 10 pm, 10:35 pm, 22:35:15, klockan 10, på dagen, midnatt, timme, minut, sekund.

**Högsta N** (ordning, rangordning): uppifrån, längst ned, högsta, lägsta, först, sist, därefter, tidigaste, senaste, äldsta, senaste, den senaste, nästa

**Visualiseringstyper**: alla visualiseringstyper som är inbyggda i Power BI.  Om detta är ett alternativ i fönstret Visualiseringar kan du inkludera det i din fråga.  Undantaget till detta är [anpassade visuella objekt](power-bi-custom-visuals.md) som du har lagt till i visualiseringsfönstret manuellt.

Exempel: visa distrikt per månad och total försäljning som liggande diagram

**Vad (relationen, kvalificerad)**: när, var, vilken, vilket, hur många, hur mycket, hur många gånger, hur ofta, hur vanligt, belopp, kvantitet, antal, hur lång tid, vad

## <a name="qa-helps-you-phrase-the-question"></a>Frågor och svar hjälper dig att formulera frågan
Frågor och svar gör sitt bästa för att säkerställa att svaret korrekt speglar den ställda frågan. Detta sker på flera sätt. För alla dessa kan du acceptera åtgärden helt, delvis eller inte alls. När du skriver din fråga kompletterar

* Frågor och svar dina ord och frågor. Den använder olika strategier, inklusive att automatiskt slutföra okända ord, vanliga frågor för underliggande arbetsböcker och tidigare använda frågor som returnerade giltiga svar. Om det finns mer än ett alternativ för automatisk komplettering visas de i en listruta.
* rättar stavning.
* innehåller en förhandsgranskning av svaret i form av en visualisering. Visualiseringen uppdateras efter hand som du skriver och redigerar frågan (den väntar inte på att du ska trycka på Retur).
* föreslår automatiskt ersättningstermer from den underliggande datauppsättningen när du flyttar tillbaka pekaren till frågerutan.
* ställer om frågan baserat på data i underliggande datauppsättningar. Därmed kommer Frågor och svar att förstå din fråga och ersätta orden med synonymer från den underliggande datauppsättningen.
* tonar ner ord som den inte förstår.

## <a name="dont-stop-now"></a>Sluta inte nu
När Frågor och svar visar dina resultat kan du hålla igång samtalet! Använda interaktiva funktioner på visualiseringen och Frågor och svar för att få mer insikter.

## <a name="next-steps"></a>Nästa steg
Gå tillbaka till [Frågor och svar i Power BI](power-bi-q-and-a.md)  

[Power BI – grundläggande begrepp](service-basic-concepts.md)  

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

