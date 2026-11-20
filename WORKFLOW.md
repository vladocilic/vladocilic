# Zajednička pravila rada (Claude i Codex)

Ovaj dokument vrijedi za **sve** AI agente koji rade na projektu These Neurons.
Vlasnik projekta komunicira na hrvatskom – pišite mu na hrvatskom.

## Izvor posla: mapa `zelje/`

- Svaka datoteka u `zelje/` (osim `_PREDLOZAK.md`) je jedna želja vlasnika.
- Na vrhu datoteke su polja `status`, `za` i `prioritet`.
- Uzimaj samo želje gdje je `za` tvoje ime (`claude` ili `codex`) ili `bilo-tko`.
- Redoslijed: prvo `prioritet: visok`, zatim po broju u nazivu datoteke.

## Tijek jedne želje

1. **Preuzmi:** promijeni `status: nova` → `status: u-radu`, a u
   „Bilješke agenta" upiši tko radi i datum. Commitaj to odmah, prije rada,
   da drugi agent ne uzme istu želju.
2. **Radi:** na zasebnoj grani `<agent>/<broj-zelje>-<kratki-opis>`,
   npr. `codex/003-tamni-nacin`.
3. **Nejasno?** Ne izmišljaj. Postavi `status: pitanje`, upiši pitanje
   u „Bilješke agenta" i stani.
4. **Završi:** u „Bilješke agenta" kratko (na hrvatskom) napiši što je
   napravljeno i kako to provjeriti, postavi `status: gotovo`.

## Pravila

- Nikad ne mijenjaj dio datoteke želje iznad crte `---` osim polja `status`.
- Ne preuzimaj želju koja je već `u-radu` kod drugog agenta.
- Ako tvoja promjena utječe na posao drugog agenta, zapiši to u bilješke.
- Ne briši želje; gotove ostaju kao povijest.
