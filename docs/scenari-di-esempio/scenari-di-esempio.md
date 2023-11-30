# Premessa

Di seguito la sequenza di operazioni da eseguire per ottenere l'aggiudicazione di un appalto nel settore ordinario sopra soglia scheda P1_16

# Esempi di flusso
## Pubblicazione procedura sopra soglia
Creazione e pubblicazione di una procedura sopra soglia con invio dell'avvisio di indizione al TED.
Schede utilizzate: P1_16  

### 1 Preparazione dati 

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
#### 2.3 Esito Operazione
 L'operazione di conferma è asincona e richiede un secondo accesso per ottere l'esito.
 Se la conferma va a buon fine esito-operazione consente di acquisire l'identificativo dell'avviso per il suo successivo uso nel payload dati 
#### Servizio:
..ServiziComuni/v2/esito-operazione?idAppalto=c88f5cb1-65ee-4ab4-ae35-d9e55e926697&tipoRicerca=ULTIMO_ESITO&tipoOperazione=AP_CONF
#### Payload:

#### Response:
```yaml

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
#### 2.3 Pubblica avviso
 Per richiedere la pubblicazione di una scheda di indizione è necessaria una chiamata esplicita al servizio pubblica avviso (in tutti gli altri casi il sistema pubblica automaticamente gli avvisi di pre e post informazione)
#### Servizio:
../PubblicaAvviso/v2/pubblica-avviso
#### Payload:
```yaml
{
    "idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179",
    "idAvviso": "75abbbb7-9720-46b2-afc2-51ca1cc6f498"
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
#### 2.3 Stato avviso
 La pubblicazione dell'avviso può richiedere uno o più giorni e il processo attraversa diversi stati.
 La condizione attuale può essere consultata con il servizio stato avviso
#### Servizio:
..//PubblicaAvviso/v2/stato-avviso?idAvviso=75abbbb7-9720-46b2-afc2-51ca1cc6f498
#### Payload:

#### Response:
```yaml
{
    "status": 200,
    "title": "OK",
    "detail": "Operazione Effettuata",
    "type": "about:blank",
    "statoAvviso": {
        "idAvviso": "75abbbb7-9720-46b2-afc2-51ca1cc6f498",
        "idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179",
        "idPianificazione": null,
        "dataControllo": "2023-11-21T15:15:03.620+00:00",
        "stato": {
            "idTipologica": "statoAvviso",
            "codice": "PUBB"
        }
    }
}
```

#### 2.3 Consulta avviso
 Il servizio restituisce maggiori dettagli sull'avviso e le informazioni relative alla pubblicazione dal parte del sistema TED e del servizio Pubblicita a Valore Legale (PVL) di ANAC
#### Servizio:
..//PubblicaAvviso/v2/stato-avviso?idAvviso=75abbbb7-9720-46b2-afc2-51ca1cc6f498
#### Payload:

#### Response:
```yaml
{
    "instance": null,
    "status": 200,
    "title": "OK",
    "detail": "Operazione Effettuata",
    "type": "about:blank",
    "avviso": {
        "idAvviso": "75abbbb7-9720-46b2-afc2-51ca1cc6f498",
        "idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179",
        "idPianificazione": null,
        "dataCreazione": "2023-11-28T20:34:54.898+00:00",
        "dataPubblicazione": null,
        "stato": {
            "idTipologica": "statoAvviso",
            "codice": "IN_ATT_PUBB"
        },
        "dataControllo": "2023-11-28T20:40:02.345+00:00",
        "azione": {
            "idTipologica": "tipoAzioneAvviso",
            "codice": "AZ_PUBB"
        },
        "datiPubblicazioneEU": {
            "noticeId": "37cb1871-6381-4a78-bd84-d7e77b93d448",
            "versionId": "01",
            "tipo": {
                "idTipologica": "tipoAvviso",
                "codice": "EU"
            },
            "stato": {
                "idTipologica": "statoAvviso",
                "codice": "IN_ATT_PUBB"
            },
            "dataControllo": "2023-11-28T20:40:02.345+00:00",
            "dataInoltroPubblicazione": "2023-11-28T20:40:03.964+00:00",
            "dataRicezionePubblicazione": "2023-11-27T22:00:00.000+00:00",
            "dataPubblicazione": null
        },
        "datiPubblicazioneIT": {
            "tipo": {
                "idTipologica": "tipoAvviso",
                "codice": "IT"
            },
            "stato": null,
            "dataControllo": null,
            "dataInoltroPubblicazione": null,
            "dataPubblicazione": null
        }
    },
    "scheda": {...omessa...},
    "appalto": {
        "idAppalto": "9d35c075-4316-46f5-aa5c-27fb111d0179",
        "codiceAppalto": "utilizzare un codice Univoco",
        "oggetto": "oggetto",
        "dataCreazione": "2023-11-28T20:14:53.592+00:00",
        "dataModifica": "2023-11-28T20:40:02.346+00:00",
        "stato": {
            "idTipologica": "statoAppalto",
            "codice": "IN_ATT_PUBB"
        }
    },
    "piano": null
}```
