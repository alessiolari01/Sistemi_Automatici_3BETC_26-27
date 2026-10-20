# Template Didattica (Overleaf)

Su Overleaf tutti i percorsi partono dalla **radice del progetto**: un file in
`Compiti/.../contenuto_verifica.tex` scrive `\input{Banca_Esercizi/...}` e non `../Banca_Esercizi/...`.
Per compilare un file: *Menu → Main document* e scegli il file.

```
stili/                 stili condivisi (non si compilano)
  comune.sty           pacchetti comuni: siunitx all'italiana, circuitikz europeo, grigi
  appunti.sty          Dispensa e Lezioni (frontespizio, formulario, \lezione)
  verifica.sty         Verifiche ed Esercizi a casa (file A/B/C, soluzioni, punti)
Banca_Esercizi/        BANCA ESERCIZI: un file = un esercizio
  _MODELLO_esercizio.tex
  catalogo_esercizi.tex   compila per vedere tutta la banca con le soluzioni
  elettrotecnica/...
Dispensa/              teoria per argomento (capitoli/, figure/)
Lezioni/               un file per lezione (AAAA-MM-GG_argomento.tex), dati.tex, registro
Compiti/               una cartella per verifica, Verifica_AAAA_MM_GG_Materia_Classe
Esercizi_X_Casa/       una cartella per consegna, stessi esercizi della banca
```

## Come si ottiene un PDF
**Un file = un PDF.** Apri il file che ti serve, *Menu → Main document* (o
"Imposta come main document"), ricompila. Non si tocca codice.

| Cosa                                   | File da impostare come Main document                    |
|----------------------------------------|---------------------------------------------------------|
| Verifica, testo Fila A / B / C         | `Compiti/<verifica>/1_Testo_FilaA`, `2_Testo_FilaB`, `3_Testo_FilaC` |
| **Soluzioni per gli studenti**         | `4_Soluzioni_FilaA`, `5_Soluzioni_FilaB`, `6_Soluzioni_FilaC` |
| **Griglia di correzione** (per te)     | `7_Correzione`                                          |
| Esercizi a casa                        | `Esercizi_X_Casa/<consegna>/1_Testo`, `2_Soluzioni`, `3_Correzione` |
| Una sola lezione                       | `Lezioni/lezioni/AAAA-MM-GG_argomento`                  |
| Registro di tutte le lezioni           | `Lezioni/main_Lezioni`                                  |
| Dispensa                               | `Dispensa/main_Dispensa`                                |
| Catalogo della banca esercizi          | `Banca_Esercizi/catalogo_esercizi`                            |

Il contenuto di una verifica sta in **un solo file** (`contenuto_verifica.tex`):
i file numerati scelgono solo la versione, così testo, soluzioni e correzione
sono sempre coerenti. Per una nuova verifica si copia la cartella e si aggiorna
il percorso nell'ultima riga dei file numerati.

Nota: su Overleaf il PDF scaricato prende il nome del progetto, non del file.

- **Soluzioni per gli studenti**: solo "Esercizio n" e la sua soluzione, senza
  testo, punti né criteri. Una per fila.
- **Griglia di correzione**: un solo foglio per tutte e tre le file. Per ogni
  esercizio: punti, risultati attesi fila A, B e C affiancati, criteri di
  correzione; in fondo la griglia punteggio → voto.
- Ogni verifica sta in **un foglio fronte/retro**: tabella punti e griglia voti
  vanno sempre in fondo alla 2ª pagina. Se sfora, nel log compare `VERIFICA-PAGINE`.
- "Pagina 1 di 2" e "continua sul retro" compaiono solo se gli esercizi
  arrivano sulla 2ª pagina (la tabella punti non conta). Per questo gli esercizi
  vanno scritti dentro `\begin{esercizio}...\end{esercizio}`.
- Classe e A.S. sono in alto a sinistra: se li lasci vuoti restano righe da compilare.
- La versione completa ha i criteri di correzione e una pagina finale di
  **controllo risultati A/B**: i risultati troppo "tondi" sono segnati con `[!]`
  (e nel log compare `VERIFICA-TONDO`).

## Scrivere un esercizio
Parti da `Banca_Esercizi/_MODELLO_esercizio.tex`:
- `\dato{R1}{150}{180}{220}`: valori per la fila A, B e C (in unità base: `2.2e3`).
- `\calcola{Req}{\x{R1}+\x{R2}}`: il risultato viene calcolato da solo per tutte e tre le file.
- `\mis{Req}{\ohm}`: stampa con il prefisso giusto (`2,2 kΩ`, `41,4 mA`).
- `\criterio{...}` dentro la soluzione: come assegni i punti (finisce nella
  griglia di correzione, mai nelle soluzioni per gli studenti).
- Generatore con simbolo europeo: `to[vsource, l=$V$, n=G]` e poi `\morsetti{G}`
  per i segni + e − (il + va verso il punto di arrivo del `to`).
- Ricordati di aggiungere l'esercizio a `catalogo_esercizi.tex`.
