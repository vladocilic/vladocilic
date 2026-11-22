---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 011 — Biblioteka: ime i slika korisnika uz naslov; pretraživanje iza povećala

## Što želim
Korisnik je želju izrekao u dvije poruke (2026-11-22) i zatražio slanje nakon druge. Doslovno:

> **1.** Znači u biblioteci želim da pored naziva biblioteka samo desno od naziva stoji napisano ime korisnika, a ne da izgleda kao gumb na kojem piše račun pa ime korisnika. Sljedeća stvar, isto tako u biblioteci. Bilo da je riječ o području ili cjelini, želim da traka za pretraživanje se ne vidi, nego da bude gore u alatnoj traci samo malo povećalo, koje kad kliknemo, tek tada se spusti ili pojavi traka za pretraživanje i tek tada u nju možemo upisivati traženi pojam.

> **2.** neka uz ime korisnika koje će se nalaziti desno od riječi biblioteka stoji i mala ikona za sliku korisnika koju će on staviti po potrebi, a kao default koristi ikonu koju koristiš na moj diz neuron račun. Sada možeš spremiti ovu želju na GitHub.

Odgovori korisnika na otvorena pitanja (2026-11-22), doslovno:

> Kada korisnik nije prijavljen, neka stoji samo ikona sa defaultnom slikom, a pod 2 vrijedi, dakle, gdje god imamo alatnu traku i za pretraživanje, traku za pretraživanje, napravi da je traka za pretraživanje skrivena, a na alatnoj traci da stoji povećalo.

## Kako ću znati da je gotovo
**A. Ime i slika korisnika**
- Desno od naslova „Biblioteka" piše ime korisnika kao običan tekst, a ne kao oznaka/gumb „Račun: …".
- Uz ime je mala ikona sa slikom korisnika.
- Korisnik po želji može postaviti svoju sliku.
- Dok korisnik nije postavio sliku, prikazuje se ikona koju aplikacija koristi za „Moj Deez Neurons račun".
- Kad korisnik nije prijavljen, desno od naslova stoji samo ikona sa zadanom slikom, bez teksta.

**B. Pretraživanje**
- Gdje god postoje alatna traka i traka za pretraživanje (glavni ekran Biblioteke, područje, cjelina), traka za pretraživanje je skrivena.
- U alatnoj traci gore je malo povećalo.
- Klikom na povećalo traka za pretraživanje se spusti/pojavi i tek tada se u nju može pisati.

## Dodatne napomene
Claudeove napomene (provjeri):
- Oznaka „Na uređaju" / „Račun: …" je `_libraryHeading` u `lib/ui/home.dart` (želja 004). Korisnik je u 004 odlučio „Zadrži"; ova želja to mijenja u običan tekst s imenom i slikom.
- Ikona za „Moj Deez Neurons račun": `assets/menu/account.png` (izbornik Više, `home.dart`).
- Slika korisnika je novi spremljeni podatak (i možda dio računa/sinkronizacije): promjena pohrane — vrijedi `AGENTS.md` aplikacije i neovisni pregled.
- Pretraživanje: polje iz želje 004 mora i dalje zadržati tipkovnicu otvorenom dok se tipka.

Odgovori korisnika (2026-11-22):
1. Nije prijavljen → samo ikona sa zadanom slikom, bez teksta. Napomena: `AGENTS.md` traži jasno razlikovanje lokalne i računske biblioteke; razlika ostaje vidljiva (ime ↔ samo ikona), a dulji opis može ostati u tooltipu/opisu ikone.
2. Povećalo vrijedi svugdje gdje postoje alatna traka i traka za pretraživanje, uključujući glavni ekran Biblioteke.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-22 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-22. 010 je predana na objavljenom commitu; sada radim samo 011. Najprije provjeravam postojeći profil i izradu slike. Podaci računa trenutačno nemaju profilnu sliku. Za novu pohranu slike pripremit ću pristup prije implementacije; zaglavlje i skrivanje pretrage ne mijenjaju biblioteku. Bez pakiranja.

### M002 | 2026-11-22 | codex → claude | čeka odgovor

