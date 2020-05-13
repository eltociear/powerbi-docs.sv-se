---
title: Importera Excel-arbetsböcker till Power BI Desktop
description: Du kan enkelt importera Excel-arbetsböcker som innehåller Power Query-frågor, Power Pivot-modeller och Power View-kalkylblad till Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 0a9880eea0511b942c3c7310a059caf5cd9415e1
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83292074"
---
# <a name="import-excel-workbooks-into-power-bi-desktop"></a>Importera Excel-arbetsböcker till Power BI Desktop
Med Power BI Desktop kan du enkelt importera Excel-arbetsböcker som innehåller Power Query-frågor, Power Pivot-modeller och Power View-kalkylblad till Power BI Desktop. Power BI Desktop skapar automatiskt rapporter och visualiseringar baserat på Excel-arbetsboken. Efter importen kan du fortsätta att förbättra och förfina rapporterna i Power BI Desktop med hjälp av befintliga funktioner och nya funktioner som lanseras med varje månatlig Power BI Desktop-uppdatering.

## <a name="how-do-i-import-an-excel-workbook"></a>Hur gör jag för att importera en Excel-arbetsbok?
1. Om du vill importera en Excel-arbetsbok till Power BI Desktop väljer du **Arkiv** > **Importera** > **Power Query, Power Pivot, Power View**.

   ![Importera Excel-arbetsbok](media/desktop-import-excel-workbooks/importexceltopbi_1.png)


2. Välj en Excel-arbetsbok att importera från fönstret **Öppna**. 

   Det finns för tillfället ingen begränsning angående storlek eller antal objekt i arbetsboken, men större arbetsböcker tar längre tid för Power BI Desktop att analysera och importera.

   > [!NOTE]
   > Om du vill läsa in eller importera Excel-filer från delade OneDrive för företag-mappar eller från Office 365-gruppmappar använder du webbadressen till Excel-filen och anger den som webbdatakälla i Power BI Desktop. Du måste utföra några steg för att formatera webbadressen till OneDrive för företag på rätt sätt, läs mer om de här stegen i [Använd OneDrive för företag-länkar i Power BI Desktop](desktop-use-onedrive-business-links.md).
   > 
   > 

3. Välj **Starta** i dialogrutan Importera som visas.

   ![Importera innehåll från en Excel-arbetsbok](media/desktop-import-excel-workbooks/import-excel-power-bi-5.png)


   Power BI Desktop analyserar arbetsboken och konverterar den till en Power BI Desktop-fil (.pbix). Den här åtgärden är en engångshändelse. När Power BI Desktop-filen har skapats med de här stegen är den inte beroende av den ursprungliga Excel-arbetsboken och kan modifieras, sparas och delas utan att den ursprungliga arbetsboken påverkas.

   När importen har slutförts visas en sammanfattningssida som beskriver de objekt som har konverterats, och eventuella objekt som inte kunde importeras.

   ![Importsammanfattningssida](media/desktop-import-excel-workbooks/importexceltopbi_3.png)

4. Välj **Stäng**. 

   Power BI Desktop importerar Excel-arbetsboken och läser in en rapport baserat på arbetsbokens innehåll.

   ![Inläst importrapport](media/desktop-import-excel-workbooks/importexceltopbi_4.png)

När arbetsboken har importerats kan du fortsätta att arbeta med rapporten. Du kan skapa nya visualiseringar, lägga till data eller skapa nya rapportsidor genom att använda någon av funktionerna i Power BI Desktop.

## <a name="which-workbook-elements-are-imported"></a>Vilka arbetsbokselement importeras?
Power BI Desktop kan importera följande element, som vanligtvis kallas *objekt*, i Excel.

