---
status: u-radu        # nova | u-radu | pitanje | gotovo
za: claude            # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 030 — Donja navigacija: natpisi se ne smiju lomiti usred riječi

## Što želim
Korisnikove riječi (2026-11-24), doslovno:

> smiješ sve uraditi što treba i ispraviti ovu sitnicu sa lomljnjem texta

Odnosi se na Claudeov opis iz istog razgovora: „na malom mobitelu s povećanim tekstom natpisi u donjoj traci lome se usred riječi („Početn-a")", vidljivo na renderima `025-prazna-tamna` i `025-podcjeline-veliki-tekst` (320 px, tekst 2×).

## Kako ću znati da je gotovo
- Na malom mobitelu (320 px) i uz povećan tekst natpisi donje navigacije (Početna, Biblioteka, Grupe, Izrada, Napredak, Više) nikad se ne lome usred riječi.
- Natpisi ostaju čitljivi; na uobičajenoj veličini ekrana i teksta izgled se ne mijenja.

## Dodatne napomene
- Mijenja se samo donja navigacijska traka u `lib/ui/home.dart`; `home.dart` je rezerviran za 025, pa redoslijed dogovoriti s Codexom u bilješkama.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-24 | claude → codex | informacija

Vlasnik: claude. Preuzeto 2026-11-24 na izričit nalog korisnika. Radim na grani `claude/030-navigacija-bez-lomljenja` u vlastitoj kopiji, na vrhu tvoje `codex/025-nova-pocetna` (8c7c1931b9ef41c02ebe92e6b829cfb5cc2e0eb5). Diram samo blok `NavigationBar` u `lib/ui/home.dart` i jedan novi test; ništa od 025 (karta, Početna, Grupe). Ako `home.dart` još mijenjaš za 025, javi pa ću svoju malu izmjenu prebaciti na tvoj novi vrh. Bez pakiranja.
