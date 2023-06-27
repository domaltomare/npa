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
## 3.1 Flusso minimale
Il flusso per la comunicazione dei dati relativi ad una procedura prevede, nel caso più essenziale, i passi seguenti:

| Step | Descrizione | Servizio | Payload | Nota |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| 1 | Creazione di un bando o avviso di indizione| comunicaAppalto <br>operazioni:<br> <ul><li>crea-appalto</li><li>conferma-appalto</li></ul> |  Una delle schede dove schedaIndizione = "SI".| Tutte le schede di indizione prevedono l'invio di un documento ESPD di tipo request, nel caso si tratti di una procedura oltre la soglia europea è necessaria la trasmissione della eForm coerente con il tipo di procedura scelto. L'operazione conferma-appalto esegue implicitamente anche l'operazione verifica-appalto e una volta terminata assegna un CIG ad ogni lotto indicato nella scheda di indizione.|
| 2 | Pubblicazione di un bando o avviso di indizione| pubblicaAvviso <br>operazioni:<br> <ul><li>pubblica-avviso</li></ul> | L'identificativo dell'avviso ottenuto allo step 1 | Il sistema effettua la pubblicazione a livello nazionale e, se si tratta di una procedura di importo superiore alla soglia comunitaria, verso il TED nelle modalità previste |
| 3 | Comunicazione partecipanti | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | scheda S2 | La scheda S2 contiene l'elenco delle offerte presentate in gara e il dettaglio dei partecipanti. L'invio della scheda attiva le funzioni erogate dal servizio FVOE per gli Operatori Economici riportati in elenco. Nel caso di procedura ristretta la scheda S2 è preceduta dalla S1 che riporta l'elenco delle manifestazioni di interesse |
| 4 | Comunicazione esito | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | Una delle schede previste per la fasi: "affidamento", "aggiudicazione" | L'invio di una scheda di mancata aggiudicazione NAG1, NAG2 termina la procedura |
| 3 | Sottoscrizione del contratto | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | Scheda SC1 | La scheda di sottoscrizione del contratto attiva la fase di esecuzione. La scheda SC1 può essere inviata più volte nel ciclo di vita dell'appalto, ogni invio genera una linea contrattuale separata e indipendente dalle altre. Questa funzionalità consente di gestire ad esempio: la sottoscrizione di un nuovo contratto a seguito di rescissione di uno precedente; la sottoscrizione di più contratti di esecuzione, anche simultanei con il medesimo o più fornitorei distinti. |
| 4 | Inizio esecuzione | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | Scheda I1 per l'inizio dell'esecuzione o scheda CO1 per la comunicazione di chiusura anticipata | Ogni scheda I1 è associata alla corrispondente scheda SC1 che riporta i dati contrattuali |
| 5 | Monitoraggio esecuzione | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | Una qualsiasi scheda della fase di esecuzione | Ogni scheda relativa alla fase di esecuzione è associata alla corrispondente scheda SC1 che riporta i dati contrattuali |
| 6 | Conclusione | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | CO1 | Ogni scheda CO1 è associata alla corrispondente scheda SC1 che riporta i dati contrattuali. Alla scheda CO1 segue la comunicazione dell'esito del collaudo ove previsto CL1 |

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

