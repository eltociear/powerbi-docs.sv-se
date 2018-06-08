## <a name="requirements"></a>Krav
**Minimikrav**

* .NET 4.6 Framework
* 64-bitars version av Windows 7 eller Windows Server 2008 R2 (eller senare)

**Rekommenderas:**

* Processor med 8 kärnor
* 8 GB minne
* 64-bitarsversionen av Windows 2012 R2 (eller senare)

**Att tänka på:**

* Gatewayen kan inte installeras på en domänkontrollant.
* Om du planerar att använda Windows-autentisering måste du installera gatewayen på en dator som är medlem i samma Active Directory-miljö som datakällorna.
* Du bör inte installera en gateway på en dator eller en bärbar dator, som kan stängas av, försättas i viloläge eller frånkopplas från Internet, eftersom en gateway inte kan köras under dessa omständigheter. Dessutom kan gatewayens prestanda vara sämre i ett trådlöst nätverk.
* Analysis Services krävs inte för att använda gatewayen. Du kan använda gatewayen för att ansluta till en Analysis Services-datakälla.

