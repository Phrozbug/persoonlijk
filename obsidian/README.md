# Nieuwe startpagina voor Obsidian_Prive

Advies en kant-en-klare bestanden, 12 oktober 2026. Alles in de map `Obsidian_Prive/` hiernaast kopieer je één op één in je vault (Nextcloud, map `Obsidian_Prive`). Niets hiervan overschrijft een bestaand bestand, behalve `00-Start.md`; daarvoor staat hieronder een stap die je huidige pagina bewaart als Kompas.

## 1. Waarom je dingen niet terugvindt

Ik heb de vault doorgelicht (1.530 notities) en dit is het beeld:

| Wat ik zag | Gevolg |
|---|---|
| **479 notities in `00-Inbox`**, bijna een derde van de vault (282 Apple-Notities, 111 spraakopnames, 84 OCR-bijlagen). | Zoeken geeft vooral ruis; de inbox is een eindstation geworden, precies wat je eigen styleguide verbiedt. |
| **271 notities in `90-System/HAL`**, grotendeels chatlogs. | Elke zoekopdracht vindt eerst gesprekken over een onderwerp in plaats van de notitie zelf. |
| **`00-Start.md` is 27 kB proza**: strategie, mijlpalen, sporen, dagblok. | Het is een leesdocument, geen dashboard. Je scrolt, je navigeert niet. Alles wat Notion wél doet (tabel, filter, sorteren, klikken) ontbreekt. |
| **Geen vaste eigenschappen** op notities: `type:` komt in 40 varianten voor (werkmateriaal, cc-opdracht, raming, plan, enquete…), `status:` en `gebied:` bestaan niet. | Zonder eigenschappen kan geen enkel dashboard "alle actieve werkprojecten" laten zien. Dit is het echte verschil met Ultimate Brain: daar dwingt de database structuur af. |
| **Werk en privé lopen door de mappen heen**: Be-Responsible staat onder `10-`, maar het platform (je echte zakelijke focus) staat onder `30-Frankrijk/Huis-Kopen` en het exitplan onder `20-Persoonlijk/Projecten`. | "Wat me nu zakelijk bezighoudt" is in geen enkele map terug te vinden. |

Het probleem is dus niet Obsidian of Dataview, maar: geen structuurlaag bovenop de mappen, en een startpagina die leest als een memo.

## 2. Wat ik heb gekozen en waarom

**Blijf in Obsidian, bouw het Notion-gevoel met Bases.** Bases is sinds versie 1.9 de ingebouwde databaseweergave van Obsidian (tabel, kaarten, lijst, en sinds 1.14 kanban), staat in jouw vault al aan en heeft geen plugin nodig. Je krijgt precies wat Ultimate Brain biedt: sorteerbare kolommen, filters per weergave, eigenschappen inline bewerken, en weergaven die je in een notitie insluit. Dataview blijft voor de paar dingen die Bases niet kan (lijsten uit meerdere mappen tegelijk, de inbox-teller).

**Waarom niet overstappen naar Notion en Ultimate Brain** (de pagina die je stuurde):
- Je hele systeem hangt aan de vault: HAL schrijft erin via Nextcloud, Qdrant indexeert hem, n8n leest hem, de Signal-bridge en de dagnotities komen erin. Notion breekt dat allemaal; je zou HAL opnieuw moeten bouwen op de Notion-API.
- Ultimate Brain is een takensysteem met notities eraan. Jij hebt je taken bewust in Todoist en je CRM in Twenty gezet ("drie systemen, drie rollen"). Een tweede takendatabase in Notion is precies de dubbeling die je in het Kompas verbiedt.
- Notion is cloud-only en Amerikaans. Jij hebt juist Obsidian Sync opgezegd om alles op je eigen Gangkast en de VPS in Gravelines te houden.
- Wat je bij Ultimate Brain mooi vindt (Today, Inbox, Week, Projects, Favorites als tabbladen; notities met project, gebied en soort) is één op één na te bouwen met Bases. Dat is wat deze map doet.

**Werk en privé scheiden op basis van de werkelijkheid, niet alleen op mapnummer.** "Werk" is in de nieuwe weergaven: `10-Be-Responsible`, het platform (`30-Frankrijk/Huis-Kopen`) en het exitplan (`20-Persoonlijk/Projecten`). "Privé" is de rest van `20-Persoonlijk` plus `02-Lijsten`; "Frankrijk" is het huis, de taal en de plaatsen. Zet je later `gebied: werk` op een notitie, dan telt die mee, waar hij ook staat.

