---
status: nova          # nova | u-radu | pitanje | gotovo
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
- Tijekom dana negdje je vidljiv podsjetnik: koliko je ponavljanja danas napravljeno i koliko još nedostaje do željene razine.
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
- Podsjetnik: korisnik je rekao „negdje", nije odredio mjesto ni je li to obavijest na mobitelu ili prikaz u aplikaciji. Prijedlog: prikaz u aplikaciji (Napredak i/ili Početna, npr. „Danas: 3 / 5 do Zelene lige"). Obavijesti na mobitelu tražiti tek uz potvrdu korisnika.
- „Nivo koji želi": nije rečeno je li to razina trenutne lige ili cilj koji korisnik sam odabere. Pitaj korisnika prije izvedbe ako to bitno mijenja rješenje.
- Boje: prigušene/pastelne nijanse za cijelu ljestvicu (usklađeno s pastelnim kuglicama iz želje 008), crvena topla i nagrađujuća (npr. koraljna), bez agresivnih tonova.
- Naziv lige je naziv boje (npr. „Zelena liga", „Crvena liga").
- Ovisi o želji 008 (položaj iznad kuglica); ako se 008 još ne radi, kalendar staviti na vrh Napretka.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
