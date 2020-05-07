---
title: Uppdatera en datauppsättning från OneDrive eller SharePoint Online
description: Uppdatera en datauppsättning som skapats från en Power BI Desktop-fil i OneDrive eller SharePoint Online
author: davidiseminger
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Data refresh
ms.openlocfilehash: b2a05f3112a9272d5e41cff20729c445c7a0ae39
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76038564"
---
# <a name="refresh-a-dataset-stored-on-onedrive-or-sharepoint-online"></a>Uppdatera en datauppsättning som lagras på OneDrive eller SharePoint Online
Att importera filer från OneDrive eller SharePoint Online i Power BI-tjänsten är ett bra sätt för att kontrollera att ditt arbete i Power BI Desktop förblir synkroniserat med Power BI-tjänsten.

## <a name="advantages-of-storing-a-power-bi-desktop-file-on-onedrive-or-sharepoint-online"></a>Fördelarna med att lagra en Power BI Desktop-fil i OneDrive eller SharePoint Online
När du lagrar en Power BI Desktop-fil på OneDrive eller SharePoint Online, kommer alla data som du har läst in i din filmodell importeras till datamängden. Alla rapporter som du har skapat i filen läses in i **Rapporter** i Power BI-tjänsten. Vi antar att du gör ändringar i din fil på OneDrive eller SharePoint Online. De här förändringarna kan innefatta att lägga till nya åtgärder, ändra kolumnnamn eller redigera visualiseringar. När du sparar filen, synkroniserar Power BI-tjänsten även med dessa ändringar, vanligtvis inom ungefär en timme.

Du kan utföra manuell engångsuppdatering direkt i Power BI Desktop genom att välja **Uppdatera** på menyfliken **Start**. När du väljer **Uppdatera**, uppdaterar du filmodellen med uppdaterade data från den ursprungliga datakällan. Den här typen av uppdatering sker helt och hållet inifrån själva Power BI Desktop-programmet. Den skiljer sig åt från manuell eller schemalagd uppdatering i Power BI och det är viktigt att förstå skillnaden.

![](media/refresh-desktop-file-onedrive/pbix-refresh.png)

När du importerar en Power BI Desktop-fil från OneDrive eller SharePoint Online, läser du in data, och modellinformation i en datamängd i Power BI. Du kommer att vilja uppdatera datamängden i Power BI-tjänsten, eftersom det är vad dina rapporter baseras på. Eftersom datakällorna är externa kan du manuellt uppdatera datamängden med **Uppdatera nu**. Du kan också konfigurera ett uppdateringsschema med hjälp av **Schemalägg uppdatering**. 

![](media/refresh-desktop-file-onedrive/powerbi-service-refresh.png)

När du uppdaterar datamängden ansluter Power BI inte till filen på OneDrive eller SharePoint Online för att fråga efter uppdaterade data. Den använder informationen i datamängden för att ansluta direkt till datakällorna och fråga efter uppdaterade data. Sedan läser den in dessa data till datamängden. Uppdaterade data i datamängden synkroniseras inte tillbaka till filen på OneDrive eller SharePoint Online.

## <a name="whats-supported"></a>Vad stöds?
Power BI har stöd för **Uppdatera** och **Schemalägg uppdatering** för datamängder som skapas från Power BI Desktop-filer som importerats från en lokal enhet där du använder **Hämta data** eller **Frågeredigeraren** för att ansluta till och läsa in data från nedanstående datakällor.

> [!NOTE]
> OneDrive-uppdatering för datamängder med liveanslutning stöds. Att ändra liveanslutningens datamängd, från en datamängd till en annan i en redan publicerad rapport, stöds dock inte i OneDrive-uppdateringsscenariot.

### <a name="power-bi-gateway---personal"></a>Power BI Gateway – Personal
* Alla datakällor online som visas i **Hämta data** och **Frågeredigeraren** i Power BI Desktop.
* Alla lokala datakällor som visas i **Hämta data** och **Frågeredigeraren** i Power BI Desktop, förutom Hadoop-filer (HDFS) och Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](./includes/refresh-datasources.md)]

> [!NOTE]
> En gateway måste vara installerad och köras för att Power BI ska kunna ansluta till lokala datakällor och uppdatera datauppsättningen.
> 
> 

## <a name="onedrive-or-onedrive-for-business-whats-the-difference"></a>OneDrive eller OneDrive för företag. Vad är skillnaden?
Om du både har en personlig OneDrive och OneDrive för företag, bör du behålla alla filer som du vill importera till Power BI på OneDrive för företag. Skälet är att du förmodligen använder två olika konton för att logga in till dem.

När du ansluter till OneDrive för företag i Power BI, är det enkelt att ansluta eftersom ditt Power BI-konto ofta är samma konto som ditt OneDrive för företag-konto. På din personliga OneDrive loggar du vanligtvis in med ett annat [Microsoft-konto](https://account.microsoft.com).

När du loggar in med ditt Microsoft-konto bör du markera **Jag vill förbli inloggad**. Power BI kan sedan synkronisera alla uppdateringar du gör i filen i Power BI Desktop med datamängderna i Power BI.

![](media/refresh-desktop-file-onedrive/refresh_signin_keepmesignedin.png)

Om du har ändrat dina Microsoft-autentiseringsuppgifter, kan du inte synkronisera ändringar mellan din fil på OneDrive och datamängden i Power BI. Du måste ansluta till och importera filen igen från OneDrive.

## <a name="how-do-i-schedule-refresh"></a>Hur gör jag för att schemalägga uppdateringar?
När du ställer in ett uppdateringsschema, ansluter Power BI direkt till datakällorna. Power BI använder anslutningsinformation och autentiseringsuppgifter i datamängden för att fråga efter uppdaterade data. Sedan läser Power BI in uppdaterade data i datamängden. Därefter uppdateras alla rapportvisualiseringar och instrumentpaneler baserat på datamängden i Power BI-tjänsten.

Mer information om hur du konfigurerar schemalagda uppdateringar finns i [Konfigurera schemalagd uppdatering](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Om något går fel
Om något går fel beror det vanligtvis på att Power BI inte kan logga in till datakällorna. Saker kan också gå fel om datamängden försöker ansluta till en lokal datakälla men gatewayen är offline. Kontrollera att Power BI kan logga in till datakällorna för att undvika sådana problem. Försöka att logga in till dina datakällor i **datakällans autentiseringsuppgifter**. Ibland ändras det lösenord som du använder för att logga in på en datakälla, eller så loggas Power BI ut från en datakälla.

Om du gör ändringar i Power BI Desktop-filen på OneDrive och spara, och dessa ändringar inte avspeglas i Power BI inom en timme, kan det bero på att Power BI inte kan ansluta till ditt OneDrive. Försök att ansluta till filen på OneDrive igen. Om du uppmanas att logga in bör du kontrollera att du har markerat **Jag vill förbli inloggad**. Eftersom Power BI inte kunde ansluta till ditt OneDrive för att synkronisera med filen måste du importera filen igen.

Se till att lämna **Skicka ett e-postmeddelande till mig om uppdateringen misslyckas** markerat. Du vill veta direkt om en schemalagd uppdatering misslyckas.

## <a name="troubleshooting"></a>Felsökning
Ibland går det inte som förväntat att uppdatera data. Du stöter normalt på datauppdateringsproblem när du är ansluten med en gateway. Ta en titt på artiklarna för gatewayfelsökning där du hittar verktyg och information om kända problem.

[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)

[Felsöka Power BI Gateway – Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

Fler frågor? Fråga [Power BI Community](https://community.powerbi.com/).

