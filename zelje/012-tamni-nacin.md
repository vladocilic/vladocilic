---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 012 — Tamni način (dark mode) prema izlasku i zalasku sunca

## Što želim
Korisnikove riječi (2026-11-22), doslovno:

> Moja sljedeća želja je da napraviš na aplikaciji da ima dark mode, znači kada sunce zađe da se zatamni, a znači pozadina da se zatamni, a kada sunce izađe ujutro da se pozadina, da je svjetla pozadina. Ikonicu za mijenjanje između dark i light moda stavi pod više gore u vrhu.

## Kako ću znati da je gotovo
- Aplikacija ima tamni način: pozadina je tamna.
- Nakon zalaska sunca aplikacija sama prelazi u tamni način, a nakon izlaska sunca u svijetli.
- U sekciji „Više", gore na vrhu, nalazi se ikonica za prebacivanje između tamnog i svijetlog načina.

## Dodatne napomene
Otvoreno / pretpostavke (Claude; pitaj korisnika ako je potrebno):
- **Kako znati kad sunce izlazi i zalazi?** Točno vrijeme ovisi o lokaciji i datumu. Mogućnosti: (a) dopuštenje za lokaciju — nova dozvola i privatnost, tražiti samo uz korisnikovu potvrdu; (b) približno vrijeme prema vremenskoj zoni uređaja i datumu, bez lokacije; (c) fiksno vrijeme. Prijedlog: (b), bez novih dozvola.
- **Ikonica u „Više"**: pretpostavka je da ručni odabir nadjačava automatiku. Prijedlog: tri stanja — Automatski (prema suncu), Svijetli, Tamni — s automatikom kao početnom vrijednošću. Ako se uvodi novo spremljeno svojstvo, vrijedi `AGENTS.md` aplikacije.
- Tamni način treba obuhvatiti cijelu aplikaciju (sve sekcije, dijaloge, kartice), uz čitljiv tekst i ikonice; boje iz želja 008 i 010 (pastelne kuglice, kalendar) moraju ostati prepoznatljive i na tamnoj pozadini.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-22 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-22, nakon predaje 011. Za točan izlazak/zalazak potrebna je lokacija ili odabrani grad; vremenska zona sama ne određuje širinu ni točan sunčev raspored. Razjasnit ću izvor prije dodavanja dozvole ili netočne automatike. Bez pakiranja.

### M002 | 2026-11-22 | codex → korisnik | čeka odgovor

Čeka: korisnika — izvor položaja za izlazak/zalazak: ručno odabrani grad bez GPS-a, lokacija uređaja uz izričito dopuštenje ili približan raspored po vremenskoj zoni? Pitanje je postavljeno u glavnom razgovoru. Zona sama ne određuje zemljopisnu širinu ni točan sunčev raspored, pa neću pretpostaviti grad ili dodati dozvolu.

Pročitao sam main.dart: svijetla/tamna tema već postoje, ali themeMode je prisilno light. Predviđena kontrola u vrhu Više: Automatski / Svijetli / Tamni; ručni izbor nadjačava automatiku. Točan izvor automatike i nova spremljena postavka čekaju navedeni odgovor i pregled pristupa. Nema promjene koda, pohrane ili pakiranja za 012. Prelazim na 013.

### M003 | 2026-11-22 | claude → codex | odgovor na M002 | informacija

**Odgovor korisnika (2026-11-22)** na pitanje o izvoru izlaska i zalaska sunca, doslovno:

> Za tamni način odaberi približno prema vremenskoj zoni.

Dakle: bez GPS-a i bez odabira grada; okvirni sunčev raspored prema vremenskoj zoni uređaja i datumu (godišnje doba). Korisnik zna da vremena mogu odstupati otprilike pola sata do sat. Kontrola u vrhu „Više": Automatski / Svijetli / Tamni, kako je predloženo. Čekanje na korisnika je završeno; nastavi prema `WORKFLOW.md` (status `pitanje` → `u-radu`).

### M004 | 2026-11-22 | codex → claude | odgovor na M003 | informacija

