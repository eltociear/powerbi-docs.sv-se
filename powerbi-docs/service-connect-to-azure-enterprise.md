---
title: Anslut till Microsoft Azure Enterprise med Power BI
description: "Microsoft Azure Enterprise för Power BI"
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
ms.openlocfilehash: 39c3fd776e3aed821c7c10c1e905d7400ca64efd
ms.sourcegitcommit: 284b09d579d601e754a05fba2a4025723724f8eb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2017
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
5. Ange din åtkomstnyckel för att ansluta. Nyckeln för din registrering finns din Azure EA-portal.
   
    ![](media/service-connect-to-azure-enterprise/creds.png)
6. Importen startar automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i navigeringsfönstret. Välj instrumentpanelen för att se dina importerade data.
   
   ![](media/service-connect-to-azure-enterprise/dashboard.png)

**Och sedan?**

* Prova att [ställa en fråga i rutan Frågor och svar](service-q-and-a.md) överst på instrumentpanelen
* [Ändra panelerna](service-dashboard-edit-tile.md) på instrumentpanelen.
* [Välj en panel](service-dashboard-tiles.md) för att öppna den underliggande rapporten.
* Även om din datauppsättning kommer att vara schemalagd att uppdateras dagligen, kan du ändra uppdateringsschemat eller uppdatera på begäran med **Uppdatera nu**

## <a name="whats-included"></a>Vad ingår
Azure Enterprise-innehållspaketet innehåller månatliga rapporteringsdata för det antal månader som du anger under anslutningsflödet. Intervallet är rörligt så datumen som ingår uppdateras när datauppsättningen uppdateras.

## <a name="system-requirements"></a>Systemkrav
Innehållspaketet kräver åtkomst till företagsfunktioner i Azure-portalen.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Hitta parametrar
Power BI-rapportering finns tillgängligt för EA-direkt, partner och indirekta kunder som kan se faktureringsinformation. Läs nedan för mer information om hur du hittar de värden som anslutningsflödet förväntar sig.

**URL för Azure-miljön**

* Det här värdet är vanligtvis https://ea.azure.com, men du kan kontrollera URL:en när du loggar in för att bekräfta.
  
    ![](media/service-connect-to-azure-enterprise/params3.png)

**Antal månader**

* Det här bör vara ett tal mellan 1-36 som representerar antalet månader av data (från idag) som du vill importera.

**Registreringsnummer**

* Det här är ditt Azure Enterprise-registreringsnummer som finns på startsidan för [Azure Enterprise Portal](https://ea.azure.com/) under registreringsinformation.
  
    ![](media/service-connect-to-azure-enterprise/params2.png)

**Åtkomstnyckel**

* Din nyckel finns i Azure Enterprise-portalen under ladda ned användning > API-åtkomstnyckel
  
    ![](media/service-connect-to-azure-enterprise/creds2.png)

**Ytterligare hjälp**

* För ytterligare hjälp med hur du konfigurerar Azure Enterprise Power BI-paketet, loggar du in på Azure Enterprise Portal och visar API-hjälpfilen under hjälp och ytterligare instruktioner under rapporter -> nedladdningsanvändning > API-åtkomstnyckel.

## <a name="next-steps"></a>Nästa steg
[Kom igång i Power BI](service-get-started.md)

[Hämta data i Power BI](service-get-data.md)

