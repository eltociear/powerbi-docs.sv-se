---
title: Publicera på webben från Power BI
description: Med Power BI Publicera på webben kan du enkelt bädda in interaktiva Power BI-visualiseringar online, t.ex. blogginlägg, webbplatser, via e-post eller sociala medier på alla enheter.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/25/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 34754f413cd6bb8e520ff8d7f2c9d4a28da73ef5
ms.sourcegitcommit: 032a77f2367ca937f45e7e751997d7b7d0e89ee2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609917"
---
# <a name="publish-to-web-from-power-bi"></a>Publicera på webben från Power BI

Med Power BI-alternativet **Publicera på webben** kan du enkelt bädda in interaktiva Power BI-visualiseringar online, till exempel blogginlägg, webbplatser, via e-post eller sociala medier från valfri enhet. Du kan också enkelt redigera, uppdatera eller sluta dela publicerade visuella objekt.

> [!WARNING]
> När du använder **Publicera på webben** kan vem som helst på Internet titta på din publicerade rapport eller ditt visuella objekt. Detta kräver ingen autentisering och omfattar visning av data på detaljnivå som dina rapporter aggregerar. Innan du publicerar en rapport bör du kontrollera att det går bra att du delar data och visualiseringar offentligt. Publicera inte konfidentiell eller upphovsrättsskyddad information. Om du tvekar, så kontrollera först organisationens principer innan du publicerar.

>[!Note]
>Om du vill bädda in ditt innehåll på ett säkert sätt på en intern portal eller webbplats använder du något av alternativen [Bädda in](service-embed-secure.md) eller [Bädda in i SharePoint Online](service-embed-report-spo.md). Detta säkerställer att alla behörigheter och all datasäkerhet tillämpas när dina användare visar dina interna data.

## <a name="how-to-use-publish-to-web"></a>Så här använder du Publicera på webben

