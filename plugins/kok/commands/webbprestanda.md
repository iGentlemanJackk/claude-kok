---
description: Leta efter prestandaproblem i en webbapp (databas, cache, bilder, optimistisk UI) och föreslå rättelser, utan att ändra något förrän jag sagt ja
---
Gå igenom webbappen (eller delen nedan). Ändra ingenting än: lista först varje fynd med fil:rad, vad som händer
och förslaget, störst effekt först. Mät där det går (frågornas tid, EXPLAIN, Lighthouse) och säg när ett fynd är
en gissning.

1. **N+1-frågor**: en databasfråga per rad i en loop (en lista med 50 inlägg och en fråga per inläggs författare).
   Rättelse: eager loading (t.ex. `include`/`select_related`/`with`) eller en fråga för alla på en gång. Visa
   varje ändring.
2. **Index**: inte på varje kolumn. Index gör skrivningar långsammare och tar plats. Hitta frågorna som är långsamma
   eller körs ofta (filter, sökning, sortering, främmande nycklar), kör EXPLAIN, och föreslå index bara för dem,
   gärna sammansatta i rätt ordning. Lista indexen och varför innan något skapas.
3. **Cache** för data som sällan ändras (inställningar, menyer, listor): visa var cachen töms när datan ändras.
   Säg vad som händer om den inte töms (gammal data) och hur länge den får leva. Ingen cache för data per
   användare utan att nyckeln innehåller användaren.
4. **Bilder**: fast bredd och höjd (eller aspect-ratio) på alla bilder, så att sidan inte hoppar. Lazy-load
   (`loading="lazy"`) bara för bilder under det som syns först; den största bilden högst upp laddas direkt
   (gärna `fetchpriority="high"`), annars blir sidan långsammare.
5. **Optimistisk UI** för gillningar, av/på-knappar och små sparningar som går att ångra: uppdatera direkt, skicka
   i bakgrunden, ångra med ett meddelande om det misslyckas. Inte för betalningar, inloggning eller annat där
   användaren måste veta att det verkligen sparades: där visas ett tydligt "sparar..." och svaret.

Avsluta med vilka fynd du föreslår att rätta nu och hur vi testar att det blev snabbare.

Del att granska: $ARGUMENTS
