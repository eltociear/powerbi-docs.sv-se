---
title: Installera Power BI-appar automatiskt vid inbäddning för din organisation
description: Lär dig hur du installerar Power BI-appar automatiskt vid inbäddning för din organisation.
ms.subservice: powerbi-developer
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: 0adfb72c408f96749afc8a3d7a6884e10e52fadb
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "80114691"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Installera Power BI-appar automatiskt vid inbäddning för din organisation

Om en användare vill bädda in innehåll från en app måste användaren bäddar in ha [åtkomst till appen](../../service-create-distribute-apps.md). Om appen är installerad för användaren fungerar inbäddningen smidigt. Mer information finns i [Bädda in rapporter eller instrumentpaneler från en app](embed-from-apps.md). I PowerBI.com kan du definiera att alla appar ska kunna [installeras automatiskt](https://powerbi.microsoft.com/blog/automatically-install-apps/). Den här åtgärden görs dock för hela klientorganisationen och gäller för alla appar.

## <a name="auto-install-app-on-embedding"></a>Installera appar automatiskt vid inbäddning

Om en användare har åtkomst till en app utan att appen är installerad så misslyckas inbäddningen. Du kan undvika sådana fel vid inbäddning från en app genom att tillåta automatisk installation av appen vid inbäddningen. Det här innebär att appen installeras automatiskt om användaren försöker bädda in en app som inte är installerad. Innehållet du vill använda bäddas alltså in direkt vilket är smidigt för användaren.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Inbäddning för Power BI-användare (användaren äger data)

Om du vill tillåta att appar installeras automatiskt för dina användare måste du ge appen behörigheten ”Skapa innehåll” när du [registrerar appen](register-app.md#register-with-the-power-bi-application-registration-tool), eller så lägger du till behörigheten om appen redan är registrerad.

![Skapa innehåll vid appregistrering](media/embed-auto-install-app/register-app-create-content.png)

Sedan måste du ange appens ID i den inbäddade webbadressen. För att kunna ange appens ID måste den som skapat appen först installera den och sedan anropa något av de [Rest-API:er för Power BI](https://docs.microsoft.com/rest/api/power-bi/) som stöds – [Hämta rapporter](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) eller [hämta instrumentpaneler](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). Appskaparen måste sedan hämta den inbäddade webbadressen ur svaret från REST-API:et. App-ID:t visas i webbadressen om innehållet kommer från en app.  När du har inbäddade webbadressen kan du använda den till att bädda in regelbundet.

## <a name="secure-embed"></a>Säker inbäddning

Om du vill installera appar automatiskt måste du först installera appen, sedan navigera till appen på PowerBI.com, öppna rapporten och hämta länken som vanligt. Alla andra användare med åtkomst till appen kan använda länken till att bädda in rapporten.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

* Du kan bara bädda in rapporter och instrumentpaneler i det här scenariot.

* Den här funktionen stöds för närvarande inte om appen äger data eller i scenarier med SharePoint-inbäddning.