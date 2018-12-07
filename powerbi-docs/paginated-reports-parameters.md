---
title: Skapa parametrar för sidnumrerade rapporter i Power BI-tjänsten (förhandsversion)
description: I den här artikeln lär du dig att skapa parametrar för sidnumrerade rapporter i Power BI-tjänsten.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: d36f8e26282ae794976b0d679feb426ea04a981b
ms.sourcegitcommit: b03912343a5a214c6bb972aaa6aa051c2a5f4332
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2018
ms.locfileid: "52900300"
---
# <a name="create-parameters-for-paginated-reports-in-the-power-bi-service-preview"></a>Skapa parametrar för sidnumrerade rapporter i Power BI-tjänsten (förhandsversion)

I den här artikeln lär du dig att skapa parametrar för sidnumrerade rapporter i Power BI-tjänsten.  En rapportparameter är ett sätt att välja rapportdata och variera rapportpresentationen på. Du kan ange ett standardvärde och en lista med tillgängliga värden, och dina rapportläsare kan ändra valet.  

Följande bild visar designvyn i Report Builder för en rapport med parametrarna @BuyingGroup, @Customer, @FromDate och @ToDate. 
  
![Parametrar i Report Builder](media/paginated-reports-parameters/power-bi-paginated-parameters-report-builder.png)
  
1.  Rapportparametrarna i fönstret Rapportdata.  
  
2.  Tabell med en av parametrarna i datamängden.  
  
3.  Fönstret Parametrar. Du kan anpassa layouten för parametrarna i parameterfönstret. 
  
4.  Parametrarna @FromDate och @ToDate har datatypen **DateTime**. När du visar rapporten kan du antingen ange ett datum i textrutan eller välja ett datum i kalendern. 

5.  En av parametrarna i dialogrutan **Egenskaper för datamängd**.  

  
## <a name="create-or-edit-a-report-parameter"></a>Skapa eller redigera en rapportparameter  
  
1.  Öppna din sidnumrerade rapport i Report Builder.

1. I fönstret **Rapportdata** högerklickar du på noden **Parametrar** > **Lägg till parameter**. Dialogrutan **Egenskaper för rapportparameter** öppnas.  
  
2.  I **Namn** skriver du ett namn på parametern eller så godkänner du standardnamnet.  
  
3.  I **Fråga** skriver du den text som ska visas bredvid textrutan för parametern när användaren kör rapporten.  
  
4.  I **Datatyp** väljer du datatypen för parametervärdet.  
  
5.  Om parametern kan innehålla ett tomt värde, väljer du **Tillåt tomt värde**.  
  
6.  Om parametern kan innehålla ett null-värde, väljer du **Tillåt null-värde**.  
  
7.  Om du vill tillåta att en användare kan välja mer än ett värde för parametern, väljer du **Tillåt flera värden**.  
  
8.  Ange synlighetsalternativet.  
  
    -   Om du vill att visa parametern i verktygsfältet högst upp i rapporten, väljer du **Synlig**.  
  
    -   Om du vill dölja parametern så att den inte visas i verktygsfältet, väljer du **Dold**.  
  
    -   Om du vill dölja parametern och hindra att den ändras på rapportservern när rapporten har publicerats, väljer du **Internt**. Rapportparametern visas därefter bara i rapportdefinitionen. För det här alternativet måste du ange ett standardvärde, eller tillåta att parametern accepterar ett null-värde.  
  
9. Välj **OK**. 
  
## <a name="next-steps"></a>Nästa steg

Se [Visa parametrar för sidnumrerade rapporter](paginated-reports-view-parameters.md) för att se hur parametrarna ser ut i Power BI-tjänsten.

Detaljerad information om parametrar i sidnumrerade rapporter finns i artikeln [Rapportparametrar (Report Builder och Rapportdesignern)](https://docs.microsoft.com/sql/reporting-services/report-design/report-parameters-report-builder-and-report-designer) i SQL Server Reporting Services-dokumentationen  
