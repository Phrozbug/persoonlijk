# Aanvulling Styleguide (voorstel 2026-10-12)

Plak dit onder de kop "Naamgeving" in `90-System/Styleguide.md`, of laat HAL het doen.

## Eigenschappen (frontmatter)

Elke nieuwe notitie krijgt minimaal `type` en `gebied`. Toegestane waarden:

- `type`: notitie · project · opdracht · verslag · naslag · lijst · dashboard · bijlage
- `gebied`: werk · prive · frankrijk · naslag · systeem
- `status` (alleen project en opdracht): actief · wacht · idee · klaar
- `project`: naam van de projectkaart, letterlijk
- `fav`: true zet een notitie in Favorieten op de startpagina

"Werk" is alles wat geld moet opleveren: Be-Responsible, het platform (EHKIF, FHH, Agence Cible) en het exitplan. "Prive" is gezin, gezondheid, vrienden, admin in Nederland. "Frankrijk" is het huis, de taal en de plaatsen.

## Projectkaarten

Eén notitie per lopend project met `type: project`, gemaakt met de template `90-System/Templates/Projectkaart.md`, in de projectmap zelf. De kaart bevat doel, stand, volgende stap, beslissingen. Acties met een datum staan in Todoist, niet op de kaart.

## Inbox is aanvoer

- `00-Inbox/Apple-Notities` en `00-Inbox/Voice` worden wekelijks door HAL verwerkt: inhoud naar de juiste map, bronnotitie naar `99-Archive/Verwerkt/`.
- Wat ouder is dan 30 dagen en niet is aangeraakt gaat zonder verwerking naar het archief.
- `00-Inbox/Bijlagen` (OCR) krijgt `type: bijlage` en telt niet mee in zoekweergaven.
- Losse notities in de inbox-root horen binnen 7 dagen een plek te hebben.

## Voor HAL

- Schrijf bij `maak_notitie` altijd `type` en `gebied` in de frontmatter.
- Nieuwe CC-opdracht: `type: opdracht`, `status: open`; bij afronding `status: klaar` of `mislukt`.
- Chatlogs blijven in `90-System/HAL/Gesprekken` en worden niet standaard meegenomen in zoekresultaten.
