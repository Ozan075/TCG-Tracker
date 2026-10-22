# TCG Tracker

Een Nederlandstalige kaartentracker voor je TCG-collectie. Houd inkoop, gradingkosten en slabwaarde bij en zie automatisch je investering, potentiële winst en rendement.

De tracker werkt op telefoon en pc. De website draait op **GitHub Pages**; **Supabase** verzorgt accounts en online opslag per gebruiker. Zonder inloggen kun je de tracker lokaal gebruiken.

## Functies

- Dashboard met totale investering, potentiële winst, rendement en beste kaart.
- Overzichten per gradingstatus en grade, plus een top 5 winst en verlies.
- Kaarten toevoegen, bewerken en verwijderen; verwijderen kan direct ongedaan worden gemaakt.
- Een tabel op pc en afzonderlijke invoerblokken op mobiel.
- Zoeken op kaartnaam, grade en notities.
- Filteren op gradingstatus, grade of ontbrekende slabwaarde.
- Sorteren op kaartgegevens, bedragen en berekende resultaten.
- Een grade-keuzemenu met BGS-, PSA- en CGC-opties, bestaande eigen grades en de mogelijkheid een andere grade toe te voegen.
- Registreren, inloggen, uitloggen en een wachtwoord herstellen.
- Persoonlijke online collecties, met controle op gelijktijdige wijzigingen.
- Bestaande lokale kaarten op verzoek aan je account toevoegen.
- CSV-export, CSV-import en volledige JSON-back-ups.

## Kaartgegevens en berekeningen

Iedere rij of ieder mobiel invoerblok stelt één kaart voor.

| Veld | Betekenis |
| --- | --- |
| Kaartnaam | Naam en eventueel kaartnummer of set |
| Inkoopprijs incl. | Totale aankoopkosten die je zelf invult, bijvoorbeeld inclusief verzending |
| Gradingkosten | Kosten voor het laten graden |
| Kaart grade | Bijvoorbeeld BGS 10, PSA 10 of een eigen grade |
| Slabwaarde | De door jou geschatte actuele waarde |
| Gradingstatus | Niet ingestuurd, Voorbereiden, Verzonden, In behandeling of Terugontvangen |
| Notities | Aanvullende informatie over de kaart |

De tracker berekent:

```text
Totale kosten = inkoopprijs + gradingkosten
Potentiële winst = slabwaarde − totale kosten
Rendement = potentiële winst ÷ totale kosten × 100%
```

Een lege slabwaarde betekent **onbekend**, niet € 0. Zo'n kaart telt wel mee in de totale investering, maar niet in winst en rendement. Een expliciet ingevulde waarde van € 0 telt wel mee. Rendement wordt niet berekend als de totale kosten € 0 zijn.

Het dashboard telt kaarten met een ingevulde naam. De weergegeven winst is potentiële winst op basis van de ingevulde waarde; de tracker heeft geen aparte verkoop- of gerealiseerde-winstregistratie. Marktprijzen worden niet automatisch opgehaald.

## Gebruik

1. Open de gepubliceerde tracker.
2. Kies **Inloggen / registreren** voor een persoonlijke online collectie, of werk zonder account lokaal.
3. Ga naar **Kaarten** en kies **Nieuwe kaart**.
4. Vul de kaartgegevens en bedragen in. Je mag Nederlandse bedragen gebruiken, zoals `12,50` of `1.234,56`.
5. Kies een grade en gradingstatus. Kosten, winst en rendement worden automatisch bijgewerkt.
6. Controleer de opslagmelding. **Online opgeslagen** betekent dat de server de wijziging heeft bevestigd.

Log op een ander apparaat met hetzelfde account in om je online collectie te laden. Gebruik **Vernieuwen** om wijzigingen van een ander apparaat op te halen. De tracker controleert ook periodiek en wanneer je terugkeert naar het tabblad.

### Bestaande lokale kaarten overzetten

1. Maak eerst een JSON-back-up via **Back-up, import en collectiebeheer**.
2. Log in op het apparaat en in de browser waar je lokale kaarten staan.
3. Kies **Lokale kaarten overzetten** en controleer het getoonde account.
4. Bevestig en wacht op **Online opgeslagen**.

De overdracht gebeurt alleen op jouw verzoek. Kaarten met een ID dat al in je online collectie staat, worden niet nogmaals toegevoegd. Je oorspronkelijke lokale collectie blijft op dat apparaat bewaard.

### Back-ups en import

Open onderaan **Back-up, import en collectiebeheer**.

| Actie | Wat gebeurt er? |
| --- | --- |
| Back-up (JSON) | Bewaart alle rijen en hun gegevens, ook rijen zonder kaartnaam |
| Exporteer CSV | Exporteert kaarten met een naam, inclusief berekende kosten en winst |
| Importeer CSV | Voegt kaarten aan de huidige collectie toe na bevestiging |
| Importeer JSON-back-up | Vervangt de huidige collectie na bevestiging; de actie kan direct ongedaan worden gemaakt |
| Voorbeeldkaarten laden | Voegt vijf voorbeeldkaarten aan de huidige collectie toe |
| Alles wissen | Leegt de huidige collectie na bevestiging; de actie kan direct ongedaan worden gemaakt |

Voor CSV-import kun je het beste een CSV-export van de tracker als voorbeeld gebruiken. `Kaartnaam` moet als kolom aanwezig zijn. Berekende kolommen worden opnieuw uit de ingevoerde bedragen berekend.

### Geen verbinding of verschillende versies

Bij wijzigingen in een al geladen online collectie bewaart de tracker een lokaal concept voor dat account. Als de verbinding terugkomt, probeert hij opnieuw te synchroniseren. Sluit de pagina bij voorkeur pas als **Online opgeslagen** verschijnt.

Als de online collectie ondertussen is veranderd, verschijnt een melding met twee versies. Je kunt jouw versie downloaden als back-up, de online versie laden of jouw versie online opslaan. Vóór het vervangen wordt een back-up van de te vervangen versie gedownload. Controleer dat de download is gelukt.

Lokale gegevens en concepten zijn gekoppeld aan een browser en apparaat. Bewaar daarom ook losse JSON-back-ups. Het wissen van browsergegevens verwijdert de lokale opslag.



## Techniek

- HTML, CSS en JavaScript in één bestand.
- GitHub Pages voor de statische website.
- Supabase Auth voor accounts en sessies.
- Supabase Postgres met RLS voor persoonlijke collecties.
- `localStorage` voor lokale collecties en accountgebonden concepten.
- CSV en JSON voor overdracht en back-ups.

## Documentatie

- [GitHub Pages: publicatiebron instellen](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
- [Supabase API-sleutels](https://supabase.com/docs/guides/getting-started/api-keys)
- [Supabase Row Level Security](https://supabase.com/docs/guides/database/postgres/row-level-security)
- [Supabase redirect-URL's](https://supabase.com/docs/guides/auth/redirect-urls)
- [Supabase e-mail en SMTP](https://supabase.com/docs/guides/auth/auth-smtp)
