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
ms.openlocfilehash: 7827ce359022eccfb75798b08da164b7504c84df
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68271838"
---
# <a name="troubleshooting-power-bi-gateway---personal"></a>Felsöka Power BI Gateway – Personal

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

I följande avsnitt beskrivs några vanliga problem som kan uppstå när du använder Power BI Gateway – Personal.

## <a name="update-to-the-latest-version"></a>Uppdatera till den senaste versionen

Den aktuella versionen av gatewayen för personligt bruk är **Lokal datagateway (personlig)** . Uppdatera din installation om du vill använda den här versionen.

Ett stort antal problem kan uppstå om gatewayversionen är inaktuell.  Det är en allmänt bra vana att kontrollera att du har den senaste versionen. Om du inte har uppdaterat gatewayen på en månad eller längre bör du överväga att installera den senaste versionen av gatewayen. Kontrollera sedan om du kan återskapa problemet.

## <a name="installation"></a>Installation
**Personlig gateway är 64-bitars** – Om din dator är 32-bitars kan du inte installera den personliga gatewayen. Operativsystemet måste vara en 64-bitars version. Installera en 64-bitars version av Windows eller installera den personliga gatewayen på en 64-bitars dator.

**Den personliga gatewayen kan inte installeras som tjänst trots att du är lokal administratör på datorn** – Installationen kan misslyckas om användaren finns i datorns lokala administratörsgrupp men grupprincipen inte tillåter det aktuella användarnamnet att logga in som en tjänst. Börja med att kontrollera om grupprincipen tillåter att en användare loggar in som en tjänst. Vi arbetar på att lösa problemet. [Läs mer](https://technet.microsoft.com/library/cc739424.aspx)

**Tidsgränsen uppnåddes** – Det här meddelandet är vanligt om den dator (fysisk eller virtuell dator) som du installerar den personliga gatewayen på har en processor med bara en kärna. Stäng alla program och inaktivera alla processer som inte behövs och försök installera igen.

**Data Management Gateway eller Analysis Services Connector kan inte installeras på samma dator som den personliga gatewayen** – Om du redan har Analysis Services Connector eller Data Management Gateway installerat måste du först avinstallera anslutningsprogrammet (Connector) eller gatewayen. Försök sedan att installera den personliga gatewayen.

> [!NOTE]
> Om det uppstår problem under installationen kan installationsloggarna innehålla information som kan hjälpa dig att lösa det. Mer information finns i [Installationsloggar](#SetupLogs).
> 
> 

 **Proxykonfiguration** – Du kan stöta på problem med att konfigurera din personliga gateway om miljön behöver användning av en proxy. Mer information om hur du konfigurerar proxyinformation finns i [Konfigurera proxyinställningar för den lokala datagatewayen](/data-integration/gateway/service-gateway-proxy).

## <a name="schedule-refresh"></a>Uppdatera schema
**Fel: Autentiseringsuppgiften som lagras i molnet saknas.**

Du kan få detta fel i inställningarna för \<datamängden\> om du har en schemalagd uppdatering och sedan avinstallerat och ominstallerat den personliga gatewayen. När du avinstallerar en personlig gateway tas datakällans autentiseringsuppgifter för en datamängd som har konfigurerats för uppdatering bort från Power BI-tjänsten.

**Lösning:** I Power BI så går du till uppdateringsinställningarna för en datauppsättning. I Hantera datakällor väljer du **Redigera autentiseringsuppgifter** för alla datakällor med fel och loggar in på datakällan igen.

**Fel: De autentiseringsuppgifter som anges för datauppsättningen är ogiltiga. Uppdatera autentiseringsuppgifterna genom en uppdatering eller i dialogrutan Inställningar för datakälla om du vill fortsätta.**

**Lösning**: Om du får ett meddelande om autentiseringsuppgifter så kan det innebära:

* Kontrollera att användarnamn och lösenord för inloggning till datakällor är aktuella. Gå till datauppsättningens uppdateringsinställningar i Power BI. I Hantera datakällor väljer du **Redigera autentiseringsuppgifter** för att uppdatera autentiseringsuppgifterna för datakällan.
* Kombinationsprogram mellan en molnkälla och en lokal källa misslyckas i en enskild fråga att uppdateras i den personliga gatewayen om en av källorna använder OAuth för autentisering. Ett exempel på detta problem är ett kombinationsprogram mellan CRM Online och en lokal SQL Server. Kombinationsprogrammet misslyckas eftersom CRM Online kräver OAuth.
  
  Detta fel är ett känt problem som håller på att utredas. Undvik problemet genom ha en separat fråga för molnkällan och den lokala källan. Använd sedan en sammanfognings- eller tilläggsfråga för att kombinera dem.

**Fel: Datakällan stöds inte.**

**Lösning:** Om du får ett meddelande om en datakälla som inte stöds i inställningarna för Uppdatera schema så kan det betyda: 

* Datakällan stöds för närvarande inte för uppdatering i Power BI. 
* Excel-arbetsboken innehåller inte en datamodell, endast kalkylbladsdata. Power BI stöder för närvarande bara uppdatering om den överförda Excel-arbetsboken innehåller en datamodell. När du importerar data med Power Query i Excel, måste du välja alternativet för att läsa in data till datamodellen. Det här alternativet garanterar att data importeras till en datamodell. 

**Fel: [Det går inte att kombinera data] &lt;frågedel&gt;/&lt;…&gt;/&lt;…&gt; ansluter till datakällor som har sekretessnivåer som inte kan användas tillsammans. Återskapa den här datakombinationen.**

**Lösning**: Det här felet beror på begränsningarna av sekretessnivå och de typer av datakällor som du använder.

**Fel: Datakällsfel: Det går inte att konvertera värdet ”\[Table\]” till typen Tabell.**

**Lösning**: Det här felet beror på begränsningarna av sekretessnivå och de typer av datakällor som du använder.

**Fel: Otillräckligt med utrymme för den här raden.**

Det här felet inträffar om du har en enskild rad som är större än 4 MB. Leta upp raden från din datakälla och försöka filtrera bort den eller minska dess storlek.

## <a name="data-sources"></a>Datakällor
**Dataprovider saknas** – Den personliga gatewayen finns bara som 64-bitars version. Det krävs att en 64-bitars version av dataprovidrarna är installerad på samma dator där den personliga gatewayen är installerad. Exempel: Om datakällan i datauppsättningen är Microsoft Access, måste du installera din 64-bitars ACE-provider på samma dator som där du har installerat din personliga gateway.  

>[!NOTE]
>Om du har 32-bitars version av Excel kan du inte installera en 64-bitars version av ACE-provider på samma dator.

**Windows-autentisering stöds inte för Access-databas** – Power BI stöder för närvarande endast anonym autentisering för Access-databas. Vi arbetar med att aktivera Windows-autentisering för Access-databas.

**Inloggningsfel när du anger autentiseringsuppgifter för en datakälla** – Om du får ett fel som liknar detta när du anger Windows-autentiseringsuppgifter för en datakälla kan det hända att du fortfarande har en äldre version av den personliga gatewayen. [Installera den senaste versionen av Power BI Gateway – Personal](https://powerbi.microsoft.com/gateway/).

  ![](media/service-admin-troubleshooting-power-bi-personal-gateway/pbi_pg_credentialserror.jpg.png)

**Fel: Inloggningsfel vid val av Windows-autentisering för en datakälla med ACE OLEDB** – Om du får följande felmeddelande när du anger autentiseringsuppgifterna för en datakälla med ACE OLEDB-providern:

![](media/service-admin-troubleshooting-power-bi-personal-gateway/aceoledberror.png)

Power BI stöder för närvarande inte Windows-autentisering för en datakälla med användning av ACE OLEDB-provider.

**Lösning:** Du kan kringgå det här felet genom att välja **Anonym autentisering**. För en äldre ACE OLEDB-provider är anonyma autentiseringsuppgifter likvärdiga med Windows-autentiseringsuppgifter.

## <a name="tile-refresh"></a>Paneluppdatering
Se följande artikel om det uppstår ett fel med uppdateringen av paneler på instrumentpanelen.

[Felsöka panelfel](refresh-troubleshooting-tile-errors.md)

## <a name="tools-for-troubleshooting"></a>Verktyg för felsökning
### <a name="refresh-history"></a>Uppdateringshistorik
**Uppdateringshistorik** hjälper dig att se vilka fel som har inträffat och ger användbara data om du behöver skapa en supportbegäran. Du kan visa både schemalagda uppdateringar och sådana som görs på begäran. Så här går du till **Uppdateringshistorik**.

1. I Power BI-navigeringsfönstret i **Datauppsättningar** väljer du en datauppsättning &gt;Öppna meny&gt; **Schemalägg uppdatering**.
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh.png)
1. I **Inställningar för...** väljer du **Uppdateringshistorik**.  
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/scheduled-refresh-2.png)
   
   ![](media/service-admin-troubleshooting-power-bi-personal-gateway/refresh-history.png)

### <a name="event-logs"></a>Händelseloggar
Det finns flera händelseloggar som kan ge information. De två första, **Data Management Gateway** och **PowerBIGateway**, finns tillgängliga om du är administratör på datorn.  Om du inte är administratör, och du använder den personliga gatewayen, visas loggposterna i **programloggen**.

**Data Management Gateway**- och **PowerBIGateway**-loggarna finns under **Program- och tjänstloggar**.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/event-logs.png)

