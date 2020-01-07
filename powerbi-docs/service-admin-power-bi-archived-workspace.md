---
title: Power BI – arkiverad arbetsyta
description: Power BI-arkiverad arbetsyta efter att du hanterat din Office 365-klient
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/18/2019
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 403bf213cc2da7ad803780946e606433166e3484
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2020
ms.locfileid: "74699968"
---
# <a name="power-bi-archived-workspace"></a>Power BI – arkiverad arbetsyta

> [!IMPORTANT]
> Power BI stöder inte längre funktionen Arkiverad arbetsyta, som tas bort i slutet av 2019. Om du använder Arkiverad arbetsyta bör du omedelbart återskapa det innehåll som du vill behålla på en ny arbetsyta i din aktuella klientorganisation. Du kan inte förvänta dig fortsatt åtkomst till Arkiverad arbetsyta. Power BI stöder inte längre den relaterade funktionen [externt övertagande av en Azure AD-klientorganisation](service-admin-faq.md#what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users).

Med Power BI, kan vem som helst registrera sig och börja använda tjänsten inom några minuter.  Senare kan din organisations IT-avdelning välja att ta över hanteringen av Power BI för användare i din organisation.  Om detta inträffar kan du dra nytta av central hantering av användare och behörigheter i din organisation. Du kanske också kan dra nytta av effektiviserad inloggning med samma användarnamn och lösenord för andra tjänster i din organisation.

Allt innehåll som du har skapat innan din IT-avdelning började hantera Power BI placeras i en Power BI-arkiverad arbetsyta, som kan nås från navigeringsfönstret i [Power BI](https://app.powerbi.com). Du bör skapa nytt Power BI-innehåll i min arbetsyta som är skyddad och hanteras av din organisations IT-avdelning.  Din arkiverade arbetsyta kommer att fortsätta finnas, men det finns begränsningar på de åtgärder som du kan utföra på innehållet i din arkiverade arbetsyta.  Om du vill ta bort dessa begränsningar, behöver du migrera innehållet från din arkiverade arbetsyta till min arbetsyta som hanteras av din IT-avdelning.

## <a name="restrictions-in-your-archived-workspace"></a>Begränsningar i din arkiverade arbetsyta

Power BI kommer inte att ta bort innehållet från din arkiverade arbetsyta. Du kan fortsätta att hämta data, skapa rapporter och instrumentpaneler och uppdatera datauppsättningar. Befintliga användare som du har delat innehåll med kommer fortfarande att kunna visa innehållet i sina arkiverade arbetsytor också. Det finns dock några begränsningar för innehållet i din arkiverade arbetsyta:

* **OneDrive för företag**: Du kommer inte längre att kunna hämta data eller uppdatera från OneDrive för företag för datauppsättningar på din arkiverade arbetsyta.  Om du försöker ansluta till den här källan, får du en varning.

* **Dela instrumentpaneler**: Du kan inte dela instrumentpaneler med andra användare från din arkiverade arbetsyta.  Alla användare som redan har tillgång kommer att fortsätta att kunna visa delade instrumentpaneler genom att gå in på sin arkiverade arbetsyta.

* **Skapa grupper**: Du kan inte skapa grupper på din arkiverade arbetsyta.

* **Åtkomst i Power BI-mobilappar**: Även om du fortfarande kan visa innehåll på webben på din arkiverade arbetsyta, visas det här innehållet inte längre i Power BI-mobilappar.

## <a name="migrating-content-in-your-archived-workspace"></a>Migrera innehåll i din arkiverade arbetsyta

Om du vill använda Power BI bör du skapa nytt innehåll i Min arbetsyta. Du bör också planera att migrera allt innehåll i din arkiverade arbetsyta till Min arbetsyta.  Hur du migrerar innehållet beror på vilken typ av innehåll det rör sig om:

* **Datauppsättningar för Excel eller Power BI Desktop**: Migrera de här datauppsättningarna genom att växla från din arkiverade arbetsyta till Min arbetsyta och ladda upp Excel- eller Power BI Desktop-filen på nytt genom att klicka på knappen **Mina data**.  Om du ställer in schemalagd uppdatering, måste du konfigurera om inställningarna för den nya datauppsättningen i min arbetsyta.

* **Övriga datauppsättningar**: Växla till Min arbetsyta och återanslut sedan till andra datauppsättningar som du skapat på din arkiverade arbetsyta genom att klicka på knappen **Hämta data**.  Du kan behöva ange säkerhets- eller anslutningsinformationen igen.

* **Rapporter**: Rapporter som finns i Excel- eller Power BI Desktop-filer återskapas automatiskt när du överför motsvarande Excel- eller Power BI Desktop-fil. Rapporter som installeras som en del av ett innehållspaket återskapas också när du återansluter till innehållspaketet. Om du skapade dina egna rapporter via Power BI-tjänsten behöver du återskapa de rapporterna i din Min arbetsyta.

* **Instrumentpaneler**: Instrumentpaneler som installeras som en del av innehållspaket återskapas automatiskt när du återansluter till innehållspaketet på Min arbetsyta. Om du skapade dina egna instrumentpaneler via Power BI-tjänsten behöver du återskapa de instrumentpanelerna i Min arbetsyta.

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