**Todoist live op de startpagina.** Het dagblok dat HAL moest verversen is op 12 oktober mislukt (tijdslimiet). Voor Todoist is dat niet meer nodig: de plugin *Todoist Sync* toont `today | overdue` live in een codeblok, met afvinken vanuit Obsidian. HAL houdt alleen nog de agenda en Twenty in het blok tussen de markeringen, dat werk is kleiner en robuuster.

## 3. Wat er in deze map zit

| Bestand | Wat het doet |
|---|---|
| `00-Start.md` | Nieuwe startpagina: navigatiebalk, Vandaag (Todoist + vault-lijsten), Deze maand, Projecten, Werk / Privé naast elkaar, Inbox, Recent, Zoektips, Boodschappen. Kort genoeg om op één scherm te overzien. |
| `90-System/Dashboards/Notities.base` | Alle inhoudelijke notities zonder ruis, met kolom Gebied (afgeleid uit de map). Weergaven: Recent, Werk, Privé, Frankrijk, Favorieten, Per gebied, Alles. |
| `90-System/Dashboards/Projecten.base` | Eén regel per project (`type: project`). Weergaven: Actief (met volgende stap en deadline), Bord (kanban op status), Werk, Privé en Frankrijk, Alles. |
| `90-System/Dashboards/Inbox.base` | Inbox gesplitst op bron: Te verwerken (losse notities), Apple-Notities, Spraak, Bijlagen, Ouder dan 14 dagen. |
| `90-System/Dashboards/Opdrachten.base` | Alle CC-opdrachten op status, zodat je ziet wat open staat en wat stil ligt. |
| `90-System/Templates/Projectkaart.md` | Templater-sjabloon: één pagina per project met gebied, status, volgende stap, deadline en een lijst van alle notities die naar dat project verwijzen. |
| `90-System/Templates/Notitie.md` | Templater-sjabloon voor een gewone notitie met gebied en project. |
| `.obsidian/snippets/dashboard-extra.css` | Opmaak voor de navigatiebalk, de kaarten en de ingesloten Bases. Werkt samen met je bestaande `mcl-dashboard.css`. |

## 4. Installeren (een kwartier)

1. **Bewaar je huidige startpagina.** Hernoem in Obsidian `00-Start.md` naar `90-System/Dashboards/Kompas.md` (rechtermuisknop, Hernoemen; Obsidian werkt de links bij). Alle strategie, mijlpalen en sporen blijven zo bestaan en de nieuwe pagina linkt ernaar.
2. **Kopieer de map `Obsidian_Prive/` uit deze repo** over je vault heen (via Finder in de Nextcloud-map, of upload in Nextcloud). Dat zet `00-Start.md`, de vier `.base`-bestanden, de twee templates en het CSS-snippet op hun plek.
3. **Zet het snippet aan:** Instellingen, Uiterlijk, CSS-snippets, `dashboard-extra` inschakelen.
4. **Installeer de plugin Todoist Sync** (community plugins, zoek op "Todoist Sync", maker jamiebrynes7). Plak je Todoist API-token (Todoist, Instellingen, Integraties, Developer). Het blok op de startpagina werkt dan meteen. Zonder deze plugin zie je op die plek alleen het codeblok; de rest van de pagina werkt gewoon.
5. **Controleer je Obsidian-versie** (Instellingen, Algemeen). Tabel en lijst werken vanaf 1.10, het kanbanbord in `Projecten.base` vanaf 1.14. Oudere versie: update, dat is gratis.
6. **Templater:** Instellingen, Templater, Template folder location op `90-System/Templates` (staat er waarschijnlijk al). Maak in QuickAdd twee keuzes: "Nieuw project" (Template, `Projectkaart.md`, map naar keuze) en "Nieuwe notitie" (Template, `Notitie.md`).
7. **Hotkey voor Omnisearch:** Instellingen, Sneltoetsen, zoek "Omnisearch: Vault search", zet `Cmd+Shift+O`. Omnisearch zoekt in de tekst, inclusief pdf's en OCR-bijlagen, en is al geïnstalleerd.

De Homepage-plugin opent `00-Start` al bij het starten; daar hoef je niets aan te doen.

## 5. Maak zes projectkaarten (het echte werk, een half uur)

Het dashboard toont pas projecten als er notities zijn met `type: project`. Maak met de template `Projectkaart` een kaart per lopend project en zet de kaart in de projectmap:

