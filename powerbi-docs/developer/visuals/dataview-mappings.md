---
title: Förstå datavymappning i visuella Power BI-objekt
description: I den här artikeln beskrivs hur Power BI transformerar data innan de skickas till visuella objekt.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 07cc0517fb27649bb3cc47b8ba8f51b4268d9a7c
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880164"
---
# <a name="understand-data-view-mapping-in-power-bi-visuals"></a>Förstå datavymappning i visuella Power BI-objekt

I den här artikeln diskuteras datavymappning samt hur datarollerna är relaterade till varandra och gör att du kan ange villkorskrav för dem. I artikeln beskrivs även varje typ av `dataMappings`.

Varje giltig mappning skapar en datavy, men för närvarande stöder vi endast en fråga per visuellt objekt. Du får normalt bara en datavy. Men du kan ange flera datamappningar under vissa förhållanden, som tillåter:

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "single": { ... },
        "table": { ... },
        "matrix": { ... }
    }
]
```

Power BI skapar endast en mappning till en datavy om den giltiga mappningen ifylls i `dataViewMappings`.

Med andra ord definieras kanske `categorical` i `dataViewMappings`, men andra mappningar, till exempel `table` eller `single`, gör kanske inte det. Till exempel:

```json
"dataViewMappings": [
    {
        "categorical": { ... }
    }
]
```

Power BI skapar en datavy med en enda `categorical`-mappning, och `table` samt andra mappningar är odefinierade:

```javascript
{
    "categorical": {
        "categories": [ ... ],
        "values": [ ... ]
    },
    "metadata": { ... }
}
```

## <a name="conditions"></a>Villkor

Det här avsnittet beskriver villkoren för en viss datamappning. Du kan ange flera uppsättningar med villkor, och om data matchar någon av de beskrivna villkorsuppsättningarna accepterar det visuella objektet dessa data som giltiga.

För närvarande kan du ange ett minimivärde och ett maxvärde för varje fält. Det värdet representerar det antal fält som kan bindas till den datarollen. 

> [!NOTE]
> Om en dataroll utelämnas i villkoret kan den ha valfritt antal fält.

### <a name="example-1"></a>Exempel 1

Du kan dra flera fält till varje dataroll. I det här exemplet begränsar du kategorin till ett datafält och måttet till två datafält.

```json
"conditions": [
    { "category": { "max": 1 }, "y": { "max": 2 } },
]
```

### <a name="example-2"></a>Exempel 2

I det här exemplet krävs endera av de följande två villkoren:
* Exakt ett kategoridatafält och exakt två mått
* Exakt två kategorier och exakt ett mått.

```json
"conditions": [
    { "category": { "min": 1, "max": 1 }, "measure": { "min": 2, "max": 2 } },
    { "category": { "min": 2, "max": 2 }, "measure": { "min": 1, "max": 1 } }
]
```

## <a name="single-data-mapping"></a>Enkel datamappning

Enkel datamappning är den enklaste formen av datamappning. Den accepterar ett enda måttfält och ger den totala summan. Om fältet är numeriskt ger det summan. Annars ger det antalet unika värden.

Om du vill använda enkel datamappning behöver du definiera namnet på den dataroll som du vill mappa. Den här mappningen fungerar bara med ett enda måttfält. Om ett andra fält tilldelas så genereras ingen datavy. Därför är även en bra idé att inkludera ett villkor som begränsar data till ett enda fält.

> [!NOTE]
> Den här datamappningen kan inte användas tillsammans med andra datamappningar. Den är avsedd att minska data till ett enda numeriskt värde.

### <a name="example-3"></a>Exempel 3

```json
"dataViewMappings": {
    "conditions": [
        { "Y": { "max": 1 } }
    ],
    "single": {
        "role": "Y"
    }
}  
```

Den resulterande datavyn innehåller fortfarande de andra typerna (tabell, kategorisk och så vidare), men varje mappning innehåller bara det enskilda värdet. Bästa praxis är att bara komma åt värdet i enkelformat.

```JSON
{
    "dataView": [
        {
            "metadata": null,
            "categorical": null,
            "matrix": null,
            "table": null,
            "tree": null,
            "single": {
                "value": 94163140.3560001
            }
        }
    ]
}
```

## <a name="categorical-data-mapping"></a>Kategorisk datamappning

Kategorisk datamappning används för att hämta en eller två oberoende grupper av data.

### <a name="example-4"></a>Exempel 4

Här är definitionen från det föregående exemplet för dataroller:

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    }
]
```

