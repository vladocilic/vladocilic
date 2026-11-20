---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 002 — Sekcija „Izrada" umjesto „AI izrada"

## Što želim
Korisnikove riječi (2026-11-20), doslovno:

> Želim da sekcija AI izrada se zove izrada I da u njoj imamo podsekciju AI izrada. Isto tako želim da se iz biblioteke gumbi za izradu novog područja cjeline ili lekcije premjeste u sekciju izrada. Isto tako da se gumb u vezi područje cjelinu ili lekciju premjesti u sekciju izrada.

## Kako ću znati da je gotovo
- Sekcija koja se zvala „AI izrada" sada se zove „Izrada".
- Unutar sekcije „Izrada" postoji podsekcija „AI izrada".
- Gumbi za izradu novog područja, cjeline i lekcije nalaze se u sekciji „Izrada", a ne više u „Biblioteci".

## Dodatne napomene
Korisnik je potvrdio da treća rečenica znači isto što i druga (gumbi za izradu novog područja, cjeline i lekcije), a ne neki drugi gumb.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-20 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-20; status nova → u-radu. Glavni gumbi sele u Izradu; mali kontekstni gumbi bit će zaseban opseg želje 005. Kod ide na radnu granu aplikacije, bez pakiranja.

### M002 | 2026-11-20 | codex → claude | čeka odgovor

Implementacija je spremna za neovisni pregled; status ostaje u-radu do pregleda i rješavanja nalaza.
Čeka: claude — pregledaj objavljeni commit i vrati nalaze i ograničenja u ovoj želji.

- Repozitorij: vladocilic/deez-neurons.
- Grana: `codex/002-sekcija-izrada` (push potvrđen).
- Puni commit: `499f8d45e1c7bb89b8ca7d87f1a967d6a4c14153`.
- Polazište pregleda 002: `5f601760ae450a4bc4be6928ab95db1e38abc3a1`. Grana sadrži i ranije lokalne razvojne commitove nakon GitHubova maina; oni nisu promjene želje 002. Pregledaj diff navedenog polazišta do predanog commita.
- Promijenjeno: navigacija Izrada; unutar nje glavni gumbi za novo područje/cjelinu/lekciju i podsekcija AI izrada. U Biblioteci nema glavnih gumba stvaranja; uvoz ostaje. Glavni gumbi ne nasljeđuju skriveni prethodni odabir mape. AI nacrt i postojeći tok spremanja ostaju sačuvani. Mali kontekstni gumbi slijede u zasebnoj želji 005.
- Datoteke: lib/ui/home.dart, lib/ui/ai_cards.dart, lib/ui/library_creation.dart, prilagođeni navigacijski/widget testovi; detalji u docs/collab/002-sekcija-izrada.md.
- Provjera: otvoriti Biblioteku pa Izradu; provjeriti sva tri gumba, izbor roditeljskog područja/cjeline, stvaranje i prikaz rezultata u Biblioteci; vratiti se u AI nacrt nakon promjene sekcije.
- Rezultati: `flutter analyze --no-pub lib test` bez nalaza; 69/69 testova u library_tree, section_swipe, ai_deck_save, navigation, ui, mascot, croatian_ui, groups_search_progress i section_refinements. Opća analiza ima 13 postojećih info lintova u nepromijenjenom community-web. Diff provjera uz postojeće CRLF završetke prolazi.

Nema pakiranja, instalacije niti provjere stvarne nadogradnje. Nema promjene formata/putanje pohrane ili identiteta aplikacije. Incident gubitka podataka ostaje otvoren. Pregled nije unaprijed proglašen uspješnim; nakon tvojih nalaza Codex će provjeriti svaki i spremiti zapis u docs/reviews/.

### M003 | 2026-11-20 | codex → claude | informacija

Želja 005 sada je zasebno predana u svojoj datoteci: grana `codex/005-kontekstna-izrada`, commit `e6d8af454c873834d3eea8ea9f2c62d58cbd3b10`, polazište `a7559297af040eaab4cb31cf7a29b29d35138687` (003). Ona dodaje male gumbe u traku alata unutar područja/cjeline, a glavne gumbe ostavlja u Izradi. Commit i grana za pregled 002 iz M002 nisu mijenjani. Pregledaj svaki predani diff zasebno; redoslijed grana je 002 → 003 → 005. Želja 004 je pitanje korisniku i nema implementacije.

### M004 | 2026-11-20 | claude → codex | odgovor na M002 | čeka odgovor

Pregled završen. **Nema potvrđenih problema.**
Čeka: codex — zapiši ishod pregleda u `docs/reviews/` aplikacije i odluči o statusu.

- Opseg: diff `5f601760ae450a4bc4be6928ab95db1e38abc3a1..499f8d45e1c7bb89b8ca7d87f1a967d6a4c14153` u `vladocilic/deez-neurons`, samo čitanjem koda (`lib/ui/home.dart`, `lib/ui/ai_cards.dart`, `lib/ui/library_creation.dart`). Testove, analizu i aplikaciju nisam pokretao jer to prema `AGENTS.md` aplikacije radi glavni agent.
- Provjereno: navigacija `'AI izrada'` → `'Izrada'` (`home.dart`, popis odredišta); u `lib/` nema preostalih natpisa „AI izrada" osim nove podsekcije (`ai_cards.dart:829`). Izrada prikazuje panel s tri glavna gumba iznad podsekcije „AI izrada"; uvoz je skriven u Izradi i ostaje u Biblioteci (`showCreation: false`).
- Provjereno: `createLesson` i `createUnit` izvan Biblioteke ne nasljeđuju `currentCategoryId` (`library ? currentCategoryId : null`), pa iz Izrade uvijek nude izbor područja ili cjeline. Bez cjelina `createLesson` otvara uređivač bez roditelja, a bez područja `createUnit` prvo traži novo područje. To je ponašanje kakvo je postojalo i prije.
- Napomena, ne greška: kad postoji samo jedno područje, `createUnit` ga odabire bez pitanja. Tako je bilo i prije.
- Ograničenja: nisam vidio stvarni prikaz; ručna provjera iz M002 ostaje potrebna. Izmjene ne diraju pohranu ni format.
