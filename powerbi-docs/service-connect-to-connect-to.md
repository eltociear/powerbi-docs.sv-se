---
title: Anslut till comScore Digital Analytix med Power BI
description: comScore Digital Analytix för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: bc9a8637416bdea50e955c1aea73bbcfeed51bb6
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="connect-to-comscore-digital-analytix-with-power-bi"></a>Anslut till comScore Digital Analytix med Power BI
Visualisera och utforska dina comScore Digital Analytix-data i Power BI med Power BI-innehållspaketet. Data uppdateras automatiskt en gång per dag.

Anslut till [comScore-innehållspaketet för Power BI.](https://app.powerbi.com/getdata/services/comscore)

>[!NOTE]
>För att ansluta till innehållspaketet behöver du ett comScore DAx-användarkonto och ha comScore API-åtkomst. Mer [information](#Requirements) nedan.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj Hämta data längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-connect-to/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-connect-to/services.png)
3. Välj **comScore Digital Analytix** \> **hämta**.
   
   ![](media/service-connect-to-connect-to/comscore.png)
4. Ange datacenter, comScore klient-ID och plats som du vill ansluta till. Mer information om hur du hittar de här värdena finns i [hitta dina comScore-parametrar](#FindingParams) nedan.
   
   ![](media/service-connect-to-connect-to/parameters.png)
5. Ange ditt användarnamn och lösenord för comScore för att fortsätta. Mer information om hur du hittar det här värdet finns nedan.
   
   ![](media/service-connect-to-connect-to/creds.png)
6. Importen startar automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

<a name="Requirements"></a>

## <a name="system-requirements"></a>Systemkrav
Ett comScore DAx-användarkonto och åtkomst till comScore DAx API krävs för att ansluta. Kontakta din comScore DAX-administratör för att bekräfta ditt konto.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Information om hur du hittar var och en av comScore-parametrarna finns nedan.

**Datacenter**

Datacentret som du ansluter till fastställs av den URL som du navigerar till i comScore.

Om du använder https://dax.comscore.com anger du ”US”, om du använder https://dax.comscore.eu anger du ”EU”.

![](media/service-connect-to-connect-to/comscore_url.png) 

**Klient**

Klienten är samma som du anger när du loggar in på comScore DAx.

![](media/service-connect-to-connect-to/comscore_signin.png) 

**Plats**

ComScore-platsen anger vilken plats som du vill se data från. Du hittar listan över platser från ditt comScore-konto.

![](media/service-connect-to-connect-to/comscore_sites.png)

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

