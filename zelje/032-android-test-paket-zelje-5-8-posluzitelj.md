---
status: nova
za: codex
prioritet: visok
---

# 032 — Android testni paket, zatim Želje 5 i 8 i aktivacija poslužitelja

## Što želim
Korisnikove riječi (28. 11. 2026.): „Kada kodeks završi i javi se, reći ćeš mu da mi zapakira za Android, da mogu probati na mobitelu, i onda ćeš mu reći da nastavi sa ostalim željama, sa svim ovim što smo rekli, 5, 8, aktivacija poslužitelja, nazive liga ćemo zadržati za sada.”

Redoslijed:
1. **Android testni paket** s prihvaćenim izmjenama želja 1–4, 6 i 7 (031, izvršni commit `dea243867a1d57a8b10158300033796846a2429e`), da ga korisnik isproba na mobitelu. Prema `AGENTS.md` aplikacije: paket je **testni/dijagnostički**. Incident podataka je otvoren, pa ga ne predstavljati kao sigurnu nadogradnju i jasno navesti što nije provjereno. Korisniku dati **punu lokaciju APK-a**.
2. **Želje 5 i 8** iz `vladocilic/deez-neurons`, grana `claude/zelje`, `docs/ZELJE.md`. Korisnik je 28. 11. 2026. dao **posebnu dozvolu** za njihovu izvedbu (oznaka „NE IZVODITI BEZ POSEBNE DOZVOLE” time je ispunjena). Izvesti prema dogovorenom modelu u tim željama, posebno:
   - gradivo se dijeli **datotekom s oznakom grupe** (WhatsApp / e-pošta, „Podijeli s grupom”), a poslužitelj **ne sprema lekcije**, nego samo grupe, članstva, popis gradiva (naslov, verzija, datum) i malu statistiku,
   - nova verzija lekcije zadržava napredak; oznake „Nemaš ovu lekciju” i stare verzije; crveni brojčanici obavijesti,
   - statistika za voditelja, pristanak, „Ime za mene” i dodatna pravila iz Želje 5,
   - **odbačeno:** način „provjera znanja” se ne radi.
   Raditi u fazama. Prije koda predložiti plan faza u ovoj želji. Promjene formata `.flashcard`, pohrane, prijave i sinkronizacije traže **neovisni pregled** (Claude).
3. **Aktivacija javnog poslužitelja** (Hostinger Node.js, HTTPS, `DEEZ_DATA_DIR`, Google prijava, SMTP), prema `docs/ACCOUNTS.md`. Pripremiti sve što se može bez korisnika. Za korake koji traže korisnikove račune i pristupe (Hostinger hPanel, Google konzola, e-pošta) dati korisniku jasne korak-po-korak upute i stati. Ništa ne objavljivati bez korisnikove potvrde.

**Ne raditi:** nazive liga (korisnik ih zadržava za kasnije).

## Kako ću znati da je gotovo
- Dobio sam punu lokaciju Android APK-a i mogu ga isprobati na mobitelu.
- Želje 5 i 8 su izvedene po fazama i pregledane.
- Poslužitelj je aktiviran nakon mojih koraka i grupe rade između dva stvarna mobitela.

## Dodatne napomene
- Zaštita podataka (`AGENTS.md`) ima prednost pred svim ostalim.
- Bez paralelnog uređivanja istih datoteka.

---
<!-- Ispod ove crte piše agent. -->
## Bilješke agenta

### M001 | 2026-11-28 | claude → codex | informacija

Upisano na izravan korisnikov nalog u Claudeovu razgovoru. Izvor dogovora i detalja: `deez-neurons` `claude/zelje:docs/ZELJE.md` (Želje 5 i 8, sa svim nadopunama od 27. i 28. 11.). Korak 1 (Android paket) radi se prvi i ne čeka korake 2–3.

### M002 | 2026-11-28 | claude → codex | informacija

**Korisnikova izmjena (28. 11. 2026., 00:32): sada raditi SAMO korak 1, Android testni paket.** Paket sadrži prihvaćene želje 1–4, 6 i 7 iz 031 i služi za probu na mobitelu. Prema `AGENTS.md` mora biti označen kao testni/dijagnostički, jer je incident podataka otvoren. Korisniku dati punu lokaciju APK-a.

Koraci 2 (Želje 5 i 8) i 3 (aktivacija poslužitelja) **čekaju korisnikovu novu uputu**. Ne započinjati ih ni planom dok korisnik ne kaže.
