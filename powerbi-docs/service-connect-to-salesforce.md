---
title: Anslut till Salesforce med Power BI
description: "Salesforce för Power BI"
services: powerbi
documentationcenter: 
author: SarinaJoan
manager: kfile
backup: maggiesMSFT
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/16/2017
ms.author: sarinas
ms.openlocfilehash: fabdf9b9702c3da1374c8b5c7ee7e356ae471af9
ms.sourcegitcommit: c24e5d7bd1806e0d637e974b5143ab5125298fc6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/19/2018
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
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="system-requirements"></a>Systemkrav
* Ansluten med ett Salesforce-konto för produktion som har API-åtkomst aktiverat
* Behörighet har getts till Power BI-appen under inloggningen
* Kontot har tillräckligt med API-anrop tillgängliga för att hämta och uppdatera data
* En giltig autentiseringstoken krävs för uppdatering. Kontrollera att du har 5 eller mindre Salesforce-datauppsättningar importerade, eftersom Salesforce har en gräns på 5 autentiseringstoken per program

## <a name="troubleshooting"></a>Felsökning
Granska kraven ovan om det uppstår några fel. Observera också att möjligheten att logga in till en anpassad eller sandbox-domän inte stöds för tillfället.

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Hämta data](service-get-data.md)

