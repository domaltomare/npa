# 1 Premessa

il RP predefinito è il soggetto che crea l’appalto.
- può cambiare con il servizio …
- può nominare delegati con il servizio

# 2 Interpretazione delle specifiche dell'orchestratore per la gestione del flusso 
La tabella di orchestrazione riporta, tra le altre, le indicazioni per gestire correttamente la sequenza di schede da inviare per le attività o il monitoraggio dell'appalto. Le informazioni da cosiderare sono le seguenti:
| Nome colonna | Descrizione |
| ---- | ---- |
| poubblicazioneTED | Il valore SI indica che l'eForm contenuta nella scheda verrà inviata al TED per la pubblicazione (la pubblicazione è richiesta dalla Stazione Appaltante mediante l'invocazione del servizio pubblicaAvviso.pubblica-avviso) |
| eForm | In questo campo è presente una lista di valori separata da virgola che indica i codici delle eForms. La scheda deve contenere una ed una sola eForma tra quelle previste |
| IncludeESPD| Il valore SI indica che la scheda deve contenere un documento ESPD request |
| pubblicazioneNazionale | Il valore SI indica che l'eForm contenuta nella scheda verrà inviata al TED per la pubblicazione (la pubblicazione è richiesta dalla Stazione Appaltante mediante l'invocazione del servizio pubblicaAvviso.pubblica-avviso) |
| schedaPreinformazione | Il valore è SI indica che la scheda riguarda la fase di preinformazione e non attiva un'istanza di appalto; la scheda è accettata esclusivamente dal servizio pianificazioneAppalto. Rientrano in questo ambito le comunicazioni relative alla costituzione di albi o elenchi di fornitori o gli avvisi che riducono i tempi di indizione della procedura di gara.  La conferma di una scheda non attiva il rilascio del CIG |
| schedaDiIndizione | Il valore è SI indica che la scheda riguarda la fase di pubblicazione e attiva un'istanza di appalto; la scheda è accettata esclusivamente dal servizio comunicaAppalto. **La conferma di una scheda può attivare il rilascio del CIG** |
| attribuisceCIG | Il valore SI indica alla conferma della scheda il sistema attribuirà un CIG per ogni lotto presente |
| schedaSuccessiva  | In questo campo è presente una lista di valori separata da virgola che indica i codici delle schede che possono o non possono essere trasmesse successivamente alla scheda stessa. Il valore "STATO FINALE" indica che non sono ammesse ulteriori trasmissione per la procedura; il valore "*" indica che la scheda attuale può essere seguita da qualunque altra scheda; l'operatore "!" seguito da schedaCodice indica che la scheda identificata schedaCodice non può essere trasmessa successivamente alla presente |
| flussoAppartenenza | Ogni procedura istanziata da una scheda di indizione appartiene al flusso codificato dalla scheda stessa. Le schede trasmesse successivamente alla scheda iniziale sono ammesse solo se appartenenti al medesimo flusso (con il simbolo ! vengono indicati i flussi ai quali la scheda non appartiene; con il simbolo * si indica che la scheda appartiene a qualunque flusso). Questa informazione è necessaria per stabilire quale tipologia di scheda può essere trasmessa successivamente ad una scheda appartenente al flusso * |
| flussoUscita | Se valorizzato indica che la trasmissione della scheda cambia il flusso di appartenenza della procedura |
| regole | In questo campo è presente una lista di valori separata da virgola che indica la successione di regole che vengono applicate alla scheda |
| dataInizio | Data dalla quale il sistema accetta questa versione della scheda |
| dataFine | Data dalla quale il sistema non accetta questa versione della scheda |

# 3 Esempi di flusso
## 3.1 Flusso tipo
il flusso di un appalto è essere organizzato come segue:

| Step | Descrizione | Servizio | Payload | Nota |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| 1 | Creazione di un bando o avviso di indizione| comunicaAppalto <br>operazioni:<br> <ul><li>crea-appalto</li><li>conferma-appalto</li></ul> |  Una delle schede dove schedaIndizione = "SI".||
| 2 | Pubblicazione di un bando o avviso di indizione| pubblicaAvviso <br>operazioni:<br> <ul><li>pubblica-avviso</li></ul> |||
| 3 | Comunicazione partecipanti | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | scheda S2 | |
| 4 | Comunicazione esito | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | | |
| 3 | Sottoscrizione del contratto | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | | |
| 4 | Inizio esecuzione | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | | |
| 5 | Monitoraggio esecuzione | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | | |
| 6 | Conclusione | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | | |

## 3.2 - scenari di esempio
Nei paragrafi successivi vengono affrontati i principali casi e gli scenari alternativi possibili nel flusso 

### 3.2.1 Richiesta CIG e pubblicazione su TED e sistema nazionale

### 3.2.1.2 Richiesta CIG e pubblicazione su sistema nazionale

### 3.2.2 Comunicazione dei partecipanti

### 3.2.3 Comunicazione di aggiudicazione

### 3.2.4 sottoscrizione del contratto e avvio dell'esecuzione

### 3.2.5 comunicazioni relative alla fase di esecuzione

### 3.2.6 conclusione del contratto

### 3.2.7 nuova istanza di contratto



# 4 accesso al FVOE
## 4.1 Richiesta accesso al FVOE

## 4.2 verifica documentazione presente

## 4.3 richiesta di nuovi documenti o aggiornamento dei documenti esistenti