| Objekt i Excel-arbetsboken | Slutresultatet i Power BI Desktop-filen |
| --- | --- |
| Power Query-frågor |Alla Power Query-frågor från Excel konverteras till frågor i Power BI Desktop. Om det finns frågegrupper definierade i Excel-arbetsboken replikeras samma organisation i Power BI Desktop. Alla frågor läses in om de inte har ställts in på **Skapa enbart anslutning** i Excel-dialogrutan **Importera data**. Du kan anpassa inläsningsbeteendet genom att välja **Egenskaper** på fliken **Start** i Frågeredigeraren i Power BI Desktop. |
| Externa Power Pivot-dataanslutningar |Alla externa Power Pivot-dataanslutningar konverteras till frågor i Power BI Desktop. |
| Länkade tabeller eller aktuella arbetsbokstabeller |Om det finns en kalkylbladstabell i Excel som är länkad till datamodellen, eller till en fråga (med hjälp av *From Table* eller funktionen *Excel.CurrentWorkbook()* i M), visas följande alternativ: <ol><li><b>Importera tabellen till Power BI Desktop-filen</b>. Den här tabellen är en ögonblicksbild av data, efteråt är data skrivskyddade i tabellen i Power BI Desktop. Det finns en storleksgräns på 1 miljon tecken (totalt för alla kolumnrubriker och celler) för tabeller som skapas med det här alternativet.</li><li><b>Behåll en anslutning till den ursprungliga arbetsboken</b>. Du kan även behålla en anslutning till den ursprungliga Excel-arbetsboken så hämtar Power BI Desktop det senaste innehållet i den här tabellen med varje uppdatering precis som andra frågor som skapas mot en Excel-arbetsbok i Power BI Desktop.</li></ul> |
| Beräknade kolumner, mått, KPI:er, datakategorier och relationer i datamodellen |De här datamodellobjekten konverteras till motsvarande objekt i Power BI Desktop. Observera att det finns vissa datakategorier som inte är tillgängliga i Power BI Desktop, som Bild. I de här fallen återställs datakategoriinformationen för kolumnerna. |
| Power View-kalkylblad |En ny rapportsida skapas för varje Power View-kalkylblad i Excel. Namnet och sorteringen för dessa rapportsidor matchar den ursprungliga Excel-arbetsboken. |

## <a name="are-there-any-limitations-to-importing-a-workbook"></a>Finns det några begränsningar för import av en arbetsbok?
Det finns några begränsningar när du importerar en arbetsbok till Power BI Desktop:

* **Externa anslutningar till SQL Server Analysis Services-tabellmodeller:** I Excel 2013 kan du skapa en anslutning till SQL Server Analysis Services-tabellmodeller och skapa Power View-rapporter ovanpå dessa modeller utan att behöva importera data. Den här typen av anslutning stöds för närvarande inte när du importerar Excel-arbetsböcker till Power BI Desktop. Under tiden måste du återskapa dessa externa anslutningar i Power BI Desktop.
* **Hierarkier:** Den här typen av datamodellobjekt stöds för närvarande inte i Power BI Desktop. Därför ignoreras hierarkier när du importerar Excel-arbetsböcker till Power BI Desktop.
* **Binära datakolumner:** Den här typen av datamodellobjekt stöds för närvarande inte i Power BI Desktop. Binära datakolumner tas bort från den resulterande tabellen i Power BI Desktop.
* **Power View-element som inte stöds:** Det finns några funktioner i Power View som inte är tillgängliga i Power BI Desktop, som teman och vissa typer av visualiseringar (som punktdiagram med uppspelningsaxel och beteenden för att öka detaljnivå). Dessa visualiseringar som inte stöds, resulterar i meddelanden om *visualiseringen stöds inte* på deras motsvarande platser i Power BI Desktop-rapporten, vilka du kan ta bort eller konfigurera om efter behov.
* **Namngivna områden som använder** ***From Table*** **i Power Query eller** ***Excel.CurrentWorkbook*** **i M:** För närvarande kan du inte importera de här typerna av namngivna områdesdata till Power BI Desktop, men det är en planerad uppdatering. För närvarande laddas dessa namngivna områden till Power BI Desktop som en anslutning till den externa Excel-arbetsboken.
* **PowerPivot till SSRS:** Externa PowerPivot-anslutningar till SQL Server Reporting Services (SSRS) stöds inte för närvarande eftersom datakällan inte är tillgänglig i Power BI Desktop.

