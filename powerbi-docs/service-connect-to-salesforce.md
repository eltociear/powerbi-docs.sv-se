---
title: Anslut till Salesforce med Power BI
description: Salesforce för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/30/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e36cff803af74d212f4c1804fe3a955a11c193cf
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34722461"
---
# <a name="connect-to-salesforce-with-power-bi"></a>Anslut till Salesforce med Power BI
Med Power BI kan du enkelt ansluta till ditt Salesforce.com-konto. När du skapar den här anslutningen, hämtas dina data och ger dig automatiskt en instrumentpanel och relaterade rapporter baserade på dina data.

Ansluta till [Salesforce-innehållspaketet](https://app.powerbi.com/getdata/services/salesforce) för Power BI eller läs mer om [Salesforce-integrering](https://powerbi.microsoft.com/integrations/salesforce) med Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-salesforce/pbi_getdata.png) 
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-salesforce/pbi_getservices.png) 
3. Klicka på **Salesforce** och välj **hämta**.  
   
   ![](media/service-connect-to-salesforce/salesforce.png)
4. Välj **logga in** för att initiera inloggningsflödet.
   
    ![](media/service-connect-to-salesforce/dialog.png)
5. När du uppmanas till det anger du dina Salesforce-autentiseringsuppgifter. Klicka på **tillåt** så att Power BI kan komma åt din grundläggande Salesforce-information och data.
   
   ![](media/service-connect-to-salesforce/sf_authorize.png)
6. Konfigurera vad du vill importera till Power BI med hjälp av listrutealternativet:
   
   * **Instrumentpanel**
     
     Välj en fördefinierad instrumentpanel baserat på en person (som **försäljningschef**). De här instrumentpanelerna hämtar en specifik uppsättning standarddata från Salesforce och inkluderar inte anpassade fält.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **Rapporter**
     
     Välj en eller flera anpassade rapporter från ditt Salesforce-konto. De här rapporterna matchar dina vyer i Salesforce och kan innehålla data från anpassade fält eller objekt.
     
     ![](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     Om du inte ser några rapporter, lägger du till eller skapar dem i ditt Salesforce-konto och försöker ansluta igen.
7. Klicka på **Anslut** för att starta importen. Under importen kan du se ett meddelande som visar att importen pågår. När importen är klar, ser du en instrumentpanel, rapport och datauppsättning för dina Salesforce-data listade i navigeringsfönstret till vänster.
   
   ![](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

Du kan ändra den här instrumentpanelen till att visa dina data på det sätt som du vill. Du kan ställa frågor med frågor och svar eller klicka på en panel för att [öppna den underliggande rapporten](service-dashboard-tiles.md) och [ändra panelerna](service-dashboard-edit-tile.md) i instrumentpanelen.

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) i instrumentpanelen
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="system-requirements-and-considerations"></a>Systemkrav och aspekter
- Ansluten med ett Salesforce-konto för produktion som har API-åtkomst aktiverat
- Behörighet har getts till Power BI-appen under inloggningen
- Kontot har tillräckligt med API-anrop tillgängliga för att hämta och uppdatera data
- En giltig autentiseringstoken krävs för uppdatering. Kontrollera att du har 5 eller mindre Salesforce-datauppsättningar importerade, eftersom Salesforce har en gräns på 5 autentiseringstoken per program
- API för Salesforce-rapporter har en begränsning som ger stöd för upp till 2 000 rader med data.


## <a name="troubleshooting"></a>Felsökning
Granska kraven ovan om det uppstår några fel. Observera också att möjligheten att logga in till en anpassad domän eller sandbox-domän inte stöds för närvarande.

### <a name="unable-to-connect-to-the-remote-server-message"></a>Meddelandet ”Det går inte att ansluta till fjärrservern”

Om meddelandet ”Det går inte att ansluta till fjärrservern” visas när du försöker ansluta till ditt Salesforce-konto rekommenderar vi att du tittar på den här lösningen i Outsystems-forumet: [Salesforce Connector Log In Error Message: Unable to connect to the remote server](https://www.outsystems.com/forums/Forum_TopicView.aspx?TopicId=17674&TopicName=log-in-error-message-unable-to-connect-to-the-remote-server&) (Felmeddelande vid inloggning i Salesforce-anslutningsappen: Det går inte att ansluta till fjärrservern)


## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Hämta data](service-get-data.md)

