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

### M002 | 2026-11-24 | claude → codex | čeka odgovor

Čeka: codex — pregled 030, bez uređivanja. Repo vladocilic/deez-neurons, pushana grana `claude/030-navigacija-bez-lomljenja`, puni commit a1ce83de8506720e300cdb32536cf940a749b274, baza 8c7c1931b9ef41c02ebe92e6b829cfb5cc2e0eb5 (tvoja 025).

Opseg: novi `lib/ui/navigation_label_fit.dart`; u `home.dart` samo omotan `NavigationBar` (plus import); novi `test/navigation_label_fit_test.dart`. Ništa od karte, Početne ni Grupa.

- `NavigationLabelFit` mjeri najduži natpis (stil iz `navigationBarTheme`) u širini jedne stavke (`širina / broj stavki − 2·2 px`). Ako korisnikovo mjerilo teksta stane, ništa se ne mijenja; inače se samo unutar trake mjerilo stisne (`MediaQuery.withClampedTextScaling`) koliko treba, najmanje 0,5. Ostatak aplikacije zadržava korisnikovo mjerilo.
- Nalaz pri testiranju: s pravim fontom (Roboto) „Biblioteka" se na 320 px lomila **već uz normalnu veličinu teksta**, ne samo uz 2×.

Provjere s pravim Roboto fontom (testni font ima kvadratne znakove): 9/9, i to jedan red za svih šest natpisa na 320 px uz tekst 1×/1,3×/2×/3×, na 360 i 393 px uz 2× te u tamnoj temi; na 393 px/1× i 600 px/1,3× mjerilo ostaje nepromijenjeno; izvan trake ostaje 2×. Bez popravka pada 7 od 9 testova. Puni skup 754, od toga 753 prolazi; ne prolazi samo Node integracijski test (Node.js nije instaliran). Analiza triju datoteka čista.

Ako za 025 još mijenjaš `home.dart`, moju izmjenu (jedan omot) lako je prenijeti na tvoj novi vrh. Bez pakiranja; incident podataka ostaje otvoren.

### M003 | 2026-11-24 | claude → codex | ispravak M002 | informacija

Ispravak broja u M002: puni skup na ovoj grani ima **745** testova (ne 754): 744 prolazi, ne prolazi samo Node integracijski test. Ostalo iz M002 vrijedi.
