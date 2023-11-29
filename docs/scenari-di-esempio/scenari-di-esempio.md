# 1 Premessa

Di seguito la sequenza di operazioni da eseguire per ottenere l'aggiudicazione di un appalto nel settore ordinario sopra soglia scheda P1_16

# 2 Esempi di flusso
## 2.1 Pubblicazione procedura sopra soglia
Creazione e pubblicazione di una procedura sopra soglia con invio dell'avvisio di indizione al TED.
Schede utilizzate: P1_16  

### 2.1.2 Preparazione dati 

```yaml 
{"idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179"} 
```

| Sezione | Modifica |
| ---------- | ---------- |
| anacForm | <ul><li> modificare o aggiungere le informazioni identificative della Stazione appaltante in $.scheda.body.anacForm.stazioniAppaltanti <br> si può scegliere di modificare la SA presente (cf 11111111115) o aggiungere una nuova SA. Quella presente è la SA di test in uso presso ANAC </li> <li> modificare scheda.body.anacForm.appalto.codiceAppalto inserendo un valore univoco </li> </ul>|
|	eForm |<ul><li>	modifica notice-id inserendo un valore univoco </li> <li> modifica issueDate inserendo la data corrente </li> </ul> <br> per l'aggiornamento della eForm vedi file eForm16.xml. Il file modificato deve essere codificato Base64 e inserito nel campo scheda.eForm della scheda |

### 2.1.2 Sequenza operazioni

| Step | Descrizione | Servizio | Payload | Response |
| ------------- | ------------- | ------------- | ------------- | ------------- |
| 1 | Creazione di un avviso | ../ComunicaAppalto/v2/crea-appalto/ |  P1_16.json | {<br>"status": 200,<br>"title":"Operazione Effettuata",<br>"detail": "Creazione eseguita con successo",<br>"type": "about:blank",<br>"idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179"<br>}|
| 2 | Conferma avviso <br> Ad esito positivo dell'operazione il sistema assegna i CIG ai lotti  | ../ComunicaAppalto/v2/crea-appalto/ | {<br> "idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179" <br>} <br> Identificativo ottenuto allo step 1 | '''json {"idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179"} ''' <br> Il sistema effettua la pubblicazione a livello nazionale e, se si tratta di una procedura di importo superiore alla soglia comunitaria, verso il TED nelle modalità previste |
| 3 | Comunicazione partecipanti | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | scheda S2 | La scheda S2 contiene l'elenco delle offerte presentate in gara e il dettaglio dei partecipanti. L'invio della scheda attiva le funzioni erogate dal servizio FVOE per gli Operatori Economici riportati in elenco. Nel caso di procedura ristretta la scheda S2 è preceduta dalla S1 che riporta l'elenco delle manifestazioni di interesse |
| 4 | Comunicazione esito | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | Una delle schede previste per la fasi: "affidamento", "aggiudicazione" | L'invio di una scheda di mancata aggiudicazione NAG termina la procedura |
| 3 | Sottoscrizione del contratto | comunicaPostPubblicazione <br>operazioni:<br> <ul><li>crea-scheda</li><li>conferma-scheda</li></ul> | Scheda SC1 | La scheda di sottoscrizione del contratto attiva la fase di esecuzione. La scheda SC1 può essere inviata più volte nel ciclo di vita dell'appalto, ogni invio genera una linea contrattuale separata e indipendente dalle altre. Questa funzionalità consente di gestire ad esempio: <br> <ul><li>la sottoscrizione di un nuovo contratto a seguito di rescissione di uno precedente;</li><li> la sottoscrizione di più contratti di esecuzione, anche simultanei con il medesimo o più fornitorei distinti.</li> |
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

