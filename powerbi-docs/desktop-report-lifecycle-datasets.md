---
title: Ansluta till datauppsättningar i Power BI-tjänsten från Power BI Desktop
description: Använda en gemensam datamängd för flera Power BI Desktop-rapporter på flera arbetsytor och hantera din rapportlivscykel
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/07/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 8b68f6ee5e475c1b53f914c84372a0875fe87b5d
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839112"
---
# <a name="connect-to-datasets-in-the-power-bi-service-from-power-bi-desktop"></a>Ansluta till datauppsättningar i Power BI-tjänsten från Power BI Desktop
Du kan upprätta en live-anslutning till en delad datauppsättning i Power BI-tjänsten och skapa olika rapporter från samma datauppsättning. Det här innebär att du kan skapa den perfekta datamodellen i Power BI Desktop och publicera den till Power BI-tjänsten. Sedan kan du och andra skapa flera olika rapporter (i separata .pbix-filer) från samma, gemensamma datamodell och spara dem på olika arbetsytor. Den här funktionen kallas **Live-anslutning till Power BI-tjänst**.

![Hämta data från Power BI-tjänsten](media/desktop-report-lifecycle-datasets/report-lifecycle_01.png)

Det finns olika typer av fördelar med den här funktionen, inklusive metodtips som vi kommer att diskutera i den här artikeln. Det finns också några överväganden och begränsningar, så se till att du har läst igenom dem – de är i slutet av den här artikeln.

## <a name="using-a-power-bi-service-live-connection-for-report-lifecycle-management"></a>Använda live-anslutning till Power BI-tjänsten för livscykelhantering av rapporter
En utmaning med att Power BI är så populärt är den ökande mängden rapporter, instrumentpaneler och deras underliggande datamodeller. Anledningen är att det är enkelt att skapa intressanta rapporter i **Power BI Desktop**, dela ([publicera](desktop-upload-desktop-files.md)) rapporterna i **Power BI-tjänsten** och att skapa bra instrumentpaneler från dessa datauppsättningar. Eftersom många personer har gjort det, ofta med samma (eller nästan samma) datauppsättningar, blir det svårt att veta vilken rapport som baseras på vilken datauppsättning – och hur ny varje datauppsättning är. Med **Live-anslutning till Power BI-tjänst** löser man utmaningen genom att skapa, dela och expandera gemensamma datauppsättningsrapporter och instrumentpaneler på ett enklare och mer konsekvent sätt.

### <a name="create-a-dataset-everyone-can-use-then-share-it"></a>Skapa en datauppsättning som alla kan använda och dela den sedan
Anta att Anna (en affärsanalytiker) är med i din grupp och att hon är duktig på att skapa bra datamodeller (s.k. datauppsättningar). Med Annas expertis kan hon skapa en datauppsättning och rapport och sedan dela rapporten i **Power BI-tjänsten**.

