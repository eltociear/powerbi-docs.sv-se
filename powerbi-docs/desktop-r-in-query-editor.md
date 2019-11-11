---
title: Använda R i Power Query-redigeraren
description: Använda R i frågeredigeraren för Power BI Desktop till avancerade analyser
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/06/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: d2ba33e18701ad147cb38072461804b4528101ea
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73877924"
---
# <a name="use-r-in-query-editor"></a>Använda R i frågeredigeraren

[**R**](https://mran.microsoft.com/documents/what-is-r) är ett kraftfullt programmeringsspråk som används av många statistiker, dataforskare och dataanalytiker. Du kan använda **R** i **frågeredigeraren** i Power BI Desktop för att:

* Förbereda datamodeller

* Skapa rapporter

* Utföra datarengöring, avancerad datautformning och datamängdsanalys, som omfattar slutförande av saknade data, förutsägelser, klustring och mer.  

## <a name="install-r"></a>Installera R

Du kan ladda ned **R** kostnadsfritt från [nedladdningssidan för Revolution Open](https://mran.revolutionanalytics.com/download/) och [CRAN-lagringsplatsen](https://cran.r-project.org/bin/windows/base/).

### <a name="install-mice"></a>Installera mice

Du behöver ha [**mice**-biblioteket](https://www.rdocumentation.org/packages/mice/versions/3.5.0/topics/mice) installerat i din R-miljö. Utan **mice** fungerar inte exempelskriptkoden korrekt. **mice**-paketet implementerar en metod för hantering av saknade data.

Så här installerar du **mice**:

1. Starta programmet R.exe (till exempel C:\Program\Microsoft\R Open\R-3.5.3\bin\R.exe)  

2. Kör installationskommandot:

   ``` 
   >  install.packages('mice') 
   ```

## <a name="use-r-in-query-editor"></a>Använda R i frågeredigeraren

För att demonstrera användning av **R** i **frågeredigeraren** använder vi en exempeldatamängd för aktiemarknaden som finns i en .csv-fil och går igenom följande steg:

1. [Ladda ned **EuStockMarkets_NA.csv**-filen](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv). Kom ihåg var du sparar den.

1. Läs in filen i **Power BI Desktop**: på menyfliksområdet **Start** väljer du **Hämta data > Text/CSV**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_1.png)

1. Markera filen och välj **Öppna**. CSV-data visas i dialogrutan **Text-/CSV-fil**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_2.png)

1. När data har lästs in visas de i fönstret **Fält**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_3.png)

1. Öppna **frågeredigeraren** från menyfliksområdet **Start** genom att välja **Redigera frågor**.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_4.png)

1. I menyfliksområdet **Transformera** väljer du **Kör R-skript**. Redigeringsprogrammet **Kör R-skript** visas.  

   Raderna 15 och 20 har saknade data. Det gör även rader som du inte kan se i bilden. Stegen nedan visar hur R slutför de raderna.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_5d.png)

1. I det här exemplet anger du följande skriptkod. Se till att ersätta ”&lt;Your File Path&gt;” (Din filsökväg) med sökvägen till **EuStockMarkets_NA.csv** på ditt lokala filsystem, till exempel C:/Användare/Anders Andersson/Dokument/Microsoft/EuStockMarkets_NA.csv

    ```r
       dataset <- read.csv(file="<Your File Path>/EuStockMarkets_NA.csv", header=TRUE, sep=",")
       library(mice)
       tempData <- mice(dataset,m=1,maxit=50,meth='pmm',seed=100)
       completedData <- complete(tempData,1)
       output <- dataset
       output$completedValues <- completedData$"SMI missing values"
    ```

    > [!NOTE]
    > Du kan behöva skriva över en variabel med namnet *output* för att korrekt kunna skapa den nya datauppsättningen med tillämpade filter.

7. När du har valt **OK** visar **frågeredigeraren** en varning om datasekretess.

   ![](media/desktop-r-in-query-editor/r-in-query-editor_6.png)
8. För att R-skript ska fungera korrekt i Power BI-tjänsten behöver du ange alla datakällor till **offentliga**. Mer information om sekretessinställningar och deras konsekvenser finns i [Sekretessnivåer](desktop-privacy-levels.md).

   ![](media/desktop-r-in-query-editor/r-in-query-editor_7.png)

   När du har valt **Spara** körs skriptet. Observera en ny kolumn i fönstret **Fält** med namnet **completedValues**. Observera att det är några dataelement som saknas, t.ex på rad 15 och 18. Ta en titt på hur R hanterar det i nästa avsnitt.

   Trots att vi bara har fem rader med R-skript kan **frågeredigeraren** fylla i saknade värden med en förutsägelsemodell.

## <a name="create-visuals-from-r-script-data"></a>Skapa visuella objekt från R-skriptdata

Nu kan vi skapa ett visuellt objekt för att se hur R-skriptkoden använder biblioteket **mice** till att fylla i saknade värden, enligt följande bild:

![](media/desktop-r-in-query-editor/r-in-query-editor_8a.png)

Du kan spara alla slutförda visuella objekt i en **Power BI Desktop**-.pbix-fil och använda datamodellen och dess R-skript i Power BI-tjänsten.

> [!NOTE]
> Du kan [ladda ned en .pbix](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/Complete%20Values%20with%20R%20in%20PQ.pbix)-fil med alla de här stegen slutförda.

När du har laddat upp .pbix-filen till Power BI-tjänsten behöver du vidta ytterligare åtgärder för att aktivera uppdatering av tjänstdata och uppdaterade visuella objekt:  

* **Aktivera schemalagd uppdatering för datamängden** – information om hur du aktiverar schemalagd uppdatering för den arbetsbok som innehåller datamängd med R-skript finns i [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md), som även innehåller information om **Personlig gateway**.

* **Installera den personliga gatewayen** – du behöver ha en **personlig gateway** installerad på den dator där filen och **R** finns. Power BI-tjänsten använder den arbetsboken och renderar alla uppdaterade visuella objekt på nytt. Mer information finns i [installera och konfigurera en personlig gateway](service-gateway-personal-mode.md).

## <a name="limitations"></a>Begränsningar

Det finns vissa begränsningar för frågor med R-skript som skapats i **frågeredigeraren**:

* Alla inställningar för R-datakälla måste anges som **offentliga**. Alla andra steg i en fråga från **frågeredigeraren** måste också vara offentliga. Gå till inställningar för datakällan i **Power BI Desktop** genom att välja **Arkiv > Alternativ och inställningar > Datakällsinställningar**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_9.png)

  I dialogrutan **Datakällsinställningar** väljer du datakällan eller datakällorna och sedan **Redigera behörigheter...** .  Ange **Sekretessnivå** till **Offentlig**.

  ![](media/desktop-r-in-query-editor/r-in-query-editor_10.png)    
* För att aktivera schemalagd uppdatering av visuella R-objekt eller datamängden behöver du aktivera **Schemalagd uppdatering** och ha en **personlig gateway** installerad på den dator där arbetsboken och **R** finns. Mer information om detta finns i föregående avsnitt i den här artikeln, med länkar till mer information om var och en.

Det finns olika saker du kan göra med R och egna frågor, så utforska och utforma dina data precis som du vill att de ska visas.

## <a name="next-steps"></a>Nästa steg

* [Introduktion till R](https://mran.microsoft.com/documents/what-is-r) 

* [Kör R-skript i Power BI Desktop](desktop-r-scripts.md) 

* [Använd en extern R IDE med Power BI](desktop-r-ide.md) 

* [R-paket i Power BI-tjänsten](service-r-packages-support.md)
