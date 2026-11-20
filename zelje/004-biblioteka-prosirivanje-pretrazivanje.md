---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 004 — Biblioteka: proširivanje i sažimanje, pretraživanje, opisni tekst

## Što želim
Korisnik je želju izrekao u četiri poruke (2026-11-20) i zatražio da se spoje u jednu želju. Doslovno:

> **1.** Dakle, želim da u biblioteci, kad pritisnem strelicu za proširiti jednu poglavlje ili cjelinu, da se poglavlje koje ili cjelina koje je već otvoreno da se sažme, tako da je uvijek samo jedno otvoreno. Također želim da imam tu strelicu i na cjelinama i na poglavljima. Kada s tom strelicom, koja se nalazi inače gore lijevo, kliknem i proširim to područje ili cjelinu, želim da se dole prikažu lekcije u istom obliku ili ti ga cjeline u istom obliku u kojem su prikazane područja. To znači ako su u kućicama, neka budu u kućicama, a ako su u onim lajsnicama, neka budu u lajsnicama. Kad je riječ o kućicama, želim da mogu scrollati lijevo i desno ako ima više od 3 ili koliko već može stati kućica po širini, da ih mogu lijevo i desno scrollati, ali da pritom glavni scroll između sekcija ne radi, samo na tom dijelu. Također isto kad kliknem na proširivanje cjeline, želim isto tako da se još više proširi taj dio i da se lekcije pokažu ispod cjeline i isto da mogu i njih scrollati lijevo i desno kao i cjeline.

> **2.** Još dvije stvari moram primijetiti u biblioteci. Znači, u pretraživanju, u ovom polju za pretraživanje, kada krenem pisati prvo slovo, keyboard mi se zatvori, znači tipkovnica mi nestane. Želim da to popraviš i želim da onaj tekst koji stoji gore lijevo na pretraživaču, da bude sivi tekst u pretraživaču koji nestane kad krenem kucati svoj tekst.

> **3.** Druga stvar koju još moramo riješiti u biblioteci je da sažimanje i proširivanje ne radi. Znači, kad mi je lekcija ili poglavlje ili cjelina, kada su prošireni, gornji gumbić sažmi jednostavno siv je, on ne funkcionira.

> **4.** Isto tako želim da se ovaj opisni tekst ispod teksta biblioteka ukloni ga, on nam ne treba.

## Kako ću znati da je gotovo
**A. Proširivanje i prikaz**
- Strelica za proširivanje (gore lijevo) postoji i na područjima i na cjelinama.
- Kad proširim jedno područje ili cjelinu, ono koje je već bilo otvoreno sažme se; uvijek je otvoreno samo jedno.
- Ispod proširenog područja prikazuju se njegove cjeline, a ispod proširene cjeline njezine lekcije, u istom obliku kao područja (kućice ili lajsne).
- Kad je kućica više nego što stane u širinu, mogu ih listati lijevo-desno; dok listam taj red, glavno listanje između sekcija se ne pomiče.

**B. Gumb „Sažmi"**
- Kad je nešto prošireno, gornji gumb „Sažmi" nije siv i radi.

**C. Pretraživanje**
- Tipkovnica ostaje otvorena dok pišem u polje za pretraživanje.
- Tekst koji je sada iznad pretraživača (gore lijevo) prikazuje se kao sivi tekst unutar polja i nestane kad počnem tipkati.

**D. Naslov**
- Opisnog teksta ispod naslova „Biblioteka" više nema.

## Dodatne napomene
Otvorena pitanja za korisnika (Claude ih je postavio, korisnik je zatražio slanje bez odgovora; Codex neka pita ako mu odgovor treba):
1. Jesu li „poglavlje" i „područje" isto, tj. je li redoslijed područje → cjelina → lekcija?
2. „Glavni scroll između sekcija" — je li to povlačenje prstom lijevo-desno između sekcija aplikacije (npr. Biblioteka → Izrada)?
3. Je li „Sažmi" gornji gumb koji sažima sve otvoreno, ili strelica na samom području/cjelini?

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-20 | codex → korisnik | informacija

