---
title: "Introduktion till organisationsinnehållspaket i Power BI"
description: "Läs mer om att packa upp och dela dina instrumentpaneler, rapporter, Excel-arbetsböcker och datauppsättningar med dina kollegor som organisationsinnehållspaket."
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: ajayan
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/12/2017
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 00ddec3dbf4087935a7c3583138dabb2a83f0ae5
ms.sourcegitcommit: 88c8ba8dee4384ea7bff5cedcad67fce784d92b0
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/24/2018
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Introduktion till organisationsinnehållspaket i Power BI
> [!NOTE]
> Har du hört om de nya *apparna* ännu? Appar är det nya sättet att distribuera innehåll till stora målgrupper i Power BI. Vi rekommenderar att du använder appar istället för organisationsinnehållspaket eller skrivskyddade arbetsytor. Läs [mer om appar](service-install-use-apps.md).
> 
> 

Distribuerar du regelbundet rapporter via e-post till ditt team? Prova i stället: Packa upp dina instrumentpaneler, rapporter, Excel-arbetsböcker och datauppsättningar och publicera dem i din grupp som ett *organisationsinnehållpaket*. Det är lätt för ditt team att hitta innehållspaketen du skapar &#151; de finns på AppSource. Eftersom de är en del av Power BI använder de alla funktioner i Power BI, inklusive interaktiv datagranskning, nya visuella objekt, frågor och svar, integrering med andra datakällor och datauppdatering.

![](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

Att skapa innehållspaket skiljer sig från att dela instrumentpaneler eller samarbeta med dem i en arbetsyta. Läs [Hur ska jag samarbeta med och dela instrumentpaneler och rapporter?](service-how-to-collaborate-distribute-dashboards-reports.md) för att välja det bästa alternativet för din situation. 

I AppSource, kan du bläddra eller söka efter innehållspaket som publiceras till hela organisationen, distributioner eller säkerhetsgrupper och till de [Office 365-grupper som du tillhör](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9). Om du inte är medlem i en specifik grupp visas inte innehållspaket som delas med den gruppen. Alla medlemmar i gruppen har samma skrivskyddad åtkomst till innehållspaketets data, rapporter, arbetsböcker och instrumentpaneler (om det inte är en datakälla för SQL Server Analysis Services (SSAS), varmed dina behörigheter överförs med datakällan).

Instrumentpaneler, rapporter och Excel-arbetsböcker är skrivskyddade, men du kan kopiera och använda instrumentpaneler och rapporter som utgångspunkt för att skapa din egen anpassade version av innehållspaketet.

> [!NOTE]
> Organisationsinnehållspaket är endast tillgängliga när du och dina kollegor använder [Power BI Pro](service-free-vs-pro.md).
> 
> 

## <a name="what-is-appsource"></a>Vad är *AppSource*?
När du publicerar ett organisationsinnehållspaket läggs detta till på AppSource.  Med den här centraliserade databasen är det enkelt för medlemmar att bläddra till och identifiera instrumentpaneler, rapporter och datauppsättningar som har publicerats för dem.  

* Om du vill visa AppSource väljer du **Hämta data** > **Min organisation** > **Hämta**.

Läs mer om att [söka och öppna organisationsinnehållspaket](service-organizational-content-pack-find-and-open.md).

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
* [Power BI – grundläggande begrepp](service-basic-concepts.md)
* Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

