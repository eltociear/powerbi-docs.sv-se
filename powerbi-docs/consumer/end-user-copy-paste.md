---
title: Kopiera och klistra in en visualisering i Power BI-tjänsten
description: Kopiera och klistra in en visualisering i Power BI-tjänsten
author: mihart
ms.reviewer: maggie.tsang
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 08/25/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 6e1850e281c58bd89597af2bbd9ade0a769071ae
ms.sourcegitcommit: 1aaa742c239a3119cdaad698be5a7553b68801fa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/27/2020
ms.locfileid: "89040257"
---
# <a name="copy-a-visual-as-an-image-to-your-clipboard"></a>Kopiera ett visuellt objekt som en bild till Urklipp

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]

Har det hänt att du velat dela en bild från en Power BI-rapport eller en instrumentpanel? Nu kan du kopiera det visuella objektet och klistra in det i andra program som har stöd för inklistring. 

När du kopierar en statisk bild av ett visuellt objekt får du en kopia av det visuella objektet samt metadata. Det här omfattar:
* länk tillbaka till Power BI-rapporten eller instrumentpanelen
* rubrik för rapporten eller instrumentpanelen
* meddelande om bilden innehåller konfidentiell information
* tidstämpel för senaste uppdatering
* filter som tillämpas på det visuella objektet

### <a name="copy-from-a-dashboard-tile"></a>Kopia från en instrumentpanelsruta

1. Gå till den instrumentpanel som du vill kopiera från.

2. I det övre högra hörnet av det visuella objektet väljer du **Fler alternativ (...)** och sedan **Kopiera visuellt objekt som bild**. 

    ![Alternativet Kopiera visuellt objekt som bild visas i listrutemenyn](media/end-user-copy-paste/power-bi-copy-dashboard.png)

3. När dialogrutan **Ditt visuella objekt är redo att kopieras** visas väljer du **Kopiera till Urklipp**.

    ![dialogruta med alternativet Kopiera till Urklipp](media//end-user-copy-paste/power-bi-copied.png)

4. När det visuella objektet har kopierats, klistrar du in det i ett annat program genom att trycka på **Ctrl+V** eller **högerklicka på** > **Klistra in**. I skärmbilden nedan har vi klistrat in det visuella objektet i Microsoft Word. 

    ![visuellt objekt som har klistrats in i Microsoft Word](media//end-user-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Kopiera från ett visuellt rapportobjekt 

1. Gå till den rapport som du vill kopiera från.

2. I det övre högra hörnet av det visuella objektet väljer du ikonen för **Kopiera visuellt objekt som bild**. 

    ![Ikonen Kopiera visuellt objekt visas](media/end-user-copy-paste/power-bi-copy-icon.png)

3. När dialogrutan **Ditt visuella objekt är redo att kopieras** visas väljer du **Kopiera till Urklipp**.

    ![dialogruta med alternativet Kopiera till Urklipp](media//end-user-copy-paste/power-bi-copied.png)


4. När det visuella objektet har kopierats, klistrar du in det i ett annat program genom att trycka på **Ctrl+V** eller **högerklicka på** > **Klistra in**. I skärmbilden nedan har vi klistrat in det visuella objektet i ett e-postmeddelande.

    ![visuellt objekt inklistrat i Outlook](media//end-user-copy-paste/power-bi-copy-email.png)

5. Om det finns en datakänslighetsetikett tillämpad på rapporten visas en varning när du väljer kopieringsikonen.  

    ![varning om känsliga data](media//end-user-copy-paste/power-bi-sensitive.png)

    Dessutom läggs en känslighetsetikett till i metadata nedanför det inklistrade visuella objektet. 

    ![visuellt objekt med etikett för konfidentiell information](media//end-user-copy-paste/power-bi-confidential.png)



## <a name="considerations-and-troubleshooting"></a>Överväganden och felsökning

   ![kopiering ej tillgänglig](media//end-user-copy-paste/power-bi-copy-grey.png)


F: Varför är kopieringsikonen inaktiverad i ett visuellt objekt?    
S: Vi stöder för tillfället inbyggda visuella Power BI-objekt och certifierade visuella objekt. Det finns begränsat stöd för vissa visuella objekt, inklusive: 
- ESRI och andra kartvisualiseringar 
- Visuella Python-objekt 
- R-visualiseringar 
- Visuella PowerApps-objekt   

S: Möjligheten att kopiera ett visuellt objekt kan stängas av av IT-avdelningen eller Power BI-administratören.


F: Varför klistras mitt visuella objekt inte in på rätt sätt?    
S: Det finns begränsningar för anpassade visuella objekt och animerade visuella objekt. 



## <a name="next-steps"></a>Nästa steg
Mer om [Visualiseringar i Power BI-rapporter](end-user-visual-type.md)

Om du har redigeringsbehörighet för en rapport kan du [kopiera och klistra in visuella objekt i samma rapport](../visuals/power-bi-visualization-copy-paste.md). 

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

