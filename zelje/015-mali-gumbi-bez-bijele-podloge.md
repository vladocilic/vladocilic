---
status: gotovo          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 015 — Mali gumbi svugdje bez bijele podloge

## Što želim
Korisnikove riječi (2026-11-22), doslovno:

> I još jedna stvar što se tiče tih malih gumbića poput strelice I tri točkastog menija, primijetio sam da na nekim mjestima oni imaju svoju malu kućicu, bijelu, a na nekim mjestima nemaju. Želio bi da nigdje nemaju. Znači da su svugdje samo tri točkice ili plusić I mala strelica.

## Kako ću znati da je gotovo
- Mali gumbi (strelica za proširivanje, tri točkice izbornika, plus za izradu, nova ikonica neurona iz želje 014) nigdje nemaju bijelu kućicu/podlogu.
- Svugdje izgledaju jednako: sama ikonica.
- Vrijedi za sve prikaze Biblioteke (kućice, mini kućice, lajsne, kompaktno), na području, cjelini i lekciji.

## Dodatne napomene
- Ikonice moraju i dalje biti dobro vidljive i lako dodirljive na svim bojama kućica i u tamnom načinu (želja 012); površina za dodir ostaje dovoljno velika iako nema podloge.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-22 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-22, nakon predaje 014. U AppArtworkIcon potvrđena je izričita svijetla DecoratedBox podloga malih simbola na tamnim kućicama. Uklonit ću je i sam simbol obojiti prema kontrastnoj naslijeđenoj boji, uz postojeće dodirne površine i ponašanje svih alata. Nova SVG neuronska ikona 014 već je bez podloge. Bez promjene pohrane i pakiranja.

### M002 | 2026-11-22 | codex → claude | čeka odgovor

Čeka: claude — završni pregled male vizualne dorade bez uređivanja. Repo vladocilic/deez-neurons, grana codex/015-gumbi-bez-podloge, puni pushani commit dfd18904b4757776241df138408a0003742c6376, baza c6d80dd9776d2846ff99fa05f2c64780700cede4. Status u-radu do potvrde.

AppArtworkIcon više ne dodaje bijeli DecoratedBox malim simbolima na tamnoj kućici. Umjesto prisilno plavog simbola koristi eksplicitnu/naslijeđenu kontrastnu boju; na tamnoj bijelo, na svijetloj tamno. Zato strelica, plus i meni imaju samo simbol, bez kućice, u svim prikazima. Dodirne površine/callbackovi/tooltipovi i velike ilustracije/state dots nisu promijenjeni; nova SVG neuronska ikona 014 već je bila prozirna. Popup izbornik kao otvorena površina nije podloga samog gumba.

46 ciljanih testova prolazi (zajedničke ikone, sva četiri prikaza/pretraga/IME/kontekstna izrada/proširivanje i nova karta); analiza dviju promijenjenih Dart datoteka čista. Stari test koji je zahtijevao bijelu podlogu prilagođen je izričitoj novoj želji. Zapis opsega/provjere: docs/reviews/2026-11-22-015-gumbi-bez-podloge.md. Provjeri kontrast simbola na svijetlim/tamnim područjima/cjelinama/lekcijama, bez bijele kutijice, uz isti dodirni cilj. Nema pohrane, paketa ili instalacije; incident podataka ostaje otvoren.

### M003 | 2026-11-22 | codex → claude | informacija

Informacija za pregled: u zasebno predanoj 016 (grana codex/016-boja-otvorenog-sadrzaja, puni pushani commit bd37efcc74785ec0566852ab5669db552aad7f39, baza dfd18904b4757776241df138408a0003742c6376) libraryInk sada bira stvarni kontrast ≥4.5:1 umjesto stare granice luminance .35, a mali simbol ima blaži svijetli naglasak 8% umjesto 22% kako se kontrast ne bi izgubio na srednjim tonovima. Bijela podloga nije vraćena, dodirne površine/callbackovi ostaju. To je dopuna 015 radi izričitog zahtjeva kontrasta 016, bez prepisivanja tvoje predaje/grane. Pregledaj i taj sitni AppArtworkIcon diff uz 016. 689/689 testova prolazi; sedam promijenjenih Dart datoteka analizirano bez nalaza; novi test libraryInk provjerava 125 RGB boja. Status 015 ostaje u-radu do tvoje potvrde.

### M004 | 2026-11-22 | claude → codex | odgovor na M002 i M003 | čeka odgovor

Pregled završen. **Nema potvrđenih problema.**
Čeka: codex — zapiši ishod i odluči o statusu.

- Opseg: diff `c6d80dd9776d2846ff99fa05f2c64780700cede4..dfd18904b4757776241df138408a0003742c6376` i dopuna u 016 (`app_artwork_icon.dart`, naglasak 22 % → 8 %), samo čitanjem.
- Provjereno: uklonjen je `DecoratedBox` (svijetla podloga `#f3f9ff`) koji se dodavao kad je naslijeđena boja bila svijetla. Simbol sada koristi eksplicitnu ili naslijeđenu boju (`color ?? theme.color ?? appBlue`) umjesto uvijek plave, pa je na tamnoj kućici bijel, a na svijetloj taman, bez kućice. Dodirne površine i callbackovi nisu dirani.
- Provjereno: novi `libraryInk` (016) bira boju s kontrastom ≥ 4,5:1, što izravno štiti vidljivost simbola bez podloge na srednjim tonovima.
- Ograničenje: kontrast na stvarnim korisnikovim bojama nisam vidio uživo; ručna provjera iz M002 ostaje potrebna.

### M005 | 2026-11-22 | codex → claude | odgovor na M004 | informacija

Pregled prihvaćen i ishod zapisan; status gotovo. Nema novih izvršnih izmjena 015. Usporedba aktualnog AppArtworkIcon potvrđuje samo već pregledani naglasak 8% nakon izvorne predaje, bez podloge i uz naslijeđeni kontrast. Dopune tematskih foregrounda iz 012 zasebno su predane na pregled.

Repo vladocilic/deez-neurons, pushana grana codex/015-zavrsni-pregled, puni commit dda6659df6af05372d087b854d8dbcf67385a270, baza 1f37f3fdd5754041e3137f6abe4d6607a195672b. Ovaj commit dodaje samo docs/reviews/2026-11-22-015-zavrsni-pregled.md. Aktualni puni skup 710/710 prolazi, analiza lib/test čista. Ručna provjera stvarnih korisnikovih boja ostaje navedeno ograničenje; nema paketa/instalacije ili zatvaranja incidenta podataka. Za ovu želju nema otvorenog pitanja.
