---
title: Använda en extern R IDE med Power BI
description: Du kan starta och använda en extern IDE med Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: c51d89979ccf6791e69a7cdd457004b065b9d537
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34288876"
---
# <a name="use-an-external-r-ide-with-power-bi"></a>Använda en extern R IDE med Power BI
Med **Power BI Desktop** kan du använda din externa R IDE (Integrated Development Environment) för att skapa och förfina R-skript och sedan använda dessa skript i Power BI.

![](media/desktop-r-ide/r-ide_1a.png)

## <a name="enable-an-external-r-ide"></a>Aktivera en extern R IDE
Tidigare var du tvungen att använda R-skriptredigeraren i **Power BI Desktop** till att skapa och köra R-skript. Med den här versionen kan du starta din externa R IDE från **Power BI Desktop** och låta dina data importeras och visas automatiskt i R IDE. Därifrån kan du ändra skriptet i den externa R IDE:n och sedan klistra in den igen i **Power BI Desktop** för att skapa visuella Power BI-objekt och rapporter.

Från och med september 2016-versionen av **Power BI Desktop** (version 2.39.4526.362), kan du ange vilken R IDE som du vill använda och låta den startas automatiskt inifrån **Power BI Desktop**.

### <a name="requirements"></a>Krav
Om du vill använda den här funktionen måste du installera en **R IDE** på den lokala datorn. **Power BI Desktop** varken inkluderar, distribuerar eller installerar R-motorn, så du måste installera **R** på den lokala datorn separat. Du kan välja vilka R IDE som ska användas med följande alternativ:

* Du kan installera din favorit-R IDE – många finns tillgängliga kostnadsfritt på t.ex. [nedladdningssidan för Revolution Open](https://mran.revolutionanalytics.com/download/) och [CRAN Repository](https://cran.r-project.org/bin/windows/base/).
* **Power BI Desktop** stöder också [R Studio](https://www.rstudio.com/) och **Visual Studio 2015** med redigeringsprogrammen [*R Tools for Visual Studio*](https://beta.visualstudio.com/vs/rtvs/).
* Du kan också installera en annan R IDE och låta **Power BI Desktop** starta den **R IDE**:n genom att göra något av följande:
  
  * Du kan associera **.R**-filer med den externa IDE som du vill att **Power BI Desktop** ska starta.
  * Du kan ange den .exe som **Power BI Desktop** ska starta genom att välja *Övrigt* i avsnittet **R-skriptalternativ** i dialogrutan **Alternativ**. Du kan öppna dialogrutan **Alternativ** genom att gå till **Arkiv > Alternativ och inställningar > Alternativ**.
    
    ![](media/desktop-r-ide/r-ide_1b.png)

Om du har flera R IDE:er installerade kan du ange vilken som ska startas genom att välja den i listrutan *Identifierade R-IDE:er* i dialogrutan **Alternativ**.

Som standard startar **Power BI Desktop** **R Studio** som en extern R IDE om den är installerad på den lokala datorn. Om **R Studio** inte installeras och du har **Visual Studio 2015** med **R Tools for Visual Studio** kommer den att startas i stället. Om ingen av dessa R IDE:er är installerad kommer programmet som är associerat med **.R**-filer att startas.

Och om ingen **.R**-filassociation finns går det att ange en sökväg till en anpassad IDE i avsnittet *Bläddra till din önskade R-IDE* i dialogrutan **Alternativ**. Du kan också starta en annan R IDE genom att välja kugghjulsikonen **Inställningar** bredvid pilikonen **Starta R IDE** i **Power BI Desktop**.

## <a name="launch-an-r-ide-from-power-bi-desktop"></a>Starta en R IDE från Power BI Desktop
Starta en R IDE från **Power BI Desktop** genom att utföra följande steg:

1. Läs in data till **Power BI Desktop**.
2. Välj några fält i fönstret **Fält** som du vill arbeta med. Om du inte har aktiverat visuell skriptinformation ännu uppmanas du att göra detta.
   
   ![](media/desktop-r-ide/r-ide_3.png)
3. När visuell skriptinformation är aktiverad kan du välja ett visuellt R-objekt i fönstret **Visualiseringar**, vilket skapar ett tomt visuellt R-objekt som är redo att visa resultatet av skriptet. Fönstret **R-skriptredigerare** visas också.
   
   ![](media/desktop-r-ide/r-ide_4.png)
4. Du kan nu välja de fält som du vill använda i ditt R-skript. När du väljer ett fält skapar fältet **R-skriptredigerare** automatiskt skriptkod baserat på det eller de fält som du väljer. Du kan antingen skapa (eller klistra in) R-skriptet direkt i fönstret **R-skriptredigerare** eller lämna det tomt.
   
   ![](media/desktop-r-ide/r-ide_5.png)
   
   > [!NOTE]
   > Aggregeringens standardtyp för visuella R-objekt är *Summera inte*.
   > 
   > 
5. Nu kan du starta din R IDE direkt från **Power BI Desktop**. Välj knappen **Starta R IDE** som finns på höger sida i namnlisten **R-skriptredigerare** enligt nedan.
   
   ![](media/desktop-r-ide/r-ide_6.png)
6. Den angivna R IDE:n startas av Power BI Desktop enligt följande bild (i den här bilden är **RStudio** standard för R IDE).
   
   ![](media/desktop-r-ide/r-ide_7.png)
   
   > [!NOTE]
   > **Power BI Desktop** lägger till de tre första raderna i skriptet så att den kan importera data från **Power BI Desktop** när du kör skriptet.
   > 
   > 
7. Skript som du skapade i **fönstret R-skriptredigerare** i **Power BI Desktop** visas från och med rad 4 i R-IDE:n. Du kan nu skapa R-skriptet i R IDE:n. När R-skriptet är klart i din R-IDE måste du kopiera och klistra in det i fönstret **R-skriptredigerare** i **Power BI Desktop** igen, *exklusive* de tre första raderna i skriptet som **Power BI Desktop** skapade automatiskt. Kopiera inte de tre första raderna i skriptet tillbaka till **Power BI Desktop**, dessa rader användes bara för att importera data till din R IDE från **Power BI Desktop**.

### <a name="known-limitations"></a>Kända begränsningar
Att starta en R IDE direkt från Power BI Desktop har några begränsningar:

* Att automatiskt exportera skriptet från din R IDE till **Power BI Desktop** stöds inte.
* **R-klient**redigeraren (RGui.exe) stöds inte eftersom själva redigeraren inte stöder att öppna filer.

## <a name="next-steps"></a>Nästa steg
Ta en titt på följande extra information om R i Power BI.

* [Köra R-skript i Power BI Desktop](desktop-r-scripts.md)
* [Skapa visuella Power BI-objekt med R](desktop-r-visuals.md)

