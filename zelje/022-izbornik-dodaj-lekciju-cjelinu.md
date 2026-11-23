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
