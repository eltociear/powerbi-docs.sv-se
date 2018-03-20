## <a name="general"></a>Allmänt
**Fråga:** Vad kallas själva Windows-tjänsten?  
**Svar:** Gatewayen kallas för Lokal datagateway i Tjänster

**Fråga:** Vilka är kraven för gatewayen?  
**Svar:** Ta en titt på avsnittet med krav i den huvudsakliga [gatewayartikeln](../service-gateway-onprem.md).

**Fråga:** Vilka datakällor stöds i gatewayen?  
**Svar:** Se tabellen med datakällor i den huvudsakliga [gatewayartikeln](../service-gateway-onprem.md).

**Fråga:** Behöver jag en gateway för molndatakällor som Azure SQL Database?  
**Svar:** Nej! Tjänsten kommer att kunna ansluta till datakällan utan en gateway.

**Fråga:** Finns det några inkommande anslutningar till gatewayen från molnet?  
**Svar:** Nej. Gatewayen använder utgående anslutningar till Azure Service Bus.

**Fråga:** Vad händer om jag blockerar utgående anslutningar? Vad måste jag i så fall öppna?  
**Svar:** Se [listan med portar](../service-gateway-onprem.md#ports) och värdar som används av gatewayen.

**Fråga:** Måste gatewayen vara installerad på samma dator som datakällan?  
**Svar:** Nej. Gatewayen ansluter till datakällan med anslutningsinformationen som har angetts. Tänk på en gateway som ett klientprogram i detta avseende. Den behöver bara kunna ansluta till servernamnet som har angetts.

**Fråga:** Vad är svarstiden för att köra frågor till en datakälla från gatewayen? Vilken är den bästa arkitekturen?  
**Svar:** Vi rekommenderar att du har en gateway som finns nära datakällan för att undvika nätverksfördröjning. Om du kan installera gatewayen på den faktiska datakällan minimeras svarstiden. Du kan även använda datacentra. Om tjänsten t.ex. använder ett datacenter för västra USA och du har SQL Server på en virtuell Azure-dator, vill du sannolikt ha den virtuella Azure-datorn i västra USA också. Detta minimerar svarstiden och undviker onödiga avgifter för den virtuella Azure-datorn.

**Fråga:** Finns det några krav på bandbredd i nätverket?  
**Svar:** Vi rekommenderar att ha ett bra dataflöde för nätverksanslutningen. Varje miljö är annorlunda och mängden data som skickas påverkar resultaten. ExpressRoute kan bidra till att garantera en nivå för dataflödet mellan den lokala platsen och Azure-datacentret.

Du kan använda tredjepartsverktyget [Azure Speed Test-appen](http://azurespeedtest.azurewebsites.net/) till att mäta ditt dataflöde.

**Fråga:** Kan gatewayen köra Windows-tjänsten med ett Azure Active Directory-konto?  
**Svar:** Nej. Windows-tjänsten måste ha ett giltigt Windows-konto. Som standard körs den med tjänst-SID *NT SERVICE\PBIEgwService*.

**Fråga:** Hur skickas resultaten tillbaka till molnet?  
**Svar:** Detta sker via Azure Service Bus. Mer information finns [här](../service-gateway-onprem.md#how-the-gateway-works).

**Fråga:** Var lagras mina autentiseringsuppgifter?  
**Svar:** De autentiseringsuppgifter som du anger för en datakälla lagras krypterat i gatewaymolntjänsten. Autentiseringsuppgifterna dekrypteras i den lokala gatewayen.

**Fråga:** Kan jag placera gatewayen i ett perimeternätverk (även kallat DMZ, demilitariserad zon och kontrollerat undernät)?  
**Svar:** En gateway kräver anslutning till datakällan. Om datakällan inte går att nå i ditt perimeternätverk, kan gatewayen kanske inte ansluta till den. Exempelvis kanske inte SQL Server finns i perimeternätverket. Och du kan inte ansluta till SQL Server från perimeternätverket. Om du placerade gatewayen i perimeternätverket skulle det inte gå att nå SQL Server.

**Fråga:** Går det att tvinga gatewayen att använda HTTPS-trafik med Azure Service Bus i stället för TCP?  
**Svar:** Ja. Även om detta avsevärt minskar prestandan. Du kommer att behöva ändra filen *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Du kan ändra värdet från `AutoDetect` till `Https`. Den här filen finns som standard på *C:\Program\Lokal datagateway*.

**Fråga:** Behöver jag godkänna IP-listan för Azure Datacenter? Var hittar jag listan?  
**Svar:** Om du blockerar utgående IP-trafik kan du behöva godkänna IP-listan för Azure Datacenter. För närvarande kommer gatewayen kommunicera med Azure Service Bus via IP-adressen, tillsammans med det fullständiga domännamnet. IP-listan för Azure Datacenter uppdateras varje vecka. Du kan ladda ned [IP-listan för Microsoft Azure Datacenter](https://www.microsoft.com/download/details.aspx?id=41653).

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>Hög tillgänglighet och haveriberedskap
**Fråga:** Finns det några planer på att aktivera scenarier med hög tillgänglighet med gatewayen?  
**Svar:** Ja, det här är en del av de framtida funktioner som Power BI-teamet arbetar med. Håll koll på [Power BI-bloggen](https://powerbi.microsoft.com/blog/) för ytterligare uppdateringar om funktionen.

**Fråga:** Vilka alternativ är tillgängliga för haveriberedskap?  
**Svar:** Du kan använda återställningsnyckeln till att återställa eller flytta en gateway. När du installerar gatewayen anger du återställningsnyckeln.

**Fråga:** Vad är fördelen med återställningsnyckeln?  
**Svar:** Den gör det möjligt att migrera eller återställa gatewayinställningarna. Den används också till haveriberedskap.

## <a name="troubleshooting"></a>Felsökning
**Fråga:** Var finns gatewayloggarna?  
**Svar:** Se verktygsavsnittet i [felsökningsartikeln](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting).

**Fråga:** Hur kan jag se vilka frågor som skickas till den lokala datakällan?  
**Svar:** Du kan aktivera frågespårning.  Detta inkluderar de frågor som skickas. Kom ihåg att ändra tillbaka till det ursprungliga värdet efter felsökningen. Om frågespårning är aktiverat blir loggarna större.

Du kan också använda de verktyg som finns i datakällan för att spåra frågor. Du kan till exempel använda Extended Events eller SQL Profiler för SQL Server och Analysis Services.

