#Concentrazione delle Persone nel 2015 a Roma
==========================================================================================

## Introduzione
---------------
Il progetto presentato si pone l'obiettivo di visualizzare l'affluenza delle persone nei vari luoghi di interesse durante tutto il corso del'anno 2015. La rappresentazione è stata creata il 3D utilizzando Three.js. Il progetto mostra una mappa attuale di roma, dei segmenti perpendicolari alla mappa che servono a puntare i vari luoghi per una più chiara visualizzazione ed infine 12 differenti livelli, uno per ogni mese, di colori differenti per distinguerli tra di loro (non presenti nella legenda), e distanziati in altezza.
Questi livelli sono formati da vari toroidi di raggio differente in base al count associato ad ogni luogo, estratto processando il database di foto pubblicate su instagram nell'arco dell'anno 2015.
Si trova inoltre sulla parte alta destra un controller con il quale si può interagire per selezionare un certo mese ed espandere quest'ultimo per giorni, così da avere una visione più granulare dei dati, per ottenere informazioni altrimenti non comprensibili da altre visualizzazioni.
E' presente anche una legenda, rappresentante i colori dei singoli giorni distinti, per una più chiara visione delle informazioni.

## Dataset
---------------
Il dataset dal quale sono state estratte le informazioni contiene circa 98000 fotografie recuperate da instagram dei vari luoghi di roma con ulteriori dati associati; tutti questi sono stati processati per ottenere delle strutture dati più snelle e chiare, utili per la visulizzazione che volevamo ottenere. Questa fase è stata fondamentale, visto che i dati dovevano essere poi processati in three.js il più velocemente possibile, così da diminuire il tempo di attesa dell'utente nel caricamento di tutti i dati. Sono così state studiate e create delle strutture ad hoc per migliorare l'efficienza e la velocità del programma. Sono così stati usati infine due file contenenti uno i dati con granularità mensile, mentre l'altro con granularità giornaliera.

## Implementazione
---------------
Nell'implementazione vengono prima definiti gli elementi di scena e settati i fattori di luce, luminosità e camera. Inizia poi la fase di processamento per mesi, che vengono visualizzati all'apertura del progetto; si accede così al file contenente tutte le informazioni precedentemente creato e si crea un oggetto "padre" per ogni mese; ad ognuno di questi oggetti vengono attaccati tanti figli quanti sono i luoghi visitati in quel mese, ognuno con una certa posizione definita dalla latitudine e longitudine del posto e con una certa grandezza, definita usanfo una funzione logaritmica, così da far comunque vedere i luoghi con un count piccolo, e non far apparire enormi i luoghi con un count grande. Tutti questi oggetti vengono poi attaccati alla scena in posizioni diverse così da meglio distinguerli.

![Mappa con visione "per mesi"](ProjectInfiVis/screenshot/progetto1.jpg)
------------------

Viene poi configurato un controller che prìermette di decidere quale tra i mesi presenti vogliamo espandere per meglio visualizzare i dati; quando viene selezionato un mese, il programma rimuove dalla scena l'oggerro "padre" per quel mese e ne aggiunge uno nuovo, al quale vengono aggiunti tutti i luoghi suddivisi per giorni in quel mese. I vari colori e l'altezza differenziano i vari giorni tra di loro per ogni singlolo posto, inoltre la grandezza dei toroidi identifica la differenza dei count per ogni giorno. Oltre a questo, sopra ogni luogo viene creata una scritta in 3D con il nome del luogo, per meglio riconoscerlo; infine ogni segmento verticale che identifica il luogo nella mappa, cambia colore, rispetto a quello univoco che si ha rispetto alla visualizzazione per mesi, così da distinguere i luoghi del mese selezionato da quello degli altri mesi, se i luoghi sono troppo vicini. Sono state aggiunte anche delle piccole particolarità per una migliore navigazione e visualizzazione delle informazioni: per prima cosa, selezionando i mesi alti la camera cambia puntamento e guarda l'oggetto appena aggiunto così che ci si può focalizzare sul mese selezionato.Inoltre, altra cosa che viene modificata è la posizione del piano con la mappa, che si alza in base al mese scelto, così che si riesce a capire la posizione dei luoghi anche per i mesi che stanno più in alto nella rappresentazione.
Quando da un mese, poi, se ne seleziona un altro, grazie alla memoria del mese precedentemente aperto, si ripristina la visualizzazione "per mese" del mese prima espanso, e si apre quella del mese scelto.

![Mappa con visione "per giorni"](ProjectInfiVis/screenshot/progetto2.jpg)
------------------
![Mappa con visione "per giorni"](ProjectInfiVis/screenshot/progetto3.jpg)
------------------

## Conclusioni
---------------
Il sistema così sviluppato, ci permette una visualizzazione dei dati su più livelli di granularità, così da poter confrontare i dati sotto più punti di vista; Grazie poi all'espansione "per giorni" è stato possibile notare informazioni che altrimenti non avremmo potuto notare: per esempio luoghi che essendo vicini spazialmente ed avendo per alcuni giorni un afflusso di un certo tipo, ci possono far pensare ad un movimento di un flusso di persone da una parte ad un'altra; inoltre la trovata di visualizzare i giorni della settimana suddivisi per colori, ci ha permesso invece di notare luoghi in cui l'afflusso avviene solo in certi giorni, come magari il sabato o la domenica, ed altri in cui l'afflusso è costante tutti i giorni
