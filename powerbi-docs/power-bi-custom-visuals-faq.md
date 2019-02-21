---
title: Vanliga frågor och svar om anpassade visuella Power BI-objekt
description: Bläddra i en lista med vanliga frågor och svar om anpassade visuella Power BI-objekt
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 9b4ff995b1cfaede1608e976bf2715feece0ade6
ms.sourcegitcommit: a2f274cfb392fe3b1b466a39ec7eaf58a7c5ce00
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2019
ms.locfileid: "56408148"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Vanliga frågor och svar om anpassade visuella Power BI-objekt

## <a name="organizational-custom-visuals"></a>Anpassade visuella objekt i en organisation

### <a name="how-can-the-admin-manage-the-organizational-custom-visuals"></a>Hur hanterar administratören anpassade visuella objekt i en organisation?

Under fliken ”Anpassade virtuella objekt i organisationen” i administrationsportalen kan administratören se och [hantera alla anpassade visuella objekt i företaget](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals): lägga till, inaktivera, aktivera och ta bort.
Det finns inte längre något behov av att dela dessa visuella objekt via e-postmeddelanden eller en delad mapp! När de anpassade visuella objekten har distribuerats till organisationens lagringsplats kan användarna i organisationen enkelt hitta och importera dem till sina rapporter, direkt från Power BI Desktop eller Power BI-tjänsten. Du kan hitta de anpassade visuella objekten i organisationen i det inbyggda lagret (i Desktop och i tjänsten) på fliken *MIN ORGANISATION*. När administratören laddar upp en ny version av ett anpassat visuellt objekt i organisationen, så hämtar alla i organisationen samma uppdaterade version. Rapportförfattarna behöver inte ta bort de visuella objekten i sina rapporter för att få tillgång till de nya versionerna, eftersom alla rapporter som använder dessa visuella objekt uppdateras automatiskt! Uppdateringsmekanismen påminner om den för visuella marknadsplatsobjekt.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Om en administratör laddar upp ett anpassat visuellt objekt från den offentliga marknadsplatsen till organisationslagret, uppdateras det då automatiskt när leverantören uppdaterar det visuella objektet på den offentliga marknadsplatsen?

Nej, det finns ingen automatisk uppdatering från den offentliga marknadsplatsen.
Det är administratörens ansvar att uppdatera det anpassade visuella objektets version i organisationen.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>Finns det något sätt att inaktivera organisationslagret?

Nej, användarna ser alltid fliken MIN ORGANISATION från Power BI Desktop och Service. Administratören kan inaktivera eller ta bort alla anpassade visuella objekt från administrationsportalen, varvid organisationenslagret töms.
  
### <a name="if-the-administrator-disables-custom-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-custom-visuals"></a>Har användarna fortfarande åtkomst till de anpassade visuella objekten i organisationen om administratören inaktiverar anpassade visuella objekt från administrationsportalen (klientinställningar)?

Ja, om administratören inaktiverar de anpassade visuella objekten från administrationsportalen, så påverkar det inte organisationslagret. Vissa organisationer inaktiverar anpassade visuella objekt och aktiverar endast utvalda visuella objekt som har importerats och laddats upp av Power BI-administratören till organisationslagret. Inaktivering av de anpassade visuella objekten från administrationsportalen verkställs inte i Power BI Desktop. Desktop-användare kan fortfarande lägga till och använda anpassade visuella objekt från den offentliga marknadsplatsen i sina rapporter. Dessa offentliga anpassade visuella objekt upphör att återges så snart de har publicerats till Power BI-tjänsten och utlöser ett fel. När du använder Power BI-tjänsten går det inte att importera anpassade visuella objekt från den offentliga marknadsplatsen. Visuella objekt från organisationslagret kan importeras eftersom inställningen för anpassade visuella objekt i administrationsportalen påtvingas i Power BI-tjänsten.

### <a name="why-does-the-organizational-store-and-organizational-custom-visuals-make-a-great-enterprise-solution"></a>Varför utgör organisationslagret och anpassade visuella objekt en utmärkt företagslösning?

* Alla får samma version av virtuella objekt, vilket kontrolleras av Power BI-administratören. När administratören uppdaterar det visuella objektets version i administratörsportalen får alla användare i organisationen automatiskt tillgång till den uppdaterade versionen.

* Det finns inte längre något behov av att dela visuella filer via e-post eller delade mappar! Ett ställe som är synligt för alla inloggade medlemmar.

* Säkerhet och support, nya versioner av anpassade visuella objekt i organisationen uppdateras automatiskt i alla rapporter som liknar de visuella objekten på marknadsplatsen.

* Användare i organisationen som använder de anpassade visuella objekten i organisationen måste vara inloggade för att kunna se och använda de anpassade visuella objekten, vilket är ett säkerhetselement för organisationen.

* Administratörer kan styra vilka anpassade visuella objekt som ska vara tillgängliga i organisationen.

* Administratörer kan aktivera/inaktivera visuella objekt för testning från administratörsportalen. Bättre säkerhetstillämpning eftersom dessa visuella objekt endast är tillgängliga för organisationens medlemmar.

## <a name="certified-custom-visuals"></a>Certifierade anpassade visuella objekt

### <a name="what-are-certified-custom-visuals"></a>Vad är certifierade anpassade visuella objekt?

Certifierade anpassade visuella objekt är visuella objekt på [marknadsplatsen](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) som uppfyller vissa [specificerade](power-bi-custom-visuals-certified.md) kodkrav och testning av Power BI-teamet.  Testerna som utfördes är utformade för att kontrollera att det visuella objektet inte har tillgång till externa tjänster eller resurser. Microsoft är ändå inte upphovsman till anpassade visuella objekt från tredje part. Vi rekommenderar att kunder kontaktar upphovsmannen direkt för att verifiera funktionaliteten för sådana visuella objekt.

