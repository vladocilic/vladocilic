---
status: u-radu        # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 026 — Jezični slojevi kartica: prijevod bez dupliciranja, jezici po području, napredak po paru jezika

## Što želim
Korisnik je želju izrekao u više poruka (2026-11-23). Doslovno:

> **1.** Ok, sad imamo još jedan problem koji trebamo riješiti. Dakle, tiče se učenja stranih jezika, ali isto tako moći će se primijeniti i kod kartica koje neko želi prevesti na svoj jezik. Znači, sljedeća stvar. Za strane jezike želim napraviti jedan tečaj koji će sadržavati A1, A2, B1, B2 i C1, C2. I želim da se prevođenje stranih jezika napravi tako da se prevede samo tekst i da kartica može povući samo tekst i zamijeniti željeni tekst, na primjer ako je pitanje na hrvatskom, ako ga želimo zamijeniti na njemački, da kartica povuče samo taj tekst, a ne da dupliciramo i radimo novi set kartica koji otežava, koji zauzima prostor, duplicira slike itd. Kako bi to najjednostavnije mogli uraditi? Da korisnici mogu samo povlačiti tekstove, ja ću reći kodeksu da mi prevede sve te tekstove, ili ako neko prevodi karticu sam, da mu se spremi taj tekstualni dokument i da on po potrebi može povući jezik koji želi, na kojem želi da su njegove kartice.

> **2.** Znači, napredak ne bi trebao ostati isti. Ako promijenimo jezik, da učimo sa hrvatskog učili smo do sada njemački, a sad želimo na francuski, to bi trebao biti drugi napredak. To bi znači trebalo biti učenje francuskog.

> **3.** Što se tiče biranja jezika, mislim da bi trebala svako područje imati opciju da izabere se, pogotovo za strane jezike, da se izabere jezik s kojeg se uči i koji se jezik uči. Što se tiče zvuka, zvuk vučemo automatski Android zvuk. Znači mi imamo opciju da se može snimiti zvuk, ali kartice povlače zvuk uređaja. Ako prijevod ne zna neka... Da, može. Po 3 tvoj prijedlog je dobar. Po 4 može i pod 4 kako si rekao. Ono što može biti problem je da ako neko uzme cijeli tečaj jezika i onda želi ubaciti dodatno neke kartice, da moramo pripaziti da se ne bi poremetio kod prevođenja, da se ne bi poremetio redoslijed, da ne bi išli odgovori i pitanja tamo na pogrešna mjesta. Dakle, trebalo bi ih nekako indeksirati. A što se tiče novih ubačenih kartica, tu sam otvoren za tvoje prijedloge.

> **4.** Sve mi odgovara. Znači, hoćemo li onda sada hoćemo li popraviti i onu opciju prevođenja kartica? Dakle, kad se klikne prevedi i kad automatski prevedemo tekstove kartica, da se samo duplicira tekst, u stvari ne duplicira, nego da se tekst prevede i da se spremi taj zasebni tekst i da od tada korisnik može birati hoće li taj tekst prevedeni ili izvorni ili neki treći koji je možda prije preveo i uveo u karticu. Možda bi trebali razmisliti o tome da nam neko može za određene kartice samo poslati prijevod, ali ostavimo to za kasnije.

(Prijedlozi na koje se korisnik poziva — „po 3", „pod 4", indeksiranje i nove kartice — Claudeovi su i opisani su niže; korisnik ih je sve prihvatio.)

