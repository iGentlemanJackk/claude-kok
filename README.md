# kok

Plugin för Claude Code (pluginet heter `kok`, repot `claude-kok`): rätt modell och effort per uppgift.

- `scout` (Haiku, low): söker i koden och ger filer och rader. Ändrar inget.
- `reviewer` (Opus, high): granskar ändringarna före commit. Ändrar inget.
- `planner` (Fable, high): planerar större ändringar. Ändrar inget.
- `/kok:modellval [uppgift]`: tabellen och ett förslag för uppgiften.
- `/kok:prestanda [del]`: letar efter prestandaproblem i ett WoW-addon (loopar, uppslag, cache, ramar, OnUpdate,
  händelser, addon-meddelanden, sparade variabler). Listar först, ändrar inget förrän du sagt ja.
- `/kok:webbprestanda [del]`: samma för en webbapp (N+1-frågor, index, cache, bilder, optimistisk UI).

## Installera

```
/plugin marketplace add iGentlemanJackk/claude-kok
```

```
/plugin install kok@kok
```

Uppdatera: `/plugin marketplace update kok`.

## Använda

- "Använd reviewer på mina ändringar"
- "Låt planner planera ..."
- `/kok:modellval lägga till inloggning`
- `/kok:prestanda Panel.lua`
- `/kok:webbprestanda startsidan`
