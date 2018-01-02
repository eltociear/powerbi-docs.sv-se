## <a name="firewall-or-proxy"></a>Brandvägg eller proxy
Mer information om att tillhandahålla proxyinformation för din gateway finns i [Konfigurera proxyinställningar för Power BI-gatewayer](../service-gateway-proxy.md).

Du kan kontrollera om din brandvägg eller proxy blockerar anslutningar genom att köra [Test-NetConnection](https://technet.microsoft.com/library/dn372891.aspx) från en PowerShell-kommandotolk. Det här kommandot testar anslutningen till Azure Service Bus. Det testar endast nätverksanslutningen och har inte något att göra med molnservertjänsten eller gatewayen. Det hjälper dig att avgöra om din dator verkligen kan få åtkomst till Internet.

    Test-NetConnection -ComputerName watchdog.servicebus.windows.net -Port 9350

> [!NOTE]
> Test-NetConnection är bara tillgängligt i Windows Server 2012 R2 och senare. Det finns också i Windows 8.1 och senare. Du kan använda Telnet för tidigare OS-versioner om du vill testa portanslutningen.
> 
> 

Resultatet bör se ut som nedan. Skillnaden finns i TcpTestSucceeded. Om **TcpTestSucceeded** inte är *sant* kan det finnas en brandvägg som blockerar dig.

    ComputerName           : watchdog.servicebus.windows.net
    RemoteAddress          : 70.37.104.240
    RemotePort             : 5672
    InterfaceAlias         : vEthernet (Broadcom NetXtreme Gigabit Ethernet - Virtual Switch)
    SourceAddress          : 10.120.60.105
    PingSucceeded          : False
    PingReplyDetails (RTT) : 0 ms
    TcpTestSucceeded       : True

Om du vill vara grundlig ersätter du värdena **ComputerName** och **Port** med de som anges för [portarna](../service-gateway-onprem.md#ports)

Brandväggen kan även blockera anslutningarna som Azure Service Bus upprättar till Azure-datacentra. Om så är fallet kan du godkänna (avblockera) IP-adresserna för din region för dessa datacentra. Du kan hämta en lista med Azures IP-adresser [här](https://www.microsoft.com/download/details.aspx?id=41653).

