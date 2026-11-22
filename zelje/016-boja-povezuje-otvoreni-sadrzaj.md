---
status: u-radu          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 016 — Boja otvorene kućice povezuje je s njezinim cjelinama/lekcijama

## Što želim
Korisnikove riječi (2026-11-22), doslovno:

> Kada tapnemo na kućicu područja ili cjeline, nekako dole se otvore lekcije ili cjeline, a da ne znam točno s kojom je povezano, sa kojom cjelinom ili područjem. Znači, ako sam tapnuo na cjelinu i dole vidim lekcije, ne mogu jasno vidjeti da su te lekcije povezane s tim područjem. Možeš li dati neku ideju kako da to riješimo?

> Bi li mogli nekako od odabrane kućice spustiti njenu boju dole prema cjelinama ili lekcijama, tako da ta boja povezuje cjeline s područjem ili lekcije s cjelinama?

Na Claudeov prijedlog (skica u prilogu, natpis u traci da/ne, okomita traka u prikazu lajsni) korisnik je odgovorio: „Odgovori su točno kako si rekao, da, za drugo bez natpisa i za treće isto da."

## Skica
[`slike/016-skica-most-boje.png`](slike/016-skica-most-boje.png) — gruba Claudeova skica ideje (natpis „Cjeline u: Fizika" na skici korisnik **ne** želi).

## Kako ću znati da je gotovo
**Prikaz kućica (i mini kućica)**
- Kad strelicom proširim područje ili cjelinu, ispod njezine kućice spušta se „most" u njezinoj boji, iste širine kao kućica, sve do trake s njezinim cjelinama/lekcijama.
- Traka ispod je iste boje, pa kućica, most i traka čine jedan povezan obojeni oblik (kao jezičac mape), sa zaobljenim prijelazima.
- Ostale kućice u istom redu ostaju odvojene, pa se jasno vidi koja je otvorena.
- Isto se ponavlja na svakoj razini: otvorena cjelina unutar trake spušta svoju boju do svojih lekcija.
- Bez natpisa u traci; povezanost se vidi samo bojom.

**Prikaz lajsni (i kompaktni popis)**
- Cjeline/lekcije otvorenog područja ili cjeline imaju s lijeve strane okomitu traku u boji roditelja, pa se vidi kome pripadaju.

## Dodatne napomene
- Odnosi se na proširivanje strelicom u Biblioteci (želje 004/009). Tap na kućicu i dalje otvara mapu (vidi 014, M004).
- Boje moraju ostati čitljive i u tamnom načinu (012); tekst i ikonice na obojenoj traci trebaju dovoljan kontrast.
- Mali gumbi bez bijele podloge (015).

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-22 | codex → claude | informacija

Vlasnik: codex. Preuzeto 2026-11-22, nakon predaje 015. Pročitana je cijela želja i pregledana skica 016-skica-most-boje.png. Izvodim most iste širine/boje od otvorene kućice do njezine trake, bez natpisa, za kućice i mini kućice; u lajsnama/kompaktnom prikazu lijevu traku stvarne boje roditelja, uključujući ugniježđene razine. Horizontalno pomicanje trake mora pomicati i sidro mosta. Ne mijenjam hijerarhiju, boje u pohrani, lekcije ili napredak. Bez pakiranja.
