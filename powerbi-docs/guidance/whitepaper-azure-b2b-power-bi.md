---
title: Distribuera Power BI-innehåll till externa gästanvändare med Azure Active Directory B2B
description: Fakta blad som beskriver hur du använder Azure Active Directory B2B för att distribuera Power BI till externa gäst användare
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 2783f434e2bb1d6d45ed1a9442c60da7b09e7ae4
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85782796"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribuera Power BI-innehåll till externa gästanvändare med Azure Active Directory B2B

**Sammanfattning:** Det här är ett tekniskt whitepaper som beskriver hur du distribuerar innehåll till användare utanför organisationen med hjälp av integreringen av Azure Active Directory Business-to-Business (Azure AD B2B).

**Skribenter:** Lukasz Pawlowski, Kasper de Jonge

**Teknisk granskare:** Adam Wilson, Sheng LiU, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, Maya Shenhav, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> Du kan spara eller skriva ut detta whitepaper genom att välja **Skriv ut** i webbläsaren och sedan välja **Spara som PDF**.

## <a name="introduction"></a>Introduktion

Power BI ger organisationer en 360-graders vy över sin verksamhet och ger alla i dessa organisationer möjlighet att fatta intelligenta beslut med hjälp av data. Många av dessa organisationer har starka och betrodda relationer med externa partners, klienter och leverantörer. Dessa organisationer behöver ge säker åtkomst till Power BI instrument paneler och rapporter till användare i dessa externa partner.

Power BI integreras med [Azure Active Directory Business-to-Business (Azure AD B2B)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) för att tillåta säker distribution av Power BI innehåll till gäst användare utanför organisationen, samtidigt som den fortfarande behåller kontrollen och styr åtkomsten till interna data.

Den här white paper omfattar all information som du behöver för att förstå Power BI s integrering med Azure Active Directory B2B. Vi tar det vanligaste användnings fallet, installation, licensiering och säkerhet på radnivå.

> [!NOTE]
> Under den här white paper kan vi se Azure Active Directory som Azure AD och Azure Active Directory affärs verksamhet som Azure AD B2B.

## <a name="scenarios"></a>Scenarier

Contoso är ett bil tillverkare som arbetar med många olika leverantörer som tillhandahåller det med alla komponenter, material och tjänster som krävs för att köra dess tillverknings åtgärder. Contoso vill effektivisera sin logistik för leverans kedjan och planera för att använda Power BI för att övervaka nyckel prestanda mått för sin leverans kedja. Contoso vill dela med externa partner för leverans kedja på ett säkert och hanterbart sätt.

Contoso kan aktivera följande upplevelser för externa användare som använder Power BI och Azure AD B2B.

### <a name="ad-hoc-per-item-sharing"></a>Ad hoc-delning per objekt

Contoso fungerar med en leverantör som skapar radiatorer för Contosos bilar. De måste ofta optimera tillförlitligheten hos radiatorer med data från alla Contosos bilar. En analytiker på Contoso använder Power BI för att dela en Tillförlitlighets rapport för utstrålaren med en tekniker hos leverantören. Teknikern får ett e-postmeddelande med en länk för att visa rapporten.

Som det beskrivs ovan utförs den här ad hoc-delningen av företags användare vid behov. Länken som skickas av Power BI till den externa användaren är en Azure AD B2B-inbjudan. När den externa användaren öppnar länken uppmanas de att delta i Contosos Azure AD-organisation som gäst användare. När inbjudan har accepterats öppnar länken den aktuella rapporten eller instrument panelen. Azure Active Directory administratören delegerar behörighet att bjuda in externa användare till organisationen och väljer vad dessa användare kan göra när de godkänner inbjudan enligt beskrivningen i avsnittet styrning i det här dokumentet. Contoso-analytikern kan endast bjuda in gäst användaren på grund av att Azure AD-administratören har tillåtit åtgärden och Power BI-administratören har tillåtit användare att bjuda in gäster att visa innehåll i Power BIs klient inställningar.

