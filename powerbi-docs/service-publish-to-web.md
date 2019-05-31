---
title: Publicera på webben från Power BI
description: Med Power BI Publicera på webben kan du enkelt bädda in interaktiva Power BI-visualiseringar online, t.ex. blogginlägg, webbplatser, via e-post eller sociala medier på alla enheter.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/16/2019
LocalizationGroup: Share your work
ms.openlocfilehash: 1b5dfc0b05595e96c9a297a5be3700e71cdbe229
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051570"
---
# <a name="publish-to-web-from-power-bi"></a>Publicera på webben från Power BI

Med Power BI **publicera på webben** alternativet kan du enkelt bädda in interaktiva Power BI-visualiseringar online, till exempel i blogginlägg, webbplatser, via e-post eller sociala medier, från valfri enhet. Du kan också enkelt redigera, uppdatera eller sluta dela publicerade visuella objekt.

> [!WARNING]
> När du använder **publicera på webben**, alla på Internet kan visa din publicerade rapporten eller visualiseringen. Det krävs ingen autentisering och innehåller visar data på detaljnivå dina sammanlagda rapporter. Kontrollera att det är ok att dela data och visualiseringar offentligt innan du publicerar en rapport. Publicera inte konfidentiell eller upphovsrättsskyddad information. Om du tvekar, så kontrollera först organisationens principer innan du publicerar.

>[!Note]
>Om du vill bädda in ditt innehåll på ett säkert sätt på en intern portal eller webbplats använder du något av alternativen [Bädda in](service-embed-secure.md) eller [Bädda in i SharePoint Online](service-embed-report-spo.md). Detta säkerställer att alla behörigheter och all datasäkerhet tillämpas när dina användare visar dina interna data.

## <a name="how-to-use-publish-to-web"></a>Så här använder du Publicera på webben

**Publicera på webben** är tillgänglig för rapporter i dina person eller arbetsytor som du kan redigera.  Det är inte tillgänglig för rapporter som delats med dig eller de förlita dig på säkerhet på radnivå för att skydda data. Se den [ **begränsningar** ](#limitations) avsnittet nedan för en fullständig lista över fall där **publicera på webben** stöds inte. Granska den **varning** tidigare i den här artikeln innan du använder **publicera på webben**.

Följande *korta videon* visar hur den här funktionen fungerar. Sedan testa själv i stegen nedan.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

Följande steg beskriver hur du använder **Publicera på webben**.

1. Öppna en rapport i din arbetsyta som du kan redigera och välj **fil > Publicera på webben**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)

2. Granska dialogrutan innehåll och välj **skapa inbäddningskod**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

3. Läs varningen som visas här och bekräfta att data är bäddas in i en offentlig webbplats. Om det är väljer **publicera**.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

4. En dialogruta visas med en länk. Du kan skicka den här länken i ett e-postmeddelande, bädda in den i koden, till exempel en iFrame eller klistra in den direkt i en webbsida eller blogg.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

5. Om du har skapat en inbäddningskod för en rapport och du väljer **publicera på webben**, dialogrutor i steg 2 – 4 visas inte. I stället den **inbäddningskod** dialogruta:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Du kan bara skapa en inbäddningskod för varje rapport.


## <a name="tips-and-tricks-for-view-modes"></a>Tips och tricks för visningslägen

När du bäddar in innehåll i ett blogginlägg måste du vanligtvis det att rymmas inom en specifik skärmstorlek.  Du kan justera höjden och bredden i taggen iFrame efter behov. Dock måste du kontrollera om rapporten passar inom området för angivna iFrame så att du måste också ange ett lämpligt visningsläge när du redigerar rapporten.

Följande tabell innehåller råd om visningsläget och hur det ser ut när det är inbäddat.

| Visningsläge | Hur det ser ut när det är inbäddat |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Anpassa till sida** anpassas efter din rapport sidans höjd och bredd. Om du ställer in sidan på 'Dynamisk' förhållanden som 16:9 eller 4:3 skalas innehållet för att passa iFrame. När den är inbäddad i en iFrame med **Anpassa till sida** kan resultera i **utfyllnad**, där en grå bakgrund visas i iFrame områden efter innehållet som skalas ska rymmas inom iFrame. Om du vill minimera utfyllnaden, du ange din iFrame höjden och bredden på rätt sätt. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Faktisk storlek** säkerställer att rapporten bevarar storleken som angetts på rapportsidan. Detta kan resultera i rullningslister visas i din iFrame. Ange iFrame höjd och bredd för att undvika rullningslister. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Anpassa till bredd** garanterar att innehållet passar i den iFrame vågrätt. En kantlinje visas fortfarande, men innehållet skalas för att använda alla vågrätt utrymme som är tillgängliga. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Tips och tricks för höjd och bredd i iFrame

