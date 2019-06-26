---
title: Inbäddade datakällor för sidnumrerade rapporter i Power BI-tjänsten
description: I den här artikeln får du lära dig att skapa och ändra en inbäddad datakälla i en sidnumrerad rapport i Power BI-tjänsten.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 06/06/2019
ms.openlocfilehash: 7b687fd67f844e000811ae00a53772ab9403ab90
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "66838945"
---
# <a name="create-an-embedded-data-source-for-paginated-reports-in-the-power-bi-service"></a>Skapa en inbäddad datakälla för sidnumrerade rapporter i Power BI-tjänsten

I den här artikeln får du lära dig att skapa och ändra en inbäddad datakälla för en sidnumrerad rapport i Power BI-tjänsten. Du definierar en inbäddad datakälla i en enda rapport och använder den endast i den rapporten. För närvarande måste sidnumrerade rapporter som publiceras till Power BI-tjänsten innehålla inbäddade datamängder och inbäddade datakällor. De kan anslutas till följande datakällor:

- Azure SQL Database och Data Warehouse
- SQL Server
- SQL Server Analysis Services
- Oracle 
- Teradata 

För följande datakällor ska du använda alternativet [SQL Server Analysis Services-anslutning](service-premium-connect-tools.md):

- Azure Analysis Services
- Power BI Premium datasets

Sidnumrerade rapporter ansluter till lokala datakällor via en [Power BI-gateway](service-gateway-getting-started.md). Du ställer in gatewayen när du har publicerat rapporten till Power BI-tjänsten.

Mer information finns i [Rapportdata i Power BI Report Builder](report-builder-data.md).

## <a name="create-an-embedded-data-source"></a>Skapa en inbäddad datakälla
  
1. Öppna Power BI Report Builder.

1. I verktygsfältet i fönstret Rapportdata väljer du **Nytt** > **Datakälla**. Dialogrutan **Egenskaper för datakälla** öppnas.

    ![Ny datakälla](media/paginated-reports-embedded-data-source/power-bi-paginated-new-data-source.png)
  
2.  I textrutan **Namn** skriver du ett namn på datakällan, eller så godkänner du standardinställningen.  
  
3.  Välj **Använd en anslutning som är inbäddad i min rapport**.  
  
1.  I listan **Välj anslutningstyp** väljer du en typ av datakälla. 

1.  Ange en anslutningssträng med hjälp av någon av följande metoder:  
  
    -   Skriv anslutningssträngen direkt i textrutan **Anslutningssträng**. 
  
    -   Välj uttrycksknappen (**fx)** för att skapa ett uttryck som blir en anslutningssträng. I dialogrutan **Uttryck** skriver du uttrycket i rutan Uttryck. Välj **OK**. 
  
    -   Välj **Skapa** för att öppna dialogrutan **Anslutningsegenskaper** för den datakälla som du valde i steg 2.  
  
        Fyll i lämpliga fält i dialogrutan **Anslutningsegenskaper** för typen av datakälla. Anslutningsegenskaper är bl.a. typ av datakälla, namnet på datakällan och de autentiseringsuppgifter som används. När du har angett värden i dialogrutan väljer du **Testa anslutningen** för att kontrollera att datakällan är tillgänglig och att de autentiseringsuppgifter som du angav är korrekta.  
  
4.  Välj **Autentiseringsuppgifter**.  
  
     Ange de autentiseringsuppgifter som ska användas för den här datakällan. Ägaren av datakällan väljer vilken typ av autentiseringsuppgifter som stöds. Mer information finns i [Ange autentiseringsuppgifter och anslutningsinformation för Rapport över datakällor](https://docs.microsoft.com/sql/reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources).
  
5.  Välj **OK**.  
  
     Datakällan visas i fönstret Rapportdata.  

## <a name="next-steps"></a>Nästa steg

- [Skapa en inbäddad datamängd för en sidnumrerad rapport i Power BI-tjänsten](paginated-reports-create-embedded-dataset.md)
- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)
