---
title: Lägg till en anpassad kolumn i Power BI Desktop
description: Skapa snabbt en ny anpassad kolumn i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/18/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 25295447736ddb674d23a7b4ac34aa04f44887ba
ms.sourcegitcommit: 17f45a81b0dcbf9e3f1fb2a551584170baecd320
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72922517"
---
# <a name="add-a-custom-column-in-power-bi-desktop"></a>Lägg till en anpassad kolumn i Power BI Desktop

I Power BI Desktop kan du enkelt lägga till en ny anpassad kolumn med data i din modell med hjälp av Frågeredigeraren. I Frågeredigeraren kan du skapa och byta namn på den anpassade kolumnen för att skapa [PowerQuery M-formelfrågor](https://docs.microsoft.com/en-us/powerquery-m/quick-tour-of-the-power-query-m-formula-language) som definierar din anpassade kolumn. Det finns en [omfattande uppsättning funktionsreferenser](https://docs.microsoft.com/powerquery-m/power-query-m-function-reference) för PowerQuery M-formelfrågor. 

När du skapar en anpassad kolumn i Frågeredigeraren så lägger Power BI Desktop till den som ett **tillämpat steg** i **Frågeinställningar** för frågan. Du kan när som helst ändra eller flytta kolumnen.

![Sidan Lägg till anpassad kolumn](media/desktop-add-custom-column/add-custom-column_01.png)

## <a name="use-query-editor-to-add-a-custom-column"></a>Använd Frågeredigeraren till att lägga till en anpassad kolumn

Så här kommer du igång med att skapa en anpassad kolumn:

1. Starta Power BI Desktop och läs in några data.

2. Gå till fliken **Start** i menyfliksområdet, välj **Redigera frågor** och sedan **Redigera frågor** på menyn som visas.

   ![Välj Redigera frågor](media/desktop-add-custom-column/add-column-from-example_02.png)

   Fönstret **Frågeredigeraren** öppnas. 

2. Gå till fliken **Lägg till kolumn** i menyfliksområdet och välj **Anpassad kolumn**.

   ![Välj Anpassad kolumn](media/desktop-add-custom-column/add-custom-column_02.png)

   Fönstret **Lägg till anpassad kolumn** öppnas.

## <a name="the-add-custom-column-window"></a>Fönstret Lägg till anpassad kolumn

Fönstret **Lägg till anpassad kolumn** innehåller följande funktioner: 
- En lista med tillgängliga kolumner i listan **Tillgängliga kolumner** till höger.

- Standardnamnet för din anpassade kolumn i fältet **Nytt kolumnnamn**. Du kan ändra kolumnens namn.

- [PowerQuery M-formelfrågor](https://docs.microsoft.com/en-us/powerquery-m/power-query-m-function-reference) i rutan **Formel för anpassad kolumn**. Du skapar de här frågorna genom att skapa formeln som definierar den nya anpassade kolumnen. 

   ![Sidan Lägg till anpassad kolumn](media/desktop-add-custom-column/add-custom-column_03.png)

## <a name="create-formulas-for-your-custom-column"></a>Skapa formler för din anpassade kolumn

1. Välj en kolumn i listan **Tillgängliga kolumner** till höger och välj sedan **Infoga** under listan för att lägga till kolumnen i formeln för den anpassade kolumnen. Du kan också lägga till en kolumn genom att dubbelklicka på den i listan.

2. Lägg märke till indikatorn längst ned i fönstret **Lägg till anpassad kolumn** när du skriver formeln och skapar din kolumn. 

   Om det inte förekommer några fel ser du en grön bockmarkering och meddelandet *Inga syntaxfel har identifierats*.

   ![Lyckad syntaxkontroll på sidan Lägg till anpassad kolumn](media/desktop-add-custom-column/add-custom-column_04.png)

   Om det förekommer syntaxfel ser du en gul varningsikon och en länk till felet i formeln.

   ![Fel på sidan Lägg till anpassad kolumn](media/desktop-add-custom-column/add-custom-column_05.png)

3. Välj **OK**. 

   Power BI Desktop lägger till din anpassade kolumn i modellen och lägger till steget **Lade till anpassad** i listan **Tillämpade steg**för frågan i **Frågeinställningar**.

   ![Anpassad kolumn som lagts till i Frågeinställningar](media/desktop-add-custom-column/add-custom-column_06.png)

4. Om du vill ändra den anpassade kolumnen dubbelklickar du på steget **Lade till anpassad** i listan **Tillämpade steg**. 

   Fönstret **Lägg till anpassad kolumn** visas med formeln för din anpassade kolumn.

## <a name="use-the-advanced-editor-for-custom-columns"></a>Använda den avancerade redigeraren för anpassade kolumner

När du har skapat din fråga kan du också använda den **avancerade redigeraren** till att ändra frågestegen. Gör så här:

1. Gå till **Frågeredigeraren** och välj fliken **Visa** i menyfliksområdet. 

2. Välj **Avancerad redigerare**.

   Sidan **Avancerad redigerare** öppnas, där du har full kontroll över din fråga. 

   ![Sidan Avancerad redigerare](media/desktop-add-custom-column/add-custom-column_07.png)

   
## <a name="next-steps"></a>Nästa steg

- Du kan skapa anpassade kolumner på andra sätt, bland annat baserat på exempel du anger i Frågeredigeraren. Du kan läsa mer i [Lägg till en kolumn från ett exempel i Power BI Desktop](desktop-add-column-from-example.md).

- Referensinformation om Power Query M finns i [funktionsreferensen till Power Query M](/powerquery-m/power-query-m-function-reference).

