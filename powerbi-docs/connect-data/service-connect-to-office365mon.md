---
title: Ansluta till Office365Mon med Power BI
description: Office365Mon för Power BI
author: paulinbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 11/26/2019
ms.author: painbar
LocalizationGroup: Connect to services
ms.openlocfilehash: 422782c3036f94c1ea764f46135200116092d70c
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86216241"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Ansluta till Office365Mon med Power BI
Det är lätt att analysera dina Office 365-avbrott och hälsoprestandadata med Power BI och Office365Mon-mallappen. Power BI hämtar dina data, inklusive avbrott och hälsoavsökningar, och skapar sedan en anpassad instrumentpanel och rapporter som baseras på dessa data.

Anslut till [Office365Mon-mallappen](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3) för Power BI.

>[!NOTE]
>Du måste ha ett Office365Mon-administratörskonto för att kunna ansluta och läsa in Power BI-mallappen.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i navigeringsfönstret.
   
   ![Skärmbild av knappen Hämta data i navigeringsfönstret.](media/service-connect-to-office365mon/pbi_getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![Skärmbild av dialogrutan Tjänster och knappen Hämta.](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Välj **Office365Mon** \> **Hämta**.
   
   ![Skärmbild av dialogrutan Office365Mon med länken Hämta.](media/service-connect-to-office365mon/o365mon.png)
4. Som autentiseringsmetod väljer du **oAuth2** \> **Logga in**.
   
   När du uppmanas till det anger du autentiseringsuppgifterna som Office365Mon-administratör och följer autentiseringsprocessen.
   
   ![Skärmbild av dialogrutan Anslut till Office365Mon med o Auth2 i fältet Autentiseringsmetod.](media/service-connect-to-office365mon/creds.png)
   
   ![Skärmbild av inloggningen till Office365Mon där du uppmanas att ange autentiseringsuppgifter.](media/service-connect-to-office365mon/creds2.png)
5. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datamängd i navigeringsfönstret. Nya objekt har markerats med en gul asterisk \*, välj Office365Mon-posten.
   
   ![Skärmbild av navigeringsfönstret i Power BI med instrumentpanelen, rapporten och datamängden.](media/service-connect-to-office365mon/dashboard4.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](../consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](../create-reports/service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](../consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="troubleshooting"></a>Felsökning
Om du får felet **”Inloggningen misslyckades”** när du använder dina Office365Mon-autentiseringsuppgifter för prenumerationen, har inte kontot du använder behörighet att hämta Office365Mon-data från ditt konto. Kontrollera att det är ett administratörskonto och försök igen.

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI?](../fundamentals/power-bi-overview.md)

[Hämta data för Power BI](service-get-data.md)
