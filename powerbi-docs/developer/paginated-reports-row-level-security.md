---
title: Säkerhet på radnivå med inbäddat innehåll i Power BI
description: Läs mer om vad du behöver göra för att bädda in Power BI-innehåll i ditt program.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 11/04/2019
ms.openlocfilehash: 09471cdacacc8d0b1067598cefac41915b0ef0d7
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78920910"
---
# <a name="implementing-row-level-security-in-embedded-paginated-reports-preview"></a>Implementera säkerhet på radnivå i inbäddade sidnumrerade rapporter (förhandsversion)

När du bäddar in en sidnumrerad rapport kan du styra vilka data som ska visas. På så sätt kan du skräddarsy vilken information som ska visas per användare. Om du till exempel har en sidnumrerad Power BI-rapport som innehåller globala försäljningsresultat, kan du bädda in den så att endast försäljningsresultaten från en viss region är tillgängliga.

Den här funktionen ger ett säkert sätt att visa en delmängd av datan, utan att äventyra resten av informationen. Det liknar funktionen [Säkerhet på radnivå (RLS)](embedded-row-level-security.md), som är en säker metod att visa data på i Power BI-rapporter (som inte är sidnumrerade), instrumentpaneler, paneler och datamängder.  

> [!Note]
> Den här funktionen kan användas för inbäddade och sidnumrerade rapporter för kunder.

## <a name="configuring-a-parameter-to-filter-the-dataset"></a>Konfigurera en parameter som filtrerar datamängden

När du använder säkerhet på radnivå i en sidnumrerad Power BI-rapport, måste du tilldela en [-parameter](../paginated-reports/report-builder-parameters.md) till **UserID**-attributet. Parametern begränsar vilka data som hämtas från datamängden innan rapporten bäddas in.

När du har tilldelat parametern till **UserID**, använder du API:et [Reports GenerateTokenForCreateInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup) till att hämta din inbäddningstoken.

## <a name="use-userid-as-a-filter-at-report-or-query-level"></a>Använda UserID som filter på rapport- eller frågenivå

Du kan använda **UserId** som ett *filter* eller i en *fråga* till datakällan i [Power BI Report Builder](../paginated-reports/report-builder-power-bi.md).

### <a name="using-the-filter"></a>Använda filtret

1. I fönstret **Egenskaper för datamängd** väljer du **Filter** i den vänstra rutan.

    ![Power BI Report Builder-filter](media/embedded-paginated-reports-secure-data/filter.png)

2. Välj den parameter som du vill använda när du filtrerar data i listmenyn **Uttryck**.

     ![Power BI Report Builder-uttryck](media/embedded-paginated-reports-secure-data/expression.png)

3. Klicka på funktionsknappen **Värde**. 

    ![Power BI Report Builder-värde](media/embedded-paginated-reports-secure-data/function.png)

4. Välj **Inbyggda fält** i fönstret **Uttryck** i listan **Kategori**.

    ![Power BI Report Builder-uttryck](media/embedded-paginated-reports-secure-data/built-in-fields.png)

5. Välj **UserID** i listan **Objekt** och klicka på **OK**.

    ![UserID för Power BI Report Builder](media/embedded-paginated-reports-secure-data/userid.png)

6. I fönstret **Egenskaper för datamängd** kontrollerar du att uttrycket är *den valda parametern = UserID*. Klicka sedan på **OK**.

    ![Egenskaper för Power BI Report Builder-datamängd](media/embedded-paginated-reports-secure-data/verify.png)

### <a name="using-a-query"></a>Använda en fråga

1. I fönstret **Egenskaper för datamängd** väljer du **Parametrar** i det vänstra fönstret och klickar på **Lägg till**.

    ![Power BI Report Builder-parametrar](media/embedded-paginated-reports-secure-data/parameters.png)

2. I **Parameternamn** anger du **\@UserID**, och i **Parametervärde** lägger du till **[&UserID]** .

    ![Power BI Report Builder-parameternamn](media/embedded-paginated-reports-secure-data/parameter-name.png) 

3. I den vänstra rutan väljer du **Fråga** och i frågan lägger du till **UserID**-parametern som en del av din fråga. Klicka sedan på **OK**.
    > [!NOTE]
    > I skärmbilden nedan används färgparametern som exempel (whereFinalTable.Color = @UserID). Vid behov är det möjligt att skapa en mer komplex fråga.

    ![Redigering av Power BI Report Builder-frågor](media/embedded-paginated-reports-secure-data/query-edit.png)

## <a name="passing-the-configured-parameter-using-the-embed-token"></a>Skicka den konfigurerade parametern med hjälp av en inbäddningstoken

När du bäddar in en sidnumrerad rapport åt dina kunder, används API:et [Reports GenerateTokenForCreateInGroup](https://docs.microsoft.com/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup) till att hämta en inbäddningstoken. Denna token kan också användas till att filtrera några av de data som hämtas från den sidnumrerade rapporten.

Om du bara vill exponera vissa data tilldelar du fältet `username` den information som du vill ska visas. Om du till exempel anger *grönt* i fältet `username` i en sidnumrerad rapport med en färgparameter, begränsar din inbäddningstoken inbäddade data så att de endast visar data med värdet *grönt* i färgkolumnen.

```JSON
{
    "accessLevel": "View",
    "reportId": "cfafbeb1-8037-4d0c-896e-a46fb27ff229",
    "identities": [
            {
                    // Replace the 'username' with a paginated report parameter
                    "username":     "...",
                    "reports: [
                        "cfafbeb1-8037-4d0c-896e-a46fb27ff229"
                    ]
            }
    ]
}
```
