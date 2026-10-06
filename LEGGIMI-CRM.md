# DVDRescue 1.5.0 — collegamento al CRM

DVDRescue parla con il CRM Tastiere Digitali con **le stesse API di VHSCapture** (`/api/cattura/*`),
con il suo tipo di lavoro: **i DVD da recuperare**, cioè il blocco «Riversaggio / Backup» della scheda
quando il supporto è **DVD** (quantità = quanti dischi).

## Come si collega
1. Nel CRM: Controllo PC → 🔑 della postazione → copia il token (lo stesso di VHSCapture su quel PC va bene).
2. In DVDRescue: ⚙ nella banda in alto → indirizzo del CRM, token, «Prova collegamento», Salva.

## Come lavora
- **Estrai** → se il collegamento è attivo chiede **per quale cliente**: le schede con DVD ancora da recuperare;
  in cima «▶ Continua con …» se c'era un lavoro aperto.
- Durante l'estrazione nella Coda del CRM compare «📀 PC · Rossi · recupera il DVD 1º di 2».
- A fine estrazione: **Fatto, conta** (un DVD recuperato) · **Scarta** (il disco non si recupera: il totale scende,
  il prezzo si ricalcola) · **Non contare**. Annullato o errore → non si conta niente.
- I DVD recuperati contano anche nel totale dei supporti della scheda: finiti tutti (cassette + DVD) la scheda
  diventa «pronta» nel CRM. **🔢 Conteggio** corregge fatti/totali.
- Se la rete salta, gli eventi restano in coda su disco e partono da soli.
