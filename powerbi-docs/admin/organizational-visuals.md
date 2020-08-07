---
title: Visuella objekt för organisationer
description: I den här artikeln beskrivs administratörsfunktioner för organisationskontroller.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 07/01/2020
ms.openlocfilehash: 4b112c3522a35f86f74481a79f3fff919a0e9e33
ms.sourcegitcommit: 2131f7b075390c12659c76df94a8108226db084c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544837"
---
# <a name="manage-power-bi-visuals-admin-settings"></a>Hantera administrationsinställningar för visuella Power BI-objekt

Som Power BI-administratör i organisationen kan du styra vilken typ av Power BI-kontroller som användarna har tillgång till.

För att hantera Power BI-kontroller måste du vara global administratör i Office 365 eller ha tilldelats rollen som administratör för Power BI-tjänsten. Läs mer om administratörsrollen för Power BI-tjänsten i [Förstå administratörsrollen för Power BI](service-admin-role.md).

## <a name="access-the-admin-portal"></a>Använda administratörsportalen

Du aktiverar inställningarna som beskrivs i artikeln i administratörsportalen.

1. Välj **Inställningar** i Power BI-tjänsten.

2. Välj **Administratörsportal** från inställningsmenyn.

    ![Formulär för visuella Power BI-objekt](media/organizational-visuals/admin-portal.png)

## <a name="power-bi-visuals-tenant-settings"></a>Inställningar för Power BI-kontroller på klientorganisationsnivå

Som Power BI-administratör i organisationen kan du styra vilken typ av Power BI-kontroller som användarna har tillgång till.

Gränssnittsinställningarna för klientorganisationer gäller bara Power BI-tjänsten. Om du vill använda samma inställningar i Power BI Desktop ska du använda grupprinciper. I slutet av varje avsnitt finns en tabell där det står hur du aktiverar inställningen i Power BI Desktop.

