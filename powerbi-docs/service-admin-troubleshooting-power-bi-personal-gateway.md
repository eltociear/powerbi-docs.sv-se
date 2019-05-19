---
title: Felsöka Power BI Gateway – Personal
description: Felsöka Power BI Gateway – Personal
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 5/06/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: bc6eaccc2976266102dcca0d20df73df810fa5f3
ms.sourcegitcommit: bf535771c9ef495f9bb658569403fa5e3dd82e6a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65853547"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Felsöka Power BI Gateway – Personal
I följande avsnitt går igenom några vanliga problem som du kan stöta på när du använder Power BI Gateway-Personal.

> [!NOTE]
> Den aktuella versionen av gatewayen för personligt bruk är **Lokal datagateway (personlig)**. Uppdatera din installation om du vill använda den här versionen.
> 
> 

## <a name="update-to-the-latest-version"></a>Uppdatera till den senaste versionen
Många problem kan uppstå om gatewayversionen är inaktuell.  Det är en allmänt bra vana att kontrollera att du är den senaste versionen. Om du inte har uppdaterat gatewayen på en månad eller längre, Överväg att installera den senaste versionen av gatewayen. Läs om du kan återskapa problemet.

## <a name="installation"></a>Installation
**Personliga gatewayen är 64-bitars** – om din dator är 32-bitars, du kan inte installera den personliga gatewayen. Operativsystemet måste vara 64-bitarsversionen. Installera en 64-bitars version av Windows eller installera den personliga gatewayen på en 64-bitars dator.

