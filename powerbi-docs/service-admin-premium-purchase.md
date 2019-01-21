---
title: Så här köper du Power BI Premium
description: Lär dig hur du kan köpa Power BI Premium och ge åtkomst till innehåll för hela organisationen.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/14/2019
ms.author: mblythe
LocalizationGroup: Premium
ms.openlocfilehash: ebcf4a6467991bfc0d434302cd2c846ca4af1a5c
ms.sourcegitcommit: a20825ebd0ef4c2cb77232e3dd0e9f8260cacf71
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54324007"
---
# <a name="how-to-purchase-power-bi-premium"></a>Så här köper du Power BI Premium

Den här artikeln beskriver hur du köper Power BI Premium-kapacitet till din organisation. Du köper Power BI Premium-kapacitet i administrationscentret för Office 365, och du [hanterar kapaciteterna](service-admin-premium-manage.md) i administratörsportalen för Power BI.

<iframe width="640" height="360" src="https://www.youtube.com/embed/NkvYs5Qp4iA?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

Mer information om Power BI Premium finns i [Vad är Power BI Premium?](service-premium.md). Aktuell information om prissättning och planering finns på [prissättningssidan för Power BI](https://powerbi.microsoft.com/pricing/) och [Power BI Premium-kalkylatorn](https://powerbi.microsoft.com/calculator/).

> [!IMPORTANT]
> Innehållsförfattare behöver fortfarande en Power BI Pro-licens, även om organisationen använder Power BI Premium. Se till att du köper minst en Power BI Pro-licens för din organisation.
>
>Om en Premium-prenumeration upphör att gälla har du 30 dagar med fullständig åtkomst till din kapacitet. Efter det återgår innehållet till en delad kapacitet. Modeller som är större än 1 GB kommer inte att stödjas i delad kapacitet.

## <a name="create-a-new-tenant-with-power-bi-premium-p1"></a>Skapa en ny klient med Power BI Premium P1

Om du inte har någon befintlig klient och vill skapa en, så kan du köpa Power BI Premium samtidigt. Följande länk vägleder dig genom processen med att skapa en ny klientorganisation och kan användas för att köpa Power BI Premium: [Power BI Premium P1-erbjudande](https://signup.microsoft.com/Signup?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1).

![Power BI Premium P1](media/service-admin-premium-purchase/premium-purchase-with-tenant.png)

När du skapar klientorganisationen blir du automatiskt tilldelad rollen som global Office 365-administratör för den klientorganisationen.

## <a name="purchase-a-power-bi-premium-capacity-for-an-existing-organization"></a>Köp Power BI Premium-kapacitet för en befintlig organisation

Om du har en befintlig organisation måste du vara i rollen global Office 365-administratör eller rollen faktureringsadministratör för att köpa prenumerationer och licenser. Mer information finns i [Om Office 365-administratörsroller](https://support.office.com/article/About-Office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d).

Om du vill köpa en Premium-kapacitet följer du dessa steg.

1. Från Power BI-tjänsten väljer du Office 365-appväljaren och sedan **Admin**.

    ![Office 365-appväljaren](media/service-admin-premium-purchase/o365-app-picker.png)

    Du kan också bläddra till Administrationscenter för Office 365. Du kommer dit genom att gå till https://portal.office.com och välja **Admin**.

1. Välj **Fakturering** > **Köp tjänster**.

1. Sök efter Power BI Premium-erbjudanden under **Andra alternativ**. Här visas en lista över med P1 till P3, EM3 och P1 (månad för månad).

1. Hovra över ellipsen (**. . .**) och välj sedan **Köp nu**.

    ![Köp nu](media/service-admin-premium-purchase/premium-purchase.png)

1. Slutför köpet genom att följa stegen.

Du kan också välja en av följande länkar som leder dig direkt till inköpssidan för respektive SKU. Mer information om dessa SKU:er finns i [Vad är Power BI Premium?](service-premium.md#premium-capacity-nodes).

> [!IMPORTANT]
> Om du väljer någon av länkarna nedan uppstår ett fel om du inte är i rollen global Office 365 Global-administratör eller rollen faktureringsadministratör.

| Direktköpslänkar |
| --- |
| [EM3-SKU (månad för månad)](https://portal.office.com/commerce/completeorder.aspx?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |
| [P1-SKU](https://portal.office.com/commerce/completeorder.aspx?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |
| [P1-SKU (månad för månad)](https://portal.office.com/commerce/completeorder.aspx?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) |
| [P2-SKU](https://portal.office.com/commerce/completeorder.aspx?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |
| [P3-SKU](https://portal.office.com/commerce/completeorder.aspx?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |

När du har slutfört köpet visas skärmen **Köptjänster** med information om att objektet har köpts och har aktiverats.

![Om du har köpt Power BI Premium](media/service-admin-premium-purchase/premium-purchased.png)

## <a name="purchase-additional-capacities"></a>Köper ytterligare kapaciteter

Nu när du har en kapacitet kan du lägga till fler allteftersom dina behov växer. Du kan använda valfri kombination av premiumkapacitets-SKU:er (från P1 till P3) i din organisation. De olika SKU:erna tillhandahåller olika resursfunktioner.

1. I administrationscentret för Office 365 väljer du **Fakturering** > **Köptjänster**.

1. Söka efter det Power BI Premium-objekt som du vill köpa mer av under **Andra alternativ**.

1. Hovra över **ellipsen (...)** och välj sedan **Ändra licenskvantitet**.

    ![Ändra licensantal](media/service-admin-premium-purchase/premium-purchase-more.png)

1. Ändra det antal instanser av objektet som du vill ha. Välj **Skicka** när du är klar.

   > [!IMPORTANT]
   > Om du väljer **Skicka** debiteras det registrerade kreditkortet.

Sidan **Köp tjänster** visar sedan hur många instanser du har. De tillgängliga v-kärnorna återspeglar den nya kapacitet som köpts under **Kapacitetsinställningar** i Power BI-administratörsportalen.

![Tillgängliga v-kärnor för Power BI Premium](media/service-admin-premium-purchase/premium-capacities.png)

## <a name="cancel-your-subscription"></a>Avbryt din prenumeration

Du kan avbryta prenumerationen från Administrationscenter för Office 365. Gör följande om du vill avbryta din Premium-prenumeration.

![Avbryt prenumeration](media/service-admin-premium-purchase/premium-cancel-subscription.png)

1. Bläddra fram till Administrationscenter för Office 365.

1. Välj **Fakturering** > **Prenumerationer**.

1. Välj din Power BI Premium-prenumeration i listan.

1. Välj **Avbryt prenumeration** i listrutan **Fler åtgärder**.

    ![Fler åtgärder](media/service-admin-premium-purchase/o365-more-actions.png)

1. Sidan **Avbryt prenumeration** visar huruvida du är skyldig att betala en [avgift för tidig uppsägning](https://support.office.com/article/early-termination-fees-6487d4de-401a-466f-8bc3-c0beb5cc40d3) eller inte. På den här sidan anges även när data tas bort för prenumerationen.

1. Läs igenom informationen och välj **Avbryt prenumeration** om du vill fortsätta.

## <a name="next-steps"></a>Nästa steg

[Power BI-prissättningssida](https://powerbi.microsoft.com/pricing/)
[Power BI Premium-kalkylator](https://powerbi.microsoft.com/calculator/)
[Vad är Power BI Premium?](service-premium.md)
[Vanliga frågor och svar om Power BI Premium](service-premium-faq.md)
[Microsoft Power BI Premium – white paper](https://aka.ms/pbipremiumwhitepaper)
[Planera ett white paper för en företagsdistribution för Power BI](https://aka.ms/pbienterprisedeploy)

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)