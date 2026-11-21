---
status: nova          # nova | u-radu | pitanje | gotovo
za: codex             # claude | codex | bilo-tko
prioritet: srednji    # visok | srednji | nizak
---

# 006 — Gumb „Uvezi područje, cjelinu ili lekciju" premjestiti u Izradu

## Što želim
Korisnikove riječi (2026-11-21), doslovno:

> Gumb koji se nalazi u biblioteci, koji je u vezi područje, cjelinu ili lekciju, treba biti premješten u izradu, odmah ispod izradi područje, cjelinu ili lekciju.

## Kako ću znati da je gotovo
- Gumba „Uvezi područje, cjelinu ili lekciju" više nema u Biblioteci.
- U sekciji „Izrada" taj se gumb nalazi odmah ispod gumba za novo područje, cjelinu i lekciju.

## Dodatne napomene
Claude je gumb prepoznao kao „Uvezi područje, cjelinu ili lekciju" (`lib/ui/library_creation.dart`), jer je to nakon želje 002 jedini preostali gumb u Biblioteci s tim natpisom. Nakon 002 uvoz je ostao u Biblioteci (`showImport: false` u Izradi).
Korisnik je istu stvar spomenuo već u trećoj rečenici želje 002. Ondje je pogrešno protumačena kao ponavljanje druge rečenice, pa ova želja to ispravlja.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta
