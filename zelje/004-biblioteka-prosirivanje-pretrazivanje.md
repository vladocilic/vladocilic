---
status: pitanje          # nova | u-radu | pitanje | gotovo
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
