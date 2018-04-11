---
title: Power BI Gateway - Personal
description: Power BI Gateway - Personal
services: powerbi
documentationcenter: ''
author: mgblythe
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 8d047e814eaa7c84ee7e1be20d1f4722c6cb1e56
ms.sourcegitcommit: c80fbf5b12754ce217cb47a17cb5400b1036a8f2
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/06/2018
---
# <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
> [!NOTE]
> Det finns en ny version av den personliga gatewayen för Power BI, det vill säga **lokal datagateway (personligt läge)**. Följande artikel beskriver den tidigare versionen av personlig gateway, **Power BI Gateway - Personal**, som dras tillbaka och slutar fungera från och med den 31 juli 2017. Information om den nya versionen av personlig gateway, inklusive hur du installerar den nya versionen finns i artikeln [**lokal datagateway (personligt läge)**](service-gateway-personal-mode.md).
> 
> 

**Power BI Gateway – Personal** fungerar som en brygga som snabbt och säkert överför data mellan Power BI-tjänsten och lokala datakällor som stöder [uppdatering](refresh-data.md). Den här artikeln är avsedd att ge dig en djup förståelse av hur gatewayen fungerar och om du behöver en gateway. Vi har också samlat denna [användbara video](https://www.youtube.com/watch?v=de58vROLqZI) om din personliga gateway. 

Den installeras och körs som en tjänst på datorn. Som en tjänst körs den med hjälp av ett Windows-konto som du anger under konfigurationen. I vissa fall körs gatewayen som ett program. Vi ska se mer på detta senare.

När Power BI uppdaterar data från en lokal datakälla, säkerställer gatewayen att Power BI-kontot har rätt behörighet för att ansluta till och fråga efter data från källan.

Dataöverföring mellan Power BI och gatewayen säkras via [Azure Service Bus](http://azure.microsoft.com/documentation/services/service-bus/). Service Bus skapar en säker kanal mellan Power BI-tjänsten och din dator. Eftersom gatewayen tillhandahåller den här säkra anslutningen behöver du vanligtvis inte öppna en port i brandväggen.

Innan vi tittar närmare på gatewayen ska vi ta en närmare titt på begreppen som används i Power BI:

En *datauppsättning* är data som överförts till Power BI-tjänsten från en onlinedatakälla eller lokal datakälla. Du kan skapa en datauppsättning när du använder Hämta data för att ansluta till och överföra data. Datauppsättningar visas i fönstret Min arbetsyta i Power BI-arbetsytan i webbläsaren. När du skapar rapporter och fäster paneler till dina instrumentpaneler måste tittar du på data från dina datauppsättningar.

En *datakälla* är den plats som datan i en datauppsättning egentligen kommer från. Det kan vara praktiskt taget allt;:en databas, Excel-kalkylblad, webbtjänst och så vidare. Det är enkelt att skapa ett enkelt arbetsblad med datarader i Excel som kan användas som datakälla. Du kan också använda Power Query eller Power Pivot i Excel för att ansluta till och fråga data från datakällor online eller lokalt – allt i samma arbetsbok. Med Power BI Desktop använder du Hämta data för att ansluta till och fråga data från datakällor online eller lokalt.

Den personliga gatewayen har installerats via en lokal datagateway. Du kan hämta den på [Power BI Gateway-sidan](https://powerbi.microsoft.com/gateway/).

## <a name="do-i-need-a-gateway"></a>Behöver jag en gateway?
Innan du installerar en gateway är det viktigt att veta om du verkligen behöver en. Det beror på dina datakällor:

### <a name="on-premises-data-sources"></a>Lokala datakällor
En personlig gateway *krävs* för att kunna uppdatera datauppsättningar som hämtar data från en lokal datakälla som stöds i din organisation.

UPPDATERA NU och SCHEMALÄGG UPPDATERING stöds i gatewayen för datakällor som har hämtats från:

* Arbetsböcker för Microsoft Excel 2013 (eller senare) där Power Query eller Power Pivot används för att ansluta till och fråga efter data från en lokal datakälla. Alla lokala datakällor som visas i Hämta externa data i Power Query eller Power Pivot förutom Hadoop-filer (HDFS) och Microsoft Exchange.
* Microsoft Power BI Desktop-filer där Hämta data används för att ansluta till och fråga data från en lokal datakälla som stöds. Alla lokala datakällor som visas i Hämta data, stöd för uppdatera, förutom Hadoop-filer (HDFS) och Microsoft Exchange.

### <a name="online-data-sources"></a>Onlinedatakällor
En gateway *krävs endast* om du använder funktionen [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx). I andra fall krävs en gateway *inte* för att uppdatera datauppsättningar som hämtar data från en online-datakälla.

> [!NOTE]
> Om du använder funktionen [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx), behöver du en gateway om du har återpublicerat datauppsättningen eller rapporten efter 18 november 2016.
> 
> 

UPPDATERA NU och SCHEMALÄGG UPPDATERING stöds utan gateway för datakällor som har hämtats från:

* Innehållspaket från online-datakällor (innehållspaket\\tjänster). Som standard uppdateras datauppsättningar från innehållspaket automatiskt en gång om dagen, men du kan också uppdatera manuellt eller konfigurera ett uppdateringsschema.
* Arbetsböcker för Microsoft Excel 2013 (eller senare) där Power Query eller Power Pivot används för att ansluta till och fråga efter data från en onlinedatakälla.
* Microsoft Power BI Desktop-filer där Hämta data används för att ansluta till och fråga data från en onlinedatakälla som stöds.

**Fråga:** vad händer om min Excel-arbetsbok eller Power BI Desktop-fil hämtar data från både online- och lokala datakällor?

**Svar:** en gateway *krävs*. Du måste installera och konfigurera en gateway för att uppdatera data från dina lokala datakällor.

**Fråga:** vad händer om Excel-arbetsboken endast har datarader som jag har skrivit in? **

**Svar:** en gateway *krävs* inte. Du behöver bara installera och konfigurera en gateway om arbetsboken använder Power Query eller Power Pivot för att fråga efter och läsa in data till datamodellen från en lokal datakälla

## <a name="setting-up-a-gateway-for-the-first-time"></a>Konfigurera en gateway för första gången
Konfigurera en gateway för första gången är en process med tre steg:

1. Ladda ned och installera en gateway
2. Konfigurera en gateway
3. Ansluta till datakällor i Power BI

Låt oss ta en närmare titt på varje steg.

### <a name="download-and-install-a-gateway"></a>Ladda ned och installera en gateway
> [!NOTE]
> Det finns en ny version av den personliga gatewayen för Power BI, det vill säga **lokal datagateway (personligt läge)**. Den här artikeln beskriver den tidigare versionen av personlig gateway, **Power BI Gateway – Personal**, som ska tas bort och slutar fungera från och med den 31 juli 2017. Information om den nya versionen av personlig gateway, inklusive hur du installerar den nya versionen finns i artikeln [**lokal datagateway (personligt läge)**](service-gateway-personal-mode.md).
> 
> 

Du uppmanas att installera en gateway när du klickar på UPPDATERA NU eller SCHEMALÄGG UPPDATERING för första gången för en datauppsättning som stöds. Eller, om du vill hämta gatewayen, väljer du **Datagateway** under menyn Hämtningar. Ladda ned den [lokala datagatewayen](http://go.microsoft.com/fwlink/?LinkID=820925).

Du ska välja **Personlig gateway** i stället för **Lokal datagateway** för att hämta en gateway som är för dig själv.

Det är lätt att installera en gateway. Du väljer en plats för att installera på och läser och godkänner licensavtalet precis som med alla andra program. Det finns dock ett par saker som är viktiga att veta. Framför allt, vilken sorts dator du installerar gatewayen på och typen av konto som du använder för att logga in på Windows från den datorn.

> [!NOTE]
> Gatewayen måste ha åtkomst till datakällan. Om din personliga dator inte kan ansluta till datakällan kan du behöva installera en [lokal datagateway](service-gateway-onprem.md) på en dator som har åtkomst till datakällan. Ett exempel på detta är att installera SQL Server på en virtuell dator (VM) på Azure. Din persondator har kanske inte åtkomst till den virtuella datorn. Du kan installera den lokala datagatewayen på den virtuella datorn i stället och konfigurera en datakälla i Power BI-tjänsten.
> 
> 

### <a name="computer-type"></a>Datortyp
Typen av dator som du installerar en gateway på är viktigt.

> [!NOTE]
> En personlig gateway stöds bara på 64-bitars Windows-operativsystem.
> 
> 

På en bärbar dator - för att en schemalagd uppdatering ska ske måste gatewayen vara igång. Bärbara datorer är vanligtvis avstängda eller i viloläge mer än de används. Om du installerar din gateway på en bärbar dator måste du ange schemalagda uppdateringstider för när den bärbara datorn körs. Annars kommer uppdateringen inte att påbörjas igen förrän nästa schemalagda uppdateringstid.

På en stationär dator – inte många problem här. Se bara till att datorn och gatewayen körs vid dina schemalagda uppdateringstider. Många stationära datorer försätts i viloläge och då kan inte schemalagda uppdateringar köras.

När du har installerat en gateway behöver du inte installera en annan. En gateway räcker för valfritt antal datauppsättningar som stöds. Du behöver inte heller installera gatewayen på samma dator som du överför din arbetsbok och dina Power BI Desktop-filer från. Här är ett exempel: Anta att du har en Excel-arbetsbok som ansluter till en SQL Server-datakälla i din organisation. Du använde Hämta data i Power BI för att ladda upp arbetsboken från din bärbara dator. Du har också en stationär dator som körs ständigt och du har installerat och konfigurerat en gateway på den datorn. Du har loggat in till dina datakällor i Power BI och du har ställt in ett uppdateringsschema för datauppsättningen.  När en schemalagd uppdateringstid inträffar upprättar Power BI en säker anslutning till gatewayen som har installerats på datorn. Den ansluter säkert till datakällorna för att hämta uppdateringar. För uppdatering sker ingen kommunikation med den ursprungliga arbetsboken som du överförde från din bärbara dator.

> [!NOTE]
> Du kan installera en personlig och företagsgateway på samma dator.
> 
> 

### <a name="windows-account"></a>Windows-konto
När du installerar en gateway måste du vara inloggad på datorn med ditt Windows-konto. Typen av behörigheter som Windows-kontot har påverkar hur gatewayen installeras och hur den körs i Windows.

När du är inloggad i Windows:

|  | Med administratörsbehörighet | Utan administratörsbehörighet |
| --- | --- | --- |
| **Power BI Gateway – Personal körs som** |Tjänst |Program |
| **Schemalagd uppdatering** |Så länge datorn och gateway-tjänsten körs behöver du inte vara inloggad vid den schemalagda uppdateringstiden. |Du måste vara inloggad på datorn vid den schemalagda uppdateringstiden. |
| **Ändra lösenordet för Windows-kontot** |Du måste ändra lösenordet i gateway-tjänsten. Om kontolösenordet som används av gatewayen inte längre är giltigt, misslyckas uppdateringen. |Gatewayen körs alltid med det kontot och lösenordet som du har använt för den aktuella sessionen. Om du inte är inloggad på Windows kommer inte gatewayen att köras varmed uppdateringen misslyckas. |

### <a name="configure-the-gateway"></a>Konfigurera en gateway
När installationsguiden är klar uppmanas du att starta konfigurationsguiden. Det är lätt att konfigurera en gateway. Du måste logga in på Power BI från guiden. Detta är nödvändigt för att guiden ska upprätta en anslutning med Power BI-kontot i Power BI-tjänsten.

Om du är inloggad till Windows med ett konto med administratörsbehörighet uppmanas du att ange dina autentiseringsuppgifter för Windows-kontot. Du kan ange ett annat Windows-konto, men kom ihåg att behörigheterna bestämmer hur gatewayen körs. Gatewaytjänsten körs med det här kontot.

### <a name="sign-in-to-data-sources"></a>Logga in på datakällor
När guiden har slutförts och din gateway är igång måste du ange autentiseringstyp och logga in på var och en av din datauppsättnings datakällor. Det här steget slutförs i Power BI.

![](media/personal-gateway/pg_dataset_settings_signin.png)

Du behöver endast ange en autentiseringstyp och logga in på en datakälla en gång. Du loggar in från området **Hantera datakällor** på inställningsskärmen för datauppsättningen. Om du har flera datakällor måste du logga in på var och en. Gatewayen anger en standardautentisering beroende på datakällan. I de flesta fall är det Windows-autentisering. I vissa fall kan datakällan dock i vissa fall kan kräva olika autentiseringstyper. Om du är osäker, kontrollera med din administratör för datakällan.

## <a name="up-and-running"></a>Nu har du kommit igång!
När din gateway är igång kan du kan klicka på SCHEMALÄGG UPPDATERING för en datauppsättning för att visa datauppsättningens inställningssida.

![](media/personal-gateway/pg_awintsales_settings.png)

Den här sidan visas:

1. Uppdateringsstatus – visar att uppdateringen lyckades och nästa schemalagda uppdateringstid.
2. **Gateway** -visar om en gateway är installerad och online. Om en gateway har installerats men inte är online, har Hantera datakällor och Schemalägg uppdatering inaktiverats.
3. **Hantera datakällor** -visar datakällor som datauppsättningen ansluter till. Du kan logga in eller ändra autentiseringstyp. Du bara behöver logga in till varje datakälla en gång.
4. **Schemalägg uppdatering** – du kan konfigurera ett uppdateringsschema här. De här inställningarna kommer att inaktiveras om gatewayen inte är online.
5. Aviseringar om misslyckad uppdatering – det här alternativet är markerat som standard och skickar ett e-postmeddelande till dig om en schemalagd uppdatering misslyckas.

## <a name="updating-your-windows-account-password"></a>Uppdatera lösenordet för Windows-kontot
Om du har loggat in på datorn med ett Windows-konto med administratörsbehörighet när du har installerade din gateway, körs den som en tjänst med Windows-kontot som du angav i guiden. Det här är ofta samma Windows-konto som du loggar in på datorn med. När du ändrar lösenordet för Windows-kontot kan du också behöva ändra det i gatewayen, annars kan tjänsten kanske inte köras och uppdateringen misslyckas. Välj ikonen för personlig gateway i Aktivitetsfältet i Windows-skrivbordet eller i appar om du vill ändra lösenordet för Windows-kontot för gateway.

![](media/personal-gateway/pg_programicon.png)

Härifrån kan du uppdatera ditt lösenord och kontrollera statusen för din gateway-anslutning.

![](media/personal-gateway/pg_credentials.png)

## <a name="ports"></a>Portar
Gatewayen kommunicerar via utgående portar: TCP 443 (standard), 5671, 5672, 9350 till 9354.  Gatewayen behöver inte några ingående portar.

| Domännamn | Utgående portar | Beskrivning |
| --- | --- | --- |
| *.powerbi.com |443 |HTTPS |
| *.analysis.windows.net |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |
| *.servicebus.windows.net |5671–5672 |Advanced Message Queuing Protocol (AMQP) |
| *.servicebus.windows.net |443, 9350–9354 |Lyssnare på Service Bus Relay via TCP (kräver 443 för att hämta token för åtkomstkontroll) |
| *.frontend.clouddatahub.net |443 |HTTPS |
| *.core.windows.net |443 |HTTPS |
| login.microsoftonline.com |443 |HTTPS |
| *.login.windows.net |443 |HTTPS |

Om du behöver vitlista IP-adresser i stället för domänerna kan du hämta och använda listan över IP-adressintervall för Microsoft Azure-Datacenter. [Hämta](https://www.microsoft.com/download/details.aspx?id=41653)

## <a name="next-steps"></a>Nästa steg
[Lokala datagatewayar (personligt läge) – den nya versionen av den personliga gatewayen](service-gateway-personal-mode.md)
[Konfigurera proxyinställningar för den Power BI-gatewayen](service-gateway-proxy.md)  
[Power BI Premium](service-premium.md)

Har du fler frågor? [Fråga Power BI Community](http://community.powerbi.com/)

