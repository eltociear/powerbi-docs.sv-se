---
title: "Översikt över Power BI-tjänstens program för innehållspaketet"
description: "Certifieringsprogrammet för innehållspaket"
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 01/04/2018
ms.author: maghan
ms.openlocfilehash: f0a50c0aba1a05c55236192a730c3187cb37c055
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2018
---
# <a name="overview-of-the-power-bi-service-content-pack-program"></a>Översikt över Power BI-tjänstens program för innehållspaketet
Ett innehållspaket är en uppsättning färdigt innehåll som låter användare direkt få insikter från en källa. Ett innehållspaket fokuserar vanligtvis på ett specifikt företagsscenario och ger insikter för en roll, en domän eller ett arbetsflöde.

ISV:er kan skapa mallinnehållspaket som låter kunder ansluta och instansiera med sina egna konton. Som domänexperter kan de låsa upp data på ett sätt som är lätt att använda för en företagsanvändare. Innehållspaketen erbjuder ad hoc-övervakning och analys för dina kunder utan att investera mycket i en infrastruktur för rapportering. 

Dessa ISV-skapade mallinnehållspaket kan skickas in till Power BI-teamet för att bli offentligt tillgängliga i Power BI-innehållspaketgalleriet (app.powerbi.com/getdata/services) och på Microsoft AppSource (appsource.microsoft.com). Ett exempel på upplevelsen med offentliga innehållspaket finns [här](template-content-pack-experience.md).

## <a name="overview"></a>Översikt
Den generella processen för att utveckla och skicka in ett mallinnehållspaket omfattar flera steg.

 ![Process](media/service-content-pack-overview/developer-content-pack-overview.png)

1. [Granska kraven för](#requirements) och kontrollera att du uppfyller dem
2. [Skapa innehåll](template-content-pack-authoring.md#queries) i Power BI Desktop
3. [Skapa en instrumentpanel](template-content-pack-authoring.md#dashboard) i PowerBI.com
4. [Testa innehållspaketet](template-content-pack-testing.md) själv inom organisationen
5. [Skicka in](template-content-pack-testing.md#submission) innehållet till Power BI för publicering

<a name="requirements"></a>

## <a name="requirements"></a>Krav
Om du vill skapa och skicka in ett innehållspaket för publicering i PowerBI-tjänsten och AppSource, måste du uppfylla följande krav:

* Du har ett SaaS-program som används av företagsanvändare.
* Ditt SaaS-program har användardata som kan visualiseras i Power BI.
* Ditt SaaS-program har en API som kan nås via det offentliga Internet. Helst är API:et ett REST-baserat API eller ett OData-flöde. Power BI-innehållspaket stöder flera autentiseringstyper som grundläggande autentisering, OAuth 2.0 och API-nyckel. 
* Ditt SaaS-program är godkänt för att publicera ett innehållspaket. Skicka din begäran till pbiservicesapps@microsoft.com. Vi granskar varje överföring efter relevans och förväntad användning. 
* Ett signerat partneravtal. Du kan göra det i [inlämningssteget](template-content-pack-testing.md#submission).

Granska avsnittet [redigering](template-content-pack-authoring.md) för mer information om de tekniska kraven.

## <a name="business-scenario"></a>Företagsscenario
Innehållspaket ger insikter och mått som fokuserar på ett visst företagsscenario. Om du förstår din målgrupp och vad de ska få ut från innehållspaketet så hjälper det att tillse att dina användare lyckas med det innehåll du ger dem.

### <a name="tips"></a>Tips
* Identifiera din målgrupp och den uppgift de försöker utföra  
* Fokusera på en viss tidsperiod (de senaste 90 dagarna) eller de senaste N-resultaten  
* Importera bara tabeller/kolumner som är relaterade till ditt scenario  
* Överväg att erbjuda flera innehållspaket för separata unika scenarier  

## <a name="frequently-asked-questions"></a>Vanliga frågor och svar
**Kan jag skapa ett innehållspaket för Power BI-tjänsten för ett tredje parts SaaS-program som jag inte äger?**

Nej, vi kräver för tillfället signering av ett partneravtal med ägaren för SaaS-programmet innan du publicerar innehållspaketet till tjänsten.

**Jag har ingen offentlig utvecklar-API för min tjänst. Kan jag fortfarande skapa ett innehållspaket för Power BI-tjänsten som hämtar data direkt från datalagret?**

Nej, innehållspaket för Power BI-tjänsten kräver en utvecklar-API som kan nås via det offentliga Internet.

**Vilken typ av API:er stöds av tjänstens innehållspaket och vilka autentiseringstyper kan de fungera med?**

Innehållspaket för Power BI-tjänsten stöder REST API eller OData-flöde. Power BI fungerar med flera olika autentiseringstyper som grundläggande autentisering, OAuth2.0 och Web API-nyckel. Granska avsnittet [redigering](template-content-pack-authoring.md#dashboard) för mer information om de tekniska kraven.

**Jag har fler frågor om innehållspaket för tjänsten. Hur kan jag kontakta er?**

Skicka oss gärna ett e-post med dina frågor på pbiservicesapps@microsoft.com

## <a name="support"></a>Support
För support under utveckling, kan du använda [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support). Det här kontot övervakas och hanteras aktivt. Kundincidenter når snabbt ett lämpligt team.

## <a name="next-step"></a>Nästa steg
[Redigering](template-content-pack-authoring.md)

