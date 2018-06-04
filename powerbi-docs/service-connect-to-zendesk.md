---
title: Anslut till Zendesk med Power BI
description: Zendesk för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 997dd8b598e67d590723c72fb35245c3b3486c8b
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34242456"
---
# <a name="connect-to-zendesk-with-power-bi"></a>Anslut till Zendesk med Power BI
Zendesk-innehållspaketet erbjuder en Power BI-instrumentpanel och en uppsättning Power BI-rapporter som ger inblick om dina biljettvolymer och prestanda för agenter. Du kan använda instrumentpanelen de rapporter som tillhandahålls, eller anpassa dem för att fokusera på den information som du är mest intresserad av.  Data uppdateras automatiskt en gång per dag. 

Anslut till [Zendesk-innehållspaketet](https://app.powerbi.com/getdata/services/zendesk) eller läs mer om [Zendesk-integrering](https://powerbi.microsoft.com/integrations/zendesk) med Power BI.

>[!NOTE]
>Ett Zendesk-administratörskonto krävs för att ansluta. Mer information om [kraven](#Requirements) finns nedan.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-zendesk/pbi_getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-zendesk/pbi_getservices.png) 
3. Välj **Zendesk** \> **hämta.**
   
   ![](media/service-connect-to-zendesk/zendesk.png)
4. Ange den URL som är kopplad till ditt konto. Den är i formatet **https://company.zendesk.com**. Information om att [hitta dessa parametrar](#FindingParams) finns nedan.
   
   ![](media/service-connect-to-zendesk/pbi_zendeskconnect.png)
5. När du uppmanas till det anger du dina Zendesk-autentiseringsuppgifter.  Välj **oAuth 2** som autentiseringsmetod och klicka på **Logga in**. Följ Zendesk-autentiseringsflödet. (Om du redan är inloggad på Zendesk i webbläsaren, behöver du kanske inte ange några autentiseringsuppgifter.)
   
   > [!NOTE]
   > Det här innehållspaketet kräver att du ansluter med ett Zendesk-administratörskonto. 
   > 
   > 
   
   ![](media/service-connect-to-zendesk/pbi_zendesksignin.png)
6. Klicka på **Tillåt** för att låta Power BI komma åt dina Zendesk-data.
   
   ![](media/service-connect-to-zendesk/zendesk2.jpg)
7. Klicka på **Anslut** för att starta importen. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Nya objekt markeras med en gul asterisk \*.
   
   ![](media/service-connect-to-zendesk/pbi_zendeskdash.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="whats-included"></a>Vad ingår
Power BI-innehållspaketet inkluderar data om följande:  

* Användare (slutanvändare och agenter)  
* Organisationer  
* Grupper  
* Biljetter  

Det finns också en uppsättning åtgärder som har beräknats, till exempel genomsnittlig väntetid och lösta biljetter under de senaste 7 dagarna. En fullständig lista finns i innehållspaketet.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Systemkrav
Ett Zendesk-administratörskonto krävs för att komma åt Zendesk-innehållspaketet. Om du är en agent eller en slutanvändare och är intresserad av att visa dina Zendesk-data, lägg till ett förslag och granska Zendesk-anslutningsprogrammet i [Power BI Desktop](desktop-connect-to-data.md).

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Din Zendesk URL kommer att vara samma som den URL som du använder för att logga in på ditt Zendesk-konto. Om du inte är säker på din Zendesk-URL, kan du använda Zendesk [inloggningshjälp](https://www.zendesk.com/login/).

## <a name="troubleshooting"></a>Felsökning
Om du har problem med att ansluta, kontrollera din Zendesk-URL och bekräfta att du använder ett Zendesk-administratörskonto.

## <a name="next-steps"></a>Nästa steg
* [Kom igång med Power BI](service-get-started.md)
* [Hämta data](service-get-data.md)

