---
title: Anslut till Microsoft Azure Enterprise med Power BI
description: Microsoft Azure Enterprise för Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 7425e194bd6bda51442a128d146fb4061a77af81
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34243205"
---
# <a name="connect-to-microsoft-azure-enterprise-with-power-bi"></a>Anslut till Microsoft Azure Enterprise med Power BI
Utforska och övervaka dina Microsoft Azure Enterprise-data i Power BI med Power BI-innehållspaketet. Data uppdateras automatiskt en gång per dag.

Anslut till [Microsoft Azure Enterprise-innehållspaketet](https://app.powerbi.com/getdata/services/azure-enterprise) för Power BI.

## <a name="how-to-connect"></a>Så här ansluter du
1. Välj **Hämta data** längst ned i det vänstra navigeringsfönstret.
   
    ![](media/service-connect-to-azure-enterprise/getdata.png)
2. I rutan **tjänster** väljer du **Hämta**.
   
   ![](media/service-connect-to-azure-enterprise/services.png)
3. Välj **Microsoft Azure Enterprise** \> **hämta**.
   
   ![](media/service-connect-to-azure-enterprise/mazureenterprise.png)
4. Ange URL:en för Azure-miljön, antal månader av data som du vill importera och ditt Azure Enterprise-registreringsnummer. URL:en för din Azure-miljö är `https://ea.azure.com` eller `https://ea.windowsazure.cn`. Se information om att [hitta parametrarna](#FindingParams) nedan.
   
    ![](media/service-connect-to-azure-enterprise/params.png)
5. Ange din åtkomstnyckel för att ansluta. Nyckeln för din registrering finns i din Azure EA-portal.
   
    ![](media/service-connect-to-azure-enterprise/creds.png)
6. Importen startar automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att visa dina importerade data.
   
   ![](media/service-connect-to-azure-enterprise/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](power-bi-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning är schemalagd för att uppdateras dagligen, kan du ändra uppdateringsschemat eller försöka uppdatera den på begäran med **Uppdatera nu**.

## <a name="whats-included"></a>Vad ingår
Azure Enterprise-innehållspaketet innehåller månatliga rapporteringsdata för det antal månader som du anger under anslutningsflödet. Intervallet är rörligt så datumen som ingår uppdateras när datauppsättningen uppdateras.

## <a name="system-requirements"></a>Systemkrav
Innehållspaketet kräver åtkomst till företagsfunktionerna i Azure Portal.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Power BI-rapportering finns tillgängligt för EA-direkt, partner och indirekta kunder som kan visa faktureringsinformation. Läs nedan för mer information om hur du hittar de värden som anslutningsflödet förväntar sig.

**URL för Azure-miljön**

* Det här värdet är vanligtvis https://ea.azure.com, men du kan kontrollera URL:en när du loggar in för att bekräfta.
  
    ![](media/service-connect-to-azure-enterprise/params3.png)

**Antal månader**

* Det här bör vara ett tal mellan 1 och 36 som representerar antalet månader av data (från idag) som du vill importera.

**Registreringsnummer**

* Det här är ditt Azure Enterprise-registreringsnummer som finns på startsidan för [Azure Enterprise Portal](https://ea.azure.com/) under registreringsinformation.
  
    ![](media/service-connect-to-azure-enterprise/params2.png)

**Åtkomstnyckel**

* Din nyckel finns i Azure Enterprise Portal under ”Ladda ned användningsdata” > ”API-åtkomstnyckel”.
  
    ![](media/service-connect-to-azure-enterprise/creds2.png)

**Ytterligare hjälp**

* För ytterligare hjälp med hur du konfigurerar Azure Enterprise Power BI-paketet, loggar du in i Azure Enterprise Portal och visar API-hjälpfilen under ”Hjälp” och ytterligare instruktioner under Rapporter -> Ladda ned användningsdata > API-åtkomstnyckel.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

