---
title: Egenskaper för Power BI-datauppsättningar
description: Lär dig mer om egenskaperna för API:er för Power BI-datauppsättningar
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: b0fabcb5915a4f642abc1af03979a4597e2aa2f7
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73864947"
---
# <a name="dataset-properties"></a>Egenskaper för datamängd

Den aktuella v1 av datauppsättnings-API:t tillåter endast att en datauppsättning skapas med ett namn och en samling tabeller. Varje tabell kan ha ett namn och en samling kolumner. Varje kolumn har ett namn och en datatyp. Vi arbetar med att utöka dessa egenskaper, framför allt med stöd för mått och relationer mellan tabeller. Den fullständiga listan över egenskaper som stöds för den här versionen är följande:

> [!IMPORTANT]
> Den finns på sidan för [åtgärdsgrupper för datauppsättningar](https://docs.microsoft.com/rest/api/power-bi/datasets).

## <a name="dataset"></a>Datauppsättning

Namn  |Typ  |Beskrivning  |Skrivskyddad  |Krävs
---------|---------|---------|---------|---------
ID     |  GUID       | Unik identifierare för datauppsättningen i hela systemet.        | Sant        | Falskt        
namn     | Sträng        | Användardefinierat namn på datauppsättningen.        | Falskt        | Sant        
tabeller     | Tabell[]        | Tabellsamling.        |  Falskt       | Falskt        
relationer     | Relation[]        | En samling relationer mellan tabeller.        | Falskt        |  Falskt  
defaultMode     | Sträng        | Anger huruvida datamängden push-överförs, strömmas eller båda, med värdena ”Push” och ”Streaming”.         | Falskt        |  Falskt

## <a name="table"></a>Tabell

Namn  |Typ  |Beskrivning  |Skrivskyddad  |Krävs
---------|---------|---------|---------|---------
namn     | Sträng        |  Användardefinierat namn på tabellen. Det används också som tabellens identifierare.       | Falskt        |  Sant       
kolumner     |  kolumn[]       |  Kolumnsamling.       | Falskt        |  Sant       
mått     | mått[]        |  Måttsamling.       | Falskt        |  Falskt       
isHidden     | Boolesk        | Om värdet är Sant döljs tabellen från klientverktyg.        | Falskt        | Falskt        

## <a name="column"></a>Kolumn

Namn  |Typ  |Beskrivning  |Skrivskyddad  |Krävs
---------|---------|---------|---------|---------
namn     |  Sträng        | Användardefinierat namn på kolumnen.        |  Falskt       | Sant       
dataType     |  Sträng       |  [EDM-datatyper](https://msdn.microsoft.com/library/ee382832.aspx) som stöds och begränsningar. Se [Begränsningar för datatyper](#DataTypeRestrictions).      |  Falskt       | Sant        
formatString     | Sträng        | En sträng som anger hur värdet ska formateras när det visas. Mer information om strängformatering finns på sidan om [FORMAT_STRING Contents](https://msdn.microsoft.com/library/ms146084.aspx) (Innehållsformat i strängar).      | Falskt        | Falskt        
sortByColumn    | Sträng        |   Strängnamn på en kolumn i samma tabell som ska användas för att ordna den aktuella kolumnen.     | Falskt        | Falskt       
dataCategory     | Sträng        |  Strängvärdet som ska användas för datakategorin som beskriver data i kolumnen. Vissa vanliga värden är: Adress, Stad, Kontinent, Land, Bild, Bild-URL, Latitud, Longitud, Organisation, Plats, Postnummer, Region, Webb-URL       |  Falskt       | Falskt        
isHidden    |  Boolesk       |  Egenskap som anger om kolumnen är dold från vyn. Standardvärdet är Falskt.       | Falskt        | Falskt        
summarizeBy     | Sträng        |  Standardmetod för sammansättning för kolumnen. Några värden är: standard, ingen, summa, min, max, antal, genomsnittlig, antal unika.     |  Falskt       | Falskt

## <a name="measure"></a>Mått

Namn  |Typ  |Beskrivning  |Skrivskyddad  |Krävs
---------|---------|---------|---------|---------
namn     | Sträng        |  Användardefinierat namn på måttet.       |  Falskt       | Sant        
uttryck     | Sträng        | Ett giltigt DAX-uttryck.        | Falskt        |  Sant       
formatString     | Sträng        |  En sträng som anger hur värdet ska formateras när det visas. Mer information om strängformatering finns på sidan om [FORMAT_STRING Contents](https://msdn.microsoft.com/library/ms146084.aspx) (Innehållsformat i strängar).       | Falskt        | Falskt        
isHidden     | Sträng        |  Om värdet är Sant döljs tabellen från klientverktyg.       |  Falskt       | Falskt       

## <a name="relationship"></a>Relation

Namn  |Typ  |Beskrivning  |Skrivskyddad  |Krävs 
---------|---------|---------|---------|---------
namn     | Sträng        | Användardefinierat namn på relationen. Det används också som relationens identifierare.        | Falskt       | Sant        
crossFilteringBehavior     | Sträng        |    Filterriktningen för relationen: OneDirection (standard), BothDirections, automatisk       | Falskt        | Falskt        
fromTable     | Sträng        | Namnet på sekundärnyckeltabellen.        | Falskt        | Sant         
fromColumn    | Sträng        | Namnet på sekundärnyckelkolumnen.        | Falskt        | Sant         
toTable    | Sträng        | Namnet på primärnyckeltabellen.        | Falskt        | Sant         
toColumn     | Sträng        | Namnet på primärnyckelkolumnen.        | Falskt        | Sant        

<a name="DataTypeRestrictions"/>

## <a name="data-type-restrictions-applies-to-datatype-property"></a>Begränsningar för datatyper (gäller dataType-egenskapen)

Datatyp  |Begränsningar  
---------|---------
Int64     |   Int64.MaxValue och Int64.MinValue tillåts inte.      
Double     |  Double.MaxValue- och Double.MinValue-värden tillåts inte. NaN stöds inte. +Infinity och -Infinity stöds inte i vissa funktioner (t.ex. Min, Max).       
Boolesk     |   Sant eller Falskt.
Datumtid    |   Vid datainläsning kvantifierar vi värden med dagbråk till hela multiplar av 1/300 sekunder (3,33ms).      
Sträng     |  För närvarande tillåts upp till 4 000 tecken per strängvärde.
Decimal|precision = 28, skala = 4

## <a name="example"></a>Exempel
Följande kodexempel innehåller flera av dessa egenskaper:

```json
{

  "name": "PushAdvanced",

  "tables": [

    {

      "name": "Date",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        }

      ]

    },

    {

      "name": "sales",

      "columns": [

        {

          "name": "Date",

          "dataType": "dateTime",

          "formatString": "dddd\\, mmmm d\\, yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "Sales",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ],

      "measures": [

        {

          "name": "percent to forecast",

          "expression": "SUM(sales[Sales])/SUM(forecast[forecast])",

          "formatString": "0.00 %;-0.00 %;0.00 %"

        }

      ]

    },

    {

      "name": "forecast",

      "columns": [

        {

          "name": "date",

          "dataType": "dateTime",

          "formatString": "m/d/yyyy",

          "summarizeBy": "none"

        },

        {

          "name": "forecast",

          "dataType": "int64",

          "formatString": "0",

          "summarizeBy": "sum"

        }

      ]

    }

  ],

  "relationships": [

    {

      "name": "2ea345ce-b147-436e-8ac2-9d3c4d82af8d",

      "fromTable": "sales",

      "fromColumn": "Date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    },

    {

      "name": "5d95f419-e589-4345-9581-6e70670b1bba",

      "fromTable": "forecast",

      "fromColumn": "date",

      "toTable": "Date",

      "toColumn": "Date",

      "crossFilteringBehavior": "bothDirections"

    }

  ]

}
```