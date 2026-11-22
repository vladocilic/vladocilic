---
status: pitanje          # nova | u-radu | pitanje | gotovo
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
