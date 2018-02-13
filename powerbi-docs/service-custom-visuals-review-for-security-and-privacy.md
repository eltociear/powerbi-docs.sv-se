---
title: "Granska anpassade visuella objekt ur säkerhets- och sekretessynvinkel"
description: "Innan du aktiverar ett anpassat visuellt objekt bör du granska objektet ur säkerhets- och sekretessynvinkel för att säkerställa att det uppfyller din organisations standarder."
services: powerbi
documentationcenter: 
author: markingmyname
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
ms.date: 09/05/2017
ms.author: maghan
ms.openlocfilehash: 15f8d9090736a62fdaa53aa3f19e7e0fff127337
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2018
---
# <a name="review-custom-visuals-for-security-and-privacy"></a>Granska anpassade visuella objekt ur säkerhets- och sekretessynvinkel
Innan du aktiverar ett anpassat visuellt objekt bör du granska objektet ur säkerhets- och sekretessynvinkel för att säkerställa att det uppfyller din organisations standarder.

## <a name="enable-a-custom-visual"></a>Aktivera ett anpassat visuellt objekt
<a name="enable"></a>Ett anpassat visuellt objekt i en rapport är inaktiverat tills du väljer **Aktivera anpassad visuell information** enligt nedan.  

![](media/service-custom-visuals-review-for-security-and-privacy/emptyvisual.png)

## <a name="considerations-before-you-enable-a-custom-visual"></a>Att tänka på innan du aktiverar ett anpassat visuellt objekt
<a name="considerations"></a>

> [!WARNING]
> Ett anpassat visuellt objekt kan innehålla kod som innebär säkerhets- eller sekretessrisker. Därför är ett anpassat visuellt objekt i en rapport inaktiverat tills du väljer Aktivera anpassad visuell information. Fundera över följande innan du bestämmer dig för att aktivera ett anpassat visuellt objekt:
> 
> 

1. Säkerställ att du har förtroende för författaren och källan till de anpassade visuella objekten i rapporten.
2. Om du är osäker på vad du ska göra kan du kontakta IT-teamet och fråga dem om du ska aktivera anpassade visuella objekt i rapporter som du tittar på.
3. Om någon delar en rapport med dig som innehåller ett anpassat visuellt objekt, även om det är fråga om en nära medarbetare, ska du inte känna dig skyldig att aktivera det anpassade visuella objektet. Det är okej att ta ett steg tillbaka och fundera över om det är viktigt för den aktuella uppgiften. Det är alltid okej att be någon att förse dig med en rapport utan anpassade visuella objekt, om du känner dig osäker på de anpassade visuella objekten.

## <a name="security-best-practices-for-it-professionals-to-enable-a-custom-visual"></a>Bästa säkerhetspraxis för IT-proffs rörande aktivering av anpassade visuella objekt
<a name="security"></a>

> [!WARNING]
> Ett anpassat visuellt objekt kan innehålla kod som innebär säkerhets- eller sekretessrisker. Därför är ett anpassat visuellt objekt i en rapport inaktiverat tills du väljer Aktivera anpassad visuell information. Det finns flera bästa praxis som du kan följa för att utvärdera ett anpassat visuellt objekt ur säkerhets- och sekretessynvinkel.
> 
> 

1. Inför en granskningsprocess för anpassade visuella objekt i organisationen. Granskade anpassade visuella objekt kan därefter delas med interna användare via en intern webbplats, till exempel ett SharePoint-dokumentbibliotek eller ett OneNote-dokument.
2. Ge vägledning till företagsanvändarna om lämplig användning av anpassade visuella objekt och starta en e-postgrupp för företagsanvändare till vilken de kan skicka frågor om säkerhet och sekretess.
3. Utvärdera JavaScript-koden i en anpassad visuell pbiviz-fil.

**Utvärdera JavaScript-kod i ett anpassat visuellt objekt**

Ett anpassat visuellt objekt använder JavaScript och kan därför medföra säkerhets- och sekretessrisker. Om du får ett anpassat visuellt objekt eller en pbix-fil med ett anpassat visuellt objekt från en okänd källa, kan det vara en bra idé att titta närmare på JavaScriptet för att se om det är säkert.

Extrahera JavaScript-koden för det anpassade visuella objektet för att utvärdera den. Så här extraherar du koden:  

1. Spara pbiviz-filen i en mapp.
2. Döp om filen till en zip-fil.
3. Extrahera zip-filen till en lokal mapp.

## <a name="custom-visual-file-contents"></a>Filinnehåll för ett anpassat visuellt objekt
En pbiviz-fil innehåller följande:

