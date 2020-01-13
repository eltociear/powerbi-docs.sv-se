---
title: Bädda in en Power BI-rapportserverrapport med en iFrame i SharePoint Server
description: Den här artikeln visar hur du bäddar in en Power BI-rapportserverraport i en iFrame i SharePoint Server
author: maggiesMSFT
ms.author: maggies
ms.date: 08/12/2019
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.openlocfilehash: fe91de89e7eec601c516895089e3dcc03eff14ea
ms.sourcegitcommit: 6272c4a0f267708ca7d38a45774f3bedd680f2d6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2020
ms.locfileid: "75657223"
---
# <a name="embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Bädda in en Power BI-rapportserverrapport med en iFrame i SharePoint Server

I den här artikeln lär du dig att bädda in en Power BI-rapportserverrapport med hjälp av en iFrame på en SharePoint-sida. Om du arbetar med SharePoint Online måste Power BI-rapportserver vara allmänt tillgänglig. I SharePoint Online fungerar inte den Power BI-webbdel som fungerar med Power BI-tjänsten med Power BI-rapportserver.  

![iFrame-exempel](media/quickstart-embed/quickstart_embed_01.png)

## <a name="prerequisites"></a>Förutsättningar
* [Power BI-rapportserver](https://powerbi.microsoft.com/report-server/) ska vara installerad och konfigurerad.
* [Power BI Desktop som har optimerats för Power BI-rapportservern](install-powerbi-desktop.md) ska vara installerat.
* En [SharePoint](https://docs.microsoft.com/sharepoint/install/install)-miljö ska installerad och konfigurerad.
* Internet Explorer 11 stöds endast vid användning av SharePoint Online.  Du kan använda andra webbläsare som stöds i ettdera scenariot.

## <a name="create-the-power-bi-report-url"></a>Skapa Power BI-rapport-URL:en

1. Ladda ned exemplet från GitHub: [Bloggdemo](https://github.com/Microsoft/powerbi-desktop-samples). Välj **Klona eller ladda ned** och sedan **Ladda ned ZIP**.

    ![Ladda ned PBIX-exempelfil](media/quickstart-embed/quickstart_embed_14.png)

2. Packa upp filen och öppna .pbix-exempelfilen i Power BI Desktop som optimerats för Power BI-rapportserver.

    ![PBI RS Desktop-verktyget](media/quickstart-embed/quickstart_embed_02.png)

3. Spara rapporten till **Power BI-rapportservern**. 

    ![PBI RS spara](media/quickstart-embed/quickstart_embed_03.png)

4. Visa rapporten i webbportalen för Power BI-rapportserver.

    ![Webbportalen](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capture-the-url-parameter"></a>Samla in URL-parametern

När du har URL:en kan du skapa en iFrame på en SharePoint-sida för att värdhantera rapporten. För Power BI-rapportserverrapportens URL lägger du till följande frågesträngsparameter för att bädda in rapporten i en SharePoint-iFrame: `?rs:embed=true`.

   Till exempel:
    ``` 
    https://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embed-the-report-in-a-sharepoint-iframe"></a>Bädda in rapporten i en SharePoint-iFrame

1. Navigera till en SharePoint **webbplatsinnehåll**-sida.

    ![Sida med webbplatsinnehåll](media/quickstart-embed/quickstart_embed_05.png)

2. Välj sidan där du vill lägga till en rapport.

    ![Sidapp med webbplatsinnehåll](media/quickstart-embed/quickstart_embed_06.png)

3. Välj kugghjulsikonen längst upp till höger och välj sedan **Redigera sida**.

    ![Alternativet Redigera sida](media/quickstart-embed/quickstart_embed_07.png)

4. Välj **Lägg till en webbdel**.

5. Under **Kategorier** väljer du **Media och innehåll**. Under **Delar** väljer du **Innehållsredigerare** och sedan **Lägg till**.

    ![Välja webbdel för innehållsredigeraren](media/quickstart-embed/quickstart_embed_09.png)

6. Välj **Klicka här för att lägga till nytt innehåll**.

7. I menyn längst upp väljer du **Formatera text** och sedan **Redigera källa**.

     ![Redigera källa](media/quickstart-embed/quickstart_embed_11.png)

8. I fönstret **Redigera källa** klistrar du in iFrame-koden i **HTML-källa** och väljer **OK**.

    ![iFrame-kod](media/quickstart-embed/quickstart_embed_12.png)

     Till exempel:
     ```html
     <iframe width="800" height="600" src="https://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. I menyn längst upp väljer du **Sida** och sedan **Sluta redigera**.

    ![Sluta redigera](media/quickstart-embed/quickstart_embed_13.png)

    Rapporten visas på sidan.

    ![iFrame-exempel](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Nästa steg

- [Skapa en Power BI-rapport för Power BI-rapportserver](quickstart-create-powerbi-report.md).  
- [Skapa en sidnumrerad rapport för Power BI-rapportserver](quickstart-create-paginated-report.md).  

Har du fler frågor? [Testa Power BI Community](https://community.powerbi.com/). 
