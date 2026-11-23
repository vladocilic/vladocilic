---
status: nova          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 020 — Tamni način: antracit (tamnosiva) pozadina umjesto gotovo crne

## Što želim
Korisnikove riječi (2026-11-23), doslovno:

> Sljedeća želja je da u noćnom radu ne bude skroz crna boja u pozadini, nego neka bude kao ova tvoja, nekakva antracit, tamno siva.

## Kako ću znati da je gotovo
- U tamnom načinu pozadina aplikacije nije gotovo crna, nego antracit, tamnosiva.
- Površine (kartice, trake, dijalozi, donja navigacija) su u istom antracit tonu, malo svjetlije od pozadine, da se razlikuju.
- Tekst, ikonice i boje korisnika (palete, kalendar, kuglice/lige, karta neurona) ostaju čitljivi i prepoznatljivi.

## Dodatne napomene
- Nastavak želje 012. Sada je `scaffoldBackgroundColor` u tamnoj temi `#101820`, a `surface` `#17212b` (`lib/main.dart`, `appTheme`); oba su plavkasto-crna.
- „Kao ova tvoja" znači tamni izgled Claude aplikacije: neutralna, blago topla tamnosiva. Okvirni prijedlog (Codex smije fino podesiti radi kontrasta): pozadina ≈ `#262624`, površine ≈ `#30302e`, rubovi ≈ `#3e3e3a`. Izbjegavati plavkasti ton.
- Provjeriti kontrast teksta (≥ 4,5 : 1) i postojeće tamne boje iz 012 (npr. `primaryContainer` `#23455c`, `linearTrackColor` `#34485a`, rub kartica `#526578`) da se slažu s antracitom.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