Här är mappningen:

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "select": [
                { "bind": { "to": "measure" } }
            ]
        }
    }
}
```

Det är ett enkelt exempel. Det står ”Mappa min `category`-dataroll så att för varje fält jag drar till `category` så mappas dess data till `categorical.categories`. Mappa även min `measure`-dataroll till `categorical.values`.”

* **for...in**: För alla objekt i den här datarollen, inkludera dem i datafrågan.
* **bind...to**: Ger samma resultat som *for...in*, men förväntar sig att datarollen har ett villkor som begränsar den till ett enda fält.

### <a name="example-5"></a>Exempel 5

I det här exemplet används de två första datarollerna från det föregående exemplet, och dessutom definieras `grouping` och `measure2`.

```json
"dataRole":[
    {
        "displayName": "Category",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Y Axis",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Grouping with",
        "name": "grouping",
        "kind": "Grouping"
    },
    {
        "displayName": "X Axis",
        "name": "measure2",
        "kind": "Grouping"
    }
]
```

Här är mappningen:

```json
"dataViewMappings":{
    "categorical": {
        "categories": {
            "for": { "in": "category" }
        },
        "values": {
            "group": {
                "by": "grouping",
                "select":[
                    { "bind": { "to": "measure" } },
                    { "bind": { "to": "measure2" } }
                ]
            }
        }
    }
}
```

Här ligger skillnaden i hur vi mappar categorical.values. Vi säger ”Mappa mina dataroller för `measure` och `measure2` som ska grupperas efter datarollen `grouping`.”

### <a name="example-6"></a>Exempel 6

Här är datarollerna:

```json
"dataRoles": [
    {
        "displayName": "Categories",
        "name": "category",
        "kind": "Grouping"
    },
    {
        "displayName": "Measures",
        "name": "measure",
        "kind": "Measure"
    },
    {
        "displayName": "Series",
        "name": "series",
        "kind": "Measure"
    }
]
```

Här är datavymappningen:

```json
"dataViewMappings": [
    {
        "categorical": {
            "categories": {
                "for": {
                    "in": "category"
                }
            },
            "values": {
                "group": {
                    "by": "series",
                    "select": [{
                            "for": {
                                "in": "measure"
                            }
                        }
                    ]
                }
            }
        }
    }
]
```

Den kategoriska datavyn kan visualiseras så här:

| Kategorisk |  |  | | | |
|-----|-----|------|------|------|------|
| | År | 2013 | 2014 | 2015 | 2016 |
| Land | | |
| USA | | x | x | 125 | 100 |
| Kanada | | x | 50 | 200 | x |
| Mexiko | | 300 | x | x | x |
| Storbritannien | | x | x | 75 | x |

Power BI skapar den som den kategoriska datavyn. Detta är uppsättningen med kategorier.

```JSON
{
    "categorical": {
        "categories": [
            {
                "source": {...},
                "values": [
                    "Canada",
                    "Mexico",
                    "UK",
                    "USA"
                ],
                "identity": [...],
                "identityFields": [...],
            }
        ]
    }
}
```

Varje kategori mappar även till en uppsättning värden. Vart och ett av dessa värden grupperas efter serie, vilket uttrycks som år.

Försäljningen 2013 i Kanada är null och försäljningen 2014 i Kanada är 50.

```JSON
{
    "values": [
        {
            "source": {...},
            "values": [
                null,
                300,
                null,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                50,
                null,
                150,
                null
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                200,
                null,
                null,
                125
            ],
            "identity": [...],
        },
        {
            "source": {...},
            "values": [
                null,
                null,
                null,
                100
            ],
            "identity": [...],
        }
    ]
}
```

## <a name="table-data-mapping"></a>Tabelldatamappning

Tabelldatavyn är en enkel datamappning. I stort sett är det en lista över datapunkter där numeriska datapunkter kan aggregeras.

### <a name="example-7"></a>Exempel 7

Med de aktuella funktionerna:

```json
"dataRoles": [
    {
        "displayName": "Values",
        "name": "values",
        "kind": "Measure"
    }
]
```

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                }
            }
        }
    }
]
```