| Projectkaart | Map | Gebied | Volgende stap (nu) |
|---|---|---|---|
| Platform EHKIF en de groep | `30-Frankrijk/Huis-Kopen/` | werk | Eerste partnervermelding van € 490 verkopen |
| French House Hunt | `30-Frankrijk/Huis-Kopen/` | werk | Opvolging golf 1, 13 oktober |
| Agence Cible site | `30-Frankrijk/Huis-Kopen/Website/` | werk | htaccess-blok, Turnstile, KvK-nummer |
| Exitplan | `20-Persoonlijk/Projecten/Exitplan-Agence-Cible/` | werk | Oude Todoist-mijlpalen herschrijven |
| HAL en de Gangkast | `90-System/HAL/` | systeem | Tweede reservetest met HAL |
| Huis Sainte-Marie | `30-Frankrijk/Sainte-Marie/` | frankrijk | Airco-offerte Adrien opvragen |

`00-Dashboard-Exitplan.md` kun je direct ombouwen: zet `type: project`, `status: actief` en `gebied: werk` in de frontmatter en hij verschijnt in het bord.

## 6. De inbox terugbrengen naar nul (met HAL)

Dit is de helft van de oplossing en het hoort bij HAL, niet bij jou. Voorstel voor drie regels in `90-System/Styleguide.md` (staan ook klaar in `Styleguide-aanvulling.md`):

1. **Apple-Notities en spraakopnames zijn aanvoer, geen notities.** HAL verwerkt ze wekelijks: inhoud naar de juiste map volgens de kaart in de styleguide, de bronnotitie naar `99-Archive/Verwerkt/`. Wat ouder is dan 30 dagen en nooit is aangeraakt gaat zonder verwerking naar het archief.
2. **OCR-bijlagen** krijgen `type: bijlage` en worden uit alle zoekweergaven gefilterd (dat doet `Notities.base` al).
3. **Chatlogs** (`90-System/HAL/Gesprekken`) worden niet meer door Qdrant geïndexeerd in de standaardzoekopdracht; de `soort: gesprek`-filter bestaat al, maak hem de default in de HAL-prompt.

Eenmalig: de 282 Apple-Notities in één CC-opdracht laten sorteren door HAL (per notitie: bestemming volgens de styleguide, of archief). Dat is een halve dag rekentijd voor HAL en nul voor jou.

## 7. Eigenschappen: de minimale afspraak

Zodat HAL en jij hetzelfde schrijven (toevoegen aan de styleguide):

```yaml
type: notitie | project | opdracht | verslag | naslag | lijst | dashboard | bijlage
gebied: werk | prive | frankrijk | naslag | systeem
status: actief | wacht | idee | klaar        # alleen bij project en opdracht
project: Naam van de projectkaart              # vrije tekst, gelijk aan de kaartnaam
fav: true                                      # zet een notitie in Favorieten
```

Bestaande notities hoef je niet te hertaggen: de weergaven leiden het gebied af uit de map. Eigenschappen zijn voor nieuwe notities en voor de uitzonderingen (werknotitie in een privémap).

## 8. Wat ik niet heb gedaan en waarom

- **Geen Notion-export of migratie.** Zie hoofdstuk 2.
- **Geen tweede takensysteem in de vault.** Todoist blijft de enige plek voor acties met een datum; de vault-lijsten (`02-Lijsten`) blijven voor afvinklijsten zonder datum.
- **Geen agenda-plugin.** Google Agenda in Obsidian vraagt een OAuth-koppeling per apparaat; het HAL-blok (agenda en Twenty) is daarvoor de betere route en bestaat al als CC-opdracht.
- **Geen nieuwe CSS-thema's of plugin-stapels.** Alles draait op wat er al in je vault staat plus één plugin (Todoist Sync).

## Bronnen

- Obsidian Bases: [overzicht](https://obsidian.md/help/bases), [syntax](https://obsidian.md/help/bases/syntax), [weergaven en insluiten](https://obsidian.md/help/bases/views), [functies](https://obsidian.md/help/bases/functions)
- Obsidian changelog: [1.11](https://obsidian.md/changelog/2026-01-12-desktop-v1.11.4/), [1.12](https://obsidian.md/changelog/2026-02-10-desktop-v1.12.0/), [roadmap](https://obsidian.md/roadmap/)
- Todoist Sync plugin: [query blocks](https://jamiebrynes7.github.io/obsidian-todoist-plugin/docs/query-blocks), [repository](https://github.com/jamiebrynes7/obsidian-todoist-plugin)
- Ultimate Brain for Notion: [productpagina](https://thomasjfrank.com/brain), [wat is nieuw in 3.0](https://thomasjfrank.com/?p=9522)
- Dashboards in Obsidian: [QueryDash](https://community.obsidian.md/plugins/querydash), [TaskNotes](https://community.obsidian.md/plugins/tasknotes), [Bases Timeline](https://community.obsidian.md/plugins/bases-timeline)
