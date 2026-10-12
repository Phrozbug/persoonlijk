---
type: dashboard
bijgewerkt: 2026-10-12
beheerd_door: Marc en HAL
cssclasses:
  - dashboard
---

# 🧭 Start

`= date(today)` · [[Kompas|🧭 Kompas]] · [[00-Dashboard-Exitplan|🎯 Exitplan]] · [[Projectplanning-Huis-Kopen|🏡 Platform]] · [[Styleguide|📐 Styleguide]]

> [!nav] Navigatie
> **Werk:** [[Notities.base#Werk|Alle werknotities]] · [[Projecten.base#Werk|Projecten werk]] · [[00-Dashboard-Exitplan|Exitplan]] · [[Projectplanning-Huis-Kopen|Platform]] · [[eenhuiskopeninfrankrijk-Site-Memory|Site-memory EHKIF]]
> **Privé:** [[Notities.base#Privé|Alle privénotities]] · [[Notities.base#Frankrijk|Frankrijk]] · [[Projecten.base#Privé en Frankrijk|Projecten privé]] · [[Huis-Klussen-en-Onderhoud|Huis Sainte-Marie]] · [[Vaste-Lasten-en-Abonnementen|Vaste lasten]]
> **Vault:** [[Inbox.base|Inbox]] · [[Notities.base#Favorieten|Favorieten]] · [[Notities.base#Recent|Recent]] · [[Opdrachten.base|CC-opdrachten]] · [[HAL-Lessons|HAL]]

---

## 📅 Vandaag

> [!multi-column]
>
>> [!today]+ ✅ Todoist: vandaag en over tijd
>> ```todoist
>> filter: "today | overdue"
>> autorefresh: 300
>> sorting:
>>   - date
>>   - priority
>> show:
>>   - due
>>   - project
>> ```
>
>> [!today]+ 📝 Vault-lijsten (Todo en Klussen)
>> ```tasks
>> not done
>> path includes 02-Lijsten
>> path does not include Boodschappen
>> hide backlink
>> hide task count
>> short mode
>> limit 12
>> ```

<!-- HAL:VANDAAG START -->
_Hier zet HAL twee keer per dag de agenda van de komende 14 dagen en de stand van Twenty (zie [[CC-Opdracht-Startpagina-Dagblok]]). Todoist hoeft niet meer in dit blok: dat staat hierboven live._
<!-- HAL:VANDAAG EIND -->

---

## 🔥 Deze maand

> [!tip] Oktober draait om één ding: de eerste factuur
> Eén partnervermelding van € 490 verkopen. Alles wat bouwen is, wacht tot november. Context en week-voor-week: [[Kompas#🔥 Deze maand: de eerste factuur]].

---

## 📁 Projecten

![[Projecten.base#Actief]]

> Nieuw project: maak een projectkaart met de template `Projectkaart` (QuickAdd of Templater). Bord met alle statussen: [[Projecten.base#Bord]].

---

## 💼 Werk en 🏠 Privé

> [!multi-column]
>
>> [!werk]+ 💼 Werk: laatst bewerkt
>> ```dataview
>> LIST
>> FROM "10-Be-Responsible" OR "30-Frankrijk/Huis-Kopen" OR "20-Persoonlijk/Projecten"
>> WHERE !contains(file.folder, "_archief") AND !contains(file.folder, "Claude outputs")
>> SORT file.mtime DESC
>> LIMIT 8
>> ```
>> Alles: [[Notities.base#Werk|Be-Responsible]] · [[Notities.base#Frankrijk|Platform en Agence Cible]]
>
>> [!prive]+ 🏠 Privé: laatst bewerkt
>> ```dataview
>> LIST
>> FROM "20-Persoonlijk" OR "30-Frankrijk/Sainte-Marie" OR "30-Frankrijk/Taal" OR "02-Lijsten"
>> WHERE !contains(file.folder, "20-Persoonlijk/Projecten")
>> SORT file.mtime DESC
>> LIMIT 8
>> ```
>> Alles: [[Notities.base#Privé|Privé]] · [[Notities.base#Frankrijk|Frankrijk]]

---

## 📥 Inbox

```dataviewjs
const p = dv.pages('"00-Inbox"');
const map = {};
for (const f of p) {
  const parts = f.file.folder.split("/");
  const sub = parts.length > 1 ? parts[1] : "Los";
  map[sub] = (map[sub] || 0) + 1;
}
const regels = Object.entries(map).sort((a,b) => b[1]-a[1]).map(([k,v]) => `${k} **${v}**`).join(" · ");
dv.paragraph(`${p.length} notities in de inbox: ${regels}`);
```

![[Inbox.base#Te verwerken]]

> Aanvoer per bron: [[Inbox.base#Apple-Notities|Apple-Notities]] · [[Inbox.base#Spraak|Spraak]] · [[Inbox.base#Bijlagen|Bijlagen]] · [[Inbox.base#Ouder dan 14 dagen|Ouder dan 14 dagen]]

---

## 🕐 Recent gewijzigd

![[Notities.base#Recent]]

---

## 🔍 Iets kwijt?

1. **Omnisearch** (`Cmd+Shift+O`, zie hotkeys): zoekt in de tekst van alle notities, ook in pdf's en OCR-bijlagen.
2. **Snelle switcher** (`Cmd+O`): als je de naam ongeveer weet.
3. **HAL vragen** via Signal of de spraak-app: "waar staat de notitie over …". HAL zoekt op betekenis, niet op woorden.
4. **Per gebied bladeren:** [[Notities.base#Per gebied]].

---

## 🛒 Boodschappen en lijsten

> [!multi-column]
>
>> [!prive]+ 🛒 Boodschappen
>> ```tasks
>> not done
>> path includes 02-Lijsten/Boodschappen
>> hide backlink
>> hide task count
>> short mode
>> ```
>
>> [!prive]+ 📂 Lijsten in de vault
>> ```dataview
>> LIST
>> FROM "02-Lijsten"
>> SORT file.name ASC
>> ```
