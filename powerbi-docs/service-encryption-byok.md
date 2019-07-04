---
title: Använda egna krypteringsnycklar för Power BI (förhandsversion)
description: Lär dig hur du använder egna krypteringsnycklar i Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/18/2019
LocalizationGroup: Premium
ms.openlocfilehash: 5c93a50ce481c5fad899c1911b30100dca7cb841
ms.sourcegitcommit: 8c52b3256f9c1b8e344f22c1867e56e078c6a87c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67264473"
---
# <a name="bring-your-own-encryption-keys-for-power-bi-preview"></a>Använda egna krypteringsnycklar för Power BI (förhandsversion)

Power BI krypterar data _i vila_ och _under bearbetning_. Som standard använder Power BI Microsoft-hanterade nycklar till datakrypteringen. I Power BI Premium kan du även använda egna nycklar för data i vila som importeras till en datamängd (lär mer under [Att tänka på med datakällor och lagring](#data-source-and-storage-considerations)). Den här metoden beskrivs ofta som _BYOK_ (Bring Your Own Key).

## <a name="why-use-byok"></a>Varför ska du använda BYOK?

Med BYOK blir det enklare att uppfylla efterlevnadskrav som täcker nyckelhantering med molntjänstleverantören (i det här fallet Microsoft). Med BYOK tillhandahåller du och styr krypteringsnycklarna för dina Power BI-data i vila på appnivå. Det innebär att du kan kontrollera och återkalla organisationens nycklar om du väljer att avsluta tjänsten. När du återkallar nycklarna kan tjänsten inte läsa dina data.

## <a name="data-source-and-storage-considerations"></a>Att tänka på med datakällor och lagring

Om du vill använda BYOK måste du ladda upp data till Power BI-tjänsten från en PBIX-fil (Power BI Desktop). Du kan inte använda BYOK i följande scenarier:

- Liveanslutning till Analysis Services
- Excel-arbetsböcker (såvida inte data först importeras till Power BI Desktop)
- Push-datauppsättningar

BYOK gäller enbart för den datamängd som är associerad med PBIX-filen, inte för frågeresultatcacher för paneler och visuella objekt.

## <a name="configure-azure-key-vault"></a>Konfigurera Azure Key Vault

I det här avsnittet får du lära dig att konfigurera Azure Key Vault, ett verktyg för att lagra och få åtkomst till hemligheter, som krypteringsnycklar, på ett säkert sätt. Du kan använda ett befintligt nyckelvalv till att lagra krypteringsnycklarna eller så kan du skapa ett nytt särskilt för Power BI.

Anvisningarna i det här avsnittet förutsätter att du har grundläggande kunskaper om Azure Key Vault. Mer information finns i [Vad är en Azure Key Vault?](/azure/key-vault/key-vault-whatis). Konfigurera ditt nyckelvalv så här:

1. Lägg till Power BI-tjänsten som ett huvudnamn för nyckelvalvet med behörighet att packa ihop och packa upp.

1. Skapa en RSA-nyckel med längden 4 096 bitar (eller använd en befintlig nyckel av den här typen) med behörighet att packa ihop och packa upp.

1. Rekommenderas: Kontrollera att alternativet _mjuk borttagning_ är aktiverat för nyckelvalvet.

### <a name="add-the-service-principal"></a>Lägg till tjänstens huvudnamn

1. I ditt nyckelvalv i Azure-portalen, under **Åtkomstprinciper**, väljer du **Lägg till ny**.

1. Under **Välj huvudkonto** söker du efter och väljer Microsoft.Azure.AnalysisServices.

1. Under **Nyckelbehörigheter** väljer du **Packa upp nyckeln** och **Packa nyckeln**.

    ![Komponenter i PBIX-filen](media/service-encryption-byok/service-principal.png)

1. Välj **OK** och sedan **Spara**.

### <a name="create-an-rsa-key"></a>Skapa en RSA-nyckel

1. Under **Nycklar** i nyckelvalvet väljer du **Generera/importera**.

1. Välj RSA som **Nyckeltyp** och 4096 som **RSA-nyckelstorlek**.

    ![Komponenter i PBIX-filen](media/service-encryption-byok/create-rsa-key.png)

1. Välj **Skapa**.

1. Under **Nycklar** väljer du den nyckel du skapade.

1. Välj GUID som **Aktuell version** för nyckeln.

1. Kontrollera att både **Packa nyckel** och **Packa upp nyckel** är valda. Kopiera värdet för **Nyckelidentifierare** så att du kan använda det när du aktiverar BYOK i Power BI.

    ![Komponenter i PBIX-filen](media/service-encryption-byok/key-properties.png)

### <a name="soft-delete-option"></a>Alternativ för mjuk borttagning

Vi rekommenderar att du aktiverar [mjuk borttagning](/azure/key-vault/key-vault-ovw-soft-delete) för nyckelvalvet så att du inte förlorar några data om du skulle råka ta bort nyckeln eller nyckelvalvet. Du måste använda [PowerShell till att aktivera egenskapen ”mjuk borttagning”](/azure/key-vault/key-vault-soft-delete-powershell) för nyckelvalvet eftersom det här alternativet inte är tillgängligt i Azure-portalen ännu.

När du har konfigurerat Azure Key Vault på rätt sätt kan du aktivera BYOK för klientorganisationen.

## <a name="enable-byok-on-your-tenant"></a>Aktivera BYOK för klientorganisationen

Du aktiverar BYOK på klientorganisationsnivå med [PowerShell](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt.Admin) genom att först introducera de krypteringsnycklar du skapade och lagrade i Azure Key Vault för Power BI-klientorganisationen. Sedan tilldelar du krypteringsnycklarna per Premium-kapacitet för kryptering av innehållet i kapaciteten.

### <a name="important-considerations"></a>Att tänka på

Innan du aktiverar BYOK måste du ha följande i åtanke:

- Du kan för närvarande inte inaktivera BYOK när du har aktiverat det. Beroende på vilka parametrar du anger för `Add-PowerBIEncryptionKey` kan du styra hur BYOK ska användas för en eller flera av dina kapaciteter. Du kan däremot inte ångra introduktionen av nycklar för klientorganisationen. Mer information finns under [Aktivera BYOK](#enable-byok).

- Du kan inte _direkt_ flytta en arbetsyta som använder BYOK från en dedikerad kapacitet i Power BI Premium till en delad kapacitet. Först måste du flytta arbetsytan till en dedikerad kapacitet som inte har BYOK aktiverat.

### <a name="enable-byok"></a>Aktivera BYOK

När du ska aktivera BYOK måste du vara klientorganisationsadministratör för Power BI-tjänsten och vara inloggad med cmdleten `Connect-PowerBIServiceAccount`. Använd sedan [`Add-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/Add-PowerBIEncryptionKey) för att aktivera BYOK, som i det här exemplet:

```powershell
Add-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
```

Cmdleten tar två växlingsparametrar som påverkar krypteringen för nuvarande och framtida kapaciteter. Som standard används ingen av växlarna:

- `-Activate`: Anger att den här nyckeln ska användas för klientorganisationens alla befintliga kapaciteter.

- `-Default`: Anger att den här nyckeln nu är standard för hela klientorganisationen. När du skapar en ny kapacitet ärver kapaciteten den här nyckeln.

Om du anger `-Default`, krypteras alla kapaciteter som skapas för den här klientorganisationenen från och med nu med den nyckel som du anger (eller en uppdaterad standardnyckel). Du kan inte ångra standardåtgärden, så du kan inte längre skapa någon Premium-kapacitet som inte använder BYOK för klientorganisationen.

Du har kontroll över hur BYOK används i klientorganisationen. Om du till exempel vill kryptera en enstaka kapacitet anropar du `Add-PowerBIEncryptionKey` utan `-Activate` eller `-Default`. Anropa sedan `Set-PowerBICapacityEncryptionKey` för den kapacitet du vill aktivera BYOK för.

## <a name="manage-byok"></a>Hantera BYOK

Power BI har ytterligare cmdletar som hjälper dig att hantera BYOK för klientorganisationen:

- Använd [`Get-PowerBICapacity`](/powershell/module/microsoftpowerbimgmt.capacities/get-powerbicapacity) för att hämta nyckeln som en kapacitet använder för närvarande:

    ```powershell
    Get-PowerBICapacity -Scope Organization -ShowEncryptionKey
    ```

- Använd [`Get-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiencryptionkey) för att hämta nyckeln som klientorganisationen använder för närvarande:

    ```powershell
    Get-PowerBIEncryptionKey
    ```

- Använd [`Get-PowerBIWorkspaceEncryptionStatus`](/powershell/module/microsoftpowerbimgmt.admin/get-powerbiworkspaceencryptionstatus) för att se om datamängderna på en arbetsyta är krypterade och om krypteringsstatusen är synkroniserad med arbetsytan:

    ```powershell
    Get-PowerBIWorkspaceEncryptionStatus -Name'Contoso Sales'
    ```

    Observera att kryptering aktiveras på kapacitetsnivå, men att du ser krypteringsstatusen på datamängdsnivå för den angivna arbetsytan.

- Använd [`Set-PowerBICapacityEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/set-powerbicapacityencryptionkey) till att uppdatera krypteringsnyckeln för Power BI-kapaciteten:

    ```powershell
    Set-PowerBICapacityEncryptionKey-CapacityId 08d57fce-9e79-49ac-afac-d61765f97f6f -KeyName 'Contoso Sales'
    ```

- Använd [`Switch-PowerBIEncryptionKey`](/powershell/module/microsoftpowerbimgmt.admin/switch-powerbiencryptionkey) för att växla (eller _rotera_) versionen av den nyckel som används för kryptering. Cmdleten uppdaterar helt enkelt `-KeyVaultKeyUri` för en nyckels `-Name`:

    ```powershell
    Switch-PowerBIEncryptionKey -Name'Contoso Sales' -KeyVaultKeyUri'https://contoso-vault2.vault.azure.net/keys/ContosoKeyVault/b2ab4ba1c7b341eea5ecaaa2wb54c4d2'
    ```