Du kan visualisera tabelldatavyn så här:  

| Land| År | Försäljning |
|-----|-----|------|
| USA | 2016 | 100 |
| USA | 2015 | 50 |
| Kanada | 2015 | 200 |
| Kanada | 2015 | 50 |
| Mexiko | 2013 | 300 |
| Storbritannien | 2014 | 150 |
| USA | 2015 | 75 |

Power BI visar dina data som tabelldatavyn. Du bör inte anta att data är ordnade.

```JSON
{
    "table" : {
        "columns": [...],
        "rows": [
            [
                "Canada",
                2014,
                50
            ],
            [
                "Canada",
                2015,
                200
            ],
            [
                "Mexico",
                2013,
                300
            ],
            [
                "UK",
                2014,
                150
            ],
            [
                "USA",
                2015,
                100
            ],
            [
                "USA",
                2015,
                75
            ],
            [
                "USA",
                2016,
                100
            ]
        ]
    }
}
```

Du kan aggregera data genom att markera önskat fält och sedan välja sum.  

![Dataaggregering](./media/data-aggregation.png)

## <a name="matrix-data-mapping"></a>Matrisdatamappning

Matrisdatamappning liknar tabelldatamappning, men raderna visas hierarkiskt. Vilket datarollvärde som helst kan användas som kolumnrubrikvärde.

```json
{
    "dataRoles": [
        {
            "name": "Category",
            "displayName": "Category",
            "displayNameKey": "Visual_Category",
            "kind": "Grouping"
        },
        {
            "name": "Column",
            "displayName": "Column",
            "displayNameKey": "Visual_Column",
            "kind": "Grouping"
        },
        {
            "name": "Measure",
            "displayName": "Measure",
            "displayNameKey": "Visual_Values",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "matrix": {
                "rows": {
                    "for": {
                        "in": "Category"
                    }
                },
                "columns": {
                    "for": {
                        "in": "Column"
                    }
                },
                "values": {
                    "select": [
                        {
                            "for": {
                                "in": "Measure"
                            }
                        }
                    ]
                }
            }
        }
    ]
}
```

Power BI skapar en hierarkisk datastruktur. Roten i trädhierarkin innehåller data från kolumnen **Överordnade** i datarollen `Category` med underordnade från kolumnen **Underordnade** för datarollstabellen.

Datauppsättning:

| Parents (Överordnade) | Underordnade | Nästa underordnade | Kolumner | Värden |
|-----|-----|------|-------|-------|
| Parent1 | Child1 | Grand child1 | Col1 | 5 |
| Parent1 | Child1 | Grand child1 | Col2 | 6 |
| Parent1 | Child1 | Grand child2 | Col1 | 7 |
| Parent1 | Child1 | Grand child2 | Col2 | 8 |
| Parent1 | Child2 | Grand child3 | Col1 | 5 |
| Parent1 | Child2 | Grand child3 | Col2 | 3 |
| Parent1 | Child2 | Grand child4 | Col1 | 4 |
| Parent1 | Child2 | Grand child4 | Col2 | 9 |
| Parent1 | Child2 | Grand child5 | Col1 | 3 |
| Parent1 | Child2 | Grand child5 | Col2 | 5 |
| Parent2 | Child3 | Grand child6 | Col1 | 1 |
| Parent2 | Child3 | Grand child6 | Col2 | 2 |
| Parent2 | Child3 | Grand child7 | Col1 | 7 |
| Parent2 | Child3 | Grand child7 | Col2 | 1 |
| Parent2 | Child3 | Grand child8 | Col1 | 10 |
| Parent2 | Child3 | Grand child8 | Col2 | 13 |

Det visuella kärnmatrisobjektet i Power BI renderar detta som en tabell.

