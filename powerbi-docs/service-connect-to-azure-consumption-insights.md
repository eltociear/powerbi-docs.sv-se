---
title: Ansluta till Microsoft Azure Consumption Insights med Power BI
description: Microsoft Azure Consumption Insights för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 31f1d4161801b45307e92ad3f654d30843897dc8
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2018
ms.locfileid: "34244167"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Ansluta till Microsoft Azure Consumption Insights med Power BI
Utforska och övervaka dina Microsoft Azure-förbrukningsdata i Power BI med Power BI-innehållspaketet. Data uppdateras automatiskt en gång per dag.

Anslut till [Microsoft Azure Consumption Insights-innehållspaketet](https://app.powerbi.com/getdata/services/azureconsumption) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. I rutan **Tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Välj **Microsoft Azure Consumption Insights** \> **Hämta**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Ange antal månader av data som du vill importera och ditt Azure Enterprise-registreringsnummer. Se information om att [hitta parametrarna](#FindingParams) nedan.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Ange din åtkomstnyckel för att ansluta. Nyckeln för din registrering finns i din Azure EA-portal. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. Importen startar automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="whats-included"></a>Det här ingår
Microsofts Azure Consumption Insights-innehållspaketet innehåller månatliga rapporteringsdata för det intervall av månader som du anger under anslutningsflödet. Intervallet är rörligt så datumen som ingår uppdateras när datauppsättningen uppdateras.

## <a name="system-requirements"></a>Systemkrav
Innehållspaketet kräver åtkomst till företagsfunktionerna i Azure Portal. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Power BI-rapportering finns tillgängligt för EA-direkt, partner och indirekta kunder som kan visa faktureringsinformation. Läs mer nedan för ytterligare information om hur du hittar de värden som anslutningsflödet förväntar sig.

**Antal månader**

* Det här bör vara ett tal mellan 1 och 36 som representerar antalet månader av data (från idag) som du vill importera.

**Registreringsnummer**

* Det här är ditt Azure Enterprise-registreringsnummer som finns på startsidan för [Azure Enterprise Portal](https://ea.azure.com/) under registreringsinformation.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Åtkomstnyckel**

* Din nyckel finns i Azure Enterprise Portal under ”Ladda ned användningsdata” > ”API-åtkomstnyckel”.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Ytterligare hjälp**

* För ytterligare hjälp med hur du konfigurerar Azure Enterprise Power BI-paketet, loggar du in i Azure Enterprise Portal och visar API-hjälpfilen under ”Hjälp” och ytterligare instruktioner under Rapporter -> Ladda ned användningsdata > API-åtkomstnyckel. 

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