## <a name="visuals-with-additional-purchases"></a>Visuella objekt med ytterligare köp

### <a name="what-is-a-visual-with-additional-purchases"></a>Vad är ett visuellt objekt med ytterligare köp?

Ett visuellt objekt med ytterligare köp liknar köp via app-tillägg (IAP-tillägg) i marknadsplatsen. Dessa tillägg har prislappen **Ytterligare köp kan krävas**.

Anpassade visuella IAP-objekt är kostnadsfria, nedladdningsbara anpassade visuella objekt, så användare behöver inte betala något för att ladda ned de här anpassade visuella objekten från marknadsplatsen. Med visuella IAP-objekt erbjuds valfria köp via app för avancerade funktioner.  

### <a name="whats-the-benefit-to-developers"></a>Vilka fördelar innebär det för utvecklare?

Anpassade visuella IAP-objekt i AppSource är synliga för de många dagliga besökarna, och kan bidra med värdefull trafik och ökad medvetenhet om dina anpassade visuella IAP-objekt och dig som utvecklare.

Tidigare har du kanske hanterat dessa visuella objekt via din webbplats, men nu kan du skicka in dem till AppSource. Det här gör de visuella IAP-objekten mer synliga och lättare att upptäcka inom Power BI-communityn.

Visuella objekt i AppSource har en direkt feedbackkanal från dina kunder som använder det anpassade visuella IAP-objektet, via omdömes- och recensionssystemet i Store.  

När det visuella IAP-objektet har godkänts av AppSource-verifieringsteamet kan du också skicka dessa visuella objekt för certifiering. Det är en valfri process.  

När det visuella objektet har certifierats kan anpassade visuella IAP-objekt exporteras till PowerPoint och visas i de e-postmeddelanden som tas emot när en användare prenumererar på rapportsidor. Så genom att skicka in visuella IAP-objekt till marknadsplatsen kan anpassade visuella IAP-objekt nu också certifieras och få stöd för extra funktioner.  

### <a name="do-iap-visuals-need-to-be-certified"></a>Måste visuella IAP-objekt certifieras?

Certifieringsprocessen är valfri. Det är upp till utvecklaren att avgöra om de vill certifiera anpassade visuella IAP-objekt eller inte, på samma sätt som med kostnadsfria visuella objekt.

### <a name="what-is-changing-in-the-submission-process"></a>Vad ändras i insändningsprocessen?

Det är samma process för att skicka in anpassade visuella IAP-objekt till marknadsplatsen som för att skicka in kostnadsfria visuella objekt. Det görs via instrumentpanelen för försäljning.  Den enda som ändras i insändningsprocessen är att utvecklare måste skriva följande i utvecklaranmärkningarna i instrumentpanelen för försäljning: “Visual with in-app purchase” (”Visuellt objekt med köp via app”). Du måste också tillhandahålla en licensnyckel/token om det behövs för att verifiera avgiftsbelagda/avancerade funktioner.  

Det finns inget nytt alternativ i instrumentpanelen för försäljning: *free with in-app purchases* (kostnadsfritt med köp via app). Du måste därför skicka in dina visuella IAP-objekt som *free* (kostnadsfritt).

Informera därtill användarna i den långa beskrivning i Store om vad de kan förvänta sig, vilka funktioner som är kostnadsfria och vilka funktioner som kräver ytterligare köp för att kunna användas.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>Vad ska jag göra innan jag skickar in mitt anpassade visuella IAP-objekt?

Om du arbetar med ett anpassat visuellt IAP-objekt, eller redan har ett, kontrollerar du att det uppfyller alla riktlinjer.  

Om du har en logotyp i det visuella objektet kontrollerar du att den uppfyller riktlinjerna för logotyper (färg, plats, storlek och utlösning av åtgärder).

I riktlinjerna hittar du också metodtips.  
> [!Note]
> Alla kostnadsfria visuella objekt måste behålla de kostnadsfria funktioner som erbjudits tidigare. Du kan lägga till valfria avancerade betalfunktioner utöver de tidigare kostnadsfria funktionerna. Vi rekommenderar att du skickar visuella IAP-objekt med de avancerade funktionerna som nya visuella objekt och inte uppdaterar de gamla kostnadsfria visuella objekten.


### <a name="can-i-get-my-iap-custom-visual-certified"></a>Kan jag certifiera mina anpassade visuella IAP-objekt?

Ja, precis som med kostnadsfria visuella objekt.  När ditt anpassade visuella IAP-objekt har godkänts av AppSource-teamet kan du skicka in ditt visuella objekt för certifiering.

Ditt visuella objekt måste uppfylla certifieringskraven för att bli certifierat. Det visuella objektet får till exempel inte ha åtkomst till externa tjänster för verifiering av licenser.

Kom ihåg att certifiering är en valfri process och att det är upp till dig om du vill certifiera ditt visuella IAP-objekt eller inte.

## <a name="additional-questions"></a>Fler frågor

### <a name="how-to-get-support"></a>Hur får jag support?

Ta gärna kontakt med supporten för anpassade visuella objekt: *pbicvsupport@microsoft.com* om du har frågor, kommentarer eller problem.  

## <a name="next-steps"></a>Nästa steg

Mer information finns i [Felsöka anpassade visuella objekt i Power BI](power-bi-custom-visuals-troubleshoot.md).
