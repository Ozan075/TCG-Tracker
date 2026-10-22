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

## Installeren op GitHub Pages

De site bestaat uit één `index.html`; er is geen buildstap of pakketinstallatie nodig.

1. Zet `index.html` in je GitHub-repository. Je kunt deze `README.md` ernaast plaatsen.
2. Open in de repository **Settings → Pages**.
3. Kies bij **Source** voor **Deploy from a branch**.
4. Selecteer de branch met het bestand, bijvoorbeeld `main`, en de map **/ (root)**.
5. Klik op **Save** en wacht tot de publicatie gereed is.
6. Open de link die GitHub bij Pages toont.

Gebruik bij een bestaande installatie dezelfde branch en publicatiemap als voorheen. Vervang voor een update het bestaande `index.html` en commit de wijziging. De Supabase-database hoeft voor een gewone HTML-update niet opnieuw te worden aangemaakt.

De pagina gebruikt Supabase JavaScript via jsDelivr en een lettertype via Google Fonts. Voor online accounts en synchronisatie is een internetverbinding nodig.

## Supabase instellen

**Voor het al ingestelde project hoef je deze installatie niet opnieuw uit te voeren.** De onderstaande stappen zijn bedoeld voor een nieuwe installatie of een eigen kopie.

### 1. Project en browserkoppeling

1. Maak een Supabase-project aan.
2. Schakel de **Data API** in.
3. Laat automatisch blootstellen van nieuwe tabellen uit; het SQL-blok hieronder kent de benodigde rechten expliciet toe.
4. Automatische RLS mag aan blijven.
5. Open **Connect** of **Settings → API Keys** en kopieer de Project URL en Publishable key.
6. Zoek in `index.html` naar `CLOUD_URL` en `CLOUD_KEY` en vul de gegevens van jouw project in:

```js
const CLOUD_URL = 'https://JOUW-PROJECT.supabase.co';
const CLOUD_KEY = 'sb_publishable_JOUW_PUBLIEKE_SLEUTEL';
```

Een publishable key is bedoeld voor gebruik in de browser. Plaats geen databasewachtwoord, `sb_secret_`-sleutel of `service_role`-sleutel in de HTML of repository. De toegangsbeveiliging komt van Supabase Auth en de databasepolicies hieronder.

### 2. Database aanmaken

Open **SQL Editor → New query**, plak het hele blok hieronder en klik op **Run**. Voer dit eenmalig uit in een nieuw project. **Success. No rows returned** is de verwachte uitkomst.

```sql
-- Run this entire block once in Supabase > SQL Editor > New query > Run.
begin;
create table public.tcg_collections (
  user_id uuid primary key references auth.users(id) on delete cascade,
  cards jsonb not null default '[]'::jsonb,
  version bigint not null default 1 check (version > 0),
  updated_at timestamptz not null default now(),
  constraint tcg_cards_array check (jsonb_typeof(cards) = 'array')
);
alter table public.tcg_collections enable row level security;
revoke all on public.tcg_collections from anon, authenticated;
grant usage on schema public to authenticated;
grant select, insert, update on public.tcg_collections to authenticated;
create policy "Eigen collectie lezen" on public.tcg_collections
  for select to authenticated using ((select auth.uid()) = user_id);
create policy "Eigen collectie aanmaken" on public.tcg_collections
  for insert to authenticated with check ((select auth.uid()) = user_id);
create policy "Eigen collectie wijzigen" on public.tcg_collections
  for update to authenticated
  using ((select auth.uid()) = user_id)
  with check ((select auth.uid()) = user_id);
create function public.tcg_save_collection(p_cards jsonb, p_expected_version bigint)
returns setof public.tcg_collections
language plpgsql security invoker set search_path = '' as $$
begin
  if auth.uid() is null then raise exception 'Log eerst in'; end if;
  if p_cards is null or jsonb_typeof(p_cards) <> 'array' then
    raise exception 'Ongeldige collectie';
  end if;
  if p_expected_version = 0 then
    return query insert into public.tcg_collections(user_id, cards)
      values (auth.uid(), p_cards)
      on conflict (user_id) do nothing returning *;
  else
    return query update public.tcg_collections
      set cards = p_cards, version = version + 1, updated_at = now()
      where user_id = auth.uid() and version = p_expected_version
      returning *;
  end if;
  if not found then raise exception 'TCG_CONFLICT' using errcode = '40001'; end if;
end;
$$;
revoke all on function public.tcg_save_collection(jsonb,bigint) from public, anon;
grant execute on function public.tcg_save_collection(jsonb,bigint) to authenticated;
commit;
```

De tabel bewaart één collectie per gebruiker. Row Level Security beperkt lezen, toevoegen en wijzigen tot de eigenaar. De opslagfunctie controleert een versienummer, zodat een oudere collectie een nieuwere versie niet automatisch overschrijft.

### 3. Inloggen en e-mail

1. Zorg dat aanmelden met e-mailadres en wachtwoord is ingeschakeld in **Authentication**.
2. Open **Authentication → URL Configuration**.
3. Vul bij **Site URL** het volledige adres van de gepubliceerde tracker in, inclusief een eventuele repositorymap en afsluitende `/`.
4. Voeg hetzelfde adres bij **Redirect URLs** toe. Gebruik je ook het directe adres met `/index.html`, voeg dat dan eveneens toe.
5. Bewaar de instellingen en test aanmelden, e-mailbevestiging en wachtwoordherstel.

Supabase's standaard e-maildienst is bedoeld om te testen en stuurt alleen naar e-mailadressen van projectteamleden. Test eerst met het e-mailadres van je Supabase-account. Voor registratie en wachtwoordherstel door andere gebruikers moet je een eigen SMTP-dienst instellen. De instellingen staan bij **Authentication → SMTP Settings**; de precieze menunaam kan wijzigen. Laat e-mailbevestiging ingeschakeld als je geverifieerde e-mailadressen wilt gebruiken.

## Problemen oplossen

| Probleem | Controleer dit |
| --- | --- |
| De oude site blijft zichtbaar | Controleer de laatste Pages-publicatie en herlaad de pagina; op pc kan dat met Ctrl + Shift + R |
| De kaartenweergave is te breed op mobiel | Controleer of de nieuwste `index.html` is gepubliceerd en geladen |
| Je ziet alleen lokale kaarten | Controleer of je bent ingelogd; lokaal werken en online accounts hebben afzonderlijke collecties |
| Je collectie ontbreekt op een ander apparaat | Log in met hetzelfde account en controleer op het eerste apparaat of alles online is opgeslagen |
| Online opslag is nog niet ingesteld | Controleer of het volledige SQL-blok in het juiste Supabase-project is uitgevoerd |
| Een bevestigings- of herstelmail ontbreekt | Controleer spam, het gebruikte adres en de SMTP-instellingen |
| Een e-maillink opent een verkeerd adres | Controleer Site URL en Redirect URLs, inclusief de repositorymap |
| Er zijn twee versies | Lees de conflictmelding en maak een back-up voordat je een versie kiest |

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
