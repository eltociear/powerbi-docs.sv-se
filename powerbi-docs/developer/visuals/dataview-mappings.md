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
ms.openlocfilehash: b50ebde94d78ca42437979d792fb6402affe8855
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "74696675"
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
{
    "dataRoles": [
        {
            "displayName": "Y",
            "name": "Y",
            "kind": "Measure"
        }
    ],
    "dataViewMappings": [
        {
            "conditions": [
                {
                    "Y": {
                        "max": 1
                    }
                }
            ],
            "single": {
                "role": "Y"
            }
        }
    ]
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

Kodexempel för att bearbeta enkel mappning av datavyer

```typescript
"use strict";
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;
import DataViewSingle = powerbi.DataViewSingle;
// standart imports
// ...

export class Visual implements IVisual {
    private target: HTMLElement;
    private host: IVisualHost;
    private valueText: HTMLParagraphElement;

    constructor(options: VisualConstructorOptions) {
        // constructor body
        this.target = options.element;
        this.host = options.host;
        this.valueText = document.createElement("p");
        this.target.appendChild(this.valueText);
        // ...
    }

    public update(options: VisualUpdateOptions) {
        const dataView: DataView = options.dataViews[0];
        const singleDataView: DataViewSingle = dataView.single;

        if (!singleDataView ||
            !singleDataView.value ) {
            return
        }

        this.valueText.innerText = singleDataView.value.toString();
    }
}
```

Resultatet blir att det visuella objektet visar ett enda värde från Power BI:

![Visuellt exempel på mappning av en enda datavy](./media/visual-simple-dataview-mapping.png)

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
| USA | | x | x | 650 | 350 |
| Kanada | | x | 630 | 490 | x |
| Mexiko | | 645 | x | x | x |
| Storbritannien | | x | x | 831 | x |

Power BI skapar den som den kategoriska datavyn. Detta är uppsättningen med kategorier.

```JSON
{
    "categorical": {
        "categories": [
            {
                "source": {...},
                "values": [
                    "Canada",
                    "USA",
                    "UK",
                    "Mexico"
                ],
                "identity": [...],
                "identityFields": [...],
            }
        ]
    }
}
```

Varje kategori mappar även till en uppsättning värden. Vart och ett av dessa värden grupperas efter serie, vilket uttrycks som år.

Varje `values`-array representerar till exempel data för respektive år.
Varje `values`-array innehåller 4 värden, för Kanada, USA, Storbritannien och Mexiko:

```JSON
{
    "values": [
        // Values for 2013 year
        {
            "source": {...},
            "values": [
                null, // Value for `Canada` category
                null, // Value for `USA` category
                null, // Value for `UK` category
                645 // Value for `Mexico` category
            ],
            "identity": [...],
        },
        // Values for 2014 year
        {
            "source": {...},
            "values": [
                630, // Value for `Canada` category
                null, // Value for `USA` category
                null, // Value for `UK` category
                null // Value for `Mexico` category
            ],
            "identity": [...],
        },
        // Values for 2015 year
        {
            "source": {...},
            "values": [
                490, // Value for `Canada` category
                650, // Value for `USA` category
                831, // Value for `UK` category
                null // Value for `Mexico` category
            ],
            "identity": [...],
        },
        // Values for 2016 year
        {
            "source": {...},
            "values": [
                null, // Value for `Canada` category
                350, // Value for `USA` category
                null, // Value for `UK` category
                null // Value for `Mexico` category
            ],
            "identity": [...],
        }
    ]
}
```

Kodexempel för bearbetning av kategorimappning i datavyer. I exemplet skapas den hierarkiska strukturen `Country => Year => Value`

```typescript
"use strict";
import powerbi from "powerbi-visuals-api";
import DataView = powerbi.DataView;
import DataViewDataViewCategoricalSingle = powerbi.DataViewCategorical;
import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
import PrimitiveValue = powerbi.PrimitiveValue;
// standart imports
// ...

export class Visual implements IVisual {
    private target: HTMLElement;
    private host: IVisualHost;
    private categories: HTMLElement;

    constructor(options: VisualConstructorOptions) {
        // constructor body
        this.target = options.element;
        this.host = options.host;
        this.categories = document.createElement("pre");
        this.target.appendChild(this.categories);
        // ...
    }

    public update(options: VisualUpdateOptions) {
        const dataView: DataView = options.dataViews[0];
        const categoricalDataView: DataViewCategorical = dataView.categorical;

        if (!categoricalDataView ||
            !categoricalDataView.categories ||
            !categoricalDataView.categories[0] ||
            !categoricalDataView.values) {
            return;
        }

        // Categories have only one column in data buckets
        // If you want to support several columns of categories data bucket, you should iterate categoricalDataView.categories array.
        const categoryFieldIndex = 0;
        // Measure has only one column in data buckets.
        // If you want to support several columns on data bucket, you should iterate years.values array in map function
        const measureFieldIndex = 0;
        let categories: PrimitiveValue[] = categoricalDataView.categories[categoryFieldIndex].values;
        let values: DataViewValueColumnGroup[] = categoricalDataView.values.grouped();

        let data = {};
        // iterate categories/countries
        categories.map((category: PrimitiveValue, categoryIndex: number) => {
            data[category.toString()] = {};
            // iterate series/years
            values.map((years: DataViewValueColumnGroup) => {
                if (!data[category.toString()][years.name] && years.values[measureFieldIndex].values[categoryIndex]) {
                    data[category.toString()][years.name] = []
                }
                if (years.values[0].values[categoryIndex]) {
                    data[category.toString()][years.name].push(years.values[measureFieldIndex].values[categoryIndex]);
                }
            });
        });

        this.categories.innerText = JSON.stringify(data, null, 6);
        console.log(data);
    }
}
```

Det visuella resultatet:

![Det visuella objektet med kategorimappning i datavyn](./media/categorical-data-view-mapping-visual.png)

## <a name="table-data-mapping"></a>Tabelldatamappning

Tabelldatavyn är en enkel datamappning. I stort sett är det en lista över datapunkter där numeriska datapunkter kan aggregeras.

### <a name="example-7"></a>Exempel 7

Med de aktuella funktionerna:

```json
"dataRoles": [
    {
        "displayName": "Column",
        "name": "column",
        "kind": "Measure"
    },
    {
        "displayName": "Value",
        "name": "value",
        "kind": "Measure"
    }
]
```

```json
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "select": [
                    {
                        "for": {
                            "in": "column"
                        }
                    },
                    {
                        "for": {
                            "in": "value"
                        }
                    }
                ]
            }
        }
    }
]
```

Du kan visualisera tabelldatavyn så här:  

Dataexempel:

| Land| År | Försäljning |
|-----|-----|------|
| USA | 2016 | 100 |
| USA | 2015 | 50 |
| Kanada | 2015 | 200 |
| Kanada | 2015 | 50 |
| Mexiko | 2013 | 300 |
| Storbritannien | 2014 | 150 |
| USA | 2015 | 75 |

Databindning:

![Databindning för mappning av tabelldata](./media/table-dataview-mapping-data.png)

Power BI visar dina data som tabelldatavyn. Du bör inte anta att data är ordnade.

```JSON
{
    "table" : {
        "columns": [...],
        "rows": [
            [
                "Canada",
                2014,
                630
            ],
            [
                "Canada",
                2015,
                490
            ],
            [
                "Mexico",
                2013,
                645
            ],
            [
                "UK",
                2014,
                831
            ],
            [
                "USA",
                2015,
                650
            ],
            [
                "USA",
                2016,
                350
            ]
        ]
    }
}
```

Du kan aggregera data genom att markera önskat fält och sedan välja sum.  

![Dataaggregering](./media/data-aggregation.png)

Kodexempel för bearbetning av tabellmappning i datavyer.

```typescript
"use strict";
import "./../style/visual.less";
import powerbi from "powerbi-visuals-api";
// ...
import DataViewMetadataColumn = powerbi.DataViewMetadataColumn;
import DataViewTable = powerbi.DataViewTable;
import DataViewTableRow = powerbi.DataViewTableRow;
import PrimitiveValue = powerbi.PrimitiveValue;
// other imports
// ...

export class Visual implements IVisual {
    private target: HTMLElement;
    private host: IVisualHost;
    private table: HTMLParagraphElement;

    constructor(options: VisualConstructorOptions) {
        // constructor body
        this.target = options.element;
        this.host = options.host;
        this.table = document.createElement("table");
        this.target.appendChild(this.table);
        // ...
    }

    public update(options: VisualUpdateOptions) {
        const dataView: DataView = options.dataViews[0];
        const tableDataView: DataViewTable = dataView.table;

        if (!tableDataView) {
            return
        }
        while(this.table.firstChild) {
            this.table.removeChild(this.table.firstChild);
        }

        //draw header
        const tableHeader = document.createElement("th");
        tableDataView.columns.forEach((column: DataViewMetadataColumn) => {
            const tableHeaderColumn = document.createElement("td");
            tableHeaderColumn.innerText = column.displayName
            tableHeader.appendChild(tableHeaderColumn);
        });
        this.table.appendChild(tableHeader);

        //draw rows
        tableDataView.rows.forEach((row: DataViewTableRow) => {
            const tableRow = document.createElement("tr");
            row.forEach((columnValue: PrimitiveValue) => {
                const cell = document.createElement("td");
                cell.innerText = columnValue.toString();
                tableRow.appendChild(cell);
            })
            this.table.appendChild(tableRow);
        });
    }
}
```

Formatfilen `style/visual.less` för det visuella objektet innehåller en layout för tabellen:

```less
table {
    display: flex;
    flex-direction: column;
}

tr, th {
    display: flex;
    flex: 1;
}

td {
    flex: 1;
    border: 1px solid black;
}
```

![Det visuella objektet med tabellmappning i datavyn](./media/table-dataview-mapping-visual.png)

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

## <a name="next-steps"></a>Nästa steg

Läs om hur du [lägger till stöd för att öka detaljnivån för datavyer i visuella Power BI-objekt](drill-down-support.md).
