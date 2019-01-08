---
title: Ansluta till Office365Mon med Power BI
description: Office365Mon för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: cce886edbed00075efaa43bae9c8a712929e8b9a
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54007992"
---
# <a name="connect-to-office365mon-with-power-bi"></a>Ansluta till Office365Mon med Power BI
Det är lätt att analysera dina Office 365-avbrott och hälsoprestandadata med Power BI och Office365Mon-innehållspaketet. Power BI hämtar dina data, inklusive avbrott och hälsoavsökningar, och skapar sedan en anpassad instrumentpanel och rapporter som baseras på dessa data.

Anslut till [Office365Mon-innehållspaketet](https://app.powerbi.com/groups/me/getdata/services/office365mon) för Power BI.

>[!NOTE]
>Du måste ha ett Office365Mon-administratörskonto för att kunna ansluta och läsa in Power BI-innehållspaketet.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-office365mon/pbi_getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-office365mon/pbi_getservices.png) 
3. Välj **Office365Mon** \> **Hämta**.
   
   ![](media/service-connect-to-office365mon/o365mon.png)
4. Som Autentiseringsmetod väljer du **oAuth2** \> **Logga in**.
   
   När du uppmanas till det anger du autentiseringsuppgifterna som Office365Mon-administratör och följer autentiseringsprocessen.
   
   ![](media/service-connect-to-office365mon/creds.png)
   
   ![](media/service-connect-to-office365mon/creds2.png)
5. När Power BI har importerat dessa data, visas en ny instrumentpanel, rapport och datauppsättning i det vänstra navigeringsfönstret. Nya objekt har markerats med en gul asterisk \*, välj Office365Mon-posten.
   
   ![](media/service-connect-to-office365mon/dashboard4.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datauppsättning schemaläggs att uppdateras dagligen så kan du ändra uppdateringsfrekvensen eller testa att uppdatera den på begäran med **Uppdatera nu**

## <a name="troubleshooting"></a>Felsökning
Om du får felet **”Inloggningen misslyckades”** när du använder dina Office365Mon-autentiseringsuppgifter för prenumerationen, har inte kontot du använder behörighet att hämta Office365Mon-data från ditt konto. Kontrollera att det är ett administratörskonto och försök igen.

## <a name="next-steps"></a>Nästa steg
[Vad är Power BI?](power-bi-overview.md)

[Hämta data för Power BI](service-get-data.md)

