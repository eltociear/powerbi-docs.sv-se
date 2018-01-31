---
title: "Hämta Power BI Desktop"
description: Ladda ner och installera Power BI Desktop
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: monitoring
qualitydate: 08/15/2017
ms.service: powerbi
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/24/2018
ms.author: davidi
ms.openlocfilehash: 2f00c1a96ca92be68452a58e046f23d6be4eb49c
ms.sourcegitcommit: 7249ff35c73adc2d25f2e12bc0147afa1f31c232
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/25/2018
---
# <a name="get-power-bi-desktop"></a>Hämta Power BI Desktop
**Power BI Desktop** låter dig skapa avancerade frågor, modeller och rapporter som visualiserar data. Med **Power BI Desktop**, kan du skapa datamodeller, skapa rapporter och dela ditt arbete genom att publicera till Power BI-tjänsten.  **Power BI Desktop** är en kostnadsfri nedladdning.

Du kan hämta **Power BI Desktop** på två sätt som beskrivs i följande avsnitt:

* **Ladda ned** direkt (ett MSI-paket som du hämtar och installerar på din dator)
* Installera som en app från **Windows Store**

Endera metod ger dig den senaste versionen av **Power BI Desktop** på din dator, men det finns några skillnader att tänka på, vilka beskrivs i följande avsnitt.

## <a name="download-power-bi-desktop"></a>Ladda ner Power BI Desktop
Om du vill ladda ner den senaste versionen av **Power BI Desktop**, kan du välja nedladdningsikonen från det övre högra hörnet av Power BI-tjänsten och välja **Power BI Desktop**.

![](media/desktop-get-the-desktop/getpbid_downloads.png)

Du kan också hämta den senaste versionen av Power BI Desktop från följande nedladdningssida:

* [**Power BI Desktop-nedladdning** (både 32- och 64-bitars versioner)](https://powerbi.microsoft.com/desktop).
  
  [![](media/service-admin-power-bi-security/PBI_Security_01.png)](https://powerbi.microsoft.com/desktop)

Oavsett hur du väljer att ladda ned det så kommer **Power BI Desktop** att be dig att köra installationsfilen efter att du laddat ner den:

![](media/desktop-get-the-desktop/getpbid_3.png)

**Power BI Desktop** installeras som ett program och körs på skrivbordet.

![](media/desktop-get-the-desktop/designer_gsg_install.png)

> [!NOTE]
> Att installera den nedladdade (MSI)-versionen och **Windows Store**-versionen av **Power BI Desktop** på samma dator (kallas ibland en *sida-vid-sida* installation) stöds inte.
> 
> 

## <a name="install-as-an-app-from-the-windows-store"></a>Installera som en app från Windows Store
Du kan också hämta **Power BI Desktop** från Windows Store med följande länk:

* [Installera **Power BI Desktop** från **Windows Store**](http://aka.ms/pbidesktopstore)

![](media/desktop-get-the-desktop/getpbid_04.png)

Det finns några fördelar med att få **Power BI Desktop** från Windows Store:

* **Automatiska uppdateringar** – Windows hämtar den senaste versionen automatiskt i bakgrunden så snart den finns tillgänglig så att din version alltid är uppdaterad.
* **Mindre nedladdningar** – **Windows Store** ser till att enbart komponenter som har ändrats i varje uppdatering hämtas till datorn, vilket resulterar i mindre nedladdningar för varje uppdatering.
* **Admin-behörighet behövs inte** – när du hämtar MSI:n direkt och installerar den, behöver du vara administratör för att installationen ska slutföras. När du får **Power BI Desktop** från Windows Store, behövs *ingen* adminbehörighet.
* **Redo för IT lansering** – **Windows Store**-versionen kan enklare distribueras eller *lanseras* till alla i din organisation och kan göra **Power BI Desktop** tillgängligt via **Microsoft Store för företag**.
* **Språkidentifiering** – **Windows Store**-versionen inkluderar alla språk som stöds och kontrollerar vilka språk som används på datorn varje gång den startas. Detta påverkar även lokaliseringen av modeller som skapats i **Power BI Desktop**, inbyggda datumhierarkier kommer till exempel att matcha det språk som **Power BI Desktop** använde när .pbix-filen skapades.

Det finns några överväganden och begränsningar för att installera **Power BI Desktop** från Windows Store, som inkluderar följande:

* Om du använder SAP-anslutningsappen, kan du behöva flytta dina SAP-drivrutinsfiler till *Windows\System32*-mappen.

> [!NOTE]
> Att installera den nedladdade (MSI)-versionen och **Windows Store**-versionen av **Power BI Desktop** på samma dator (kallas ibland en *sida-vid-sida* installation) stöds inte.
> 
> [!NOTE]
> Power BI Report Server-versionen av **Power BI Desktop** är en separat installation och skiljer sig från de versioner som beskrivs i den här artikeln. För information om Report Server-versionen av **Power BI Desktop**, finns artikeln [Snabbstart: skapa en Power BI-rapport för Power BI-rapportservern](report-server/quickstart-create-powerbi-report.md).
> 
> 

## <a name="using-power-bi-desktop"></a>Använd Power BI Desktop
När du startar **Power BI Desktop**, visas en *Välkommen*-skärm.

![](media/desktop-get-the-desktop/getpbid_05.png)

Om det här är först gången du använder **Power BI Desktop** (om installationen inte är en uppgradering), uppmanas du att fylla i ett formulär och besvara några frågor eller logga in på **Power BI-tjänsten** innan du kan fortsätta.

Därifrån kan du börja skapa datamodeller eller rapporter och sedan dela dem med andra på Power BI-tjänsten. Kolla in länkarna **mer information** i slutet av den här artikeln för länkar till guider som kan hjälpa dig att komma igång med **Power BI Desktop**.

## <a name="minimum-requirements"></a>Minimikrav
Följande lista innehåller minimikraven för att köra **Power BI Desktop**:

* Windows 7 / Windows Server 2008 R2 eller senare
* .NET 4.5
* Internet Explorer 9 eller senare
* **Minne (RAM):** minst 1 GB tillgängligt, 1,5 GB eller mer rekommenderas.
* **Bildskärm:** minst 1 440 x 900 eller 1 600 x 900 (16:9) rekommenderas. Lägre upplösningar, till exempel 1 024 x 768 eller 1 280 x 800 rekommenderas inte, eftersom vissa kontroller (till exempel att stänga startskärmen) visas utanför de upplösningarna.
* **Windows bildskärmsinställningar:** om dina bildskärmsinställningar är inställda att ändra storleken på text, appar och andra objekt till mer än 100%, kanske du inte ser vissa dialogrutor som måste stängas eller svaras på för att fortsätta med **Power BI Desktop**. Om du påträffar det här problemet, kontrollera dina **bildskärmsinställningar** genom att gå till **Inställningar > System > Visa** i Windows och använda skjutreglaget för att återställa bildskärmsinställningarna till 100 %.
* **Processor:** 1 gigahertz (GHz) eller snabbare x86- eller x64-bitars processor rekommenderas.

## <a name="next-steps"></a>Nästa steg
När du har installerat **Power BI Desktop** kan du komma igång snabbt med hjälp av följande innehåll:

* [Komma igång med Power BI Desktop](desktop-getting-started.md)
* [Frågeöversikt med Power BI Desktop](desktop-query-overview.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Anslut till data i Power BI Desktop](desktop-connect-to-data.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Vanliga frågeuppgifter i Power BI Desktop](desktop-common-query-tasks.md)   

