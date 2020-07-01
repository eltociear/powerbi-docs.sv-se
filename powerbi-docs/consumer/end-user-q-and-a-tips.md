---
title: Tips för att ställa frågor med Frågor och svar
description: Tips för att ställa frågor med Frågor och svar i Power BI
author: mihart
ms.reviewer: Mohammad
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 03/11/2020
ms.author: mihart
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 891795eec35fbead6d66370d59db511917d4eb26
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85235440"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>Tips för att ställa frågor i Frågor och svar i Power BI

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

## <a name="words-and-terminology-that-qa-recognizes"></a>Ord och terminologi som Frågor och svar känner igen
Listan över nyckelord på den här sidan är inte fullständig.  Det bästa sättet att se om Power BI identifierar ett nyckelord är att testa att skriva det i frågerutan.  Om en term eller ett ord har tonats ned kan inte Power BI identifiera den/det.

Nedanstående lista använder presens men alla tempus kan kännas igen. Till exempel omfattar ”är” **vara**, **var**, **kommer att vara**, **har** **varit**, **har**, **hade**, **kommer att** **ha**, **gör**, **gjorde**, **gjort**.  Och ”sortera” innehåller **sorterade** och **sortering**.  Dessutom känner Power BI igen och inkluderar ord i singular och plural. 

> [!NOTE]
> Frågor och svar finns också tillgängligt i [Microsoft Power BI-appen för iOS på iPad-, iPhone- och iPod Touch-enheter](mobile/mobile-apps-ios-qna.md).
>  


|Kategori  |Nyckelord  |Column3  |
|---------|---------|---------|
|**Aggregeringar**     | total, summa, mängd, antal, kvantitet, sammanlagt, mest, minst, färre, större, högst, störst, max, maximum, lägst, mindre, minimum, min          |
|     |         |         
**Artiklar**     |  en, ett              |
|     |         |         
|**Tomma och booleska**     |   tomt, tom, null, föregås av ”inte” eller ”icke-”, tom sträng, tom text, true, t, false, f          |
|     |         |         |
|**Jämförelser**     |   vs, jämförd med, jämfört med, jämfört            |
|     |         |         |
|**Konjunktioner**     |  och, eller, var och en av, med, jämfört med, &, och, men och inte heller, tillsammans med, förutom       |         
|          |         |
|**Förkortningar**     |  Frågor och svar identifierar nästan alla förkortningar, prova.  Här följer några exempel: t.ex., o.s.v., m.m., t.v., t.h, nr.          |
|        |         |
|**Datum**     |       Power BI identifierar de flesta datumvillkoren (dag, vecka, månad, år, kvartal, decennium, ...) och datum som skrivits i olika format (se nedan). Power BI identifierar också följande nyckelord: MonthName, dagar 1–31, decennium. Exempel: 3 januari 1995, januari 3 1995, jan 03 1995 3 januari 1995, den 3 januari, januari 1995, 1995 januari 1995-01, 01/1995, namn på månader         |
|        |         |
|**Relativa datum**     |   idag, just nu, aktuell tid, igår, i framtiden, aktuellt, därefter kommande, sista, tidigare, sedan, innan, nu, snabbare än, efter, senare än, från, på, på, från nu, efter nu, framtida, tidigare, sista, föregående, inom, över N dagar sedan, N dagar från nu, nästa, en gång, två gånger.|
|    |  Exempel: Antal order under de senaste 6 dagarna.  |            |
|        |         |
|**Likhet (intervall)**     |   lika med, =, efter, är mer än, i, mellan, före  |
|  |Exempel: Beställningsår är före 2012? Priset mellan 10 och 20? Är Johns ålder större än 40? Total försäljning i 200 300?              |
|        |         |
|**Likhet (värde)**     |   är lika med, lika med, för, inom, finns på |
|   | Exempel: Vilka produkter är gröna? Beställningsdatum motsvarar 2012. Är John 40 år? Total försäljning som inte är lika med 200? Beställningsdatum motsvarar 1/1/2016. 10 i pris? Grön färg? 10 i pris?              |
|        |         |
|**Namn**     |       Om en kolumn i datauppsättningen innehåller frasen ”name” (t.ex. EmployeeName) förstår Frågor och svar att värdena i kolumnen är namn. Du kan ställa frågor som ”vilka anställda heter Robert”.          |
|        |         |
**Pronomen**  | han, honom, själv, hans, hon, sig själv, hennes, den, sig själv, dess, de, deras, dem själva, deras, den här, de här, detta, dessa
|**Frågekommandon**     |    sorterade, sortera efter riktning, gruppera, gruppera efter, visa, lista, visa mig, namn, endast, ordna, rangordna, jämför, till, med, mot, alfabetiskt, stigande, fallande, ordning             |
|        |         |
|**Intervall**     |      större, mer, högre, är över, >, mindre, lägre, färre, under, <, minst, mindre än, >=, mest, inte mer än, <=, i, mellan, i intervallet, från, senare, tidigare, snabbare, efter, vid, senare än, efter, sedan, från och med, börjar från, slutar med           |
|        |         |
**Tid**  |am, pm, klockan, på dagen, midnatt, timme, minut, sekund, tt:mm:ss, tt.mm.ss  |
|  |  Exempel: 10 pm, 10:35 pm, 22:35:15, klockan 10, på dagen, midnatt, timme, minut, sekund.  |
|  |  |
|**Högsta N**     |     (ordning, rangordning): uppifrån, längst ned, högsta, lägsta, först, sist, därefter, tidigaste, senaste, äldsta, senaste, den senaste, nästa            |
|        |         |
|**Visualiseringstyper**     |  alla visualiseringstyper som är inbyggda i Power BI.  Om detta är ett alternativ i fönstret Visualiseringar kan du inkludera det i din fråga.  Undantaget till den här regeln är [visuella Power BI-objekt](../developer/visuals/power-bi-custom-visuals.md) som du har lagt till i visualiseringsfönstret manuellt.  |
|  |  Exempel: visa distrikt per månad och total försäljning som liggande diagram               |
|        |         |
|**Vad (relationen, kvalificerad)**  | när, var, vilken, vilket, hur många, hur mycket, hur många gånger, hur ofta, hur vanligt, belopp, kvantitet, antal, hur lång tid, vad                |

