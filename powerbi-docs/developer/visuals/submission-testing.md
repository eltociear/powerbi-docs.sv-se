---
title: Inlämningstestning av ett visuellt Power BI-objekt
description: I den här artikeln beskrivs testfall som ditt visuella objekt måste klara innan publicering till AppSource. Det finns även alternativtestfall.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 65e00fa5311ea12c9fe0011c6aa7c3e779f33dc5
ms.sourcegitcommit: bfc2baf862aade6873501566f13c744efdd146f3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83131122"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Inlämningstestning av ett visuellt Power BI-objekt

Innan du publicerar ditt visuella objekt till [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) måste det klara dessa testfall. Testa ditt visuella objekt innan du skickar in det. Om det visuella objektet inte klarar de nödvändiga testfallen kommer det att avvisas.

Mer information om publiceringsprocessen finns i [Publicera visuella Power BI-objekt till Partner Center](./office-store.md).

## <a name="general-test-cases"></a>Allmänna testfall

| Testfall | Förväntat resultat
| --------- | ----------------
| Skapa ett **stående stapeldiagram** med **kategori** och **värde**. Konvertera det till ditt visuella objekt och sedan tillbaka till stapeldiagram. | Inget fel visas efter dessa konverteringar. |
| Skapa en **Mätare** med tre mått. Konvertera det till ditt visuella objekt och sedan tillbaka till **Mätare**. | Inget fel visas efter dessa konverteringar. |
| Gör dina val i ditt visuella objekt. | Andra visuella objekt visar valen. |
| Välj element i andra visuella objekt. | Ditt visuella objekt visar filtrerade data enligt valet i andra visuella objekt. |
| Kontrollera min/max **dataViewMapping**-villkor. | Fält-buckets kan acceptera flera fält, ett enda fält eller så bestäms de av andra buckets. **dataViewMapping**-villkoren min/max måste ha konfigurerats korrekt i funktionerna för ditt visuella objekt. |
| Ta bort alla fält i olika ordning. | Visuella objekt rensas korrekt när fält tas bort i valfri ordning. Det finns inga fel i konsolen eller webbläsaren. |
| Öppna fönstret **Format** med varje möjlig bucket-konfiguration. | Det här testet utlöser inte null-referensundantag. |
| Filtrera data med **Filter**-fönstret på visualiserings-, sid- och rapportnivå. | Knappbeskrivningar är korrekta när du har tillämpat filter. Knappbeskrivningar visar det filtrerade värdet. |
| Filtrera data med ett **Utsnitt**. | Knappbeskrivningar är korrekta när du har tillämpat filter. Knappbeskrivningar visar det filtrerade värdet. |
| Filtrera data ett publicerat visuellt objekt. Välj till exempel en cirkelsektor eller en kolumn. | Knappbeskrivningar är korrekta när du har tillämpat filter. Knappbeskrivningar visar det filtrerade värdet. |
| Om korsfiltrering stöds kontrollerar du att filtren fungerar som de ska. | Det tillämpade valet filtrerar andra visuella objekt på den här sidan av rapporten. |
| Välj med Ctrl-, Alt- och Shift-tangenterna. | Inga oväntade beteenden visas. |
| Ändra **Visningsläge** till **Faktisk storlek**, **Anpassa till sidan** och **Anpassa till bredd**. | Muskoordinaterna är korrekta. |
| Ändra storlek på ditt visuella objekt. | Det visuella objektet reagerar korrekt på storleksändring. |
| Ange minimistorlek för rapporten. | Det finns inga visningsfel. |
| Se till att rullningslisterna fungerar som de ska. | Det bör finnas rullningslister vid behov. Kontrollera rullningslistens storlekar. Rullningslisterna får inte vara för breda eller höga. Rullningslisternas position och storlek måste stämma överens med andra element i ditt visuella objekt. Kontrollera att rullningslisterna behövs för olika storlekar på det visuella objektet. |
| Fäst det visuella objektet på en **Instrumentpanel**. | Det visuella objektet ska visas korrekt. |
| Lägg till flera versioner av ditt visuella objekt på en enda rapportsida. | Alla versioner av det visuella objektet ska visas och fungera korrekt. |
| Lägg till flera versioner av ditt visuella objekt till flera rapportsidor. | Alla versioner av det visuella objektet ska visas och fungera korrekt. |
| Växla mellan rapportsidor. | Det visuella objektet visas korrekt. |
| Testa läsvyn och redigeringsvyn för det visuella objektet. | Alla funktioner fungerar som de ska. |
| Om det visuella objektet använder animeringar, lägger du till, ändrar och tar bort element i ditt visuella objekt. | Animering av visuella element fungerar korrekt. |
| Öppna fönstret **Egenskap**. Aktivera och inaktivera egenskaper, ange anpassad text, visa de tillgängliga alternativen och mata in felaktiga data. | Det visuella objektet svarar som det ska. |
| Spara rapporten och öppna den igen. | Alla egenskapernas inställningar ligger kvar. |
| Växla sidor i rapporten och växla sedan tillbaka. | Alla egenskapernas inställningar ligger kvar. |
| Testa alla funktioner i ditt visuella objekt, inklusive olika alternativ som visas i det visuella objektet. | Alla skärmar och funktioner fungerar som de ska. |
| Testa alla datatyper för numeriska data, datum och tecken som i följande tester. | Alla data är korrekt formaterade. |
| Granska formatering av knappbeskrivningsvärden, axeletiketter, dataetiketter och andra visuella element med formatering. | Alla element är korrekt formaterade. |
| Kontrollera att dataetiketterna använder formatsträngen. | Alla dataetiketter är korrekt formaterade. |
| Växla på och av automatisk formatering för numeriska värden i knappbeskrivningar. | Knappbeskrivningar visar värden korrekt. |
| Testadataposter med olika typer av data, inklusive numeriska, text, datum/tid och andra formatsträngar från modellen. Testa olika datavolymer, till exempel tusentals rader, en rad och två rader. | Alla skärmar och funktioner fungerar som de ska. |
| Ge felaktiga data till ditt visuella objekt, till exempel null, oändlighet, negativa värden och fel värdetyper. | Alla skärmar och funktioner fungerar som de ska. |

