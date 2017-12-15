---
title: "Så här använder du frågor och svar i Power BI"
description: "Så här använder du frågor och svar i Power BI"
services: powerbi
documentationcenter: 
author: mihart
manager: kfile
editor: 
tags: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 09/25/2017
ms.author: mihart
ms.openlocfilehash: a6736916a4bb2e94c1f5e1e3c3c3e5339cf990ec
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/13/2017
---
# <a name="how-to-use-power-bi-qa"></a>Så här använder du frågor och svar i Power BI
## <a name="ask-questions-of-your-data-using-natural-language"></a>Ställ frågor om dina data med naturligt språk
Starta på en instrumentpanel. Frågerutan frågor och svar är där du skriver in din fråga med naturligt språk. Frågor och svar kan identifiera de ord du skriver och lista ut var (i vilken datauppsättning) som svaret finns. Frågor och svar hjälper dig också att formulera din fråga med automatisk komplettering, omformulering och andra textbaserade och visuella hjälpmedel.

![](media/service-how-to-q-and-a/powerbi-qna.png)

Svaret på din fråga visas som en interaktiv visualisering och uppdateras allteftersom du ändrar frågan.

Frågor och svar är interaktivt och till och med roligt. Ofta leder en fråga till flera andra när visualiseringarna avslöjar intressanta spår att följa upp. Titta när Amanda demonstrerar frågor och svar för att skapa visuella objekt, granska dem på djupet och fästa dem till instrumentpaneler.

> [!NOTE]
> Frågor och svar finns också tillgängligt i [Microsoft Power BI-appen för iOS på iPad-, iPhone- och iPod Touch-enheter](mobile-apps-ios-qna.md).
> 
> 

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="use-natural-language-to-ask-questions-about-your-data"></a>Använd naturligt språk för att ställa frågor om dina data
1. Placera markören i frågerutan. Innan du ens börjar skriva, visar frågor och svar en ny skärm med förslag för att hjälpa dig formulera din fråga.
   
   ![](media/service-how-to-q-and-a/powerbi-qna-cursor.png)  
   
   Den här listan innehåller:  
   a.  frågor som används för att skapa [paneler ](service-dashboard-tiles.md)som redan är fästa på instrumentpanelen och  
   b.  namnet på tabeller i [underliggande datauppsättningar](service-get-data.md).  
   
   Du kan alltid välja en av dessa frågor som en startpunkt och fortsätta att förfina frågan för att hitta det specifika svar som du letar efter. Eller använd ett tabellnamn för att hjälpa dig uttrycka en ny fråga.
2. Välj från listrutan eller börja skriva in din egen fråga.  
   
   ![](media/service-how-to-q-and-a/powerbi-qna-list.png)
3. Medan du skriver din fråga, väljer Power BI frågor och svar ut den bästa [visualiseringen](power-bi-visualization-types-for-reports-and-q-and-a.md)för att visa ditt svar och den ändras dynamiskt allteftersom du ändrar frågan. Frågor och svar hjälper dig också att formulera din fråga med automatisk komplettering, genom att omformulera din fråga och med andra textbaserade och visuella hjälpmedel.  
   ![](media/service-how-to-q-and-a/powerbi-qna-viz.png)
4. När du skriver en fråga, letar Power BI efter ett svar i alla datauppsättningar som har en panel på den instrumentpanelen.  Om alla paneler är från *datauppsättning A* så kommer ditt svar att komma från *datauppsättning A*.  Om det finns paneler från *datauppsättning A* och *datauppsättning B* så letar frågor och svar efter det bästa svaret från de två datauppsättningarna.
   
   > [!TIP]
   > Så var försiktig, om du bara har en panel från *datauppsättning A* och du tar bort den från instrumentpanelen, kommer frågor och svar inte längre att ha åtkomst till *datauppsättning A*.
   > 
   > 
5. När du är nöjd med resultatet, [fäster du visualiseringen till en instrumentpanel](service-dashboard-pin-tile-from-q-and-a.md) genom att välja fästikonen i det övre högra hörnet. Om instrumentpanelen har delats med dig, eller är en del av en app, kan du inte fästa.
   
   ![](media/service-how-to-q-and-a/pbi_qna_finish-typing-question.jpg)

