---
title: 'DAX: Undvik att omvandla tomma värden till värden'
description: Vägledning kring att omvandla tomma värden till värden.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/24/2019
ms.author: v-pemyer
ms.openlocfilehash: 2f70b98ed540a2e5b87e5a949e30b0c1c02069d1
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700396"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX: Undvik att omvandla tomma värden till värden

När du skriver måttuttryck som datamodellerare kan du stöta på fall där det inte går att returnera något meningsfullt värde. Då kan det vara lockande att istället returnera ett neutralt värde, som noll. Vi rekommenderar att du noga överväger om en sådan design skulle vara effektiv och praktisk.

Titta på följande måttdefinition som explicit omvandlar tomma resultat till noll.

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

Titta på en annan måttdefinition som också omvandlar tomma resultat till noll.

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

Funktionen [DIVIDE](/dax/divide-function-dax) delar måttet **Profit** med måttet **Sales**. Om resultatet är noll eller tomt returneras det tredje argumentet, det alternativa resultatet (som är valfritt). Eftersom noll skickas som alternativt resultat i exemplet så returnerar måttet alltid ett värde.

En sådan måttdesign är ineffektiv och leder till dåligt fungerande rapporter.

När de läggs till i ett visuellt rapportobjekt försöker Power BI hämta alla grupperingar inom filterkontexten. Utvärdering och hämtning av stora frågeresultat gör ofta att rapportåtergivningen tar lång tid. Varje mått i exemplet gör en gles beräkning till en tät, så att Power BI måste använda mer minne än nödvändigt.

För många grupperingar kan också vara förvirrande för användarna.

Nu ska vi se vad som händer när måttet **Profit Margin** läggs till i ett visuellt tabellobjekt med gruppering efter kund.

![Ett visuellt tabellobjekt har tre kolumner: Customer, Sales och Profit Margin. Du ser ungefär 10 rader data i tabellen, men den lodräta rullningslisten visar att det finns många fler rader som kan visas. Du ser inga värden i kolumnen Sales. I kolumnen Profit Margin visas bara noll.](media/dax-avoid-converting-blank/table-visual-poor.png)

Det visuella tabellobjektet har ett orimligt stort antal rader. (Det finns i själva verket 18 484 kunder i modellen, och tabellen försöker visa samtliga.) Observera att kunderna i vyn inte har någon försäljning. Men eftersom måttet **Profit Margin** alltid returnerar ett värde så visas de ändå.

> [!NOTE]
> När det finns för många datapunkter att visa i ett visuellt objekt kan Power BI använda strategier för datareducering till att ta bort eller sammanfatta stora frågeresultat. Läs mer om det här i [Datapunktsbegränsningar och strategier efter visuell typ](../visuals/power-bi-data-points.md).

Nu ska vi se vad som händer med en bättre definition av måttet **Profit Margin**. Nu returneras bara ett värde när måttet **Sales** inte är tomt (eller noll).

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

Nu visas bara kunder som har en försäljning i den aktuella filterkontexten i det visuella tabellobjektet. Det förbättrade måttet gör rapportmiljön mer effektiv och praktisk för användarna.

![Samma visuella tabellobjekt med fyra datarader. Varje rad avser en kund som har ett försäljningsvärde, och vinstmarginalen är skild från noll.](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> Om det behövs kan du konfigurera det visuella objektet så att alla grupperingar visas (de som returnerar värden eller är tomma) i filterkontexten genom att aktivera alternativet [Visa poster utan data](../desktop-show-items-no-data.md).

## <a name="recommendation"></a>Rekommendation

Vi rekommenderar att dina mått returnerar BLANK när det inte går att returnera något meningsfullt värde.

Den här designmetoden är effektiv och gör att Power BI kan återge rapporter snabbare. Det är också bättre att returnera BLANK eftersom visuella rapportobjekt som standard eliminerar grupperingar med tomma summor.

## <a name="next-steps"></a>Nästa steg

Mer information om den här artikeln finns i följande resurser:

- [Data Analysis uttryck (DAX)-referens](/dax/)
- Har du några frågor? [Fråga Power BI Community](https://community.powerbi.com/)
