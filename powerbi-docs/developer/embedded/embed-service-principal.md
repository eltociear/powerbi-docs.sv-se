---
title: Bädda in Power BI-innehåll med tjänstens huvudnamn och en programhemlighet
description: Lär dig hur du använder autentisering med inbäddad analys med hjälp av en programhemlighet och tjänstens huvudnamn för ett Azure Active Directory-program.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 05/12/2020
ms.openlocfilehash: e7b1e33322e0c1174b05a4e7b3617b5d3f7a18e8
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85231225"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>Bädda in Power BI-innehåll med tjänstens huvudnamn och en programhemlighet

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

I den här artikeln beskrivs autentisering med tjänstens huvudnamn med *program-ID* och *apphemlighet*.

>[!NOTE]
>Vi rekommenderar att du skyddar dina serverdelstjänster med certifikat, i stället för med hemliga nycklar.
>* [Läs mer om hur du hämtar åtkomsttoken från Azure AD med hjälp av hemliga nycklar eller certifikat](https://docs.microsoft.com/azure/architecture/multitenant-identity/client-assertion).
>* [Bädda in Power BI-innehåll med tjänstens huvudnamn och certifikat](embed-service-principal-certificate.md).

## <a name="method"></a>Metod

Följ dessa steg om du vill använda tjänstens huvudnamn och ett program-ID med inbäddad analys:

1. Skapa en [Azure AD-app](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-application-management).

    1. Skapa Azure AD-appens hemlighet.
    
    2. Hämta appens *program-ID* och *apphemlighet*.

    >[!NOTE]
    >De här stegen beskrivs i **steg 1**. Mer information om hur du skapar en Azure AD-app finns i artikeln [Skapa en Azure AD-App](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal).

2. Skapa en Azure AD-säkerhetsgrupp.

3. Aktivera Power BI-tjänstens administratörsinställningar.

4. Lägg till ett tjänsthuvudnamn i din arbetsyta.

5. Bädda in innehållet.

> [!IMPORTANT]
> Om du aktiverar tjänstens huvudnamn för användning med Power BI gäller inte längre programmets AD-behörigheter. Programmets behörigheter hanteras då via Power BI-administrationsportalen.

## <a name="step-1---create-an-azure-ad-app"></a>Steg 1 – Skapa en Azure AD-app

Skapa en Azure AD-app med någon av följande metoder:
* Skapa appen i [Microsoft Azure-portalen](https://portal.azure.com/#allservices)
* Skapa appen med hjälp av [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-3.6.1).

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>Skapa en Azure AD-app i Microsoft Azure-portalen

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. Klicka på fliken **Certifikat och hemligheter**.

     ![program-ID](media/embed-service-principal/certificates-and-secrets.png)


8. Klicka på **Ny klienthemlighet**

    ![ny klienthemlighet](media/embed-service-principal/new-client-secret.png)

9. I fönstret *Lägg till en klienthemlighet* anger du en beskrivning och när du vill att klienthemligheten ska upphöra att gälla. Klicka sedan på **Lägg till**.

10. Kopiera och spara värdet för *Klienthemligheten*.

    ![värde för klienthemlighet](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >När du lämnar det här fönstret döljs värdet för klienthemligheten och du kommer inte att kunna visa eller kopiera det igen.

### <a name="creating-an-azure-ad-app-using-powershell"></a>Skapa en Azure AD-app med PowerShell

Det här avsnittet innehåller ett exempelskript för att skapa en ny Azure AD-app med hjälp av [PowerShell](https://docs.microsoft.com/powershell/azure/create-azure-service-principal-azureps?view=azps-1.1.0).

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```

## <a name="step-2---create-an-azure-ad-security-group"></a>Steg 2 – Skapa en Azure AD-säkerhetsgrupp

Tjänstens huvudnamn har inte åtkomst till något av dina Power BI-innehåll eller API:er. För att ge tjänstens huvudnamn åtkomst skapar du en säkerhetsgrupp i Azure AD och lägger till tjänstens huvudnamn som du skapade i säkerhetsgruppen.

Det finns två sätt att skapa en Azure AD-säkerhetsgrupp:
* Manuellt (i Azure)
* Använda PowerShell

### <a name="create-a-security-group-manually"></a>Skapa en säkerhetsgrupp manuellt

Om du vill skapa en Azure-säkerhetsgrupp manuellt följer du anvisningarna i artikeln [Skapa en basgrupp och lägga till medlemmar med hjälp av Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal). 

### <a name="create-a-security-group-using-powershell"></a>Skapa en säkerhetsgrupp med PowerShell

Nedan är ett exempelskript för att skapa en ny säkerhetsgrupp och lägga till programmet i den säkerhetsgruppen.

>[!NOTE]
>Om du vill aktivera åtkomst med tjänstens huvudnamn för hela organisationen kan du hoppa över det här steget.

```powershell
# Required to sign in as a tenant admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>Steg 3 –Aktivera Power BI-tjänstens administratörsinställningar

För att en Azure AD-App ska kunna komma åt Power BI-innehåll och API:er måste en Power BI-administratör aktivera åtkomst till tjänstens huvudnamn i administratörsportalen för Power BI.

Lägg till den säkerhetsgrupp som du skapade i Azure AD i det specifika området för säkerhetsgrupp i **Inställningar för utvecklare**.

>[!IMPORTANT]
>Tjänstens huvudnamn har åtkomst till alla klientinställningar som de är aktiverade för. Beroende på dina administratörsinställningar inkluderar detta vissa säkerhetsgrupper eller hela organisationen.
>
>Om du vill begränsa åtkomsten till tjänstens huvudnamn till särskilda klientinställningar ger du åtkomst till vissa säkerhetsgrupper. Du kan också skapa en dedikerad säkerhetsgrupp för tjänstens huvudnamn och undanta den från önskade klientinställningar.

![Administratörsportalen](media/embed-service-principal/admin-portal.png)

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>Steg 4 – Lägg till tjänstens huvudnamn i din arbetsyta

Om du vill aktivera åtkomstartefakter för Azure AD-appen, till exempel rapporter, instrumentpaneler och datauppsättningar i Power BI-tjänsten, lägger du till entiteten för tjänstens huvudnamn som medlem eller administratör på din arbetsyta.

>[!NOTE]
>Det här avsnittet innehåller gränssnittsanvisningar. Du kan också lägga till ett tjänsthuvudnamn i en arbetsyta med hjälp av [Grupper – Lägg till API för gruppanvändare](https://docs.microsoft.com/rest/api/power-bi/groups/addgroupuser).

1. Bläddra till den arbetsyta som du vill aktivera åtkomst för och välj **Åtkomst till arbetsytan** på menyn **Mer**.

    ![Arbetsyteinställningar](media/embed-service-principal/workspace-access.png)

2. Lägg till tjänstens huvudnamn som **Administratör** eller **Medlem** på arbetsytan.

    ![Administratör för arbetsytan](media/embed-service-principal/add-service-principal-in-the-UI.png)

## <a name="step-5---embed-your-content"></a>Steg 5: Bädda in innehåll

Du kan bädda in ditt innehåll med ett exempelprogram eller i ditt program.

* [Bädda in innehåll med exempelprogrammet](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [Bädda in innehåll i programmet](embed-sample-for-customers.md#embed-content-within-your-application)

När ditt innehåll hasr bäddats in kan du [övergå till produktion](embed-sample-for-customers.md#move-to-production).

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>Nästa steg

>[!div class="nextstepaction"]
>[Registrera en app](register-app.md)

> [!div class="nextstepaction"]
>[Power BI Embedded för dina kunder](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Objekt för program och tjänstens huvudnamn i Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[Säkerhet på radnivå med hjälp av lokal datagateway med tjänstens huvudnamn](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[Bädda in Power BI-innehåll med tjänstens huvudnamn och certifikat](embed-service-principal-certificate.md)
