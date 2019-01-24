---
title: Introduktion till organisationsinnehållspaket i Power BI
description: Läs mer om att packa upp och dela dina instrumentpaneler, rapporter, Excel-arbetsböcker och datauppsättningar med dina kollegor som organisationsinnehållspaket.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/02/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f7e8d58e5fd738e5da678723ef239f5303be5070
ms.sourcegitcommit: 54907bb59a5c31b25d368d83a0c4faa5e2f0db66
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54838472"
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Introduktion till organisationsinnehållspaket i Power BI
> [!NOTE]
> Du kan inte skapa innehållspaket för organisationen eller installera dem i förhandsversionen för den nya arbetsytan. Nu är ett bra tillfälle att uppgradera dina innehållspaket till appar, om du inte har börjat ännu. Lär dig [mer om den nya arbetsytan](service-create-the-new-workspaces.md).
> 

Distribuerar du regelbundet rapporter via e-post till ditt team? Prova det här istället: Paketera dina instrumentpaneler, rapporter, Excel-arbetsböcker och datauppsättningar och publicera dem till ditt team som ett *organisationsinnehållspaket*. Det är lätt för ditt team att hitta innehållspaketen du skapar &#151; de finns på AppSource. Eftersom de är en del av Power BI använder de alla funktioner i Power BI, inklusive interaktiv datagranskning, nya visuella objekt, frågor och svar, integrering med andra datakällor och datauppdatering.

![](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

Att skapa innehållspaket skiljer sig från att dela instrumentpaneler eller samarbeta med dem i en arbetsyta. Läs [Hur ska jag samarbeta med och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md) för att välja det bästa alternativet för din situation. 

I AppSource, kan du bläddra eller söka efter innehållspaket som publiceras till hela organisationen, distributioner eller säkerhetsgrupper och till de [Office 365-grupper som du tillhör](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9). Om du inte är medlem i en specifik grupp visas inte innehållspaket som delas med den gruppen. Alla medlemmar i gruppen har samma skrivskyddad åtkomst till innehållspaketets data, rapporter, arbetsböcker och instrumentpaneler (om det inte är en datakälla för SQL Server Analysis Services (SSAS), varmed dina behörigheter överförs med datakällan).

Instrumentpaneler, rapporter och Excel-arbetsböcker är skrivskyddade, men du kan kopiera och använda instrumentpaneler och rapporter som utgångspunkt för att skapa din egen anpassade version av innehållspaketet.

> [!NOTE]
> Organisationsinnehållspaket är endast tillgängliga när du och dina kollegor använder [Power BI Pro-licenser](service-features-license-type.md).
> 
> 

## <a name="what-is-appsource"></a>Vad är *AppSource*?
När du publicerar ett organisationsinnehållspaket läggs detta till på AppSource.  Med den här centraliserade databasen är det enkelt för medlemmar att bläddra till och identifiera instrumentpaneler, rapporter och datauppsättningar som har publicerats för dem.  

* Om du vill visa AppSource väljer du **Hämta data** > **Min organisation** > **Hämta**.

## <a name="the-life-cycle-of-an-organizational-content-pack"></a>En organisations innehållspakets livscykel
Alla Power BI Pro användare kan skapa, publicera och komma åt organisationsinnehållspaket. Det är endast skaparen av organisationsinnehållspaketet som kan redigera arbetsboken och datauppsättningen, schemalägga en uppdatering och ta bort den.

Livscykeln ser ut ungefär så här:

1. Nate skapar ett innehållspaket i Power BI Pro och publicerar den i distributionsgruppen Marknadsföring. Uppdateringsinställningarna följer med datauppsättningen och kan bara ändras av Nate.
   
   > [!NOTE]
   > Om Nate skapar ett innehållspaket inifrån den arbetsyta i [Power BI-appen](service-create-distribute-apps.md) han tillhör kan andra personer i Power BI-arbetsytan ta över ägarskapat, även om han lämnar arbetsytan.
   > 
   > 
2. Nate skickar e-post till distributionsgruppen och informerar dem om det nya innehållspaketet.
3. Jane är medlem i distributionsgruppen Marketing i Power BI Pro och söker efter och ansluter innehållspaketet i AppSource. Hon har nu en skrivskyddad kopia.  Hon vet att det är skrivskyddat eftersom den delningsikon visas till vänster och instrumentpanelen och rapportens namn till det vänstra navigeringsfönstret. Och när du väljer hon instrumentpanelen informeras Jane av en låsikon att hon tittar på instrumentpanelen för ett innehållspaket. 
4. Låt oss säga att hon bestämmer sig för att anpassa den. Hon har nu sin egen kopia av instrumentpanelen och rapporterna. Hennes arbete påverkar inte källan, det ursprungliga innehållspaketet eller andra medlemmar i distributionsgruppen. Hon arbetar nu på sin egen kopia av instrumentpanelen och rapporten.
5. Nate gör uppdateringar på instrumentpanelen och när det är klart kan han publicerar en ny version av innehållspaketet.
   
   * Julio, en annan medlem i distributionsgruppen har inte anpassat det ursprungliga innehållspaketet. De nya ändringarna tillämpas automatiskt på hans version av innehållspaketet.  
   * Jane anpassade innehållspaketet. Hon får ett meddelande om att det finns en ny version.  Hon kan gå till AppSource och få det uppdaterade innehållspaketet utan att förlora sin anpassade version. Hon har nu två versioner: den anpassade versionen och det uppdaterade innehållspaketet.
6. Låt oss säga att Nate ändrar säkerhetsinställningarna. Julio och Jane har inte längre åtkomst till innehållet. Eller låt oss säga att de har tagits bort från distributionsgruppen Marknadsföring.
   
   * Julio anpassade inte det ursprungliga innehållspaketet, så innehållet tas bort automatiskt. 
   * Jane anpassade innehållspaketet. Nästa gång hon öppnar instrumentpanelen har alla paneler från det ursprungliga innehållspaketet försvunnit men paneler som hon har fäst från andra rapporter (som hon fortfarande har behörighet att använda) visas fortfarande. Associerade rapporter och datauppsättningar är inte längre tillgängliga (och visas inte i det vänstra navigeringsfönstret).
7. Eller också tar Nate bort innehållspaketet.
   
   * Julio anpassade inte det ursprungliga innehållspaketet, så innehållet tas bort automatiskt. 
   * Jane anpassade innehållspaketet. Nästa gång hon öppnar instrumentpanelen har alla paneler från det ursprungliga innehållspaketet försvunnit men paneler som hon har fäst från andra rapporter visas fortfarande. Associerade rapporter och datauppsättningar är inte längre tillgängliga (och visas inte i det vänstra navigeringsfönstret).

## <a name="data-security"></a>Datasäkerhet
Alla medlemmar i distributionsgruppen har samma behörighet för data som skaparen av innehållspaketet. Det enda undantaget är SQL Server Analysis Services (SSAS) lokala tabelldatauppsättningar. Eftersom rapporter och instrumentpaneler ansluter till den lokala SSAS-modellen i realtid, används autentiseringsuppgifterna för varje enskild medlem i distributionsgruppen för att fastställa vilka data som han eller hon kan komma åt.

## <a name="next-steps"></a>Nästa steg
* [Skapa och publicera ett organisationsinnehållspaket](service-organizational-content-pack-create-and-publish.md)
* [Skapa och distribuera en app i Power BI](service-create-distribute-apps.md) 
* [Power BI – grundläggande begrepp](consumer/end-user-basic-concepts.md)
* Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

