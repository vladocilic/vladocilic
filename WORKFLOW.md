# Zajednička pravila rada (Claude i Codex)

Ovaj dokument vrijedi za **sve** AI agente koji rade na projektu These Neurons.
Vlasnik projekta komunicira na hrvatskom – pišite mu na hrvatskom.
Pravila su usuglašena u želji [`zelje/001-dogovor-komunikacije.md`](zelje/001-dogovor-komunikacije.md)
i odobrena od korisnika 2026-11-20.

## Repozitoriji i uloge

- **Sandučić:** `vladocilic/vladocilic`, grana `main`. Ovdje su želje i sva komunikacija.
- **Aplikacija:** `vladocilic/deez-neurons`. Kod se mijenja samo na radnim granama tog repozitorija.
  Za rad na aplikaciji vrijedi i njezin `AGENTS.md`, osobito zaštita podataka.
- **Oba agenta smiju izvoditi želje** (odobrio korisnik 2026-11-23: „Odobravam da i Claude piše kod").
  Tko radi neku želju određuje polje `za` (`codex`, `claude`, `bilo-tko`); vlasnik je onaj tko je preuzme.
- **Pregled radi drugi agent:** želju koju izvodi Codex pregledava Claude, a želju koju izvodi Claude pregledava Codex.
  Pregledavatelj te želje ne uređuje njezin kod.
- **Bez paralelnog uređivanja istih datoteka:** prije preuzimanja provjeri sve želje `u-radu` i datoteke koje
  njihov vlasnik navodi. Ako bi se dirale iste datoteke (osobito `lib/ui/home.dart`), ne preuzimaj — pričekaj
  ili u želji dogovori redoslijed. U poruci o preuzimanju navedi glavne datoteke koje ćeš mijenjati.
- **Odvojene radne kopije:** svaki agent radi u vlastitoj kopiji repozitorija i na vlastitim granama
  (`codex/...`, `claude/...`); nikad u istoj mapi u isto vrijeme.
- **Pakiranje i provjera nadogradnje** (Android/Windows paketi, emulator, fizički uređaj) radi Codex,
  dok korisnik ne odluči drugačije; Claude ih radi samo kad radi na korisnikovu računalu i kad mu je
  to izričito dodijeljeno.
- Oba agenta smiju u mapi `zelje/` sandučića dopisivati vlastite poruke i mijenjati polje `status`.
- `AGENTS.md` aplikacije treba uskladiti s ovim pravilima (to je promjena projektne datoteke; radi je
  Codex u sljedećoj prilici, Claude je pregleda).

## Pokretanje agenata

GitHub čuva poruke, ali **ne pokreće** ni jednog agenta. Korisnik pokreće agenta porukom
„Provjeri sandučić na GitHubu". Na početku svakog pokretanja agent čita:
nove želje za sebe, vlastite želje u statusu `u-radu` ili `pitanje` i nove poruke upućene njemu.

### Izravna predaja Claudeu (korisnikov nalog 2026-11-25)

Nakon završetka rada ili pregleda koji traži Claudeov nastavak, Codex sam upisuje i šalje upute u odgovarajući postojeći razgovor Claudeove desktop aplikacije, kako bi Claude mogao nastaviti. Korisnik ne treba prenositi poruke. Uputa navodi konkretnu želju i poruku u sandučiću te sljedeći zadatak; GitHub sandučić ostaje izvor potpune predaje i komunikacije. Codex provjerava da je poruka poslana. Ako slanje nije dostupno ili dopušteno alatima, jasno navodi ograničenje i ne tvrdi da je Claude pokrenut.

## Izvor posla: mapa `zelje/`

- Svaka datoteka u `zelje/` (osim `_PREDLOZAK.md`) je jedna želja korisnika.
- Na vrhu datoteke su polja `status`, `za` i `prioritet`.
- Uzimaj samo želje gdje je `za` tvoje ime (`claude` ili `codex`) ili `bilo-tko`.
- Redoslijed: `prioritet` visok → srednji → nizak; unutar istog prioriteta po broju u nazivu datoteke.
- Prije preuzimanja provjeri ostale preuzete želje.

## Tijek jedne želje

1. **Preuzmi:** u istom commitu na `main` upiši vlasnika i datum u „Bilješke agenta"
   i promijeni `status: nova` → `status: u-radu`. Agent koji izgubi utrku ne počinje raditi.
2. **Radi:** kod ide na radnu granu repozitorija aplikacije,
   npr. `codex/003-tamni-nacin`. Komunikacija ostaje u datoteci želje na `main` sandučića.
3. **Nejasno?** Ne izmišljaj. Postavi `status: pitanje` i dodaj redak
   `Čeka: korisnika | codex | claude — <konkretno pitanje>`. Stani u dijelu koji ovisi o odgovoru.
4. **Predaja za pregled:** glavni agent navodi repozitorij, granu i puni hash commita koji je
   pushan na GitHub, očekivano ponašanje i rezultate provjera. Lokalne, necommitane promjene
   nisu predane na pregled.
5. **Pregled:** Claude vraća nalaze i ograničenja u istoj želji. Glavni agent provjerava svaki
   nalaz i sprema zapis pregleda u `docs/reviews/` aplikacije.
6. **Završi:** tek nakon stvarnog završetka i potrebnih provjera kratko (na hrvatskom) napiši
   što je napravljeno i kako to provjeriti, pa postavi `status: gotovo`.

Predaja ili dopuna unutar postojećeg zadatka ne mijenja polje `za`.

## Poruke

- Sve poruke idu ispod `## Bilješke agenta` u datoteci želje, redom M001, M002, …
- Zaglavlje poruke ima oblik:
  `### M00N | datum | autor → primatelj | odgovor na M00X | čeka odgovor/informacija`
  (dio „odgovor na" izostavlja se kad poruka ne odgovara ni na što).
- Postojeće poruke se ne brišu ni prepravljaju; ispravak je nova poruka.

## Štednja tokena (korisnikov nalog 2026-11-25)

Vrijedi za oba agenta.

- **Korisniku:** kratko, najviše nekoliko redaka: što je napravljeno, rezultat i što čeka. Bez ponavljanja tehničkih detalja koji su već u sandučiću.
- **Poruke u sandučiću:** samo bitno. Predaja sadrži repo, granu, puni commit, bazu, opseg datoteka, popis ispravaka (jedna do dvije rečenice po stavci) i rezultate provjera. Pregled sadrži nalaze (važnost, mjesto, scenarij) i ishod. Bez prepričavanja prethodnih poruka i bez ponavljanja onoga što stoji u zapisu `docs/reviews/`.
- **Detalji** (reprodukcije, duža obrazloženja) idu u zapis pregleda ili commit poruku, ne u sandučić.
- **Čitanje:** čitati samo potrebne dijelove datoteka i poruka. Izlaze naredbi i testova filtrirati na sažetak i pogreške.
- **Testovi:** tijekom rada ciljani testovi; puni skup jednom prije predaje.
- **Novi razgovor:** kad razgovor postane dug, agent nastavlja u novom razgovoru. Sve potrebno za nastavak je u sandučiću.

## Sigurno zapisivanje

- Prije svakog upisa ponovno pročitaj cijelu datoteku s najnovijeg `main`.
- Piši na vrh najnovijeg `main` (Contents API s aktualnim blob SHA ili git push).
  **Nikad ne prepisuj prisilno** (`--force`).
- Ako je upis odbijen: ponovno pročitaj, provjeri status i vlasnika želje, pa uklopi svoju poruku.
  Ako je želju u međuvremenu preuzeo drugi agent, ne upisuj novo preuzimanje i ne počinji rad.

## Granice uređivanja

- Ne mijenjaj korisnikov tekst ni metapodatke datoteke želje (YAML zaglavlje i sve iznad crte
  koja otvara `## Bilješke agenta`), osim polja `status`. Komentari i ostali sadržaj se čuvaju.
- Ne preuzimaj želju koja je već `u-radu` kod drugog agenta.
- Ako tvoja promjena utječe na posao drugog agenta, zapiši to u bilješke.
- Ne briši želje; gotove ostaju kao povijest.
- Promjene ovih pravila unose se tek uz izričito odobrenje korisnika.
