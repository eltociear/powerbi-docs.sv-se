---
title: Viktig information om Power BI-rapportserver
description: "Det här avsnittet beskriver begränsningar och problem med Power BI-rapportservern."
services: powerbi
documentationcenter: 
author: guyinacube
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/01/2017
ms.author: maghan
ms.openlocfilehash: aa0f8870396980edfdb85739e0459c365d1e2163
ms.sourcegitcommit: eec6b47970bf69ed30638d1a20051f961ba792f2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/06/2018
---
# <a name="power-bi-report-server-release-notes"></a>Viktig information om Power BI-rapportserver
Det här avsnittet beskriver begränsningar och problem med Power BI-rapportservern.

Om du vill ladda ned Power BI-rapportservern och Power BI Desktop som är optimerat för Power BI-rapportservern, går du till [Lokal rapportering med Power BI-rapportserver](https://powerbi.microsoft.com/report-server/).

## <a name="october-2017"></a>Oktober 2017
* Stöd för importerade data i Power BI-rapporter
* Möjligheten att visa excel-arbetsböcker i webbportalen. Detta görs genom att konfigurera Office Online-servern.
* Stöd för nya Power BI-tabell och matrisvisualiseringar.
* REST API-stöd

## <a name="june-2017"></a>Juni 2017
* Inga nya objekt för juni 2017.

## <a name="may-2017"></a>Maj 2017
* Power BI-rapporter måste skapas med Power BI Desktop optimerat för Power BI-rapportservern för att fungera med Power BI-rapportservern. Du kan hämta Power BI Desktop från länken längst upp i den här sidan.
* Power BI-rapporter har endast stöd för live-anslutningar till Analysis Services (tabell eller flerdimensionella).
* Inget stöd för visuella R-objekt.

**Problem och effekt för kunder:** om du har både SQL Server Reporting Services och Power BI-rapportserver på samma dator och avinstallerar en av dem, kommer du inte längre att kunna ansluta till den återstående rapportservern med konfigurationshanteraren för rapportservern.

**Lösning** Undvik det här problemet genom att utföra följande åtgärder när du har avinstallerat en av servrarna.

1. Starta en kommandotolk i administratörsläge.
2. Gå till katalogen där den återstående rapportservern är installerad.
   
    *Standardplats för Power BI-rapportservern: C:\Program Files\Microsoft Power BI Report Server*
   
    *Standardplats för SQL Reporting Services: C:\Program Files\Microsoft SQL Server Reporting Services*
3. Gå sedan till nästa mapp. Det här är antingen *SSRS* eller *PBIRS* beroende på vad som är kvar.
4. Gå till WMI-mappen.
5. Kör följande kommando:
   
    ```
    regsvr32 /i ReportingServicesWMIProvider.dll
    ```
   
    Du kan ignorera följande fel om du ser det.
   
    ```
    The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
    ```

## <a name="next-steps"></a>Nästa steg
[Nyheter i Power BI-rapportserver](whats-new.md)  
[Användarhandbok](user-handbook-overview.md)  
[Handbok för administratör](admin-handbook-overview.md)  
[Snabbstart: Installera Power BI-rapportserver](quickstart-install-report-server.md)  
[Installera Report Builder](https://docs.microsoft.com/sql/reporting-services/install-windows/install-report-builder)  
[Ladda ned SQL Server Data Tools (SSDT)](http://go.microsoft.com/fwlink/?LinkID=616714)

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

