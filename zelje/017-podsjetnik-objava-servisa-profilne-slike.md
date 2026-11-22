---
status: pitanje       # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: nizak      # visok | srednji | nizak
---

# 017 — PODSJETNIK: objava servisa za profilnu sliku (odgođeno)

## Što želim
Korisnikove riječi (2026-11-22), doslovno:

> onda ćemo to uraditi kasnije. ostavi trag da ne zaboravimo

Ovo je trag za kasnije, **ne nalog za rad**. Odnosi se na želju 011: kod profilne slike (klijent i `community-web/node`) je napravljen i pregledan, ali **novi servis nije objavljen na produkcijskom serveru**. Dok se ne objavi, svi korisnici vide zadanu ikonu, a promjena slike je jasno nedostupna (capability `profileAvatar`). Sve ostalo u aplikaciji radi i može se testirati bez ove objave.

## Kako ću znati da je gotovo
- Korisnik je izričito odobrio objavu.
- Prije objave napravljena je i provjerena sigurnosna kopija produkcijske baze.
- Korisniku je korak po korak objašnjeno što će se napraviti, i on je to potvrdio prije same objave.
- Nakon objave: profilna slika radi na dva uređaja istog računa, a lekcije, napredak i sinkronizacija računa su netaknuti.

## Dodatne napomene
- **Ne pokretati bez korisnikovog izričitog odobrenja.** Status ostaje `pitanje`.
Čeka: korisnika — odobrenje i dogovor termina za produkcijsku objavu servisa profilne slike (želja 011).
- Prijedlog poruke koju korisnik može poslati Codexu kad bude spreman:
  > Odobravam objavu servisa za profilnu sliku (želja 011). Prije objave napravi i provjeri sigurnosnu kopiju produkcijske baze. Objasni mi korak po korak što ćeš napraviti i čekaj moju potvrdu prije same objave. Nakon objave provjeri sliku na dva uređaja i da su lekcije i napredak računa netaknuti.
- Povezano: želja 011 (grane `codex/011-profilna-slika-racuna`, `codex/011-normalizacija-rastera`, zapis `docs/reviews/2026-11-22-011-prihvacen-pregled.md` u `vladocilic/deez-neurons`).
- Podsjetnik iz pregleda: stvarna nadogradnja aplikacije na fizičkom mobitelu još nije provjerena (`AGENTS.md`, incident `UPGRADE_DATA_SAFETY` otvoren); prije instalacije korisnik treba imati sigurnosnu kopiju biblioteke.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
