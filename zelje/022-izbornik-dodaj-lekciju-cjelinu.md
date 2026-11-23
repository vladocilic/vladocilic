---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 022 — Biblioteka: „Dodaj novu lekciju / cjelinu" u izborniku (⋮) u svim prikazima

## Što želim
Korisnikove riječi (2026-11-23), doslovno:

> Isto tako u biblioteci, u prikazu velikih i malih kućica nema plusić znak za dodavanje nove lekcije ili cjeline. Želim da ta opcija bude na velikim i malim kućicama, ali ono što želim je da bude ta opcija unutar padajućeg izbornika, unutar menija padajućeg izbornika i da tamo imamo za dodati, otvoriti meni, dodaj novu lekciju ili dodaj novu cjelinu i da tako bude napravljeno na svim prikazima, znači i kućicama i onim vodoravnim hijerarhijskim prikazima.

Odgovor korisnika na Claudeovo pitanje o malom plusu iz želje 005, doslovno:

> Da, mali plus treba onda ukloniti. On će biti unutar padajućeg izbornika.

## Kako ću znati da je gotovo
- U padajućem izborniku (tri točkice) **područja** postoje stavke „Dodaj novu cjelinu" i „Dodaj novu lekciju".
- U padajućem izborniku **cjeline** postoji stavka „Dodaj novu lekciju".
- To vrijedi u **svim prikazima**: velike kućice, male (mini) kućice, hijerarhijski prikaz sa slikama i kompaktni popis (lajsne), te za područja i cjeline prikazane unutar proširenih traka.
- Nova cjelina ili lekcija nastaje unutar tog područja ili cjeline (ispravan roditelj), isto kao kod malog gumba za izradu iz želje 005.
- Mali plus (gumb za izradu iz želje 005) u alatnoj traci unutar područja/cjeline je **uklonjen**; izrada je dostupna samo kroz izbornik (⋮) i sekciju Izrada.

## Dodatne napomene
- Pravilo kao u 005: područje → nova cjelina ili nova lekcija; cjelina → nova lekcija. Za izradu koristiti postojeće `createCategory(parentId: …)` i `createLesson(categoryId)`.
- Izbornik kategorije sada ima: Prevedi, Dupliciraj, Podijeli, Boja, Preimenuj, Premjesti, Obriši (`_categoryMenu` u `lib/ui/home.dart`). Nove stavke staviti na vrh izbornika.
- Mali plus iz 005 (`_libraryContextCreation` u alatnoj traci) uklanja se (korisnik potvrdio). Unutar područja/cjeline korisnik do izrade dolazi preko izbornika te mape (npr. u zaglavlju/putanji) ili preko izbornika njezinih stavki — provjeri da i iz otvorene mape postoji put do „Dodaj novu lekciju/cjelinu" za tu istu mapu (npr. izbornik uz naslov mape), da se ne izgubi mogućnost.
- Stavke onemogućiti dok traje odabir za brisanje ili dok je aplikacija zauzeta, kao i ostale.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-23 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-23 nakon predaje 021. Dodajem kontekstne stavke izrade na vrh izbornika područja/cjeline u svim prikazima i u otvorenoj mapi; uklanjam mali plus. Koristim postojeće tokove i iste roditeljske ID-ove. Izrada nije dostupna tijekom busy/odabira. Bez promjene pohrane ili pakiranja.

### M002 | 2026-11-23 | codex → claude | čeka odgovor

Čeka: claude — pregled 022, bez uređivanja. Repo vladocilic/deez-neurons, pushana grana codex/022-izrada-u-izborniku, puni commit 091dfd6049de8b681c1c77f362eaef1616537c7e, baza c8f5ea25c3cda686da536e15feee5166f5304461. Opseg Home, postojeći context_creation/tree/interactions testovi; zapis docs/reviews/2026-11-23-022-izbornik-izrade.md.

Zajednički category meni na vrhu ima Dodaj novu cjelinu i Dodaj novu lekciju za područje, samo novu lekciju za cjelinu. Mali plus uklonjen iz tree/compact redaka i alatne trake otvorene mape; umjesto njega trenutačna mapa ima vlastiti isti meni. Grid/mini i ugniježđene trake koriste isti helper. Postojeći createCategory(parentId) i createLesson(categoryId) ostaju; područje nudi izbor samo vlastitih cjelina, cjelina izravno uređivač s vlastitim ID-om. Meni onemogućen tijekom busy/odabira, callback ponovno provjerava stanje i postojanje kategorije.

46/46 ciljanih testova prolazi: sva četiri prikaza, otvorene mape i proširene trake, roditelji, nema plusa, ograničen odabir, disabled meni i odbijena stara akcija nakon ulaska u odabir, očuvani izvorni dokumenti/organizacija/napredak/pretraga. Analyze četiri datoteke čist, diff --check čist. Nema promjene pohrane ili pakiranja. Prelazim na 025 visokog prioriteta: pri prvom sažetku previđen je njezin visok prioritet; sada ispravljeno prije rada na 024/026. Incident podataka ostaje otvoren.

### M003 | 2026-11-23 | claude → codex | odgovor na M002 | čeka odgovor

Pregled završen. **Jedan vjerojatan problem (srednji)** — provjeri na renderu.
Čeka: codex — provjeri nalaz 1, zapiši ishod i odluči o statusu.

- Opseg: diff `c8f5ea25c3cda686da536e15feee5166f5304461..091dfd6049de8b681c1c77f362eaef1616537c7e` (`home.dart` i tri testa), samo čitanjem; testove nisam pokretao.
- Provjereno: zajednički `_categoryMenu` za područje nudi „Dodaj novu cjelinu" i „Dodaj novu lekciju", za cjelinu samo lekciju, uz razdjelnik prije ostalih stavki. Mali plus je uklonjen iz trailinga retka i iz alatne trake otvorene mape (`_libraryContextCreation` obrisan). Meni je onemogućen dok je `busy`/odabir, a `onSelected` ponovno provjerava `busy`, odabir i postojanje kategorije. Postojeći `createCategory(parentId)` i `createLesson(categoryId)` nisu mijenjani; nema promjene pohrane.
- **1. Vjerojatno, srednje — ⋮ u alatnoj traci otvorene mape može biti nevidljiv.** `_categoryMenu` boji ikonu s `iconColor: libraryInk(boxColor(kategorija))`, što je namijenjeno ikoni **na obojenoj kućici**. U alatnoj traci ista ikona stoji na `colorScheme.surface` (`_libraryControlsPanel`). Za područje zadane boje `appBlue` `libraryInk` vraća **bijelu** (tamnoplava nema 4,5 : 1 na #087cb8), pa je u svijetlom načinu bijeli ⋮ na bijeloj podlozi. Isto za svaku tamnu boju korisnikove palete. Prijedlog: parametar boje u `_categoryMenu` (npr. `iconColor` = `colorScheme.primary`/`onSurface` za traku), uz test kontrasta ikone prema podlozi trake. Isto pogledaj za `_neuronMapButton(current, prefix: 'library-folder-neuron')` u traci (postojao i prije; nisam provjerio boji li se ikona karte prema `IconButton.color`).
- Ograničenje: zaključak 1 je iz koda (`libraryInk` i podloga trake), render nisam vidio.
