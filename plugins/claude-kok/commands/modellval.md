---
description: Visa vilken modell och effort som passar en uppgift, och föreslå den för det jag gör nu
---
Föreslå modell och effort för uppgiften nedan (eller det vi jobbar med nu om inget står). Svara kort med kommandona att köra.

| Uppgift | Modell | Effort |
|---|---|---|
| Planera en större ändring | Fable (`/model fable`) eller agenten `planner` | high |
| Bygga efter en plan | Sonnet (`/model sonnet`) | medium |
| Gränssnitt och utseende | Opus (`/model opus`) | high |
| Inloggning och betalningar | Opus | xhigh, och testa för hand |
| Söka i koden | agenten `scout` (Haiku) | low |
| Namnbyten och mallkod | Haiku (`/model haiku`) | low |
| Skriva tester | Sonnet | low |
| Bugg som ingen hittar | Opus | max, sedan Fable om det inte räcker |
| Säkerhetsgranskning | Fable | xhigh |
| Kodgranskning | agenten `reviewer` (Opus), aldrig samma chatt som skrev koden | high |

Effort sätts med `/effort <low|medium|high|xhigh|max>`. `/model opusplan` planerar med Opus och bygger med Sonnet.

Uppgift: $ARGUMENTS
