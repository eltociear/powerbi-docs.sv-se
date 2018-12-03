---
title: Skapa visuella Power BI-objekt med R
description: Skapa visuella Power BI-objekt med R
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 0a739e963039e61aa66e398d27fa82982eb26bb0
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52670519"
---
# <a name="create-power-bi-visuals-using-r"></a>Skapa visuella Power BI-objekt med R
Med **Power BI Desktop**, kan du använda **R** för att visualisera dina data.

## <a name="install-r"></a>Installera R
**Power BI Desktop** inkluderar, distribuerar eller installerar inte **R**-motorn. Om du vill köra R-skript i **Power BI Desktop**, måste du separat installera **R** på din lokala dator. Du kan hämta och installera **R** kostnadsfritt från flera platser, inklusive [nedladdningssidan för Revolution Open](https://mran.revolutionanalytics.com/download/) och [CRAN Repository](https://cran.r-project.org/bin/windows/base/). Den aktuella versionen av R-skriptning i **Power BI Desktop** stöder unicode-tecken såväl som blanksteg (tomma tecken) i installationssökvägen.

## <a name="enable-r-visuals"></a>Aktivera R-visualiseringar
Om du vill aktivera r-visualiseringar, väljer du **Fil > Alternativ och inställningar > Alternativ** och på sidan **Alternativ** som visas, kontrollerar du att din lokala R-installation har angetts i avsnittet **R-skriptning** i fönstret **Alternativ** som det visas i följande bild. I följande bild, är sökvägen till den lokala installationen av R **C:\Program Files\R\R-3.2.0** och den sökvägen anges uttryckligen i textrutan. Kontrollera att sökvägen som visas återspeglar den lokala R-installation som du vill att **Power BI Desktop** ska använda.
   
   ![](media/desktop-r-visuals/r-visuals-2.png)

När du angett din R-installation, är du redo att börja skapa R-visualiseringar.

## <a name="create-r-visuals-in-power-bi-desktop"></a>Skapa R-visualiseringar i Power BI Desktop
1. Välj ikonen **R-visualisering** i fönstret **Visualisering** som visas i följande bild, för att lägga till en R-visualisering.
   
   ![](media/desktop-r-visuals/r-visuals-3.png)

   När du lägger till en R-visualisering till en rapport gör **Power BI Desktop** följande:
   
   - En R-visuell bildplatshållare visas på rapportens arbetsyta.
   
   - **R-skriptredigeraren** visas längst ned i mittenfönstret.
   
   ![](media/desktop-r-visuals/r-visuals-4.png)

2. Lägg nu till de fält som du vill använda i ditt R-skript till avsnittet **Värden** under brunnen **Fält**, precis som med andra **Power BI Desktop**-visualiseringar. 
    
    Endast fält som har lagts till i **Fält** är tillgängliga för ditt R-skript. Du kan lägga till nya fält eller ta bort onödiga fält från **Fält**-brunnen när du arbetar med ditt R-skript i **Power BI Desktop R-skriptredigeraren**. **Power BI Desktop** identifierar automatiskt vilka fält som du har lagt till eller tagit bort.
   
   > [!NOTE]
   > Aggregeringens standardtyp för visuella R-objekt är *Summera inte*.
   > 
   > 
   
3. Nu kan du använda de data du har valt för att skapa en rityta. 

    När du markerar fält, skapar **R-skriptredigeraren** stödjande R-skriptsbindningskod baserat på dina val i det grå avsnittet överst i redigerarfönstret. När du väljer eller tar bort ytterligare fält, skapas automatiskt stödjande kod i R-skriptet eller tas bort.
   
   I exemplet som visas i följande bild, har tre fält valts: hp, gear och drat. På grund av dessa val, skapade R-skriptredigeraren följande bindningskod:
   
   * En dataram som heter **datauppsättning** skapades
     * Den dataramen består av olika fält som användaren har valt
   * Standardsammansättningstypen är *summera inte*
   * Ungefär som med tabellvisualiseringar, grupperas fält och duplicerade rader visas bara en gång
   
   ![](media/desktop-r-visuals/r-visuals-5.png)
   
   > [!TIP]
   > I vissa fall kanske du inte vill att automatisk gruppering ska ske, eller så kanske du vill att alla rader visas, inklusive dubbletter. I så fall kan du lägga till ett indexfält till din datauppsättning som gör att alla rader anses vara unika vilket förhindrar gruppering.
   > 
   > 
   
   Den skapade dataramen heter **datauppsättning** och du kommer åt valda kolumner via deras respektive namn. Du kan t.ex. komma åt kugghjulsfältet genom att skriva *dataset$gear* i ditt R-skript. Använd enkla citattecken för fält med blanksteg eller specialtecken.

4. Nu när dataramen automatiskt skapats av de fält du valt, är du redo att skriva ett R-skript som resulterar i ritning till R-standardenheten. När skriptet har slutförts, väljer du **kör** från namnlisten för **R-skriptredigeraren** (**Kör** är till höger i namnlisten).
   
    När du väljer **Kör**, identifierar **Power BI Desktop** området och visar det på arbetsytan. Se till att nödvändiga paket installerats eftersom processen körs på din lokala R-installation.
   
   **Power BI Desktop** ritar om visualiseringen när någon av följande händelser inträffar:
   
   * När du väljer **Kör** från namnlisten för **R-skriptredigeraren**
   * När en dataändring inträffar, på grund av datauppdatering, filtrering eller markering

     Följande bild visar ett exempel på korrelationsritningskoden och ritar korrelationer mellan attribut för olika typer av bilar.

     ![](media/desktop-r-visuals/r-visuals-6.png)

5. För att få en större vy över visualiseringar, kan du minimera **R-skriptredigeraren**. Precis som i annan visuell information i **Power BI Desktop**, kan du korsfiltrera korrelationsritningen genom att välja endast sportbilar i toroidvisualiseringen (den runda visualiseringen till höger i ovanstående exempelbild).

    ![](media/desktop-r-visuals/r-visuals-7.png)

6. Du kan också modifiera R-skriptet för att anpassa den visuella informationen och utnyttja kraften i R genom att lägga till parametrar till ritkommandot.

    Det ursprungliga ritkommandot var följande:

    corrplot(M, method = "color",  tl.cex=0.6, tl.srt = 45, tl.col = "black")

    Med några ändringar i R-skriptet är nu kommandot följande:

    corrplot(M, method = "circle", tl.cex=0.6, tl.srt = 45, tl.col = "black", type= "upper", order="hclust")

    Därför ritar nu R-visualiseringen cirklar, överväger bara den övre hälften och sorterar om matrisen för att klustra korrelerade attribut som det visas i följande bild.

    ![](media/desktop-r-visuals/r-visuals-8.png)

    När ett R-skript körs som resulterar i ett fel, ritas inte det visuella R-objektet och ett felmeddelande visas på arbetsytan. Om du vill ha information om felet väljer du **Mer information** från R-visualiseringsfelet på arbetsytan.

    ![](media/desktop-r-visuals/r-visuals-9.png)

    > **Säkerhet för R-skript:** R-visualiseringar skapas från R-skript, vilka kan innehålla kod med säkerhets- eller integritetsrisker. När användare försöker visa eller interagera med en R-visualisering för första gången, visas en säkerhetsvarning. Aktivera endast visuell R-information om du litar på skaparen och källan, eller när du granskat och förstått R-skriptet.
    > 
    > 

## <a name="known-limitations"></a>Kända begränsningar
Visuell R-information i **Power BI Desktop** har några begränsningar:

* Storleksbegränsningar för data – data som används för ritning av visuella R-objekt är begränsat till 150 000 rader. Om du väljer mer än 150 000 rader, är det enbart de översta 150 000 raderna som används och ett meddelande visas på bilden.
* Tidsbegränsning för beräkningar – om en beräkning för ett visuellt R-objekt överstiger fem minuter så går tidsgränsen ut, vilket resulterar i ett fel.
* Relationer – om datafält väljs från olika tabeller utan någon definierad relation mellan dem så uppstår ett fel, precis som med andra Power BI Desktop-visualiseringar.
* Visuella R-objekt uppdateras när data uppdateras, filtreras eller markeras. Bilden är dock inte interaktiv och kan inte vara källa för korsfiltrering.
* Visuella R-objekt svarar på markering av andra visuella objekt, men du kan inte korsfiltrera andra element genom att klicka på element i det visuella R-objektet.
* Endast områden som ritas till R-standardenheten för visning visas korrekt på arbetsytan. Undvik att uttryckligen använda en annan R-visningsenhet.
* I den här versionen identifieras inte RRO-installationer automatiskt av 32-bitars versionen av Power BI Desktop så du måste manuellt ange sökvägen till R-installationskatalogen i **Alternativ och inställningar > Alternativ > R-skriptning**.

## <a name="next-steps"></a>Nästa steg
Ta en titt på följande extra information om R i Power BI.

* [Köra R-skript i Power BI Desktop](desktop-r-scripts.md)
* [Använd en extern R IDE med Power BI](desktop-r-ide.md)