## <a name="qa-helps-you-phrase-the-question"></a>Frågor och svar hjälper dig att formulera frågan
Frågor och svar gör sitt bästa för att förstå och besvara den ställda för. Funktionen försöker att förstå på flera olika sätt. För alla dessa formuleringar kan du acceptera åtgärden helt, delvis eller inte alls. När du skriver din fråga kompletterar

* Frågor och svar dina ord och frågor. Den använder olika strategier, inklusive att automatiskt slutföra okända ord, lagrade frågor och tidigare använda frågor som returnerade giltiga svar. Om det finns mer än ett alternativ för automatisk komplettering visas de i en listruta.
* rättar stavning.
* innehåller en förhandsgranskning av svaret i form av ett visuellt objekt. Det visuella objektet uppdateras efter hand som du skriver och redigerar frågan (den väntar inte på att du ska trycka på Retur).
* föreslår ersättningstermer from den underliggande datauppsättningen när du flyttar tillbaka pekaren till frågerutan.
* ställer om frågan baserat på data i underliggande datauppsättningar. Frågor och svar ersätter orden med synonymer från den underliggande datauppsättningen. Genom att läsa omformuleringen vet du om Frågor och svar förstod din fråga eller inte. 
* lägger till en dubbel understrykning för ord som den inte förstår.
* lägger till en enkel understrykning för ord som den inte förstår.
* gör att du kan kontakta ägaren till rapporten eller instrumentpanelen när termen inte går att hitta eller fråga inte genererar några resultat.

## <a name="dont-stop-now"></a>Sluta inte nu
När Frågor och svar visar dina resultat kan du hålla igång samtalet! Använda det visuella objektets interaktiva funktioner och Frågor och svar för att få fler insikter.

## <a name="next-steps"></a>Nästa steg
Gå tillbaka till [Frågor och svar i Power BI](end-user-q-and-a.md)  

[Power BI – grundläggande begrepp](end-user-basic-concepts.md)  

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

