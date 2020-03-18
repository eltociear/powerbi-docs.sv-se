---
title: Rapportvy i Power BI Desktop
description: Rapportvy i Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: a840a549e5dee79406ddfb2a07877895ce7b6c0f
ms.sourcegitcommit: 7e845812874b3347bcf87ca642c66bed298b244a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79206802"
---
# <a name="work-with-report-view-in-power-bi-desktop"></a>Arbeta med rapportvyn i Power BI Desktop

Om du har arbetat med Power BI, vet du hur enkelt det är att skapa rapporter som ger dynamiska perspektiv och insikter om dina data. Power BI har också fler avancerade funktioner i Power BI Desktop. Du kan använda Power BI Desktop till att skapa avancerade frågor, kombinera data från flera källor, skapa relationer mellan tabeller och mycket mer.

Power BI Desktop innehåller en *rapportvy* där du kan skapa ett obegränsat antal rapportsidor med visualiseringar. Rapportvyn i Power BI Desktop har en liknande designupplevelse som rapportens redigeringsvy i *Power BI-tjänsten*. Du kan flytta runt visuella objekt, kopiera och klistra in, sammanfoga och så vidare.

Skillnaden mellan dessa är att när du använder Power BI Desktop kan du arbeta med dina frågor och modellera dina data så att dina data ger de bästa insikterna i dina rapporter. Du kan spara Power BI Desktop-filen var du vill, oavsett om det är en lokal hårddisk eller till molnet.

## <a name="lets-take-a-look"></a>Låt oss ta en titt!

När du läser in data i Power BI Desktop första gången, ser du rapportvyn med en tom arbetsyta.

![Power BI Desktop](media/desktop-report-view/pbi_reportviewinpbidesigner_reportview.png)

Du kan växla mellan vyerna **Rapport**, **Data** och **Relation** genom att välja ikonerna i det vänstra navigationsfönstret:

![Rapportvy-ikonen](media/desktop-report-view/pbi_reportviewinpbidesigner_changeview.png)

När du har lagt till data, kan du lägga till fält i en ny visualisering på arbetsytan.

![Lägg till ett visuellt objekt genom att dra från Fält-fönstret](media/desktop-report-view/pbid_reportview_addvis.gif)

Om du vill ändra typen av visualisering kan du välja den på arbetsytan och sedan välja en ny typ i **Visualiseringar**.

![Ändra ett visuellt objekt genom att välja ett nytt](media/desktop-report-view/pbid_reportview_changevis.gif)

> [!TIP]
> Se till att experimentera med olika typer av visuella objekt. Det är viktigt att din visualisering förmedlar informationen i dina data på ett tydligt sätt.

En rapport har minst en tom sida från början. Sidor visas i fönstret navigator till vänster om arbetsytan. Du kan lägga till alla typer av grafik på en sida, men det är viktigt att inte överdriva. För många visualiseringar på en sida gör det svårt att hitta rätt information. Du kan lägga till nya sidor i rapporten. Klicka bara på **Ny sida** i menyfliksområdet.

![Ny sida-ikonen](media/desktop-report-view/pbidesignerreportviewnewpage.png)

Om du vill ta bort en sida klickar du på **X** på sidans flik längst ned i rapportvyn.

![Lägga till en sida i en rapport](media/desktop-report-view/pbi_reportviewinpbidesigner_deletepage.png)

> [!NOTE]
> Rapporter och visualiseringar går inte att fästa på en instrumentpanel från Power BI Desktop. För att göra det måste du publicera dem till din Power BI-webbplats. Mer information finns i [Publicera datamängder och rapporter från Power BI Desktop](desktop-upload-desktop-files.md).

## <a name="copy-and-paste-between-reports"></a>Kopiera och klistra in mellan rapporter

Det är enkelt att ta ett visuellt objekt från en Power BI Desktop-rapport och klistra in det i en annan rapport. Använd kortkommandot CTRL+C för att kopiera rapportens visuella objekt. I den andra Power BI Desktop-rapporten använder du CTRL+V för att klistra in det visuella objektet i rapporten. Du kan välja ett visuellt objekt i taget, eller så kan du välja att kopiera alla visuella objekt på en sida och därefter klistra in dem i Power BI Desktops målrapport.

Möjligheten att kopiera och klistra in visuella objekt är användbart för personer som skapar och uppdaterar flera rapporter ofta. När du kopierar mellan filer, så överförs inställningar och formatering som uttryckligen har ställts in i formateringsfönstret, medan visuella element som förlitar sig på ett tema eller standardinställningarna automatiskt uppdateras för att matcha temat för målrapporten. Så när du får ett visuellt objekt formaterat så det ser ut precis som du vill så kan du kopiera och klistra in det visuella objektet i nya rapporter och spara allt ditt formateringsarbete.

Om fälten i din modell är olika, visas ett fel i det visuella objektet och en varning om vilka fält som saknas. Felet liknar den upplevelse du får när du tar bort ett fält i modellen som det visuella objektet använder.

![Fel vid kopiera/klistra in visuellt objekt – inget datafält](media/desktop-report-view/report-view_07.png)

Åtgärda felet genom att ersätta det trasiga fältet med de fält som du vill använda från modellen i rapporten där du klistrade in det visuella objektet. Om du använder ett anpassat visuellt objekt så måste du även importera det anpassade visuella objektet till målrapporten.

## <a name="hide-report-pages"></a>Dölja rapportsidor

När du skapar en rapport har du även möjlighet att dölja sidor i den. Detta kan vara användbart om du behöver skapa underliggande data eller visuella objekt i en rapport, men inte vill att dessa sidor ska vara synliga för andra, t.ex. när du skapar tabeller eller stödjande visuella objekt som används på andra rapportsidor. Det finns många andra kreativa orsaker till att du kanske vill skapa en rapportsida och sedan dölja den från en rapport som du vill publicera.

Det är lätt att dölja en rapportsida. Du högerklickar helt enkelt på rapportsidans flik och väljer **Dölj** på den meny som visas.

![Alternativet Dölj sida](media/desktop-report-view/report-view_05.png)

Det finns vissa saker du bör tänka på när du döljer en rapportsida:

* Du kan fortfarande se en dold rapportvy i Power BI Desktop, även om sidans rubrik är gråtonad. I följande bild döljs sida 4.

    ![nedtonad sida som är dold](media/desktop-report-view/report-view_06.png)

* Du *kan inte* se en dold rapportsida när du visar rapporten i Power BI-tjänsten.

* Att dölja en rapportsida är *inte* en säkerhetsåtgärd. Användare kan fortfarande använda sidan, och dess innehåll är fortfarande tillgängligt när du visar detaljerad information eller använder andra metoder.

* När en sida är dold i visningsläge, visas inga navigeringspilar.
