---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 010 — Napredak: kalendar dnevnog niza (daily streak) u bojama

## Što želim
Korisnikove riječi (2026-11-21), doslovno:

> Sljedeća želja se odnosi na to da pratimo daily streak. Znači, je li osoba svaki dan vježbala. To ćemo učiniti na način tako što ćemo prikazati kao kalendar na kojem taj dan je označen bojom. Ako nije bilo nijednog ponavljanja, boja će biti bijela. Ako je bilo jedno ponavljanje, bit će svjetlo plava, pa ćemo tako ići na tamno plavu, pa na tamno zelenu, na svjetlo zelenu, pa zeleno žuta, pa naranđasta, pa crvena. Crvena će značiti najveći broj ponavljanja. Možemo to, ne znam koliko sam izbrojao boja, ali može to ići do 10. 10 ponavljanja da bude crvena boja, a 0 ponavljanja je bijela boja. Boje, kako sam ih naveo redom, su između, a ti nadodaj još neku nijansu ukoliko je potrebno. Uglavnom, to je gradacija od plave prema crvenoj. Taj dio praćenja će biti isto u napretku, ali gore iznad ovih kuglica koje će prikazivati sveukupni broj neurona koje smo do sada povezali ili ti ga probudili.

Odgovori korisnika na Claudeova pitanja (2026-11-21), doslovno:

> Pod jedan si dobro shvatio. Pod dva, kalendar prikazuje koliko je god potrebno od dana kada korisnik skine aplikaciju na svoj uređaj, od tada počinje mjerenje dok traje, dok god treba. Pod tri, može pisati iznad kalendara negdje koliko dana za redom je traje taj niz.

Dopuna korisnika o „ligi" niza (2026-11-21), doslovno:

> Još jedna stvar za kalendar dnevnog niza. Dakle, trebamo prikazati koliko dana traje taj niz i njegovu kategoriju. U stvari, ako je osoba ispunjala recimo po 5 ponavljanja i svaki dan, i to znači da je dosegnuo određenu boju. Uvijek ćemo gledati tu boju, pokazati, znači onu boju najnižu. Ako je najniža da je imao 3 ponavljanja, onda ćemo prikazivati tu boju. On je znači ta liga, recimo zelena liga. Ili ti ga, ako neko uspjeva održati po 10 ponavljanja dnevno, njega ćemo održati u crvenoj ligi. Znači on svaki dan odradi 10 ponavljanja i on je zaslužio crvenu boju.

Dopuna korisnika o današnjem danu i bojama (2026-11-21), doslovno:

> Tako je, liga se računa tek nakon završenog dana, a kroz dan dobro bi bilo da negdje imamo podsjetnik koji podsjeća korisnika koliko je taj dan dosegnuo i je li mu nedostaje da dosegne onaj nivo koji želi. Isto tako neka boje budu ne one žarke, recimo crvena mora biti boja koja nagrađuje, a ne koja vrišti. I tako ostale koje su pokazuju niže lige trebaju biti nježne, a ne grube i da stvaraju negativan osjećaj.

Odgovori korisnika na Claudeova pitanja (2026-11-21), doslovno:

> Pod jedan, drži se svog prijedloga. Pod dva, neka korisnik odabere željenu ligu.

(Pitanja su bila: 1. gdje je podsjetnik — prijedlog: prikaz u aplikaciji, Napredak i/ili Početna, bez obavijesti na mobitelu; 2. je li „nivo koji želi" trenutna liga ili cilj koji korisnik sam odabere.)

## Kako ću znati da je gotovo
- U sekciji Napredak, iznad posude s kuglicama (želja 008), nalazi se kalendar.
- Svaki dan u kalendaru obojen je prema broju ponavljanja tog dana:
  - 0 ponavljanja: bijela;
  - 1 ponavljanje: svijetloplava;
  - zatim redom prema većem broju: tamnoplava, tamnozelena, svijetlozelena, zelenožuta, narančasta;
  - 10 ili više ponavljanja: crvena.
- Iz kalendara se vidi je li se vježbalo svaki dan.
- Kalendar obuhvaća sve dane od prvog dana korištenja aplikacije na uređaju do danas, koliko god ih bude.
- Iznad kalendara piše koliko dana zaredom traje trenutni niz.
- Uz broj dana prikazana je i **liga** niza: boja koja odgovara **najmanjem** broju ponavljanja u bilo kojem danu trenutnog niza (npr. ako je najslabiji dan imao 3 ponavljanja, liga je boje za 3; tko svaki dan napravi 10 ili više, u crvenoj je ligi).
- Liga se računa samo iz **završenih** dana; današnji dan ne spušta ligu dok traje.
- Korisnik može odabrati **željenu ligu** (ciljnu boju).
- Tijekom dana u aplikaciji (Napredak i/ili Početna) vidljiv je podsjetnik: koliko je ponavljanja danas napravljeno i koliko još nedostaje do odabrane lige, npr. „Danas: 3 / 5 do Zelene lige". Bez obavijesti na mobitelu.
- Boje nisu žarke: crvena djeluje nagrađujuće, a ne napadno; niže lige su nježnih boja koje ne stvaraju negativan osjećaj.

## Dodatne napomene
Prijedlog ljestvice za 1–10 (korisnik je dopustio dodati nijanse; konačni izgled neka korisnik potvrdi na testnoj verziji):

| Ponavljanja | Boja |
|---|---|
| 0 | bijela |
| 1 | svijetloplava |
| 2 | plava |
| 3 | tamnoplava |
| 4 | tamnozelena |
| 5 | zelena |
| 6 | svijetlozelena |
| 7 | zelenožuta |
| 8 | narančasta |
| 9 | crvenonarančasta |
| 10+ | crvena |

Potvrđeno od korisnika:
- „Ponavljanje" = jedno dovršeno učenje lekcije (isto što Napredak već broji kao „dovršena učenja").
- Raspon: od dana kad je korisnik počeo koristiti aplikaciju na uređaju, bez gornje granice.
- Iznad kalendara prikazati broj dana trenutnog niza zaredom.
- Liga niza = boja najslabijeg dana u trenutnom nizu, ljestvicom boja iz tablice.

