---
title: Använda Kerberos för enkel inloggning (SSO) till SAP BW med hjälp av gx64krb5
description: Konfigurera din SAP BW-server till att aktivera enkel inloggning från Power BI-tjänsten med hjälp av gx64krb5
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 08/01/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 5dd31dc4333dc03100370100e16eadab6012c1f0
ms.sourcegitcommit: 7a0ce2eec5bc7ac8ef94fa94434ee12a9a07705b
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2019
ms.locfileid: "71106341"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>Använda Kerberos för enkel inloggning (SSO) till SAP BW med hjälp av gx64krb5

I den här artikeln beskrivs hur du konfigurerar din SAP BW-server för att aktivera enkel inloggning från Power BI-tjänsten med hjälp av gx64krb5.

> [!NOTE]
> Du kan slutföra stegen i den här artikeln utöver stegen i [Konfigurera enkel inloggning med Kerberos](service-gateway-sso-kerberos.md) för att aktivera uppdatering för SAP BW-programserverbaserade rapporter som använder enkel inloggning med Kerberos i Power BI-tjänsten. Microsoft rekommenderar dock att du använder CommonCryptoLib som SNC-bibliotek. SAP erbjuder inte längre stöd för gx64krb5, och de steg som krävs för att konfigurera det för användning med gatewayen är betydligt mer komplexa jämfört med CommonCryptoLib. Information om hur du konfigurerar enkel inloggning med hjälp av CommonCryptoLib finns i [Konfigurera SAP BW för enkel inloggning med hjälp av CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md). Du bör slutföra konfigurationen för CommonCryptoLib _eller_ gx64krb5. Slutför inte konfigurationsstegen för båda biblioteken.

### <a name="set-up-gx64krb5gsskrb5-on-gateway-machine-and-the-sap-bw-server"></a>Konfigurera gx64krb5/gsskrb5 på gatewaydatorn och på SAP BW-servern

