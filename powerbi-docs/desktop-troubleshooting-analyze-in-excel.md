---
title: Felsöka Analysera i Excel i Power BI Desktop
description: Lösningar på vanliga problem för Analysera i Excel
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 07/27/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: cae73b7d232cf183fb99623016fba485904a2d7a
ms.sourcegitcommit: f01a88e583889bd77b712f11da4a379c88a22b76
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2018
ms.locfileid: "39326911"
---
# <a name="troubleshooting-analyze-in-excel"></a>Felsöka Analysera i Excel
Det kan finnas tillfällen när Analysera i Excel ger ett oväntat resultat eller funktionen inte fungerar som väntat. Den här sidan innehåller lösningar för vanliga problem när du använder Analysera i Excel.

> [!NOTE]
> Det finns en separat sida som är tillägnad åt att beskriva och aktivera [Analysera i Excel](service-analyze-in-excel.md).
> 
> Om det uppstår ett fel som inte finns i listan nedan och det orsakar problem, kan du be att få ytterligare hjälp på [community-webbplatsen](http://community.powerbi.com/) eller så kan du skapa ett [supportärende](https://powerbi.microsoft.com/support/).
> 
> 

Den här artikeln innehåller följande felsökningsavsnitt:

* Uppdatera Excel-bibliotek för OLE DB-providern
* Bestämma om du behöver uppdatera ditt Excel-bibliotek
* Anslutningsfel
* Förbjudet fel
* Inga datamodeller
* Token har upphört att gälla-fel
* Det går inte att ansluta till lokala Analysis Services
* Det går inte att dra något till området för pivottabellvärden (inga mått)

## <a name="update-excel-libraries-for-the-ole-db-provider"></a>Uppdatera Excel-bibliotek för OLE DB-providern
För att använda **Analysera i Excel** måste datorn ha en aktuell installerad AS OLE DB-provider. Denna [community-post](http://community.powerbi.com/t5/Service/Analyze-in-Excel-Initialization-of-the-data-source-failed/m-p/30837#M8081) är en bra källa för att verifiera installationen av OLE DB-providern eller för att hämta den senaste versionen.

Excel-biblioteket måste matcha din version av Windows. Om du använder 64-bitars-versionen av Windows måste du installera 64-bitars OLE DB-providern.

Om du vill hämta de senaste Excel-biblioteken ska du besöka Power BI och välja **nedåtpilen** i det övre högra hörnet av Power BI-tjänsten. Välj sedan **Analysera i Excel-uppdateringar**.

![](media/desktop-troubleshooting-analyze-in-excel/tshoot-analyze-excel_1.png)

I dialogrutan som visas väljer du **Hämta (förhandsgranskning)**.

![](media/desktop-troubleshooting-analyze-in-excel/tshoot-analyze-excel_2.png)

## <a name="determining-whether-you-need-to-update-your-excel-libraries"></a>Bestämma om du behöver uppdatera ditt Excel-bibliotek
Du kan hämta den senaste versionen av Excel OLE DB-providerbibliotek via länkarna i föregående avsnitt. När du har hämtat OLD DB-providerbiblioteket och startat installationen utförs kontroller mot den aktuella versionen.

Om ditt klientbibliotek för Excel OLE DB-providern är uppdaterat visas följande dialogruta:

![](media/desktop-troubleshooting-analyze-in-excel/troubleshoot-analyze-excel_3.png)

C:\Users\davidi\Desktop\powerbi-content-pr\articles\media\powerbi-desktop-troubleshooting-analyze-in-excel

Alternativt visas följande dialogruta om den nya versionen som du installerar är nyare än versionen på din dator:

![](media/desktop-troubleshooting-analyze-in-excel/troubleshoot-analyze-excel_2.png)

Om du ser en dialogruta som uppmanar dig att uppgradera bör du fortsätta med installationen för att hämta den senaste versionen av OLE DB-providern som är installerad på din dator.

## <a name="connection-cannot-be-made-error"></a>Anslutningsfel
Den primära orsaken till felet *Det går inte att upprätta en anslutning* är att din dators klientbibliotek för OLE DB-providern inte är aktuella. Information om hur du fastställer rätt uppdatering, samt länkar, finns i **Uppdatera Excel-bibliotek för OLE DB-providern** tidigare i den här artikeln.

## <a name="forbidden-error"></a>Förbjudet fel
Vissa användare har mer än ett Power BI-konto. När Excel försöker att ansluta till Power BI med hjälp av befintliga autentiseringsuppgifter kan autentiseringsuppgifter som inte har åtkomst till datauppsättningen eller rapporten som du vill komma åt användas.

När detta inträffar visas felmeddelandet **Förbjuden**, vilket innebär att du kan vara inloggad på Power BI med autentiseringsuppgifter som inte har behörighet för datauppsättningen. Efter att du har påträffat felet **Förbjuden** när du uppmanas att ange dina autentiseringsuppgifter ska du ange autentiseringsuppgifter som har behörighet att komma åt den datauppsättning som du försöker använda.

Om du fortfarande stöter på fel loggar du in på Power BI med kontot som har behörighet och kontrollerar att du kan visa och komma åt datauppsättningen i Power BI som du försöker få åtkomst till i Excel.

## <a name="no-data-models"></a>Inga datamodeller
Om det uppstår ett fel som anger att det **inte går att hitta OLAP-kubmodellen** innebär detta att datauppsättningen som du försöker få åtkomst till inte har någon datamodell och därför inte kan analyseras i Excel.

## <a name="token-expired-error"></a>Token har upphört att gälla-fel
Om du ser felet **Token har upphört att gälla** innebär det att du inte har använt funktionen **Analysera i Excel** på datorn som du använder. Ange dina autentiseringsuppgifter igen och öppna filen igen så bör felet försvinna.

## <a name="unable-to-access-on-premises-analysis-services"></a>Det går inte att ansluta till lokala Analysis Services
Om du försöker komma åt en datauppsättning som har anslutningar till lokala Analysis Services-data kan du få ett felmeddelande. **Analysera i Excel** stöder anslutning till datauppsättningar och rapporter på lokala **Analysis Services** med en anslutningssträng, så länge som datorn tillhör samma domän som **Analysis Services**-servern och ditt konto har åtkomst till den **Analysis Services**-servern.

## <a name="cant-drag-anything-to-the-pivottable-values-area-no-measures"></a>Det går inte att dra något till området värden i pivottabeller (inga mått)
När **Analysera i Excel** ansluter till en extern OLAP-modell (vilket är hur Excel ansluter till Power BI) kräver *pivottabellen* [att **åtgärder** ska definieras i den externa modellen](https://support.microsoft.com/kb/234700)eftersom alla beräkningar utförs på servern. Detta skiljer sig från när du arbetar med en lokal datakälla (till exempel tabeller i Excel, eller när du arbetar med datauppsättningar i **Power BI Desktop** eller **Power BI-tjänsten**), i vilket fall tabellmodellen är tillgänglig lokalt och [du kan använda införstådda mått](https://msdn.microsoft.com/library/gg399077.aspx), som är mått som genereras dynamiskt och inte lagras i datamodellen. I dessa fall kan Excel bete sig annorlunda än **Power BI Desktop** eller **Power BI-tjänsten**: det kan finnas kolumner i dessa data som kan hanteras som åtgärder i Power BI, men kan inte användas som värden (mått) i Excel.

Det finns ett par alternativ för att hantera det här problemet:

1. Skapa [mått i datamodellen i **Power BI Desktop**](desktop-tutorial-create-measures.md), publicera datamodellen för **Power BI-tjänsten** och få åtkomst till den publicerade datauppsättningen från Excel.
2. Skapa [mått i datamodellen från Excel PowerPivot](https://support.office.com/article/Create-a-Measure-in-Power-Pivot-d3cc1495-b4e5-48e7-ba98-163022a71198).
3. Om du har importerat data från en Excel-arbetsbok som endast innehåll tabeller (ingen datamodell) kan du [lägga till tabeller i datamodellen](https://support.office.com/article/Add-worksheet-data-to-a-Data-Model-using-a-linked-table-d3665fc3-99b0-479d-ba09-a37640f5be42). Följ därefter stegen i alternativ 2, direkt ovanför, för att skapa mått i datamodellen.

När din mått har definierats i modellen i Power BI-tjänsten kan du använda dem i området **Värden** i Excel PivotTables.

## <a name="next-steps"></a>Nästa steg
[Analysera i Excel](service-analyze-in-excel.md)

[Självstudier: Skapa dina egna mått i Power BI Desktop](desktop-tutorial-create-measures.md)

[Mått i PowerPivot](https://msdn.microsoft.com/library/gg399077.aspx)

[Skapa ett mått i PowerPivot](https://support.office.com/article/Create-a-Measure-in-Power-Pivot-d3cc1495-b4e5-48e7-ba98-163022a71198)

[Lägga till kalkylbladsdata i en datamodell med hjälp av en länkad tabell](https://support.office.com/article/Add-worksheet-data-to-a-Data-Model-using-a-linked-table-d3665fc3-99b0-479d-ba09-a37640f5be42)

[Skillnader mellan OLAP- och icke-OLAP-pivottabeller i Excel](https://support.microsoft.com/kb/234700)

