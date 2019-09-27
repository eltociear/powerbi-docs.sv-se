---
title: 'Självstudie: Skapa en maskininlärningsmodell i Power BI (förhandsversion)'
description: I den här självstudien skapar du en maskininlärningsmodell i Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61407194"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Självstudie: Skapa en maskininlärningsmodell i Power BI (förhandsversion)

I den här självstudieartikeln använder du **automatiserad maskininlärning** till att skapa och tillämpa en modell för binär förutsägelse i Power BI. Självstudien innehåller vägledning om hur du skapar ett Power BI-dataflöde och använder de entiteter som definieras i dataflödet för att träna och validera en maskininlärningsmodell direkt i Power BI. Vi använder sedan den poängsättningsmodellen för att skapa förutsägelser.

Först skapar du en maskininlärningsmodell för binär förutsägelse i syfte att förutsäga inköpsavsikten hos onlinekonsumenter baserat på en uppsättning av deras onlinesessionsattribut. En maskininlärningsdatamängd för prestandatestning används i den här övningen. När en modell har tränats genererar Power BI automatiskt en valideringsrapport som förklarar modellens utfall. Du kan sedan granska valideringsrapporten och tillämpa modellen på dina data för poängsättning.

Den här självstudien består av följande steg:

> [!div class="checklist"]
> * Skapa ett dataflöde med indata
> * Skapa och träna en maskininlärningsmodell
> * Granska modellens valideringsrapport
> * Tillämpa modellen på en dataflödesentitet
> * Använda det poängsatta utfallet från modellen i en Power BI-rapport

## <a name="create-a-dataflow-with-the-input-data"></a>Skapa ett dataflöde med indata

Den första delen av den här självstudien är att skapa ett dataflöde med indata. Såsom det visas i följande avsnitt består processen av några steg som börjar med hämtning av data.

### <a name="get-data"></a>Hämta data

Det första steget i att skapa ett dataflöde är att förbereda datakällorna. I vårt fall använder vi en maskininlärningsdatamängd från en uppsättning onlinesessioner, varav vissa resulterade i ett köp. Datamängden innehåller en uppsättning attribut om dessa sessioner, som vi kommer att använda för att träna modellen.

Du kan ladda ned datamängden från webbplatsen för UC Irvine.  För den här självstudien finns den även tillgänglig via följande länk: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Skapa entiteterna

Logga in på Power BI-tjänsten för att skapa entiteter i ditt dataflöde, och navigera till en arbetsyta på din dedikerade kapacitet som har AI-förhandsversionen aktiverad.

Om du inte redan har en arbetsyta kan du skapa en genom att välja **Arbetsytor** i den vänstra navigeringsmenyn i Power BI-tjänsten och sedan välja **Skapa apparbetsyta** längst ned på de panel som visas. Då öppnas en panel till höger där du kan ange arbetsytans information. Ange ett namn på arbetsytan och välj **Avancerat**. Bekräfta att arbetsytan använder dedikerad kapacitet med hjälp av alternativknappen samt att den tilldelas till en instans av dedikerad kapacitet där AI-förhandsgranskningen är aktiverad. Välj sedan **Spara**.

