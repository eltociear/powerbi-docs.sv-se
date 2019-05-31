---
title: Azure Machine Learning-integrering i Power BI (förhandsversion)
description: Lär dig hur du använder Machine Learning med Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/02/2019
ms.author: davidi
LocalizationGroup: conceptual
ms.openlocfilehash: 6c09392566805f2857c50784f16c0e3f9d4b5697
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/29/2019
ms.locfileid: "61232502"
---
# <a name="azure-machine-learning-integration-in-power-bi-preview"></a>Azure Machine Learning-integrering i Power BI (förhandsversion)

Många organisationer använder **Machine Learning**-modeller för bättre insikter och förutsägelser om verksamheten. Möjligheten att visualisera och anropa insikter från dessa modeller i dina rapporter och instrumentpaneler och andra analyser kan hjälpa att sprida dessa insikter till företagsanvändare som behöver dem som mest.  Power BI gör du det enkelt att införliva insikter från modeller som finns på Azure Machine Learning Service med hjälp av enkla peka och klicka-åtgärder.

Om du vill använda den här funktionen kan en datatekniker bevilja åtkomst till Azure ML-modellen till den BI-analytikern som använder Azure Portal.  I början av varje session identifierar Power Query sedan alla Azure ML-modeller som användaren har åtkomst till och visar dem som dynamiska Power Query-funktioner.  Användaren kan sedan anropa dessa funktioner genom att öppna dem i menyfliksområdet i Power Query Editor eller genom att aktivera funktionen M direkt. Power BI slår automatiskt ihop åtkomstbegäranden då Azure ML-modellen anropas för en uppsättning rader för att få bättre prestanda.

Den här funktionen stöds för närvarande endast för Power BI-dataflöden och Power Query online i Power BI-tjänsten.

Mer information om dataflöden finns i [Självbetjänad dataförberedelse i Power BI](service-dataflows-overview.md).

Om du vill veta mer om Azure Machine Learning kan du läsa:

