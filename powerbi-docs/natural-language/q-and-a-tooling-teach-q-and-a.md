---
title: Träna Frågor och svar att förstå frågor och termer i Power BI Frågor och svar
description: Så använder du Frågor och svar i Power BI till att utforska dina data
author: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 04/21/2020
ms.author: maggies
LocalizationGroup: Ask questions of your datadefintion
ms.openlocfilehash: 8f0d4c970de1724f47a016cbe063f1cc3df20178
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85239923"
---
# <a name="teach-qa-to-understand-questions-and-terms-in-power-bi-qa"></a>Träna Frågor och svar att förstå frågor och termer i Power BI Frågor och svar

I avsnittet **Träna Frågor och svar** i Frågor och svar-konfigurationen tränar du upp Frågor och svar att förstå frågor på naturligt språk och termer som inte känns igen. Börja genom att skicka en fråga som innehåller ett eller flera ord som Frågor och svar inte känner igen. Frågor och svar uppmanar dig då att definiera termen. Ange antingen ett filter eller fältnamn som motsvarar vad ordet representerar. Frågor och svar tolkar sedan om den ursprungliga frågan. Om du är nöjd med resultatet sparar du det.

> [!NOTE]
> Funktionen Träna Frågor och svar har bara stöd för importläget. Dessutom saknas för närvarande stöd för anslutning till en lokal datakälla eller en Azure Analysis Services-datakälla. Den här begränsningen bör försvinna i kommande versioner av Power BI.

## <a name="start-to-teach-qa"></a>Börja träna Frågor och svar

1. Öppna menyfliksområdet **Modellering** i Power BI Desktop och välj **Konfiguration av Frågor och svar** > **Träna Frågor och svar**.

    ![Röd synonym i Träna Frågor och svar](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-synonym-red.png)

2. Skriv en mening med en term som Frågor och svar inte känner igen och välj **Skicka**.

3. Välj ordet med röd understrykning. 

    Frågor och svar ger dig förslag och du uppmanas att ange rätt definition av termen. 
    
3. Ange en definition under **Definiera de termer som Frågor och svar inte förstod**.

    ![Förhandsgranska synonymer i Träna Frågor och svar](media/q-and-a-tooling-teach-q-and-a/qna-tooling-teach-fixpreview.png)

4. Välj **Spara** för att förhandsgranska det uppdaterade visuella objektet.

5. Ange nästa fråga eller välj **X** för att stänga fönstret.

Rapportanvändarna ser inte den här ändringen förrän du publicerar rapporten till tjänsten igen.

## <a name="define-nouns-and-adjectives"></a>Definiera substantiv och adjektiv

Du kan träna två typer av termer i Frågor och svar:

- Substantiv
- Adjektiv

### <a name="define-a-noun-synonym"></a>Definiera en synonym till ett substantiv

När du arbetar med data kan du ha namn på fält som användarna kan referera till med andra namn. Ett exempel kan vara Försäljning. Många ord eller fraser kan referera till försäljning, till exempel ”intäkter”. Om en kolumn heter Försäljning och rapportanvändaren skriver ”intäkter” kanske inte Frågor och svar kan välja rätt kolumn för att besvara frågan. I det här fallet vill du ange för Frågor och svar att ”försäljning” och ”intäkter” syftar på samma sak.

Frågor och svar identifierar automatiskt när ett okänt ord är ett substantiv, med hjälp av information från Microsoft Office. Om Frågor och svar identifierar ett substantiv visas följande uppmaning:

- <your term> **refererar till** 

Du fyller i rutan med termen från dina data.

![Uppmaning om synonym i Träna Frågor och svar](media/q-and-a-tooling-teach-q-and-a/qna-tooling-synonym-prompt.png)

Om du anger något annat än ett fält från datamodellen kan du få oönskade resultat.

### <a name="define-an-adjective-filter-condition"></a>Definiera ett filtervillkor för adjektiv

Ibland kanske du vill definiera termer som fungerar som ett villkor för underliggande data. Ett exempel kan vara ”utmärkta utgivare”. ”Utmärkta” kan vara ett villkor där du bara väljer utgivare som har publicerat X antal produkter. Frågor och svar försöker identifiera adjektiv och visar då en annan uppmaning:

- <field name> **som har**  

Du fyller i rutan med villkoret.

![Uppmaning om synonym i Träna Frågor och svar](media/q-and-a-tooling-teach-q-and-a/qna-tooling-adjectives.png)

Här är några exempel på villkor du kan definiera:

- Land som är USA
- Land som inte är USA
- Produkter > 100
- Produkter som är större än 100
- Produkter = 100
- Produkter är 100
- Produkter < 100
- Produkter som är mindre än 100

I de här exemplen kan ”produkter” vara antingen ett kolumnnamn eller ett mått. 

Du kan också ange en sammansättning i själva uttrycket för frågor och svar. Om till exempel ”populära produkter” är produkter med minst 100 sålda enheter kan du definiera produkter med ”summan av sålda enheter > 100” som populära.  

:::image type="content" source="media/q-and-a-tooling-teach-q-and-a/power-bi-qna-popular-products.png" alt-text="Definiera ”populära produkter”":::

Du kan bara definiera enstaka villkor i verktyget. Om du vill definiera mer komplicerade villkor använder du DAX och skapar en beräknad kolumn eller mått. Sedan kan du skapa ett enskilt villkor för den beräknade kolumnen eller måttet i verktyget.

## <a name="manage-terms"></a>Hantera termer

När du har angett definitioner kan du gå tillbaka för att se dina ändringar och redigera eller ta bort dem. 

1. I **Konfiguration av Frågor och svar** går du till avsnittet **Hantera termer**.

2. Ta bort de termer du inte vill använda längre. Du kan för närvarande inte redigera termer. Om du vill definiera om en term tar du bort termen och definierar den på nytt.

    ![Hantera termer i Frågor och svar](media/q-and-a-tooling-teach-q-and-a/qna-manage-terms.png)

## <a name="next-steps"></a>Nästa steg

Det finns ett antal metodtips för att förbättra motorn för naturligt språk. Mer information finns i [Frågor och svar – metodtips](q-and-a-best-practices.md).
