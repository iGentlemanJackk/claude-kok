# kok

Plugin för Claude Code (pluginet heter `kok`, repot `claude-kok`): rätt modell och effort per uppgift.

- `scout` (Haiku, low): söker i koden och ger filer och rader. Ändrar inget.
- `reviewer` (Opus, high): granskar ändringarna före commit. Ändrar inget.
- `planner` (Fable, high): planerar större ändringar. Ändrar inget.
- `/kok:modellval [uppgift]`: tabellen och ett förslag för uppgiften.

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