En **publicera på webben** bädda in se ut så här:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Du kan redigera bredd och höjd manuellt för att kontrollera att det är exakt hur du vill att den ska få plats på sidan där du bäddar in den.

Du kan prova att lägga till 56 bildpunkter i den iFrame höjd för den aktuella storleken för det nedre fältet för att uppnå en mer perfekt passning. Om din rapportsida använder dynamisk storlek, så kan du i tabellen nedan se några storlekar som du kan använda för att uppnå en anpassning utan utfyllnad.

| Proportion | Storlek | Dimension (bredd och höjd) |
| --- | --- | --- |
| 16:9 |Liten |640 x 416 px |
| 16:9 |Medium |800 x 506 px |
| 16:9 |Stor |960 x 596 px |
| 4:3 |Liten |640 x 536 px |
| 4:3 |Medium |800 x 656 px |
| 4:3 |Stor |960 x 776 px |

## <a name="manage-embed-codes"></a>Hantera inbäddningskoder

När du har skapat en **publicera på webben** inbäddningskod, du kan hantera din koder från den **inställningar** menyn i Power BI. Hantering av inbäddningskoder omfattar möjligheten att ta bort det visuella målet eller rapporten för en kod (vilket gör inbäddningskoden oanvändbar), eller hämta inbäddningskoden.

1. Om du vill hantera dina inbäddningskoder för **Publicera på webben** öppnar du **Inställningar** och väljer **Hantera inbäddningskoder**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Inbäddade koder visas.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Du kan hämta eller ta bort en inbäddningskod. Tar bort det inaktiverar alla länkar till rapporten eller visualiseringen.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Om du väljer **ta bort**, du blir tillfrågad om en bekräftelse.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Uppdateringar av rapporter och datauppdatering

