# Istruzioni per Claude — Sistemi Automatici 3BETC 26-27

Progetto LaTeX per il materiale scolastico di Alessio (verifiche, soluzioni,
esercizi a casa, lezioni, dispense). Si usa su **Overleaf**, collegato a questo
repo. Il materiale lo prepara Claude; Alessio imposta un file come
*Main document* e compila. Lui non deve mai modificare codice LaTeX.

## Regole fisse
- **Percorsi dalla radice del progetto** (Overleaf compila dalla radice):
  `\input{Banca_Esercizi/...}`, `\usepackage{stili/verifica}`. Mai `../`.
- **Un file = un PDF.** Ogni PDF ha il suo file da impostare come Main document.
  Il contenuto sta in un solo file (`contenuto_verifica.tex` /
  `contenuto_esercizi.tex`); i file numerati impostano solo
  `\fila` (A | B | C) e `\versione` (testo | soluzioni | correzione | completa).
- **Solo bianco e nero** (la stampa a scuola è B/N): niente colori.
- **Template generico**: niente nomi di scuola, classe, anno o materia reali
  nei modelli (`*_AAAA_MM_GG_Materia_Classe`). Nelle copie reali sì.
- **Verifica = un foglio fronte/retro**: testo al massimo su 2 pagine; tabella
  punti e griglia voti sempre in fondo alla 2ª pagina (`\riepilogo`).
- Niente spazi per rispondere né domande a crocette: solo esercizi di calcolo.
- **Risultati non "tondi"**: scegli dati che costringono ad arrotondare.
  Il catalogo e la versione `completa` segnano con [!] i risultati con
  ≤ 2 cifre significative: non ce ne devono essere.
- Tre file A, B e C equivalenti per difficoltà: `\dato{nome}{vA}{vB}{vC}`.
  Evita arrotondamenti ambigui (es. 202,5 o 12,25 a 3 cifre).
- **Le tre file non sono identiche**: stessa difficoltà ma con varianti (es. una dà
  una corrente, un'altra scambia serie/parallelo o dà una grandezza con un'incognita).
  Nel file: `\dato{..}{vA}{vB}{vC}` (0 dove il dato non c'è), `\soloFila{A}{\calcola...}`
  per i calcoli di una sola fila, `\ABC{testoA}{testoB}{testoC}` per testo, figura,
  richieste e soluzioni, `\criterioABC{A}{B}{C}` per i criteri.
- Durata della prova mai scritta sul foglio (`\durata{}` vuoto). Sul foglio niente
  scritte sotto l'intestazione (no `\obiettivi`, no `\istruzioni`), niente riga grossa.
- Disegno: resistori a rettangolo col nome dentro (`\resV`, `\resH` in `stili/comune.sty`),
  correnti segnate **sul filo** (`\corV`/`\corH`), tensione data con `\segniV`/`\segniH`
  (+, − e nome). Segna in figura solo le I e V richieste in "Trovare" e i dati.
- Nodi: lettere A, B, C… (senza E, in ordine alfabetico senza salti) su tutti i nodi
  (`\nodo`, `\etich`); tensione su un solo resistore = $V_k$ col numero del resistore,
  su gruppi = coi nodi ($V_{BC}$); i nodi tra due resistori in serie non si nominano;
  la corrente in un ramo in serie prende il nome del primo resistore incontrato.
- Struttura di un esercizio: `\begin{esercizio}[N]` (punteggio totale, niente `\part`);
  sotto "Esercizio N" va direttamente la riga **Dati:** (rientro allineato dopo i due
  punti), senza testo introduttivo che dia suggerimenti; poi la figura; poi eventuale
  richiesta di legge/maglia in una riga; infine `\trovare{$I_1$\pt{1}, $V_2$\pt{2}}`.
- "Trovare" elenca solo 3-4 grandezze (finali o chiave, senza testo): i passaggi
  intermedi vanno fatti comunque. I punti (`\pt`) NON compaiono nel testo del compito
  ma solo nella versione completa e nei criteri della correzione (passaggi non elencati
  valutati se presenti).
- Circuiti: simboli europei; generatore `to[vsource, l=$V$, n=G]` + `\morsetti{G}`.
- Niente versioni DSA: eventuali parti da togliere le decide Alessio.
- Negli esercizi veri tutto deve essere corretto e coerente: la soluzione usa
  solo simboli già introdotti nel testo, dati e risultati verificati.
- Soluzioni per gli studenti senza criteri; criteri solo con `\criterio{}`
  (finiscono nella griglia di correzione).

## Regole per Sistemi Automatici 3BETC
- Argomenti finora: sistema binario (conversioni), diagrammi di flusso, porte logiche.
  Solo argomenti già fatti a lezione.
- Struttura della verifica (appunti di Alessio del 20/10/2026), 46 pt:
  1) decimale → binario (4 numeri, 8 pt), 2) binario → decimale (4 numeri, 8 pt), 3) diagramma di flusso con
  due decisioni (8 pt), 4) diagramma di flusso con ciclo senza vettori (10 pt), 5–6) 3 ingressi e 2 porte
  logiche in cascata (6+6 pt). Esempio: `Compiti/Verifica_2026_10_24_Sistemi_3BETC/`.
