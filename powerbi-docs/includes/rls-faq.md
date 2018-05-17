## <a name="faq"></a>Vanliga frågor och svar
**Fråga:** Vad händer om jag tidigare har skapat roller och regler för en datauppsättning i Power BI-tjänsten? Fungerar de fortfarande om jag inte gör någonting?  
**Svar:** Nej. Visuella objekt kommer inte att återges korrekt. Du måste återskapa rollerna och reglerna i Power BI Desktop och sedan publicera till Power BI-tjänsten.

**Fråga:** Kan jag skapa rollerna för Analysis Services-datakällor?  
**Svar:** Du kan göra det om du har importerat datan till Power BI Desktop. Om du använder en live-anslutning kan du inte konfigurera RLS i Power BI-tjänsten. Detta definieras i Analysis Services-modellen lokalt.

**Fråga:** Kan jag använda RLS för att begränsa kolumner eller mått som är tillgängliga för mina användare?  
**Svar:** Nej. Om användarna har åtkomst till en viss datarad, kan de se alla datakolumner för den raden.

**Fråga:** Tillåter RLS att jag döljer detaljerade data men ger åtkomst till data som sammanfattas i visuella objekt?  
**Svar:** Nej, du kan skydda enskilda datarader men användarna kan alltid se information eller sammanfattade data.

