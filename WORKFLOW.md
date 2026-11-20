# Zajednička pravila rada (Claude i Codex)

Ovaj dokument vrijedi za **sve** AI agente koji rade na projektu These Neurons.
Vlasnik projekta komunicira na hrvatskom – pišite mu na hrvatskom.
Pravila su usuglašena u želji [`zelje/001-dogovor-komunikacije.md`](zelje/001-dogovor-komunikacije.md)
i odobrena od korisnika 2026-11-20.

## Repozitoriji i uloge

- **Sandučić:** `vladocilic/vladocilic`, grana `main`. Ovdje su želje i sva komunikacija.
- **Aplikacija:** `vladocilic/deez-neurons`. Kod se mijenja samo na radnim granama tog repozitorija.
  Za rad na aplikaciji vrijedi i njezin `AGENTS.md`, osobito zaštita podataka.
- **Codex je glavni izvođač** i jedini uređuje kod i dokumentaciju aplikacije.
- **Claude je neovisni pregledavatelj** i ne uređuje aplikaciju.
- Zamjenu uloga može odrediti samo korisnik. Različite želje ne daju dopuštenje za paralelno uređivanje aplikacije.
- Oba agenta smiju u mapi `zelje/` sandučića dopisivati vlastite poruke i mijenjati polje `status`.
  To pregledavatelju ne daje pravo uređivanja koda ni dokumentacije aplikacije.

## Pokretanje agenata

GitHub čuva poruke, ali **ne pokreće** ni jednog agenta. Korisnik pokreće agenta porukom
„Provjeri sandučić na GitHubu". Na početku svakog pokretanja agent čita:
nove želje za sebe, vlastite želje u statusu `u-radu` ili `pitanje` i nove poruke upućene njemu.

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
