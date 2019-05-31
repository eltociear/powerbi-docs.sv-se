---
title: Anslut till Zendesk med Power BI
description: Zendesk för Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: sarinas
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 04/26/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 1edc4179b000191dfeff87387417009bc28e0ee5
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578875"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Anslut till Zendesk med Power BI

Den här artikeln beskriver hur du hämtar data från ditt Zendesk-konto med en mall för Power BI-appen. Zendesk-appen erbjuder en Power BI-instrumentpanel och en uppsättning Power BI-rapporter som ger insikter om dina biljettvolymer och agentprestanda. Data uppdateras automatiskt en gång per dag. 

När du har installerat appen mall kan anpassa du instrumentpanelen och rapporterna att markera den information som är mest intresserad av. Du kan sedan distribuera den som en app till kollegor i din organisation.

Anslut till [Zendesk-innehållspaketet](https://app.powerbi.com/getdata/services/zendesk) eller läs mer om [Zendesk-integrering](https://powerbi.microsoft.com/integrations/zendesk) med Power BI.

När du har installerat appen mall, kan du ändra instrumentpanelen och rapporterna. Du kan sedan distribuera den som en app till kollegor i din organisation.

>[!NOTE]
>Du behöver ett Zendesk-administratör-konto för att ansluta. Mer information om [kraven](#system-requirements) finns nedan.

## <a name="how-to-connect"></a>Så här ansluter du

[!INCLUDE [powerbi-service-apps-get-more-apps](./includes/powerbi-service-apps-get-more-apps.md)]

3. Välj **Zendesk** \> **Hämta nu**.
4. I **installera den här Power BI-appen?** Välj **installera**.
4. I den **appar** väljer den **Zendesk** panelen.

    ![Power BI Zendesk appanelen](media/service-connect-to-zendesk/power-bi-zendesk-tile.png)

6. I **Kom igång med din nya app**väljer **Anslut data**.

    ![Kom igång med din nya app](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

4. Ange den URL som är kopplad till ditt konto. URL: en har formatet **https://company.zendesk.com** . Se information om att [hitta parametrarna](#finding-parameters) nedan.
   
   ![Anslut till Zendesk](media/service-connect-to-zendesk/pbi_zendeskconnect.png)

5. När du uppmanas till det anger du dina Zendesk-autentiseringsuppgifter.  Välj **oAuth 2** som autentiseringsmetod och klicka på **Logga in**. Följ Zendesk-autentiseringsflödet. (Om du är redan inloggad på Zendesk i webbläsaren, du kan inte ange några autentiseringsuppgifter.)
   
   > [!NOTE]
   > Det här Innehållspaketet kräver att du ansluter med ett Zendesk-administratör-konto. 
   > 
   
   ![Logga in med oAuth2](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Klicka på **Tillåt** för att låta Power BI komma åt dina Zendesk-data.
   
   ![Klicka på Tillåt](media/service-connect-to-zendesk/zendesk2.jpg)
7. Klicka på **Anslut** för att starta importen. 
8. När Power BI har importerat data visas i listan med innehåll för din Zendesk-app: en ny instrumentpanel, rapport och datauppsättning.
9. Välj instrumentpanelen för att börja utforska.

    ![Zendesk dashboard](media/service-connect-to-zendesk/power-bi-zendesk-dashboard.png)
   
## <a name="modify-and-distribute-your-app"></a>Ändra och distribuera din app

Du har installerat appen Zendesk-mall. Det innebär att du har också skapat Zendesk app-arbetsytan. I arbetsytan kan du ändra rapporten och instrumentpanelen och sedan distribuera den som en *app* till kollegor i din organisation. 

1. Om du vill visa hela innehållet i den nya Zendesk-arbetsytan i det vänstra navigeringsfältet, väljer **arbetsytor** > **Zendesk**. 

    ![Zendesk-arbetsyta i det vänstra navigeringsfönstret](media/service-connect-to-zendesk/power-bi-zendesk-workspace-left-nav.png)

    Den här vyn är listan med innehåll för arbetsytan. I det övre högra hörnet ser du **uppdatera app**. När du är redo att distribuera appen till dina kollegor, är det där du börjar. 

    ![Zendesk content list](media/service-connect-to-zendesk/power-bi-zendesk-content-list.png)

2. Välj **rapporter** och **datauppsättningar** så att andra element på arbetsytan.

    Läs mer om [distribuera appar](service-create-distribute-apps.md) till dina kollegor.

## <a name="system-requirements"></a>Systemkrav
Ett Zendesk-administratörskonto krävs för att komma åt Zendesk-innehållspaketet. Om du är en agent eller en slutanvändare och är intresserad av att visa dina Zendesk-data, Lägg till ett förslag och granska Zendesk-anslutningsprogrammet i den [Power BI Desktop](desktop-connect-to-data.md).

## <a name="finding-parameters"></a>Hitta parametrar
Din Zendesk URL kommer att vara samma som den URL som du använder för att logga in på ditt Zendesk-konto. Om du inte är säker på din Zendesk-URL, kan du använda Zendesk [inloggningshjälp](https://www.zendesk.com/login/).

## <a name="troubleshooting"></a>Felsökning
Om du har problem med att ansluta, kontrollera din Zendesk-URL och bekräfta att du använder ett Zendesk-administratörskonto.

## <a name="next-steps"></a>Nästa steg

* [Skapa nya arbetsytor i Power BI](service-create-the-new-workspaces.md)
* [Installera och använda appar i Power BI](consumer/end-user-apps.md)
* [Ansluta till Power BI-appar för externa tjänster](service-connect-to-services.md)
* Har du några frågor? [Fråga Power BI Community](http://community.powerbi.com/)

