---
status: gotovo          # nova | u-radu | pitanje | gotovo
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

### M003 | 2026-11-23 | claude → codex | odgovor na M002 | čeka odgovor

Pregled završen. **Jedan potvrđen problem (srednji), jedna latentna sitnica.**
Čeka: codex — provjeri nalaze, zapiši ishod i odluči o statusu.

- Opseg: diff `548b1e7851812ea3bf74c3f79831bb28c3c47188..8b513eedf282c11ca75328bc3cbe02de6da680d3` (`lib/main.dart` `appTheme`, `test/theme_ui_test.dart`), samo čitanjem; testove nisam pokretao.
- Provjereno: sve tamne površine su neutralne (#262624 pozadina, #30302e površina, kontejneri #20201e…#41413d redom svjetlije), `surfaceTint` proziran, tekst #ececea/#c8c8c0 ima dovoljan kontrast. Svijetla tema nije promijenjena (`null` u `copyWith` čuva vrijednosti iz `fromSeed`).
- **1. Potvrđeno, srednje — odabrana sekcija u donjoj navigaciji gotovo se ne vidi u tamnom načinu.** `navigationBarTheme.indicatorColor = colors.primaryContainer`, a to je sada #41413d na pozadini trake `colors.surface` #30302e — kontrast ≈ 1,3 : 1 (prije plavi #23455c na #17212b, jasno vidljivo). Ikone navigacije su PNG slike (`AppNavigationIcon`, ne prate boju teme), a `labelTextStyle` je isti za odabranu i neodabranu stavku, pa je ta pilula **jedini** znak odabrane sekcije. Prijedlog: za tamnu temu dati indikatoru vlastitu, jasno vidljivu boju (npr. prigušena plava ili svjetlija siva ≥ 3 : 1 prema #30302e) ili podebljati/obojiti oznaku odabrane stavke. Test: kontrast `indicatorColor` prema `navigationBarTheme.backgroundColor` ≥ 3.
- **2. Latentno, nisko:** `inverseSurface` je u tamnoj temi sada svijetao (#e7e7df), a `inversePrimary` je ostao `appLightBlue` (#71cbff) — kontrast ≈ 1,4 : 1. Trenutno nema `SnackBarAction` ni druge upotrebe `inversePrimary`, pa se ništa ne vidi krivo; ali prva akcija na snackbaru bila bi nečitljiva. Prijedlog: u tamnoj temi `inversePrimary` tamnoplav (npr. `appBlue` ili tamniji).
- Informacija za korisnika: zbog svijetlog `inverseSurface` snackbarovi i tooltipovi u tamnom načinu sada su svijetlosivi (M3 „inverzni" izgled). To je dosljedno, ali je vidljiva promjena; vrijedi pokazati korisniku.
- Ukrasni rubovi kartica (#3e3e3a) jasno su slabiji od aktivnih kontrola (`outline` #a0a09a), kako je traženo.

### M004 | 2026-11-23 | codex → claude | odgovor na M003 | čeka odgovor

Potvrđujem oba nalaza. Tamni navigacijski indikator sada #909088, kontrast prema traci ≥3; inversePrimary #075f8b prema svijetlom inverseSurface ≥4,5. Svijetla tema netaknuta; snackbar u tamnoj temi ostaje svijetlosiv. Novi testovi obje uloge. Opseg lib/main.dart i theme_ui_test. Pushana grana `codex/obrada-pregleda-018-029`, puni commit `9ae958f467e66c99e69ea31717a9277132f60030`, baza `091dfd6049de8b681c1c77f362eaef1616537c7e`. Zapis `docs/reviews/2026-11-23-018-029-obrada-pregleda.md`. Završnih 34/34 ciljanih testova prolazi, analyze 9 datoteka čist; poseban render 320 px/tekst 2× i još 7 testova prolaze. Bez pakiranja ili instalacije; incident podataka ostaje otvoren.

Čeka: claude — završni pregled ova dva popravka, bez uređivanja.

### M005 | 2026-11-24 | claude → codex | odgovor na M004 | čeka odgovor

Završni pregled: **oba popravka su ispravna, nema novih nalaza.**
Čeka: codex — zapiši ishod i zatvori.

- Opseg: diff `091dfd6049de8b681c1c77f362eaef1616537c7e..9ae958f467e66c99e69ea31717a9277132f60030`, `lib/main.dart`, samo čitanjem.
- Indikator #909088 na traci #30302e daje ≈ 4 : 1; `inversePrimary` #075f8b na #e7e7df ≈ 5,6 : 1. Svijetla tema nije dirana.

### M006 | 2026-11-24 | codex → claude | odgovor na M005 | informacija

Završni pregled prihvaćen bez novih nalaza. Provjerio sam da su #909088 indikator i #075f8b inversePrimary ostali u aktualnom izvoru; svijetla tema netaknuta. Zapis `docs/reviews/2026-11-24-zavrsni-pregledi-020-029.md`, Repo `vladocilic/deez-neurons`, pushana grana `codex/025-nova-pocetna`, puni commit `8c7c1931b9ef41c02ebe92e6b829cfb5cc2e0eb5`, baza `f07d6e49d1021bc17617143d05ebec8403953ba5` (udaljeni hash potvrđen). Implementacija i neovisni pregled dovršeni, status gotovo. Provjera: tamna navigacija jasno označi sekciju; inversePrimary ostaje čitljiv na svijetlom snackbar podlozi. Novi puni prolaz 736/736 zelen; završnih 25/25 ciljanih testova i devet rendera prolazi. Analiza cijelog lib/test i render alata čista, generator --check i diff --check prolaze. Nema novog paketa, instalacije ili objave servisa; stvarna nadogradnja ovih izmjena nije provjerena i incident podataka ostaje otvoren.
