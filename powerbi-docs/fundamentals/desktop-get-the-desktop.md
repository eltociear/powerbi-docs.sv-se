---
title: Hämta Power BI Desktop
description: Ladda ner och installera Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/29/2020
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 3038463a9e3447ee9b38ae3cb178f3486d21bc80
ms.sourcegitcommit: c83146ad008ce13bf3289de9b76c507be2c330aa
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86215107"
---
# <a name="get-power-bi-desktop"></a>Hämta Power BI Desktop
Med Power BI Desktop kan du skapa avancerade frågor, modeller och rapporter som visualiserar data. Med Power BI Desktop kan du bygga datamodeller, skapa rapporter och dela ditt arbete genom att publicera till Power BI-tjänsten. Power BI Desktop är en kostnadsfri nedladdning.

Du kan skaffa Power BI Desktop på två sätt som beskrivs i följande avsnitt:

* [Installera som en app från Microsoft Store](#install-as-an-app-from-the-microsoft-store).
* [Ladda ned direkt som en körbar fil som du laddar ned och installerar på datorn](#download-power-bi-desktop-directly).

Endera metoden ger den senaste versionen av Power BI Desktop på datorn, men det finns några skillnader att tänka på som beskrivs i följande avsnitt.

## <a name="install-as-an-app-from-the-microsoft-store"></a>Installera som en app från Microsoft Store
Det finns några sätt att skaffa den senaste versionen av Power BI Desktop från Microsoft Store. 

1. Använd något av följande alternativ för att öppna **Power BI Desktop-sidan** i Microsoft Store:

   - Öppna en webbläsare och gå direkt till [Power BI Desktop-sidan](https://aka.ms/pbidesktopstore) i Microsoft Store.

    - Från [Power BI-tjänsten](https://docs.microsoft.com/power-bi/service-get-started) väljer du ikonen **Ladda ned** i det övre högra hörnet och väljer sedan **Power BI Desktop**.

      ![Skärmbild av Microsoft Store och alternativet för att ladda ned Power BI Desktop.](media/desktop-get-the-desktop/getpbid_downloads.png)

   - Gå till [Power BI Desktop-produktsidan](https://powerbi.microsoft.com/desktop/) och välj sedan **Ladda ned kostnadsfritt**.
  
2. När du har kommit till **Power BI Desktop-sidan** i Microsoft Store väljer du **Installera**.

     ![Skärmbild av Microsoft Store och alternativet för att installera Power BI Desktop.](media/desktop-get-the-desktop/getpbid_04.png)

Det finns några fördelar med att hämta Power BI Desktop från Microsoft Store:

* **Automatiska uppdateringar**: Windows laddar ned den senaste versionen automatiskt i bakgrunden så snart den finns tillgänglig, så att din version alltid är uppdaterad.
* **Mindre nedladdningar**: Microsoft Store ser till att enbart komponenter som har ändrats i varje uppdatering laddas ned till datorn, vilket resulterar i mindre nedladdningar för varje uppdatering.
* **Administratörsbehörighet behövs inte**: När du laddar ned paketet direkt och installerar det behöver du vara administratör för att installationen ska slutföras. Om du skaffar Power BI Desktop från Microsoft Store behöver du *inte* adminbehörighet.
* **Aktiverad för IT-distribution**: Genom Microsoft Store för företag kan du enklare *distribuera* Power BI Desktop till alla i din organisation

* **Språkidentifiering**: Microsoft Store-versionen inkluderar alla språk som stöds och kontrollerar vilket språk som används på datorn varje gång den startas. Detta språkstöd påverkar även lokaliseringen av modeller som skapas i Power BI Desktop. Till exempel matchar inbyggda datumhierarkier det språk som Power BI Desktop använder när .pbix-filen skapas.

Följande överväganden och begränsningar gäller när du installerar Power BI Desktop från Microsoft Store:

* Om du använder SAP-anslutningsappen, kan du behöva flytta dina SAP-drivrutinsfiler till *Windows\System32*-mappen.
* Vid installation av Power BI Desktop från Microsoft Store kopieras inte användarinställningar från .exe-versionen. Du kan behöva återansluta till de senaste datakällorna och ange dina autentiseringsuppgifter för datakälla igen. 

> [!NOTE]
> Power BI-rapportserverversionen av Power BI Desktop är en separat installation och skiljer sig från de versioner som beskrivs i den här artikeln. Mer information om rapportserverversionen av Power BI Desktop finns i [Skapa en Power BI-rapport för Power BI-rapportserver](../report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="download-power-bi-desktop-directly"></a>Ladda ned Power BI Desktop direkt
  
  Om du vill ladda ned den körbara Power BI Desktop-filen från Download Center väljer du **Ladda ned** på [Download Center-sidan](https://www.microsoft.com/download/details.aspx?id=58494). Ange sedan en 32-bitars eller 64-bitars installationsfil som ska laddas ned.

  ![Skärm bild av Nedladdningscenter och kryssrutan för nedladdning av 64-bitarsversionen av Power BI Desktop.](media/desktop-get-the-desktop/download-desktop-exe.png)

### <a name="install-power-bi-desktop-after-downloading-it"></a>Installera Power BI Desktop när det har laddats ned
Du uppmanas att köra installationsfilen när nedladdningen är klar.

Från och med juli 2019-versionen levereras Power BI Desktop som ett enda .exe-installationspaket som innehåller alla språk med stöd, med en separat .exe-fil för versionen med 32 respektive 64 bitar. MSI-paketen upphör från och med versionen från september 2019, vilket kräver exe-filen för installation. Den här metoden gör distribution, uppdateringar och installation (särskilt för administratörer) mycket enklare och smidigare. Du kan även använda kommandoradsparametrar för att anpassa installationsprocessen enligt beskrivningen i [Använda kommandoradsalternativ under installation](#using-command-line-options-during-installation).

När du startar installationspaketet installeras Power BI Desktop som ett program och körs på skrivbordet.

![Skärmbild av Power BI Desktop-installationen och installationsguiden.](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> Installation av den nedladdade versionen (MSI, inaktuell) och Microsoft Store-versionen av Power BI Desktop på samma dator (kallas ibland en *sida-vid-sida*-installation) stöds inte. Avinstallera Power BI Desktop manuellt innan du laddar ned det från Microsoft Store.
> 

## <a name="using-power-bi-desktop"></a>Använd Power BI Desktop
När du startar Power BI Desktop visas en välkomstskärm.

![Skärmbild av Power BI Desktop-installationen och välkomstskärmen.](media/desktop-get-the-desktop/getpbid_05.png)

Om du använder Power BI Desktop för första gången (det vill säga att installationen inte är en uppgradering) uppmanas du att fylla i ett formulär eller logga in på Power BI-tjänsten innan du kan fortsätta.

Därifrån kan du börja skapa datamodeller eller rapporter och sedan dela dem med andra på Power BI-tjänsten. I avsnittet [Nästa steg](#next-steps) finns länkar till guider som hjälper dig att komma igång med att använda Power BI Desktop.

## <a name="minimum-requirements"></a>Minimikrav
Följande lista innehåller minimikraven för att köra Power BI Desktop:

* Windows 7 / Windows Server 2008 R2 eller senare
* .NET 4.5
* Internet Explorer 10 eller senare
* Minne (RAM): Minst 1 GB tillgängligt, 1,5 GB eller mer rekommenderas.
* Skärm: Minst 1 440 x 900 eller 1 600 x 900 (16:9) rekommenderas. Lägre upplösningar, till exempel 1 024 x 768 eller 1 280 x 800, rekommenderas inte eftersom vissa kontroller (till exempel att stänga startskärmen) visas utanför de upplösningarna.
* Bildskärmsinställningar i Windows: Om du anger bildskärmsinställningarna till att ändra storleken på text, appar och andra objekt till mer än 100% ser du kanske inte vissa dialogrutor som du måste interagera med för att fortsätta använda Power BI Desktop. Om det här problemet uppstår kontrollerar du bildskärmsinställningarna i Windows genom att gå till **Inställningar** > **System** > **Bildskärm** och använda skjutreglaget för att återställa bildskärmsinställningarna till 100 %.
* CPU: 1 gigahertz (GHz) eller snabbare 32-bitars eller 64-bitars x86-processor rekommenderas.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Vi vill att du ska ha en bra upplevelse när du använder Power BI Desktop. Det kan dock hända att du stöter på problem med Power BI Desktop. Det här avsnittet innehåller lösningar eller förslag för att hantera sådana problem. 

### <a name="using-command-line-options-during-installation"></a>Använda kommandoradsalternativ under installation 

När du installerar Power BI Desktop kan du ange egenskaper och alternativ med kommandoradsväxlar. De här inställningarna är särskilt användbara för administratörer som hanterar eller underlättar installationen av Power BI Desktop mellan organisationer. Dessa alternativ gäller för .msi- och .exe-installationer. 


|Kommandoradsalternativ  |Beteende  |
|---------|---------|
|-q, -quiet, -s, -silent     |Tyst installation         |
|-passive     |Visa endast förloppsindikatorn under installation         |
|-norestart     |Förhindra kravet på omstart av datorn         |
|-forcerestart     |Starta om datorn efter installationen utan uppmaning         |
|-promptrestart     |Uppmana användaren om omstart av datorn krävs (standard)         |
|-l<>, -log<>     |Logga installationen till en specifik fil som anges inom <>         |
|-uninstall     |Avinstallera Power BI Desktop         |
|-repair     |Reparera installationen (eller installera om den för närvarande inte är installerad)         |
|-package, -update     |Installera Power BI Desktop (standard förutsatt att -uninstall eller -repair inte har angetts)         |

Du kan även använda följande syntaxparametrar som du anger med syntaxen *egenskap = värde*:

|Parameter  |Innebörd  |
|---------|---------|
|ACCEPT_EULA     |Kräver värdet 1 för att automatiskt godkänna licensavtalet         |
|ENABLECXP     |Värdet 1 registreras i det Customer Experience-program som registrerar telemetri om produktanvändningen         |
|INSTALLDESKTOPSHORTCUT     |Värdet 1 lägger till en genväg till skrivbordet         |
|INSTALLLOCATION     |Filsökväg till den plats där du vill installera den         |
|LANGUAGE     |Språkkod (till exempel en-US, de-DE eller pr-BR) för att framtvinga programmets standardspråk. Om du inte anger något språk visar Power BI Desktop språket från Windows-operativsystemet. Du kan ändra den här inställningen i dialogrutan **Alternativ**.         |
|REG_SHOWLEADGENDIALOG     |Värdet 0 inaktiverar visning av den dialogruta som visas innan du har loggat in på Power BI Desktop.         |
|DISABLE_UPDATE_NOTIFICATION     |Värdet 1 inaktiverar uppdateringsmeddelanden.         |


Du kan till exempel köra Power BI Desktop med följande alternativ och parametrar för att installera utan något användargränssnitt med språket tyska: 

```-quiet LANG=de-DE ACCEPT_EULA=1```

### <a name="installing-power-bi-desktop-on-remote-machines"></a>Installera Power BI Desktop på fjärrdatorer

Om du distribuerar Power BI Desktop till dina användare med ett verktyg som kräver en Windows-installationsfil (.msi-fil) kan du extrahera msi-filen från .exe-filen för Power BI Desktop-installationen. Använd ett verktyg från tredje part, till exempel WiX Toolset.

> [!NOTE]
> WiX verktygsalternativ kan ändras utan föregående meddelande, eftersom detta är en produkt från tredje part. Läs deras senaste dokumentation och kontakta deras e-postlista om du behöver hjälp.

1. På den dator där du laddade ned installationsprogrammet för Power BI Desktop installerar du den senaste versionen av [WiX Toolset](https://wixtoolset.org/).
2. Öppna ett kommandoradsfönster som administratör och gå till den mapp där du installerade WiX Toolset.
3. Kör följande kommando: 
    
    ```Dark.exe <path to Power BI Desktop installer> -x <output folder>```

    Till exempel:

    ``` Dark.exe C:\PBIDesktop_x64.exe -x C:\output```

    Utdatamappen innehåller en mapp med namnet *AttachedContainer* som innehåller MSI-filerna.

Det finns inte stöd för att uppgradera en installation från en .exe till en .msi som du har extraherat från en .exe.   För att göra den här uppgraderingen måste du först avinstallera den äldre versionen av Power BI Desktop som du har.

### <a name="issues-when-using-previous-releases-of-power-bi-desktop"></a>Problem när du använder tidigare versioner av Power BI Desktop

För vissa användare kan det visas ett felmeddelande som liknar följande när de använder en inaktuell version av Power BI Desktop: 

*Det gick inte att återställa den sparade databasen till modellen* 

Användaren kan oftast åtgärda problemet genom att uppdatera till den aktuella versionen av Power BI Desktop.

### <a name="disabling-notifications"></a>Avaktivera aviseringar
Vi rekommenderar att du uppdaterar till den senaste versionen av Power BI Desktop för att kunna utnyttja nya funktioner, prestanda, stabilitet och andra förbättringar. Det kan hända att vissa företag inte vill att deras användare uppdaterar till varje ny version. Du kan inaktivera meddelanden genom att ändra registret med följande steg:

1. I Registereditorn går du till nyckeln **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop**.
2. Skapa en ny **REG_DWORD**-post i nyckeln med följande namn: **DisableUpdateNotification**.
3. Ange värdet för den nya posten till **1**.
4. Starta om datorn så börjar ändringen gälla.

### <a name="power-bi-desktop-loads-with-a-partial-screen"></a>Power BI Desktop läser in en partiell skärm

Under vissa omständigheter, inklusive vissa skärmupplösningskonfiguraitoner, kan vissa användare se Power BI Desktop visa innehåll med stora svarta områden. Detta problem beror vanligtvis på de senaste uppdateringarna för operativsystemet som påverkar hur objekt renderas snarare än hur innehåll presenteras i Power BI Desktop. Följ dessa steg för att åtgärda problemet:

1. Tryck på **Start** och skriv ordet *suddig* i det sökfält som visas.
2. I dialogrutan som visas väljer du alternativet: **Låt Windows åtgärda appar som är suddiga.**
3. Starta om Power BI Desktop

Problemet kan komma att lösas med senare Windows-uppdateringar. 
 

## <a name="next-steps"></a>Nästa steg
När du har installerat Power BI Desktop kan du komma igång snabbt med hjälp av följande innehåll:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Frågeöversikt i Power BI Desktop](../transform-model/desktop-query-overview.md)
* [Datakällor i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Ansluta till data i Power BI Desktop](../connect-data/desktop-connect-to-data.md)
* [Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](../transform-model/desktop-common-query-tasks.md)   
