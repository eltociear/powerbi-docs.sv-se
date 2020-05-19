---
title: Anslut Microsofts hållbarhetskalkylator
description: Microsofts hållbarhetskalkylator för Power BI
author: joshthor3222
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 01/06/2020
ms.author: v-tikid
LocalizationGroup: Connect to services
ms.openlocfilehash: 8ab3dbb500faf072b87ba398b16b820c164cdefa
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83337614"
---
# <a name="connect-the-microsoft-sustainability-calculator"></a>Anslut Microsofts hållbarhetskalkylator
Få insikter om din IT-infrastrukturs koldioxid för att fatta mer hållbara beräkningsbeslut

Microsofts hållbarhetskalkylator ger nya insikter om koldioxidutsläppsdata som är associerade med Azure-tjänster. De som ansvarar för rapportering om och främjar hållbarhet inom sina organisationer har nu möjlighet att kvantifiera den koldioxidpåverkan som varje Azure-prenumeration har, samt se uppskattade koldioxidminskningar när belastningarna körs i Azure jämfört med lokala datacenter. Dessa data kan användas för rapportering av växthusgasutsläpp på nivå 3. För att få åtkomst till Microsofts hållbarhetskalkylator behöver du ditt klient-ID och din åtkomstnyckel, som vanligtvis är tillgängliga från din organisations Azure-administratör.

Om du vill använda den här appen behöver du information från Azure-företagsportalen. Företagets systemadministratörer kan hjälpa dig att få den här informationen. Läs igenom de här anvisningarna och hämta den information som krävs innan du installerar appen. 

Den här versionen av anslutningsprogrammet stöder bara Enterprise-registreringar från [https://ea.azure.com](https://ea.azure.com/). Registreringar från Kina stöds inte för tillfället.

## <a name="how-to-connect"></a>Så här ansluter du
[!INCLUDE [powerbi-service-apps-get-more-apps](../includes/powerbi-service-apps-get-more-apps.md)]

1. Välj **Microsofts hållbarhetskalkylator** \> **Hämta den nu**.
1. I **Installera den här Power BI-appen?** väljer du **Installera**.
1. Gå till fönstret **Appar** och välj ikonen **Microsofts hållbarhetskalkylator**.
1. I **Kom igång med din nya app** väljer du **Anslut**.

    ![Kom igång med din nya app](media/service-connect-to-zendesk/power-bi-new-app-connect-get-started.png)

1. Ange **företagsnamn, användarregistreringsnummer** och **antal månader \> Logga in.** Se information om att [hitta parametrarna](#finding-parameters) nedan.

    ![Företagsregistrering](media/service-connect-to-microsoft-sustainability-calculator/company-enrollment.png)

1. Som **Autentiseringsmetod** väljer du **Nyckel**och därefter **Organisation** som **Sekretessnivå**.
1. Som **Nyckel** anger du **Åtkomstnyckel \> Logga in**.

    ![Ange åtkomstnyckel](media/service-connect-to-microsoft-sustainability-calculator/access-key-entry.png)

1. Importen startar automatiskt. När den är klar visas en ny instrumentpanel, rapport och modell i **Navigeringsfönstret**. Välj rapporten för att visa dina importerade data.

## <a name="finding-parameters"></a>Hitta parametrar

Din Azure-administratör kan hjälpa dig att hitta företags **registrerings-ID** och **åtkomstnyckel**. Administratören kommer att

1. Logga in på [Azure Enterprise Portal](https://ea.azure.com) och klicka på **Hantera** i det vänstra menyfliksområdet och hämta **Registreringsnummer** enligt anvisningarna nedan
2. Från [Azure Enterprise Portal](https://ea.azure.com) klickar du på **Rapporter** och sedan på API-åtkomstnyckeln enligt det nedanstående för att hämta den primära registreringskontonyckeln

## <a name="using-the-app"></a>Använda appen

Om du vill uppdatera parametrarna när som helst navigerar du till inställningar för **datauppsättning** och gå till inställningarna för apparbetsytan. Därefter kan du uppdatera klient-ID, företagsnamn eller datamånader. När du har bekräftat parametrarna klickar du på **Uppdatera** för att läsa in data igen med de nya parametrarna.