![Registrera dig på Power BI-tjänsten](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Alla gillar hennes rapport och hennes datauppsättning, och det är där det skulle kunna bli problem – alla i teamet försöker skapa *sin egen version* av datauppsättningen och sedan dela sina egna rapporter med gruppen. Plötsligt finns det mängder med rapporter (från olika datauppsättningar) på din grupps arbetsyta i **Power BI-tjänsten**. Vilken är den senaste? Är datauppsättningarna identiska, eller bara nästan? Vilka skillnader är det? Med funktionen **Live-anslutning till Power BI-tjänst** kan allt ändras till det bättre. I nästa avsnitt ser vi hur andra kan använda Annas publicerade datamängd till sina egna rapporter, på egna arbetsytor, och att alla kan använda samma granskade och publicerade datamängd när de skapar sina egna unika rapporter.

### <a name="connect-to-a-power-bi-service-dataset-using-a-live-connection"></a>Ansluta till en Power BI-tjänsts datauppsättning med hjälp av en live-anslutning
När Anna skapar sin rapport (och skapar datauppsättningen som den baseras på) publicerar hon den till **Power BI-tjänsten** och den visas på arbetsytan för hennes grupp i Power BI-tjänsten. Om hon sparar den på en *ny upplevelsearbetsyta* kan hon ställa in behörigheten Skapa så att den blir tillgänglig att visa och använda för alla både inom och utanför arbetsytan.

Mer information om de nya upplevelsearbetsytorna finns i avsnittet om [apparbetsytor](service-new-workspaces.md).

Andra medlemmar både inom och utanför arbetsytan kan nu upprätta en liveanslutning till Annas delade datamodell (med **liveanslutning till Power BI-tjänsten**) och skapa egna unika rapporter från *hennes ursprungliga datamängd* på *en egen ny upplevelsearbetsyta*.

I följande bild kan du se hur Anna skapar en **Power BI Desktop**-rapport och publicerar den (med datamodellen) till **Power BI-tjänsten**. Sedan kan andra ansluta till hennes datamodell med **liveanslutning till Power BI-tjänsten** och skapa egna unika rapporter på egna arbetsytor baserade på hennes datamängd.

![Flera rapporter baserade på samma datamängd](media/desktop-report-lifecycle-datasets/report-lifecycle_03.png)

> [!NOTE]
> Om du sparar din datamängd på en [klassisk delad arbetsyta](service-create-workspaces.md) så kan endast medlemmar på arbetsytan skapa rapporter baserade på datamängden. För att upprätta en live-anslutning till Power BI-tjänsten, måste datauppsättningen som du vill ansluta till finnas i en delad arbetsyta där du är medlem.
> 
> 

## <a name="step-by-step-for-using-the-power-bi-service-live-connection"></a>Stegvisa instruktioner för att använda en live-anslutning till Power BI-tjänsten
Nu när vi vet hur användbar **liveanslutningar till Power BI-tjänsten** är och hur du kan använda dem för hantering av rapporternas livscykel, så kan vi gå igenom de steg som tog oss från Annas utmärkta rapport (och datamängd) till en delad datamängd som medlemmarna i hennes Power BI-team kan använda.

### <a name="publish-a-power-bi-report-and-dataset"></a>Publicera en Power BI-rapport och datauppsättning
Det första steget i att hantera rapportlivscykeln med **Live-anslutning till Power BI-tjänst** är att ha en rapport (och datauppsättning) som gruppmedlemmarna vill använda. Så Anna måste först **publicera** sin rapport från **Power BI Desktop**. Hon gör detta genom att välja **Publicera** från **Start** i menyfliksområdet i Power BI Desktop.

![Publicera en rapport](media/desktop-report-lifecycle-datasets/report-lifecycle_02a.png)

Om hon inte har loggat in på sitt konto för Power BI-tjänsten, uppmanas hon att göra detta.

![Logga in på Power BI Desktop](media/desktop-report-lifecycle-datasets/report-lifecycle_04.png)

Därifrån kan hon välja arbetsytans mål där rapporten och datauppsättningen ska publiceras. Kom ihåg att om hon sparar den på en ny upplevelsearbetsyta så har alla med behörigheten Skapa åtkomst till datamängden. Du ställer in behörigheten Skapa i Power BI-tjänsten efter publiceringen. Om hon sparar den på en klassisk arbetsyta är det bara medlemmar som har åtkomst till arbetsytan där rapporten har publicerats som kan komma åt dess datamängd med hjälp av en **liveanslutning till Power BI-tjänsten**.

![Registrera dig på Power BI-tjänsten](media/desktop-report-lifecycle-datasets/report-lifecycle_05.png)

Publiceringsprocessen påbörjas och **Power BI Desktop** visar förloppet.

![Publicering pågår](media/desktop-report-lifecycle-datasets/report-lifecycle_06.png)

När det är klart visar **Power BI Desktop** detta och ger dig några länkar för att komma till själva rapporten i **Power BI-tjänsten**, samt en länk till **Quick Insights** i rapporten.

![Publiceringen lyckades](media/desktop-report-lifecycle-datasets/report-lifecycle_07.png)

Nu när rapporten och dess datamängd finns i Power BI-tjänsten kan du även *höja upp* den som ett tecken på dess kvalitet och tillförlitlighet. Du kan även begära att den ska *certifieras* av en central beslutsfattare i Power BI-klientorganisationen. Med något de här godkännandena visas datamängden alltid i ämneslistan när användare söker efter datamängder. Om du är intresserad kan du läsa mer om hur du [höjer upp din datauppsättning](service-datasets-promote.md). 

Det sista steget är att ställa in *behörigheten Skapa* datamängden som rapporten är baserad på. Behörigheten Skapa avgör vem som kan se och använda datamängden. Du kan ställa in den på själva arbetsytan eller när du delar en app från arbetsytan. Läs mer om att ställa in [behörigheten Skapa](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

Nu ska vi se hur andra gruppmedlemmar som har åtkomst till arbetsytan där rapporten (och datauppsättningen) är publicerad kan ansluta till datauppsättningen och skapa egna rapporter.

### <a name="establish-a-power-bi-service-live-connection-to-the-published-dataset"></a>Gå till den publicerade datauppsättningen med en live-anslutning till Power BI-tjänsten
För att upprätta en anslutning till den publicerade rapporten och skapa en egen rapport som baseras på den publicerade datamängden väljer du **Hämta data** i menyfliksområdet **Start** i **Power BI Desktop**. Välj **Power BI** i det vänstra fönstret och sedan **Power BI-datauppsättningar**.

Om du inte har loggat in på Power BI, uppmanas du att göra detta. När du har loggat in ser du ett fönster med de arbetsytor som du är medlem i. Du kan välja den arbetsyta som innehåller datauppsättningen som du vill upprätta en **Live-anslutning till Power BI-tjänst** till.

Datamängderna i listan är de delade datamängder som du har behörigheten Skapa för, oavsett arbetsyta. Du kan söka efter en viss datamängd och se dess namn, ägare, arbetsytan där den finns och när den senast uppdaterades. Du ser även *godkända* datamängder överst i listan, som antingen certifierats eller höjts upp. 

![Lista med tillgängliga datamängder](media/desktop-report-lifecycle-datasets/desktop-select-shared-dataset.png)

När du väljer **Läs in** i fönstret upprättar du en live-anslutning till den valda datauppsättningen vilket innebär att de data som du ser (fält och deras värden) blir inlästa i **Power BI Desktop** i realtid.

![Fältet Datamängd i fönstret Fält](media/desktop-report-lifecycle-datasets/report-lifecycle_10.png)

Nu kan du (och andra) skapa och dela anpassade rapporter från samma datauppsättning. Detta är ett bra sätt att ha en person med kunskap att skapa en genomtänkt datauppsättning (som t.ex. Anna gör) och sedan låta flera medarbetare använda den delade datauppsättningen till att skapa sina egna rapporter.

## <a name="limitations-and-considerations"></a>Begränsningar och överväganden
När du använder **Live-anslutning till Power BI-tjänst** finns det några begränsningar och överväganden som du bör komma ihåg.

* Det är bara användare med behörigheten Skapa för en datamängd som kan ansluta till den publicerade datamängden med en **liveanslutning till Power BI-tjänsten**. 
* Användare av den kostnadsfria versionen ser endast datamängder från Min arbetsyta och Premium-baserade arbetsytor.
* Eftersom detta är en live-anslutning är vänsternavigering och modellering inaktiverade, vilket liknar hur det fungerar när du ansluter till **SQL Server Analysis Services**.
* Eftersom det är en live-anslutning tvingas RLS (säkerhet på rad- och rollnivå), OneDrive för företag och andra anslutningar på samma sätt som de gör när man är ansluten till **SQL Server Analysis Services**.
* Om ägaren ändrar den ursprungliga delade .pbix-filen, kommer datauppsättningen och rapporten som delas i **Power BI-tjänsten** att skrivas över. Rapporter baserade på datamängden skrivs inte över, men eventuella ändringar i datamängden visas i rapporten.
* Medlemmar i en arbetsyta kan inte byta ut den ursprungliga delade rapporten. Om du försöker göra detta visas en varning som uppmanar dig att byta namn på filen och publicera.
* Om du tar bort den delade datamängden i **Power BI-tjänsten** så fungerar inte andra rapporter som är baserade på datamängden och de visuella objekten visas inte.
* För innehållspaket måste du först skapa en kopia av ett innehållspaket innan du använder det som en bas för att dela en .pbix-rapport och datauppsättning till **Power BI-tjänsten**.
* När innehållspaket från *Min organisation* har kopierats kan du inte ersätta rapporten som skapades i tjänsten, och/eller en rapport som skapats vid kopiering av ett innehållspaket, med en live-anslutning. Om du försöker göra detta visas en varning som uppmanar dig att byta namn på filen och publicera. I den här situationen kan du bara byta ut de publicerade live-anslutna rapporterna.
* Om du tar bort en delad datamängd i **Power BI-tjänsten** så kan ingen längre komma åt datamängden från **Power BI Desktop**.