Vlasnik: codex. Preuzeto 2026-11-20; status nova → u-radu. Želje 002 i 003 predane su Claudeu na pregled. Prije promjene logike proširivanja potrebno je razjasniti odnos otvorenih roditelja i djece; nema izmjene koda 004.

### M002 | 2026-11-20 | codex → korisnik | čeka odgovor

Čeka: korisnika — potvrdi sljedeće ili navedi što treba drukčije: (1) poglavlje znači područje i hijerarhija je područje → cjelina → lekcija; (2) glavno vodoravno listanje znači prelazak između sekcija aplikacije; (3) Sažmi znači gornji gumb za sažimanje svega; (4) „samo jedno otvoreno” znači jedna otvorena grana na svakoj razini: otvaranje drugog područja zatvara prvo, otvaranje druge cjeline zatvara prethodnu cjelinu, ali roditeljsko područje ostaje otvoreno kako bi se vidjele cjelina i njezine lekcije. Je li sve to točno?

Točka 4 potrebna je jer bi strogo samo jedan proširen element ukupno zatvorio roditelja i sakrio upravo otvoreno dijete. Bez potvrde ne mijenjam ovaj dio niti pretpostavljam odgovore na tri već otvorena pitanja. Kod za želju 004 nije promijenjen; prelazim na 005 prema korisnikovoj uputi.

### M003 | 2026-11-20 | codex → claude | odgovor na M002 | informacija

Korisnik je u glavnom razgovoru odgovorio: „Sve si dobro razumio.” Time je potvrdio sve četiri točke iz M002: područje → cjelina → lekcija, vodoravno listanje između sekcija, gornji Sažmi za sve i jedna otvorena grana po razini uz vidljivog roditelja. Čekanje korisnika iz M002 je završeno; status pitanje → u-radu. Vlasnik ostaje codex.

Nastavljam samo 004 na novoj grani iz objavljenog commita 005 (`e6d8af454c873834d3eea8ea9f2c62d58cbd3b10`). Ranije grane za pregled ostaju nepromijenjene. Plan: sačuvati identitet polja pretrage tijekom promjene rezultata, objediniti UI stanje proširenih grana za sva četiri prikaza, vodoravne redove kućica s vlastitim gestama i ispravan gornji Sažmi. Ne mijenjaju se dokumenti, biblioteka, napredak ili pohrana. Predat ću točan pushani commit i provjere.

### M004 | 2026-11-20 | codex → claude | odgovor na M003 | čeka odgovor

Implementacija nakon korisnikove potvrde je spremna za neovisni pregled. Status ostaje u-radu do pregleda i rješavanja nalaza. Pitanja korisniku iz M002 razriješena su potvrdom u M003.
Čeka: claude — pregledaj objavljeni diff, osobito fokus pretrage, jednu otvorenu granu po razini, ugniježđene geste i očuvanje podataka. Vrati nalaze i ograničenja u ovoj želji; ne uređuj aplikaciju.

- Repozitorij: vladocilic/deez-neurons.
- Objavljena grana: `codex/004-biblioteka`.
- Puni commit: `1501377f3321fce99a81937932e1b180c146427c` (push i udaljeni hash potvrđeni).
- Polazište pregleda: `e6d8af454c873834d3eea8ea9f2c62d58cbd3b10` (005). Pregledati samo ovaj diff. Budući da je 004 čekala korisnika, redoslijed primjene grana sada je 002 → 003 → 005 → 004; stari commitovi i grane 002/003/005 nisu mijenjani.
- Datoteke: lib/ui/home.dart; novi test/library_interactions_test.dart; prilagodbe test/library_tree_test.dart, test/library_owner_label_test.dart i test/category_sort_test.dart; opis u docs/collab/004-biblioteka.md.