| **Fil** | **Beskrivning** |
|:--- |:--- |
| ./package.json |En manifestfil som anger vilka filer som ska läsas in för det anpassade visuella objektet. |
| ./resources |Innehåller CSS, TypeScript och JavaScript som används av det anpassade visuella objektet. |
| ./resources/&lt;namn&gt; |&lt;Namnet&gt; är namnet på det anpassade visuella objektet. |
| ./resources/&lt;namn&gt;.css |Css-resursfilen för det anpassade visuella objektet. |
| ./resources/&lt;namn&gt;.js |Den kod som körs när en användare klickar på Aktivera anpassad visuell information eller när en användare importerar ett anpassat visuellt objekt. Varning: JavaScript-kod kan medföra säkerhets- eller sekretessrisker. |
| ./resources/&lt;namn&gt;.ts |JavaScript-källkoden för det visuella objektet i TypeScript-format. Varning: JavaScript- eller TypeScript-kod kan medföra säkerhets- eller integritetsrisker. |
| ./resources/&lt;namn&gt;.png |Ikonen som visas för användaren för det visuella objektet. |

Du kan utvärdera koden när du har extraherat pbiviz-filen. Här följer några bästa praxis och hot att hålla utkik efter.

## <a name="best-practices-to-evaluate-the-javascript-or-typescript-code"></a>Bästa praxis för att utvärdera JavaScript- eller TypeScript-kod
**JavaScript**- eller **TypeScript**-kod kan medföra säkerhets- eller integritetsrisker. Här följer några bästa praxis och hot att hålla utkik efter.

### <a name="best-practices-to-evaluate-javascript-code"></a>Bästa praxis för att utvärdera JavaScript-kod
* Utvärdera alltid js-filinnehållet. Det här är den kod som faktiskt körs. Det kan vara så att innehållet i ts-filen inte kompileras till js-filen som ingår i det anpassade visuella objektet.
* Utvärdera alltid ts-filinnehållet. Du kan läsa in ts-filen i **Utvecklarverktyg**, exportera det visuella objektet och jämföra den resulterande js-filen i den nyligen skapade pbiviz-filen med den ursprungliga js-filen i det visuella objektet.
* Kontrollera att ikonen för det anpassade visuella objektet inte är allt för lik den för andra visuella objekt som användaren är bekant med.
* Utvärdera alltid det visuella objektet på ett testkonto som har minimal behörighet och inte har tillgång till känsliga data. Det idealiska är om testkontot är ett lokalt konto utan inloggningsinformation för andra tjänster än Power BI.

### <a name="threats-to-look-for-in-javascript-code"></a>Hot att hålla utkik efter i JavaScript-kod
* Kontrollera nätverksaktiviteten när det visuella objektet används i både redigerings- och visningsläge. Kontrollera att du är nöjd med de begäranden som görs. Du bör inte se begäranden till resurser utanför Power BI-domänen om inte skaparen av det visuella objektet har meddelat detta på förhand.
* Alla data som du ser lämnar Power BI-domänen ska matcha dina förväntningar på ”normal” användning. Till exempel – om det visuella objektet implementerar en videospelare som använder en iFrame för att visa en video från en annan webbplats, bör en del information färdas i IFrame-begärandena för att återge videon korrekt. Men om du ser att hela datauppsättningen skickas i ledningen kan du undersöka vidare om detta krävs och är önskvärt.
* Kontrollera om personligt identifierbara data skickas eller lagras av det anpassade visuella objektet.
* Kontrollera om det anpassade visuella objektet försöker komma åt lokala datorresurser, som att skriva filer till diskar eller använda cookies.
* Kontrollera om det anpassade visuella objektet har något som verkar vara dold kod eller kod utan en tydlig syfte.
* Spara kopior av varje visuellt objekt som du har granskat i det förflutna.
* Om du granskar en uppdatering för ett visuellt objekt som du har granskat tidigare, ska du vara noga med att söka efter ändringar. Var alltid lika grundlig när det gäller uppdateringar som då du fick det visuella objektet för granskning första gången.
* Kontakta oss om du hittar något misstänkt eller oklart, vi finns här för att hjälpa dig.

## <a name="next-steps"></a>Nästa steg
[Visualiseringar i Power BI](power-bi-report-visualizations.md)  
[Anpassade visualiseringar i Power BI](power-bi-custom-visuals.md)  
[Publicera anpassade visuella objekt i Office Store](developer/office-store.md)  
[Komma igång med utvecklarverktyg för anpassade visuella objekt](service-custom-visuals-getting-started-with-developer-tools.md)  
[Så här certifierar du ett anpassat visuellt objekt](power-bi-custom-visuals-certified.md)    
[Video: Skapa anpassade visualiseringar för Power BI med Sachin Patney och Nico Cristache](https://www.youtube.com/watch?v=kULc2VbwjCc)  

Har du fler frågor? [Prova att fråga Power BI Community](http://community.powerbi.com/)

