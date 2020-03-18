---
title: Skicka data till en datauppsättning
description: Skicka data till en Power BI-datauppsättning
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/22/2019
ms.openlocfilehash: 932e458c90b248e01a88d45a849838cff27f6dcb
ms.sourcegitcommit: a175faed9378a7d040a08ced3e46e54503334c07
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79488210"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Skicka data till en Power BI-datauppsättning

Power BI-API:et låter dig skicka data till en Power BI-datauppsättning. I den här artikeln visar vi hur du skickar en datauppsättning för försäljningsmarknadsföring som innehåller en produkttabell till en befintlig datauppsättning.

Innan du sätter igång, behöver du ett konto i Azure Active Directory (Azure AD) och ett [Power BI-konto](../embedded/create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Steg för att skicka data till en datauppsättning

* Steg 1: [Registrera en app med Azure AD](../embedded/register-app.md)
* Steg 2: [Hämta en åtkomsttoken för autentisering](walkthrough-push-data-get-token.md)
* Steg 3: [Skapa en datauppsättning i Power BI](walkthrough-push-data-create-dataset.md)
* Steg 4: [Hämta en datauppsättning för att lägga till rader i en Power BI-tabell](walkthrough-push-data-get-datasets.md)
* Steg 5: [Lägg till rader i en Power BI-tabell](walkthrough-push-data-add-rows.md)

Nästa avsnitt är en allmän diskussion av Power BI-API-åtgärder som skickar data.

## <a name="power-bi-api-operations-to-push-data"></a>Power BI-API-åtgärder för att skicka data

Med Power BI REST API:et kan du skicka datakällor till Power BI. När en app lägger till rader i en datauppsättning uppdateras panelerna på instrumentpanelen automatiskt med nya data. För att skicka data använder du åtgärderna [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset) och [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows). Om du vill hitta en datauppsättning, använder du åtgärden [Get Datasets](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets). Du kan skicka ett grupp-ID för att arbeta med en grupp för vilken som av de här åtgärderna. Använd åtgärden [Get Groups](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups) för att hämta en lista över grupp-ID.

Här är åtgärderna för att skicka data till en datauppsättning:

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Hämta datauppsättningar](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [Post Rows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Hämta grupper](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Du skapar en datauppsättning i Power BI genom att skicka en JavaScript Object Notation (JSON)-sträng till Power BI-tjänsten. Läs mer om JSON i [Introduktion till JSON](https://json.org/).

JSON-strängen för en datauppsättning har följande format:

**Power BI Dataset JSON-objekt**

    {"name": "dataset_name", "tables":
        [{"name": "", "columns":
            [{ "name": "column_name1", "dataType": "data_type"},
             { "name": "column_name2", "dataType": "data_type"},
             { ... }
            ]
          }
        ]
    }

För vårt exempel med datauppsättningen för försäljning och marknadsföring, skickar du en sträng såsom visas nedan. I det här exemplet är **SalesMarketing** datauppsättningens namn och **Product** är tabellens namn. När du har definierat tabellen, definierar du tabellschemat. För datauppsättningen **SalesMarketing** så har tabellens schema dessa kolumner: ProductID, Manufacturer, Category, Segment, Product och IsCompete.

**Exempel på datauppsättningsobjekt-JSON**

    {
        "name": "SalesMarketing",
        "tables": [
            {
                "name": "Product",
                "columns": [
                {
                    "name": "ProductID",
                    "dataType": "int"
                },
                {
                    "name": "Manufacturer",
                    "dataType": "string"
                },
                {
                    "name": "Category",
                    "dataType": "string"
                },
                {
                    "name": "Segment",
                    "dataType": "string"
                },
                {
                    "name": "Product",
                    "dataType": "string"
                },
                {
                    "name": "IsCompete",
                    "dataType": "bool"
                }
                ]
            }
        ]
    }

Du kan använda följande datatyper för ett Power BI-tabellschema.

## <a name="power-bi-table-data-types"></a>Power BI tabelldatatyper

| **Datatyp** | **Begränsningar** |
| --- | --- |
| Int64 |Int64.MaxValue och Int64.MinValue tillåts inte. |
| Double |Double.MaxValue- och Double.MinValue-värden tillåts inte. NaN stöds inte. +Infinity och -Infinity stöds inte i vissa funktioner (t.ex. Min, Max). |
| Boolesk |Ingen |
| Datumtid |Vid datainläsning kvantifierar vi värden med dagbråk till hela multiplar av 1/300 sekunder (3,33ms). |
| Sträng |Tillåter för närvarande upp till 128 000 tecken. |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>Mer information om att skicka data till Power BI

Om du vill komma igång med att skicka data till en datauppsättning, se [Steg 1: Registrera en app med Azure AD](../embedded/register-app.md) i navigeringsfönstret.

## <a name="next-steps"></a>Nästa steg

* [Registrera dig för Power BI](../embedded/create-an-azure-active-directory-tenant.md)  
* [Introduktion till JSON](https://json.org/)  
* [Översikt över Power BI REST API](overview-of-power-bi-rest-api.md)  

Har du fler frågor? [Prova Power BI Community](https://community.powerbi.com/)