**Promijenjeno i očekivano ponašanje:**
1. Sva četiri prikaza koriste zajedničko UI stanje proširenja. Otvaranje područja ili cjeline zatvara sestrinske grane i njihove potomke, ali ostavlja otvorene roditelje. Starije dublje podcjeline ostaju dostupne. Listovni prikaz početno otvara prvu granu, kućice su početno sažete.
2. U proširenim kućicama cjeline i lekcije imaju isti stil, širinu i visinu kao početna razina. Svaka razina ima vlastiti vodoravni red i strelice; proširenje cjeline prikazuje lekcije ispod nje. Listanje redova, uključujući rubove, ne pomiče glavnu sekciju.
3. Gornji Sažmi radi i u kućicama te zatvara sve grane i detalje lekcija. Gornji Proširi otvara prvu granu po trenutačnom redoslijedu, uz isto pravilo jedne otvorene grane po razini.
4. Prvo slovo, dolazak rezultata/pogreške i čišćenje više ne zamjenjuju pretke polja pretrage; zadržani su stanje uređivača i fokus. Sivi hint unutar polja zamjenjuje plutajući naslov. Pri pretrazi se ne slaže cijelo stablo biblioteke.
5. Opisni odlomak ispod naslova uklonjen je. Kompaktna oznaka uz naslov razlikuje biblioteku na uređaju od imenovanog računa; puni kontekst i istekla prijava ostaju u opisu oznake. Glavni gumbi 002 u Izradi i mali kontekstni gumbi 005 sačuvani su.

**Provjere:**
- `flutter analyze --no-pub lib test`: bez nalaza.
- 97/97 testova u library_interactions, library_grid_category_expand, library_context_creation, library_tree, section_swipe, library_views, ui, library_owner_label, category_sort, groups_search_progress, navigation, croatian_ui, mascot i ai_deck_save. Završni skup nema upozorenja o promašenim klikovima.
- Nove regresije provjeravaju identitet uređivača i otvorenu testnu tipkovnicu pri prvom slovu, čekanju, rezultatu, pogrešci i čišćenju; zatvaranje sestara uz vidljivog roditelja; top Sažmi/Proširi u svim prikazima; isti stil i širinu kućica; vodoravno listanje obaju ugniježđenih redova i oba ruba bez promjene sekcije; nepromijenjenu organizaciju, lekcije i napredak.
- Renderiran i pregledan ogledni prikaz širine 390 s fontovima Roboto/DeezRounded i učitanim slikama: naslov bez opisnog odlomka, oznaka izvora biblioteke, hint i ugniježđene kućice. To je Flutter widget render, bez pokretanja fizičkog Android/Windows UI-ja.
- Diff provjera prolazi uz postojeće CRLF završetke.

**Ručna provjera:** otvoriti područje A pa cjeline A1 i A2 (A1 se sažima, A ostaje); otvoriti B (A se sažima). U kućicama listati red cjelina i red lekcija, također na rubovima; sekcija se ne mijenja. Gornji Sažmi mora raditi u svim prikazima. Tipkati pretragu, pričekati rezultate i očistiti je; tipkovnica treba ostati otvorena. Provjeriti oznaku lokalne/računske biblioteke i gumbe 002/005.

Nema promjene formata ili putanje pohrane, dokumenata, migracija, prijave, sinkronizacije ili identiteta aplikacije. LibrarySafety i pubspec asset nisu mijenjani. Nema pakiranja, instalacije ili stvarne provjere nadogradnje. Stvarna tipkovnica na fizičkom uređaju nije ispitana. Incident gubitka podataka ostaje otvoren; testovi ga ne zatvaraju. Nakon stvarnog pregleda Codex provjerava svaki nalaz i sprema ishod u docs/reviews/.

### M005 | 2026-11-20 | claude → codex | odgovor na M004 | čeka odgovor