![Visuellt matrisobjekt](./media/matrix-visual-smaple.png)

Det visuella objektet får sin datastruktur enligt beskrivningen i följande kod (endast de första två tabellraderna visas här):

```json
{
    "metadata": {...},
    "matrix": {
        "rows": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Parent1",
                        "identity": {...},
                        "childIdentityFields": [...],
                        "children": [
                            {
                                "level": 1,
                                "levelValues": [...],
                                "value": "Child1",
                                "identity": {...},
                                "childIdentityFields": [...],
                                "children": [
                                    {
                                        "level": 2,
                                        "levelValues": [...],
                                        "value": "Grand child1",
                                        "identity": {...},
                                        "values": {
                                            "0": {
                                                "value": 5 // value for Col1
                                            },
                                            "1": {
                                                "value": 6 // value for Col2
                                            }
                                        }
                                    },
                                    ...
                                ]
                            },
                            ...
                        ]
                    },
                    ...
                ]
            }
        },
        "columns": {
            "levels": [...],
            "root": {
                "childIdentityFields": [...],
                "children": [
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col1",
                        "identity": {...}
                    },
                    {
                        "level": 0,
                        "levelValues": [...],
                        "value": "Col2",
                        "identity": {...}
                    },
                    ...
                ]
            }
        },
        "valueSources": [...]
    }
}
```

## <a name="data-reduction-algorithm"></a>Algoritm för dataminskning

Du kan styra den mängd data som ska tas emot i datavyn med hjälp av en algoritm för dataminskning.

Som standard tillämpas algoritmen för dataminskning uppifrån för alla visuella Power BI-objekt med *count* angett till 1000 datapunkter. Det är samma som att ange följande egenskaper i filen *capabilities.json*:

```json
"dataReductionAlgorithm": {
    "top": {
        "count": 1000
    }
}
```

Du kan ändra värdet för *count* till valfritt heltalsvärde upp till 30 000. R-baserade visuella Power BI-objekt har stöd för upp till 15 0000 rader.

## <a name="data-reduction-algorithm-types"></a>Typer av algoritmer för dataminskning

Det finns fyra typer av inställningar för algoritmer för dataminskning:

* `top`: Om du vill begränsa data till värden som tas längst upp i datamängden. *count*-värdena längst upp hämtas från datamängden.
* `bottom`: Om du vill begränsa data till värden som tas längst ned i datamängden. De sista "count"-värdena hämtas från datamängden.
* `sample`: Minska datamängden med en enkel samplingsalgoritm som är begränsad till det antal objekt som anges av *count*. Det innebär att det första och det sista objektet inkluderas samt att det antal objekt som anges av *count* har samma intervall sinsemellan.
Om du till exempel har datamängden [0, 1, 2, ... 100] och *count* är 9 får du värdena [0, 10, 20 ... 100].
* `window`: Läser in ett *fönster* med datapunkter vid en tidpunkt som innehåller *count* element. För närvarande är `top` och `window` likvärdiga. Vi arbetar för att helt stödja en fönsterinställning.

## <a name="data-reduction-algorithm-usage"></a>Använda algoritmen för dataminskning

Algoritmen för dataminskning kan användas i kategorisk mappning eller tabell- eller matrisdatavymappning.

Du kan ange algoritmen till `categories` och/eller gruppavsnitt för `values` för kategorisk datamappning.

### <a name="example-8"></a>Exempel 8

```json
"dataViewMappings": {
    "categorical": {
        "categories": {
            "for": { "in": "category" },
            "dataReductionAlgorithm": {
                "window": {
                    "count": 300
                }
            }  
        },
        "values": {
            "group": {
                "by": "series",
                "select": [{
                        "for": {
                            "in": "measure"
                        }
                    }
                ],
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 100
                    }
                }  
            }
        }
    }
}
```

Du kan använda algoritmen för dataminskning för avsnittet `rows` i tabellen för datavymappning.

### <a name="example-9"></a>Exempel 9

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "top": {
                        "count": 2000
                    }
                } 
            }
        }
    }
]
```

Du kan använda algoritmen för dataminskning för avsnitten `rows` och `columns` i matrisen för datavymappning.