>[!NOTE]
>När du ändrar inställningar för en klientorganisation påverkas inte Power BI-kontrollerna på fliken [Organisationskontroller](#organizational-visuals).

### <a name="visuals-from-appsource-or-a-file"></a>Kontroller från AppSource eller en fil

Hantera organisationens åtkomst till följande typer av Power BI-kontroller:

* Kontroller som utvecklare skapat och sparat som .pbiviz-filer.

* Kontroller från AppSource.

Följ anvisningarna nedan om du vill att användare i organisationen ska kunna ladda upp .pbiviz-filer och lägga till kontroller från AppSource i sina rapporter och instrumentpaneler.

1. Visa inställningarna under **Tillåt visuella objekt som skapats med Power BI SDK**.

2. Klicka på **Aktiverad**.

3. Välj vilka som ska kunna ladda upp .pbiviz- och AppSource-kontroller:

    * Välj **Hela organisationen** om alla i organisationen ska kunna ladda upp .pbiviz-filer och lägga till kontroller från AppSource.

     * Välj alternativet **Vissa säkerhetsgrupper** om du vill hantera uppladdningen av .pbiviz-filer och kontroller från AppSource med hjälp av säkerhetsgrupper. Lägg till de säkerhetsgrupper du vill hantera i fältet *Ange säkerhetsgrupper*. De säkerhetsgrupper du anger exkluderas som standard. Om du vill ta med de här säkerhetsgrupperna och exkludera alla andra i organisationen väljer du alternativet **Förutom vissa säkerhetsgrupper**.

4. Klicka på **Godkänn**.

![visuella objekt från fil eller AppSource](media/organizational-visuals/tenant-settings.png)

Ändringar av inställningar för klientorganisationer i gränssnittet gäller bara för Power BI-tjänsten. Om du vill att användare i organisationen ska kunna ladda upp .pbiviz-filer och lägga till kontroller från AppSource i visualiseringsfönstret i Power BI Desktop använder du en [Azure AD-grupprincip](https://docs.microsoft.com/azure/active-directory-domain-services/manage-group-policy).

|Nyckel  |Värdenamn  |Värde  |
|---------|---------|---------|
|Programvara\Principer\Microsoft\Power BI Desktop\    |EnableCustomVisuals    |0 – Avaktivera </br>1 – Aktivera (standard)         |
|

### <a name="certified-power-bi-visuals"></a>Certifierade visuella Power BI-objekt

När du aktiverar den här inställningen återges endast [certifierade Power BI-kontroller](../developer/visuals/power-bi-custom-visuals-certified.md) i organisationens rapporter och instrumentpaneler. Power BI-kontroller från AppSource och filer som inte är certifierade returnerar ett felmeddelande.

1. Välj **Lägg till och använd endast certifierade kontroller**i administratörsportalen.

2. Klicka på **Aktiverad**.

3. Klicka på **Godkänn**.

![certifierade kontroller](media/organizational-visuals/certified-visuals.png)

Ändringar av inställningar för klientorganisationer i gränssnittet gäller bara för Power BI-tjänsten. Om du vill hantera inställningen om certifierade kontroller för klientorganisationen i Power BI Desktop använder du en [Azure AD-grupprincip](https://docs.microsoft.com/azure/active-directory-domain-services/manage-group-policy).

|Nyckel  |Värdenamn  |Värde  |
|---------|---------|---------|
|Programvara\Principer\Microsoft\Power BI Desktop\    |EnableUncertifiedVisuals    |0 – Avaktivera </br>1 – Aktivera (standard)         |
|

## <a name="organizational-visuals"></a>Visuella objekt för organisationer

Som Power BI-administratör kan du hantera listan med Power BI-kontroller som är tillgängliga i [organisationslagret](../developer/visuals/power-bi-custom-visuals.md#organizational-store). På fliken **Organisationskontroller** i *administratörsportalen* kan du lägga till och ta bort kontroller och bestämma vilka kontroller som ska visas automatiskt i visualiseringsfönstret för organisationens användare. Du kan lägga till alla typer av kontroller i listan, även kontroller som inte är certifierade och .pbiviz-kontroller, och det spelar ingen roll om de strider mot [inställningarna för klientorganisationen](#power-bi-visuals-tenant-settings).

Inställningarna för organisationskontroller distribueras automatiskt till Power BI Desktop.

>[!NOTE]
>Organisationskontroller stöds inte i Power BI Report Server.

### <a name="add-a-visual-from-a-file"></a>Lägga till en kontroll från en fil

Använd den här metoden när du ska lägga till en ny Power BI-kontroll från en .pbiviz-fil.

> [!WARNING]
> En Power BI-kontroll som laddas upp från en fil kan innehålla kod som innebär säkerhets- eller integritetsrisker. Kontrollera att författaren och källan till kontrollen är betrodda innan du distribuerar den till organisationens lagringsplats.

1. Välj **Lägg till kontroll** > **Från en fil**.

    ![lägga till kontroller från en fil](media/organizational-visuals/add-from-file.png)

2. Fyll i följande fält:

    * **Välj en .pbiviz-fil** – välj en kontrollfil att ladda upp.

    * **Ge kontrollen ett namn** – ge kontrollen en kort rubrik så att rapportförfattarna enkelt kan se vad den gör.

    * **Ikon** – ladda upp en ikonfil som ska visas i visualiseringsfönstret.

    * **Beskrivning** – ange en kort beskrivning av kontrollen som ger användaren mer kontext.

    * **Åtkomst** – det här avsnittet innehåller två alternativ:
    
        * Välj om användarna i organisationen ska ha åtkomst till kontrollen. Den här inställningen är aktiverad som standard.

        * Välj om organisationens användare ska se kontrollen i visualiseringsfönstret. Den här inställningen är avaktiverad som standard. Mer information finns i [Lägga till en kontroll i visualiseringsfönstret](#add-a-visual-to-the-visualization-pane).

    ![lägg till kontroll](media/organizational-visuals/add-visual.png)

3. Initiera uppladdningen genom att välja **Lägg till**. När kontrollen har laddats upp visas den i listan med organisationskontroller.

### <a name="add-a-visual-from-appsource-preview"></a>Lägga till en kontroll från AppSource (förhandsversion)

Använd den här metoden när du ska lägga till en ny Power BI-kontroll från AppSource.

Power BI-kontroller från AppSource uppdateras automatiskt. Användarna i organisationen har alltid tillgång till den senaste versionen av kontrollen.

1. Välj **Lägg till kontroll** > **Från AppSource**.

    ![lägga till kontroller från AppSource](media/organizational-visuals/add-visual-from-appsource.png)

2. Leta rätt på AppSource-kontrollen du vill lägga till i fönstret **Power BI-kontroller** och klicka på **Lägg till**. När kontrollen har laddats upp visas den i listan med organisationskontroller.

### <a name="add-a-visual-to-the-visualization-pane"></a>Lägga till ett visuellt objekt i visualiseringsfönstret

Du kan välja kontroller från sidan med organisationskontroller om du vill att alla användare i organisationen ska se dem i visualiseringsfönstret.

1. Klicka på **Inställningar** i raden för kontrollen du vill lägga till.

    ![organisationsfönster](media/organizational-visuals/organizational-pane.png)organisationsfönster

2. Aktivera inställningen för visualiseringsfönstret och klicka på **Uppdatera**.

    ![uppdatera-organisationsfönster](media/organizational-visuals/update-organizational-pane.png)

### <a name="delete-a-visual-uploaded-from-a-file"></a>Ta bort en kontroll som laddats upp från en fil

Välj papperskorgen om du vill ta bort det visuella objektet permanent från databasen.

> [!IMPORTANT]
> Du kan inte ångra borttagningen. När det visuella objektet väl har tagits bort upphör det omedelbart att återges i befintliga rapporter. Även om du laddar upp samma kontroll igen ersätter den inte kontrollen du tog bort. Användare kan dock importera det nya visuella objektet igen och ersätta den version som de har i sina rapporter.

### <a name="disable-a-pbiviz-visual"></a>Inaktivera en .pbiviz-kontroll

Du kan inaktivera en .pbiviz-kontroll så att den inte är tillgänglig via [organisationslagret](../developer/visuals/power-bi-custom-visuals.md#organizational-store) samtidigt som du behåller den i listan med organisationskontroller.

1. Klicka på **Inställningar** i raden för .pbiviz-kontrollen du vill inaktivera.

2. Inaktivera följande inställning i avsnittet **Åtkomst**: *Användare i organisationen kan komma åt, visa, dela och interagera med det här visuella objektet*.

När du har inaktiverat .pbiviz-kontrollen återges den inte i befintliga rapporter utan visar felmeddelandet nedan:

*Detta anpassade visuella objekt är inte längre tillgängligt. Kontakta din administratör om du vill ha mer information.*

>[!NOTE]
>.pbiviz-kontroller med bokmärken fortsätter att fungera även när de har inaktiverats.

### <a name="update-a-visual"></a>Uppdatera ett visuellt objekt

AppSource-kontroller uppdateras automatiskt. När en ny version blir tillgänglig från AppSource ersätter den äldre versioner som distribuerats via listan med organisationskontroller.

Om du vill uppdatera en .pbiviz-kontroll gör du så här:

1. Klicka på **Inställningar** i raden för kontrollen du vill lägga till.

2. Klicka på **Bläddra** och välj den .pbiviz-fil du vill ersätta den befintliga kontrollen med.

3. Klicka på **Uppdatera**.

## <a name="next-steps"></a>Nästa steg

> [!div class="nextstepaction"]
>[Administrera Power BI i Admin-portalen](service-admin-portal.md)

> [!div class="nextstepaction"]
>[Visuella objekt i Power BI](../developer/visuals/power-bi-custom-visuals.md)

> [!div class="nextstepaction"]
>[Organisationskontroller i Power BI](../developer/visuals/power-bi-custom-visuals-organization.md)