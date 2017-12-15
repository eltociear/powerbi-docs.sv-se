---
title: Ansluta till QuickBooks Online med Power BI
description: "QuickBooks Online för Power BI"
services: powerbi
documentationcenter: 
author: joeshoukry
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
ms.author: yshoukry
ms.openlocfilehash: def174cb86b701f628e4637d3a9933a42c5a5740
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Ansluta till QuickBooks Online med Power BI
När du ansluter till dina QuickBooks Online-data från Power BI får du omedelbart en Power BI-instrumentpanel och Power BI-rapporter som tillhandahåller insikter om verksamhetens kassaflöde, lönsamhet, kunder med mera. Använd instrumentpanelen och rapporterna som de är eller anpassa dem för att fokusera på den information du är mest intresserad av. Data uppdateras automatiskt en gång per dag.

Anslut till [QuickBooks Online-innehållspaketet](https://dxt.powerbi.com/getdata/services/quickbooks-online) för Power BI.

>[!NOTE]
>Om du vill importera dina QuickBooks Online-data till Power BI, måste du vara administratör för ditt QuickBooks Online-konto och logga in med dina autentiseringsuppgifter som administratör för kontot.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getdata.png) 
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getservices.png) 
3. Välj **QuickBooks Online**och välj **Hämta**.
   
   ![](media/service-connect-to-quickbooks-online/qbo.png)
4. Välj **oAuth2** för autentiseringsmetod och välj **Logga in**. 
5. Ange dina autentiseringsuppgifter för QuickBooks Online när du uppmanas om detta och följ autentiseringsprocessen för QuickBooks Online. Om du redan är inloggad på QuickBooks Online i webbläsaren, behöver du inte ange några autentiseringsuppgifter.
   >[!NOTE]
   >Du måste ha autentiseringsuppgifter som administratör för ditt QuickBooks Online-konto.
6. Välj det företag som du vill ansluta till Power BI på nästa skärm.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)
7. Välj **Auktorisera** på nästa skärm för att starta importen. Det kan ta några minuter beroende på storleken på företagets data. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
   När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Nya objekt markeras med en gul asterisk \*.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_leftnavnew.png)
8. Välj instrumentpanelen QuickBooks Online. Det här är instrumentpanelen som Power BI skapade automatiskt för att visa dina importerade data. Du kan ändra den här instrumentpanelen till att visa dina data på det sätt som du vill. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_dash.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="troubleshooting"></a>Felsökning
**”Hoppsan! Det har uppstått ett fel”**

Om du får det här meddelandet när du har valt **Auktorisera**:

”Hoppsan! Det har uppstått ett fel.” Stäng det här fönstret och försök igen.

En annan användare prenumererar redan på programmet för det här företaget. Kontakta [e-post admin] om du vill göra ändringar i prenumerationen.”

![](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... det innebär att en annan administratör i ditt företag redan har anslutit till företagets data med Power BI. Be administratören att dela instrumentpanelen med dig. För närvarande kan bara en administratör ansluta ett visst QuickBooks Online-företags datauppsättning till Power BI. Efter att Power BI har skapar instrumentpanelen, kan administratören dela den med flera kollegor på samma Power BI-klienter.

**”Den här appen har inte ställts in till att tillåta anslutningar från ditt land”**

Power BI stöder för närvarande endast USA-utgåvor av QuickBooks Online. 

![](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Nästa steg
[Kom igång med Power BI](service-get-started.md)

[Power BI – grundläggande begrepp](service-basic-concepts.md)