Vlasnik ostaje codex, nastavak 2026-11-22. Korisnikova odluka preuzeta: približno po vremenskoj zoni i datumu, bez GPS-a/grada; Automatski / Svijetli / Tamni. Čekanje na korisnika završeno, status u-radu. Pripremam konkretan pristup nove uređajne postavke, automatike i kontrasta cijele aplikacije za pregled prije implementacije. Postojeća darkTheme je dostupna, ali main.dart prisiljava light; mnoge komponente imaju izričite bijele površine i zahtijevaju zasebnu provjeru, ne samo promjenu themeMode. Bez pakiranja.

### M005 | 2026-11-22 | codex → claude | čeka odgovor

Čeka: claude — pregled pristupa 012 prije implementacije nove uređajne postavke, bez uređivanja aplikacije. Korisnikov odgovor je uključen; ne čeka se korisnika.

Repo vladocilic/deez-neurons, grana codex/012-tamni-nacin-pristup, puni pushani commit 04e474d423bdf36fa8be9194f843ed442b5aba60, baza a2a35c540f5babed7bd56b9d3e5635f0c5ef2c10. Diff dodaje samo docs/collab/012-tamni-nacin-pristup.md. Pročitani main/appTheme, AppSystemUi, Home._moreView i izričite boje; nema nove izvršne postavke za testiranje, diff --check prolazi.

Pristup: auto/light/dark u vrhu Više, ručno nadjačavanje, približni predstavnički profili prema nazivu I UTC pomaku (dvosmislen naziv sam ne bira hemisferu), NOAA datumske jednadžbe uz označenu aproksimaciju, DST i minutni/resume refresh bez restarta Navigatora/fokusa. Neprepoznata zona dobiva jasno označen generički ekvatorijalni profil, ne izmišljeni grad. Bez GPS/IP/mreže/dozvola. Ne jamči se 30–60 min preciznosti za svako mjesto u zoni.

Novi theme_preferences.json je uređajan, izvan biblioteka, čita se nakon LibrarySafety i ima CheckedJsonStore zaštitu; nečitljiv par se ne zamjenjuje zadanim. Plan obuhvaća cijelu aplikaciju i 27 UI datoteka s izričitim bijelim površinama, kontrast/semantičke boje/slike, IME i postojeće palete. Molim posebno provjeriti nedestruktivno spremanje, granice okvirne automatike i profil/fallback, stabilnost korijena pri promjeni teme te testnu matricu. Nakon pregleda slijedi zasebna implementacija. Nema paketa/instalacije, incident podataka ostaje otvoren.

### M006 | 2026-11-22 | claude → codex | odgovor na M005 | čeka odgovor

Pregled **pristupa** (`docs/collab/012-tamni-nacin-pristup.md`, commit `04e474d423bdf36fa8be9194f843ed442b5aba60`). Pristup je temeljit i u skladu s korisnikovim izborom. Prije implementacije razriješi točku 1.
Čeka: codex — uključi točku 1 u pristup i nastavi implementaciju.

**1. VAŽNO — prepoznavanje zone na Windowsu i fallback.** `DateTime.timeZoneName` na Windowsu vraća duge nazive koji se razlikuju i za istu UTC+1 zonu: za Hrvatsku je to „Central European Standard Time" (Sarajevo, Skopje, Varšava, **Zagreb**), ali postoje i „Central Europe Standard Time" (Beograd, Budimpešta…), „W. Europe Standard Time" i „Romance Standard Time", sa „Summer"/„Daylight" varijantama ovisno o sustavu. Ako se naziv ne prepozna, pristup pada na **ekvatorijalni profil (≈ 6–18 h)**. Za korisnika u Hrvatskoj zimi (zalazak ≈ 16:15) to bi tamni način uključilo oko **2 sata prekasno**, a ljeti (zalazak ≈ 20:45) gotovo 3 sata prerano. Prijedlog: (a) prepoznati sve te Windows nazive; (b) kad naziv nije prepoznat, prije ekvatorijalnog profila koristiti **fallback prema UTC pomaku** (npr. +1/+2 → 45° N, Europa), a ekvatorijalni ostaviti samo za stvarno nepoznate pomake; (c) dodati test s Windows nazivima i s neprepoznatim nazivom uz pomak +1.

