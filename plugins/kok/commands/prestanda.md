---
description: Leta efter prestandaproblem i ett WoW-addon (Lua) och föreslå rättelser, utan att ändra något förrän jag sagt ja
---
Gå igenom addonet (eller delen nedan) och leta efter det som gör spelet ryckigt eller belastar servern. Ändra
ingenting än: lista först varje fynd med fil:rad, vad som händer, hur ofta det körs och förslaget. Störst
effekt först. Säg om ett fynd är en gissning; mät gärna med `debugprofilestop()` runt koden i spelet.

Leta efter:

1. **Samma arbete i en loop** (som N+1 i en databas): spelets API (GetItemInfo, C_Container, GetProfessionInfo)
   eller en sökning i datan för varje rad, varje gång panelen ritas. Rättelse: hämta en gång och återanvänd,
   eller gör allt i en omgång.
2. **Sökningar genom hela listor** där en uppslagstabell räcker (som ett index): `for _, x in ipairs(lista) do
   if x.namn == namn` i kod som körs ofta. Rättelse: bygg en tabell `{ [namn] = x }` en gång. Bara där koden
   körs ofta eller listan är lång; inte överallt.
3. **Det som sällan ändras räknas om hela tiden**: översättningar, data från Data.lua, rader i en flik. Rättelse:
   spara resultatet (cache) och töm det när det ändras, t.ex. vid BAG_UPDATE_DELAYED, SKILL_LINES_CHANGED eller
   när en inställning ändras. Säg vad som tömmer varje cache; en cache som aldrig töms visar gammal data.
4. **Ramar som skapas i onödan**: CreateFrame för varje rad eller varje gång en flik visas, dolda flikar som ritas
   ändå. Rättelse: skapa ramar först när de behövs och återanvänd dem (en pool), rita bara det som syns. Sätt
   storleken innan texten, så att panelen inte hoppar när den ritas om.
5. **Knappar som väntar på svar** (Tavern: Connect, Skip, profiler): visa resultatet direkt när man klickar,
   skicka meddelandet i bakgrunden genom kön, och ångra med ett meddelande i spelet om inget svar kommer.
   Bara för sådant som går att ångra; inte där spelaren måste veta att det gick fram.

Och sådant som är särskilt för addons:

- **OnUpdate** som gör arbete varje bildruta: räkna tiden och kör högst några gånger i sekunden, eller använd
  C_Timer.After / C_Timer.NewTicker.
- **Händelser som kommer i skurar** (BAG_UPDATE, UNIT_AURA, COMBAT_LOG_EVENT_UNFILTERED): vänta en kort stund och
  gör jobbet en gång (C_Timer.After 0.2-0.5 s), eller använd den "DELAYED"-variant som finns.
- **Skräp i minnet**: nya tabeller och långa strängar (`..` i loopar) i kod som körs ofta. Återanvänd tabeller,
  använd table.concat.
- **Addon-meddelanden**: allt genom en kö med throttle, högst 255 byte per meddelande, inget i stridsläge som inte
  måste, och aldrig till spelare som inte har addonet.
- **Sparade variabler som växer utan gräns** (loggar, kända spelare, statistik): sätt ett tak eller rensa gammalt.
- **Arbete vid inloggning**: skjut upp det som inte behövs direkt (C_Timer.After efter PLAYER_ENTERING_WORLD).

Avsluta med en kort lista: vilka fynd du föreslår att rätta nu, och vilka tester som ska skrivas för dem.

Del att granska: $ARGUMENTS