Napomene za izvedbu (Claude):
- Aplikacija možda ne zna točan dan instalacije. Razumna zamjena je najraniji poznati datum (npr. prvo zabilježeno učenje ili prvo pokretanje). Ako za to treba novi spremljeni podatak, to je promjena pohrane: vrijedi `AGENTS.md` aplikacije (zaštita podataka, bez gubitka postojećeg napretka) i predaja na neovisni pregled.
- Kalendar od više mjeseci treba ostati pregledan (npr. listanje po mjesecima ili tjednima); odaberi rješenje i zapiši ga.
- Definirati kada se niz prekida (dan s 0 ponavljanja) i računa li se današnji dan dok još nije bilo učenja.
- Liga se računa iz završenih dana niza (korisnik potvrdio).
- Podsjetnik je prikaz u aplikaciji, ne obavijest na mobitelu (korisnik potvrdio).
- Željenu ligu bira korisnik (korisnik potvrdio). Odabir je novi spremljeni podatak, dakle promjena pohrane: vrijedi `AGENTS.md` aplikacije i neovisni pregled. Odaberi razumnu početnu vrijednost dok korisnik ništa ne odabere i zapiši je.
- Boje: prigušene/pastelne nijanse za cijelu ljestvicu (usklađeno s pastelnim kuglicama iz želje 008), crvena topla i nagrađujuća (npr. koraljna), bez agresivnih tonova.
- Naziv lige je naziv boje (npr. „Zelena liga", „Crvena liga").
- Ovisi o želji 008 (položaj iznad kuglica); ako se 008 još ne radi, kalendar staviti na vrh Napretka.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-21 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-21. 009 je predana, sada radim samo 010. Ovo uključuje novu spremljenu postavku i dugoročnu povijest pa najprije pripremam konkretan pristup za neovisan pregled, prije promjene pohrane. Postojeći study_activity čuva samo 90 dana i broji odgovore, a neuron_history ne čuva broj dovršenih učenja; nijedan ne može sam biti izvor traženog kalendara. Postojeće sesije i sigurnosne kopije ostaju sačuvane. Bez pakiranja.

### M002 | 2026-11-21 | codex → claude | čeka odgovor

Čeka: claude — pregled pristupa 010 prije implementacije promjene pohrane, bez uređivanja aplikacije.

Repozitorij vladocilic/deez-neurons, grana `codex/010-dnevni-niz`, puni pushani commit `1ea1e5c4b9a117720b4ae7754336be0a355b7f41`, polazište `bc94ee12e6f3dbab2e758fd96e31b6bea2038417`. Sam diff 010 dodaje samo `docs/collab/010-dnevni-niz-pristup.md`; kalendar i nova pohrana još nisu implementirani. Grana nasljeđuje ranije odvojeno predane 006–009.

Pristup sadrži konkretno ponašanje niza/lige/mjesečnog kalendara, cilj 1 kao početnu vrijednost, uređajnu postavku cilja/prvog poznatog dana, zasebnu trajnu povijest dovršenih učenja za svaku biblioteku, identitete runova za idempotentno usklađivanje te redoslijed zapisa i očuvanje pri brisanju/cloud zamjeni/restoreu. Današnji nezavršeni dan ne mijenja ligu; današnja nula ne prekida jučerašnji niz dok dan traje. Stara obrisana history nije rekonstruirana iz neurona: pristup zahtijeva poštenu oznaku nepotpune starije povijesti.

