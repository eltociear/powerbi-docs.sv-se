---
title: Aktivera känslighetsetiketter för data i Power BI
description: Lär dig att aktivera känslighetsetiketter för data i Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/23/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: ba1cacfa930bcc0ed51234dea13639420ac8fab7
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315659"
---
# <a name="enable-data-sensitivity-labels-in-power-bi"></a>Aktivera känslighetsetiketter för data i Power BI

[Datakänslighetsetiketter från Microsoft Information Protection](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) måste vara aktiverade i klientorganisationen för att kunna användas i Power BI. I den här artikeln kan Power BI-klientadministratörer se hur de gör detta. Om du vill få en översikt av känslighetsetiketter för data i Power BI kan du läsa [Dataskydd i Power BI](service-security-data-protection-overview.md). Mer information om att tillämpa känslighetsetiketter i Power BI finns i [Tillämpa känslighetsetiketter](../collaborate-share/service-security-apply-data-sensitivity-labels.md) 

När känslighetsetiketter är aktiverade:

* Angivna användare och säkerhetsgrupper i organisationen kan klassificera och [tillämpa känslighetsetiketter](../collaborate-share/service-security-apply-data-sensitivity-labels.md) för sina rapporter, instrumentpaneler, datamängder och dataflöden i Power BI.
* Alla medlemmar i organisationen kan se de här etiketterna.

