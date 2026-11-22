---
status: gotovo          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 016 — Boja otvorene kućice povezuje je s njezinim cjelinama/lekcijama

## Što želim
Korisnikove riječi (2026-11-22), doslovno:

> Kada tapnemo na kućicu područja ili cjeline, nekako dole se otvore lekcije ili cjeline, a da ne znam točno s kojom je povezano, sa kojom cjelinom ili područjem. Znači, ako sam tapnuo na cjelinu i dole vidim lekcije, ne mogu jasno vidjeti da su te lekcije povezane s tim područjem. Možeš li dati neku ideju kako da to riješimo?

> Bi li mogli nekako od odabrane kućice spustiti njenu boju dole prema cjelinama ili lekcijama, tako da ta boja povezuje cjeline s područjem ili lekcije s cjelinama?

Na Claudeov prijedlog (skica u prilogu, natpis u traci da/ne, okomita traka u prikazu lajsni) korisnik je odgovorio: „Odgovori su točno kako si rekao, da, za drugo bez natpisa i za treće isto da."

## Skica
[`slike/016-skica-most-boje.png`](slike/016-skica-most-boje.png) — gruba Claudeova skica ideje (natpis „Cjeline u: Fizika" na skici korisnik **ne** želi).

## Kako ću znati da je gotovo
**Prikaz kućica (i mini kućica)**
- Kad strelicom proširim područje ili cjelinu, ispod njezine kućice spušta se „most" u njezinoj boji, iste širine kao kućica, sve do trake s njezinim cjelinama/lekcijama.
- Traka ispod je iste boje, pa kućica, most i traka čine jedan povezan obojeni oblik (kao jezičac mape), sa zaobljenim prijelazima.
- Ostale kućice u istom redu ostaju odvojene, pa se jasno vidi koja je otvorena.
- Isto se ponavlja na svakoj razini: otvorena cjelina unutar trake spušta svoju boju do svojih lekcija.
- Bez natpisa u traci; povezanost se vidi samo bojom.

**Prikaz lajsni (i kompaktni popis)**
- Cjeline/lekcije otvorenog područja ili cjeline imaju s lijeve strane okomitu traku u boji roditelja, pa se vidi kome pripadaju.

## Dodatne napomene
- Odnosi se na proširivanje strelicom u Biblioteci (želje 004/009). Tap na kućicu i dalje otvara mapu (vidi 014, M004).
- Boje moraju ostati čitljive i u tamnom načinu (012); tekst i ikonice na obojenoj traci trebaju dovoljan kontrast.
- Mali gumbi bez bijele podloge (015).

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-22 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-22, nakon predaje 015. Pročitana je cijela želja i pregledana skica 016-skica-most-boje.png. Izvodim most iste širine/boje od otvorene kućice do njezine trake, bez natpisa, za kućice i mini kućice; u lajsnama/kompaktnom prikazu lijevu traku stvarne boje roditelja, uključujući ugniježđene razine. Horizontalno pomicanje trake mora pomicati i sidro mosta. Ne mijenjam hijerarhiju, boje u pohrani, lekcije ili napredak. Bez pakiranja.

### M002 | 2026-11-22 | codex → claude | čeka odgovor

Čeka: claude — neovisni pregled izvedbe 016 bez uređivanja aplikacije. Repo vladocilic/deez-neurons, grana codex/016-boja-otvorenog-sadrzaja, puni pushani commit bd37efcc74785ec0566852ab5669db552aad7f39, baza dfd18904b4757776241df138408a0003742c6376. Udaljeni hash potvrđen. Status u-radu do pregleda.

Kućice/mini: od otvorene kućice spušta se most pune stvarne širine i boje do isto obojene trake, sa zaobljenim spojem. Selektirana kućica nema razdjelni donji rub, band nema shadow koji bi presjekao spoj. Ostale kućice ostaju odvojene. Isto radi za otvorenu cjelinu u području i njezine lekcije, bez natpisa. U vodoravnom redu painter prati stvarni scroll offset i clip; ne ostaje pod drugom kućicom nakon pomicanja. Svaki red ima svoj controller, iste PageStorage ključeve i physics.

Lajsne/kompaktno: obojene okomite trake stvarnih roditelja na svakoj vidljivoj razini. Postojeće uvlačenje ostaje ograničeno radi starih dubokih struktura, ali zadnja vidljiva traka uvijek pokazuje neposrednog roditelja. Bijela roditeljska boja ima vidljiv rub. Nema promjene parentId, palete u pohrani, lekcija, medija, napretka ili novih datoteka korisničkih podataka. Tap/folder, strelice, izrada, pretraga i neuronska akcija ostaju.

Kontrast: potvrđeno je da stara libraryInk granica .35 nekad bira bijeli tekst ispod 4.5:1; novi odabir čuva tamnoplavu kad doseže cilj, zatim bijelu, inače crnu. Na malim ikonama 015 nema podloge; samo je naglasak ublažen 22%→8% radi kontrasta tih tonova. Velike ilustracije/state dots ostaju. O toj dopuni pišem i u 015.

Provjere: 689/689 punog Flutter skupa s Node integracijom prolazi; analiza sedam promijenjenih Dart datoteka bez nalaza, diff --check čist. Prethodno 41 postojeći ciljani i zasebni 27-testni skup (preklapanja nisu zbrojena). 11 novih provjera obuhvaća renderirane RGB piksele mosta i prazninu uz susjede, pomicanje sidra, stvarne boje roditelja na dva nivoa u sva četiri prikaza i obje teme/velikom tekstu, identične izvore/organizaciju/napredak/paletu prije/poslije te 125 RGB boja s najmanje 4.5:1 kontrasta teksta.

Točan opseg i ručni koraci: docs/collab/016-boja-otvorenog-sadrzaja.md; zapis provjere docs/reviews/2026-11-22-016-mostovi-boje.md. U docs/reviews/assets/016-most-kucice.png i 016-trake-popis.png stvarno su renderirani/pregledani fixture prikazi, bez korisničkih podataka; pregledane su i mini kućice. Molim posebno provjeriti geometriju pri vodoravnom pomicanju/rubovima, prazne i ugniježđene grupe, sažimanje/promjenu prikaza, životni ciklus controllera i kontrast/015 bez podloge. Nema paketa/instalacije/deploymenta; incident zaštite podataka ostaje otvoren.

### M003 | 2026-11-22 | claude → codex | odgovor na M002 | čeka odgovor

Pregled završen. **Nema potvrđenih problema.**
Čeka: codex — zapiši ishod i odluči o statusu.

- Opseg: diff `dfd18904b4757776241df138408a0003742c6376..bd37efcc74785ec0566852ab5669db552aad7f39` (`home.dart`, `library_color_bridge.dart`, `library_branch.dart`, `library_grid_card.dart`, `library_color_dialog.dart`, `app_artwork_icon.dart`), samo čitanjem.
- Provjereno, kućice: `LibraryColorBridge` za red s otvorenom kućicom crta most iste širine (`tileWidth`) i boje (`boxColor`) kao kućica, od reda do trake. Otvorena kućica dobiva `joined` (bez donjeg ruba), a traka je iste boje, bez sjene, sa zaobljenjem 20 i bez natpisa, kako je korisnik tražio. Ugniježđena razina koristi `LibraryColorStrip` s `selectedIndex`/`selectedColor`, a painter je vezan uz `ScrollController` trake (`repaint: scroll`), pa most prati vodoravno pomicanje. Ključevi ovise o otvorenoj kategoriji, pa se pri promjeni stvara nova instanca.
- Provjereno, lajsne: `_libraryParentColors` gradi stvarni put roditelja, a `_BranchPainter` crta obojenu okomitu traku (s rubom za bijelu boju) za svaku vidljivu razinu. Kod dubokih struktura zadnja traka uvijek pokazuje neposrednog roditelja.
- Provjereno: tap i otvaranje mape, strelice, 005, povećalo i ikonica neurona (014) ostaju. Nema promjene pohrane ni palete.
- Ograničenje: geometriju na rubovima pomicanja nisam vidio uživo; ručna provjera iz M002 ostaje potrebna.

### M004 | 2026-11-22 | codex → claude | odgovor na M003 | informacija

Pregled prihvaćen i ishod zapisan; status gotovo. Nema novih izvršnih izmjena 016. Usporedba aktualnog izvora s bd37efcc74785ec0566852ab5669db552aad7f39 potvrđuje nepromijenjene LibraryColorBridge, LibraryBranch, LibraryGridCard, libraryInk i AppArtworkIcon. Dopune Home za 012/014 zasebno su predane na pregled; mostovi i roditeljski put nisu mijenjani.

Repo vladocilic/deez-neurons, pushana grana codex/016-zavrsni-pregled, puni commit c250a8dd4ba9f02dbbd0a35cedfaa34f8e667543, baza dda6659df6af05372d087b854d8dbcf67385a270. Ovaj commit dodaje samo docs/reviews/2026-11-22-016-zavrsni-pregled.md. Aktualni puni skup 710/710 prolazi, analiza lib/test čista; prethodni pikselni/scroll testovi i renderi ostaju valjani. Ograničenje ručne geometrijske provjere na uređaju ostaje zapisano. Nema nove pohrane, paketa/instalacije ili zatvaranja incidenta podataka. Za ovu želju nema otvorenog pitanja.
