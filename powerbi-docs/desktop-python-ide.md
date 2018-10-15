---
title: Använd en extern Python IDE med Power BI
description: Du kan starta och använda en extern IDE med Power BI
author: otarb
manager: rajatt
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 06/18/2018
ms.author: otarb
LocalizationGroup: Connect to data
ms.openlocfilehash: 634acc9e456462e2ca6d1a09bb6d97b87e75605b
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/17/2018
ms.locfileid: "45974999"
---
# <a name="use-an-external-python-ide-with-power-bi"></a>Använd en extern Python IDE med Power BI
Med **Power BI Desktop** kan du använda din externa Python IDE (Integrated Development Environment) för att skapa och förfina Python-skript och sedan använda dessa skript i Power BI.

![](media/desktop-python-ide/python-ide-1.png)

## <a name="enable-an-external-python-ide"></a>Aktivera ett externt Python IDE
Du kan starta ditt externa Python IDE från **Power BI Desktop** och låta dina data importeras och visas automatiskt i Python IDE. Därifrån kan du ändra skriptet i det externa Python IDE:t och sedan klistra in det igen i **Power BI Desktop** för att skapa visuella Power BI-objekt och rapporter.

Du kan ange vilket Python IDE som du vill använda och låta det startas automatiskt inifrån **Power BI Desktop**.

### <a name="requirements"></a>Krav
Om du vill använda den här funktionen måste du installera ett **Python IDE** på den lokala datorn. **Power BI Desktop** varken inkluderar, distribuerar eller installerar Python-motorn, så du måste installera **Python** på den lokala datorn separat. Du kan välja vilka Python IDE som ska användas med följande alternativ:

* Du kan installera ditt favorit-Python IDE – många finns tillgängliga kostnadsfritt på t.ex. [hämtningssidan för Visual Studio Code](https://code.visualstudio.com/download/).
* **Power BI Desktop** stöder också **Visual Studio**.
* Du kan också installera ett annat Python IDE och låta **Power BI Desktop** starta det **Python IDE**:t genom att göra något av följande:
  
  * Du kan associera **.PY**-filer med den externa IDE som du vill att **Power BI Desktop** ska starta.
  * Du kan ange den .exe som **Power BI Desktop** ska starta genom att välja *Övrigt* i avsnittet **Python-skriptalternativ** i dialogrutan **Alternativ**. Du kan öppna dialogrutan **Alternativ** genom att gå till **Arkiv > Alternativ och inställningar > Alternativ**.
    
    ![](media/desktop-python-ide/python-ide-2.png)

Om du har flera Python IDE:er installerade kan du ange vilken som ska startas genom att välja den i listrutan *Identifierade Python-IDE:er* i dialogrutan **Alternativ**.

Som standard startar **Power BI Desktop** **Visual Studio Code** som en extern Python IDE om den är installerad på den lokala datorn. Om **Visual Studio Code** inte installeras och du har **Visual Studio** så startas det istället. Om ingen av dessa Python IDE:er är installerade kommer programmet som är associerat med **.PY**-filer att startas.

Och om det inte finns någon **.PY**-filassociation så går det att ange en sökväg till en anpassad IDE i avsnittet *Bläddra till din önskade Python-IDE* i dialogrutan **Alternativ**. Du kan också starta en annan Python IDE genom att välja kugghjulsikonen **Inställningar** bredvid pilikonen **Starta Python IDE** i **Power BI Desktop**.

## <a name="launch-a-python-ide-from-power-bi-desktop"></a>Starta en Python IDE från Power BI Desktop
Starta en Python IDE från **Power BI Desktop** genom att utföra följande steg:

1. Läs in data till **Power BI Desktop**.
2. Välj några fält i fönstret **Fält** som du vill arbeta med. Om du inte har aktiverat visuell skriptinformation ännu uppmanas du att göra detta.
   
   ![](media/desktop-python-ide/python-ide-3.png)
3. När visuell skriptinformation är aktiverad kan du välja ett visuellt Python-objekt i fönstret **Visualiseringar**, vilket skapar ett tomt visuellt Python-objekt som är redo att visa resultatet av skriptet. Fönstret **Python-skriptredigerare** visas också.
   
   ![](media/desktop-python-ide/python-ide-4.png)
4. Du kan nu välja de fält som du vill använda i ditt Python-skript. När du väljer ett fält skapar fältet **Python-skriptredigerare** automatiskt skriptkod baserat på det eller de fält som du väljer. Du kan antingen skapa (eller klistra in) Python-skriptet direkt i fönstret **Python-skriptredigerare** eller lämna det tomt.
   
   ![](media/desktop-python-ide/python-ide-5.png)
   
   > [!NOTE]
   > Aggregeringens standardtyp för visuella Python-objekt är *Summera inte*.
   > 
   > 
5. Nu kan du starta din Python IDE direkt från **Power BI Desktop**. Välj knappen **Starta Python IDE** som finns på höger sida i namnlisten **Python-skriptredigerare** enligt nedan.
   
   ![](media/desktop-python-ide/python-ide-6.png)
6. Den angivna Python IDE:n startas av Power BI Desktop enligt följande bild (i den här bilden är **Visual Studio Code** standard för Python IDE).
   
   ![](media/desktop-python-ide/python-ide-7.png)
   
   > [!NOTE]
   > **Power BI Desktop** lägger till de tre första raderna i skriptet så att den kan importera data från **Power BI Desktop** när du kör skriptet.
   > 
   > 
7. Skript som du skapade i **fönstret Python-skriptredigerare** i **Power BI Desktop** visas från och med rad 4 i Python-IDE:n. Du kan nu skapa Python-skriptet i Python IDE:n. När Python-skriptet är klart i din Python-IDE måste du kopiera och klistra in det i fönstret **Python-skriptredigerare** i **Power BI Desktop** igen, *exklusive* de tre första raderna i skriptet som **Power BI Desktop** skapade automatiskt. Kopiera inte de tre första raderna i skriptet tillbaka till **Power BI Desktop**, dessa rader användes bara för att importera data till din Python IDE från **Power BI Desktop**.

### <a name="known-limitations"></a>Kända begränsningar
Att starta en Python IDE direkt från Power BI Desktop har några begränsningar:

* Att automatiskt exportera skriptet från din Python IDE till **Power BI Desktop** stöds inte.

## <a name="next-steps"></a>Nästa steg
Ta en titt på följande extra information om Python i Power BI.

* [Köra Python-skript i Power BI Desktop](desktop-python-scripts.md)
* [Skapa visuella Power BI-objekt med Python](desktop-python-visuals.md)

