---
title: Publicera en sidnumrerad rapport i Power BI-tjänsten
description: I den här självstudien får du lära dig att publicera en sidnumrerad rapport i Power BI-tjänsten genom att överföra den från din lokala dator.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 12/03/2019
ms.openlocfilehash: a7f0e6f08f25d47cd50789a3c8f296ae20c4cab0
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831205"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Publicera en sidnumrerad rapport i Power BI-tjänsten

I den här artikeln får du lära dig om att publicera en sidnumrerad rapport i Power BI-tjänsten genom att överföra den från din lokala dator. Du kan överföra sidnumrerade rapporter till Min arbetsyta eller en annan arbetsyta, så länge arbetsytan finns i en Premium-kapacitet. Leta efter diamantikonen ![Diamantikon för Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) bredvid arbetsytans namn. 

Om rapportdatakällan finns lokalt, måste du [skapa en gateway](#create-a-gateway) när du har överfört rapporten.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Lägg till en arbetsyta till en Premium-kapacitet

Om arbetsytan inte har diamantikonen ![Diamantikon för Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) bredvid namnet, behöver du lägga till arbetsytan till en Premium-kapacitet. 

1. Välj **Arbetsytor**, välj ellipsen ( **...** ) bredvid arbetsytans namn och välj sedan **Redigera arbetsyta**.

    ![Välj Redigera arbetsyta](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. I dialogrutan **Redigera arbetsyta** expanderar du **Avancerat** och drar sedan **Dedikerad kapacitet** till **På**.

    ![Välj dedikerad kapacitet](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Du kanske inte kan ändra den. Om inte kan du kontakta administratören för Power BI Premium-kapaciteten för att ge dig tilldelningsbehörighet att lägga till din arbetsyta till en Premium-kapacitet.


## <a name="upload-a-paginated-report"></a>Ladda upp en sidnumrerad rapport

1. Skapa din sidnumrerade rapport i Report Builder och spara den till din lokala dator.

1. Öppna Power BI-tjänsten i en webbläsare och gå till Premium-arbetsytan där du vill publicera rapporten. Observera diamantikonen ![Diamantikon för Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) bredvid namnet. 

1. Välj **Hämta data**.

    ![Hämta Data i Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. I rutan **Filer** väljer du **Hämta**.

    ![Hämta filer i Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Välj **Lokal fil** > gå till den sidnumrerade rapporten > **Öppna**.

    ![Välj lokal fil](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Välj **Fortsätt** > **Redigera autentiseringsuppgifter**.

    ![Välj Redigera autentiseringsuppgifter](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Konfigurera dina inloggningsuppgifter > **Logga in**.

    ![Redigera autentiseringsuppgifter](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Du kan se rapporten i listan över rapporter.

    ![Sidnumrerad rapport i rapportlistan](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Välj den för att öppna den i Power BI-tjänsten. Om den har parametrar, måste du välja dem innan du kan visa rapporten.
 
    ![Välj parametrar](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>Skapa en gateway

Precis som alla andra Power BI-rapporter, om rapportdatakällan finns på plats, måste du skapa eller ansluta till en gateway för att komma åt data.

1. Bredvid rapportnamnet, väljer du **Hantera**.

   ![Hantera den sidnumrerade rapporten](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Information och följande steg finns i Power BI-tjänstartikeln [Vad är en lokal datagateway?](service-gateway-onprem.md).

### <a name="gateway-limitations"></a>Gateway-begränsningar

För närvarande stöder inte gatewayer flervärdesparametrar.


## <a name="next-steps"></a>Nästa steg

- [Visa en sidnumrerad rapport i Power BI-tjänsten](consumer/paginated-reports-view-power-bi-service.md)
- [Vad är sidnumrerade rapporter i Power BI Premium?](paginated-reports-report-builder-power-bi.md)

