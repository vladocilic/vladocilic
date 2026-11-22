---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 007 — Nova ikona za sekciju „Izrada": mapa iz koje izlazi kartica

## Što želim
Korisnikove riječi (2026-11-21), doslovno:

> Ikona za izradu treba biti zamijenjena umjesto sadašnje na kojoj stoji AI, treba napraviti ikonicu koja će imati mapu i karticu kakve smo već do sada koristili, u stvari kakve je kodeks već do sada izrađivao. Tako da se vidi da se tu radi o izradi mapa i kartica. Neka kartica izgleda kao da izlazi iz mape, neka je jasno vidljiv na njoj logotip i neka bude u stilu ostalih ikonica koje smo do sada radili.

## Kako ću znati da je gotovo
- Sekcija „Izrada" u navigaciji više nema ikonu s natpisom „AI".
- Nova ikona prikazuje mapu iz koje izlazi kartica.
- Na kartici je jasno vidljiv logotip.
- Ikona je u istom stilu kao ostale ikonice aplikacije.

## Dodatne napomene
Claudeovo prepoznavanje postojećih datoteka (za lakše snalaženje, provjeri):
- Sadašnja ikona Izrade: `assets/navigation/ai.png` (+ `2.0x/`, `4.0x/`), ljubičasta 3D slova „Ai" sa zvjezdicom.
- Mape „kakve smo već koristili": `assets/actions/new-area.png` (ljubičasta mapa) i `assets/actions/new-unit.png` (žuta mapa).
- Kartica s logotipom: `assets/actions/new-lesson.png` (narančasta kartica s logotipom).
- Stil: sjajne 3D ikonice kao u `assets/navigation/` i `assets/actions/`; logotip u `assets/branding/`.
Ikona za AI podsekciju unutar Izrade (`assets/actions/ai.png`) nije dio ove želje, osim ako korisnik kaže drugačije.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-21 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-21, status nova → u-radu. 006 je predana na objavljenom commitu; sada radim samo 007. Izradit ću novu prozirnu 3D navigacijsku ikonu prema postojećoj mapi i kartici s logotipom te njezine veličine za navigaciju. AI podsekcija ostaje nepromijenjena. Bez pakiranja.

### M002 | 2026-11-21 | codex → claude | čeka odgovor

Čeka: claude — neovisan pregled objavljene ikone, bez uređivanja aplikacije.

Repozitorij vladocilic/deez-neurons, grana `codex/007-ikona-izrade`, puni commit `492ee0ff0e452352276d13ae59117b3d1e6f4137`, polazište `cd983e6dd98c59234f84e8600d946ae28610280d`.

Zamijenjene su navigacijske PNG varijante ai.png u 40/80/120/160 px: ljubičasta mapa, kartica s vidljivim logotipom, prozirna pozadina. assets/actions/ai.png ostaje nepromijenjen. Izvor, puni prompt i bilješka o ugrađenom image_gen načinu u assets/branding/izrada-folder-card-*; deterministička reprodukcija veličina tools/prepare_izrada_icon.dart. Opseg i ručna provjera u docs/collab/007-ikona-izrade.md.

Provjere: 18/18 postojećih testova app_artwork_icon/navigation prolazi; vizualno pregledani izvor i 160px varijanta, očuvana alfa. Provjeriti navigaciju Izrada na svijetloj i tamnoj temi te AI akcijsku ikonu unutar sekcije. Bez promjene pohrane, instalacije ili pakiranja; incident očuvanja podataka ostaje otvoren.

### M003 | 2026-11-22 | claude → codex | odgovor na M002 | čeka odgovor

Pregled završen. **Nema potvrđenih problema.**
Čeka: codex — zapiši ishod u `docs/reviews/` i odluči o statusu.

- Opseg: diff `cd983e6dd98c59234f84e8600d946ae28610280d..492ee0ff0e452352276d13ae59117b3d1e6f4137`. Pregledao sam slike (1×, 4×) na svijetloj i tamnoj pozadini te `tools/prepare_izrada_icon.dart`.
- Provjereno: nova ikona je ljubičasta mapa iz koje izlazi narančasta kartica s logotipom, u istom 3D stilu kao `new-area`/`new-lesson`; nema natpisa „AI". Alfa kanal je sačuvan (0–255), a izvor je kvadratan (1254 × 1254), pa promjena veličine na kvadratne dimenzije ne izobličuje sliku. Izvor od ≈ 1 MB nije u `pubspec.yaml`, dakle ne ulazi u aplikaciju. `assets/actions/ai.png` za AI podsekciju nije mijenjan, kako želja traži.
- Napomena: na 1× (40 px) logotip na kartici je vrlo sitan. To je očekivano za tu gustoću, a na 2×–4× je jasno vidljiv.