- Conversioni: più numeri per esercizio (4, disposti 2×2, `a)`–`d)`), testo come negli appunti
  `$173_{10} = \ldots_2$`; decimali a **3 cifre** (8–10 bit), binari da 8 a 10 bit (risultato decimale < 1024);
  **un solo numero pari** per esercizio; le tre file con gli stessi numeri di bit. 2 pt per numero.
  Soluzione: tabella delle divisioni per 2 con i resti / somma delle potenze di 2.
- Qui i risultati sono numeri interi o tabelle: niente `\calcola`/[!]; i risultati attesi
  delle tre file vanno scritti nei criteri (`\criterioABC`), così compaiono nella correzione.
- Diagrammi di flusso: stili in `stili/comune.sty` (`fcterm` inizio/fine, `fcio` Leggi/Scrivi,
  `fcinit` inizializzazione (esagono allungato: tutte le assegnazioni iniziali, es. $L \gets 0$),
  `fcproc` elaborazione, `fcdec` decisione, `fcfreccia`, etichette Sì/No); assegnazione con
  $\gets$; ramo Sì a destra, ramo No in basso; il ciclo torna sopra la decisione da sinistra.
  Consegna come il 4.A: frase di contesto + "Disegna il diagramma di flusso di un algoritmo che ..."; righe **Dati da leggere:** e **Altre variabili:** (nome = significato); poi la regola e cosa visualizzare. Senza suggerimenti sulla soluzione.
  **Niente vettori** (non li conoscono): nei cicli niente "leggi N valori"; un solo gruppo di
  dati letti e variabili aggiornate nel ciclo. **Nel testo si danno i nomi di tutte le variabili**
  (dati, risultati, contatori: es. livello $L$, secchi $N$, contatore $i$).
  **Niente tempo** nei cicli ("ogni minuto"): il ciclo gira alla velocità del clock; il contatore
  conta operazioni (secchi versati, spedizioni), non minuti.
- Porte logiche: simboli americani (`american and port`, `or`, `nand`, `nor`) dentro
  `circuitikz` con `scale=1.25,transform shape`; ingressi $A$, $B$, $C$, uscita $Y$; l'uscita
  intermedia NON si segna (né in figura né in tabella). **Solo tabella di verità** (8 righe): le espressioni logiche non sono ancora state
  spiegate. Per renderla meno meccanica: pallini di negazione sugli ingressi (`circle` su
  `g.bin k`) e/o in uscita (NAND, NOR); nelle soluzioni si ridisegna il circuito sopra
  la tabella ($A$, $B$, $C$, $Y$); l'uscita della prima porta solo nei criteri, per il docente.
- Soluzioni: niente note che rimandano al testo o a figure che nelle soluzioni non compaiono.
- Le file A, B, C hanno esercizi diversi ma di pari difficoltà (`\ABC{...}{...}{...}`).

## Nuova verifica
1. Copia `Compiti/Verifica_AAAA_MM_GG_Materia_Classe/` in
   `Compiti/Verifica_2026_10_27_NomeMateria_3A/` (data, materia, classe).
2. Nei file numerati (`1_…` – `7_…`: 3 testi, 3 soluzioni, 1 correzione) aggiorna il percorso dell'ultima riga.
3. In `contenuto_verifica.tex` compila i dati (materia, argomento, classe, ...)
   e inserisci gli esercizi: dalla banca con `\input{Banca_Esercizi/...}`,
   o nuovi dentro `\begin{esercizio}...\end{esercizio}`.
4. Gli esercizi nuovi e riusabili vanno anche in `Banca_Esercizi/<materia>/`
   (partendo da `_MODELLO_esercizio.tex`) e in `catalogo_esercizi.tex`.
5. Compila tutte le versioni dalla radice e controlla: testo ≤ 2 pagine,
   nessun `VERIFICA-TONDO`/`VERIFICA-PAGINE` nel log, risultati corretti.

Esercizi a casa: stessa procedura con `Esercizi_X_Casa/Esercizi_AAAA_MM_GG_Materia_Classe/`.

## Lezioni
Una lezione = `Lezioni/lezioni/AAAA-MM-GG_argomento.tex`, che inizia con
`\input{Lezioni/_inizio}` e `\lezione[note]{gg/mm/aaaa}{argomento}`, e finisce con
`\input{Lezioni/_fine}`. Va aggiunta anche a `Lezioni/main_Lezioni.tex` (registro).
Le lezioni vengono dagli appunti scritti a mano (PDF di Samsung Notes) di Alessio:
trascrivili fedelmente, con data e classe.

## Compilare in locale per verifica
Dalla radice del repo: `latexmk -pdf -outdir=/tmp/out <file>.tex`.
Non fare commit di PDF o file ausiliari (vedi `.gitignore`).
