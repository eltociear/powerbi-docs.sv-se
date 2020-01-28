---
title: Lösa problem när du startar Power BI Desktop
description: Lösa problem när du startar Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 67c83f2cc0eb81e90f447961ed178a04e97e050e
ms.sourcegitcommit: 3d6b27e3936e451339d8c11e9af1a72c725a5668
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2020
ms.locfileid: "76160913"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>Felsöka öppning av Power BI Desktop

I Power BI Desktop kan användare som har installerat och som kör tidigare versioner av den *lokala Power BI-datagatewayen* blockeras från att starta Power BI Desktop, på grund av administrativa principbegränsningar som den lokala Power BI-gatewayen har infört för namngivna pipes på den lokala datorn.

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>Lösa problem med lokal datagateway och Power BI Desktop

Det finns tre alternativ för att lösa problemet som är kopplat till den lokala datagatewayen och göra det möjligt för Power BI Desktop att starta:

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>Lösning 1: Installera den senaste versionen av den lokala Power BI-datagatewayen

Den senaste versionen av den lokala Power BI-datagatewayen inför inte begränsningar för namngivna pipes på den lokala datorn och gör att Power BI Desktop kan starta korrekt. Om du behöver fortsätta använda den lokala Power BI-datagatewayen är detta den rekommenderade lösningen. Du kan ladda ned den [senaste versionen av den lokala Power BI-datagatewayen](https://go.microsoft.com/fwlink/?LinkId=698863). Länken är en direkt nedladdningslänk till installationsprogrammet.

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>Lösning 2: Avinstallera eller stoppa Microsoft-tjänsten för den lokala Power BI-datagatewayen

Du kan avinstallera den lokala Power BI-datagatewayen om du inte längre behöver den. Du kan också stoppa den lokala Microsoft-tjänsten Power BI-datagateway, som tar bort principbegränsningen och gör att Power BI Desktop kan öppnas.

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>Lösning 3: Kör Power BI Desktop med administratörsprivilegier

Du kan istället starta Power BI Desktop som administratör, vilket även låter Power BI Desktop starta. Vi rekommenderar ändå att du installerar den senaste versionen av den lokala Power BI-datagatewayen, vilket beskrivs tidigare.

Power BI Desktop är utformad som en flerprocessarkitektur och flera av de här processerna kommunicerar med hjälp av Windows-namngivna pipes. Det kan finnas andra processer som stör dessa namngivna pipes. Den vanligaste orsaken för sådana störningar är säkerhet, inklusive situationer där antivirusprogram eller brandväggar blockerar pipes eller omdirigerar trafik till en viss port. Om du startar Power BI Desktop med administratörsbehörigheter så kan det lösa det problemet. Om du inte kan öppna med administratörsbehörighet kan du be administratören att avgöra vilka säkerhetsregler som hindrar namngivna pipelines från att kommunicera korrekt. Vitlista sedan Power BI Desktop och dess respektive underprocesser.

## <a name="resolve-issues-when-connecting-to-sql-server"></a>Lösa problem vid anslutning till SQL Server

När du försöker ansluta till en SQL Server-databas kan du stöta på ett felmeddelande som ser ut som följande text:

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

Du kan ofta lösa problemet om du öppnar Power BI Desktop som administratör innan du skapar SQL Server-anslutningen.

När du har öppnat Power BI Desktop som administratör och upprättat anslutningen registreras de nödvändiga DLL:erna korrekt. Därefter är det inte nödvändigt att öppna Power BI Desktop som administratör.

## <a name="get-help-with-other-launch-issues"></a>Hjälp med andra startproblem

Vi strävar efter att täcka så många problem med Power BI Desktop som möjligt. Vi tittar regelbundet på problem som kan påverka många kunder och inkluderar dem i våra artiklar.

Om problemet som uppstår när du startar Power BI Desktop inte är associerat med den lokala datagatewayen eller om de tidigare lösningarna inte fungerar, kan du skicka in en händelserapport till *Power BI-supporten* (<https://support.powerbi.com>) för att identifiera och lösa problemet.

Om du skulle stöta på andra problem med Power BI Desktop framöver kan det hjälpa att aktivera spårning och samla in loggfiler. Loggfiler kan hjälpa till att isolera och identifiera problemet. Om du vill aktivera spårning väljer du **Arkiv** > **Alternativ och Inställningar** > **Alternativ**. Välj **Diagnostik** och sedan **Aktivera spårning**. Power BI Desktop måste köras för att ange detta alternativ, vilket är bättre för framtida problem som är associerade när du startar Power BI Desktop.