## <a name="optional-browser-testing"></a>Valfri webbläsartestning

AppSource-teamet validerar visuella objekt på de senaste Windows-versionerna av Google Chrome, Microsoft Edge och Mozilla Firefox.
Du kan också testa ditt visuella objekt i följande webbläsare.

| Testfall | Förväntat resultat
| --------- | ----------------
| **Windows** |
| Google Chrome (tidigare version) | Alla skärmar och funktioner fungerar som de ska. |
| Mozilla Firefox (tidigare version) | Alla skärmar och funktioner fungerar som de ska. |
| Microsoft Edge (tidigare version) | Alla skärmar och funktioner fungerar som de ska. |
| Microsoft Internet Explorer 11 (valfritt) | Alla skärmar och funktioner fungerar som de ska. |
| **macOS** |
| Chrome (tidigare version) | Alla skärmar och funktioner fungerar som de ska. |
| Firefox (tidigare version) | Alla skärmar och funktioner fungerar som de ska. |
| Safari (tidigare version) | Alla skärmar och funktioner fungerar som de ska. |
| **Linux** |
| Firefox (senaste och tidigare versioner) | Alla skärmar och funktioner fungerar som de ska. |
| **Mobil iOS** |
| Apple Safari iPad (tidigare Safari-version) | Alla skärmar och funktioner fungerar som de ska. |
| Chrome iPad (senaste Safari-version) | Alla skärmar och funktioner fungerar som de ska. |
| **Mobil Android** |
| Chrome (senaste och tidigare versioner) | Alla skärmar och funktioner fungerar som de ska. |

## <a name="desktop-testing"></a>Skrivbordstestning

Testa ditt visuella objekt i den aktuella versionen av [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

| Testfall | Förväntat resultat
| --------- | ----------------
| Testa alla funktioner i ditt visuella objekt. | Alla skärmar och funktioner fungerar som de ska. |
| Importera, spara, öppna en fil och publicera till Power BI-webbtjänsten med hjälp av knappen **Publicera** i Power BI Desktop. | Alla skärmar och funktioner fungerar som de ska. |
| Ändra strängen för numeriskt format till noll decimaler eller tre decimaler genom att öka eller minska precisionen. | Det visuella objektet visas korrekt. |

## <a name="performance-testing"></a>Prestandatestning

Ditt visuella objekt bör prestera på en acceptabel nivå. Använd utvecklarverktyg för att validera prestandan. Förlita dig inte på visuella tips och konsolens tidsloggar.

| Testfall | Förväntat resultat
| --------- | ----------------
| Skapa ett visuellt objekt med många visuella element. | Det visuella objektet bör fungera bra och inte låsa programmet. Det ska inte finnas några prestandaproblem med element, som animeringens hastighet, storleksändring, filtrering och val.

## <a name="next-steps"></a>Nästa steg

Mer information om publiceringsprocessen finns i [Publicera visuella Power BI-objekt till Partner Center](./office-store.md).

Har du fler frågor? [Fråga Power BI-communityn](https://community.powerbi.com/).