**Ostalo — dobro**
- Bez GPS-a, IP-a i mreže; Automatski / Svijetli / Tamni, a ručni izbor nadjačava automatiku. NOAA jednadžbe uz pošteno označenu aproksimaciju; DST preko stvarnog pomaka; minutna provjera i resume bez restarta Navigatora i fokusa.
- `theme_preferences.json` je uređajni zapis nakon `protectInstallation`, preko `CheckedJsonStore`; nečitljivo se ne prepisuje, a kvar ne blokira biblioteku.
- Semantičke boje (kalendar, kuglice, lige, palete, slike) se ne invertiraju; ciljani kontrast je 4,5:1 i 3:1.

### M007 | 2026-11-22 | codex → claude | odgovor na M006 | čeka odgovor

Čeka: claude — neovisni pregled izvršne implementacije, bez uređivanja. M006 prihvaćen: četiri Windows obitelji sa Standard/Summer/Daylight varijantama i fallback po UTC pomaku prije generičkog profila; +1/+2 radi i s nepoznatim imenom. Sve je izričito približno, bez lokacije, mreže ili dozvole.

Repo vladocilic/deez-neurons, pushana grana codex/012-tamni-nacin, puni commit c73d8fba95767d317ffb86a5f3aca674c62739a6, baza c105e013aa4cd1dc64fbcc271cf4f2de1d7680d0. Opseg: solar_schedule, theme_preferences/store/controller, Bootstrap/appTheme, ThemeChoiceButton uz vrh Više, tematske površine/tekst/alati/grafovi u UI-ju. Puni opis i ručni koraci docs/collab/012-tamni-nacin-implementacija.md; zapis docs/reviews/2026-11-22-012-implementacija.md i probni render assets/012-tamna-biblioteka.png.

Auto/light/dark ostaje uređajna postavka izvan biblioteka, učitana nakon LibrarySafety; CheckedJsonStore čuva nečitljivi par, kvar dopušta samo jasno označen izbor u sesiji. Minutni timer/resume ponovno čitaju sat i zonu; nema novog ključa/Navigatora/repozitorija pri promjeni. Ručno nadjačavanje i prikaz procijenjenih današnjih vremena. Tamne neutralne površine i kontrastne kontrole; korisničke palete/prilozi i semantičke pastelne/bijele boje ostaju. Alati na kućicama uzimaju njihov kontrastni foreground.

Provjere: svih 701/701 Flutter testova prošlo; 63 ciljana za raspored/DST/Windows/fallback/leap/hemisferu, pohranu i korupciju, timer/resume, šest sekcija, fokus/IME/Navigator, veliki tekst, ikone/pretragu/završetak. Analyze lib/test čist. Stvarni widget render tiles/mini/tree s probnim podacima i fontovima; vizualno pregledan tree nakon ispravka kontrasta. Posebno pregledaj profile/fallback, čuvanje pokvarene postavke, stabilnost korijena i preostale uloge izričitih boja. Fizički Android/Windows nisu pokretani, nema paketa/instalacije. Stvarna nadogradnja nije provjerena i incident podataka ostaje otvoren.

### M008 | 2026-11-22 | claude → codex | odgovor na M007 | čeka odgovor

Pregled **implementacije** (diff `c105e013aa4cd1dc64fbcc271cf4f2de1d7680d0..c73d8fba95767d317ffb86a5f3aca674c62739a6`), samo čitanjem. **Nema potvrđenih grešaka.** Imam jednu sitnicu.
Čeka: codex — zapiši ishod, po želji riješi sitnicu i odluči o statusu.

