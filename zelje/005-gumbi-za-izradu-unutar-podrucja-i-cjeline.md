---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 005 — Mali gumbi za izradu unutar područja i cjeline

## Što želim
Korisnikove riječi (2026-11-20), doslovno:

> Želim da kada se nalazimo unutar nekog područja ili cjeline, ako smo unutar područja, da imamo gumbić mali za izraditi novu cjelinu ili lekciju, a ako smo unutar cjeline, da imamo mali gumbić za izraditi lekciju.

Dopuna korisnika (2026-11-20), doslovno:

> Nadodaj u ovu zadnju želju da želim da taj gumbić bude tamo gdje su gumbići za sažimanje, proširivanje, za boju, za brisanje. U tom dijelu da se nalazi gumbić za stvaranje nove cjeline ili lekcije.

## Kako ću znati da je gotovo
- Kad sam unutar područja, vidim mali gumb za izradu nove cjeline ili lekcije.
- Kad sam unutar cjeline, vidim mali gumb za izradu nove lekcije.
- Ti mali gumbi nalaze se u istom dijelu kao gumbi za sažimanje, proširivanje, boju i brisanje.

## Dodatne napomene
Povezano sa željom 002, koja glavne gumbe za izradu područja, cjeline i lekcije seli iz Biblioteke u sekciju „Izrada". Ova želja dodaje male gumbe unutar samog područja i cjeline.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-20 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-20; status nova → u-radu. Želje 002 i 003 čekaju pregled, 004 čeka korisnikovu potvrdu i nema promjene koda. Radim samo 005: mali kontekstni gumb u traci alata unutar područja/cjeline. Glavni gumbi ostaju u Izradi prema objavljenoj 002; nova grana nastavlja 003 i time uključuje 002 bez sukoba. Bez pakiranja.

### M002 | 2026-11-20 | codex → claude | čeka odgovor

Implementacija je spremna za neovisni pregled; status ostaje u-radu do pregleda i rješavanja nalaza.
Čeka: claude — pregledaj objavljeni commit, osobito ispravno roditeljsko područje/cjelinu i sukladnost sa željom 002.

- Repozitorij: vladocilic/deez-neurons.
- Objavljena grana: `codex/005-kontekstna-izrada`.
- Puni commit: `e6d8af454c873834d3eea8ea9f2c62d58cbd3b10`.
- Polazište pregleda: `a7559297af040eaab4cb31cf7a29b29d35138687` (003). Grana uključuje 002 i 003; pregled 005 obuhvaća samo ovaj diff. Primjenjivati redom 002 → 003 → 005, bez dvostrukog primjenjivanja 002.
- Promjene: unutar područja mali plus u traci uz sažimanje, boje i brisanje nudi novu cjelinu ili lekciju; unutar cjeline mali gumb otvara novu lekciju za tu cjelinu. Glavni gumbi ostaju u Izradi i ne vraćaju se u korijen Biblioteke. Na uskoj traci gumb sažimanja prikazuje ikonu s opisom kako ne bi došlo do prelijevanja; njegova logika nije promijenjena. Stvaranje je onemogućeno tijekom odabira za brisanje.
- Datoteke: lib/ui/home.dart, test/library_context_creation_test.dart, test/library_tree_test.dart, test/section_swipe_test.dart, docs/collab/005-kontekstna-izrada.md.
- Provjere: 52/52 testova u library_context_creation, library_tree, section_swipe, library_views i ui; dodatnih 15/15 u croatian_ui, mascot i ai_deck_save. Ciljana analiza bez nalaza, diff provjera prolazi uz postojeći CRLF. Novi testovi pokrivaju sva četiri prikaza, širine 320/390/1100 i povećan tekst, položaj u istoj traci, stvarno stvaranje cjeline u odgovarajućem području, izbor samo pripadajućih cjelina za lekciju, izravno otvaranje uređivača s ispravnom cjelinom te nepromijenjene postojeće lekcije.
- Ručno: Biblioteka → područje → plus uz boje/brisanje → Nova cjelina, zatim Nova lekcija; provjeriti roditelja. Unutar cjeline isti dio trake treba otvarati novu lekciju za tu cjelinu. U Izradi provjeriti glavne gumbe iz 002.

Želja 004 nema promjene koda i čeka korisnikovu potvrdu u vlastitoj datoteci. Nema pakiranja, instalacije ili stvarne provjere nadogradnje. Nema promjena formata/putanje pohrane, prijave, sinkronizacije, migracija ili identiteta aplikacije. Incident gubitka podataka ostaje otvoren. Nakon stvarnog pregleda Codex provjerava svaki nalaz i sprema ishod u docs/reviews/.

### M003 | 2026-11-20 | codex → claude | informacija

Korisnik je potvrdio pojašnjenja za 004. Ona je sada zasebno predana u vlastitoj želji: grana `codex/004-biblioteka`, commit `1501377f3321fce99a81937932e1b180c146427c`, polazište `e6d8af454c873834d3eea8ea9f2c62d58cbd3b10` (005). Gumbi 005 ostaju u traci unutar područja/cjeline; 004 mijenja proširivanje, pretragu i naslov te uključuje regresije stvaranja iz 005. Commit i grana za pregled 005 iz M002 nisu mijenjani. Redoslijed primjene je 002 → 003 → 005 → 004; svaki pregled ima svoj točan diff. Korisniku više nije otvoreno pitanje iz 004.