> [!NOTE]
> `gx64krb5` och `gsskrb5` stöds inte längre aktivt av SAP. Mer information finns i [SAP-anteckningen 352295](https://launchpad.support.sap.com/#/notes/352295). Observera också att `gx64krb5` inte tillåter SSO-anslutningar från datagatewayen till SAP BW-meddelandeservrar. Endast anslutningar till SAP BW-programservrar är möjliga. Den här begränsningen till enbart programserver finns inte om du använder [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) som SNC-bibliotek. Andra SNC-bibliotek kan också fungera för BW SSO, men de stöds inte officiellt av Microsoft.

`gx64krb5` \ `gsskrb5` måste användas av både klienten och servern för att slutföra en anslutning med enkel inloggning via gatewayen. Både klienten och servern måste alltså använda samma SNC-bibliotek.

1. Ladda ned `gx64krb5` från [SAP-kommentar 2115486](https://launchpad.support.sap.com/) (SAP s-användare krävs). Se till att du har minst version 1.0.11.x. Ladda även ned `gsskrb5` (32-bitarsversionen av biblioteket) om du vill testa anslutningen med enkel inloggning i SAP-gränssnittet innan du försöker ansluta med enkel inloggning via gatewayen (rekommenderas). 32-bitarsversionen krävs för testning med SAP-gränssnittet eftersom SAP-gränssnittet endast är tillgängligt som 32-bitarsversion.

1. Placera `gx64krb5` på en plats på din gatewaydator som är tillgänglig för din gatewaytjänstanvändare (och även av SAP-gränssnittet om du vill kunna testa anslutningen med enkel inloggning med hjälp av SAP-inloggning). Både gatewaytjänstanvändaren och de AD-användare (Active Directory) som tjänstanvändaren kommer att personifiera behöver läs- och körningsbehörigheter för .dll-filen. Vi rekommenderar att du beviljar gruppen Autentiserade användare behörigheter för .dll-filen. I testsyfte kan du även uttryckligen bevilja dessa behörigheter till både gatewayens tjänstanvändare och den Active Directory-användare som du kommer att använda för testning.

1. Om din BW-Server inte redan har konfigurerats för enkel inloggning med hjälp av gx64krb5/gsskrb5 placerar du en till kopia på din SAP BW-serverdator, på en plats som är tillgänglig för SAP BW-servern. 

1. På klientdatorn och serverdatorn anger du miljövariabeln `SNC_LIB` eller `SNC_LIB_64`. Om du använder gsskrb5 anger du variabeln `SNC_LIB` till den absoluta sökvägen för gsskrb5.dll. Om du använder gx64krb5 anger du variabeln `SNC_LIB_64` till den absoluta sökvägen för gx64krb5.dll.

### <a name="configure-an-sap-bw-service-user-and-enable-snc-communication"></a>Konfigurera en SAP BW-tjänstanvändare och aktivera SNC-kommunikation

Slutför det här avsnittet om du inte redan har konfigurerat din SAP BW-server för SNC-kommunikation (till exempel enkel inloggning) med hjälp av gx64krb5/gsskrb5.

> [!NOTE]
> Det här avsnittet förutsätter att du redan har skapat en tjänstanvändare för BW och kopplat ett lämpligt SPN till den (till exempel något som börjar med `SAP/`).

1. Ge tjänstanvändaren åtkomst till din SAP BW-programserver:

    1. På SAP BW-serverdatorn lägger du till tjänstanvändaren i gruppen Lokala administratörer. Öppna datorhanteringsprogrammet och dubbelklicka på gruppen Lokala administratörer för din server.

        ![Skärmbild av datorhanteringsprogram](media/service-gateway-sso-kerberos/computer-management.png)

    1. Dubbelklicka på gruppen Lokala administratörer och välj sedan **Lägg till** för att lägga till din tjänstanvändare i gruppen. Välj **Kontrollera namn** för att se till att du har angett namnet på rätt sätt. Välj **OK**.

1. Ange SAP BW-serverns tjänstanvändare som den användare som startar SAP BW-servertjänsten på SAP BW-serverdatorn.

    1. Öppna **Kör** och ange ”Services.msc”. Leta efter den tjänst som motsvarar din SAP BW-programserverinstans. Högerklicka på den och välj **Egenskaper**.

        ![Skärmbild av Tjänster med Egenskaper markerat](media/service-gateway-sso-kerberos/server-properties.png)

    1. Växla till fliken **Logga in** och ändra användaren till din SAP BW-tjänstanvändare. Ange användarens lösenord och välj **OK**.

1. Logga in på din server i SAP-inloggningen och ange följande profilparametrar med hjälp av RZ10-transaktionen:

    1. Ange profilparametern snc/identity/as till p:\<den SAP BW-tjänstanvändare som du har skapat\>, till exempel p:BWServiceUser@MYDOMAIN.COM. Observera det p: som föregår tjänstanvändarens UPN. Det är inte p:CN= som när Common Crypto Lib används som SNC-bibliotek.

    1. Ange profilparametern snc/gssapi\_lib till \<sökvägen till gsskrb5.dll/gx64krb5.dll på BW-serverdatorn (det bibliotek som du använder beror på hur många bitar operativsystemet är på)\>. Kom ihåg att placera biblioteket på en plats som SAP BW-programservern kan komma åt.

    1. Ange även följande ytterligare profilparametrar och ändra värdena efter behov. Observera att de sista fem alternativen innebär att klienter kan ansluta till SAP BW-servern med hjälp av SAP-inloggning utan att ha SNC konfigurerat.

        | **Inställning** | **Värde** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. Ange egenskapen snc/enable till 1.

1. När du har angett de här profilparametrarna öppnar du SAP-hanteringskonsolen på serverdatorn och startar om SAP BW-instansen. Om servern inte startar kontrollerar du att du har angett profilparametrarna på rätt sätt. Mer information om inställningar för profilparametrar finns i [SAP-dokumentationen](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm). Du kan också läsa felsökningsinformationen senare i det här avsnittet om det uppstår problem.

### <a name="map-a-sap-bw-user-to-an-active-directory-user"></a>Mappa en SAP BW-användare till en Active Directory-användare

Om du inte redan har gjort det mappar du en Active Directory-användare till en SAP BW-programserveranvändare och testar anslutningen med enkel inloggning i SAP-inloggningen.

1. Logga in på SAP BW-servern med hjälp av SAP-inloggning. Kör transaktion SU01.

1. Som **Användare** anger du den SAP BW-användare som du vill aktivera anslutningar med enkel inloggning för (i föregående skärmbild angav vi behörigheterna för BIUSER). Välj ikonen **Redigera** (bilden av en penna) längst upp till vänster i fönstret för SAP-inloggning.

    ![Skärmbild av SAP BW-användarens underhållsskärm](media/service-gateway-sso-kerberos/user-maintenance.png)

1. Välj fliken **SNC**. I inmatningsrutan för SNC-namn anger du p:\<din Active Directory-användare\>@\<din domän\>. Observera det obligatoriska p: som måste stå före Active Directory-användarens UPN. Den Active Directory-användare som du anger måste tillhöra den person eller organisation som du vill aktivera åtkomst med enkel inloggning till SAP BW-programservern för. Om du till exempel vill aktivera åtkomst med enkel inloggning för användaren testuser\@TESTDOMAIN.COM anger du p:testuser@TESTDOMAIN.COM.

    ![Skärmbild av SAP BW-skärmen för användarunderhåll](media/service-gateway-sso-kerberos/maintain-users.png)

1. Välj **Spara**-ikonen (bilden av en diskett) i det övre vänstra hörnet på skärmen.

### <a name="test-sign-in-by-using-sso"></a>Testa att logga in med enkel inloggning

Kontrollera att du kan logga in på servern med hjälp av SAP-inloggning via enkel inloggning som den Active Directory-användare som du precis har aktiverat åtkomst med enkel inloggning för.

1. Logga in på en dator där SAP-inloggning är installerat som den Active Directory-användare som du nyss aktiverade enkel inloggning för. Starta SAP-inloggning och skapa en ny anslutning.

1. I fönstret **Create New System Entry** (Skapa ny systempost) väljer du **User Specified System** (Användarspecifierat system) > **Nästa**.

    ![Skärmbild av skärmen Skapa ny systempost](media/service-gateway-sso-kerberos/new-system-entry.png)

1. Fyll i lämpliga uppgifter på nästa sida, inklusive programserver, instansnummer och system-ID. Välj sedan **Slutför**.

1. Högerklicka på den nya anslutningen och välj **Egenskaper**. Välj fliken **Nätverk**. I textrutan **SNC-namn** anger du p:\<SAP BW-tjänstanvändarens UPN\>, till exempel p:BWServiceUser@MYDOMAIN.COM. Välj sedan **OK**.

    ![Skärmbild av skärmen Egenskaper för systempost](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. Dubbelklicka på den anslutning som du precis skapade för att försöka upprätta en anslutning med enkel inloggning till din SAP BW-server. Om den här anslutningen lyckas går du vidare till nästa steg. Annars granskar du de föregående stegen i det här dokumentet för att se till att de har slutförts korrekt eller läser avsnittet om felsökning nedan. Observera att om du inte kan ansluta till SAP BW-servern via enkel inloggning i den här kontexten så kommer du inte kunna ansluta till SAP BW-servern med hjälp av enkel inloggning i gatewaykontexten.

### <a name="add-registry-entries-to-the-gateway-machine"></a>Lägg till registerposter i gateway-datorn

Lägg till nödvändiga registerposter i registret på den dator som gatewayen är installerad på samt på datorer som är avsedda att ansluta från Power BI Desktop. Här följer kommandona som ska köras:

1. REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

1. REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG\_DWORD /d 1 /f

### <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>Lägga till en ny datakälla för SAP BW-programservern i Power BI-tjänsten eller redigera en befintlig

1. I konfigurationsfönstret för datakällan anger du programserverns **Värddatornamn**, **Systemnummer** och **klient-ID** på samma sätt som när du loggar in på SAP BW-servern från Power BI Desktop.

1. I fältet **SNC-partnernamn** anger du p: \<det SPN som du mappade till SAP BW-tjänstanvändaren\>. Om SPN-namnet till exempel är SAP/BWServiceUser@MYDOMAIN.COM, ska du ange p:SAP/BWServiceUser@MYDOMAIN.COM i fältet **SNC-partnernamn**.

1. För SNC-biblioteket väljer du **SNC_LIB** eller **SNC_LIB_64**. Kontrollera att SNC_LIB_64 på gatewaydatorn pekar på gx64krb5.dll. Alternativt kan du välja alternativet ”Anpassad” och ange den absoluta sökvägen till gx64krb5.dll (på gatewaydatorn).

1. Välj rutan **Använd SSO via Kerberos för DirectQuery-frågor** och välj **Använd**. Om testanslutningen inte fungerar kontrollerar du att de föregående stegen för installation och konfiguration slutförts korrekt.

1. [Köra en Power BI-rapport](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>Felsökning

### <a name="troubleshoot-gx64krb5gsskrb5-configuration"></a>Felsöka gx64krb5-/gsskrb5-konfigurationen

Om det uppstår problem följer du dessa steg för att felsöka gx64krb5-/gsskrb5-installationen och anslutningarna med enkel inloggning från SAP-inloggningen.

* Det kan vara användbart att visa serverloggarna (...work\dev\_w0 på serverdatorn) vid felsökning av eventuella fel som uppstår vid slutförandet av stegen för gx64krb5-/gsskrb5-konfiguration. Detta gäller särskilt om SAP BW-servern inte startas när profilparametrarna har ändrats.

* Om det inte går att starta SAP BW-tjänsten på grund av ett inloggningsfel, har du kanske angett fel lösenord när du konfigurerade SAP BW ”start-as”-användaren. Verifiera lösenordet genom att logga in på en dator i Active Directory-miljön som SAP BW-tjänstanvändaren.

* Om det uppstår fel för att SQL-autentiseringsuppgifterna förhindrar att servern startas, kontrollerar du att du har beviljats åtkomst som tjänstanvändare till SAP BW-databasen.

* Du kan få följande meddelande: ”(GSS-API) det angivna målet är okänt eller kan inte nås”. Detta innebär vanligen att du har angett fel SNC-namn. Se till att endast använda ”p:”, inte ”p:CN=” eller något annat i klientprogrammet, förutom tjänstanvändarens UPN.

* Du kan få följande meddelande: ”(GSS-API) Ett ogiltigt namn har angetts”. Kontrollera att ”p:” finns i värdet för serverns SNC-identitetsprofilparameter.

* Du kan få följande meddelande: ”(SNC-fel) den angivna modulen kunde inte hittas”. Detta beror vanligtvis på att `gsskrb5.dll/gx64krb5.dll` har placerats någonstans som kräver utökade privilegier (administratörsrättigheter) för åtkomst.

### <a name="troubleshoot-gateway-connectivity-issues"></a>Felsöka problem med gatewayanslutningen

1. Kontrollera gatewayloggarna. Öppna programmet för gatewaykonfiguration och välj **Diagnostik** > **Exportera loggar**. De senaste felen hamnar längst ned i de loggfiler som du undersöker.

    ![Skärmbild av programmet Lokal datagateway med Diagnostik markerat](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. Aktivera SAP BW-spårning och granska de genererade loggfilerna. Det finns flera olika typer av SAP BW-spårning. Mer information finns i SAP-dokumentationen.

## <a name="next-steps"></a>Nästa steg

Mer information om den **lokala datagatewayen** och **DirectQuery** finns i följande resurser:

* [Vad är en lokal datagateway?](/data-integration/gateway/service-gateway-getting-started)
* [DirectQuery i Power BI](desktop-directquery-about.md)
* [Datakällor som stöds av DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery och SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery och SAP HANA](desktop-directquery-sap-hana.md)