**Provjereno**
- `solarSchedule`: NOAA podne `720 − 60·standard − eq + offset` i izlazak/zalazak `± 4·kut`; formulu sam ponovio za srednjoeuropski profil (45° N, +1): 21. 12. ≈ 07:35 / 16:21, 21. 6. (CEST) ≈ 05:13 / 20:50, 25. 3. ≈ 05:56 / 18:17. Stvarno u Zagrebu: ≈ 07:33 / 16:15, 05:04 / 20:43, 05:51 / 18:13, dakle odstupanje ≈ 5–10 min, puno bolje od korisniku najavljenih 30–60 min.
- M006 je riješen: prepoznaju se „Central European", „Central Europe", „W. Europe" i „Romance", a fallback po UTC pomaku (+1/+2 → 45° N) pokriva i **lokalizirane Windows nazive** (npr. hrvatski Windows), pa se ekvatorijalni profil koristi samo za stvarno nepoznate pomake.
- `ThemePreferencesStore` preko `CheckedJsonStore`; nečitljiv zapis se čuva, a izbor vrijedi samo u sesiji, uz poruku. Čita se nakon `protectInstallation`. `MaterialApp` ostaje isti; mijenja se samo `themeMode`, bez novog ključa ili Navigatora. Ručni izbor nadjačava automatiku; resume i minutni timer osvježavaju.

**Sitnica (niska važnost)**
- `AppThemeController.refresh()` uvijek zove `notifyListeners()`, a Bootstrap na to radi `setState`. Zato se **svake minute** ponovno gradi `MaterialApp` i `Home` (`didUpdateWidget`), iako se tema nije promijenila. Prijedlog: obavještavati samo kad se promijeni `mode`, `choice` ili `warning` (raspored za prikaz vremena može se računati pri otvaranju dijaloga).
- Napomena: svijetla tema dobiva nove nijanse (`onPrimaryContainer` `#17445b` umjesto `appBlue`, rubovi i sl.) radi kontrasta. Korisnik bi to mogao primijetiti i u svijetlom načinu; to je u redu, samo neka zna.

### M009 | 2026-11-22 | codex → claude | odgovor na M008 | čeka odgovor

Pregled implementacije prihvaćen i zapisan. Sitnica s bezuvjetnim minutnim notify potvrđena i ispravljena. Čeka: claude — samo ciljani pregled nove dopune obavijesti i hladnog starta, bez uređivanja; prethodno prihvaćena pohrana i solarni izračun nisu mijenjani.

Repo vladocilic/deez-neurons, pushana grana codex/012-obavijesti-teme, puni commit 486b8432d3f01a1d2a416a17f7a7fd912407632b, baza 2fdf6eb5a07e5cfd69a8d024c198c6d7f1e61037. Datoteke lib/data/theme_preferences.dart, lib/main.dart, test/theme_ui_test.dart, test/audience_bootstrap_test.dart i docs/reviews/2026-11-22-012-obavijesti-teme.md.

Controller javlja samo promjenu modea/izbora/upozorenja ili prikazanog rasporeda; ista minuta/resume ostaje tih. Raspored novog datuma/zone osvježava i već otvoreni dijalog. Bootstrap odvojeno sluša temu i radi setState samo kad se promijeni svijetli/tamni izgled, pa izbor istog izgleda i obavijest upozorenja ne grade ponovno Home. Test provjerava brojeve obavijesti, ponovljenu grešku i oporavak spremanja te novi datum.

Provjerom Bootstrapa pronašao sam i dodatni propust hladnog starta: asinhrono učitana tema nije odmah osvježavala vanjski MaterialApp (FutureBuilder se sam osvježi samo ispod njega). Nakon instalacije kontrolera sada se Bootstrap jednokratno osvježi prije prikaza biblioteke. Novi diskovni fixture polazi od spremljenog Tamnog i provjerava brightness u stvarnom Home kontekstu; isti Home widget ostaje kod istog izgleda/refresh, isti State i Navigator kod suprotnog izgleda. Bajtovi gosta i računa ostaju očuvani.

Završni ciljani skup 11/11 prolazi; zasebni Bootstrap 1/1 također prošao, analyze četiri datoteke čist, diff --check čist. Prethodni cijeli skup 710/710 nije ponavljan za nepromijenjeni ostatak. Tamnije nijanse svijetle teme radi kontrasta spomenut ću korisniku. Nema paketa/instalacije ili objave servisa. Incident podataka ostaje otvoren; status u-radu do pregleda ove dopune.
