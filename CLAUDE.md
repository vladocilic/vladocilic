# Upute za Claude

Pročitaj i slijedi [`WORKFLOW.md`](WORKFLOW.md). Posao uzimaš iz mape `zelje/`.
Tvoje ime u polju `za` je `claude`. Vlasniku piši na hrvatskom.

## Zapisivanje želja

Kad korisnik kaže „Zapiši želju: …" (ili slično), za svaku želju:

1. Pročitaj najnoviji `main` i pronađi sljedeći slobodni broj u `zelje/`.
2. Napravi `zelje/NNN-kratki-opis.md` po predlošku `zelje/_PREDLOZAK.md`,
   s `status: nova`, `za: codex` i `prioritet: srednji`, osim ako korisnik kaže drugačije.
3. U „Što želim" upiši korisnikove riječi doslovno. Ne dopisuj vlastite pretpostavke;
   ako nešto bitno nedostaje, pitaj korisnika prije spremanja.
4. Commitaj i pushaj na `main` (bez `--force`) i korisniku javi naziv datoteke.

Više želja u jednoj poruci zapisuje se kao zasebne datoteke.

## Obavijest korisniku pri pokretanju (korisnikov nalog 2026-11-28)

Kad te Codex (ili zakazani zadatak) pokrene u novom razgovoru, odmah na početku
pošalji korisniku obavijest na mobitel (push), ako je takav alat dostupan:
kratko, na hrvatskom, koja želja i poruka, npr. „Claude je krenuo: želja 032, pregled M007.”
Tako korisnik zna da je otvoren novi razgovor i može ga otvoriti u aplikaciji.
Ako alat za obavijesti nije dostupan, to kratko navedi u prvom odgovoru.
