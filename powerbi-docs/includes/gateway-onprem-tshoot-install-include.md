## <a name="update-to-the-latest-version"></a>Uppdatera till den senaste versionen
Flera problem kan uppstå om gatewayversionen är föråldrad.  Det är en allmänt bra vana att kontrollera att du har den senaste versionen.  Om du inte har uppdaterat din gateway på en månad eller längre, bör du överväga att installera den senaste versionen av gatewayen och se om du kan återskapa problemet.

## <a name="common-issues"></a>Vanliga problem
Här följer några vanliga problem och lösningar som har hjälpt många kunder i miljöer med begränsad internetåtkomst.

<iframe width="560" height="315" src="https://www.youtube.com/embed/-t7RO6mHATI?showinfo=0" frameborder="0" allowfullscreen></iframe>

### <a name="authentication-to-proxy-server"></a>Autentisering till proxyservern
Proxyservern kan kräva autentisering från ett domänanvändarkonto. Som standard använder gatewayen ett tjänst-SID för att logga in på Windows-tjänsten. Det kan hjälpa att ändra inloggningsanvändaren till en domänanvändare. För mer information, se [Ändra gatewayens tjänstkonto till en domänanvändare](../service-gateway-proxy.md#changing-the-gateway-service-account-to-a-domain-user).

### <a name="your-proxy-only-allows-ports-80-and-443-traffic"></a>Proxyservern tillåter endast trafik över portarna 80 och 443
Vissa proxyservrar begränsar trafiken till enbart portarna 80 och 443. Som standard sker kommunikationen till Azure Service Bus via andra portar än 443.

Du kan tvinga gatewayen att kommunicera med Azure Service Bus med HTTPS i stället för direkt TCP. Du kommer att behöva ändra *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* fil. Ändrar du värdet från `AutoDetect` till `Https`. Den här filen finns som standard på *C:\Program Files\On-premises data gateway*.

```
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="installation"></a>Installation
### <a name="error-failed-to-add-user-to-group---2147463168---pbiegwservice---performance-log-users---"></a>Fel: Det gick inte att lägga till användaren i gruppen.  (-2147463168 PBIEgwService Performance Log Users )
Du får det här felmeddelandet om du försöker installera gatewayen på en domänkontrollant. Distribution på en domänkontrollant stöds inte. Du måste distribuera en gateway på en dator som inte är en domänkontrollant.

