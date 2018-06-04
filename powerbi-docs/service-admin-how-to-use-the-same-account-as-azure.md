---
title: Använda samma kontoinloggning för Power BI och Azure
description: Så här använder du samma kontoinloggning för Power BI och Azure
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/28/2017
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 375a251e7515ad33396cc4cf5ebb0ee715ab0330
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34254043"
---
# <a name="using-the-same-account-for-power-bi-and-azure"></a>Använda samma kontoinloggning för Power BI och Azure
Om du är en användare av både Power BI och Azure, vill du kanske använda samma inloggning för båda tjänsterna så att du inte behöver ange ditt lösenord två gånger.

Power BI loggar in dig med ditt organisationskonto som är kopplat till din arbets- eller skolmejl.  Azure loggar in dig med ett Microsoft-konto eller ditt organisationskonto.

Om du vill använda samma inloggning för både Azure och Power BI ska du logga in på Azure med ditt organisationskonto.

**Vad händer om jag redan har loggat in på Azure med mitt Microsoft-konto?**

Du kan lägga till ditt organisationskonto som medadministratör i Azure.  Gör så här:

1. Logga in på [Azure Management Portal](http://manage.windowsazure.com/). Om du är en användare i flera kataloger i Azure, klickar du på **Prenumerationer** och filtrerar sedan för att visa katalogen och de prenumerationer som du vill redigera.
2. I navigeringsfönstret klickar du på **Inställningar**. Klicka på **Administratörer** och sedan på **Lägg till**.
3. Ange den e-postadress som är associerat med ditt organisationskonto.
4. Välj den prenumeration som du vill komma åt med ditt organisationskonto och sedan klicka på kryssrutan.

Nästa gång du loggar in på Azure-hanteringsportalen ska du använda din organisations e-postadress.

Har du fler frågor? [Prova Power BI Community](http://community.powerbi.com/)

