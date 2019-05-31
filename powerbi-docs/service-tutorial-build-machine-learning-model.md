---
title: 'Självstudie: Skapa en Machine Learning-modell i Power BI (förhandsversion)'
description: I den här självstudien skapar du en Machine Learning-modellen i Power BI.
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
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61407194"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Självstudie: Skapa en Machine Learning-modell i Power BI (förhandsversion)

I den här självstudiekursen artikeln använder du **automatiserad Machine Learning** att skapa och tillämpa en binär förutsägelsemodell i Power BI. Självstudien innehåller vägledning för att skapa en Power BI-dataflöde och med hjälp av entiteterna som definierats i dataflödet att träna och validera en maskininlärningsmodell direkt i Power BI. Vi använder sedan den modellen för bedömning för att generera förutsägelser.

Först skapar du binära förutsägelse machine learning-modell för att förutsäga köp syftet med online julruschen baserat på en uppsättning deras online session-attribut. En datauppsättning som benchmark machine learning används för den här övningen. När en tränas genererar Power BI automatiskt en verifieringsrapport förklarar modellen resultaten. Du kan granska verifieringsrapporten och tillämpar modellen på dina data för bedömning.

Den här kursen består av följande steg:

> [!div class="checklist"]
> * Skapa ett dataflöde med indata
> * Skapa och träna en modell för maskininlärning
> * Granska verifieringsrapporten modell
> * Tillämpa modellen på en entitet för dataflöde
> * Med poängsatta utdata från modellen i Power BI-rapport

## <a name="create-a-dataflow-with-the-input-data"></a>Skapa ett dataflöde med indata

Den första delen av den här självstudien är att skapa ett dataflöde med indata. Den här processen tar några få steg som du ser i följande avsnitt från och med att hämta data.

### <a name="get-data"></a>Hämta data

Det första steget i att skapa ett dataflöde är att ha dina datakällor som är redo. I vårt fall använder vi en datauppsättning för maskininlärning från en uppsättning med online-sessioner, varav utmynnat i ett inköp. Datauppsättningen innehåller en uppsättning attribut om de här sessionerna som vi använder för att träna vår modell.

Du kan hämta datauppsättningen från webbplatsen UC Irvine.  Vi har också den tillgänglig i den här kursen från följande länk: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Skapa entiteter

Logga in på Power BI-tjänsten för att skapa entiteter i ditt dataflöde, och navigera till en arbetsyta på din dedikerade kapacitet som har AI-förhandsversionen aktiverad.

Om du inte redan har en arbetsyta kan du skapa en genom att välja **arbetsytor** i den vänstra navigeringsmenyn i Power BI-tjänsten och välj **skapa apparbetsyta** längst ned på panelen som visas. Då öppnas en panel till höger för att ange arbetsytans information. Ange ett namn på arbetsytan och välj **Avancerat**. Bekräfta att arbetsytan använder dedikerade kapacitet med hjälp av knappen och att den har tilldelats till en dedikerad kapacitet-instans som har AI-preview aktiveras. Välj sedan **Spara**.

