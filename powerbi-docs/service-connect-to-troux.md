---
title: Ansluta till Troux med Power BI
description: Troux för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: dbf3831264a354ec96a38751dfa7a3719c5c9f2a
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34247951"
---
# <a name="connect-to-troux-for-power-bi"></a>Ansluta till Troux för Power BI
Med Troux-innehållspaketet kan du visualisera dina företagsarkitekturscentrallager på ett helt nytt sätt direkt i Power BI. Innehållspaketet ger dig flera insikter om dina företagsfunktioner, de program som innehåller dessa funktioner och de tekniker som stöder program som kan anpassas helt med hjälp av Power BI.

Anslut till [Troux-innehållspaketet](https://app.powerbi.com/getdata/services/troux) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
   ![](media/service-connect-to-troux/getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-troux/services.png)
3. Välj **Troux** \>  **Hämta**.
   
   ![](media/service-connect-to-troux/troux.png)
4. Ange din Troux OData-URL. Se information om att [söka efter de här parametrarna](#FindingParams) nedan.
   
   ![](media/service-connect-to-troux/params.png)
5. Som **Autentiseringsmetod** väljer du **Grundläggande** och anger sedan ditt användarnamn och lösenord (skiftlägeskänsliga). Välj sedan **Logga in**.
   
    ![](media/service-connect-to-troux/creds.png)
6. Efter att du har godkänt startar importen automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
     ![](media/service-connect-to-troux/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="system-requirements"></a>Systemkrav
Åtkomst till Troux OData-flödet och Troux 9.5.1 eller högre krävs.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Kundvårdsteamet kan ge dig din unika URL för Troux-OData-flödet

## <a name="troubleshooting"></a>Felsökning
Om du får ett tidsgränsfel när du har angett autentiseringsuppgifterna kan du försöka ansluta igen.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

