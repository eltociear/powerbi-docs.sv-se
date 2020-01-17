---
title: Publicera en sidnumrerad rapport i Power BI-tjänsten
description: I den här självstudien får du lära dig att publicera en sidnumrerad rapport i Power BI-tjänsten genom att överföra den från din lokala dator.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/03/2020
ms.openlocfilehash: 5f77e17eccf4c99e7a391ea310a34848c604e01d
ms.sourcegitcommit: b68a47b1854588a319a5a2d5d6a79bba2da3a4e6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75732094"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service"></a>Publicera en sidnumrerad rapport i Power BI-tjänsten

I den här artikeln får du lära dig om att publicera en sidnumrerad rapport i Power BI-tjänsten genom att överföra den från din lokala dator. Du kan överföra sidnumrerade rapporter till Min arbetsyta eller en annan arbetsyta, så länge arbetsytan finns i en Premium-kapacitet. Leta efter diamantikonen ![Diamantikon för Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) bredvid arbetsytans namn. 

Om rapportdatakällan finns lokalt måste du skapa en gateway när du har laddat upp rapporten. Läs mer i avsnittet [Skapa en gateway](#create-a-gateway) längre fram i artikeln.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Lägg till en arbetsyta till en Premium-kapacitet

Om arbetsytan inte har diamantikonen ![Diamantikon för Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) bredvid namnet, behöver du lägga till arbetsytan till en Premium-kapacitet. 

1. Välj **Arbetsytor**, välj ellipsen ( **...** ) bredvid arbetsytans namn och välj sedan **Redigera arbetsyta**.

    ![Välj Redigera arbetsyta](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. I dialogrutan **Redigera arbetsyta** expanderar du **Avancerat** och drar sedan **Dedikerad kapacitet** till **På**.

    ![Välj dedikerad kapacitet](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Du kanske inte kan ändra den. Om inte kan du kontakta administratören för Power BI Premium-kapaciteten för att ge dig tilldelningsbehörighet att lägga till din arbetsyta till en Premium-kapacitet.

## <a name="from-report-builder-publish-a-paginated-report"></a>Publicera en sidnumrerad rapport från Report Builder

1. Skapa din sidnumrerade rapport i Report Builder och spara den till din lokala dator.

1. Öppna menyn **Arkiv** i Report Builder och välj **Spara som**.

    ![Menyn Arkiv > Spara > Spara som](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    Om du inte är inloggad i Power BI än måste du logga in eller skapa ett konto nu. Välj **Logga in** uppe till höger i Report Builder och slutför stegen.

2. I listan över arbetsytor till vänster väljer du en arbetsyta med diamantikonen ![diamantikon för Power BI Premium-kapacitet](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) bredvid namnet. Ange ett **filnamn** i rutan > **Spara**. 

    ![Välj en Premium-arbetsyta](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Öppna Power BI-tjänsten i en webbläsare och gå till Premium-arbetsytan där du publicerade den sidnumrerade rapporten. Rapporten visas på fliken **Rapporter**.

    ![Sidnumrerad rapport i rapportlistan](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Välj den sidnumrerade rapporten så att den öppnas i Power BI-tjänsten. Om den har parametrar, måste du välja dem innan du kan visa rapporten.

    ![Välj parametrar](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Om rapportens datakälla finns lokalt läser du om att [skapa en gateway](#create-a-gateway) i den här artikeln så att du kommer åt datakällan.

## <a name="from-the-power-bi-service-upload-a-paginated-report"></a>Ladda upp en sidnumrerad rapport från Power BI-tjänsten

Du kan också börja från Power BI-tjänsten och ladda upp en sidnumrerad rapport.

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

   Rapporten visas på fliken **Rapporter**.

    ![Sidnumrerad rapport i rapportlistan](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Välj den för att öppna den i Power BI-tjänsten. Om den har parametrar, måste du välja dem innan du kan visa rapporten.
 
    ![Välj parametrar](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. Om rapportens datakälla finns lokalt läser du om att [skapa en gateway](#create-a-gateway) i den här artikeln så att du kommer åt datakällan.

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
- [Självstudie: Bädda in sidnumrerade Power BI-rapporter i en app för dina kunder](developer/embed-paginated-reports-customers.md)