![Bjud in gäster att Power BI med AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. Processen börjar med en intern contoso-användare som delar en instrument panel eller en rapport med en extern användare. Om den externa användaren inte redan är en gäst i Contosos Azure AD, bjuds de in. Ett e-postmeddelande skickas till sin e-postadress som innehåller en inbjudan till Contosos Azure AD
2. Mottagaren accepterar inbjudan till Contosos Azure AD och läggs till som gäst användare i Contosos Azure AD.
3. Mottagaren omdirigeras sedan till Power BI instrument panel, rapport eller app, som är skrivskyddad för användaren.

Processen anses vara ad hoc eftersom företags användare i Contoso utför inbjudan att bjuda in dem i affärs syfte. Varje objekt som delas är en enskild länk som den externa användaren kan komma åt för att visa innehållet.

När den externa användaren har bjudits in för att komma åt contoso-resurser kan ett skugg konto skapas för dem i Contoso Azure AD och de behöver inte bjudas in igen.  Första gången de försöker komma åt en Contoso-resurs, till exempel en Power BI instrument panel, går de igenom en medgivande process som löser inbjudan.  Om de inte slutför medgivande kan de inte komma åt något av Contosos innehåll.  Om de har problem med att lösa in sin inbjudan via den ursprungliga länken, kan en Azure AD-administratör skicka en länk till en särskild inbjudan för att lösa in den igen.

### <a name="planned-per-item-sharing"></a>Planerat per artikel delning

Contoso arbetar med en underleverantör för att utföra Tillförlitlighets analys av radiatorer. Underleverantören har ett team med 10 personer som behöver åtkomst till data i Contosos Power BIs miljö. Contoso Azure AD-administratören är involverad för att bjuda in alla användare och hantera eventuella tillägg/ändringar som personal vid underleverantörs ändringen. Azure AD-administratören skapar en säkerhets grupp för alla anställda på underleverantören. Med hjälp av säkerhets gruppen kan Contosos anställda enkelt hantera åtkomst till rapporter och se till att all nödvändig underleverantörs personal har åtkomst till alla nödvändiga rapporter, instrument paneler och Power BI appar. Azure AD-administratören kan också undvika att delta i Inbjudnings processen helt genom att välja att delegera Inbjudnings rättigheter till en betrodd anställd på Contoso eller via underleverantören för att säkerställa att personalen kan hantera tiden.

Vissa organisationer kräver mer kontroll över när externa användare läggs till, bjuder in många användare i en extern organisation eller flera externa organisationer. I dessa fall kan planerad delning användas för att hantera delnings skalan, för att genomdriva organisations principer och till och med delegera rättigheter till betrodda personer för att bjuda in och hantera externa användare. Azure AD B2B stöder planerade inbjudningar som skickas direkt [från Azure Portal av en IT-administratör](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator)eller via [PowerShell med hjälp av API: et för Inbjudnings hanteraren](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) där en uppsättning användare kan bjudas in i en åtgärd. Med hjälp av den planerade Inbjudnings metoden kan organisationen styra vem som kan bjuda in användare och implementera godkännande processer. Avancerade Azure AD-funktioner som dynamiska grupper kan göra det enkelt att underhålla medlemskap i säkerhets grupper automatiskt.


![Styra vilka gäster som kan se innehåll](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. Processen börjar med en IT-administratör som bjuder in gäst användaren antingen manuellt eller via det API som tillhandahålls av Azure Active Directory
2. Användaren godkänner inbjudan till organisationen.
3. När användaren har accepterat inbjudan kan en användare i Power BI dela en rapport eller instrument panel med den externa användaren eller en säkerhets grupp som de finns i. Precis som med vanlig delning i Power BI får den externa användaren ett e-postmeddelande med en länk till objektet.
4. När den externa användaren har åtkomst till länken skickas deras autentisering i sin katalog till Contosos Azure AD och används för att få till gång till Power BI innehåll.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad hoc eller planerad delning av Power BI appar

Contoso har en uppsättning rapporter och instrument paneler som de behöver för att dela med en eller flera leverantörer. För att se till att alla nödvändiga externa användare har åtkomst till det här innehållet paketeras det som en Power BI app. De externa användarna läggs antingen direkt till i appens åtkomst lista eller via säkerhets grupper. Någon på Contoso skickar sedan appens URL till alla externa användare, till exempel i ett e-postmeddelande. När de externa användarna öppnar länken visas allt innehåll på ett enkelt sätt för att navigera.

Med en Power BI app är det enkelt för Contoso att bygga en BI-Portal för sina leverantörer. En enda åtkomst lista styr åtkomsten till allt nödvändigt innehåll som minskar den tid som krävs för att kontrol lera och ange behörigheter för objekt nivå. Azure AD B2B upprätthåller säkerhets åtkomst med leverantörens interna identitet så att användarna inte behöver ytterligare inloggnings uppgifter. Om du använder planerade inbjudningar med säkerhets grupper kan du använda åtkomst hantering till appen eftersom personalen roterar in eller ut ur projektet är förenklad. Medlemskap i säkerhets grupper manuellt eller med hjälp av [dynamiska grupper](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups)så att alla externa användare från en leverantör automatiskt läggs till i rätt säkerhets grupp.


![Kontrol lera innehåll med AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. Processen startar av användaren som bjuds in till Contosos Azure AD-organisation via Azure Portal eller PowerShell
2. Användaren kan läggas till i en användar grupp i Azure AD. En statisk eller dynamisk användar grupp kan användas, men dynamiska grupper hjälper till att minska manuellt arbete.
3. Externa användare får åtkomst till Power BI-appen via användar gruppen. Appens URL ska skickas direkt till den externa användaren eller placeras på en plats som de har åtkomst till. Power BI är ett bra sätt att skicka ett e-postmeddelande med en app-länk till externa användare, men när du använder användar grupper vars medlemskap kan ändras, kan Power BI inte skicka till alla externa användare som hanteras via användar grupper.
4. När den externa användaren ansluter till Power BI-appens URL autentiseras de av Contosos Azure AD, appen installeras för användaren och användaren kan se alla de rapporter och instrument paneler som finns i appen.

Appar har också en unik funktion som gör det möjligt för appar att installera programmet automatiskt för användaren, så att det är tillgängligt när användaren loggar in. Den här funktionen installeras bara automatiskt för externa användare som redan är en del av Contosos organisation vid den tidpunkt då programmet publiceras eller uppdateras. Det är därför bäst att använda den planerade Inbjudnings metoden och är beroende av att appen publiceras eller uppdateras när användarna har lagts till i Contosos Azure AD. Externa användare kan alltid installera appen med hjälp av app-länken.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Kommentera och prenumerera på innehåll i olika organisationer

När contoso fortsätter att arbeta med sina underleverantörer eller leverantörer måste de externa teknikerna arbeta nära med Contosos analytiker. Power BI innehåller flera samarbets funktioner som hjälper användarna att kommunicera om innehåll de kan använda. Instrument panel kommentarer (och snart rapport kommentarer) låter användarna diskutera data punkter som de ser och kommunicera med rapport författare för att ställa frågor.

Externa gäst användare kan för närvarande delta i kommentarer genom att lämna kommentarer och läsa svaren. Till skillnad från interna användare kan gäst användare dock inte vara @mentioned och inte ta emot meddelanden om att de har tagit emot en kommentar. Gäst användare kan inte använda funktionen prenumerationer inom Power BI vid tidpunkten för skrivning. I en kommande version kommer dessa begränsningar att hävas och gäst användaren får ett e-postmeddelande när de kommenterar @mentions dem, eller när en prenumeration skickas till e-post som innehåller en länk till innehållet i Power BI.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Få åtkomst till innehåll i Power BI Mobile Apps

I en kommande version kommer Power BI att skicka ett e-postmeddelande till gästen när Contosos användare delar rapporter eller instrument paneler med sina externa gäst motsvarigheter. När gäst användaren öppnar länken till rapporten eller instrument panelen på sin mobila enhet öppnas innehållet i den inbyggda Power BI mobila appar på enheten, om de är installerade. Gäst användaren kommer sedan att kunna navigera mellan innehåll som delas med dem i den externa klienten och tillbaka till sitt eget innehåll från sin hem klient.

> [!NOTE]
> Gäst användaren kan inte öppna Power BI mobilapp och navigera omedelbart till den externa klienten, de måste börja med en länk till ett objekt i den externa klienten. Vanliga lösningar beskrivs i avsnittet [distribuera länkar till innehåll i den överordnade organisationens Power BI](#distributing-links-to-content-in-the-parent-organizations-power-bi) avsnitt senare i det här dokumentet.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Redigering och hantering av Power BI innehåll mellan organisationer

Contoso och dess leverantörer och underleverantörer fungerar nära varandra. En analytiker på underleverantören behöver ofta ytterligare mått eller data visualiseringar som ska läggas till i en rapport contoso har delat med dem. Data ska finnas i Contosos Power BI-klient, men externa användare ska kunna redigera den, skapa nytt innehåll och till och med distribuera den till lämpliga individer.

Power BI tillhandahåller ett alternativ som gör det möjligt för **externa gäst användare att redigera och hantera innehåll** i organisationen. Externa användare har som standard en skrivskyddad konsumtions upplevelse. Den här nya inställningen låter dock Power BI-administratören välja vilka externa användare som kan redigera och hantera innehåll i sin egen organisation. När det är tillåtet kan den externa användaren redigera rapporter, instrument paneler, publicera eller uppdatera appar, arbeta i arbets ytor och ansluta till data som de har behörighet att använda.

Det här scenariot beskrivs i detalj i avsnittet som gör det möjligt för externa användare att redigera och hantera innehåll i Power BI senare i det här dokumentet.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Organisations relationer med Power BI och Azure AD B2B

När alla användare av Power BI är interna för organisationen behöver du inte använda Azure AD B2B. Men när två eller flera organisationer vill samar beta med data och insikter, gör Power BI supporten för Azure AD B2B det enkelt och kostnads effektivt att göra det.

Nedan påträffas vanligt vis organisations strukturer som lämpar sig väl för Azure AD B2B-format över organisations samarbete i Power BI. Azure AD B2B fungerar bra i de flesta fall, men i vissa fall är de vanliga alternativa metoder som beskrivs i slutet av det här dokumentet värt att tänka på.

### <a name="case-1-direct-collaboration-between-organizations"></a>Fall 1: direkt samarbete mellan organisationer

Contosos relation med dess radiatorer-leverantör är ett exempel på direkt samarbete mellan organisationer. Eftersom det finns relativt få användare på Contoso och dess leverantör som behöver till gång till Tillförlitlighets information för utstrålande, är det idealiskt att använda Azure AD B2B-baserad extern delning. Det är enkelt att använda och enkelt att administrera. Detta är också ett vanligt mönster i konsult tjänster där en konsult kan behöva bygga upp innehåll för en organisation.

![Dela mellan organisationer](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Normalt sker den här delningen från början med ad hoc-delning per objekt. Men när teamen växer eller relationerna är fördjupa, blir den planerade metoden för delning per objekt den bästa metoden för att minska hanterings kostnaderna. Dessutom kan ad hoc eller planerad delning av Power BI appar, kommentera och prenumerera på innehåll i olika organisationer, komma åt innehåll i mobila appar, samt redigering och hantering av Power BI innehåll i flera organisationer. Om båda organisationers användare har Power BI Pro licenser i sina respektive organisationer kan de använda dessa Pro-licenser i var och en av Power BI miljöer. Detta ger en förmånlig licens eftersom den bjudande organisationen kanske inte behöver betala för en Power BI Pro-licens för de externa användarna. Detta beskrivs i mer detalj i avsnittet om licens senare i det här dokumentet.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Fall 2: överordnad och dess dotter bolag eller dotter bolag

Vissa organisations strukturer är mer komplexa, inklusive delvis eller helt ägda dotter bolag, närstående bolag eller relationer för hanterade tjänst leverantörer. Dessa organisationer har en överordnad organisation, t. ex. ett Holding bolag, men de underliggande organisationerna får en halv självständig verksamhet, ibland enligt olika regionala krav. Detta leder till varje organisation som har sin egen Azure AD-miljö och skilda Power BI klienter.

![Arbeta med dotter bolag](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


I den här strukturen behöver den överordnade organisationen vanligt vis distribuera standardiserade insikter till sina dotter bolag. Normalt sker denna delning med hjälp av ad hoc eller planerad delning av Power BI Apps-metoden som illustreras i följande bild, eftersom den tillåter distribution av standardiserat auktoritativt innehåll till breda mål grupper. I praktiken används en kombination av alla scenarier som nämns ovan i det här dokumentet.

![Kombinera scenarier](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Följande process:

1. Användare från varje dotter bolag bjuds in till Contosos Azure AD
2. Sedan publiceras Power BI-appen så att dessa användare får åtkomst till de data som krävs
3. Användarna öppnar slutligen appen via en länk som de har fått för att se rapporterna

Flera viktiga utmaningar riktas av organisationer i den här strukturen:

- Hur du distribuerar länkar till innehåll i den överordnade organisationens Power BI
- Så här tillåter du att dotter bolags användare får åtkomst till data källor som finns i den överordnade organisationen

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribuera länkar till innehåll i den överordnade organisationens Power BI

Tre metoder används ofta för att distribuera länkar till innehållet. Den första och mest grundläggande är att skicka länken till appen till de användare som krävs eller att placera den på en SharePoint Online-webbplats från vilken den kan öppnas. Användarna kan sedan bok märkena länken i sina webbläsare för snabbare åtkomst till de data som de behöver.

Den andra metoden förlitar sig på redigering och hantering av Power BI innehåll i olika organisationer. Den överordnade organisationen gör det möjligt för användare från dotter bolagen att komma åt sin Power BI och styr vad de kan komma åt via behörighet. Detta ger till gång till Power BI start där användaren från dotter bolaget ser en omfattande lista över innehåll som delas till dem i den överordnade organisationens klient organisation. URL: en till de överordnade organisationernas Power BI-miljö ges till användarna i dotter bolagen.

I den sista metoden används en Power BI-app som skapats i Power BI-klienten för varje dotter bolag. Power BI-appen innehåller en instrument panel med [paneler som kon figurer ATS med alternativet extern länk](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink). När användaren trycker på panelen, tas de till lämplig rapport, instrument panel eller app i den överordnade organisationens Power BI. Den här metoden har extra fördelen att appen kan installeras automatiskt för alla användare i dotter företaget och är tillgänglig för dem när de loggar in i sin egen Power BI-miljö. En extra fördel med den här metoden är att den fungerar bra med Power BI mobila appar som kan öppna länken internt. Du kan också kombinera detta med den andra metoden för att göra det enklare att växla mellan Power BI miljöer.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Tillåta att dotter bolags användare får åtkomst till data källor som finns i den överordnade organisationen

Analytiker måste ofta skapa egna analyser med hjälp av data från den överordnade organisationen. I det här fallet används ofta moln data källor för att åtgärda utmaningen.

Den första metoden använder [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) för att bygga ett informations lager i företags klass som hanterar behovet av analytiker över det överordnade och dess dotter bolag som visas i följande bild. Contoso kan vara värd för data och använda funktioner som säkerhet på radnivå för att säkerställa att användare i varje dotter bolag har åtkomst till sina data. Analytiker i varje organisation kan komma åt informations lagret genom Power BI Desktop och publicera resulterande analyser till sina respektive Power BI-klienter.

![Så här sker delning med Power BI klienter](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


Den andra metoden utnyttjar [Azure SQL Database](https://azure.microsoft.com/services/sql-database/) för att skapa ett Relations informations lager för att ge åtkomst till data. Detta fungerar på samma sätt som Azure Analysis Services metoden, men vissa funktioner som säkerhet på radnivå kan vara svårare att distribuera och underhålla mellan dotter bolag.

Mer avancerade metoder är också möjligt, men ovanstående är de vanligaste.

### <a name="case-3-shared-environment-across-partners"></a>Fall 3: delad miljö mellan partner

Contoso kan ingå i ett partnerskap med en konkurrent för att gemensamt bygga en bil på en delad sammansättnings linje, men för att distribuera fordonet under olika varumärken eller i olika regioner. Detta kräver omfattande samarbete och samägare av data, intelligens och analys mellan organisationer. Den här strukturen är också vanlig i konsult Services-branschen där ett team med konsulter kan utföra projektbaserade analyser för en klient.

![Delad miljö mellan partner](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



I praktiken är dessa strukturer komplexa som du ser i följande bild och kräver att personalen underhåller. För att vara effektiv är den här strukturen förlitad på redigering och hantering av Power BI innehåll i flera organisationer eftersom det gör det möjligt för organisationer att återanvända Power BI Pro licenser som köpts för sina respektive Power BI-klienter.

![Licenser och delat organisations innehåll](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



För att upprätta en delad Power BI-klient måste en Azure Active Directory skapas och minst ett Power BI Pro användar konto måste köpas för en användare i Active Directory. Den här användaren bjuder in de användare som krävs till den delade organisationen. I det här scenariot behandlas Contosos användare som externa användare när de arbetar i den delade organisationens Power BI.

Processen ser ut så här:

1. Den delade organisationen upprättas som en ny Azure Active Directory och minst ett användar konto skapas i den nya organisationen. Användaren ska ha en tilldelad Power BI Pro-licens.
2. Den här användaren upprättar sedan en Power BI klient och bjuder in de användare som krävs från Contoso och partner organisationen. Användaren upprättar också delade data till gångar som Azure Analysis Services. Contoso och partner användare kan komma åt den delade organisationens Power BI som gäst användare. Om det är tillåtet att redigera och hantera innehåll i Power BI externa användare kan använda Power BI Home, använda arbets ytor, ladda upp eller redigera innehåll och dela rapporter. Normalt lagras och nås alla delade till gångar från den delade organisationen.
3. Beroende på hur parterna är överens om att samar beta, är det möjligt för varje organisation att utveckla sina egna patentskyddade data och analyser med hjälp av delade data lager till gångar. De kan distribuera dem till deras respektive interna användare med hjälp av interna Power BI-klienter.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Fall 4: distribution till hundratals eller tusentals externa partner

Medan contoso skapade en Tillförlitlighets rapport för utstrålare för en leverantör, vill nu contoso skapa en uppsättning standardiserade rapporter för hundratals leverantörer. Detta gör det möjligt för Contoso att se till att alla leverantörer har den analys de behöver för att göra förbättringar eller åtgärda produktions fel.

![Distribution till många partner](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


När en organisation behöver distribuera standardiserade data och insikter till många externa användare/organisationer, kan de använda ad hoc eller planerad delning av Power BI Apps-scenariot för att snabbt bygga en BI-Portal och utan omfattande utvecklings kostnader. Processen för att skapa en sådan Portal med hjälp av en Power BI-app beskrivs i fallstudien: skapa en BI-Portal med Power BI + Azure AD B2B – stegvisa instruktioner längre fram i det här dokumentet.

En vanlig variant av det här fallet är när en organisation försöker dela insikter med konsumenter, särskilt när du vill använda Azure-B2C med Power BI. Power BI har inte inbyggt stöd för Azure-B2C. Om du utvärderar alternativ för det här fallet bör du överväga att använda alternativt alternativ 2 i det vanliga alternativa avsnittet i det här dokumentet.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Fallstudie: skapa en BI-Portal med Power BI + Azure AD B2B – steg-för-steg-instruktioner

Power BI s integrering med Azure AD B2B ger contoso ett smidigt och smidigt sätt att ge gäst användare säker åtkomst till sin BI-Portal. Contoso kan konfigureras med tre steg:

![Skapa en portal](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Skapa BI-portal i Power BI

    Den första aktiviteten för contoso är att skapa sin BI-portal i Power BI. Contosos BI Portal består av en samling syften-utformade instrument paneler och rapporter som kommer att göras tillgängliga för många interna och gäst användare. Det rekommenderade sättet att göra detta i Power BI är att bygga en Power BI-app. Läs mer om [appar i Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- Contosos BI-team skapar en arbets yta i Power BI

    ![arbetsyta](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Andra författare läggs till i arbets ytan

    ![Lägg till författare](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- Innehåll skapas i arbets ytan

    ![Skapa innehåll i arbets ytan](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Nu när innehållet har skapats i en arbets yta är contoso redo att bjuda in gäst användare i partner organisationer att använda det här innehållet.

2. Bjud in gästanvändare

    Det finns två sätt för Contoso att bjuda in gäst användare till sin BI-portal i Power BI:

    * Planerade inbjudningar
    * Ad hoc-inbjudningar

    **Planerade inbjudningar**

    I den här metoden bjuder contoso in gäst användarna till sin Azure AD i förväg och distribuerar sedan Power BI innehåll till dem. Contoso kan bjuda in gäst användare från Azure Portal eller med hjälp av PowerShell. Här följer stegen för att bjuda in gäst användare från Azure Portal:

    - Contosos Azure AD-administratör navigerar till **Azure Portal > Azure Active Directory > användare och grupper > alla användare > ny gäst användare**

    ![Gäst användare](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Lägg till ett Inbjudnings meddelande för gäst användarna och klicka på Bjud in

    ![Lägg till inbjudan](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Om du vill bjuda in gäst användare från Azure Portal måste du ha administratörs behörighet för Azure Active Directory av din klient.

    Om Contoso vill bjuda in många gäst användare kan de göra det med hjälp av PowerShell. Contosos Azure AD-administratör lagrar e-postadresserna till alla gäst användare i en CSV-fil. Här är [Azure Active Directory B2B-samarbets kod och PowerShell-exempel](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) och-instruktioner.

    Efter inbjudan får gäst användare ett e-postmeddelande med länken inbjudan.

    ![Länk till inbjudan](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    När gäst användarna klickar på länken kan de komma åt innehåll i Contoso Azure AD-klienten.

    > [!NOTE]
    > Du kan ändra layouten för inbjudan via e-post med hjälp av funktionen för anpassning av Azure AD enligt beskrivningen [här](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email).


    **Ad hoc-inbjudningar**

    Vad händer om contoso inte vet att alla gäst användare vill bjuda in i förväg? Eller vad händer om analytikern i Contoso som skapade BI-portalen vill distribuera innehåll till gäst användare? Vi har också stöd för det här scenariot i Power BI med ad hoc-inbjudningar.

    Analytikern kan bara lägga till externa användare i åtkomst listan för appen när de publicerar den. Gäst användarna får en inbjudan och när de accepterar det omdirigeras de automatiskt till Power BI innehållet.

    ![Lägg till extern användare](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Inbjudningar behövs bara första gången som en extern användare bjuds in till din organisation.


3. Distribuera innehåll

    Nu när Contosos BI-team har skapat BI-portalen och bjudit in gäst användare kan de distribuera sin portal till sina slutanvändare genom att ge gäst användare åtkomst till appen och publicera den. Power BI automatiskt Slutför namn på gäst användare som tidigare har lagts till contoso-klienten. Ad hoc-inbjudningar till andra gäst användare kan också läggas till nu.

    > [!NOTE]
    > Om du använder säkerhets grupper för att hantera åtkomst till appen för externa användare kan du använda den planerade Inbjudnings metoden och dela appens länk direkt med varje extern användare som måste ha åtkomst till den. Annars kanske den externa användaren inte kan installera eller Visa innehåll i appen. _

    Gäst användare får ett e-postmeddelande med en länk till appen.

    ![Länk till e-postinbjudan](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    När du klickar på den här länken uppmanas gäst användare att autentisera med sin egen organisations identitet.

    ![Inloggningssida](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    När de har autentiserats omdirigeras de till Contosos BI-app.

    ![Se delat innehåll](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Gäst användare kan sedan komma till Contosos app genom att klicka på länken i e-postmeddelandet eller lägga till ett bok märke på länken. Contoso kan också göra det enklare för gäst användare genom att lägga till den här länken till alla befintliga extra nät portaler som gäst användarna redan använder.

4. Nästa steg

    Med hjälp av en Power BI app och Azure AD B2B kunde contoso snabbt skapa en BI-Portal för sina leverantörer på ett sätt som inte är kod. Detta är avsevärt förenklat och distribuerar standardiserad analys till alla leverantörer som behövde det.

    Exemplet visade hur en gemensam rapport kan distribueras mellan leverantörer, Power BI kan gå mycket mer. För att säkerställa att varje partner bara ser data som är relevanta för sig själva kan säkerhet på radnivå enkelt läggas till i rapporten och data modellen. Avsnittet data säkerhet för externa partners längre fram i det här dokumentet beskriver den här processen i detalj.

    Ofta måste enskilda rapporter och instrument paneler bäddas in i en befintlig Portal. Detta kan också åstadkommas med hjälp av många av de metoder som visas i exemplet. I dessa fall kan det dock vara lättare att bädda in rapporter eller instrument paneler direkt från en arbets yta. Processen för att bjuda in och tilldela säkerhets behörighet till Kräv att användarna är oförändrade.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Under huven: Hur kan Lucy från Supplier1 få åtkomst till Power BI innehåll från Contosos klient organisation?

Nu när vi har sett hur contoso kan distribuera Power BI innehåll till gäst användare i partner organisationer, ska vi titta på hur det fungerar under huven.

När contoso har bjudits in [lucy@supplier1.com](mailto:lucy@supplier1.com) till sin katalog skapar Azure AD en länk mellan [Lucy@supplier1.com](mailto:Lucy@supplier1.com) och contoso Azure AD-klienten. Den här länken låter Azure AD veta att Lucy@supplier1.com kan komma åt innehåll i Contoso-klienten.

När Lucy försöker komma åt Contosos Power BI app, verifierar Azure AD att Lucy har åtkomst till contoso-klienten och ger sedan Power BI en token som anger att Lucy autentiseras för att komma åt innehåll i Contoso-klienten. Power BI använder denna token för att auktorisera och se till att Lucy har åtkomst till Contosos Power BI-app.

![Verifiering och auktorisering](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Power BI s integrering med Azure AD B2B fungerar med alla e-postadresser för företag. Om användaren inte har en Azure AD-identitet kan de uppmanas att skapa en. Följande bild visar det detaljerade flödet:

![Diagram över integrations flöde](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


Det är viktigt att känna till att Azure AD-kontot kommer att användas eller skapas i den externa partens Azure AD, vilket gör det möjligt för Lucy att använda sina egna användar namn och lösen ord, och deras autentiseringsuppgifter kommer automatiskt att sluta fungera i andra klienter när Lucy lämnar företaget när deras organisation också använder Azure AD.

## <a name="licensing"></a>Licensiering

Contoso kan välja en av tre metoder för att licensiera gäst användare från sina leverantörer och partner organisationer för att få åtkomst till Power BI innehåll.

> [!NOTE]
> _Den kostnads fria nivån av Azure AD B2B's räcker för att använda Power BI med Azure AD B2B. Vissa avancerade Azure AD B2B-funktioner som dynamiska grupper kräver ytterligare licensiering. Mer information finns i dokumentationen för Azure AD B2B._[_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Metod 1: Contoso använder Power BI Premium

Med den här metoden har contoso inköp Power BI Premium kapacitet och tilldelar innehållet i BI-portalen till denna kapacitet. Detta gör det möjligt för gäst användare från partner organisationer att komma åt Contosos Power BI app utan Power BI licens.

Externa användare omfattas även av användnings upplevelser som erbjuds till "kostnads fria" användare i Power BI när innehåll förbrukas i Power BI Premium.

Contoso kan också dra nytta av andra Power BI Premium-funktioner för sina appar som ökade uppdaterings hastigheter, dedikerad kapacitet och stor modell storlek.

![Ytterligare funktioner](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Metod 2: contoso tilldelar gäst användare Power BI Pro licenser

Med den här metoden tilldelar contoso Pro-licenser till gäst användare från partner organisationer – detta kan göras från Contosos Microsoft 365 administrations Center. Detta gör det möjligt för gäst användare från partner organisationer att komma åt Contosos Power BI app utan att köpa en licens själva. Detta kan vara lämpligt för delning med externa användare vars organisation inte har antagit Power BI ännu.

> [!NOTE]
> Contosos Pro-licens gäller enbart gäst användare när de får åtkomst till innehåll i Contoso-klienten. Pro-licenser ger åtkomst till innehåll som inte har Power BI Premium kapacitet. Externa användare med en Pro-licens begränsas dock som standard till endast en användning. Detta kan ändras med hjälp av den metod som beskrivs i avsnittet _aktivera externa användare för att redigera och hantera innehåll i Power BI_ längre fram i det här dokumentet.

![Licens information](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Metod 3: gäst användare får sin egen Power BI Pro-licens

Med den här metoden tilldelar leverantör 1 en Power BI Pro-licens till Lucy. De kan sedan komma åt Contosos Power BI-app med denna licens. Eftersom Lucy kan använda sin Pro-licens från sin egen organisation vid åtkomst till en extern Power BI-miljö, kallas den här metoden ibland för att _ta med din egen licens_ (BYOL). Om båda organisationerna använder Power BI ger detta en förmånlig licens för den övergripande analys lösningen och minimerar behovet av att tilldela licenser till externa användare.

> [!NOTE]
> Den Pro-licens som gavs till Lucy av leverantör 1 gäller för alla Power BI-klienter där Lucy är en gäst användare. Pro-licenser ger åtkomst till innehåll som inte har Power BI Premium kapacitet. Externa användare med en Pro-licens begränsas dock som standard till endast en användning. Detta kan ändras med hjälp av den metod som beskrivs i avsnittet _aktivera externa användare för att redigera och hantera innehåll i Power BI_ längre fram i det här dokumentet.

![Krav för Pro-licens](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Data säkerhet för externa partners

Som vanligt när du arbetar med flera externa leverantörer måste contoso se till att varje leverantör bara ser data om sina egna produkter. Med hjälp av användarbaserad säkerhet och dynamisk säkerhet på radnivå kan du göra det enkelt att uppnå Power BI.

### <a name="user-based-security"></a>Användarbaserad säkerhet

En av de mest kraftfulla funktionerna i Power BI är säkerhet på radnivå. Med den här funktionen kan Contoso skapa en enda rapport och data uppsättning men ändå använda olika säkerhets regler för varje användare. En djupgående förklaring finns i [säkerhet på radnivå (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

Power BI s integrering med Azure AD B2B gör det möjligt för Contoso att tilldela säkerhets regler på radnivå till gäst användare så fort de bjuds in till contoso-klienten. Som vi har sett tidigare kan Contoso lägga till gäst användare via antingen planerade eller ad hoc-inbjudningar. Om Contoso vill framtvinga säkerhet på radnivå, rekommenderar vi starkt att du använder planerade inbjudningar för att lägga till gäst användarna i förväg och tilldela dem till säkerhets rollerna innan innehållet delas. Om contoso i stället använder ad hoc-inbjudningar kan det finnas en kort tids period då gäst användarna inte kommer att kunna se några data.

> [!NOTE]
> Den här fördröjningen vid åtkomst till data som skyddas av RLS när du använder ad hoc-inbjudningar kan leda till stöd för förfrågningar till ditt IT-team eftersom användare ser antingen tomma eller trasiga rapporter/instrument paneler när de öppnar en delnings länk i det e-postmeddelande som de får. Därför rekommenderar vi starkt att du använder planerade inbjudningar i det här scenariot. * *

Låt oss gå igenom detta med ett exempel.

Som tidigare nämnts har contoso leverantörer över hela världen och de vill se till att användarna från deras leverantörs organisationer får insikter från data från enbart deras territorium.  Men användare från contoso kan komma åt alla data. I stället för att skapa flera olika rapporter skapar Contoso en enda rapport och filtrerar data baserat på den användare som visar den.

![Delat innehåll](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

För att se till att contoso kan filtrera data baserat på vem som ansluter, skapas två roller i Power BI Station ära datorer. En för att filtrera alla data från SalesTerritory "Europa" och en annan för "Nordamerika".

![Hantera roller](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

När roller definieras i rapporten måste en användare tilldelas en viss roll för att få åtkomst till data. Tilldelningen av roller sker i Power BI-tjänst ( **data uppsättningar > säkerhet** )

![Ställer in säkerhet](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Då öppnas en sida där Contosos BI-team kan se de två roller som de skapade.  Nu kan Contosos BI-team tilldela användare till rollerna.

![Säkerhet på radnivå](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

I det här exemplet contoso lägger du till en användare i en partner organisation med e-postadress [adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com) till Europa-rollen:

![Säkerhets inställningar på radnivå](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

När detta löses av Azure AD kan Contoso se namnet som visas i fönstret som är klart att läggas till:

![Visa roller](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Nu när den här användaren öppnar appen som delades med dem ser de bara en rapport med data från Europa:

![Visa innehåll](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Dynamisk säkerhet på radnivå

Ett annat intressant ämne är att se hur dynamisk säkerhet på radnivå (RLS) fungerar med Azure AD B2B.

I korthet fungerar dynamisk säkerhet på radnivå genom att filtrera data i modellen baserat på användar namnet för den person som ansluter till Power BI. I stället för att lägga till flera roller för grupper av användare definierar du användarna i modellen. Vi beskriver inte mönstret i detalj här. Kasper de Jong erbjuder en detaljerad uppskrivning av all varianter på säkerhet på radnivå i [Power BI Desktop Dynamic Security lathund-bladet](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)och i [det här dokumentet](https://download.microsoft.com/download/D/2/0/D20E1C5F-72EA-4505-9F26-FEF9550EFD44/Securing%20the%20Tabular%20BI%20Semantic%20Model.docx) .

Nu ska vi titta på ett litet exempel – contoso har en enkel rapport om försäljning per grupp:

![Exempel på innehåll](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Nu måste den här rapporten delas med två gäst användare och en intern användare – den interna användaren kan se allt, men gäst användarna kan bara se de grupper som de har åtkomst till. Det innebär att vi bara måste filtrera data för gäst användarna. För att filtrera data på rätt sätt använder contoso det dynamiska RLS-mönstret enligt beskrivningen i fakta bladet och blogg inlägget. Det innebär att contoso lägger till användar namnen till själva data:

![Visa RLS-användare till själva data](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Sedan skapar Contoso rätt data modell som filtrerar data korrekt med rätt relationer:

![Lämpliga data visas](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Om du vill filtrera data automatiskt baserat på vem som är inloggad måste contoso skapa en roll som passerar i den användare som ansluter. I det här fallet skapar Contoso två roller – det första är "securityrole" som filtrerar tabellen användare med det aktuella användar namnet för den användare som är inloggad till Power BI (detta fungerar även för Azure AD B2B gäst användare).

![Hantera roller](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

Contoso skapar även en annan "AllRole" för sina interna användare som kan se allt – den här rollen har inga säkerhetspredikat.

När du har överfört Power BI Desktop-filen till tjänsten kan Contoso tilldela gäst användare till "SecurityRole" och interna användare till "AllRole"

När gäst användarna öppnar rapporten ser de nu bara försäljning från grupp A:

![Endast från grupp A](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

I matrisen till höger kan du se resultatet av funktionen USERNAME () och USERPRINCIPALNAME () för att båda returnera e-postadressen för gäst användare.

Nu visas alla data i den interna användaren:

![Alla data som visas](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Som du kan se fungerar dynamiska RLS med både interna eller gäst användare.

> [!NOTE]
> Det här scenariot fungerar även när du använder en modell i Azure Analysis Services. Vanligt vis är din Azure Analysis-tjänst ansluten till samma Azure AD som Power BI – i så fall kan Azure Analysis Services även veta vilka gäst användare som bjudits in via Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>Ansluta till lokala data källor

Power BI erbjuder möjligheten för Contoso att utnyttja lokala data källor som [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) eller [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) direkt till den [lokala datagatewayen](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). Det är också möjligt att logga in på dessa data källor med samma autentiseringsuppgifter som används med Power BI.

> [!NOTE]
> När du installerar en gateway för att ansluta till din Power BI-klient måste du använda en användare som skapats i din klient organisation. Externa användare kan inte installera en gateway och ansluta den till klienten. _

För externa användare kan detta vara mer komplicerat eftersom externa användare vanligt vis inte är kända för den lokala AD-platsen. Power BI erbjuder en lösning för detta genom att låta contoso-administratörer mappa externa användar namn till interna användar namn enligt beskrivningen i [Hantera din data källa – Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Till exempel [lucy@supplier1.com](mailto:lucy@supplier1.com) kan mappas till [Lucy \_ supplier1 \_ com # EXT@contoso.com ](mailto:lucy_supplier1_com).

![Mappa användar namn](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Den här metoden är bra om contoso bara har en fåtal eller om contoso kan mappa alla externa användare till ett enskilt internt konto. För mer komplexa scenarier där varje användare behöver sina egna autentiseringsuppgifter, finns det en mer avancerad metod som använder [anpassade AD-attribut](https://technet.microsoft.com/library/cc961737.aspx) för att utföra mappningen enligt beskrivningen i [Hantera din data källa – Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Detta gör att contoso-administratören kan definiera en mappning för varje användare i din Azure AD (även externa B2B-användare).  Dessa attribut kan anges via AD-objektmodellen med hjälp av skript eller kod så att contoso kan automatisera mappningen på inbjudan eller en schemalagd takt.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Aktivera externa användare för att redigera och hantera innehåll i Power BI

Contoso kan göra det möjligt för externa användare att bidra med innehåll i organisationen som beskrivs tidigare i avsnittet redigering och hantering av Power BI innehåll i kors organisationen.

> [!NOTE]
> Användaren måste ha en Power BI Pro-licens på en annan arbets yta än min arbets yta för att kunna redigera och hantera innehåll i din organisations Power BI. Användare kan få Pro-licenser som beskrivs i avsnittet _Licensing_ i det här dokumentet.

På Power BI admin-portalen kan **externa gäst användare redigera och hantera innehåll i organisations** inställningen i klient organisations inställningarna. Som standard är inställningen inställd på inaktive rad, vilket innebär att externa användare får en begränsad skrivskyddad upplevelse som standard. Inställningen gäller för användare med UserType inställd på gäst i Azure AD. I tabellen nedan beskrivs de beteenden som användarna upplever beroende på deras UserType och hur inställningarna konfigureras.

| **Användar typ i Azure AD** | **Tillåt att externa gäst användare redigerar och hanterar innehålls inställningar** | **Beteende** |
| --- | --- | --- |
| Gäst | Inaktiverat för användaren (standard) | Per objekt-endast konsumtions visning. Tillåter skrivskyddad åtkomst till rapporter, instrument paneler och appar när de visas via en URL som skickas till gäst användaren. Power BI Mobile appar ger gäst användaren en skrivskyddad vy. |
| Gäst | Aktive rad för användaren | Den externa användaren får till gång till den fullständiga Power BIs miljön, men vissa funktioner är inte tillgängliga för dem. Den externa användaren måste logga in på Power BI med hjälp av Power BI tjänst-URL: en med den klient information som ingår. Användaren får en hem miljö, en min arbets yta och baserat på behörigheter kan läsa, Visa och skapa innehåll. </br></br> Power BI Mobile appar ger gäst användaren en skrivskyddad vy. |

> [!NOTE]
> Externa användare i Azure AD kan också ställas in på UserType member. Detta stöds för närvarande inte i Power BI.

I Power BI admin-portalen visas inställningen i följande bild.

![Administratörsinställningar](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Gäst användare får den skrivskyddade standard upplevelsen och kan redigera och hantera innehåll. Standardvärdet är inaktiverat, vilket innebär att alla gäst användare har den skrivskyddade upplevelsen. Power BI-administratören kan antingen aktivera inställningen för alla gäst användare i organisationen eller för särskilda säkerhets grupper som definierats i Azure AD. I följande bild skapade contoso Power BI-administratören en säkerhets grupp i Azure AD för att hantera vilka externa användare som kan redigera och hantera innehåll i Contoso-klienten.

Om du vill hjälpa de här användarna att logga in på Power BI, anger du dem med klient-URL: en. Följ dessa steg för att hitta klientorganisations-URL:en.

1. I den Power BI-tjänst på den översta menyn väljer du hjälp ( **?** ) och sedan på **Power BI**.
2. Sök efter värdet bredvid klient- **URL**. Detta är klient-URL: en som du kan dela med gäst användare.

    ![Klientorganisations-URL](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

När du använder alternativet Tillåt externa gäst användare för att redigera och hantera innehåll i organisationen får de angivna gäst användarna åtkomst till din organisations Power BI och ser vilket innehåll de har behörighet till. De kan komma åt start, bläddra och bidra med innehåll till arbets ytor, installera appar där de finns i åtkomst listan och ha en min arbets yta. De kan skapa eller vara administratör för arbetsytor som använder den nya användningen av arbetsytan.

> [!NOTE]
> När du använder det här alternativet ser du till att granska styrnings avsnittet i det här dokumentet eftersom standardinställningarna för Azure AD hindrar gäst användare från att använda vissa funktioner som personers besökare, vilket kan leda till minskad upplevelse. * *

För gäst användare som är aktiverade via alternativet Tillåt att externa gäst användare redigerar och hanterar innehåll i organisationens klient inställning är vissa upplevelser inte tillgängliga för dem. Om du vill uppdatera eller publicera rapporter måste gäst användarna använda Power BI-tjänst webb gränssnitt, inklusive hämta data för att ladda upp Power BI Desktop filer. Följande användningar stöds inte:

- Direktpublicering från Power BI Desktop till Power BI-tjänsten
- Gästanvändare kan inte använda Power BI Desktop för att ansluta till tjänstdatauppsättningar i Power BI-tjänsten
- Klassiska arbets ytor är knutna till Microsoft 365 grupper: gäst användare kan inte skapa eller vara administratörer för dessa arbets ytor. De kan vara medlemmar.
- Det går inte att skicka ad hoc-inbjudan för arbetsyteåtkomstlistor
- Power BI Publisher för Excel stöds inte för gästanvändare
- Gästanvändare kan inte installera en Power BI Gateway och ansluta den till din organisation
- Gästanvändare kan inte installera appar och publicera i hela organisationen
- Gästanvändare kan inte använda, skapa, uppdatera eller installera innehållspaket för organisationen
- Gästanvändare kan inte använda Analysera i Excel
- Gäst användare kan inte vara @mentioned med i kommentarer (den här funktionen kommer att läggas till i en kommande version)
- Gäst användare kan inte använda prenumerationer (den här funktionen kommer att läggas till i en kommande version)
- Gästanvändare som använder den här funktionen ska ha ett arbets- eller skolkonto. Gäst användare som använder personliga konton upplever fler begränsningar på grund av inloggnings begränsningar.



## <a name="governance"></a>Styrning

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Ytterligare Azure AD-inställningar som påverkar upplevelser i Power BI relaterade till Azure AD B2B

När du använder Azure AD B2B-delning, styr Azure Active Directory-administratören aspekter av den externa användarens upplevelse. Dessa styrs på sidan Inställningar för extern samarbets volym i Azure Active Directory inställningarna för din klient.

Information om inställningarna finns här:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Som standard är alternativet för gäst användare begränsad, är inställt på Ja, så gäst användare inom Power BI har begränsade upplevelser särskilt surround-delning där person väljare UIs inte arbetar för dessa användare. Det är viktigt att du arbetar med din Azure AD-administratör för att ställa in den på Nej, vilket visas nedan för att säkerställa en bra upplevelse. * *

![Inställningar för externt samarbete](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Kontrol lera gäst inbjudningar

Power BI administratörer kan styra extern delning bara för Power BI genom att gå till Power BI-administratörs portalen. Men klient organisations administratörer kan också styra extern delning med olika Azure AD-principer.  Med dessa principer kan klient administratörer

- Inaktivera inbjudningar för slutanvändare
- Endast administratörer och användare i rollen gäst deltagare kan bjuda in
- Administratörer, rollen gäst deltagare och medlemmar kan bjuda in
- Alla användare, inklusive gäster, kan bjuda in

Du kan läsa mer om de här principerna i [delegera inbjudningar för Azure Active Directory B2B-samarbete](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Alla Power BI åtgärder av externa användare [granskas också i vår gransknings Portal](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).

### <a name="conditional-access-policies-for-guest-users"></a>Principer för villkorlig åtkomst för gäst användare

Contoso kan genomdriva principer för villkorlig åtkomst för gäst användare som har åtkomst till innehåll från contoso-klienten. Detaljerade instruktioner finns i [villkorlig åtkomst för B2B-samarbets användare](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Vanliga alternativa metoder

Azure AD B2B gör det enkelt att dela data och rapporter mellan organisationer, men det finns flera andra metoder som ofta används och som kan vara överlägsna i vissa fall.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Alternativt alternativ 1: skapa dubbla identiteter för partner användare

Med det här alternativet måste contoso manuellt skapa dubbla identiteter för varje partner användare i Contoso-klienten, som du ser i följande bild. I Power BI kan Contoso dela till de tilldelade identiteterna för lämpliga rapporter, instrument paneler eller appar.

![Ange lämpliga mappningar och namn](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Anledningar till att välja det här alternativet:

- Eftersom användarens identitet styrs av din organisation, är alla relaterade tjänster, till exempel e-post, SharePoint osv., även inom ramen för din organisations kontroll. IT-administratörer kan återställa lösen ord, inaktivera åtkomst till konton eller gransknings aktiviteter i dessa tjänster.
- Användare som använder personliga konton för sitt företag är ofta begränsade till att ha åtkomst till vissa tjänster så kan behöva ett organisations konto.
- Vissa tjänster fungerar bara för din organisations användare. Det kan till exempel vara omöjligt att använda Intune för att hantera innehåll på personliga/mobila enheter för externa användare som använder Azure B2B.

Orsaker till att du inte väljer det här alternativet:

- Användare från partner organisationer måste komma ihåg två uppsättningar autentiseringsuppgifter – en för att komma åt innehåll från sin egen organisation och den andra för att komma åt innehåll från contoso. Detta är ett krångel för dessa gäst användare och många gäst användare förväxlas av den här upplevelsen.
- Contoso måste köpa och tilldela licenser per användare till dessa användare. Om en användare behöver ta emot e-post eller använda Office-program behöver de lämpliga licenser, inklusive Power BI Pro för att redigera och dela innehåll i Power BI.
- Contoso kan vilja upprätthålla mer strikta principer för auktorisering och styrning för externa användare jämfört med interna användare. För att uppnå detta måste contoso skapa en intern terminologi för externa användare och alla contoso-användare måste vara sammanutbildade om denna nomenklatur.
- När användaren lämnar sin organisation fortsätter de att ha åtkomst till Contosos resurser tills contoso-administratören manuellt tar bort sitt konto
- Contoso-administratörer måste hantera identiteten för gästen, inklusive skapande, återställning av lösen ord osv.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Alternativt alternativ 2: skapa ett anpassat Power BI Embedded program med anpassad autentisering

Ett annat alternativ för contoso är att bygga ett eget anpassat inbäddat Power BI program med anpassad autentisering ([appen äger data](https://docs.microsoft.com/power-bi/developer/embedded/embed-sample-for-customers)). Även om många organisationer inte har tid eller resurser för att skapa ett anpassat program för att distribuera Power BI innehåll till sina externa partners, är det av vissa organisationer det bästa sättet att använda och förtjänar allvarliga överväganden.

Organisationer har ofta befintliga partner portaler som centraliserar åtkomsten till alla organisations resurser för partner, ger isolering från interna organisations resurser och ger effektiva erfarenheter för partner som stöder många partner och deras enskilda användare.

![Många partner portaler](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

I exemplet ovan kan användare från varje leverantör logga in på Contosos Partner Portal som använder AAD som identitets leverantör. Det kan använda AAD B2B, Azure B2C, interna identiteter eller federera med valfritt antal andra identitets leverantörer. Användaren loggar in och får åtkomst till en partner portal som bygger på Azure-webbappen eller en liknande infrastruktur.

I webbappen är Power BI rapporter inbäddade från en Power BI Embedded-distribution. Webbappen effektiviserar åtkomsten till rapporterna och relaterade tjänster i en sammanhängande miljö som syftar till att göra det enkelt för leverantörer att interagera med contoso. Den här Portal miljön skulle isoleras från Contosos interna AAD och Contosos interna Power BI miljö för att säkerställa att leverantörer inte har åtkomst till dessa resurser. Normalt lagras data i ett separat partner informations lager för att säkerställa data isolering. Den här isoleringen har fördelar eftersom den begränsar antalet externa användare med direkt åtkomst till din organisations data, vilket begränsar vilka data som kan vara tillgängliga för den externa användaren och begränsar oavsiktlig delning med externa användare.

Med hjälp av Power BI Embedded kan portalen dra nytta av en förmånlig licensiering, med hjälp av app-token eller Master-användare plus Premium kapacitet som har köpts i Azure-modellen, vilket fören klar problem med att tilldela licenser till slutanvändare och skala upp/ned baserat på förväntad användning. Portalen kan erbjuda en övergripande högre kvalitet och konsekvent upplevelse eftersom partners får åtkomst till en enda portal som är utformad med alla partner behov i åtanke. Slutligen, eftersom Power BI Embeddedbaserade lösningar vanligt vis är utformade för att vara flera klienter, gör det enklare att isolera mellan partner organisationer.

Anledningar till att välja det här alternativet:

- Enklare att hantera när antalet partner organisationer växer. Eftersom partners läggs till i en separat katalog som är isolerad från Contosos interna AAD-katalog fören klar IT-styrningen och hjälper till att förhindra oavsiktlig delning av interna data till externa användare.
- Vanliga partner portaler är mycket märkta upplevelser med konsekventa upplevelser i partners och effektiviseras för att möta behoven hos vanliga partner. Contoso kan därför erbjuda en bättre övergripande upplevelse till partner genom att integrera alla nödvändiga tjänster på en enda portal.
- Licensierings kostnader för avancerade scenarier som att redigera innehåll i Power BI Embedded omfattas av den köpta Azure-Power BI Premium och kräver inte att Power BI Pro licenser tilldelas till dessa användare.
- Ger bättre isolering över partners om de är konstruerade som en lösning för flera innehavare.
- Partner portalen innehåller ofta andra verktyg för partner utanför Power BI rapporter, instrument paneler och appar.

Orsaker till att du inte väljer det här alternativet:

- Det krävs stor ansträngning för att bygga, hantera och underhålla en sådan portal som gör det till en betydande investering i resurser och tid.
- Tid till lösning är mycket längre än att använda B2B-delning eftersom det krävs noggrann planering och körning över flera workstreams.
- Om det finns ett mindre antal partner är det mycket arbete som krävs för det här alternativet sannolikt för högt att motivera.
- Samarbete med ad hoc-delning är det främsta scenariot som din organisation har.
- Rapporter och instrument paneler är olika för varje partner. Det här alternativet introducerar hanterings kostnader utöver att bara dela direkt med partner.



## <a name="faq"></a>VANLIGA FRÅGOR OCH SVAR

**Kan Contoso skicka en inbjudan som automatiskt löses, så att användaren bara är "redo att gå"? Eller behöver användaren alltid klicka dig igenom till inlösnings-URL: en?**

Slutanvändaren måste alltid klicka igenom medgivande upplevelsen innan de kan komma åt innehåll.

Om du kommer att bjuda in många gäst användare rekommenderar vi att du delegerar detta från dina centrala Azure AD-administratörer genom [att lägga till en användare i rollen för gäst deltagare i resurs organisationen](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role). Den här användaren kan bjuda in andra användare i partner organisationen genom att använda inloggnings gränssnittet, PowerShell-skript eller API: er. Detta minskar den administrativa belastningen på dina Azure AD-administratörer för att bjuda in eller sända inbjudningar till användare i partner organisationen.

**Kan Contoso tvinga Multi-Factor Authentication för gäst användare om dess partners inte har Multi-Factor Authentication?**

Ja. Mer information finns i [villkorlig åtkomst för B2B-samarbets användare](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

**Hur fungerar B2B-samarbete när den inbjudna partnern använder Federation för att lägga till sin egen lokala autentisering?**

Om partnern har en Azure AD-klient som är federerad för den lokala autentiserings infrastrukturen, uppnås lokalt enkel inloggning (SSO) automatiskt. Om partnern inte har en Azure AD-klient kan ett Azure AD-konto skapas för nya användare.

**Kan jag bjuda in gäst användare med e-postkonton för konsumenter?**

Det finns stöd för att bjuda in gäst användare med e-postkonton i Power BI. Detta inkluderar domäner som hotmail.com, outlook.com och gmail.com. Dessa användare kan dock få begränsningar utöver vad användare med arbets-eller skol konton får.
