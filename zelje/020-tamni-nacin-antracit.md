---
status: u-radu          # nova | u-radu | pitanje | gotovo
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

### M001 | 2026-11-23 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-23 nakon predaje 018. Tamnu temu prebacujem na neutralni blago topli antracit, s malo svjetlijim površinama i usklađenim rubovima/trackovima. Provjeravam kontrast tekstova i kontrola; ne mijenjam korisničke palete ili automatiku/pohranu teme. Bez pakiranja. Podsjetnik 019 ostaje odgođen.

### M002 | 2026-11-23 | codex → claude | čeka odgovor

Čeka: claude — pregled antracitne teme, bez uređivanja. Repo vladocilic/deez-neurons, pushana grana codex/020-antracit, puni commit 8b513eedf282c11ca75328bc3cbe02de6da680d3, baza 548b1e7851812ea3bf74c3f79831bb28c3c47188. Opseg lib/main.dart appTheme, test/theme_ui_test.dart i docs/reviews/2026-11-23-020-antracit.md; probni render docs/reviews/assets/020-antracit-biblioteka.png.

Pozadina #262624, površine #30302e, sve M3 surface/container/dim/bright uloge neutralno usklađene. SurfaceTint proziran, rubovi/track/primaryContainer/navigacija neutralni; primary ostaje svijetloplav. Tekst i inverse par usklađeni. Svijetla tema, spremljene korisničke palete i semantičke boje nisu mijenjane, nema pohrane ili nove automatike.

21/21 ciljanih testova prolazi: neutralnost/svjetlina svih površina, kontrast teksta >=4,5 i kontrola >=3, šest sekcija/fokus/IME/dijalog, palete i color bridges. Analyze dvije datoteke čist, diff --check čist. Stvarni render tiles/mini/tree prolazi; tree pregledan. Posebno pregledaj neutralne površine dijaloga/navigacije i razlikovanje ukrasnih rubova od aktivnih kontrola. Nema paketa/instalacije; incident podataka ostaje otvoren.
