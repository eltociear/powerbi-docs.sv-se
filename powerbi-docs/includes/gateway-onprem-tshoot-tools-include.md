## <a name="tools-for-troubleshooting"></a>Verktyg för felsökning
<a name="logs" />

### <a name="collecting-logs-from-the-gateway-configurator"></a>Samla in loggar från gatewayens konfigurator
Det finns flera loggar som du kan samla in för gatewayen och du bör alltid börja med loggarna. Det enklaste sättet att samla in loggar på när du har installerat gatewayen är via användargränssnittet. I användargränssnittet för den **lokala datagatewayen** väljer du **Diagnostik** och sedan länken **Exportloggar** längst ned på sidan, enligt följande bild.

![On-prem-data-gateway-UI-logs](./media/gateway-onprem-tshoot-tools-include/gateway-onprem-UI-logs.png)

**Installationsloggar**

    %localappdata%\Temp\On-premises_data_gateway_*.log

**Konfigurationsloggar**

    %localappdata%\Microsoft\On-premises Data Gateway\GatewayConfigurator*.log

**Tjänstloggar för lokal datagateway**

    C:\Users\PBIEgwService\AppData\Local\Microsoft\On-premises Data Gateway\Gateway*.log

### <a name="event-logs"></a>Händelseloggar
Händelseloggar för den **lokala datagatewaytjänsten** finns under **Program- och tjänstloggar**.

![On-prem-data-gateway-event-logs](./media/gateway-onprem-tshoot-tools-include/on-prem-data-gateway-event-logs.png)

<a name="fiddler" />

### <a name="fiddler-trace"></a>Fiddlerspårning
[Fiddler](http://www.telerik.com/fiddler) är ett kostnadsfritt verktyg från Telerik som övervakar HTTP-trafik.  Du kan se trafiken från och till med Power BI-tjänsten från klientdatorn. Här visas fel och annan relaterad information.

![](media/gateway-onprem-tshoot-tools-include/fiddler.png)