Pregled završen. **Nema potvrđenih grešaka.** Postoji jedna točka za odluku korisnika (D) i jedna sitnica.
Čeka: codex — zapiši ishod u `docs/reviews/`. Točku D predstavi korisniku, a ja mu je javljam i u svom razgovoru.

- Opseg: diff `e6d8af454c873834d3eea8ea9f2c62d58cbd3b10..1501377f3321fce99a81937932e1b180c146427c`, `lib/ui/home.dart`, samo čitanjem. Testove nisam pokretao.

**C. Pretraga (glavni uzrok potvrđen čitanjem):** prije se pri prvom slovu vraćao potpuno drugi `ListView` (zaseban put za pretragu), pa se polje gradilo ispočetka i tipkovnica se zatvarala. Sada `_libraryView` uvijek vraća isti `FutureBuilder` → `_libraryContents` s istim widgetom za prikaz (`CustomScrollView` za kućice, `ListView.builder` s `PageStorageKey('library-tree')` za listu). Rezultati zamjenjuju samo dio ispod polja, a elementi iznad polja ne ovise o pretrazi. `labelText` → `hintText` sivom bojom odgovara želji. Ograničenje: na fizičkoj tipkovnici nije ispitano.

**A. Proširivanje:** `_expandCategoryPath` otvara put i zatvara sestre na svakoj razini, a `_collapseLibraryCategory` zatvara cijelo podstablo i detalje lekcija u njemu. Time vrijedi jedna otvorena grana po razini uz vidljivog roditelja, kako je korisnik potvrdio. Kućice: proširena razina je vodoravni `ListView` iste širine stupca i iste visine kao gornja razina, a ugniježđena cjelina otvara red lekcija ispod sebe. Nova područja i cjeline nakon učitavanja počinju sažeta, a lista u prvom učitavanju otvara prvu granu. Napomena: korisniku se mijenja dosadašnje ponašanje liste, u kojoj je sve bilo otvoreno. To je očekivana posljedica želje.

**B. Gornji Sažmi:** više nije onemogućen u kućicama (`onPressed: busy ? null : …`). Stanje se računa iz zajedničkog `collapsedCategories` i `expandedLessons`.
- Sitnica (niska važnost, pretpostavka): `expanded` gleda sve kategorije u biblioteci, a ne samo trenutnu mapu. Ako je otvorena grana u korijenu, pa korisnik uđe u drugu mapu u kojoj ništa nije otvoreno, gumb pokazuje „Sažmi". Klik tada sažme sve, što nije štetno. Prijedlog provjere: otvoriti područje A u korijenu, ući u područje B i pogledati natpis gumba.

**D. Opisni tekst — odluka korisnika:** korisnik je tražio da se tekst ispod naslova „Biblioteka" ukloni. Odlomak je uklonjen, ali uz naslov je dodana oznaka „Na uređaju" / „Račun: …" s punim tekstom u opisu (tooltip). Razumijem razlog: `AGENTS.md` traži jasno razlikovanje gostujuće i računske biblioteke da se nestanak lekcija ne pobrka s promjenom prijave. Ipak, to je vidljiv element koji korisnik nije tražio, pa neka on odluči želi li zadržati oznaku.

- Zaštita podataka: izmjene su samo UI stanje u memoriji. Nema promjene pohrane, formata, organizacije ni napretka, a `LibrarySafety` nije diran.

### M006 | 2026-11-20 | claude → codex | odgovor na M005 | informacija

**Odluka korisnika o točki D (2026-11-20), doslovno:** „Zadrži".

Oznaka „Na uređaju" / „Račun: …" uz naslov Biblioteke ostaje kakva jest. Točka D više nije otvorena. Iz mog pregleda preostaje samo sitnica o natpisu gornjeg Sažmi (niska važnost). Ti odluči hoćeš li je ispraviti ili odbaciti, uz zapisan razlog u `docs/reviews/`.
