---
title: Always Encrypted i Power BI-rapportservern
description: I den här artikeln förklaras stödet för Always Encrypted i Power BI-rapportservern vid användning av datakällstyperna Microsoft SQL Server och Microsoft Azure SQL Database.
author: maggiesMSFT
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.author: maggies
ms.openlocfilehash: f8d711bba8dc7570f2d470554fd1d971639bbb7b
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/05/2020
ms.locfileid: "76710216"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Always Encrypted i Power BI-rapportservern

I den här artikeln förklaras stödet för Always Encrypted i Power BI-rapportservern vid användning av datakällstyperna Microsoft SQL Server och Microsoft Azure SQL Database. Mer information om Always Encrypted-funktioner i SQL Server finns i artikeln [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine).

## <a name="always-encrypted-user-isolation"></a>Always Encrypted – användarisolering

För närvarande begränsar Power BI-rapportservern inte åtkomsten till Always Encrypted-kolumner i rapporter om en användare har åtkomst till rapporten.  Om servern har fått åtkomst till kolumnkrypteringsnycklarna via kolumnhuvudnyckeln har användarna tillgång till alla kolumner för de rapporter som de har åtkomst till.

## <a name="always-encrypted-column-usage"></a>Always Encrypted – kolumnanvändning

### <a name="key-storage-strategies"></a>Strategier för nyckellagring

|Lagring  |Stöds  |
|---------|---------|
|Windows-certifikatarkiv | Ja |
|Azure Key Vault | Nej |
| CNG (Cryptography Next Generation) | Nej |

### <a name="certificate-storage-and-access"></a>Certifikatarkiv och åtkomst

Kontot som behöver åtkomst till certifikatet är tjänstkontot. Certifikatet bör lagras i certifikatarkivet på den lokala datorn. Mer information finns i:

- [Konfigurera tjänstkontot för rapportservern](https://docs.microsoft.com/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (Konfigurationshanteraren)
- Avsnittet [Göra certifikat tillgängliga för program och användare](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users) i SQL Server-artikeln ”Skapa och lagra kolumnhuvudnycklar för Always Encrypted”.

### <a name="column-encryption-strategy"></a>Strategi för kolumnkryptering

Strategin för kolumnkryptering i Power BI-rapportservern kan vara *deterministisk* eller *slumpmässig*. I följande tabell visas skillnaderna beroende på vilken strategi som används.

|Användning  |Deterministisk  |Slumpmässig  |
|---------|---------|---------|
|Kan läsas i befintligt skick i resultatet av en fråga, till exempel SELECT-uttryck. | Ja  | Ja  |
|Kan användas som en Gruppera efter-entitet i frågan. | Ja | Nej |
|Kan användas som aggregeringsfält, förutom COUNT och DISTINCT. | Nej, förutom COUNT och DISTINCT | Nej |
|Kan användas som rapportparameter | Ja | Nej |

Läs mer om [deterministisk och slumpmässig kryptering](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).

### <a name="parameter-usage"></a>Parameteranvändning

Användning av parametrar gäller endast för deterministisk kryptering.

**Enkelvärdesparameter**.  Du kan använda en enkelvärdesparameter mot en Always Encrypted-kolumn.

**Flervärdesparameter**. Du kan inte använda en flervärdesparameter med fler än ett värde mot en Always Encrypted-kolumn.

**Sammanhängande parametrar**. Du kan använda sammanhängande parametrar med Always Encrypted om *allt* följande är sant:

- Alla Always Encrypted-kolumner måste vara Always Encrypted med deterministisk strategi.
- Alla parametrar som används mot Always Encrypted-kolumner är enkelvärdesparametrar.
- Alla SQL-jämförelser använder Equals-operatorn (=).

## <a name="datatype-support"></a>Stöd för datatyp

| SQL-datatyp | Stöder läsning av fält | Stöder användning av Gruppera efter-element | Aggregeringar som stöds (COUNT, DISTINCT, MAX, MIN, SUM osv.) | Stöder filtrering via likhet med hjälp av parametrar | Information |
| --- | --- | --- | --- | --- | --- |
| int | Ja | Ja | COUNT, DISTINCT | Ja, som heltal |   |
| float | Ja | Ja | COUNT, DISTINCT | Ja, som flyttal |   |
| nvarchar | Ja | Ja | COUNT, DISTINCT | Ja, som text | För deterministisk kryptering måste du använda en kolumnsortering med en binär 2-sorteringsordning för teckenkolumner. Mer information finns i SQL Server-artikeln [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption).  |
| varchar | Ja | Ja | COUNT, DISTINCT | Nej |   |
| decimal | Ja | Ja | COUNT, DISTINCT | Nej |   |
| numeric | Ja | Ja | COUNT, DISTINCT | Nej |   |
| datetime | Ja | Ja | COUNT, DISTINCT | Nej |   |
| datetime2 | Ja | Ja | COUNT, DISTINCT | Ja, som datum/tid | Stöds om kolumnen inte har millisekunders precision (dvs. ingen datetime2(0)) |

## <a name="aggregation-alternatives"></a>Aggregeringsalternativ

De enda aggregeringar som stöds mot deterministiska Always Encrypted-kolumner är för närvarande de aggregeringar som direkt använder operatorn Equals (=). Den här SQL Server-begränsningen beror på Always Encrypted-kolumnernas utformning. Användarna måste aggregera i rapporten i stället för i databasen.

## <a name="always-encrypted-in-connection-strings"></a>Always Encrypted i anslutningssträngar

Du måste aktivera Always Encrypted i anslutningssträngen för en SQL Server-datakälla. Läs mer om hur du aktiverar [Always Encrypted i programfrågor](https://docs.microsoft.com/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries).

## <a name="next-steps"></a>Nästa steg

[Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) i SQL Server och Azure SQL Database

Fler frågor? [Fråga Power BI Community](https://community.powerbi.com/)

