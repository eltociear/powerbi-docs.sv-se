---
title: Anslut till en Impala-databas i Power BI Desktop
description: Anslut enkelt till och använd en Impala-databas i Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: a12ee2acd741666395b69dbb739b2f6308a924b7
ms.sourcegitcommit: 2ae660a7b70fce23eb58b159d049eca44a664f2c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52669530"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>Anslut till en Impala-databas i Power BI Desktop
I Power BI Desktop kan du ansluta till en **Impala**-databas och använda underliggande data precis som andra datakällor i Power BI Desktop.

## <a name="connect-to-an-impala-database"></a>Anslut till en Impala-databas
För att ansluta till en **Impala**-databas gör du följande: 

1. Välj **Hämta data** från menyfliksområdet **Start** i Power BI Desktop. 

2. Välj **Databas** från kategorierna till vänster. Du kommer att se **Impala**.

    ![Hämta data](media/desktop-connect-impala/connect_impala_2.png)

3. I **Impala**-fönstret som visas, skriver eller klistrar du in namnet på din Impala-server i rutan. Välj sedan **OK**. Du kan **Importera** data direkt i Power BI, eller så kan du använda **DirectQuery**. Läs mer om att [använda DirectQuery](desktop-use-directquery.md).

    ![Impala-fönstret](media/desktop-connect-impala/connect_impala_3a.png)

4. När du uppmanas, ange dina autentiseringsuppgifter eller anslut anonymt. Impala-anslutningsappen stöder Anonymous-, Basic- (användarnamn + lösenord) och Windows-autentisering.

    ![Impala-anslutningsapp](media/desktop-connect-impala/connect_impala_4.png)

    > [!NOTE]
    > När du anger ditt användarnamn och lösenord för en viss **Impala**-server, använder Power BI Desktop samma autentiseringsuppgifter i efterföljande anslutningsförsök. Du kan ändra autentiseringsuppgifterna genom att gå till **Arkiv > Alternativ och inställningar > Inställningar för datakälla**.


5. När du har anslutit öppnas ett **Navigator**-fönster som visar de data som är tillgängliga på servern. Välj element från dessa data som du vill importera och använda i **Power BI Desktop**.

    ![Navigatorfönstret](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar
Det finns några begränsningar och överväganden att tänka på med anslutningsappen för **Impala**:

* Impala-anslutningsappen stöds på lokala datagateway med hjälp av tre autentiseringsmekanismer.

## <a name="next-steps"></a>Nästa steg
Det finns många olika datakällor du kan ansluta till med Power BI Desktop. Kolla in följande resurser för mer information om datakällor:

* [Vad är Power BI Desktop?](desktop-what-is-desktop.md)
* [Datakällor i Power BI Desktop](desktop-data-sources.md)
* [Forma och kombinera data i Power BI Desktop](desktop-shape-and-combine-data.md)
* [Anslut till Excel-arbetsböcker i Power BI Desktop](desktop-connect-excel.md)   
* [Ange data direkt i Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

