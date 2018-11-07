---
title: Vanliga frågor och svar om anpassade visuella Power BI-objekt
description: Bläddra i en lista med vanliga frågor och svar om anpassade visuella Power BI-objekt
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 064d32944f52f6e391d4a7ec4df41ecbf09b7e3f
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223086"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Vanliga frågor och svar om anpassade visuella Power BI-objekt

## <a name="organizational-custom-visuals"></a>Anpassade visuella objekt i en organisation

**Hur hanterar administratören anpassade visuella objekt i en organisation?**

Under fliken ”Anpassade virtuella objekt i organisationen” i administrationsportalen kan administratören se och [hantera alla anpassade visuella objekt i företaget](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals): lägga till, inaktivera, aktivera och ta bort.
Det finns inte längre något behov av att dela dessa visuella objekt via e-postmeddelanden eller en delad mapp! När de anpassade visuella objekten väl har distribuerats till organisationens databas, kan användarna i organisationen enkelt identifiera och importera dem till sina rapporter direkt från Power BI Desktop eller Service. Du kan hitta de anpassade visuella objekten i organisationen i det inbyggda lagret (Desktop och Service) på fliken MIN ORGANISATION. När administratören laddar upp en ny version av ett anpassat visuellt objekt i organisationen, så hämtar alla i organisationen samma uppdaterade version. Rapportförfattarna behöver inte ta bort de visuella objekten i sina rapporter för att få tillgång till de nya versionerna, eftersom alla rapporter som använder dessa visuella objekt uppdateras automatiskt! Uppdateringsmekanismen påminner om den för visuella marknadsplatsobjekt.

**Om en administratör överför ett anpassat visuellt objekt från den offentliga marknadsplatsen till organisationsarkivet, uppdateras det då automatiskt så snart som leverantören uppdaterar det visuella objektet på den offentliga marknadsplatsen?**

Nej, det finns ingen automatisk uppdatering från den offentliga marknadsplatsen.
Det är administratörens ansvar att uppdatera det anpassade visuella objektets version i organisationen, om så önskas.

**Finns det något sätt att inaktivera organisationslagret?**

Nej, användarna ser alltid fliken MIN ORGANISATION från Power BI Desktop och Service. Administratören kan inaktivera eller ta bort alla anpassade visuella objekt från administrationsportalen, varvid organisationenslagret töms.
  
**Om administratören inaktiverar anpassade visuella objekt från administrationsportalen (klientinställningar), har användarna då fortfarande åtkomst till de anpassade visuella objekten?**

Ja, om administratören inaktiverar de anpassade visuella objekten från administrationsportalen, så påverkar det inte organisationslagret. Vissa organisationer inaktiverar anpassade visuella objekt och aktiverar endast utvalda visuella objekt som har importerats och laddats upp av Power BI-administratören till organisationslagret. Inaktivering av de anpassade visuella objekten från administrationsportalen påtvingas inte i Power BI Desktop. Datoranvändare kan fortfarande lägga till och använda anpassade visuella objekt från den offentliga marknadsplatsen i sina rapporter. Dessa offentliga anpassade visuella objekt upphör att återges så snart de har publicerats till Power BI-tjänsten och utlöser ett fel. När du använder Power BI-tjänsten går det inte att importera anpassade visuella objekt från den offentliga marknadsplatsen. Visuella objekt från organisationslagret kan importeras eftersom inställningen för anpassade visuella objekt i administrationsportalen påtvingas i Power BI-tjänsten.

**Varför utgör organisationslagret och anpassade visuella objekt en utmärkt företagslösning?**

* Alla får samma version av virtuella objekt, vilket kontrolleras av Power BI-administratören. När administratören uppdaterar det visuella objektets version i administratörsportalen får alla användare i organisationen automatiskt tillgång till den uppdaterade versionen.

* Det finns inte längre något behov av att dela visuella filer via e-post eller delade mappar! Ett ställe som är synligt för alla inloggade medlemmar.

* Säkerhet och support, nya versioner av anpassade visuella objekt i organisationen uppdateras automatiskt i alla rapporter som liknar de visuella objekten på marknadsplatsen.

* Användare i organisationen som använder de anpassade visuella objekten i organisationen måste vara inloggade för att kunna se och använda de anpassade visuella objekten, vilket är ett säkerhetselement för organisationen.

* Administratörer kan styra vilka anpassade visuella objekt som ska vara tillgängliga i organisationen.

* Administratörer kan aktivera/inaktivera visuella objekt för testning från administratörsportalen. Bättre säkerhetstillämpning eftersom dessa visuella objekt endast är tillgängliga för organisationens medlemmar.

## <a name="certified-custom-visuals"></a>Certifierade anpassade visuella objekt

**Vad är certifierade anpassade visuella objekt?**

Certifierade anpassade visuella objekt är visuella objekt på [marknadsplatsen](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) som uppfyller vissa [specificerade](power-bi-custom-visuals-certified.md) kodkrav och testning av Power BI-teamet.  De tester som utförs har utformats för att kontrollera att det visuella objektet inte har tillgång till externa tjänster eller resurser. Microsoft är dock inte producent av anpassade visuella objekt från tredje part, och vi rekommenderar att kunderna kontaktar författaren direkt för att verifiera funktionaliteten hos dessa visuella objekt.

## <a name="next-steps"></a>Nästa steg

Information om felsökning finns i [Felsöka dina anpassade visuella objekt i Power BI](power-bi-custom-visuals-troubleshoot.md).
