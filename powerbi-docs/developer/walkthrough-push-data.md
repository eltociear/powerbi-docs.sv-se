---
title: Skicka data till en datauppsättning
description: Skicka data till en Power BI-datauppsättning
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: conceptual
ms.date: 01/05/2017
ms.author: maghan
ms.openlocfilehash: 96b29c9dc6c384b663ef375d4968dedb011bd05d
ms.sourcegitcommit: 8ee0ebd4d47a41108387d13a3bc3e7e2770cbeb8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34813122"
---
# <a name="push-data-into-a-power-bi-dataset"></a>Skicka data till en Power BI-datauppsättning
Med Power BI-API:et kan du skicka data till en Power BI-datauppsättning. Om du till exempel vill utöka ett befintligt företagsarbetsflöde för att skicka viktiga data till din datauppsättning. I det här fallet vill du skicka en datauppsättning med försäljning och marknadsföring som har en produkttabell till en datauppsättning.

Innan du sätter igång med att skicka data till en datauppsättning, behöver du ett konto i Azure Active Directory (Azure AD) och ett [Power BI-konto](create-an-azure-active-directory-tenant.md).

## <a name="steps-to-push-data-into-a-dataset"></a>Steg för att skicka data till en datauppsättning
* Steg 1: [Registrera en app med Azure AD](walkthrough-push-data-register-app-with-azure-ad.md)
* Steg 2: [Hämta en åtkomsttoken för autentisering](walkthrough-push-data-get-token.md)
* Steg 3: [Skapa en datauppsättning i Power BI](walkthrough-push-data-create-dataset.md)
* Steg 4: [Hämta en datauppsättning för att lägga till rader i en Power BI-tabell](walkthrough-push-data-get-datasets.md)
* Steg 5: [Lägg till rader i en Power BI-tabell](walkthrough-push-data-add-rows.md)

Nästa avsnitt är en allmän diskussion av Power BI-API-åtgärder som skickar data.

## <a name="power-bi-api-operations-to-push-data"></a>Power BI-API-åtgärder för att skicka data
Med Power BI REST API:et kan du skicka datakällor till Power BI. När en app lägger till rader till en datauppsättning, uppdateras paneler på instrumentpanelen automatiskt med uppdaterade data. Du skickar data genom att köra [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets) tillsammans med [PostRows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows). Om du vill hitta en datauppsättning, använder du åtgärden [Get Datasets](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets). För vilken som av de här åtgärderna, kan du skicka ett grupp-ID för att arbeta med en grupp. Använd åtgärden [Get Groups](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups) för att hämta en lista över grupp-ID:er.

Här är åtgärderna för att skicka data till en datauppsättning:

* [PostDataset](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [Hämta datauppsättningar](https://docs.microsoft.com/rest/api/power-bi/datasets/getdatasets)
* [Post Rows](https://docs.microsoft.com/rest/api/power-bi/pushdatasets/datasets_postrows)
* [Hämta grupper](https://docs.microsoft.com/rest/api/power-bi/groups/getgroups)

Du skapar en datauppsättning i Power BI genom att skicka en JavaScript Object Notation (JSON)-sträng till Power BI-tjänsten. Läs mer om JSON i [Introduktion till JSON](http://json.org/).

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

Så, för vårt exempel med datauppsättningen för försäljning och marknadsföring, skickar du en sträng som i exemplet nedan. I det här exemplet är **SalesMarketing** namnet på datauppsättningen och **Product** är namnet på tabellen. När du har definierat tabellen, definierar du tabellschemat. För datauppsättningen **SalesMarketing**, har tabellschemat dessa kolumner: ProductID, Manufacturer, Category, Segment, Product och IsCompete.

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
Om du vill komma igång med att skicka data till en datauppsättning, se [Steg 1: Registrera en app med Azure AD](walkthrough-push-data-register-app-with-azure-ad.md) i det vänstra navigeringsfönstret.

[Nästa steg >](walkthrough-push-data-register-app-with-azure-ad.md)

## <a name="next-steps"></a>Nästa steg
[Registrera dig för Power BI](create-an-azure-active-directory-tenant.md)  
[Introduktion till JSON](http://json.org/)  
[Översikt över Power BI REST API](overview-of-power-bi-rest-api.md)  
Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