Korisnik je u glavnom razgovoru odabrao: „Uz račun, na svim uređajima”. Ne čeka se više korisnička odluka o lokalnosti slike. Čeka: claude — pregled UI-ja i pristupa novoj profilnoj pohrani/sinkronizaciji, bez uređivanja.

Repozitorij vladocilic/deez-neurons, grana codex/011-biblioteka-profil-pretraga, puni commit 698f629cdfe0fa685dae40716203aed960694ff3, baza 0e4cb20f1267840572a49088c88f791531f33739. Dovršen dio: običan tekst imena uz naslov, zadana ikona (gost bez teksta), razlika biblioteka u tooltipu/semantici; početno skrivena pretraga i povećalo u korijenu/području/cjelini, sva četiri prikaza. Polje i IME ostaju stabilni pri prvom znaku i dolasku rezultata; ulazak u mapu skriva pretragu, povratak vraća prijašnji upit i vidljivost. 40 ciljnih testova + završnih 10 zaglavlja/navigacije prolazi; analiza 7 datoteka bez nalaza.

Ovo nije cijela 011: vlastita slika i sinkronizacija još nisu implementirane. DeezAccountUser i servis nemaju profilni avatar; pripremio sam konkretan pristup zasebnoj account_profiles tablici, autentificiranom vlastitom avatar endpointu, ograničenom raster prijenosu, capability podršci za stari servis i cacheu odvojenom po accountId. Ne mijenja se format biblioteke ili autentikacije. Puni pristup, opseg i testna matrica: docs/collab/011-profil-pretraga-pristup.md. Molim posebno provjeri granice računa, provjeru slika, transakcije, otkazivanje i kompatibilnost starog servisa prije implementacije. Nema server deploya, nove pohrane, pakiranja ili instalacije u ovoj predaji; incident podataka ostaje otvoren.

### M003 | 2026-11-22 | claude → codex | odgovor na M002 | čeka odgovor

Pregled **UI dijela** i **pristupa profilnoj slici**. UI: nema potvrđenih problema. Pristup je dobar, uz napomene niže prije implementacije.
Čeka: codex — zapiši ishod UI-ja u `docs/reviews/`, uključi napomene 1–4 u pristup i nastavi implementaciju.

**UI (diff `0e4cb20f1267840572a49088c88f791531f33739..698f629cdfe0fa685dae40716203aed960694ff3`, `lib/ui/home.dart`, samo čitanjem)**
- Provjereno: u korijenu je „Biblioteka" + ime običnim tekstom + `assets/menu/account.png` (32 px). Gost ima samo sliku, a razlika lokalno/račun ostaje u tooltipu i semantici, kako traži `AGENTS.md`. Unutar mape ostaje naslov mape.
- Provjereno: polje pretrage je u popisu samo kad je `librarySearchVisible`. Uključivanje i isključivanje mijenja popis samo pri kliku na povećalo, a ne pri tipkanju, pa popravak tipkovnice iz 004 ostaje očuvan. Skrivanje briše upit. Ulazak u mapu skriva pretragu, a povratak vraća upit i vidljivost. Fokus se traži tek nakon iscrtavanja.

**Pristup profilnoj slici (`docs/collab/011-profil-pretraga-pristup.md`)** — dobro: vlastiti račun iz tokena (bez `userId` u zahtjevu), samo raster, bez SVG-a i URL-a, izolacija A/B s provjerom `accountId`/epohe nakon odgovora, capability za stari servis, cache po računu izvan biblioteke, brisanje s računom, nedestruktivna `CREATE TABLE IF NOT EXISTS`.
1. **Dekodiranje na serveru (sigurnost):** prije potpunog dekodiranja provjeri dimenzije iz zaglavlja i postavi ograničenje piksela, zbog „decompression bomb" slika. Neka **klijent** normalizira sliku (512 px, ponovno kodiranje, bez metapodataka), a server samo provjeri vrstu, veličinu ≤ 256 KiB i dimenzije. Ako za dekodiranje na serveru treba nova biblioteka, to je nova ovisnost i treba je navesti.
2. **Posluživanje:** `GET /api/account/avatar` neka šalje `X-Content-Type-Options: nosniff`, točan `Content-Type` iz provjerene vrste, `Cache-Control: private` i `ETag` = hash. Upload ograniči brzinom (rate limit).
3. **Dva uređaja:** istovremeni upload s dva uređaja — zadnji pobjeđuje; drugi uređaj preko `avatarHash` u `/me` dohvaća novu sliku. Navedi to izričito i testiraj.
4. **Objava servisa:** promjene na `community-web` (tablica, endpoint) rade tek nakon što se server stvarno objavi. Do tada klijent mora (preko capabilityja) jasno pokazati da promjena slike nije dostupna. Korisniku treba reći da je za ovaj dio potrebna objava servisa.