När du ska aktivera känslighetsetiketter för data behöver du en licens för Azure Information Protection. Mer information finns i [Licensiering](service-security-data-protection-overview.md#licensing).

## <a name="enable-data-sensitivity-labels"></a>Aktivera känslighetsetiketter för data

Gå till **administrationsportalen** för Power BI, öppna panelen **Klientinställningar** och letar reda på avsnittet **Informationsskydd**.

![Leta rätt på avsnittet Information Protection](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-01.png)

Utför följande steg i avsnittet **Information Protection**:
1. Öppna **Låt användare tillämpa känslighetsetiketter för Power BI-innehåll**.
1. Aktivera växlingsknappen.
1. Definiera vem som kan tillämpa och ändra känslighetsetiketter för Power BI-tillgångar. Som standard kan alla i organisationen tillämpa känslighetsetiketter. Du kan dock välja att endast låta vissa användare eller säkerhetsgrupper ställa in känslighetsetiketter. Om du väljer antingen hela organisationen eller specifika säkerhets grupper kan du undanta vissa delmängder av användare eller säkerhetsgrupper.
   
   * När känslighetsetiketter är aktiverade för hela organisationen är undantagen normalt säkerhetsgrupper.
   * När känslighetsetiketter bara är aktiverade för vissa användare eller säkerhetsgrupper så är undantagen normalt specifika användare.  
    Det här gör att du kan förhindra att vissa användare tillämpar känslighetsetiketter i Power BI, även om de tillhör en grupp som har behörighet att göra det.

1. Tryck på **Tillämpa**.

![Aktivera känslighetsetiketter](media/service-security-enable-data-sensitivity-labels/enable-data-sensitivity-labels-02.png)

> [!IMPORTANT]
> Det är bara Power BI Pro-användare med behörigheterna *skapa* och *redigera* för tillgången, och som ingår i säkerhetsgruppen du angav i avsnittet, som kan ställa in och redigera känslighetsetiketter. Användare som inte ingår i den här gruppen kan inte ställa in eller redigera etiketter.  

## <a name="troubleshooting"></a>Felsökning

Power BI använder känslighetsetiketter från Microsoft Information Protection. Om du får ett felmeddelande när du försöker aktivera känslighetsetiketter kan det bero på något av följande:

* Du har ingen [licens](service-security-data-protection-overview.md#licensing) för Azure Information Protection.
* Känslighetsetiketter har inte migrerats till den version av Microsoft Information Protection som stöds i Power BI. Läs mer om att [migrera känslighetsetiketter](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels).
* Inga känslighetsetiketter från Microsoft Information Protection har definierats i organisationen. Observera att en etikett måste vara en del av en publicerad princip för att kunna användas. [Läs mer om känslighetsetiketter](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) eller besök [Microsofts säkerhets- och efterlevnadscenter](https://sip.protection.office.com/sensitivity?flight=EnableMIPLabels) för att läsa om hur du definierar etiketter och publicerar policyer för din organisation.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

I den här listan anges några begränsningar för känslighetsetiketter i Power BI:

**Allmänt**
* Du kan bara tillämpa känslighetsetiketter på instrumentpaneler, rapporter, datamängder och dataflöden. För närvarande är de inte tillgängliga för [sidnumrerade rapporter](../paginated-reports/report-builder-power-bi.md) och arbetsböcker.
* Känslighetsetiketter på Power BI-tillgångar visas i vyerna Arbetsytelista, Ursprung, Favoriter, Senaste och Appar. För närvarande visas inte etiketter i vyn Delat med mig. Men även om du inte ser en etikett som tillämpats på en Power BI-tillgång så gäller den även efter export till Excel-, PowerPoint- eller PDF-format.
* Känslighetsetiketter stöds bara för klientorganisationer i det globala (offentliga) molnet. Känslighetsetiketter stöds inte för klientorganisationer i andra moln.
* Datakänslighetsetiketter stöds inte för mallappar. Känslighetsetiketter som anges av mallappens skapare tas bort när appen extraheras och installeras, och känslighetsetiketter som lagts till i artefakter i en installerad mallapp av appkonsumenten går förlorade (återställs till ingenting) när appen uppdateras.
* Power BI stöder inte känslighetsetiketter av skyddstyperna [Vidarebefordra inte](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [Användardefinierat](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) och [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). Skyddstyperna Vidarebefordra inte och Användardefinierat är etiketter som definieras i [Microsoft 365 Säkerhetscenter](https://security.microsoft.com/) eller [Microsoft 365 Efterlevnadscenter](https://compliance.microsoft.com/).
* Det är inte rekommenderat att tillåta användare att tillämpa överordnade etiketter i Power BI. Om en överordnad etikett tillämpas på innehåll kommer en export av data från det innehållet till en fil (Excel, PowerPoint och PDF) att misslyckas. Mer information finns i avsnittet om [underetiketter (etikettgruppering)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels).

**Export**
* Etikett- och skyddskontroller tillämpas endast när data exporteras till Excel-, PowerPoint- och PDF-filer. Etikett och skydd tillämpas inte när data exporteras till CSV- eller PBIX-filer, Analysera i Excel eller andra exportsökvägar.
* När du tillämpar en känslighetsetikett och skydd på en exporterad fil, läggs ingen innehållsmärkning till för filen. Om etiketten har konfigurerats att använda innehållsmärkningar tillämpas de dock automatiskt av Azure Information Protection-klienten för enhetliga etiketter när filen öppnas i Office-skrivbordsappar. Innehållsmärkningarna tillämpas inte automatiskt när du använder inbyggd märkning för skrivbords-, mobil- eller webbappar. Mer information finns i avsnittet om [innehållsmärkning och kryptering med Office-appar](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption).
* Användare som exporterar en fil från Power BI har behörighet att komma åt och redigera filen enligt inställningarna för känslighetsetiketten. Användaren som exporterar data får inte ägarbehörighet till filen.
* Exporten misslyckas om det inte går att tillämpa en etikett när data exporteras till en fil. Du kan kontrollera om exporten misslyckades på grund av att det inte gick att tillämpa etiketten. Klicka bara på rapportens eller instrumentpanelens namn i mitten av namnlisten och se om ”Det går inte att läsa in känslighetsetiketten” visas i listrutan som öppnas. Detta kan hända om den tillämpade etiketten har avpublicerats eller tagits bort av säkerhetsadministratören, eller på grund av ett tillfälligt systemfel.

## <a name="next-steps"></a>Nästa steg

I den här artikeln beskrivs hur du aktiverar känslighetsetiketter för data i Power BI. De här artiklarna innehåller mer information om dataskydd i Power BI. 

* [Översikt över dataskydd i Power BI](service-security-data-protection-overview.md)
* [Använda känslighetsetiketter för data i Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Använda Microsoft Cloud App Security-kontroller i Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Dataskyddsmåttrapport](service-security-data-protection-metrics-report.md)