- Översikt:  [Vad är Azure Machine Learning-tjänsten?](https://docs.microsoft.com/azure/machine-learning/service/overview-what-is-azure-ml)
- Snabbstarter och självstudier för Azure Machine Learning:  [Dokumentation om Azure Machine Learning](https://docs.microsoft.com/azure/machine-learning/)

## <a name="granting-access-to-the-azure-ml-model-to-a-power-bi-user"></a>Bevilja åtkomst till Azure ML-modellen till en Power BI-användare

För att komma åt Azure ML-modellen från Power BI, måste användaren ha **Läs**-åtkomst till Azure-prenumerationen.  Dessutom gäller följande:

- För Machine Learning Studio-modeller **Läs**-åtkomst till webbtjänsten för Machine Learning Studio
- För Machine Learning Service-modeller **Läs**-åtkomst till Machine Learning Service-arbetsytan

Stegen i den här artikeln beskriver hur du ger en Power BI-användaråtkomst till en modell som finns i Azure ML-tjänsten så att de kan komma åt den här modellen som en Power Query-funktion.  Mer information finns i [Hantera åtkomst med RBAC och Azure Portal](https://docs.microsoft.com/azure/role-based-access-control/role-assignments-portal).

1. Logga in på [Azure-portalen](https://portal.azure.com).

2. Gå till sidan **Prenumerationer**. Du hittar sidan **Prenumerationer** i listan **Alla tjänster** i den vänstra navigeringsmenyn i Azure Portal.

    ![Sidan för Azure-prenumerationer](media/service-machine-learning-integration/machine-learning-integration_01.png)

3. Välj din prenumeration.

    ![Välj din prenumeration](media/service-machine-learning-integration/machine-learning-integration_02.png)

4. Välj **Åtkomstkontroll (IAM)** , och välj sedan knappen **Lägg till**.

    ![Åtkomstkontroll IAM](media/service-machine-learning-integration/machine-learning-integration_03.png)

5. Välj **Läsare** som rollen. Välj den Power BI-användare som du vill bevilja åtkomst till Azure ML-modellen för.

    ![Välj Läsare som rollen](media/service-machine-learning-integration/machine-learning-integration_04.png)

6. Välj **Spara**.

7. Upprepa steg tre till sex för att bevilja **Läsar**-åtkomst till användaren för den specifika Machine Learning Studio-webbtjänsten *eller* Machine Learning Service-arbetsytan som är värd för modellen.


## <a name="schema-discovery-for-machine-learning-service-models"></a>Identifiering av schema för Machine Learning Service-modeller

Dataforskare använder i första hand Python för att utveckla och distribuera även sina maskininlärningsmodeller för Machine Learning Service.  Till skillnad från Machine Learning Studio, som hjälper till att automatisera uppgiften med att skapa en schemafil för modellen, måste dataforskaren när det gäller Machine Learning Service uttryckligen skapa schemafilen med hjälp av Python.

Den här schemafilen måste inkluderas i

## <a name="invoking-the-azure-ml-model-in-power-bi"></a>Anropa Azure ML-modellen i Power BI

Du kan anropa alla Azure ML-modeller som du har beviljats åtkomst till direkt från Power Query-redigeraren i ditt dataflöde. För att komma åt Azure ML-modeller, väljer du knappen **Redigera** för den entitet som du vill utöka med insikter från din Azure ML-modell, såsom visas på följande bild.

![Power BI-tjänsten – redigera entiteten](media/service-machine-learning-integration/machine-learning-integration_05.png)

Genom att välja knappen **Redigera** öppnas Power Query Editor för entiteter i ditt dataflöde.

![Power Query Editor](media/service-machine-learning-integration/machine-learning-integration_06.png)

Välj knappen **AI-insikter** i menyfliksområdet och välj sedan mappen _Azure Machine Learning-modeller_ från den vänstra navigeringsmenyn. Alla Azure ML-modeller som du har åtkomst till visas här som Power Query-funktioner. Dessutom mappas automatiskt indataparametrarna för Azure ML-modellen som parametrar för motsvarande Power Query-funktion.

Du kan ange någon av den valda entitetens kolumner som indata från listrutan för att anropa en Azure ML-modell. Du kan också ange ett konstant värde som ska användas som indata genom att klicka på kolumnikonen till vänster om dialogrutan Indata.

![markera kolumnen](media/service-machine-learning-integration/machine-learning-integration_07.png)

Välj **Anropa** för att visa förhandsversionen av Azure ML-modellens utdatafiler som en ny kolumn i entitetstabellen. Du kan även se modellanropet som ett tillämpat steg för frågan.

![Välj anropa](media/service-machine-learning-integration/machine-learning-integration_08.png)

Om modellen returnerar flera utdataparametrar, grupperas de tillsammans som en post i utdatakolumnen. Du kan expandera kolumnen för att skapa enskilda utdataparametrar i separata kolumner.

![expandera kolumnen](media/service-machine-learning-integration/machine-learning-integration_09.png)

När du sparar ditt dataflöde anropas modellen automatiskt när dataflödet uppdateras, för alla nya eller uppdaterade rader i entitetstabellen.

## <a name="next-steps"></a>Nästa steg

Den här artikeln visade en översikt över integrering av Machine Learning i Power BI-tjänsten. Följande artiklar kan också vara intressanta och användbara. 

* [Självstudier: Anropa en Machine Learning Studio-modell i Power BI (förhandsgranskning)](service-tutorial-invoke-machine-learning-model.md)
* [Självstudier: Använda Cognitive Services i Power BI](service-tutorial-use-cognitive-services.md)
* [Cognitive Services i Power BI (förhandsversion)](service-cognitive-services.md)

Mer information om dataflöden finns i de här artiklarna:
* [Skapa och använda dataflöden i Power BI](service-dataflows-create-use.md)
* [Med beräknade entiteter på Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Med hjälp av dataflöden med lokala datakällor](service-dataflows-on-premises-gateways.md)
* [Resurser för utvecklare för Power BI dataflöden](service-dataflows-developer-resources.md)
* [Dataflöden och Azure Data Lake-integrering (förhandsversion)](service-dataflows-azure-data-lake-integration.md)