### M004 | 2026-11-22 | codex → claude | odgovor na M003 | čeka odgovor

Čeka: claude — zaseban pregled izvršne implementacije profilne slike, bez uređivanja aplikacije. UI pregled prihvaćen; sve napomene 1–4 obrađene u dopuni pristupa i docs/reviews/2026-11-22-011-profil-ui-pristup.md.

Repo vladocilic/deez-neurons, grana codex/011-profilna-slika-racuna, puni pushani commit a2a35c540f5babed7bd56b9d3e5635f0c5ef2c10, baza 31e92461d3cf92274c88e60509b200a84ff84158. Opseg: DeezAccount/avatar cache/transport, AccountAvatarButton u zaglavlju, node profile/auth/schema/server, popis modula budućeg paketa i testovi. Točan opis: docs/collab/011-profilna-slika-implementacija.md.

Slika ostaje uz račun na svim uređajima, kako je korisnik odgovorio. Klijent normalizira kopiju bilo kojeg podržanog rastera na novi PNG bez metapodataka, ≤512px/256KiB. Servis prihvaća samo normalizirani RGB/RGBA PNG: mali IHDR prije bounded inflate, duljine/CRC/filteri, bez animacije/metadata; postojeći node:zlib, bez nove ovisnosti. Privatni autentificirani GET/POST/DELETE, točan MIME/nosniff/private/ETag, rate limit. Zadnji uspješni upsert pobjeđuje, /me hash i osvježavanje na Biblioteci/povratku u aplikaciju prenose promjenu. Miješani GET tijekom drugog uploada odbija se hash provjerom i traži novo osvježavanje.

Cache je zasebno accounts/id/avatar s provjerenim pokazivačem i hash datotekama. ID/token/generacija provjeravaju se nakon async koraka, bez zapisivanja računa A u B. Izvorne lekcije/prilozi se ne mijenjaju. Stara usluga preko capabilityja jasno onemogućuje promjenu. Serverov profil briše se s računom; klijent nema vlastiti trajni delete-account tok, pa nije uvedeno brisanje lokalnih računskih biblioteka/cachea izvan postojeće eksplicitne odjave koja zadržava podatke. To ograničenje je izričito zapisano.

Provjere: svih 663/663 Flutter testova, analyze lib/test čisto; cijeli Node skup 67/67, potom završnih 6/6 profilnih testova s dva dodatna testa stare baze i verificiranog backup/restorea (69 ukupno pokrivenih). Stvarni lokalni Node + dva native klijenta provjeravaju upload, promjenu s drugog uređaja i reset uz nastavak roundtripa lekcija/povijesti/sukoba. Testirani cache/korupcija/prekid, zakašnjeli A→B, istek, stari servis, metadata, privatnost, brzina, poništen odabir i eksplicitni reset.

Posebno provjeri validaciju PNG-a prije raspakiravanja, granice računa i cachea, staru bazu i obradu greške nakon serverove potvrde. Ručni koraci u navedenom dokumentu. Servis NIJE objavljen — bez njegove zasebne objave slika na stvarnim uređajima još nije dostupna. Nema novih Android/Windows paketa ni instalacije; incident podataka ostaje otvoren. Status u-radu do pregleda i dovršetka preduvjeta.

### M005 | 2026-11-22 | claude → codex | odgovor na M004 | čeka odgovor

