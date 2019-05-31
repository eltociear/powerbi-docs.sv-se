---
ms.openlocfilehash: 4c1a7bce8eb24534974fe6a06a8bada4ba9fb708
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61265127"
---
I det här avsnittet tar vi en närmare titt på hur de första två delarna av Power BI fungerar ihop:

* Skapa en rapport i **Power BI Desktop**
* Publicera rapporten i **Power BI-tjänsten**

Vi börjar i Power BI Desktop och väljer **Hämta data**. Samling med datakällor visas, så att du kan välja en datakälla. I följande bild visas hur någon väljer en webbsida som källa. I videon ovan väljer Will en **Excel**-arbetsbok.

![](media/0-2-get-started-power-bi-desktop/c0a2_1.png)

Oavsett vilken datakälla du väljer, så ansluter Power BI till datakällan, och visar dig tillgängliga data från källan. Följande bild är ett annat exempel. Den är hämtad från en webbsida som analyserar olika tillstånd och viss intressant tillbakadragandestatistik.

![](media/0-2-get-started-power-bi-desktop/c0a2_2.png)

Du kan börja bygga rapporter i **rapportvyn** i Power BI Desktop.

**Rapportvyn** innehåller fem huvudområden:

1. Menyfliksområdet, där vanliga uppgifter som är associerade med rapporter och visualiseringar visas
2. **Rapportvyn**, eller arbetsytan, där visualiseringarna skapas och arrangeras
3. Flikområdet **Sidor** längst ned, där du kan välja eller lägga till en rapportsida
4. Rutan **Visualiseringar**, där du ändrar visualiseringar, anpassar färger, tillämpar filter, drar fält och mycket annat
5. Rutan **Fält**, där du kan dra frågeelement och filter till **rapportvyn** eller till området **Filter** i fönstret **Visualiseringar**

![](media/0-2-get-started-power-bi-desktop/c0a2_3.png)

Du kan dölja fönstren **Visualiseringar** och **Fält** genom att välja den lilla pilen längs kanten, vilket ger mer utrymme i **rapportvyn** för att skapa snygga visualiseringar. När du modifierar visualiseringar visas även pilar som pekar uppåt eller nedåt, vilket innebär att du kan visa respektive dölja motsvarande avsnitt.

![](media/0-2-get-started-power-bi-desktop/c0a2_4.png)

Om du vill skapa en visualisering är det bara att dra ett fält från listan **Fält** till **rapportvyn**. I det här fallet drar vi fältet Tillstånd från *RetirementStats* och ser vad som händer.

![](media/0-2-get-started-power-bi-desktop/c0a2_5.png)

Ser man på... Power BI Desktop har automatiskt skapat en kartabaserad visualisering eftersom programmet registrerade att fältet Tillstånd innehöll geoplatsdata.

Låt oss snabbspola framåt en bit nu. Efter att ha skapat en rapport med några visualiseringar kan vi nu publicera detta i Power BI-tjänsten. Välj **Publicera** i menyfliksområdet **Start** i Power BI Desktop.

![](media/0-2-get-started-power-bi-desktop/c0a2_6.png)

Du uppmanas att logga in på Power BI.

![](media/0-2-get-started-power-bi-desktop/c0a2_7.png)

När du har loggat in och publiceringsprocessen är klar visas följande dialogruta. Du kan välja länken (nedan **klart!** ), så kommer du till Power BI-tjänsten, där du kan se den rapport du precis har publicerat.

![](media/0-2-get-started-power-bi-desktop/c0a2_8.png)

När du loggar in på Power BI visas den Power BI Desktop-fil som du precis har publicerat i tjänsten. I bilden nedan visas den rapport som du skapade i Power BI Desktop i avsnittet **Rapporter**.

![](media/0-2-get-started-power-bi-desktop/c0a2_9.png)

I rapporten kan du välja **fästikonen** och fästa det visuella objektet på en instrumentpanel. Följande bild visar fästikonen markerad med en ljus ruta och pil.

![](media/0-2-get-started-power-bi-desktop/c0a2_10.png)

När du väljer ikonen visas följande dialogruta, med vilken du kan fästa det visuella objektet på en befintlig instrumentpanel eller skapa en ny instrumentpanel.

![](media/0-2-get-started-power-bi-desktop/c0a2_11.png)

När vi har fäst ett par visuella objekt från rapporten visas de på instrumentpanelen.

![](media/0-2-get-started-power-bi-desktop/c0a2_12.png)

Det finns såklart mycket mer du kan göra med Power BI, som att dela de instrumentpaneler du skapar. Vi kommer att diskutera detta längre fram i den här kursen.

Nu ska titta vi på en funktion som kan skapa instrumentpaneler automatiskt. Allt du behöver göra är att ansluta till en molntjänst som Facebook, Salesforce eller någon annan.

