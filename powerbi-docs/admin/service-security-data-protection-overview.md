---
title: Dataskydd i Power BI
description: Lär dig hur dataskyddet fungerar i Power BI
author: paulinbar
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/21/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: fa969f8f738cf09e9e01e284de8f60e2fd8ce9ab
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315682"
---
# <a name="data-protection-in-power-bi"></a>Dataskydd i Power BI

Moderna företag har strikta affärsregler och krav på hur känsliga data ska hanteras och skyddas. Power BI är integrerat med Microsoft Information Protection och Microsoft Cloud App Security för att ge kontroll och synlighet över den här speciella typen av data. Detta innebär att du kan:
* Använd [känslighetsetiketter](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide) i Microsoft Information Protection för att klassificera och märka innehåll (instrumentpaneler, rapporter, datauppsättningar och dataflöden) i Power BI-tjänsten, med samma taxonomi som används för att klassificera och skydda filer i Office 365.
* Använd känslighetsetiketter och skydd i Microsoft Information Protection när du exporterar data till Excel-, PowerPoint- eller PDF-filer.
* Använd Microsoft Cloud App Security till att övervaka aktiviteter i Power BI, undersöka säkerhetsproblem och skydda innehåll i Power BI med appkontrollen för villkorsstyrd åtkomst i Microsoft Cloud App Security.