### <a name="tell-qa-which-visualization-to-use"></a>Berätta för frågor och svar vilken visualisering som ska användas.
Med frågor och svar, kan du inte bara be dina data att tala för sig själva, du kan instruera dem hur du vill att de visas. Lägg bara till som en <visualization type> i slutet av din fråga.  Till exempel visa lagervolymer efter anläggning som en karta och visa totalt lager som ett kort.  Prova själv.

## <a name="how-does-qa-know-how-to-answer-questions"></a>Hur kan frågor och svar veta hur de ska svara på frågor?
### <a name="which-datasets-does-qa-use"></a>Vilka datauppsättningar använder sig frågor och svar av?
Hur kan frågor och svar veta hur de ska svara på dataspecifika frågor? Den förlitar sig på namnen på tabellerna, kolumnerna och de beräknade fälten i den underliggande datauppsättningen. Så det du (eller datauppsättningens ägare) kallar saker och ting är viktigt! 

Anta att du har en Excel-tabell som heter försäljning, med kolumner som heter produkt, månad, sålda enheter, bruttoförsäljning och resultat. Du skulle kunna ställa frågor om vilken som av de entiteterna.  Du skulle kunna säga visa *försäljning*, totala *vinster* per *månad*, sortera *produkter* efter *sålda enheter* och mer.

Frågor och svar kan besvara frågor som baseras på hur din datauppsättning är strukturerad. Hur fungerar detta för data i Salesforce? När du ansluter till ditt konto i salesforce.com, skapar Power BI automatiskt en instrumentpanel.  Innan du börjar ställa frågor med frågor och svar, kan du kolla på de data som visas i instrumentpanelens visualiseringar och på de data som visas i listmenyn för frågor och svar.

* Om visualiseringarnas axeletiketter och värden inkluderar försäljning, konto, månad och affärsmöjligheter så kan du ställa frågor som: vilket *konto* har de högsta *affärsmöjligheterna*, eller visa *försäljning* per månad som ett stapeldiagram.
* Om listmenyn innehåller säljare, status och år, kan du till exempel fråga frågor som: vilken *säljare* hade den lägsta *försäljningen* i *Florida* under *2013*.

Om du har webbplats-prestandadata i Google Analytics, kan be frågor och svar om tiden som lagts ner på en webbsida, antalet unika besök och användarengagemang. Eller, om du frågar demografisk data, kan du ställa frågor om ålder om hushållets inkomst efter plats.

### <a name="which-visualization-does-qa-use"></a>Vilken visualisering använder sig frågor och svar av?
Frågor och svar väljer den bästa visualiseringen baserat på de data som visas. Ibland definieras data i de underliggande datauppsättningarna som en viss typ eller kategori och det hjälper frågor och svar att veta hur de ska visas. Om data till exempel har definierats som en datumtyp, är det troligare att de ska visas som ett linjediagram. Data som kategoriseras som en stad visas mer troligt som en karta.

Du kan också säga till frågor och svar vilka visualiseringar som ska användas genom att lägga till det i din fråga. Men kom ihåg att det inte alltid är möjligt för frågor och svar att visa data i den visualiseringstyp du begärt.

Information om nyckelord som frågor och svar känner igen finns i [tips för att ställa frågor](service-q-and-a-tips.md).

## <a name="next-steps"></a>Nästa steg
Gå tillbaka till [Frågor och svar i Power BI](service-q-and-a.md)  
[Självstudie: använd frågor och svar med detaljhandelsexemplet](power-bi-visualization-introduction-to-q-and-a.md)  
[Tips för att ställa frågor i frågor och svar](service-q-and-a-tips.md)  
[Förbered en arbetsbok för frågor och svar](service-prepare-data-for-q-and-a.md)  
[Fäst en panel på instrumentpanelen från frågor och svar](service-dashboard-pin-tile-from-q-and-a.md)  