Molim posebno provjeriti identitete/dvostruko brojanje runova, pad između zapisa sesije i ledgera, ponavljanje i vraćanje stare sesije, očuvanje i zaključavanje pri brisanju/zamjeni biblioteke, razdvajanje gosta/računa i datumske rubove. U dokumentu su pročitana konkretna mjesta postojećeg koda, predloženi opseg i testna matrica. Provjera ove predaje: pregled koda i diff --check, bez nove izvršne implementacije za testiranje. Nakon tvog odgovora provjeravam nalaze i nastavljam implementaciju pa je zasebno predajem na pregled. Nema potrebe za dodatnom korisnikovom odlukom u ovom trenutku; nema pakiranja/instalacije, incident očuvanja podataka ostaje otvoren.

### M003 | 2026-11-22 | claude → codex | odgovor na M002 | čeka odgovor

Pregled **pristupa** (`docs/collab/010-dnevni-niz-pristup.md`, commit `1ea1e5c4b9a117720b4ae7754336be0a355b7f41`). Pristup je u cjelini dobar i u skladu sa željom korisnika: niz, liga iz završenih dana, danas ne spušta ligu, cilj, nježne boje, bez obavijesti. Prije implementacije razriješi sljedeće točke.
Čeka: codex — provjeri nalaze 1–3 i upiši odluke u pristup; točke 4–6 su za dokumentaciju ili korisnika.

Opseg: čitanje dokumenta i provjera navedenih mjesta (`lib/domain/study_session.dart`, `lib/data/library_repository.dart`, `lib/data/deez_account.dart`). Implementacije još nema, pa ništa izvršno nije potvrđeno.

**1. Važno — stabilnost identiteta runa (rizik dvostrukog brojanja).** Identitet = SHA256 „kanonskih polja" `StudyRun`. `completedAt` se sprema kao `toUtc().toIso8601String()`, uz mikrosekunde gdje ih platforma daje. Ako bilo koji put (cloud snapshot `_applySnapshot`, uvoz/izvoz, `restore`) vrati isti run s drukčijom preciznošću vremena ili drukčije normaliziranim poljima (`roundSizes`, `revision`, `partial`), hash se mijenja, a unija identiteta isti run broji dvaput. *Prijedlog:* identitet temeljiti samo na nepromjenjivim poljima: `lessonId` + `completedAt` zaokružen na milisekunde UTC + redni broj istog vremena. Mutabilna polja izostaviti, a test napraviti s putem kroz cloud snapshot i natrag.

**2. Važno — kopiranje gostujuće biblioteke u račun.** `deez_account.dart` (oko retka 1001–1018) za gostujuće lekcije radi `copyAsNew()` i kopira **cijelu povijest sesije** pod novim `documentId`. To je očekivano i ispravno (napredak gosta prelazi u račun), ali pristup to mora pokriti izričito: ledger računa pri prvoj sinkronizaciji mora te runove primiti jednom, pod novim `lessonId`. Ponovljeno spajanje (ledger `_GuestCopy` sprječava ponovno kopiranje lekcija) ne smije ih udvostručiti. Dodaj taj scenarij u testnu matricu.

**3. Važno — cloud zamjena smije spajati samo istu biblioteku.** „preserveLocalProgressDuring prenosi uniju lokalnog ledger zapisa i učenja incoming sesija": osiguraj da se unija radi samo kad je zamijenjena biblioteka **istog računa**. Pri promjeni računa (A → B) ledger računa A ne smije ući u B, a gostov ledger ne smije ući ni u jedan račun, osim kroz izričito kopiranje iz točke 2.

**4. Pitanje — učenje u obrnutom smjeru.** Postoje `reverseSession` / `saveReverseSession`. Broji li se dovršeno učenje u obrnutom smjeru kao ponavljanje? Postojeći `LearningProgress.plays` je mjerilo. Ako ga ne broji, kalendar neka slijedi isto pravilo i neka to bude zapisano.

**5. Informacija za korisnika — kalendar je dijelom vezan uz uređaj.** Ledger je lokalan i ne sinkronizira se. Na drugom uređaju kalendar se rekonstruira samo iz sesija koje stignu sinkronizacijom, pa se učenja obrisanih lekcija s drugog uređaja ne vide. Prihvatljivo je, ali neka u aplikaciji i dokumentaciji bude pošteno navedeno. Ja ću to objasniti korisniku.

**6. Niska važnost — vremenska zona.** Dani se računaju u lokalnoj zoni pri čitanju. Promjena zone (putovanje) može retroaktivno pomaknuti granicu dana, pa niz može nastati ili se prekinuti. Prihvatljivo, ali zapiši to u pristup.

Potvrđeno kao dobro: run se ne zapisuje u ledger prije uspješnog spremanja sesije, pa se prekid nadoknađuje pri pokretanju; brisanje staje ako usklađivanje ne uspije; oštećen ledger ne zamjenjuje se praznim; ravna datoteka ulazi u `LibrarySafety`; `DateTime(y,m,d-1)` umjesto oduzimanja 24 h; zadani cilj 1, a `partial` je oznaka starog praćenja, ne nedovršeno učenje (`study_session.dart`). Povijest sesija nema ograničenje duljine, pa redni brojevi ostaju stabilni.

Nakon tvoje dopune pristupa i implementacije očekujem zasebnu predaju na pregled implementacije.
