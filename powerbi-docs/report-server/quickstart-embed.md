---
title: Bädda in en rapport med iFrame
description: Bädda in rapporten i Power BI Report Server i en iFrame i SharePoint Server
author: markingmyname
ms.author: maghan
ms.date: 05/04/2018
ms.topic: quickstart
ms.service: powerbi
ms.component: powerbi-report-server
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 802107ce9c12075ffc51461375ca3e9a313f2be1
ms.sourcegitcommit: 9c3a9ec14c111d766ef5703366c316e72f6e588f
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558434"
---
# <a name="quickstart-embed-a-power-bi-report-server-report-using-an-iframe-in-sharepoint-server"></a>Snabbstart: Bädda in en Power BI Report Server-rapport med iFrame i SharePoint Server

I den här snabbstarten lär du dig att bädda in en Power BI Report Server-rapport med iFrame i en SharePoint-sida. Om du arbetar med SharePoint Online, måste Power BI Report Server vara allmänt tillgänglig. I SharePoint Online fungerar inte Power BI-webbdel som fungerar med Power BI-tjänsten med Power BI Report Server. 

![iFrame-exempel](media/quickstart-embed/quickstart_embed_01.png)
## <a name="prerequisites"></a>Förutsättningar
* Du måste ha [Power BI-rapportservern](https://powerbi.microsoft.com/en-us/report-server/) installerad och konfigurerad.
* Du måste ha [Power BI Desktop som har optimerats för Power BI-rapportservern](install-powerbi-desktop.md) installerad.
* Du måste ha en [SharePoint](https://docs.microsoft.com/sharepoint/install/install)-miljö installerad och konfigurerad.

## <a name="creating-the-power-bi-report-server-report-url"></a>Skapa Power BI-rapportserverns rapport-URL

1. Hämta exemplet från GitHub – [Bloggdemo](https://github.com/Microsoft/powerbi-desktop-samples).

    ![hämta en exempel-PBIX-fil](media/quickstart-embed/quickstart_embed_14.png)

2. Öppna PBIX-exempelfilen från GitHub i **Power BI Desktop optimerad för Power BI Report Server**.

    ![PBI RS Desktop-verktyget](media/quickstart-embed/quickstart_embed_02.png)

3. Spara rapporten till **Power BI-rapportservern**. 

    ![PBI RS spara](media/quickstart-embed/quickstart_embed_03.png)

4. Visa rapporten i **webbportalen**.

    ![Webbportalen](media/quickstart-embed/quickstart_embed_04.png)

### <a name="capturing-the-url-parameter"></a>Samla in URL-parametern

När du har din URL kan du skapa en iFrame på en SharePoint-sida som värd för rapporten. För en Power BI-rapportserves rapport-URL kan du lägga till en querystring-parameter av `?rs:embed=true` för att bädda in rapporten i en iFrame. 

   Till exempel:
    ``` 
    http://myserver/reports/powerbi/Sales?rs:embed=true
    ```
## <a name="embedding-a-power-bi-report-server-report-in-a-sharepoint-iframe"></a>Bädda in en Power BI Report Server-rapport i en SharePoint iFrame

1. Navigera till en SharePoint **webbplatsinnehåll**-sida.

    ![Webbplatsinnehållssida](media/quickstart-embed/quickstart_embed_05.png)

2. Välj sidan där du vill lägga till en rapport.

    ![App för webbplatsinnehållssida](media/quickstart-embed/quickstart_embed_06.png)

3. Välj kugghjulet längst upp till höger och välj **Redigera sida**.

    ![Alternativet Redigera sida](media/quickstart-embed/quickstart_embed_07.png)

4. Välj **Lägg till webbdel**.

    ![Lägg till webbdel](media/quickstart-embed/quickstart_embed_08.png)

5. Under **Kategorier** välj **Media och innehåll**, under **Delar**, välj **Innehållsredigerare** och välj sedan **Lägg till** .

    ![Välj webbdel för innehållsredigeraren](media/quickstart-embed/quickstart_embed_09.png) ![välj Lägg till](media/quickstart-embed/quickstart_embed_091.png)

6. Välj **Klicka här för att lägga till nytt innehåll**.

    ![Lägg till nytt innehåll](media/quickstart-embed/quickstart_embed_10.png)

7. Välj i menyfliksområdet fliken **Formatera text** och välj sedan **Redigera källa**.

     ![Redigera källa](media/quickstart-embed/quickstart_embed_11.png)

8. I fönstret Redigera datakällan klistrar du in iFrame-koden och klickar på OK.

    ![iFrame-kod](media/quickstart-embed/quickstart_embed_12.png)

     Till exempel:
     ```
     <iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
     ```

9. Välj i menyfliksområdet i´fliken **Sida** och markera **Sluta redigera**.

    ![Sluta redigera](media/quickstart-embed/quickstart_embed_13.png)

10. Du bör nu se rapporten på sidan.

    ![iFrame-exempel](media/quickstart-embed/quickstart_embed_01.png)

## <a name="next-steps"></a>Nästa steg

[Snabbstart: Skapa en Power BI-rapport för Power BI-rapportservern](quickstart-create-powerbi-report.md)  
[Snabbstart: Skapa en sidnumrerad rapport för Power BI-rapportservern](quickstart-create-paginated-report.md)  

Har du fler frågor? [Fråga Power BI Community](https://community.powerbi.com/) 