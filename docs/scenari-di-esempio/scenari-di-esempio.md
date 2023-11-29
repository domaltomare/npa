# Premessa

Di seguito la sequenza di operazioni da eseguire per ottenere l'aggiudicazione di un appalto nel settore ordinario sopra soglia scheda P1_16

# Esempi di flusso
## Pubblicazione procedura sopra soglia
Creazione e pubblicazione di una procedura sopra soglia con invio dell'avvisio di indizione al TED.
Schede utilizzate: P1_16  

### 1 Preparazione dati 

```yaml 
{"idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179"} 
```

| Sezione | Modifica |
| ---------- | ---------- |
| anacForm | <ul><li> modificare o aggiungere le informazioni identificative della Stazione appaltante in $.scheda.body.anacForm.stazioniAppaltanti <br> si può scegliere di modificare la SA presente (cf 11111111115) o aggiungere una nuova SA. Quella presente è la SA di test in uso presso ANAC </li> <li> modificare scheda.body.anacForm.appalto.codiceAppalto inserendo un valore univoco </li> </ul>|
|	eForm |<ul><li>	modifica notice-id inserendo un valore univoco </li> <li> modifica issueDate inserendo la data corrente </li> </ul> <br> per l'aggiornamento della eForm vedi file eForm16.xml. Il file modificato deve essere codificato Base64 e inserito nel campo scheda.eForm della scheda |

### 2 Sequenza operazioni
#### 2.1 Creazione di un avviso
#### Servizio:
../ComunicaAppalto/v2/crea-appalto/
#### Payload:
P1_16.json
#### Response:
```yaml
{
  "status": 200,
  "title":"Operazione Effettuata",
  "detail": "Creazione eseguita con successo",
  "type": "about:blank",
  "idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179"
}
```
#### 2.2 Conferma di un avviso
 Ad esito positivo dell'operazione il sistema assegna i CIG ai lotti. 
#### Servizio:
../ComunicaAppalto/v2/conferma-appalto
#### Payload:
```yaml
{
    "idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179"
}
```
#### Response:
```yaml
{
    "status": 200,
    "title": "OK",
    "detail": "Richiesta acquisita",
    "type": "about:blank"
}
```
#### 2.3 Recupero CIG assegnati ai lotti
 L'operazione consente di acquisire i codici CIG per il loro futuro uso nel payload dati 
#### Servizio:
../ComunicaAppalto/v2/recupera-cig?idAppalto=9d35c075-4316-46f5-aa5c-27fb111d0179
#### Payload:

#### Response:
```yaml
{
    "status": 200,
    "title": "OK",
    "detail": "Operazione eseguita con successo",
    "type": "about:blank",
    "totRows": 1,
    "totPages": 1,
    "currentPage": 1,
    "elementPage": 20,
    "result": [
        {
            "cig": "J00003C9C1",
            "lotIdentifier": "LOT-0001"
        }
    ]
}
```
#### 2.3 Esito Operazione
 L'operazione consente di acquisire l'identificativo dell'avviso per il loro futuro uso nel payload dati 
#### Servizio:
..ServiziComuni/v2/esito-operazione?idAppalto=c88f5cb1-65ee-4ab4-ae35-d9e55e926697&tipoRicerca=ULTIMO_ESITO&tipoOperazione=AP_CONF
#### Payload:

#### Response:
```yaml