**Publicera på webben** är tillgängligt för rapporter som du kan redigera på dina personliga arbetsytor och grupparbetsytor.  Det är inte tillgängligt för rapporter som delas med dig eller sådana som använder säkerhet på radnivå för att skydda data. I avsnittet [**Begränsningar**](#limitations) nedan finns en fullständig lista över fall där **Publicera på webben** inte stöds. Läs avsnittet **Varning** tidigare i den här artikeln innan du använder **Publicera på webben**.

Följande korta video visar hur den här funktionen fungerar. Sedan kan du prova själv med stegen nedan.

<iframe width="560" height="315" src="https://www.youtube.com/embed/UF9QtqE7s4Y" frameborder="0" allowfullscreen></iframe>

Följande steg beskriver hur du använder **Publicera på webben**.

1. Öppna en rapport på din arbetsyta som du kan redigera och välj **Arkiv > Publicera på webben**.

   ![PtW1](media/service-publish-to-web/publish_to_web1.png)
   
2. Kontakta [Power BI-administratören](service-admin-role.md) om du inte har fått behörighet att skapa inbäddningskoder

   ![PtW1](media/service-publish-to-web/publish_to_web_admin_prompt.png)
   
   Om du vill ha hjälp med att hitta den person som kan aktivera publicera på webben i din organisation kan du [se dessa tips](#how-to-find-your-power-bi-administrator).

3. Granska innehållet i dialogrutan och välj **Skapa inbäddningskod**.

   ![PtW2](media/service-publish-to-web/publish_to_web2_ga.png)

4. Läs den varning som visas här och bekräfta att det är OK om dessa data bäddas in på en offentlig webbplats. Välj **Publicera** om så är fallet.

   ![PtW3](media/service-publish-to-web/publish_to_web3_ga.png)

5. En dialogruta visas med en länk. Du kan skicka den här länken i ett e-postmeddelande, bädda in den i kod såsom en iFrame eller klistra in den direkt på en webbplats eller blogg.

   ![PtW4](media/service-publish-to-web/publish_to_web4.png)

6. Om du tidigare skapade en inbäddningskod för en rapport och väljer **Publicera på webben** ser du inte dialogrutorna i steg 2–4. I stället visas dialogrutan **Inbäddningskod**:

   ![PtW5](media/service-publish-to-web/publish_to_web5.png)

   Du kan bara skapa en inbäddningskod för varje rapport.


## <a name="tips-and-tricks-for-view-modes"></a>Tips och tricks för visningslägen

När du bäddar in innehåll i ett blogginlägg behöver du normalt få det att rymmas inom en viss skärmstorlek.  Du kan justera höjden och bredden i iFrame-taggen efter behov. Dock behöver du se till att rapporten ryms i det aktuella iFrame-området. Därför behöver du även ange ett lämpligt visningsläge när du redigerar rapporten.

Följande tabell innehåller råd om visningsläget och hur det ser ut när det är inbäddat.

| Visningsläge | Hur det ser ut när det är inbäddat |
| --- | --- |
| ![PtW6b](media/service-publish-to-web/publish_to_web6b.png) |**Anpassa till sida** tar hänsyn till rapportens sidhöjd och sidbredd. Om du ställer in sidan på *dynamiska* förhållanden såsom 16:9 eller 4:3, så skalas innehållet så att det passar i iFrame. Vid inbäddning i en iFrame kan användning av **Anpassa till sida** resultera i *letterbox-format*, där en grå bakgrund visas i iFrame-områden när innehållet har skalats för att rymmas i iFrame. Om du vill minimera letterbox-formatet anger du lämplig höjd och bredd för iFrame. |
| ![PtW6d](media/service-publish-to-web/publish_to_web6d.png) |**Faktisk storlek** säkerställer att rapporten bevarar den storlek som angetts på rapportsidan. Detta kan resultera i rullningslister i iFrame. Ange höjd och bredd för iFrame så att du kan undvika rullningslister. |
| ![PtW6c](media/service-publish-to-web/publish_to_web6c.png) |**Anpassa till bredd** säkerställer att innehållet passar det vågräta iFrame-området. En kant visas fortfarande, men innehållet skalas så att allt tillgängligt vågrätt utrymme används. |

## <a name="tips-and-tricks-for-iframe-height-and-width"></a>Tips och tricks för höjd och bredd i iFrame

En inbäddningskod för **Publicera på webben** ser ut som i följande exempel:

![PtW7](media/service-publish-to-web/publish_to_web7.png)
 
Du kan redigera bredd och höjd manuellt så att det blir exakt som du vill att det ska passa in på den sida där du bäddar in.

Du kan prova att lägga till 56 bildpunkter till iFrame-höjden för att ta hänsyn till det nedre fältets aktuella storlek och uppnå en mer exakt anpassning. Om din rapportsida använder dynamisk storlek kan du använda någon av storlekarna i tabellen nedan för att uppnå en anpassning utan letterbox-format.

| Proportion | Storlek | Dimension (bredd och höjd) |
| --- | --- | --- |
| 16:9 |Liten |640 x 416 px |
| 16:9 |Medium |800 x 506 px |
| 16:9 |Stor |960 x 596 px |
| 4:3 |Liten |640 x 536 px |
| 4:3 |Medium |800 x 656 px |
| 4:3 |Stor |960 x 776 px |

## <a name="manage-embed-codes"></a>Hantera inbäddningskoder

När du skapar en inbäddningskod för **Publicera på webben** kan du hantera koderna på menyn **Inställningar** i Power BI. Hantering av inbäddningskoder omfattar möjligheten att ta bort målvisualiseringen eller -rapporten för en kod (vilket gör inbäddningskoden oanvändbar) eller hämta inbäddningskoden.

1. Om du vill hantera dina inbäddningskoder för **Publicera på webben** öppnar du **Inställningar** och väljer **Hantera inbäddningskoder**.

   ![PtW8](media/service-publish-to-web/publish_to_web8.png)

2. Inbäddningskoderna visas.

   ![PtW9](media/service-publish-to-web/publish_to_web9.png)

3. Du kan antingen hämta eller ta bort en inbäddningskod. Om du tar bort den inaktiverar eventuella länkar till den rapporten eller visualiseringen.

   ![PtW10](media/service-publish-to-web/publish_to_web10.png)

4. Om du väljer **Ta bort** uppmanas du att bekräfta.

   ![PtW11](media/service-publish-to-web/publish_to_web11.png)

## <a name="updates-to-reports-and-data-refresh"></a>Uppdateringar av rapporter och datauppdatering

När du har skapat inbäddningskoden för **Publicera på webben** och delat den uppdateras rapporten med eventuella ändringar som du gör, och länken för inbäddningskoden blir aktiv omedelbart. Alla som öppnar länken kan visa den. Efter den här inledande åtgärden kan dock uppdateringar av rapporter eller visuella objekt ta två till tre timmar innan de blir synliga för användarna. Mer information finns i avsnittet [**Så här fungerar det**](#howitworks) längre fram i den här artikeln. 

## <a name="data-refresh"></a>Datauppdatering

Datauppdateringarna återspeglas automatiskt i din inbäddade rapport eller visuella objekt. Det kan ta ungefär en timme för uppdaterade data att bli synliga från inbäddningskoder. Du kan inaktivera automatisk uppdatering genom att välja **Uppdatera inte** på schemat för den datamängd som används av rapporten.  

## <a name="custom-visuals"></a>Anpassade visuella objekt

Anpassade visuella objekt stöds i **Publicera på webben**. När du använder **Publicera på webben** behöver inte användare som du delar det publicerade visuella objektet med aktivera anpassade visuella objekt för att kunna visa rapporten.

## <a name="limitations"></a>Begränsningar

**Publicera på webben** stöds för de allra flesta datakällor och rapporter i Power BI-tjänsten. Följande saknar dock stöd och är för närvarande inte tillgängliga med **Publicera på webben**:

- Rapporter som använder säkerhet på radnivå.
- Rapporter som använder en datakälla för Live-anslutning, som Analysis Services Tabular på lokala flerdimensionella Analysis Services och Azure Analysis Services.
- Rapporter om delas med dig direkt eller via ett organisationsinnehållspaket.
- Rapporter i en grupp som du inte är redigeringsmedlem i.
- Visuella R-objekt stöds för närvarande inte i **Publicera på webben**-rapporter.
- Exportera data från visuella objekt i en rapport som har publicerats på webben.
- ArcGIS Maps för Power BI-visualiseringar.
- Rapporter som innehåller DAX-mått på rapportnivå.
- Datafrågemodeller för enkel inloggning.
- Skydda konfidentiell eller upphovsrättsskyddad information.
- [Delade och certifierade datamängder](service-datasets-share.md).
- Den automatiska autentiseringsfunktionen som tillhandahålls av alternativet **Bädda in** fungerar inte med Power BI JavaScript-API:et. När det gäller Power BI JavaScript-API:et använder du metoden [användaren äger data](developer/embed-sample-for-your-organization.md) för inbäddning.

## <a name="tenant-setting"></a>Klientinställning

Inställningen **Publicera på webben** tillhandahåller alternativ för vilka användare kan skapa inbäddningskoder.

![Inställningen publicera på webben](media/service-admin-portal/powerbi-admin-publish-to-web-setting.png)

Du uppmanas att be en Power BI-administratör skapa en inbäddningskod när alternativet **Välj hur inbäddningskoder ska fungera** är inställt på **Tillåt endast befintliga inbäddningskoder** och inställningen **Publicera till webben** är **Aktiverad**.

![Uppmaning om att publicera på webben](media/service-publish-to-web/publish_to_web_admin_prompt.png)

Power BI-administratörer kan aktivera eller inaktivera funktionen **Publicera på webben**. De kan även begränsa åtkomsten till specifika grupper, vilket kan påverka din möjlighet att skapa en inbäddningskod. Du ser olika alternativ i användargränssnittet baserat på vad inställningen för **Publicera på webben** är.

|Funktion |Aktiverad för hela organisationen |Inaktiverad för hela organisationen |Specifika säkerhetsgrupper   |
|---------|---------|---------|---------|
|**Publicera på webben** under rapportens **Arkiv**-meny|Aktiverad för alla|Inte synlig för alla|Endast synlig för behöriga användare eller grupper.|
|**Hantera inbäddade koder** under **Inställningar**|Aktiverad för alla|Aktiverad för alla|Aktiverad för alla.<br><br>Alternativet * **Ta bort** endast för behöriga användare eller grupper.<br>* **Hämta koder** aktiverat för alla.|
|**Inbäddade koder** i administrationsportalen|Statusen visar något av följande:<br>* Aktiv<br>* Stöds ej<br>* Blockerad|Statusen visar **Inaktiverad**|Statusen visar något av följande:<br>* Aktiv<br>* Stöds ej<br>* Blockerad<br><br>Om en användare inte har behörighet baserad på klientinställningen, visas statusen som **intrång**.|
|Befintliga publicerade rapporter|Alla aktiverade|Alla inaktiverade|Rapporter fortsätta att visas för alla.|

## <a name="understanding-the-embed-code-status-column"></a>Förstå statuskolumnen för inbäddningskod

>[!Note]
>Du bör regelbundet granska de inbäddningskoder som du har publicerat och ta bort dem som inte längre behöver vara tillgängliga offentligt. 

Sidan **Hantera inbäddningskoder** innehåller en statuskolumn. Som standard är inbäddningskoder **aktiva**, men de kan även ha någon av de statusar som anges nedan.

| Status | Beskrivning |
| --- | --- |
| **Aktiv** |Rapporten är tillgänglig för Internet-användare kan visa och interagera med den. |
| **Blockerad** |Rapportinnehållet strider mot [användningsvillkoren för Power BI](https://powerbi.microsoft.com/terms-of-service). Microsoft har blockerat det. Kontakta supporten om du tror att innehållet har blockerats av misstag. |
| **Stöds ej** |Rapportens datauppsättning använder säkerhet på radnivå eller en annan konfiguration som inte stöds. En fullständig lista finns i avsnittet [**Begränsningar**](#limitations). |
| **Intrång** |Inbäddningskoden ligger utanför den definierade klientorganisationsprincipen. Detta inträffar vanligtvis när en inbäddningskod har skapats och klientorganisationsinställningen **Publicera på webben** ändrats till att exkludera den användare som äger inbäddningskoden. Om klientorganisationsinställningen är inaktiverad, eller om användaren inte längre kan skapa inbäddningskoder, visar befintliga inbäddningskoder statusen **Intrång**. |

## <a name="how-to-report-a-concern-with-publish-to-web-content"></a>Hur man rapporterar problem med innehåll för Publicera på webben

Om du vill rapportera ett problem som rör **Publicera på webben**-innehåll som bäddats in på en webbplats eller en blogg använder du **flaggikonen** i fältet längst ned, såsom visas på följande bild. Du ombeds att skicka ett e-postmeddelande till Microsoft som förklarar problemet. Microsoft utvärderar innehållet baserat på användningsvillkoren för Power BI och vidtar lämpliga åtgärder.

Om du vill rapportera ett problem använder du **flaggikonen** i fältet längst ned i den **Publicera på webben**-rapport som du ser.

![PtW12](media/service-publish-to-web/publish_to_web12_ga.png)

## <a name="licensing-and-pricing"></a>Licensiering och prissättning

Du måste vara en Microsoft Power BI-användare för att kunna använda **Publicera på webben**. Rapportens läsare behöver inte vara Power BI-användare.

<a name="howitworks"></a>
## <a name="how-it-works-technical-details"></a>Så här fungerar det (teknisk information)

När du skapar en inbäddningskod med hjälp av **Publicera på webben** görs rapporten synlig för Internetanvändare. Den är offentligt tillgänglig, så du kan förvänta dig att användarna enkelt kan dela rapporten via sociala medier i framtiden. När användarna visar rapporten, antingen genom att öppna den offentliga URL:en direkt, eller visa den inbäddad på en webbsida eller i en blogg, så cachelagrar Power BI rapportdefinitionen och resultaten för de frågor som krävs för att visa rapporten. Detta säkerställer att tusentals samtidiga användare kan visa rapporten utan att påverka prestanda.

Cacheminnet är långlivat, så om du uppdaterar rapportdefinitionen (genom att t.ex. ändra dess visningsläge) eller uppdaterar rapportdata, så kan det ta ungefär en timme innan ändringarna avspeglas i den version av rapporten som användarna ser. Därför rekommenderar vi att du mellanlagrar ditt arbete i förväg och skapa inbäddningskoden för **Publicera på webben** enbart när du är nöjd med inställningarna.

## <a name="how-to-find-your-power-bi-administrator"></a>Så här hittar du din Power BI-administratör

Om du vill ändra [Klientinställningar för publicera på webben](#tenant-setting) måste du arbeta med organisationens [Power BI-administratör](service-admin-role.md).

För mindre organisationer eller individer som registrerat sig för Power BI kanske du inte har en Power BI-administratör ännu. Du måste följa vår [process för klientadministratörsövertagande](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover). När du har en Power BI-administratör kan denne aktivera att skapa inbäddningskoder åt dig.

Etablerade organisationer har vanligtvis redan en Power BI-administratör. Personer i någon av följande roller kan fungera som Power BI-administratör:

- Office 365-administratörer
- Azure Active Directory-administratörer
- Användare med rollen Power BI-tjänstadministratör i Azure Active Directory

Du måste [hitta någon av dessa personer](https://docs.microsoft.com/office365/admin/admin-overview/admin-overview#who-has-admin-permissions-in-my-business) i din organisation så de kan uppdatera inställningen.


## <a name="next-steps"></a>Nästa steg

- [SharePoint Onlines rapportwebbdel](service-embed-report-spo.md) 

- [Bädda in en rapport på en säker portal eller webbplats](service-embed-secure.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
