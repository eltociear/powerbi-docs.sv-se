---
title: Så här köper du Power BI Premium
description: Lär dig hur du kan köpa Power BI Premium och ge åtkomst till innehåll för hela organisationen.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
LocalizationGroup: Premium
ms.openlocfilehash: 25e36334390ad88d7856124c67e275db5c7fcd1c
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383018"
---
# <a name="how-to-purchase-power-bi-premium"></a>Så här köper du Power BI Premium

> [!NOTE]
> Den här artikeln håller på att uppdateras för att beskriva nya funktioner, ge mer information och förbättra läsbarheten. 

Den här artikeln beskriver hur du köper Power BI Premium-kapacitet (P1–P3) till din organisation. Du köper Power BI Premium-kapacitet i administrationscentret för Microsoft 365, och du hanterar kapaciteterna i administratörsportalen för Power BI. Aktuell information om prissättning och planering finns på [prissättningssidan för Power BI](https://powerbi.microsoft.com/pricing/) och [Power BI Premium-kalkylatorn](https://powerbi.microsoft.com/calculator/).

Innehållsskapare behöver fortfarande en Power BI Pro-licens, även om organisationen använder Power BI Premium. Se till att du köper minst en Power BI Pro-licens för din organisation.

Om en Premium-prenumeration upphör att gälla har du 30 dagar med fullständig åtkomst till din kapacitet. Efter det återgår innehållet till en delad kapacitet. Modeller som är större än 1 GB kommer inte att stödjas i delad kapacitet.

## <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Skapa en ny klient med Power BI Premium P1

Om du inte har någon befintlig klient och vill skapa en, så kan du köpa Power BI Premium samtidigt. Följande länk vägleder dig genom processen med att skapa en ny klientorganisation och kan användas för att köpa Power BI Premium: [Power BI Premium P1-erbjudande](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1). När du skapar klientorganisationen blir du automatiskt tilldelad rollen som global Office 365-administratör för den klientorganisationen.

## <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Köp Power BI Premium-kapacitet för en befintlig organisation

Om du har en befintlig organisation (klientorganisation) måste du vara i rollen som global Office 365-administratör eller rollen faktureringsadministratör för att köpa prenumerationer och licenser. Mer information finns i [Om Office 365-administratörsroller](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

Om du vill köpa Premium-kapacitet följer du dessa steg:

1. Från Power BI-tjänsten väljer du Office 365-appväljaren och sedan **Admin**.

    ![Office 365-appväljaren](media/service-admin-premium-purchase/o365-app-picker.png)

    Du kan också bläddra till Administrationscenter för Microsoft 365. Du kommer dit genom att gå till https://portal.office.com och välja **Admin**.

1. Välj **Fakturering** > **Köp tjänster**.

1. Sök efter Power BI Premium-erbjudanden under **Andra alternativ**. Här visas en lista över med P1 till P3, EM3 och P1 (månad för månad).

1. Hovra över ellipsen (**. . .**) och välj sedan **Köp nu**.

    ![Köp nu](media/service-admin-premium-purchase/premium-purchase.png)

1. Slutför köpet genom att följa stegen.

När du har slutfört köpet visas skärmen **Köptjänster** med information om att objektet har köpts och har aktiverats.

![Om du har köpt Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

## <a name="purchase-additional-capacities"></a>Köper ytterligare kapaciteter

Nu när du har en kapacitet kan du lägga till fler allteftersom dina behov växer. Du kan använda valfri kombination av premiumkapacitets-SKU:er (från P1 till P3) i din organisation. De olika SKU:erna tillhandahåller olika resursfunktioner.

1. I administrationscentret för Microsoft 365 väljer du **Fakturering** > **Köptjänster**.

1. Söka efter det Power BI Premium-objekt som du vill köpa mer av under **Andra alternativ**.

1. Hovra över **ellipsen (...)** och välj sedan **Ändra licenskvantitet**.

    ![Ändra licensantal](media/service-admin-premium-purchase/premium-purchase-more.png)

1. Ändra det antal instanser av objektet som du vill ha. Välj **Skicka** när du är klar.

   > [!IMPORTANT]
   > Om du väljer **Skicka** debiteras det registrerade kreditkortet.

Sidan **Köp tjänster** visar sedan hur många instanser du har. De tillgängliga v-kärnorna återspeglar den nya kapacitet som köpts under **Kapacitetsinställningar** i Power BI-administratörsportalen.

![Tillgängliga v-kärnor för Power BI Premium](media/service-admin-premium-purchase/premium-capacities.png)

## <a name="cancel-your-subscription"></a>Avbryt din prenumeration

Du kan avbryta prenumerationen från Administrationscenter för Microsoft 365. Gör följande om du vill avbryta din Premium-prenumeration.

1. Gå till Administrationscenter för Microsoft 365.

1. Välj **Fakturering** > **Prenumerationer**.

1. Välj din Power BI Premium-prenumeration i listan.

1. Välj **Fler åtgärder** > **Avbryt prenumeration**.

1. Sidan **Avbryt prenumeration** visar huruvida du är skyldig att betala en [avgift för tidig uppsägning](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3) eller inte. På den här sidan anges även när data tas bort för prenumerationen.

1. Läs igenom informationen och välj **Avbryt prenumeration** om du vill fortsätta.

### <a name="when-canceling-or-your-license-expires"></a>När du avbryter eller licensen upphör att gälla

När du avbryter din Premium-prenumeration eller kapacitetslicensen upphör att gälla, kan du fortsätta att få åtkomst till din Premium-kapacitet under en period på 30 dagar från datumet för avbrottet eller då licensen upphör att gälla. Efter 30 dagar kommer du inte längre att kunna komma åt din Premium-kapaciteter eller arbetsytor i dem.

## <a name="next-steps"></a>Nästa steg

[Power BI-prissättningsida](https://powerbi.microsoft.com/pricing/)   
[Power BI Premium-kalkylator](https://powerbi.microsoft.com/calculator/)   
[Vanliga frågor och svar om Power BI Premium](service-premium-faq.md)   
[Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/pbienterprisedeploy)

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)