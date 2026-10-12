---
type: project
gebied: <% tp.system.suggester(["werk", "prive", "frankrijk", "systeem"], ["werk", "prive", "frankrijk", "systeem"]) %>
status: actief
volgende_stap: 
deadline: 
project: <% tp.file.title %>
fav: false
aangemaakt: <% tp.date.now("YYYY-MM-DD") %>
---

# <% tp.file.title %>

> **Doel in één zin:** 
> **Klaar als:** 

## Waar het nu staat

- 

## Volgende stap

Zie `volgende_stap` hierboven. Acties met een datum staan in Todoist (project *<% tp.file.title %>*), niet hier.

## Beslissingen

| Datum | Beslissing | Waarom |
|---|---|---|
| <% tp.date.now("YYYY-MM-DD") %> | | |

## Notities bij dit project

```dataview
LIST
WHERE project = this.project AND file.name != this.file.name
SORT file.mtime DESC
```
