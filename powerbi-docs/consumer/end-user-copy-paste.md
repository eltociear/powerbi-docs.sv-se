---
title: Kopiera och klistra in en visualisering i Power BI-tjänsten
description: Kopiera och klistra in en visualisering i Power BI-tjänsten
author: mihart
ms.reviewer: maggie tsang
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 06/25/2020
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 4ff249002248b438b189b59defffd3c61d981b70
ms.sourcegitcommit: 46a340937d9f01c6daba86a4ab178743858722ec
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85398318"
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

    ![Ikonen Kopiera visuellt objekt visas](media/end-user-copy-paste/power-bi-copy-dashboard.png)

3. När dialogrutan **Ditt visuella objekt är redo att kopieras** visas väljer du **Kopiera till Urklipp**.

    ![dialogruta med alternativet Kopiera till Urklipp](media//end-user-copy-paste/power-bi-copied.png)

4. När det visuella objektet är redo klistrar du in det i ett annat program genom att trycka på **Ctrl + V** eller högerklicka > Klistra in. I skärmbilden nedan har vi klistrat in det visuella objektet i Microsoft Word. 

    ![visuellt objekt inklistrat i Outlook](media//end-user-copy-paste/power-bi-paste-word.png)

### <a name="copy-from-a-report-visual"></a>Kopiera från ett visuellt rapportobjekt 

1. Gå till den rapport som du vill kopiera från.

2. I det övre högra hörnet av det visuella objektet väljer du ikonen för **Kopiera visuellt objekt som bild**. 

    ![Ikonen Kopiera visuellt objekt visas](media/end-user-copy-paste/power-bi-copy-icon.png)

3. När dialogrutan **Ditt visuella objekt är redo att kopieras** visas väljer du **Kopiera till Urklipp**.

    ![dialogruta med alternativet Kopiera till Urklipp](media//end-user-copy-paste/power-bi-copied.png)


4. När det visuella objektet är redo klistrar du in det i ett annat program genom att trycka på **Ctrl + V** eller högerklicka > Klistra in. I skärmbilden nedan har vi klistrat in det visuella objektet i ett e-postmeddelande.

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
- PowerApps    

S: Möjligheten att kopiera ett visuellt objekt kan stängas av av IT-avdelningen eller Power BI-administratören.


F: Varför klistras mitt visuella objekt inte in på rätt sätt?    
S: Det finns begränsningar för anpassade visuella objekt och animerade visuella objekt. 



## <a name="next-steps"></a>Nästa steg
Mer om [Visualiseringar i Power BI-rapporter](end-user-visual-type.md)

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)

