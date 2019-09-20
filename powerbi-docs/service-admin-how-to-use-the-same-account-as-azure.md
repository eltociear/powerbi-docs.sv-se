---
title: Använda samma kontoinloggning för Power BI och Azure
description: Så här använder du samma kontoinloggning för Power BI och Azure
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/09/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f9659ad657c4466ad58eb40d4a07916b46f9536a
ms.sourcegitcommit: 6a44cb5b0328b60ebe7710378287f1e20bc55a25
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70877773"
---
# <a name="using-the-same-account-for-power-bi-and-azure"></a>Använda samma kontoinloggning för Power BI och Azure

Om du är en användare av både Power BI och Azure, vill du kanske använda samma inloggning för båda tjänsterna så att du inte behöver ange ditt lösenord två gånger.

Power BI loggar in dig med ditt organisationskonto som är kopplat till din arbets- eller skolmejl.  Azure loggar in dig med ett Microsoft-konto eller ditt organisationskonto.

Om du vill använda samma inloggning för både Azure och Power BI ska du logga in på Azure med ditt organisationskonto.

**Vad händer om jag redan har loggat in på Azure med mitt Microsoft-konto?**

Du kan lägga till ditt organisationskonto som medadministratör i Azure med följande steg:

1. Logga in på [Azure-portalen](http://portal.azure.com/). Om du är en användare i flera kataloger i Azure markerar du **Prenumerationer** och filtrerar sedan för att visa katalogen och de prenumerationer som du vill redigera.

1. I navigerings fönstret väljer du **åtkomstkontroll (IAM)** och väljer sedan **Lägg till** \> **Lägg till medadministratör**.

    ![Lägg till en medadministratör i Azure Portal](media/service-admin-how-to-use-the-same-account-as-azure/add-co-administrator.png)

1. Ange den e-postadress som är associerat med ditt organisationskonto och välj **Lägg till**.

1. Nästa gång du loggar in på Azure-portalen ska du använda din organisations e-postadress.

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)
