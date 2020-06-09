---
title: Skapa app med tjänstens huvudnamn
description: Skapa app med tjänstens huvudnamn
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 0fe3e1743cb8853d6626b59b748d70bfcc292dbd
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315839"
---
1. Logga in på [Microsoft Azure](https://ms.portal.azure.com/#allservices).

2. Sök efter **Appregistreringar** och klicka på länken **Appregistreringar**.

    ![Azure-appregistrering](media/embedded-service-principal/azure-app-registration.png)

3. Klicka **Ny registrering**.

    ![ny registrering](media/embedded-service-principal/new-registration.png)

4. Fyll i nödvändig information:
    * **Namn** – Ange ett namn för ditt program
    * **Kontotyper som stöds** – Välj kontotyper som stöds
    * (Valfritt) **Omdirigerings-URI** – ange en URI om det behövs

5. Klicka på **Registrera**.

6. Efter registreringen är *Program-ID* tillgängligt på fliken **Översikt**. Kopiera och spara *Program-ID* för senare användning.

    ![program-ID](media/embedded-service-principal/application-id.png)