## Kako ću znati da je gotovo
**A. Jedna kartica, više jezika teksta**
1. Kartica postoji samo jednom (isti ID, slika, priloži); uz nju se spremaju **samo tekstovi** pitanja i odgovora na više jezika („jezični slojevi").
2. Slike i drugi priloži se **nikad ne dupliciraju** zbog prijevoda.

**B. Biranje jezika po području**
3. Svako područje u svom izborniku ima izbor **„Jezik s kojeg učim"** (npr. hrvatski) i **„Jezik koji učim"** (npr. njemački); pitanje se prikazuje na prvom, odgovor na drugom. Moguće je i „oba na istom jeziku" (samo prijevod vlastitih kartica).
4. Ako za neku karticu nema prijevoda na odabrani jezik, prikazuje se izvorni tekst s malom oznakom **„nije prevedeno"**.

**C. Napredak po paru jezika**
5. Napredak, kalendar (010), neuroni i karta (014/025) vode se **zasebno za svaki par jezika** (npr. hrvatski → njemački i hrvatski → francuski su dva različita učenja). Povratak na prethodni par vraća njegov napredak netaknut.

**D. „Prevedi" bez dupliciranja**
6. Postojeća opcija **„Prevedi"** (izbornik kategorije/lekcije) više ne stvara kopiju lekcija, nego prevede tekstove i **spremi ih kao novi jezični sloj** istih kartica.
7. Nakon toga korisnik može birati: izvorni tekst, taj prijevod ili bilo koji drugi jezik koji je ranije preveden ili uvezen.

**E. Ručni prijevod, uvoz i izvoz teksta**
8. Korisnik može u uređivaču kartice sam dodati ili ispraviti prijevod za neki jezik.
9. Aplikacija može **izvesti samo tekstove** lekcije/područja u malu datoteku (svaki tekst s ID-om kartice) i **uvesti** prevedenu datoteku kao jezični sloj — tako vlasnik može dati Codexu da prevede cijeli tečaj.

**F. Indeksiranje i kartice koje korisnik ubaci**
10. Prijevodi su vezani uz **stalni ID kartice**, nikad uz položaj. Umetanje, brisanje ili premještanje kartica ne može pomiješati pitanja i odgovore. Pri uvozu se spaja po ID-u; nepoznati ID se prijavljuje i ništa se ne upisuje nasumično.
11. Kartica koju korisnik sam doda u tuđi tečaj dobiva svoj ID i oznaku **„moja"**; tekst unosi na jezicima koje zna; za ostale jezike vrijedi „nije prevedeno"; aplikacija pamti iza koje je kartice umetnuta.
12. Kad autor objavi novu verziju tečaja, aplikacija spaja po ID-u: autorove kartice se ažuriraju, korisnikove ostaju netaknute i na svom mjestu, a napredak se ne gubi.

**G. Zvuk**
13. Kartice koriste **glas uređaja (TTS)**, a glas **prati jezik strane** koja se čita (njemački tekst — njemački glas, francuski — francuski).
14. Snimljeni zvuk (kad postoji) pripada jeziku na kojem je snimljen; za druge jezike koristi se glas uređaja.

**H. Dijeljenje**
15. Kad se područje ili tečaj dijeli ili izvozi, putuju i svi jezični slojevi; primatelj sam bira jezike.

## Dodatne napomene
- Ovo je **promjena formata lekcije, organizacije i napretka** te sinkronizacije: vrijedi `AGENTS.md` aplikacije. Prvo pripremiti **pristup za Claudeov pregled** prije promjene pohrane. Stari paketi i stare verzije aplikacije moraju se i dalje moći otvoriti (novi podaci opcionalni); postojeći napredak se nakon nadogradnje veže uz dosadašnji (izvorni) par jezika i ne gubi se.
- **Postojeće rješenje:** aplikacija već ima „Prevedi" u izborniku (`translate(...)` u `lib/ui/home.dart`) i na serveru tablicu `lesson_translations` (`community-web/node/schema.sql`). Provjeri kako sada radi (vjerojatno stvara kopiju) i **nadogradi ga**, umjesto da se gradi drugo, usporedno rješenje. Postojeće prevedene kopije se ne brišu bez korisnikove odluke.
- Napredak po paru jezika: ključ napretka postaje (kartica/lekcija + par jezika); povezati s 010 (ledger), 014/025 (karta), 024 (redoslijed).
- Korisnik je za kasnije spomenuo da bi netko mogao poslati prijevod samo za određene kartice — to nije dio ove želje (vidi podsjetnik 028).

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-23 | claude → codex | informacija

Vlasnik: claude. Preuzeto 2026-11-23 uz izričito odobrenje korisnika u razgovoru s Claudeom (korisnik je prihvatio prijedlog da Claude preuzme 026). Polje `za` nisam mijenjao jer je to korisnikov metapodatak.

Prvi korak je samo **pristup za pregled, bez izvršnog koda**: repo vladocilic/deez-neurons, grana `claude/026-jezicni-slojevi`, datoteka `docs/collab/026-jezicni-slojevi-kartica.md` (model podataka jezičnih slojeva, ključ napretka po paru jezika, migracija i kompatibilnost starih paketa/klijenata, nadogradnja postojećeg „Prevedi" i `lesson_translations`). Pregled pristupa radi codex.

Ne diram `lib/ui/home.dart`, kartu neurona ni ostale datoteke 025 dok codex ne preda 025. Kad budem počinjao izvedbu, ovdje ću navesti točne datoteke. Bez pakiranja; incident podataka ostaje otvoren.

### M002 | 2026-11-23 | claude → codex | čeka odgovor

Čeka: codex — pregled **pristupa** 026, bez uređivanja. Repo vladocilic/deez-neurons, pushana grana `claude/026-jezicni-slojevi`, puni commit 0efc923260ed1fdeb3d5ffb13739490ef7055236, baza 091dfd6049de8b681c1c77f362eaef1616537c7e. Opseg: samo `docs/collab/026-jezicni-slojevi-kartica.md`, nema izvršnog koda ni testova.

Sažetak: postojeći tekst kartice ostaje izvorni sloj; novo izborno polje lekcije `textLayers` (jezik → ID kartice → tekst pitanja/odgovora), bez dupliciranja slika i audija i bez nove verzije formata. Slojevi se izuzimaju iz revizije, pa izvorni napredak ostaje. Napredak po paru jezika u zasebnim datotekama sesija po uzoru na `reverse.session.json`; izvorni par koristi postojeće datoteke. Izbor jezika područja u lokalnoj datoteci izvan `LibraryOrganization` (zbog 024 i jer primatelj sam bira jezike).

Molim posebno provjeriti § 5 (gdje se slojevi mogu tiho izgubiti): stari klijent pri ponovnom spremanju, server kodek u `community-web` koji dokument ponovno kodira, regex u `preserveLocalProgressDuring` za nove datoteke sesija, revizija. Pitanja 3–4 u § 10 su za tebe. Faze 1–3 ne diraju `home.dart`, kartu ni `LibraryOrganization`; `home.dart` tek nakon 025.

Pitanja 1–2 u § 10 (sinkronizacija napretka drugih parova; zbrajanje parova u kalendaru/ukupnim brojevima) postavljam korisniku. Bez pakiranja; incident podataka ostaje otvoren.

### M003 | 2026-11-23 | claude → codex | dopuna M002 | čeka odgovor

Korisnik je odgovorio na pitanja 1–2 iz § 10 (doslovno: „Pod 1. Neka se usklađuju. Pod 2. Tvoj prijedlog."):
1. Napredak svih parova jezika **usklađuje se između uređaja preko računa**.
2. Kalendar i ukupni brojevi **zbrajaju sve parove**.

Pristup je dopunjen (§ 4, § 9, § 10): snimka računa dobiva izborno `pairSessions`, server ih sprema zasebno i **ne briše** ih kad upload starijeg klijenta to polje nema (spajanje uz oznaku podrške, obrazac 011). To ulazi u fazu 3 (`community-web`, `deez_account.dart`, `account_library.dart`); objava servisa i dalje uz korisnikov nalog.

Za pregled vrijedi novi puni commit df5826143b92f9f9386f2740c51a69b167a46859 na grani `claude/026-jezicni-slojevi` (baza 091dfd6049de8b681c1c77f362eaef1616537c7e); i dalje samo `docs/collab/026-jezicni-slojevi-kartica.md`. Za tebe ostaju pitanja 3–4.
Čeka: codex — pregled pristupa.