När du har skapat din **publicera på webben** inbäddningskoden och dela den rapporten uppdateras med ändringarna du gör och kod inbäddningslänken inbäddningskodslänken omedelbart aktiv och alla som öppnar länken kan visa den. Efter den här inledande åtgärd, men kan uppdateringarna av rapporter och visuella objekt ta ungefär en timme innan den blir synlig för användarna. Om du vill att dina uppdateringar ska vara omedelbart tillgängliga, så kan du ta bort inbäddningskoden och skapa en ny. Mer information finns i den [ **hur det fungerar** ](#howitworks) senare i den här artikeln. 

## <a name="data-refresh"></a>Datauppdatering

Datauppdateringarna återspeglas automatiskt i din inbäddade rapport eller visuella objekt. Det kan ta ungefär en timma för datauppdateringarna att bli synliga från inbäddningskoder. Om du vill inaktivera automatisk uppdatering kan du välja **uppdateras inte** på schemat för den datauppsättning som används.  

## <a name="custom-visuals"></a>Anpassade visuella objekt

Anpassade visuella objekt stöds i **Publicera på webben**. När du använder **publicera på webben**, användare som du delar ditt publicerade visuella objekt behöver inte aktivera anpassade visuella objekt att visa rapporten.

## <a name="limitations"></a>Begränsningar

**Publicera på webben** stöds för merparten av alla datakällor och rapporter i Power BI-tjänsten, men följande stöds **inte för närvarande eller är inte tillgängligt** med **publicera på webben** :

- Rapporter som använder säkerhet på radnivå.
- Rapporter som använder en datakälla för Live-anslutning, som Analysis Services Tabular på lokala flerdimensionella Analysis Services och Azure Analysis Services.
- Rapporter om delas med dig direkt eller via ett organisationsinnehållspaket.
- Rapporter i en grupp som du inte är redigeringsmedlem i.
- Visuella R-objekt stöds inte för närvarande i **publicera på webben** rapporter.
- Exportera Data från visualiseringar i en rapport, har som publicerats på webben.
- ArcGIS Maps for Power BI visuella objekt.
- Rapporter som innehåller Rapportnivå DAX-mått.
- Data för enkel inloggning för fråga modeller.
- [Säkra konfidentiell eller upphovsrättsskyddad information](#publish-to-web-from-power-bi).
- Den automatiska autentiseringsfunktionen som tillhandahålls av alternativet **Bädda in** fungerar inte med Power BI JavaScript-API:et. När det gäller Power BI JavaScript-API:et använder du metoden [användaren äger data](developer/embed-sample-for-your-organization.md) för inbäddning. Läs mer om [användaren äger data](developer/embed-sample-for-your-organization.md).

## <a name="tenant-setting"></a>Klientinställning

Power BI-administratörer kan aktivera eller inaktivera den **publicera på webben** funktionen. De kan också begränsa åtkomsten till specifika grupper som kan påverka din möjlighet att skapa en inbäddningskod.

|Visning av aktuellt objekt |Aktiverad för hela organisationen |Inaktiverad för hela organisationen |Specifika säkerhetsgrupper   |
|---------|---------|---------|---------|
|**Publicera på webben** under rapportens **filen** menyn|Aktiverad för alla|Inte synlig för alla|Endast synlig för behöriga användare eller grupper.|
|**Hantera inbäddade koder** under **Inställningar**|Aktiverad för alla|Aktiverad för alla|Aktiverad för alla.<br><br>Alternativet * **Ta bort** endast för behöriga användare eller grupper.<br>* **Hämta koder** aktiverat för alla.|
|**Inbäddade koder** i administrationsportalen|Statusen visas något av följande:<br>* Aktiv<br>* Stöds ej<br>* Blockerad|Statusen visar **Inaktiverad**|Statusen visas något av följande:<br>* Aktiv<br>* Stöds ej<br>* Blockerad<br><br>Om en användare inte har behörighet baserad på klientinställningen, visas statusen som **intrång**.|
|Befintliga publicerade rapporter|Alla aktiverade|Alla inaktiverade|Rapporter fortsätta att visas för alla.|

## <a name="understanding-the-embed-code-status-column"></a>Förstå statuskolumnen för inbäddningskod

Den **hantera inbäddningskoder** sidan innehåller en statuskolumn. Bädda in koder som standard är **Active**, men kan också vara något av de statusar som visas nedan.

| Status | Beskrivning |
| --- | --- |
| **Aktiv** |Rapporten är tillgänglig för Internet-användare kan visa och interagera med den. |
| **Blockerad** |Innehållet i rapporten strider mot den [Power BI användarvillkoren](https://powerbi.microsoft.com/terms-of-service). Microsoft har blockerat den. Kontakta supporten om du tror att innehållet har blockerats av misstag. |
| **Stöds ej** |Rapportens datauppsättning använder säkerhet på radnivå eller en annan konfiguration som inte stöds. Se den [ **begränsningar** ](#limitations) för en fullständig lista. |
| **Intrång** |Den inbäddade koden ligger utanför den definierade Klientprincipen. Detta uppstår vanligen när en inbäddningskod har skapats och sedan den **publicera på webben** för klienten har ändrats för att exkludera användaren som äger den inbäddade koden. Om klientinställningen är inaktiverad eller om användaren inte längre kan skapa inbäddade koder, befintliga inbäddade koder show en **intrång** status. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Hur man rapporterar problem med innehåll för Publicera på webben

Att rapportera ett problem som rör **publicera på webben** innehåll som är inbäddad i en webbplats eller blogg, Använd den **flaggan** i det nedre fältet som du ser i följande bild. Du kommer att bli ombedd att skicka ett e-postmeddelande till Microsoft förklarar ditt problem. Microsoft utvärderar innehållet baserat på Power BI användarvillkoren och vidta lämpliga åtgärder.

Om du vill rapportera ett problem, Välj den **flaggan** ikon i det nedre fältet i den **publicera på webben** rapportera visas.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licensiering och prissättning

Du måste vara en Microsoft Power BI-användare för att kunna använda **Publicera på webben**. Din Rapportgranskare behöver inte vara Power BI-användare.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Så här fungerar det (teknisk information)

När du skapar en inbäddningskod med **publicera på webben**, syns rapporten för Internet-användare. Det är allmänt tillgängliga, så du kan förvänta dig att enkelt dela rapporten via sociala medier i framtiden användarna. När användarna visar rapporten, antingen genom att öppna den offentliga URL:en direkt, eller visa den inbäddad på en webbsida eller i en blogg, så cachelagrar Power BI rapportdefinitionen och resultaten för de frågor som krävs för att visa rapporten. Detta säkerställer att tusentals samtidiga användare kan visa rapporten utan att påverka prestanda.

Cacheminnet är långlivat, så om du uppdaterar rapportdefinitionen (till exempel, om du ändrar dess visningsläge) eller uppdaterar rapportdata, kan det ta ungefär en timme innan ändringarna avspeglas i versionen av rapporten visa för användarna. Därför rekommenderar vi att du mellanlagrar ditt arbete i förväg och skapa inbäddningskoden för **Publicera på webben** enbart när du är nöjd med inställningarna.

## <a name="next-steps"></a>Nästa steg

- [SharePoint Onlines rapportwebbdel](service-embed-report-spo.md) 

- [Bädda in en rapport på en säker portal eller webbplats](service-embed-secure.md)

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