![Skapa en arbetsyta](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

När arbetsytan har skapats kan du välja **Hoppa över** längst ned till höger på välkomstskärmen enligt följande bild.

![Hoppa över om du har en arbetsyta](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Välj fliken **Dataflöden (förhandsversion)** . Välj knappen **Skapa** längst upp till höger på arbetsytan och välj sedan **Dataflöden**.

![Skapa dataflöde](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Välj **Lägg till nya entiteter**. Detta startar en **Power Query**-redigerare i webbläsaren.

![Lägg till ny entitet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Välj **Text-/CSV-fil** som datakälla enligt följande bild.

![Text-/CSF-fil har valts](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

I rutan **Anslut till en datakälla** som sedan visas klistrar du in följande länk till *online_shoppers_intention.csv* i rutan **Filsökväg eller URL** och väljer **Nästa**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Filsökväg](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Power Query-redigeraren visar en förhandsgranskning av data från CSV-filen. Välj **Transformera tabell** i menyfliksområdet för kommandon och välj sedan **Använd första raden som rubriker** i den meny som visas. Detta lägger till frågesteget _Upphöjda rubriker_ i avsnittet **Tillämpade steg** till höger på skärmen. Du kan byta namn på frågan till ett användarvänligt namn genom att ändra värdet i rutan **Namn** i det högra fönstret. Du kan till exempel ändra frågans namn till _Online Visitor_ (onlinebesökare).

![Ändra till ett användarvänligt namn](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Några av attributdatatyperna i den här datamängden är _numeriska_ eller _booleska_, men dessa kan tolkas som strängar av **Power Query**. Välj den ikon för attributtyp som visas överst i varje kolumnrubrik för att ändra de kolumner som anges nedan till följande typer:

* **Decimaltal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **Sant/falskt:** Weekend; Revenue

![Ändra datatyp](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

Den modell för **binär förutsägelse** som vi kommer att träna kräver en märkning i form av booleskt fält som identifierar utfallen från tidigare observationer. I den här datamängden anger attributet _Revenue_ (intäkter) köp, och det här attributet är redan tillgängligt som ett booleskt värde. Därför behöver vi inte lägga till en beräknad kolumn för märkningen. I andra datamängder kan du behöva transformera befintliga märkningsattribut till en boolesk kolumn.

Välj knappen **Klar** för att stänga Power Query-redigeraren. Då visas entitetslistan med de data för _Online Visitors_ (onlinebesökare) som vi lade till. Välj **Spara** i det övre högra hörnet, ange ett namn för dataflödet och välj sedan **Spara** i dialogrutan enligt följande bild.

![Spara dataflödet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Uppdatera dataflödet

När du sparar dataflödet visas ett meddelande om att dataflödet har sparats. Välj **Uppdatera nu** för att mata in data från källan till dataflödet.

![Uppdatera nu](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Välj **Stäng** i övre högra hörnet och vänta tills dataflödesuppdateringen är färdig.

Du kan även uppdatera dataflödet med hjälp av kommandona **Åtgärder**. Dataflödet visar tidsstämpeln när uppdateringen har slutförts.

![Tidsstämpel för uppdatering](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Skapa och träna en maskininlärningsmodell

Välj dataflödet efter att uppdateringen har slutförts. Du lägger till en maskininlärningsmodell genom att välja knappen **Tillämpa ML-modell** i listan **Åtgärder** för den basentitet som innehåller dina träningsdata och din märkningsinformation, och välj sedan **Lägg till en maskininlärningsmodell**.

![Lägg till en maskininlärningsmodell](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

Det första steget för att skapa maskininlärningsmodellen är att identifiera historiska data, inklusive det märkningsfält som du vill förutsäga. Modellen skapas genom inlärning från dessa data.

För den datamängd som vi använder är detta fältet **Revenue** (intäkter). Välj **Revenue** (intäkter) som värde för fältet ”Historiska utfall” och välj sedan **Nästa**.

![Välja historiska data](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Därefter måste vi välja vilken typ av maskininlärningsmodell som ska skapas. Power BI analyserar värdena i fältet för historiska utfall som du har identifierat och föreslår de typer av maskininlärningsmodeller som kan skapas för att förutsäga det fältet.

Eftersom vi förutsäger ett binärt utfall för huruvida en användare kommer att genomföra ett köp väljer du i det här fallet **Binär förutsägelse** för modelltypen och väljer sedan Nästa.

![Binär förutsägelse har valts](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Därefter gör Power BI en preliminär genomsökning av data och föreslår de indata som modellen kan använda. Du kan anpassa de indatatyper som används för modellen. I vår organiserade datamängd markerar du alla fält genom att markera kryssrutan intill entitetsnamnet. Välj **Nästa** för att godkänna indata.

![Markera kryssrutan Nästa](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

I det sista steget måste vi ange ett namn för modellen samt de användarvänliga märkningarna för de utfall som ska användas i den automatiskt genererade rapport som kommer att sammanfatta resultatet av modellens validering. Sedan måste vi namnge modellen _Purchase Intent Prediction_ (Förutsägelse av inköpsavsikt) samt märkningarna för sant och falskt som _Purchase_ (Köp) och _No-Purchase_ (Inget köp). Välj sedan **Spara**.

![Spara modellen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Nu är maskininlärningsmodellen redo att tränas. Välj **Uppdatera nu** för att börja träna modellen.

![Uppdatera nu](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Träningsprocessen börjar med sampling och normalisering av dina historiska data samt indelning av datamängden i två nya entiteter, *Purchase Intent Prediction Training Data* (Träningsdata för förutsägelse av inköpsavsikt) och *Purchase Intent Prediction Testing Data* (Testningsdata för förutsägelse av inköpsavsikt).

Beroende på storleken på datamängden kan träningsprocessen ta allt från några minuter till några timmar att slutföras. Nu kan du se modellen på fliken **Maskininlärningsmodeller** för dataflödet. Statusen _Redo_ anger att modellen har ställts i kö för träning eller håller på att tränas.

![Redo för träning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Medan modellen tränas kan du inte visa eller redigera dataflödet. Du kan bekräfta att modellen tränas och valideras via statusen för dataflödet. Detta visas som en pågående datauppdatering på fliken **Dataflöden** för arbetsytan.

![Pågår](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

När modellträningen är klar visar dataflödet en uppdaterad uppdateringstid. Du kan bekräfta att modellen har tränats genom att gå till fliken **Maskininlärningsmodeller** i dataflödet. Den modell som du skapade bör visa statusen **Tränad**, och tiden för **Senast tränad** bör nu ha uppdaterats.

![Senast tränad](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Granska modellens valideringsrapport

Du kan granska modellens valideringsrapport genom att i **Maskininlärningsmodeller** välja knappen **Visa prestandarapport och tillämpa modell** i kolumnen **Åtgärder** för modellen. I den här rapporten beskrivs sannolik prestanda för din maskininlärningsmodell.

På sidan **Modellprestanda** i rapporten väljer du **Viktiga influerare** för att visa de främsta förutsägande faktorerna för din modell. Du kan välja en av de förutsägande faktorerna för att se den utfallsfördelning som är associerad med den förutsägande faktorn.

![Modellprestanda](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Du kan använda utsnittet **Sannolikhetströskel** på sidan Modellprestanda för att undersöka dess inverkan på modellens precision och träffsäkerhet.

![Tröskelvärde för sannolikhet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

De andra sidorna i rapporten beskriver modellens statistiska prestandamått.

Rapporten innehåller även en sida med träningsinformation som beskriver de olika iterationer som kördes, hur egenskaperna extraherades från indata samt de hyperparametrar som användes för den slutliga modellen.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Tillämpa modellen på en dataflödesentitet

Välj knappen **Tillämpa modell** överst i rapporten för att anropa den här modellen när dataflödet uppdateras. I dialogrutan **Tillämpa** kan du ange den målentitet som innehåller de källdata som modellen ska tillämpas på.

![Använd modellen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

När du uppmanas måste du **Uppdatera** dataflödet för att förhandsgranska resultatet av modellen.

Om du tillämpar modellen skapas en ny entitet med suffixet **enriched <modellnamn>** (utökad) som läggs till i den entitet som du tillämpade modellen på. I vårt fall kommer tillämpning av modellen på entiteten **OnlineShoppers** att skapa **OnlineShoppers enriched Purchase Intent Prediction**, som innehåller förutsagda utdata från modellen.

Tillämpning av en modell för binär förutsägelse lägger till tre kolumner med förutsagt utfall, sannolikhetspoäng samt de främsta postspecifika influerarna för förutsägelsen, som var och en prefigeras med det angivna kolumnnamnet.

![Tre kolumner med utfall](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

På grund av ett känt problem kan de poängsatta utdatakolumnerna i den utökade entiteten endast nås från Power BI Desktop. Om du vill förhandsgranska dessa i tjänsten måste du använda en särskild förhandsgranskningsentitet.

När uppdateringen av dataflöde är klar kan du välja entiteten **OnlineShoppers enriched Purchase Intent Prediction Preview** för att visa resultatet.

![Visa resultatet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Använda det poängsatta utfallet från modellen i en Power BI-rapport

För att använda det poängsatta utfallet från maskininlärningsmodellen kan du ansluta till ditt dataflöde från Power BI Desktop med hjälp av anslutningsprogrammet för dataflöden. Du kan nu använda entiteten **OnlineShoppers enriched Purchase Intent Prediction** för att ta med förutsägelserna från din modell i Power BI-rapporter.

## <a name="next-steps"></a>Nästa steg

I den här självstudien skapade och tillämpade du en modell för binär förutsägelse i Power BI med hjälp av följande steg:

* Skapa ett dataflöde med indata
* Skapa och träna en maskininlärningsmodell
* Granska modellens valideringsrapport
* Tillämpa modellen på en dataflödesentitet
* Använda det poängsatta utfallet från modellen i en Power BI-rapport

Mer information om automatiserad maskininlärning i Power BI finns i [Automatiserad maskininlärning i Power BI (förhandsversion)](service-machine-learning-automated.md).
