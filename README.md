# claude-kok

Plugin för Claude Code: rätt modell och effort per uppgift.

- `scout` (Haiku, low): söker i koden och ger filer och rader. Ändrar inget.
- `reviewer` (Opus, high): granskar ändringarna före commit. Ändrar inget.
- `planner` (Fable, high): planerar större ändringar. Ändrar inget.
- `/claude-kok:modellval [uppgift]`: tabellen och ett förslag för uppgiften.

## Installera

```
/plugin marketplace add iGentlemanJackk/claude-kok
```

```
/plugin install claude-kok@claude-kok
```

Uppdatera: `/plugin marketplace update claude-kok`.

## Använda

- "Använd reviewer på mina ändringar"
- "Låt planner planera ..."
- `/claude-kok:modellval lägga till inloggning`
