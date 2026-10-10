# Contenuti di Contatore

Questi file vengono scaricati dall'app **Contatore** a ogni apertura. Modificandoli si aggiornano
consigli, regole del riscaldamento ed eventi **senza pubblicare una nuova versione dell'app**.
Non contengono dati personali: qui va solo ciò che può vedere chiunque.

## eventi.json — eventi dell'OdV (calendario)

Le istruzioni e un esempio da copiare sono **dentro il file stesso**, nei campi `_come_si_compila` e
`_esempio_da_copiare` (l'app ignora i campi che iniziano con `_`).

### Aggiungere un evento dal sito di GitHub (anche da telefono)

1. Apri https://github.com/AlessioMauser/contatore-contenuti e accedi.
2. Clicca su **eventi.json**, poi sull'icona della **matita** (in alto a destra, "Edit this file").
3. Copia il blocco `_esempio_da_copiare` dalla `{` alla `}` compresa.
4. Incollalo dentro `"eventi": [ ]`, tra le parentesi quadre. Se c'è già un evento, separa i blocchi con una virgola.
5. Cambia i valori tra virgolette e aggiorna `"aggiornato"` con la data di oggi.
6. Clicca **Commit changes…**, scrivi due parole (es. "Sportello 12 novembre") e conferma.
7. Dopo circa un minuto il sito si aggiorna: alla prossima apertura l'app mostra l'evento nel calendario.

Esempio di lista con due eventi:

```json
 "eventi": [
  {
   "id": "2026-11-12-sportello-energia",
   "titolo": "Sportello energia",
   "inizio": "2026-11-12T18:00",
   "fine": "2026-11-12T19:30",
   "luogo": "Sala civica",
   "descrizione": "Porta le tue ultime bollette: ti aiutiamo a leggerle.",
   "link": "https://www.example.org/eventi/sportello"
  },
  {
   "id": "2026-11-26-incontro-bolletta",
   "titolo": "Incontro: leggere la bolletta",
   "inizio": "2026-11-26T21:00",
   "luogo": "Online"
  }
 ]
```

Regole:
- `id` unico e senza spazi; `titolo` e `inizio` obbligatori; gli altri campi facoltativi.
- Date `AAAA-MM-GGTHH:MM` in ora italiana; per un giorno intero solo `AAAA-MM-GG`.
- Attenzione a virgole e virgolette: se il file ha un errore l'app continua a usare la versione precedente.
  Per controllarlo incolla il testo su https://jsonlint.com prima di salvare.

## consigli.json — consigli

Ogni consiglio ha:
- `id` unico e stabile (l'app ricorda quali hai già visto o segnato "Lo faccio": non cambiarlo);
- `categoria`: `riscaldamento`, `raffrescamento`, `acqua`, `luce`, `gas`, `casa`, `auto`;
- `testo`: breve, concreto, in seconda persona;
- `quando` (facoltativo): `stagioni` (`inverno`, `primavera`, `estate`, `autunno`), `meteo` (`freddo`, `caldo`, `pioggia`),
  `riscaldamento` (`gas`, `pompa`, `stufa`, `teleriscaldamento`), `alimentazione` (`benzina`, `diesel`, `gpl`, `ibrida`),
  `cambio` (`manuale`, `automatico`);
- `fonte`: `nome` e `url` della pagina da cui viene il consiglio. **Ogni consiglio deve avere una fonte verificabile.**

## riscaldamento.json — periodi di accensione per zona climatica

Regole del DPR 74/2013 (art. 4). **Da ricontrollare ogni anno a settembre** e in caso di decreti d'emergenza:
aggiornare `verificato_il` e `prossima_verifica`.

## Come pubblicare una modifica

1. Modifica il file su GitHub (icona della matita) e salva con "Commit changes".
2. Dopo un minuto l'app, alla prossima apertura, scarica la versione nuova.
3. Se il file contiene un errore di formato l'app continua a usare l'ultima versione buona: controlla con un validatore JSON (es. jsonlint.com).
