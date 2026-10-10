# Contenuti di Contatore

Questi file vengono scaricati dall'app **Contatore** a ogni apertura. Modificandoli si aggiornano
consigli, regole del riscaldamento ed eventi **senza pubblicare una nuova versione dell'app**.
Non contengono dati personali: qui va solo ciò che può vedere chiunque.

## eventi.json — eventi dell'OdV (calendario)

```json
{
 "versione": 1,
 "aggiornato": "2026-10-10",
 "eventi": [
  {
   "id": "sportello-2026-10-15",
   "titolo": "Sportello energia",
   "inizio": "2026-10-15T18:00",
   "fine": "2026-10-15T19:30",
   "luogo": "Sala civica",
   "descrizione": "Porta le tue bollette: ti aiutiamo a leggerle.",
   "link": "https://…"
  }
 ]
}
```

- `id` deve essere unico (va bene data + nome).
- Le date sono nel formato `AAAA-MM-GGTHH:MM`, ora italiana. `fine`, `luogo`, `descrizione` e `link` sono facoltativi.
- Gli eventi passati si possono lasciare: l'app mostra solo quelli futuri e del mese.

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