**Viktiga meddelanden**
* Känslighetsetiketter **påverkar** inte åtkomsten till innehåll i Power BI – åtkomsten till innehåll i Power BI hanteras alltid av Power BI-behörigheter. Etiketterna är synliga, men associerade krypteringsinställningar (som konfigurerats i [Microsoft 365 Security Center](https://security.microsoft.com/) eller [Microsoft 365 Compliance Center](https://compliance.microsoft.com/)) tillämpas inte. De tillämpas endast på data som exporteras till Excel-, PowerPoint- och PDF-filer.
* Känslighetsetiketter och filkryptering tillämpas **inte** på andra exportsökvägar än exporter till Excel, PowerPoint och PDF. Administratören av Power BI-klientorganisationen kan inaktivera en eller flera exportsökvägar som inte stöder användning av känslighetsetiketter och associerade filkrypteringsinställningar.

## <a name="sensitivity-labels-in-power-bi"></a>Känslighetsetiketter i Power BI

Känslighetsetiketter skapas och hanteras antingen i [säkerhetscentret för Microsoft 365](https://security.microsoft.com/) eller i [efterlevnadscentret för Microsoft 365](https://compliance.microsoft.com/).

Om du vill hantera känslighetsetiketter på någon av de här platserna går du till **Klassificering > Känslighetsetiketter**. De här känslighetsetiketterna kan användas i flera Microsoft-tjänster som Azure Information Protection, Office-appar och Office 365-tjänster.

> [!Important]
> Om din organisation använder känslighetsetiketter i Azure Information Protection måste du [migrera](https://docs.microsoft.com/azure/information-protection/configure-policy-migrate-labels) dem till någon av de tidigare angivna tjänsterna för att etiketterna ska kunna användas i Power BI.

> [!NOTE]
> Känslighetsetiketter kan bara användas för klientorganisationer i offentliga moln, inte för klientorganisationer i exempelvis självständiga moln.

## <a name="how-sensitivity-labels-work-in-power-bi"></a>Så här fungerar känslighetsetiketter i Power BI

När du tillämpar en känslighetsetikett på en instrumentpanel, en rapport, en datamängd eller ett dataflöde i Power BI så fungerar det i princip på samma sätt som när du lägger till en tagg för resursen, med följande fördelar:
* **Anpassningsbar** – du kan skapa kategorier för olika nivåer av känsligt innehåll i organisationen, till exempel Personligt, Offentligt, Allmänt, Konfidentiellt och Mycket konfidentiellt.
* **Klartext** – eftersom etiketten är i klartext är det enkelt för användarna att förstå hur de ska hantera innehållet enligt riktlinjerna för känslighetsetiketter.
* **Beständiga** – När en känslighetsetikett har tillämpats på innehåll följer den med innehållet när det exporteras till Excel-, PowerPoint- och PDF-filer och påverkar hur principer tillämpas och verkställs.

Det innebär att känslighetsetiketten följer innehållet när det exporteras till Excel-, PowerPoint- och PDF-filer och påverkar hur principer tillämpas och verkställs.

Power BI-klientorganisationsadministratörer kan styra [exporten till Excel](service-admin-portal.md#export-to-excel) och [exporten till PowerPoint och PDF](service-admin-portal.md#export-reports-as-powerpoint-presentations-or-pdf-documents) från [Power BI-administratörsportalen](service-admin-portal.md).

## <a name="sensitivity-label-example"></a>Exempel på känslighetsetikett

Här är ett snabbt exempel på hur en känslighetsetikett i Power BI kan fungera.
1. I Power BI-tjänsten tillämpas känslighetsetiketten **Strikt konfidentiella** på en rapport.

   ![Känslighetsetiketter i listvyn](media/service-security-data-protection-overview/sensitivity-labels-overview-01.png)
   
1. När data exporteras till en Excel-fil från den här rapporten ärvs känslighetsetiketten och skyddet av den exporterade Excel-filen.

   ![Känslighetsetiketten följer med innehållet](media/service-security-data-protection-overview/sensitivity-labels-overview-02.png)

I Microsoft Office-program ser du känslighetsetiketten som en tagg i e-postmeddelandet eller dokumentet, ungefär som i bilden ovan. Du kan också associera en klassificering med innehållet (som en etikett), som finns kvar och följer med innehållet när det används och delas i hela Power BI. Du kan använda den här klassificeringen till att generera användningsrapporter och se aktivitetsdata för ditt känsliga innehåll. Med hjälp av den här informationen kan du avgöra om det behövs skyddsinställningar senare.

## <a name="requirements-for-using-sensitivity-labels-in-power-bi"></a>Krav för att använda känslighetsetiketter i Power BI

Innan du kan aktivera och använda känslighetsetiketter i Power BI måste följande förutsättningar vara uppfyllda:
* Känslighetsetiketterna måste vara definierade antingen i [säkerhetscentret för Microsoft 365](https://security.microsoft.com/) eller i [efterlevnadscentret för Microsoft 365](https://compliance.microsoft.com/).
* [Aktivera känslighetsetiketter](service-security-enable-data-sensitivity-labels.md) i Power BI.
* Se till att användarna har [rätt licenser](#licensing).
* Om du använder Microsoft Cloud App Security med Power BI ser du till att du har [rätt licens](service-security-using-microsoft-cloud-app-security-controls.md#cloud-app-security-licensing).

## <a name="protect-content-using-microsoft-cloud-app-security"></a>Skydda innehåll med Microsoft Cloud App Security

Du kan skydda innehåll i Power BI mot oönskade läckor eller intrång med hjälp av Microsoft Cloud App Security. När Microsoft Cloud App Security är installerat och konfigurerat kan administratörer övervaka användarnas åtkomst och aktiviteter, utföra riskanalyser i realtid och ställa in etikettspecifika kontroller.

Organisationer kan till exempel använda Microsoft Cloud App Security till att konfigurera en princip som förhindrar att användare laddar ned känsliga data från Power BI till ohanterade enheter. Med en sådan konfiguration kan användarna fortsätta att vara produktiva och ansluta till Power BI var de än befinner sig, samtidigt som Microsoft Cloud App Security hindrar skadliga användaråtgärder i realtid.

**Krav**

Innan Microsoft Cloud App Security kan användas för känslighetsetiketterna måste följande förutsättningar vara uppfyllda:
* Cloud App Security och Azure Information Protection [måste vara aktiverade för klientorganisationen](https://docs.microsoft.com/cloud-app-security/azip-integration).
* Appen [måste vara ansluten till Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

## <a name="licensing"></a>Licensiering

* För att använda och visa känslighetsetiketter från Microsoft Information Protection i Power BI behöver du en Premium P1- eller Premium P2-licens för Azure Information Protection. Du kan antingen köpa Microsoft Azure Information Protection separat eller via något av Microsofts licenspaket. Läs mer i [Prissättning för Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/).
* Det finns [licenskrav](https://docs.microsoft.com/microsoft-365/compliance/get-started-with-sensitivity-labels#subscription-and-licensing-requirements-for-sensitivity-labels) för att visa och använda etiketter i Office-appar.
* För att tillämpa etiketter på Power BI-innehåll måste användarna dessutom ha en Power BI Pro-licens utöver en av Azure Information Protection-licenserna som anges ovan.
* Du måste ha [nödvändiga licenser för Microsoft Cloud App Security](https://docs.microsoft.com/power-bi/admin/service-security-using-microsoft-cloud-app-security-controls#microsoft-cloud-app-security-licensing) om du ska använda det för att skydda Power BI-innehåll mot oönskade läckor och intrång.

## <a name="considerations-and-limitations"></a>Överväganden och begränsningar

I den här listan anges några begränsningar för känslighetsetiketter i Power BI:

**Allmänt**
* Du kan bara tillämpa känslighetsetiketter på instrumentpaneler, rapporter, datamängder och dataflöden. För närvarande är de inte tillgängliga för [sidnumrerade rapporter](../paginated-reports/report-builder-power-bi.md) och arbetsböcker.
* Känslighetsetiketter på Power BI-resurser visas i vyerna Arbetsytelista, Ursprung, Favoriter, Senaste och Appar. För närvarande visas inte etiketter i vyn ”Delat med mig”. Men även om du inte ser en etikett som tillämpats på en Power BI-tillgång så gäller den även efter export till Excel-, PowerPoint- eller PDF-format.
* Känslighetsetiketter stöds bara för klientorganisationer i det globala (offentliga) molnet. Känslighetsetiketter stöds inte för klientorganisationer i andra moln.
* Datakänslighetsetiketter stöds inte för mallappar. Känslighetsetiketter som anges av mallappens skapare tas bort när appen extraheras och installeras, och känslighetsetiketter som lagts till i artefakter i en installerad mallapp av appkonsumenten går förlorade (återställs till ingenting) när appen uppdateras.
* Power BI stöder inte känslighetsetiketter för skyddstyperna [Vidarebefordra inte](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions), [Användardefinierat](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels?view=o365-worldwide#let-users-assign-permissions) och [HYOK](https://docs.microsoft.com/azure/information-protection/configure-adrms-restrictions). Skyddstyperna Vidarebefordra inte och Användardefinierat är etiketter som definieras i [Microsoft 365 Security Center](https://security.microsoft.com/) eller [Microsoft 365 Compliance Center](https://compliance.microsoft.com/).
* De är inte avsedda att användas för att tillåta att användare tillämpar överordnade etiketter i Power BI. Om en överordnad etikett tillämpas på innehåll kommer en export av data från det innehållet till en fil (Excel, PowerPoint och PDF) att misslyckas. Mer information finns i avsnittet om [Underordnade etiketter (etikettgruppering)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels?view=o365-worldwide#sublabels-grouping-labels).

**Export**
* Etikett- och skyddskontroller tillämpas endast när data exporteras till Excel-, PowerPoint- och PDF-filer. Etikett och skydd tillämpas inte när data exporteras till CSV- eller PBIX-filer, Analysera i Excel eller andra exportsökvägar.
* När du tillämpar en känslighetsetikett och skydd på en exporterad fil, läggs ingen innehållsmärkning till för filen. Om etiketten har konfigurerats att använda innehållsmärkningar tillämpas de dock automatiskt av Azure Information Protection-klienten för enhetliga etiketter när filen öppnas i Office-skrivbordsappar. Innehållsmärkningarna tillämpas inte automatiskt när du använder inbyggd märkning för skrivbords-, mobil- eller webbappar. Mer information finns i avsnittet [om innehållsmärkning och kryptering med Office-appar](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps?view=o365-worldwide#when-office-apps-apply-content-marking-and-encryption).
* Användare som exporterar en fil från Power BI har behörighet att komma åt och redigera filen enligt inställningarna för känslighetsetiketten. Användaren som exporterar data får inte ägarbehörighet till filen.
* Exporten misslyckas om det inte går att tillämpa en etikett när data exporteras till en fil. Du kan kontrollera om exporten misslyckades på grund av att det inte gick att tillämpa etiketten. Klicka bara på rapportens eller instrumentpanelens namn i mitten av namnlisten och se om ”Det går inte att läsa in känslighetsetiketten” visas i listrutan som öppnas. Detta kan hända om den tillämpade etiketten har avpublicerats eller tagits bort av säkerhetsadministratören, eller på grund av ett tillfälligt systemfel.


## <a name="next-steps"></a>Nästa steg

I den här artikeln ges en översikt över dataskyddet i Power BI. De här artiklarna innehåller mer information om dataskydd i Power BI. 

* [Aktivera känslighetsetiketter för data i Power BI](service-security-enable-data-sensitivity-labels.md)
* [Använda känslighetsetiketter för data i Power BI](../collaborate-share/service-security-apply-data-sensitivity-labels.md)
* [Använda Microsoft Cloud App Security-kontroller i Power BI](service-security-using-microsoft-cloud-app-security-controls.md)
* [Dataskyddsmåttrapport](service-security-data-protection-metrics-report.md)