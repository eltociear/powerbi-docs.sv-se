---
title: Ange kontaktuppgifter för rapporter och instrumentpaneler
description: Läs hur du anger kontaktuppgifter för rapporter och instrumentpaneler.
author: LukaszPawlowski-MS
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 10/08/2019
ms.author: lukaszp
LocalizationGroup: Common tasks
ms.openlocfilehash: 7ed0920f66c178c23e6c4db22ff6acd998619522
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76160568"
---
# <a name="set-contact-information-for-reports-and-dashboards-in-the-power-bi-service"></a>Ange kontaktuppgifter för rapporter och instrumentpaneler i Power BI-tjänsten
I den här artikeln får du veta hur du anger kontaktuppgifter för en instrumentpanel eller rapport i Power BI-tjänsten.

> [!NOTE]
> Kontaktuppgifter kan anges för objekt i en klassisk eller ny arbetsyta. Du kan inte ange kontaktuppgifter för objekt i din Min arbetsyta. Informationskortet visas när du visar en rapport eller instrumentpanel i det [nya utseendet](service-new-look.md).

Du kan lägga till flera användare eller grupper i kontakten för ett objekt. De kan vara:
* En person
* En Office 365-grupp
* En e-postaktiverad säkerhetsgrupp
* En distributionslista

Som standard är den person som skapar en ny rapport eller instrumentpanel kontakten för den. Om du anger ett värde åsidosätts standardvärdet. Du kan givetvis ta bort alla personer eller grupper från kontaktlistan. När du gör detta för klassiska arbetsytor kommer Office 365-gruppen för arbetsytan att visas. För den nya arbetsyteupplevelsen kommer [arbetsytans kontaktlista](service-create-the-new-workspaces.md#workspace-contact-list) att användas. Om arbetsytans kontaktlista inte anges, visas arbetsytans administratörer.

Kontaktuppgifterna visas för personer som visar objektet. 

 ![servicerapportkontakt](media/service-item-contact/service-report-contact.png)

När du klickar på listan över kontakter skapas ett e-postmeddelande så att du kan ställa frågor eller få hjälp. 

 ![servicekontakt-e-post](media/service-item-contact/service-contact-email.png)
 
Kontaktlistans uppgifter används även på andra platser. Den visas till exempel i vissa felscenarier i feldialogrutan. Automatiserade e-postmeddelanden relaterade till objektet, till exempel åtkomstbegäranden, skickas till kontaktlistan. 

> [!NOTE]
> När du publicerar en app anges de kontaktuppgifter som angetts för enskilda objekt till den person som publicerade eller uppdaterade appen. Du kan ställa in appens support-URL så att appanvändarna får den hjälp de behöver.

## <a name="set-contact-information-for-a-report"></a>Ange kontaktuppgifter för en rapport
1. Stanna kvar på arbetsytan och välj fliken **Rapporter**.
2. Leta upp den önskade rapporten och välj **Inställningar**-ikonen.
3. Leta upp inmatningsfältet **Kontakt** och ange ett värde.

     ![inställning för servicerapportkontakt](media/service-item-contact/service-report-contact-setting.png)

## <a name="set-contact-information-for-a-dashboard"></a>Ange kontaktuppgifter för en instrumentpanel
1. Stanna kvar på arbetsytan och välj fliken **Datauppsättningar**.
2. Leta upp den önskade instrumentpanelen och välj **Inställningar**-ikonen
3. Leta upp inmatningsfältet **Kontakt** och ange ett värde.

     ![inställningar för serviceinstrumentpanelskontakt](media/service-item-contact/service-dashboard-contact-setting.png)

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
* Kontakten anges automatiskt för nya objekt som skapas i Power BI-tjänsten. Befintliga objekt visar arbetsytans standardvärde.
* Du kan ange valfri användare eller grupp i kontaktlistan, men de kommer inte att beviljas åtkomst till objektet automatiskt. Använd delning eller ge användare som behöver det åtkomst till arbetsytan via en roll. 
* Kontaktlistan på postnivå flyttas inte till appar när de publiceras. Den nya navigeringsupplevelsen för appar ger en support-URL som du konfigurerar för att hjälpa till att hantera feedback från ett stort antal appanvändare.


## <a name="next-steps"></a>Nästa steg

Fler frågor? [Prova Power BI Community](https://community.powerbi.com/)
