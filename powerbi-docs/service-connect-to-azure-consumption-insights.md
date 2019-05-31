---
title: Ansluta till Microsoft Azure Consumption Insights med Power BI
description: Microsoft Azure Consumption Insights för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222129"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Ansluta till Microsoft Azure Consumption Insights med Power BI
Utforska och övervaka dina Microsoft Azure-förbrukningsdata i Power BI med Power BI-innehållspaketet. Data uppdateras automatiskt en gång om dagen.

Anslut till [Microsoft Azure Consumption Insights-innehållspaketet](https://app.powerbi.com/getdata/services/azureconsumption) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Välj **Microsoft Azure Consumption Insights** \> **Hämta nu**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Ange antal månader av data som du vill importera och ditt Azure Enterprise-registreringsnummer. Se information om att [hitta parametrarna](#FindingParams) nedan.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Ange din åtkomstnyckel för att ansluta. Du hittar din nyckel för registrering i Azure EA-portalen. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Importen startar automatiskt. När du är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](consumer/end-user-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](consumer/end-user-tiles.md) för att öppna den underliggande rapporten.
* När din datauppsättning är schemalagd att uppdateras varje dag, du kan ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Det här ingår
Microsoft Azure Consumption Insights-Innehållspaketet innehåller månatliga rapporteringsdata för det intervallet för månad som du angav när du ansluter. Intervallet är rörligt så datumen som ingår uppdateras när datauppsättningen uppdateras.

## <a name="system-requirements"></a>Systemkrav
Innehållspaketet kräver åtkomst till företagsfunktioner i Azure-portalen. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Power BI-rapportering är tillgängligt för direkta EA-Partner och indirekta kunder som kan visa faktureringsinformation. Läs nedan för information om hur du hittar de värden som anslutningsflödet förväntar sig.

**Antal månader**

* Antalet månader (1 – 36) av data från i dag som du vill importera.

**Registreringsnummer**

* Ditt Azure Enterprise-registreringsnummer som du hittar vid den [Azure Enterprise Portal](https://ea.azure.com/) startsidan under **registreringsuppgifter**.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Åtkomstnyckel**

* Du kan hitta din åtkomstnyckel i Azure Enterprise-portalen under **ladda ned användning** > **API-åtkomstnyckel**.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Ytterligare hjälp**

* För ytterligare hjälp med att konfigurera Azure Enterprise Power BI-paketet, logga in på Azure Enterprise Portal och visa API-hjälpfilen under **hjälpa**. Du kan också hitta ytterligare instruktioner under **rapporter** -> **ladda ned användning** -> **API-åtkomstnyckel**.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

