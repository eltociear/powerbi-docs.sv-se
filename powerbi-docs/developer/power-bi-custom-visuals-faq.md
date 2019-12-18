---
title: Vanliga frågor och svar om visuella Power BI-objekt
description: Bläddra i en lista med vanliga frågor och svar om visuella Power BI-objekt
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 9078aaebd49705833d3ad5a15497ab0c2d69a1c3
ms.sourcegitcommit: 5bb62c630e592af561173e449fc113efd7f84808
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/11/2019
ms.locfileid: "74999731"
---
# <a name="frequently-asked-questions-about-power-bi-visuals"></a>Vanliga frågor och svar om visuella Power BI-objekt

## <a name="organizational-power-bi-visuals"></a>Visuella Power BI-objekt i en organisation

Du kan hantera organisationens visuella Power BI-objekt med hjälp av administratörsportalen.

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>Hur hanterar administratören visuella Power BI-objekt i en organisation?

Under fliken *Virtuella objekt i organisationen* i administrationsportalen kan administratören se och [hantera alla visuella Power BI-objekt i företaget](../service-admin-portal.md#organizational-visuals). Detta innefattar att lägga till, inaktivera, aktivera och ta bort visuella Power BI-objekt.

Användare i organisationen kan enkelt hitta visuella Power BI-objekt och importera dem till sina rapporter direkt från Power BI Desktop eller tjänsten.

När administratören laddar upp en ny version av ett visuellt Power BI-objekt i organisationen, så får alla i organisationen tillgång till samma uppdaterade version. Alla rapporter som använder uppdaterade visuella Power BI-objekt uppdateras automatiskt.

Användare kan hitta organisationens visuella Power BI-objekt i det inbyggda Power BI Desktop- och Power BI-tjänstorganisationslagret under fliken *MIN ORGANISATION*. 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Om en administratör laddar upp ett visuellt Power BI-objekt från den offentliga marknadsplatsen till organisationslagret, innebär det då att det uppdateras automatiskt när leverantören uppdaterar det visuella objektet på den offentliga marknadsplatsen?

Nej, det finns ingen automatisk uppdatering från den offentliga marknadsplatsen. Det är administratörens ansvar att uppdatera det visuella Power BI-objektets version i organisationen.

### <a name="is-there-a-way-to-disable-the-organization-store"></a>Finns det något sätt att inaktivera organisationslagret?

Nej, användarna ser alltid fliken *MIN ORGANISATION* i Power BI Desktop och Power BI-tjänsten. Om en administratör inaktiverar eller tar bort alla visuella Power BI-objekt i organisationen från administratörsportalen, så blir organisationslagret tomt.
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>Har användarna fortfarande åtkomst till de visuella Power BI-objekten i organisationen om administratören inaktiverar visuella Power BI-objekt från administrationsportalen (klientinställningar)?

Ja, om administratören inaktiverar de visuella Power BI-objekten från administrationsportalen, så påverkar det inte organisationslagret.

Vissa organisationer inaktiverar visuella Power BI-objekt och aktiverar endast utvalda visuella objekt som har importerats och laddats upp av Power BI-administratören till organisationslagret.

Inaktivering av de visuella Power BI-objekten från administrationsportalen verkställs inte i Power BI Desktop. Desktop-användare kan fortfarande lägga till och använda visuella Power BI-objekt från den offentliga marknadsplatsen i sina rapporter. Dessa offentliga visuella Power BI-objekt upphör att återges så snart de har publicerats till Power BI-tjänsten och utlöser ett fel. 

När inställningarna för visuella Power BI-objekt i administratörsportalen framtvingas, så kan användarna av Power BI-tjänsten inte importera några visuella Power BI-objekt från den offentliga marknadsplatsen. Endast visuella objekt i organisationsarkivet kan importeras.

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>Vilka är fördelarna med visuella Power BI-objekt i organisationslagret?

* Alla får samma version av de virtuella objekten, vilket kontrolleras av Power BI-administratören. När administratören uppdaterar det visuella objektets version i administratörsportalen får alla användare i organisationen automatiskt tillgång till den uppdaterade versionen.

* Det finns inte något behov av att dela visuella filer via e-post eller delade mappar. Organisationens butikserbjudanden visas för alla inloggade medlemmar.

* Säkerhet och support, nya versioner av visuella Power BI-objekt i organisationen uppdateras automatiskt i alla rapporter.

* Administratörer kan styra vilka visuella Power BI-objekt som ska vara tillgängliga i hela organisationen.

* Administratörer kan aktivera/inaktivera visuella objekt för testning från administratörsportalen.

## <a name="certified-power-bi-visuals"></a>Certifierade visuella Power BI-objekt

### <a name="what-are-certified-power-bi-visuals"></a>Vad är certifierade visuella Power BI-objekt?

Certifierade visuella Power BI-objekt är visuella Power BI-objekt som uppfyller vissa [krav](power-bi-custom-visuals-certified.md)och som har certifierats av Microsoft.

På [marknadsplatsen](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) har certifierade visuella Power BI-objekt en gul skylt som visar att de är certifierade.

Microsoft har inte skapat de visuella Power BI-objekten från tredje part. Vi rekommenderar att kunderna kontaktar skaparna direkt för att få sådana visuella objekts funktionalitet verifierad.

### <a name="what-tests-are-done-during-the-certification-process"></a>Vilka tester utförs under certifieringsprocessen?

Certifieringsprocesstester omfattar men är inte begränsade till: 
* Kodgranskningar
* Statisk kodanalys
* Dataläckage
* Datasårbarhetstestning
* Intrångstest
* Åtkomst till XSS-testning
* Inmatning av skadlig data
* Indatavalidering
* Funktionell testning
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>Kontrolleras certifierade visuella Power BI-objekt igen i samband med varje ny överföring (uppgradering)?

Ja. Varje gång en ny version av certifierat visuellt objekt överförs till Marketplace genomgår versionsuppdateringen av det visuella objektet samma certifieringskontroller.

Versionsuppdateringscertifieringen är automatisk. Om en överträdelse resulterar i att uppdateringen nekas, så skickas ett e-postmeddelande till utvecklaren med en förklaring av vad som behöver åtgärdas.

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>Kan ett certifierat visuellt Power BI-objekt förlora sin certifiering efter en ny uppdatering?

Nej, det är inte möjligt. Ett certifierat visuellt Power BI-objekt kan inte förlora sin certifiering efter en ny uppdatering. Uppdateringen avvisas.
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>Måste jag dela min kod i ett offentligt entrallager om jag certifierar mitt visuella Power BI-objekt?

Nej, du behöver inte dela koden offentligt.

Ange läsbehörigheter om du vill kontrollera koden för det visuella Power BI-objektet. Du kan t.ex. använda ett privat centrallager i GitHub.
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>Måste ett certifierat visuellt Power BI-objekt finnas på marknadsplatsen?

Ja. Privata visuella objekt är inte certifierade.
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>Hur lång tid tar det att certifiera mitt visuella objekt?

Det kan ta upp till fyra veckor att certifiera ett nytt visuellt Power BI-objekt (förstagångscertifiering). 

Att certifiera en uppdaterad version av ett visuellt Power BI-objekt kan ta upp till tre veckor. 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>Garanterar certifieringsprocessen att inget dataläckage sker?

Testerna som utfördes är utformade för att kontrollera att det visuella objektet inte har tillgång till externa tjänster eller resurser. 

Microsoft har inte skapat de visuella Power BI-objekten från tredje part. Vi rekommenderar att kunderna kontaktar skaparna direkt för att få sådana visuella Power BI-objekts funktionalitet verifierad.
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>Är ocertifierade visuella Power BI-objekt säkra att använda?

Ocertifierade visuella Power BI-objekt innebär inte nödvändigtvis osäkra visuella objekt.

Vissa visuella objekt är inte certifierade eftersom de inte är kompatibla med ett eller flera av [certifieringskraven](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified?#certification-requirements). Till exempel att ansluta till en extern tjänst som visuell mappning eller visuella objekt med kommersiella bibliotek.
 
## <a name="visuals-with-additional-purchases"></a>Visuella objekt med ytterligare köp

### <a name="what-is-a-visual-with-additional-purchases"></a>Vad är ett visuellt objekt med ytterligare köp?

Ett visuellt objekt med ytterligare inköp liknar IAP-tillägg (In-App Purchase). De här tilläggen innehåller en prislapp som innebär att **ytterligare inköp kan krävas**.

Visuella IAP Power BI-objekt är kostnadsfria och nedladdningsbara visuella Power BI-objekt. Användare betalar inget för att ladda ned dessa visuella Power BI-objekt från marknadsplatsen.

Med visuella IAP-objekt erbjuds valfria köp via app för avancerade funktioner.  

### <a name="what-is-changing-in-the-submission-process"></a>Vad ändras i insändningsprocessen?

Processen för att skicka in de visuella IAP Power BI-objekten till marknadsplatsen är densamma som för att skicka in kostnadsfria visuella Power BI-objekt. Du kan skicka ett visuellt Power BI-objekt som ska certifieras med hjälp av [Partnercenter](https://docs.microsoft.com/partner-center/).


När du registrerar ditt visuella Power BI-objekt går du till fliken *Produktkonfiguration* och markerar kryssrutan *Produkten kräver köp av en tjänst*.

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>Vad ska jag göra innan jag skickar in mitt visuella IAP Power BI-objekt?

Om du arbetar med ett visuellt IAP Power BI-objekt, så kontrollera att det uppfyller alla [riktlinjer](guidelines-powerbi-visuals.md).  

> [!NOTE]
> Kostnadsfria visuella Power BI-objekt med en tillagd IAP-funktion måste ha samma kostnadsfria funktioner som tidigare erbjudits. Du kan lägga till valfria avancerade betalfunktioner utöver de tidigare kostnadsfria funktionerna. Vi rekommenderar att du skickar in det visuella IAP Power BI-objektet med de avancerade funktionerna som ett nytt visuellt Power BI-objekt istället för att uppdatera den gamla kostnadsfria versionen.

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>Måste visuella IAP Power BI-objekt certifieras?

[Certifierings](power-bi-custom-visuals-certified.md)processen är valfri. Det är upp till utvecklarna att avgöra om de vill certifiera sina visuella IAP Power BI-objekt eller inte.

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>Kan jag få mina visuella IAP Power BI-objekt certifierade?

Ja, så snart som ditt visuella IAP Power BI-objekt har godkänts av AppSource-teamet kan du skicka in ditt visuella Power BI-objekt för [certifiering](power-bi-custom-visuals-certified.md).

Kom ihåg att certifieringen är en valfri process och att det är upp till dig om du vill certifiera ditt visuella IAP-objekt eller inte.

## <a name="additional-questions"></a>Fler frågor

### <a name="how-to-get-support"></a>Hur får jag support?

Ta gärna kontakt med supporten för visuella Power BI-objekt på pbicvsupport@microsoft.com om du har frågor, kommentarer eller problem.  

## <a name="next-steps"></a>Nästa steg

Mer information finns i [Felsöka visuella Power BI-objekt](power-bi-custom-visuals-troubleshoot.md).
