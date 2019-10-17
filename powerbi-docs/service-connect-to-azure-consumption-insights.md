---
title: Ansluta till Microsoft Azure Consumption Insights med Power BI
description: Microsoft Azure Consumption Insights för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 09/25/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: e51f936e44e8c8ee3442aedfb2389675774c0a47
ms.sourcegitcommit: 5e277dae93832d10033defb2a9e85ecaa8ffb8ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72020432"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Ansluta till Microsoft Azure Consumption Insights med Power BI
Utforska och övervaka dina Microsoft Azure-förbrukningsdata i Power BI-tjänsten med Power BI-innehållspaketet. Data uppdateras automatiskt en gång per dag.

Anslut till [Microsoft Azure Consumption Insights-innehållspaketet](https://app.powerbi.com/getdata/services/azureconsumption) för Power BI-tjänsten.

> [!NOTE]
> För en mer anpassad konfiguration, kan du testa att använda [Azure Consumption Insights-anslutningsappen](desktop-connect-azure-consumption-insights.md) i Power BI Desktop.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret i Power BI-tjänsten.
   
    ![Hämta data](media/service-connect-to-azure-consumption-insights/getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![Hämta tjänster](media/service-connect-to-azure-consumption-insights/services.png)
3. Välj **Microsoft Azure Consumption Insights** \> **Hämta det nu**. 
   
   ![Hämta nu](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Ange antal månader av data som du vill importera och ditt Azure Enterprise-registreringsnummer. Se information om att [hitta parametrarna](#FindingParams) nedan.
   
    ![Ansluta till Microsoft Azure Consumption Insights](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Ange din åtkomstnyckel för att ansluta. Du hittar din registreringsnyckel i Azure EA-portalen. 
   
    ![Microsoft Azure Consumption Insights: nyckel](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Importen startar automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
   ![Microsoft Azure Consumption Insights-instrumentpanel](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* Medan din datamängd är schemalagd att uppdateras dagligen så kan du ändra uppdateringsschemat eller prova att uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
Microsofts Azure Consumption Insights-innehållspaketet innehåller månatliga rapporteringsdata för det månadsintervall som du anger när du ansluter. Intervallet är rörligt så de inkluderade datumen uppdateras när datauppsättningen uppdateras.

## <a name="system-requirements"></a>Systemkrav
Innehållspaketet kräver åtkomst till företagsfunktionerna i Azure-portalen. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Power BI-rapportering finns tillgängligt för EA-direkt, partner och indirekta kunder som kan visa faktureringsinformation. Läs mer nedan för ytterligare information om hur du hittar de värden som anslutningsflödet förväntar sig.

**Antal månader**

* Antalet månader (1–36) med data från idag som du vill importera.

**Registreringsnummer**

* Ditt Azure Enterprise-registreringsnummer som finns på startsidan för [Azure Enterprise-portalen](https://ea.azure.com/) under **Registreringsinformation**.
  
    ![Registreringsnummer](media/service-connect-to-azure-consumption-insights/params2.png)

**Åtkomstnyckel**

* Du hittar din åtkomstnyckel finns i Azure Enterprise Portal under **Ladda ned användning** > **API-åtkomstnyckel**.
  
    ![Åtkomstnyckel](media/service-connect-to-azure-consumption-insights/creds2.png)

**Ytterligare hjälp**

* Ytterligare hjälp med att konfigurera Azure Enterprise Power BI Pack får du genom att logga in på Azure Enterprise Portal och visa API-hjälpfilen under **Hjälp**. Du hittar även ytterligare instruktioner under **Rapporter** -> **Ladda ner användning** -> **API-åtkomstnyckel**.
* För en mer anpassad konfiguration, kan du testa att använda [Azure Consumption Insights-anslutningsappen](desktop-connect-azure-consumption-insights.md) i Power BI Desktop.

## <a name="next-steps"></a>Nästa steg

[Azure Consumption Insights-anslutningsprogrammet](desktop-connect-azure-consumption-insights.md) i Power BI Desktop

[Hämta data i Power BI](service-get-data.md)

