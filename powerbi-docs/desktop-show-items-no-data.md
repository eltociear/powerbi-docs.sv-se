---
title: Visa objekt utan data i Power BI
description: Lär dig hur Power BI hanterar och visar objekt utan data
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/16/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: a8d99a041edbbe353badbb580940e918b30a0a9d
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879717"
---
# <a name="show-items-with-no-data-in-power-bi"></a>Visa objekt utan data i Power BI

Med Power BI kan du visualisera alla typer av data från olika källor. När du skapar ett visuellt objekt så visar Power BI endast relevanta data när du skapar ett visuellt objekt för att korrekt kunna hantera hur data presenteras och visas. Power BI fastställer vilka data som är relevanta utifrån det visuella objektets konfiguration och den underliggande datamodellen. I den här artikeln beskrivs hur Power BI fungerar vid fastställande av relevanta data, med exempel som visar hur besluten fattas.

![Aktivera funktionen Visa poster utan data](media/desktop-show-items-no-data/show-items-no-data_02.png)

## <a name="determining-relevant-data"></a>Fastställa relevanta data

Om du vill förstå hur Power BI fastställer vilka data som är relevanta att visa kan du ta en tabell som ett enkelt exempel. Med hjälp av den modell som representeras i avsnittet [Exempeldatamodell](#example-data-model), som finns i slutet av den här artikeln, kan du överväga att skapa en tabell med följande inställningar:

**1. Grupper från samma tabell:** *Product[Color] – Product[Size]*

|*Product[Color]*  |*Product[Size]*  |
|---------|---------|
|Blå     |Stor         |
|Blå     |Medium         |
|Blå     |Liten         |
|Röd     |Stor         |

I det här exemplet visar Power BI kombinationer av *[Color-Size]* som finns i tabellen *[Product]* . 

Låt oss titta på en annan kombination:

**2. Grupper från olika med direkt relaterade tabeller och ett mått:** *ProductStyle[Finish] – Product[Color] – Sum(Sales[Quantity])*

|*ProductStyle[Finish]*  |*Product[Color]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Blank     |Blå         |10         |
|Matt     |Blå         |15         |

I det här exemplet visar Power BI bara befintliga kombinationer. Därför visas t.ex. inte (”None” + ”Blue”) eller (”Matt” + ”Red”) eftersom de kombinationerna inte finns i modellen. Det villkor som avgör vilka kombinationer finns är att värdet för *Sum(Sales[Quantity])* inte är tomt.

Låt oss titta på ett annat exempel: 

**3. Grupper från olika men relaterade tabeller och inget mått:** *ProductStyle[Finish] – Product[Color]*

|*ProductStyle[Finish]*  |*Product[Color]*  |
|---------|---------|
|Blank     |Blå         |
|Blank     |Röd         |
|Matt     |Blå         |

Eftersom det inte finns något explicit mått, och eftersom de två tabellerna är direkt relaterade, försöker Power BI mata in ett mått för att begränsa de resulterande kombinationerna. I det här fallet lägger Power BI in ett *CALCULATE(COUNTROWS('Product'))* -mått, som inte får vara tomt, eftersom *Product* är den tabell som är gemensam för båda tabellerna.

Därför visar Power BI de kombinationer som har poster i Product-tabellen, vilket utesluter kombinationerna *(”None” + ”Blue”)* och *(”Matte” + ”Red”)* .

**4. Grupper från olika och orelaterade tabeller**

Exempelmodellen har inte den här kombinationen, men om det skulle finnas grupper från olika och orelaterade tabeller så skulle Power BI inte kunna relatera de två kolumnerna. Resultatet skulle bli en korsprodukt av alla värden för varje kolumn. I en sådan situation utfärdar Power BI ett fel av typen *obegränsad anslutning* eftersom sådana anslutningar är dyra att beräkna i databasen och inte förser användaren med särskilt mycket information. 

![Felet som visas för en obegränsad anslutning](media/desktop-show-items-no-data/show-items-no-data_01.png)


## <a name="showing-items-with-no-data"></a>Visa poster utan data

I föregående avsnitt beskrivs hur Power BI fastställer vilka data som är relevanta att visa. Men det kan förekomma tillfällen när du *vill* att visa objekt utan data. 

Med funktionen **Visa poster utan data** kan du göra just detta, dvs inkludera datarader och kolumner som inte innehåller måttdata (tomma måttvärden).

Aktivera funktionen **Visa objekt utan data** så att den kan välja ett visuellt objekt, och högerklicka sedan på fältet i **Fält** och välj **Visa objekt utan data** på den meny som visas, så som visas i följande bild:

![Aktivera funktionen Visa poster utan data](media/desktop-show-items-no-data/show-items-no-data_02.png)


Funktionen **Visa poster utan data** har *inte* någon effekt under följande förhållanden:

* Inget mått har lagts till i det visuella objektet, och grupperingskolumnerna kommer från samma tabell
* Grupperna är orelaterade, Power BI kör inte frågor för visuella objekt som har orelaterade grupper
* Måttet relaterar inte till någon av grupperna. Det beror på att måttet aldrig kommer att vara tomt enbart för endast vissa gruppkombinationer
* Det finns ett användardefinierat måttfilter som exkluderar tomma mått, exempelvis: *SalesAmount > 0*

### <a name="how-show-items-with-no-data-works"></a>Så här fungerar Visa poster utan data

De mest intressanta exemplen på **Visa poster utan data** är när måtten är närvarande. Låt oss titta på en situation där grupperna kommer från samma tabell, eller kan vara relaterade via en sökväg i modellen. *ProductStyle* är t.ex. direkt relaterat till *Product* och indirekt relaterat till *Sales*, och *ProductStyle* och *ProductCategory* kan vara relaterade till tabellen *Product* osv.

Låt oss titta på ett par intressanta fall, och jämföra när **Visa poster utan data** först är inaktiverat och sedan är aktiverat. 

**1. Grupperade kolumner från samma tabell:** *Product[Color] – Product[Size] – Sum(Sales[Quantity])*

Hur det ser ut när funktionen **Visa poster utan data** är avstängd:

|*Product[Color]*  |*Product[Size]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Blå     |Medium         |15         |
|Blå     |Liten         |10         |

Hur det ser ut när funktionen **Visa poster utan data** är aktiverad:

|*Product[Color]*  |*Product[Size]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Blå     |Stor         |         |
|Blå     |Medium         |15         |
|Blå     |Liten         |10         |
|Röd     |Stor         |         |

Observera hur två nya kombinationer visat sig med funktionen aktiverad: *Blue – Large* och *Red – Large*. Ingendera av dessa poster har motsvarande *kvantit* i tabellen *Sales*. De visas däremot i tabellen *Product*.

**2. Grupperade kolumner från relaterade tabeller:** *ProductStyle[Finish] – Product[Color] – Sum(Sales[Quantity])*

Hur det ser ut när funktionen **Visa poster utan data** är avstängd:

|*ProductStyle[Finish]*  |*Product[Color]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Blank     |Blå         |10         |
|Matt     |Blå         |15         |

Hur det ser ut när funktionen **Visa poster utan data** är aktiverad:

|*ProductStyle[Finish]*  |*Product[Color]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Blank     |Blå         |10         |
|Blank     |Röd         |         |
|Matt     |Blå         |15         |
|Ingen     |         |         |

Observera hur *(Gloss-Red)* och *(None, blank)* visades som kombinationer. Detta är orsaken till att de visades:
* Power BI tog först itu med ProductStyle[Finish] och valde sedan att alla värden ska visas – vilket resulterade i Gloss, Matte, None.
* Med hjälp av de här värdena väljer Power BI ut alla motsvarande *Product[Color]* -poster 
* Eftersom *None* inte motsvarar någon *Product[Color]* visas ett tomt värde

Det är viktigt att tänka på att mekanismen för att välja kolumnvärdena är ordningsberoende och kan betraktas som en åtgärd av typen *vänster yttre koppling* mellan tabeller. Om kolumnordningen ändras så ändras även resultatet.

Låt oss ta en titt på ett exempel där ordningen ändras och hur det påverkar resultaten. Det här är detsamma som objektet **2** i det här avsnittet, men med ändrad ordning.

**Product[Color] – ProductStyle[Finish] – Sum(Sales[Quantity])**

Hur det ser ut när funktionen **Visa poster utan data** är aktiverad:

|*Product[Color]* |*ProductStyle[Finish]*  |*[SumQuantity]*  |
|---------|---------|---------|
|Blå     |Blank         |10         |
|Blå     |Matt         |15         |
|Röd     |Blank         |         |

Observera i det här fallet hur *ProductStyle[Finish]=None* inte visas i tabellen. Detta beror på att Power BI i det här fallet först markerade alla *Color*-värden i tabellen *Product*. Sedan väljer Power BI för varje färg motsvarande *Finish*-värde som innehåller data. Eftersom *None* inte visas i någon kombination av *Color*, så väljs den inte.


## <a name="power-bi-visual-behavior"></a>Power BI – beteende för visuella objekt

När **Visa poster utan data** är aktiverat för ett fält i ett visuellt objekt aktiveras funktionen automatiskt för alla andra fält som är i samma *bucket för visuella objekt* eller hierarki. En bucket för visuella objekt eller hierarki kan vara dess **Axel** eller **Förklaring**; **Kategori**; eller **Rader** eller **Kolumner**.

![Fält för Axel och Förklaring](media/desktop-show-items-no-data/show-items-no-data-04.png)

I till exempel ett visuellt matrisobjekt med fyra fält i bucketen **Rader** gäller att om ett fält har **Visa poster utan data** aktiverat så är det aktiverat för alla poster i matrisen. I följande bild är **Visa poster utan data** aktiverat för det första fältet i bucketen **Rader**, fältet *SupplierID*. Det är även aktiverat för de andra fälten i bucketen **Rader**.

![Fält i samma visuella objekt aktiverar automatiskt Visa poster utan data](media/desktop-show-items-no-data/show-items-no-data-05.png)

Fältet *Kontinent* som visas i bucketen **Kolumner** får dock *inte* funktionen **Visa poster utan data** automatiskt aktiverad. 

Detta beteende för visuella objekt sker ofta när ett visuellt objekt konverteras till en annan typ, till exempel konvertering av ett visuellt matrisobjekt till ett visuellt tabellobjekt. I sådana konverteringar aktiveras **Visa poster utan data** automatiskt för alla fält som flyttas till en bucket där ett fält i den bucketen har funktionen aktiverad. I föregående exempel gäller att om *SupplierID* har funktionen **Visa poster utan data** aktiverad och det visuella objektet konverteras till en tabell flyttas fältet *Kontinent* från bucketen **Kolumner** (liksom fälten i bucketen **Rader**) till den enda bucket som används i ett visuellt tabellobjekt – bucketen **Värden**. Därmed får alla fält i bucketen **Värden** funktionen **Visa poster utan data** aktiverad.

### <a name="exporting-data"></a>Exportera data

Vid användning av funktionen **Exportera sammanfattade data** är beteendet för funktionen **Visa poster utan data** samma som om exporten hade konverterats till ett visuellt tabellobjekt. Vid export av ett visuellt objekt, till exempel ett visuellt diagrammatrisobjekt, kan de exporterade data därför se annorlunda ut än det visuella objekt som visas. Detta beror på att konverteringen till ett visuellt tabellobjekt, som en del av exportprocessen, skulle aktivera **Visa poster utan data** för alla fält som exporteras. 

## <a name="example-data-model"></a>Exempeldatamodell

I det här avsnittet visas den exempeldatamodell som används i exemplen i den här artikeln.

**Modell**: ![Relationer i datamodellen](media/desktop-show-items-no-data/show-items-no-data_03.png)


**Data**:

|Product[ProductId]|    Product[ProductName]|   Product[Color]| Product[Size]|  Product[CategoryId]|    Product[StyleId]|
|---------|---------|---------|---------|---------|---------|
|1  |Prod1  |Blå   |Liten  |1  |1 |
|2  |Prod2  |Blå   |Medium |2  |2 |
|3  |Prod3  |Röd    |Stor  |1  |1 |
|4  |Prod4  |Blå   |Stor  |2  |2 |


|ProductCategory [CategoryId]|   ProductCategory[CategoryName]|
|---------|---------|
|1  |Telefon   |
|2  |Kamera |
|3  |TV |


|ProductStyle[StyleId]| ProductStyle[Finish]|   ProductStyle[Polished]|
|---------|---------|---------|
|1  |Blank  |Ja |
|2  |Matt  |Nej |
|3  |Ingen   |Nej |


|Sales[SaleId]| Sales[ProductId]|   Sales[Date]|    Sales[Quantity]|
|---------|---------|---------|---------|
|1  |1  |2012-01-01 0:00| 10 |
|2  |2  |2013-01-01 0:00| 15 |



## <a name="next-steps"></a>Nästa steg

I den här artikeln beskrivs hur du kan aktivera funktionen **Visa poster utan data** i Power BI. Följande artiklar kan också vara av intresse för dig: 

* [Standardmedlem i flerdimensionella modeller i Power BI](desktop-default-member-multidimensional-models.md)