![Skapa en arbetsyta](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

När arbetsytan har skapats kan du välja **hoppa över** i nederkant högra hörnet av skärmen Välkommen, enligt följande bild.

![Hoppa över om du har en arbetsyta](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Välj den **dataflöden (förhandsversion)** fliken. Välj den **skapa** längst upp till höger i arbetsytan och välj sedan **dataflöde**.

![Skapa dataflöde](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Välj **Lägg till nya entiteter**. Detta startar en **Power Query** redigeraren i webbläsaren.

![Lägg till ny entitet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Välj **Text/CSV-fil** som en datakälla som visas i följande bild.

![Valda text/CSF-filen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

I den **Anslut till en datakälla** som visas, klistra in länken nedan för att den *online_shoppers_intention.csv* till den **filsökväg eller URL** och sedan väljer  **Nästa**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Filsökväg](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

Power Query-redigeraren visas en förhandsgranskning av data från CSV-filen. Välj **transformera tabell** i kommandot menyfliksområdet och välj sedan **Låt första raden som rubriker** från menyn som visas. Detta lägger till den _befordras rubriker_ frågesteg i den **tillämpade steg** avsnitt till höger på skärmen. Du kan byta namn på frågan till ett mer användarvänligt namn genom att ändra värdet i den **namn** box hittades i den högra rutan. Du kan till exempel ändra Frågenamnet till _Online besökare_.

![Ändra till ett eget namn](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Vissa datatyper attribut i den här datauppsättningen är _numeriska_ eller _booleskt_, även om dessa kan tolkas som strängar med **Power Query**. Välj ikonen attributet typen högst upp på varje kolumnrubrik för att ändra de kolumner som anges ovan för att följande typer:

* **Decimaltal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **SANT/FALSKT:** Helgen; Intäkter

![Ändra datatyp](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

Den **binära förutsägelse** kommer vi tränar modellen kräver booleskt fältet som en etikett som identifierar resultat från tidigare observationer. I den här datauppsättningen i _intäkter_ attributet anger köp och det här attributet finns redan som ett booleskt värde. Därför behöver vi inte lägga till en beräknad kolumn för etiketten. Du kan behöva transformera befintliga etikettattributen till en boolesk kolumn i andra datauppsättningar.

Välj den **klar** för att stänga Power Query Editor. Detta visar entitetslistan med i _Online besökare_ data som vi har lagt till. Välj **spara** ange ett namn för dataflödet i det övre högra hörnet och välj sedan **spara** dialogrutan som visas i följande bild.

![Spara dataflödet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Uppdatera dataflödet

Spara resultaten dataflöde i ett meddelande som visas anger du att ditt dataflöde har sparats. Välj **Uppdatera nu** att mata in data från källan till dataflödet.

![Uppdatera nu](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Välj **Stäng** i övre högra hörnet och vänta tills dataflödesuppdateringen är färdig.

Du kan också uppdatera ditt dataflöde med hjälp av den **åtgärder** kommandon. Dataflödet Visar tidsstämpeln när uppdateringen har slutförts.

![Tidsstämpel för uppdatering](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Skapa och träna en modell för maskininlärning

Välj dataflödet när uppdateringen har slutförts. Om du vill lägga till en modell för maskininlärning, Välj den **gäller ML-modell** knappen i den **åtgärder** för den grundläggande entitet som innehåller information om data och etiketten din utbildning och sedan välja **Lägg till en Machine learning-modell**.

![Lägg till en maskininlärningsmodell](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

Det första steget för att skapa vår maskininlärningsmodellen är att identifiera historisk data, inklusive etikettfältet som du vill förutsäga. Modellen kommer att skapas genom att lära dig från dessa data.

När det gäller den datauppsättning som vi använder det här är den **intäkter** fält. Välj **intäkter** som värdet för historiska resultatet field- och välj sedan **nästa**.

![Välj historiska data](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Därefter måste vi välja vilken typ av machine learning-modell du skapar. Powerbi analyserar värdena i fältet historiska resultat som du har identifierat och ger förslag på vilka typer av machine learning-modeller som kan skapas för att förutsäga det fältet.

I det här fallet eftersom vi är att förutsäga ett binära resultat för om en användare gör ett köp eller inte markerar **binära förutsägelse** för modellen och sedan välja Nästa.

![Binär förutsägelse valt](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Sedan Power BI har en preliminär avsökning av data och ger förslag på indata som kan använda för modellen. Du har möjlighet att anpassa indatafält används för modellen. I vår granskad datauppsättning för att välja alla fält, markerar du kryssrutan bredvid entitetsnamnet på. Välj **nästa** att acceptera indata.

![Markera kryssrutan nästa](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

I det sista steget, måste vi ange ett namn för vår modell, samt egna etiketter för resultat som ska användas i den automatiskt genererade rapporten som kommer sammanfattar resultatet av verifieringen av modellen. Därefter måste vi namnge modellen _köp avsikt förutsägelse_, och true och false etiketter som _köp_ och _nr köp_. Välj sedan **Spara**.

![Spara modellen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Vår maskininlärningsmodellen är nu redo för utbildning. Välj **Uppdatera nu** att starta träna modellen.

![Uppdatera nu](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Utbildning processen påbörjas genom sampling och normaliserar dina historiska data och dela din datauppsättning i två nya entiteter *köp avsikt förutsägelse Träningsdata* och *köp avsikt förutsägelse testning Data*.

Beroende på storleken på datauppsättningen, kan utbildning processen ta allt från några minuter till ett par timmar. Du kan nu se modellen i den **Maskininlärningsmodeller** fliken dataflödet. Den _redo_ status anger att modellen har placerats i kö för utbildning eller omfattas av utbildning.

![Redo för utbildning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

När modellen är utbildning, inte du vill visa eller redigera dataflödet. Du kan bekräfta att modellen att utbilda och godkänts genom status för dataflödet. Detta visas som data uppdateras i den **dataflöden** fliken på arbetsytan.

![I processen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

När modellträning är klar visar dataflödet en uppdaterad uppdateringstid. Du kan bekräfta att modellen tränas genom att navigera till den **Maskininlärningsmodeller** fliken i dataströmmen. Modellen som du skapade bör ha status som **Trained** och **senaste tränade** tid ska nu uppdateras.

![Senast tränats på](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Granska verifieringsrapporten modell

Att granska verifieringsrapport modellen i den **Machine learning-modeller, s** välja den **visa systemprestanda-rapport och tillämpar modellen** knappen i den **åtgärder** kolumnen för modellen . Den här rapporten beskrivs hur machine learning-modell är troligt att utföra.

I den **Modellprestanda** sida i rapporten, Välj **Nyckelpåverkare** att visa de översta förutsägelserna för din modell. Du kan välja något av förutsägelserna att se hur resultatet-distribution som är associerade med att ge säkrare prognoser.

![Modellprestanda](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Du kan använda den **Sannolikhetströskelvärdet** utsnitt på sidan Modellprestanda och undersök dess inverkan på Precision och återkallande för modellen.

![Tröskelvärde för sannolikhet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

De övriga sidorna i rapporten beskrivs statistiska prestandamått för modellen.

Rapporten innehåller också en sida med utbildningsinformation som beskriver olika iterationer som kördes, hur funktioner extraherades från indata och hyperparametrar för den slutliga modellen som används.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Tillämpa modellen på en entitet för dataflöde

Välj den **tillämpa modellen** längst upp i rapporten för att anropa den här modellen när dataflödet uppdateras. I den **tillämpa** dialogrutan kan du ange målentiteten som innehåller källdata som modellen ska användas.

![Använd modellen](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

När du uppmanas, måste du **uppdatera** dataflöde att förhandsgranska resultaten från din modell.

Tillämpa modellen skapar en ny entitet med suffixet **berikats < modellnamn >** läggas till för den entitet som du tillämpat modellen. I vårt fall tillämpar modellen till den **OnlineShoppers** entitet skapar **OnlineShoppers berikats köp avsikt förutsägelse**, som innehåller de förväntade utdatan från modellen.

Tillämpa en binär förutsägelsemodell lägger till tre kolumner med förväntade resultatet, en sannolikhetspoäng och de översta posten-specifika Påverkare för förutsägelsen, var och en föregås av det angivna kolumnnamnet.

![Tre kolumner i resultatet](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Poängsatta utdatakolumner i entiteten avancerad och är endast tillgängliga från Power BI Desktop på grund av ett känt problem. Om du vill förhandsgranska dem i tjänsten, måste du använda en särskild förhandsvisning entitet.

När dataflödet uppdateringen har slutförts kan du välja den **OnlineShoppers berikats köp avsikt förutsägelse förhandsversion** entitet om du vill visa resultatet.

![Visa resultaten](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Med poängsatta utdata från modellen i Power BI-rapport

Om du vill använda poängsatta utdata från din machine learning-modell, kan du ansluta till ditt dataflöde från Power BI desktop kan använda dataflöden-anslutningen. Den **OnlineShoppers berikats köp avsikt förutsägelse** entiteten kan nu användas för att införliva förutsägelser från din modell i Power BI-rapporter.

## <a name="next-steps"></a>Nästa steg

I den här självstudien får du skapat och tillämpat en binär förutsägelsemodell i Power BI med de här stegen:

* Skapa ett dataflöde med indata
* Skapa och träna en modell för maskininlärning
* Granska verifieringsrapporten modell
* Tillämpa modellen på en entitet för dataflöde
* Med poängsatta utdata från modellen i Power BI-rapport

Läs mer om Machine Learning automation i Power BI, [automatiserad Machine Learning i Power BI (förhandsversion)](service-machine-learning-automated.md).