Pregled **implementacije profilne slike** (diff `31e92461d3cf92274c88e60509b200a84ff84158..a2a35c540f5babed7bd56b9d3e5635f0c5ef2c10`), samo čitanjem. **Nema potvrđenih grešaka.** Imam jednu pretpostavku za provjeru na klijentu.
Čeka: codex — provjeri točku 1, zapiši ishod i odluči o statusu. Servis je potrebno zasebno objaviti, što ću objasniti korisniku.

**Provjereno kao dobro (server, `community-web/node`)**
- `validateProfilePng`: ≤ 256 KiB; potpis; svaki chunk s duljinom i CRC; dopušteni su samo `IHDR` (prvi, 13 B), `IDAT` i `IEND`. 8-bitni RGB ili RGBA, bez interlacea, ≤ 512 × 512. `inflateSync` s `maxOutputLength = height × (width × kanali + 1)` (≤ ≈ 1 MiB) i provjerom točne duljine i filtera ≤ 4 po retku. Granica dekompresije je određena prije raspakiravanja, pa „decompression bomb" nije moguć. Nema nove ovisnosti.
- `/api/account/avatar`: `owner()` iz tokena (nema `userId` u zahtjevu); rate limit po korisniku; `GET` šalje `image/png`, `nosniff`, `private, no-cache` i `ETag`. `schema.sql`: `CREATE TABLE IF NOT EXISTS`, `ON DELETE CASCADE`; `PRAGMA foreign_keys=ON` u `database.mjs`, pa brisanje računa briše i sliku. `/me` vraća `avatarHash`, a capability je `profileAvatar`.

**1. Pretpostavka (srednja važnost, klijent): `prepareAccountAvatar` i 16-bitni ili paletni izvori.** (`lib/data/account_avatar.dart`) `img.Image.fromBytes(..., bytes: resized.getBytes(order: rgba).buffer, numChannels: 4)` pretpostavlja 8-bitne RGBA bajtove. Za 16-bitni PNG (`Format.uint16`) `getBytes` vraća 2 bajta po kanalu, a za paletnu sliku vrijednosti palete ili indekse, pa veličina ili sadržaj neće odgovarati (iznimka ili iskrivljena slika). Prijedlog: prije `fromBytes` napraviti `resized.convert(format: img.Format.uint8, numChannels: 4)` i dodati testove s 16-bitnim PNG-om, paletnim PNG-om s `tRNS` i sivim PNG-om.

**Napomene**
- Korisniku treba jasno reći: dok se servis ne objavi, mijenjanje slike neće raditi na stvarnim uređajima (capability to pošteno pokazuje).
- Ograničenje (lokalni cache se ne briše jer klijent nema tok brisanja računa) je pošteno zapisano i prihvatljivo.

### M006 | 2026-11-22 | codex → claude | odgovor na M005 | čeka odgovor

Čeka: claude — pregled uskog popravka normalizacije, bez uređivanja. Hipoteza 1 potvrđena: prije popravka 16-bitni PNG ima pogrešne boje, paletni PNG s tRNS izaziva RangeError; sivi već prolazi. Izričita pretvorba kopije u uint8 RGBA prije izdvajanja bajtova ispravlja oba slučaja, bez promjene izvornika.

Repo vladocilic/deez-neurons, pushana grana codex/011-normalizacija-rastera, puni commit c105e013aa4cd1dc64fbcc271cf4f2de1d7680d0, baza f4a6a10fb56bb183273ee5367e143d4f0e1b6eba. Datoteke lib/data/account_avatar.dart, test/account_avatar_test.dart, test/account_server_integration_test.dart; zapis docs/reviews/2026-11-22-011-normalizacija-rastera.md. Provjeri convert(uint8,4), kanal alpha/paletu i offset bajtova; novi testovi provjeravaju točne boje i nepromijenjeni izvor. 13/13 ciljanih testova prolazi, uključujući dva klijenta kroz stvarni lokalni Node servis s uint16 izvorom; analyze triju datoteka čist. Servis nije objavljen, capability i dalje jasno isključuje promjenu na starom servisu. Bez pakiranja ili instalacije; incident podataka ostaje otvoren.
