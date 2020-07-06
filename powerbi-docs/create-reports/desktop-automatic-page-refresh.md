---
title: Automatisk siduppdatering i Power BI Desktop
description: Den här artikeln visar hur man uppdaterar sidor automatiskt för DirectQuery-källor i Power BI Desktop.
author: davidiseminger
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 06/10/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 1febf93d35500d56f5b3b104487725f33d7b17ad
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85234172"
---
# <a name="automatic-page-refresh-in-power-bi-desktop"></a>Automatisk siduppdatering i Power BI Desktop 

När du övervakar kritiska händelser är det viktigt att data uppdateras så snart som källdata uppdateras. I tillverkningsbranschen är det exempelvis viktigt att upptäcka när en maskin slutat fungera eller är nära att sluta fungera.

Med funktionen för automatisk siduppdatering i Power BI kan din aktiva rapportsida söka efter nya data i fördefinierad takt i [DirectQuery-källor](https://docs.microsoft.com/power-bi/desktop-directquery-about).

## <a name="using-automatic-page-refresh"></a>Använda automatisk siduppdatering

Automatisk siduppdatering är endast tillgängligt för DirectQuery-datakällor.

Om du vill använda automatisk siduppdatering väljer du den rapportsida som du vill aktivera uppdateringen för. Välj ikonen **Formatering** (en målarroller) i fönstret **Visualiseringar** och sök efter **Siduppdatering** längst ned i fönstret. 

![Plats för siduppdatering](media/desktop-automatic-page-refresh/automatic-page-refresh-01.png)

Följande bild visar kortet **Siduppdatering**. De numrerade elementen beskrivs under bilden.

![Kortet Siduppdatering](media/desktop-automatic-page-refresh/automatic-page-refresh-02.png)

1.    Aktiverar eller inaktiverar siduppdatering
2.    Siffervärde för siduppdateringsintervallet
3.    Enhet för siduppdateringsintervallet

På det här kortet kan du aktivera siduppdatering och välja uppdateringens varaktighet. Standardvärdet är 30 minuter. (Det lägsta uppdateringsintervallet är en sekund.) Rapporten kommer att börja uppdateras med det intervall som du har angett. 

## <a name="determining-the-page-refresh-interval"></a>Bestämma siduppdateringsintervallet

När automatisk siduppdatering har aktiverats skickar Power BI Desktop ständigt frågor till DirectQuery-källan. När frågan har skickats uppstår en fördröjning innan data returneras. Så för korta uppdateringsintervall bör du kontrollera att frågorna returnerar den efterfrågade informationen inom det konfigurerade intervallet. Om data inte returneras inom intervallet, så uppdateras de visuella objekten mer sällan än vad de har konfigurerats för.

Det bästa är om uppdateringsintervallet minst matchar din förväntade nya datahastighet:

* Om nya data tas emot av källan var 20:e minut, kan uppdateringsintervallet inte vara kortare än 20 minuter. 

* Om nya data tas emot varje sekund så ställ in intervallet på en sekund. 

När det gäller korta uppdateringsintervall, t. ex. en sekund, så tänk på fölande faktorer:
- Typen av DirectQuery-datakälla
- Den belastning som dina frågor som skapas för den
- Avståndet mellan dina rapportvisningsprogram och kapacitetens datacenter 

Du kan beräkna returtider med hjälp av Prestandaanalys i Power BI Desktop. Med Prestandaanalys kan du kontrollera om varje visuell fråga har tillräckligt med tid för att återkomma med resultatet från källan. Du kan också bestämma var tiden ska användas. Utifrån Prestandaanalys-resultatet kan du justera och göra ändringar i datakällan, eller så kan du experimentera med andra visuella objekt och mått i rapporten.

Den här bilden visar resultatet av en DirectQuery i Prestandaanalys:

![Prestandaanalys-resultat](media/desktop-automatic-page-refresh/automatic-page-refresh-03.png)

Låt oss betrakta några andra egenskaper hos den här datakällan: 

-    Data tas emot med en hastighet på två sekunder. 
-    Prestandaanalys visar en maximal fråga och en visningstid på ungefär 4,9 sekunder (4,688 millisekunder). 
-    Datakällan har konfigurerats för att hantera cirka 1 000 samtidiga frågor per sekund. 
-    Du förväntar dig att cirka 10 användare ska kunna se rapporten samtidigt.

Detta resulterar i följande ekvation:

**5 visuella objekt x 10 användare = cirka 50 frågor**

Den här beräkningen visar en mycket högre belastning än vad datakällan har stöd för. Data tas emot med en hastighet på två sekunder, vilket bör vara din uppdateringsfrekvens. Men eftersom frågan tar ungefär fem sekunder att slutföra, bör du ställa in den på mer än fem sekunder. 

Observera också att det här resultatet kan avvika från när du publicerar rapporten till tjänsten. Skillnaden beror på att rapporten använder den Azure Analysis Services-instans som finns i molnet. Du vill kanske justera dina uppdateringshastigheter enligt detta. 

För att klara av frågor och uppdateringstider kör Power BI nästa uppdateringsfråga först när alla återstående uppdateringsfrågor har slutförts. Så även om uppdateringsintervallet är kortare än den tid som dina frågor tar att bearbeta, uppdateras Power BI inte förrän återstående frågor har slutförts. 

Nu ska vi titta på hur du kan identifiera och diagnostisera prestandaproblem som kapacitetsadministratör. Du kan också läsa avsnittet [Vanliga frågor och svar om automatisk siduppdatering](#frequently-asked-questions) längre fram i den här artikeln om du vill ha mer information om prestanda och felsökning.

## <a name="automatic-page-refresh-in-the-power-bi-service"></a>Automatisk siduppdatering i Power BI-tjänsten

Du kan också ställa in automatiska siduppdateringsintervall för rapporter som har skapats i Power BI Desktop och publicerats i Power BI-tjänsten. 

Om du vill konfigurera automatisk siduppdatering för rapporter i Power BI-tjänsten, så följ steg som liknar dem du använde i Power BI Desktop. Automatisk siduppdatering har även stöd för [inbäddat Power BI](../developer/embedded/embedding.md)-innehåll när det konfigureras i Power BI-tjänsten. Den här bilden visar konfigurationen av **siduppdatering** för Power BI-tjänsten:

![Automatisk siduppdatering i Power BI-tjänsten](media/desktop-automatic-page-refresh/automatic-page-refresh-04.png)

Dessa beskrivningar motsvarar de numrerade elementen: 

1.    Aktiverar eller inaktiverar siduppdatering.
2.    Siffervärde för siduppdateringsintervallet. Måste vara ett heltal.
3.    Enhet för siduppdateringsintervallet.

### <a name="page-refresh-intervals"></a>Siduppdateringsintervall

De siduppdateringsintervall som tillåts i Power BI-tjänsten påverkas av rapportens typ av arbetsyta. Detta gäller för följande rapporter:

* Publicera en rapport i en arbetsyta där automatisk siduppdatering är aktiverat
* Redigera ett siduppdateringsintervall som redan finns på en arbetsyta
* Skapa en rapport direkt i tjänsten

Power BI Desktop har inga begränsningar vad gäller uppdateringsintervall. Uppdateringsintervallet kan vara så frekvent som varje sekund. När rapporter publiceras till Power BI-tjänsten gäller vissa begränsningar. Dessa begränsningar beskrivs i följande avsnitt.

### <a name="restrictions-on-refresh-intervals"></a>Begränsningar för uppdateringsintervall

I Power BI-tjänsten tillämpas begränsningar för automatisk siduppdatering baserat på faktorer som arbetsyta och huruvida du använder Premium-tjänster eller inte.

Vi kan förtydliga hur dessa begränsningar fungerar kan vi börja med lite bakgrundsinformation om kapaciteter och arbetsytor.

*Kapaciteter* är ett viktigt Power BI-begrepp. De representerar en uppsättning resurser (lagring, processor och minne) som används till att vara värd för och leverera Power BI-innehåll. Kapaciteter är antingen delade eller dedikerade. En *delad kapacitet* delas med andra Microsoft-kunder. En *dedikerad kapacitet* allokeras fullt ut till en enskild kund. En introduktion till dedikerade kapaciteter hittar du i artikeln [Hantera Premium-kapaciteter](../admin/service-premium-capacity-manage.md).

I delad kapacitet körs arbetsbelastningar på dataresurser som delas med andra kunder. Eftersom kapaciteten måste dela resurser, införs begränsningar för att säkerställa ett *rättvist genomförande*, t. ex. genom att maximal modellstorlek (1 GB) och maximal daglig uppdateringsfrekvens (åtta gånger per dag) anges.

Power BI-*arbetsytor* finns i kapaciteterna. De representerar säkerhets-, samarbets- och distributionsbehållare. Varje Power BI-användare har en personlig arbetsyta som kallas **Min arbetsyta**. Du kan skapa ytterligare arbetsytor för samarbete och distribution. De kallas för *arbetsytor*. Som standard skapas arbetsytor, däribland personliga arbetsytor, i den delade kapaciteten.

Här visas information om de två scenarierna för arbetsytor:

**Delade arbetsytor**. För vanliga arbetsytor (arbetsytor som inte ingår i en Premium-kapacitet) har den automatiska siduppdateringen ett minsta intervall på 30 minuter (det lägsta tillåtna intervallet).

**Premium-arbetsytor**. Tillgängligheten för automatisk siduppdatering av Premium-arbetsytor beror på vilka arbetsbelastningsinställningar som din Premium-administratör har konfigurerat för Power BI Premium-kapaciteten. Det finns två variabler som kan påverka din möjlighet att konfigurera automatisk siduppdatering:

 - **Funktion på/av**. Om din kapacitetsadministratör har valt att inaktivera funktionen kan du inte konfigurera någon typ av siduppdatering i den publicerade rapporten.

 - **Minsta uppdateringsintervall**. När funktionen aktiveras måste kapacitetsadministratören ange ett lägsta uppdateringsintervall. Om intervallet är lägre än minimivärdet åsidosätter Power BI-tjänsten intervallet och använder det lägsta intervall som angetts av kapacitetsadministratören. Åsidosättningen kallas ”Åsidosättning av kapacitetsadministratör” i följande tabell. 

Den här tabellen innehåller mer information om var den här funktionen är tillgänglig, och vilka begränsningarna är för varje kapacitetstyp och [lagringsläge](../connect-data/service-dataset-modes-understand.md):

| Lagringsläge | Dedikerad kapacitet | Delad kapacitet |
| --- | --- | --- |
| DirectQuery | **Stöds**: Ja <br>**Minsta uppdateringsintervall**: 1 sekund <br>**Åsidosättning av kapacitetsadministratör**: Ja | **Stöds**: Ja <br>**Minsta uppdateringsintervall**: 30 minuter <br>**Åsidosättning av kapacitetsadministratör**: Nej |
| Importera | **Stöds**: Nej <br>**Minsta uppdateringsintervall**: Saknas <br>**Åsidosättning av kapacitetsadministratör**: Saknas | **Stöds**: Nej <br>**Minsta uppdateringsintervall**: Saknas <br>**Åsidosättning av kapacitetsadministratör**: Saknas |
| Blandat läge (DirectQuery + andra datakällor) | **Stöds**: Ja <br>**Minsta uppdateringsintervall**: 1 sekund <br>**Åsidosättning av kapacitetsadministratör**: Ja | **Stöds**: Ja <br>**Minsta uppdateringsintervall**: 30 minuter <br>**Åsidosättning av kapacitetsadministratör**: Nej |
| Live Connect AS | **Stöds**: Nej <br>**Minsta uppdateringsintervall**: Saknas <br>**Åsidosättning av kapacitetsadministratör**: Saknas | **Stöds**: Nej <br>**Minsta uppdateringsintervall**: Saknas <br>**Åsidosättning av kapacitetsadministratör**: Saknas |
| Live Connect PBI | **Stöds**: Nej <br>**Minsta uppdateringsintervall**: Saknas <br>**Åsidosättning av kapacitetsadministratör**: Saknas | **Stöds**: Nej <br>**Minsta uppdateringsintervall**: Saknas <br>**Åsidosättning av kapacitetsadministratör**: Saknas |

> [!NOTE]
> När du publicerar den aktiverade rapporten för automatisk siduppdatering från Power BI Desktop till tjänsten, måste du ange autentiseringsuppgifterna för DirectQuery-datakällan på menyn för datamängdsinställningar.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

Det finns några saker att tänka på när du använder automatisk siduppdatering i Power BI Desktop eller i Power BI-tjänsten:

* Lagringslägena Import, LiveConnect och Push stöds inte av automatisk siduppdatering.  
* Sammansatta modeller som har minst en DirectQuery-datakälla stöds.
* Power BI Desktop har inga begränsningar vad gäller uppdateringsintervall. Intervallet kan vara så frekvent som varje sekund. När rapporter publiceras till Power BI-tjänsten gäller vissa begränsningar, vilket beskrevs [tidigare](#restrictions-on-refresh-intervals) i den här artikeln.

### <a name="performance-diagnostics"></a>Prestandadiagnostik

Automatisk siduppdatering är användbart för att övervaka scenarier och utforska data som snabbt kan ändras. Men ibland kan detta medföra onödig belastning på kapaciteten eller datakällan.

Power BI har följande skydd för att förhindra onödig belastning på datakällorna:

- Alla automatiska siduppdateringsfrågor körs med en lägre prioritet för att säkerställa att interaktiva frågor (t.ex. sidinläsning och korsfiltrering av visuella objekt) prioriteras.
- Om en fråga inte har slutförts före nästa uppdateringscykel, utfärdar Power BI inte några nya uppdateringsfrågor förrän den föregående frågan har slutförts. Om du exempelvis har ett uppdateringsintervall på en sekund och dina frågor i genomsnitt tar fyra sekunder, så utfärdar Power BI endast en fråga var fjärde sekund.

Det finns två områden där du fortfarande kan stöta på flaskhalsar i prestandan:

1. **Kapaciteten**. Frågan träffar först Premium-kapaciteten som utvärderar DAX-frågan som genereras från rapportvisualiseringarna till källfrågorna.
2. **DirectQuery-datakällan**. De översatta frågorna i föregående steg körs sedan mot källan. Källan kan vara dina SQL Server-instanser, SAP Hana-källor och så vidare.

Genom att använda [appen för Premium-kapacitetsmått](../admin/service-admin-premium-monitor-capacity.md), som är tillgänglig för administratörer, kan du visualisera hur mycket av kapaciteten som används av frågor med låg prioritet.

Frågor med låg prioritet består av automatiska siduppdateringsfrågor och modelluppdateringsfrågor. Det finns för närvarande inget sätt att skilja mellan belastningen från automatiska uppdateringsfrågor och modelluppdateringsfrågor.

Om du märker att kapaciteten överbelastas av frågor med låg prioritet finns det några åtgärder som du kan vidta:

- Begär en större Premium-SKU.
- Be rapportens ägare att sänka uppdateringsintervallet.
- I kapacitetsadministratörsportalen kan du:
   - Inaktivera automatisk siduppdatering för den kapaciteten.
   - Höja det lägsta uppdateringsintervallet, vilket påverkar alla rapporter på den kapaciteten.


### <a name="frequently-asked-questions"></a>Vanliga frågor och svar

**Jag är en rapportförfattare. Jag definierade rapportuppdateringsintervallet till en sekund i Power BI Desktop, men efter publiceringen så uppdateras inte min rapport i tjänsten.**

* Se till att automatisk siduppdatering har aktiverats för sidan. Eftersom den här inställningen gäller per sida, måste du se till att den är aktiverad för varje sida i rapporten som du vill uppdatera.
* Kontrollera om du har överfört till en arbetsyta med en ansluten Premium-kapacitet. Om du inte har gjort det, så låses uppdateringsintervallet till 30 minuter.
* Om rapporten finns på en Premium-arbetsyta, så fråga din administratör om funktionen har aktiverats för den anslutna kapaciteten. Se dessutom till att det lägsta uppdateringsintervallet för kapaciteten är lägre eller detsamma som intervallet för rapporten.

**Jag är en kapacitetsadministratör. Jag ändrade inställningarna för sidans automatiska uppdateringsintervall, men ändringarna visas inte. Det innebär att rapporterna fortfarande uppdateras i felaktig takt, eller inte uppdateras alls trots att jag har aktiverat automatisk siduppdatering.**

* Det tar upp till 5 minuter innan de ändrade inställningarna av automatisk siduppdatering i användargränssnittet för kapacitetsadministratörer sprids till rapporterna.
* Förutom att aktivera automatisk siduppdatering för kapaciteten, måste du också aktivera den för de sidor i rapporten för vilka du vill aktivera den.

**Min rapport körs i blandat läge. (Blandat läge innebär att rapporten har en DirectQuery-anslutning och en importdatakälla.) Vissa visuella objekt uppdateras inte.**

- Om dina visuella objekt refererar till importtabeller, så är det helt normalt. Automatisk siduppdatering stöds inte för import.
- Se den första frågan i det här avsnittet.

**Rapporten uppdaterades utan problem i tjänsten, men sedan slutade det plötsligt att fungera.**

* Försök att uppdatera sidan och se om det löser problemet.
* Kontakta din kapacitetsadministratör. Administratören kan ha inaktiverat funktionen eller höjt det minsta uppdateringsintervallet. (Se den andra frågan i det här avsnittet.)

**Jag är en rapportförfattare. Mina visuella objekt uppdateras inte i den takt jag specificerade. De uppdateras i en lägre hastighet.**

* Om dina frågor tar längre tid att köra, så fördröjs uppdateringsintervallet. Den automatiska siduppdateringen väntar tills alla frågor har slutförts innan nya påbörjas.
* Din kapacitetsadministratör kan ha angett ett minsta uppdateringsintervall som är högre än det som du angav i rapporten. Be din kapacitetsadministratör att sänka det lägsta uppdateringsintervallet.

**Hanteras automatiska siduppdateringsfrågor från cacheminnet?**

* Nej. Alla automatiska siduppdateringsfrågor kringår eventuella cachelagrade data.


## <a name="next-steps"></a>Nästa steg

Mer information finns i de här artiklarna:

* [Använd DirectQuery i Power BI](../connect-data/desktop-directquery-about.md)
* [Använda sammansatta modeller i Power BI Desktop](../transform-model/desktop-composite-models.md)
* [Använda Prestandaanalys till att undersöka prestanda för rapportelement](desktop-performance-analyzer.md)
* [Distribuera och hantera Power BI Premium-kapaciteter](../guidance/whitepaper-powerbi-premium-deployment.md)
* [Datakällor i Power BI Desktop](../connect-data/desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](../connect-data/desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](../connect-data/desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](../connect-data/desktop-enter-data-directly-into-desktop.md)   
