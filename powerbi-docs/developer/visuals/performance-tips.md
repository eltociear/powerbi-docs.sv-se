---
title: Prestandatips
description: Så här skapar du ett visuellt Power BI-objekt med höga prestanda
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: 7ebc02b2c459517957425e78438e12e89dc2e1bb
ms.sourcegitcommit: 1059c6222458f189fb5301dcb689dad2b2c00bc1
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2020
ms.locfileid: "82196570"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>Så här skapar du ett visuellt Power BI-objekt med höga prestanda
Den här artikeln beskriver metoder för hur en utvecklare kan uppnå höga prestanda vid återgivning av visuella objekt. 

Ingen vill att ett visuellt objekt ska ta lång tid att återges och att skapa bästa möjliga prestanda med koden är kritiskt för all återgivning. 

> [!NOTE]
> När vi fortsätter att förbättra plattformen släpps nya versioner av API:et hela tiden. För att få ut mesta möjliga av plattformen och funktionsuppsättningen för visuella Power BI-objekt rekommenderar vi att du håller dig uppdaterad med den senaste versionen.
>
> Sedan vår senaste **version 2.1** har inläsningstiderna för visuella Power BI-objekt förbättrats med i genomsnitt 20 %.

## <a name="power-bi-visual-performance-tips"></a>Prestandatips för visuella Power BI-objekt
Här följer några rekommendationer om hur du uppnår optimala prestanda för visuella objekt. 

### <a name="use-user-timing-api"></a>Använda API för användartidmätning
Genom att använda **API för användartidmätning** för att mäta appens JavaScript-prestanda kan du bestämma vilka delar av skriptet som behöver optimeras.

Mer information finns i [API för användartidmätning](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx).

### <a name="review-animation-loops"></a>Granska animeringsloopar
Ritar animeringsloopen om oförändrade element? 

 - Problem: Det tar tid att rita element som inte ändras från bildruta till bildruta.

 - Lösning: Uppdatera bildrutor selektivt. 
 
När det gäller att animera statiska visualiseringar är det frestande att slå ihop kodritningen i en uppdateringsfunktion och anropa den upprepade gånger med nya data för varje iteration av animeringsloopen.

I stället bör du använda följande uppdateringsmönster med en visualiseringsmetod för att rita allt statiskt, så behöver uppdateringsfunktionen bara rita visualiseringselement som ändras. 

   > [!TIP]
   > Ineffektiva animeringsloopar finns ofta i axlar och förklaringar.

### <a name="cache-dom-nodes"></a>Cachelagra DOM-noder 
När en nod eller lista över noder hämtas från DOM måste du tänka på om du kan återanvända dem i senare beräkningar (ibland även nästa upprepningsslinga). Så länge du inte behöver lägga till eller ta bort ytterligare noder i det aktuella området kan cachelagring av dem förbättra programmets övergripande effektivitet.

För att se till att din kod är snabb och inte saktar ned i webbläsaren så bör du ha minsta möjliga DOM-åtkomst. 

- Innan: 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- Efter: 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>Undvik DOM-manipulering 
Begränsa DOM-manipulering så mycket som möjligt.  Infogningsåtgärder som `prepend()`, `append()` och `after()` är tidskrävande och bör inte användas om det inte behövs.

Till exempel:

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

Exemplet ovan kan göras snabbare med `html()` och med listan skapad i förväg: 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>Fundera över JQuery

Att begränsa dina JS-ramverk och använda inbyggd JS när det är möjligt kan öka den tillgängliga bandbredden och minska bearbetningsbelastningen. Detta kan också begränsa kompatibilitetsproblem med äldre webbläsare. 

Mer information finns på [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) med alternativa exempel för funktioner som JQuerys `show`, `hide`, `addClass` med flera.  

### <a name="use-canvas-or-webgl"></a>Använda Canvas eller WebGL 
Om du vill använda animeringar upprepade gånger bör du använda **Canvas** eller **WebGL** i stället för SVG. Till skillnad från SVG bestäms prestanda med dessa alternativ efter storlek i stället för innehåll. 

Du kan läsa mer om skillnaderna i [SVG jämfört med Canvas: Så här väljer du](https://msdn.microsoft.com/library/gg193983(v=vs.85).aspx). 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>Använda requestAnimationFrame i stället för setTimeout 
Om du använder [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) för att uppdatera dina animeringar på skärmen, anropas dina animeringsfunktioner **innan** webbläsaren anropar en till omritning.

Mer information finns i det här [exemplet](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html) på smidig animering med `requestAnimationFrame`.

## <a name="next-steps"></a>Nästa steg

Lär dig mer om optimeringstekniker i [Optimeringsguide för Power BI](/power-bi/guidance/power-bi-optimization).