**Personliga gatewayen kan inte installeras som en tjänst, även om du är en lokal administratör för datorn** -installationen kan misslyckas om användaren finns i datorns lokala gruppen Administratörer, men grupprincipen inte tillåter det aktuella användarnamnet att logga in som en tjänsten. Kontrollera att en Grupprincip, kan användaren logga in som en tjänst för tillfället. Vi arbetar på att lösa problemet. [Läs mer](https://technet.microsoft.com/library/cc739424.aspx)

**Tidsgränsen nåddes för åtgärden** – det här meddelandet är vanligt om datorn (fysisk eller virtuell dator) som du installerar den personliga gatewayen har en processor med enkel kärna. Stäng alla program och inaktivera alla processer som inte behövs och försök installera igen.

**Data Management Gateway eller Analysis Services Connector kan inte installeras på samma dator som den personliga gatewayen** – om du redan har en Analysis Services Connector eller Data Management Gateway installerat måste du först avinstallera anslutningen eller gatewayen. Försök att installera den personliga gatewayen.

> [!NOTE]
> Om det uppstår ett problem under installationen kan kan installationsloggarna ge information för att hjälpa dig att lösa problemet. Mer information finns i [installationsloggar](#SetupLogs).
> 
> 

 **Proxykonfiguration** uppstå problem med att konfigurera din personliga gateway om miljön har behov av en proxy. Mer information om hur du konfigurerar proxyinformation finns i [Konfigurera proxyinställningar för Power BI-gatewayerna](service-gateway-proxy.md)

## <a name="schedule-refresh"></a>Uppdatera schema
**Fel: Autentiseringsuppgiften som lagras i molnet saknas.**

Du kan få detta fel i inställningarna för \<datauppsättning\> om du har en schemalagd uppdatering och sedan avinstallerats och installerats om den personliga gatewayen. När du avinstallerar en personlig gateway tas datakällans autentiseringsuppgifter för en datauppsättning som har konfigurerats för uppdatering bort från Power BI-tjänsten.

**Lösning:** I Power BI så går du till uppdateringsinställningarna för en datauppsättning. I Hantera datakällor för alla datakällor med fel väljer **redigera autentiseringsuppgifter** och logga in till datakällan igen.

**Fel: De autentiseringsuppgifter som anges för datauppsättningen är ogiltiga. Uppdatera autentiseringsuppgifterna genom en uppdatering eller i dialogrutan Inställningar för datakälla om du vill fortsätta.**

**Lösning**: Om du får ett meddelande om autentiseringsuppgifter så kan det innebära:

* Kontrollera att användarnamn och lösenord för att logga in på datakällor är uppdaterade. Gå till datauppsättningens uppdateringsinställningar i Power BI. I Hantera datakällor väljer **redigera autentiseringsuppgifter** att uppdatera autentiseringsuppgifterna för datakällan.
* Kombinationsprogram mellan en molnkälla och en lokal datakälla, i en enda fråga, inte uppdateras i den personliga gatewayen om en av källorna använder OAuth för autentisering. Ett exempel på det här problemet är ett kombinationen mellan CRM Online och en lokal SQL Server. Kombinationsprogram misslyckas eftersom CRM Online kräver OAuth.
  
  Det här felet är ett känt problem och den som har tittat på. Undvik problemet genom att ha en separat fråga för molnkällan och den lokala källan. Använd en ihopkopplings eller tilläggsfråga för att kombinera dem sedan.

**Fel: Datakällan stöds inte.**

**Lösning:** Om du får ett meddelande om en datakälla som inte stöds i inställningarna för Uppdatera schema så kan det betyda: 

* Datakällan stöds inte för närvarande för uppdatering i Power BI. 
* Excel-arbetsboken innehåller en datamodell, endast kalkylbladsdata. Power BI stöder för närvarande bara uppdatering om den överförda Excel-arbetsboken innehåller en datamodell. När du importerar data med Power Query i Excel, måste du välja alternativet för att läsa in data till datamodellen. Det här alternativet innebär att data har importerats till en datamodell. 

**Fel: [Det går inte att kombinera data] &lt;frågedel&gt;/&lt;... &gt; / &lt;... &gt; ansluter till datakällor som har sekretessnivåer som inte kan användas tillsammans. Återskapa den här datakombinationen.**

**Lösning**: Det här felet beror på sekretessbegränsningarna och typerna av datakällor som du använder.

**Fel: Datakällsfel: Det går inte att konvertera värdet ”\[Table\]” till typen Tabell.**

**Lösning**: Det här felet beror på sekretessbegränsningarna och typerna av datakällor som du använder.

**Fel: Otillräckligt med utrymme för den här raden.**

Det här felet uppstår om du har en enskild rad som är större än 4 MB i storlek. Hitta raden från din datakälla och försöka filtrera ut den eller minska storleken för den raden.

## <a name="data-sources"></a>Datakällor
**DataProvider saknas** – den personliga gatewayen är endast 64-bitarsversionen. Det krävs att en 64-bitars version av dataprovidrarna är installerad på samma dator där den personliga gatewayen är installerad. Exempel: Om datakällan i datauppsättningen är Microsoft Access, måste du installera din 64-bitars ACE-provider på samma dator som där du har installerat din personliga gateway.  

>[!NOTE]
>Om du har 32-bitars version Excel kan installera du inte en 64-bitars version ACE-provider på samma dator.

**Windows-autentisering stöds inte för Access-databas** – Power BI stöder för närvarande endast anonym autentisering för Access-databas. Vi arbetar på att aktivera Windows-autentisering för Access-databas.

**Inloggningsfel när du anger autentiseringsuppgifter för en datakälla** -om du får ett felmeddelande som den här när du anger Windows-autentiseringsuppgifter för en datakälla kan du fortfarande kan ha en äldre version av den personliga gatewayen. [Installera den senaste versionen av Power BI Gateway – Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Fel: Inloggningsfel vid val av Windows-autentisering för en datakälla med ACE OLEDB** – Om du får följande felmeddelande när du anger autentiseringsuppgifterna för en datakälla med ACE OLEDB-providern:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Powerbi stöder inte för närvarande Windows-autentisering för en datakälla med hjälp av ACE OLEDB-providern.

**Lösning:** Du kan undvika det här felet, kan du välja **anonym autentisering**. Anonyma autentiseringsuppgifter är lika med Windows-autentiseringsuppgifter för äldre ACE OLEDB-providern.

## <a name="tile-refresh"></a>Paneluppdatering
Om du får ett fel med paneler på instrumentpanelen uppdateras finns i följande artikel.

[Felsöka panelfel](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Verktyg för felsökning
### <a name="refresh-history"></a>Uppdateringshistorik
**Uppdateringshistorik** hjälper dig att se vilka fel har inträffat och ger användbara data om du vill skapa en supportbegäran. Du kan visa både schemalagda och på begäran, uppdateras. Här är hur du kommer till den **uppdateringshistorik**.

1. I Power BI-navigeringsfönstret i **Datauppsättningar** väljer du en datauppsättning &gt;Öppna meny&gt; **Schemalägg uppdatering**.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. I **inställningar för...** väljer **uppdateringshistorik**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Händelseloggar
Flera händelseloggar kan ge information. De första två **Datahanteringsgateway** och **PowerBIGateway**, finns tillgängliga om du är administratör på datorn.  Om du inte är administratör och du använder den personliga gatewayen, visas loggposterna i den **program** log.

**Data Management Gateway**- och **PowerBIGateway**-loggarna finns under **Program- och tjänstloggar**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Fiddlerspårning
[Fiddler](http://www.telerik.com/fiddler) är ett kostnadsfritt verktyg från Telerik som övervakar HTTP-trafik. Du kan se kommunikationen med Power BI-tjänsten från klientdatorn. Den här kommunikationen visas fel och annan relaterad information.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Installationsloggar
Om den **personlig Gateway**, inte kan installeras, visas en länk för att visa installationsloggen. Installationsloggen kan visa information om felet. Dessa loggar är Windows installationsloggar, också kända som MSI-loggar. De kan vara ganska komplexa och svåra att läsa. Vanligtvis visas det resulterande felet finns längst ned, men fastställa orsaken till felet är inte enkelt. Det kan bero på fel i en annan logg eller på ett fel som befinner sig högre upp i loggen.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Eller, går du till din **Temp-mappen** (% temp %) och leta efter filer som börjar med **Power\_BI\_**.

> [!NOTE]
> Om du går till %temp% kan du hamna i en undermapp till temp. Den **Power\_BI\_**  filer finns i roten av temporärkatalogen.  Du kan behöva gå upp en nivå eller två.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Nästa steg
[Konfigurera proxyinställningar för Power BI-gatewayerna](service-gateway-proxy.md)  
[Datauppdatering](refresh-data.md)  
[Power BI Gateway – Personal](service-gateway-personal-mode.md)  
[Felsöka panelfel](refresh-troubleshooting-tile-errors.md)  
[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