### <a name="fiddler-trace"></a>Fiddlerspårning
[Fiddler](http://www.telerik.com/fiddler) är ett kostnadsfritt verktyg från Telerik som övervakar HTTP-trafik. Du kan se kommunikationen med Power BI-tjänsten från klientdatorn. Den här kommunikationen kan visa fel och annan relaterad information.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/fiddler.png)

<a name="SetupLogs"></a>

### <a name="setup-logs"></a>Installationsloggar
Om den **personliga gatewayen** misslyckas med installationen visas en länk där du kan se installationsloggen. Installationsloggen innehåller information om felet. De här loggarna är Windows-installationsloggar, som även kallas MSI-loggar. De kan vara ganska komplexa och svåra att läsa. Vanligtvis visas det resulterande felet längst ned, men det är inte helt enkelt att ta reda på orsaken till felet. Det kan bero på fel i en annan logg eller på ett fel som befinner sig högre upp i loggen.

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-log.png)

Eller så kan du gå till **Temp-mappen** (%temp%) och leta efter filer som börjar med **Power\_BI\_** .

> [!NOTE]
> Om du går till %temp% kan du hamna i en undermapp till temp. **Power\_BI\_** -filerna finns i roten av tempkatalogen.  Du kan behöva gå upp en nivå eller två.
> 
> 

![](media/service-admin-troubleshooting-power-bi-personal-gateway/setup-logs2.png)

## <a name="next-steps"></a>Nästa steg
[Konfigurera proxyinställningar för den lokala datagatewayen](/data-integration/gateway/service-gateway-proxy)  
[Datauppdatering](refresh-data.md)  
[Power BI Gateway – Personal](service-gateway-personal-mode.md)  
[Felsöka panelfel](refresh-troubleshooting-tile-errors.md)  
[Felsöka den lokala datagatewayen](service-gateway-onprem-tshoot.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

