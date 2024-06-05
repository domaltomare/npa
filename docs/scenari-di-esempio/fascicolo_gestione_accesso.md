# Premessa

Di seguito la sequenza di operazioni da eseguire per accedere al FV dell'OE per la successiva verifica dei requisiti  

## Richiesta di Accesso al Fascicolo dell'OE

La SA può richiedere l'accesso al fascicolo se non ha mai eseguito la richiesta o se questa é stata NEGATA o REVOCATA dall'OE o se é in stato SCADUTA.
Non vengono accettate più richieste di autorizzazione per uno stesso fascicolo già autorizzato o su cui é in attesa di risposta da parte dell'OE 

La richiesta di accesso se validata genera una notifica verso il FE dell'OE. 

### 1 Preparazione dati 
| ModelloDati | Modifica |
| ---------- | ---------- |
| RichiestaAccessoRequest | <ul><li> $RichiestaAccessoRequest.dataInizioAutorizzazione inserire obbligatoriamente la data inizio di validita dell'autorizzazione. il Valore deve essere maggiore o uguale alla data odierna</li> <li>$RichiestaAccessoRequest.dataFineAutorizzazione. Inserire facoltativamente la data fine di validità. In caso di mancata valorizzazione si assume una data fittizia 2099/12/31 indicante che la richiesta di accesso non ha scadenza</li> <li> $RichiestaAccessoRequest.operatoriEconomici.$AnagraficaOEType.codiceFiscale. Inserire obbligatoriamente almeno un CF dell'OE di cui si richiede l'accesso al Fascicolo. <br> Nella stessa richiesta é possibile richiedere l'accesso verso più OE per lo stesso appalto.<br> Il CF dell'OE inserito DEVE essere precedentemente inviato come Partecipante/Aggiudicatario in una delle seguenti schede: S1, S2, S4, RSU1, AD1_25, AD1_26, AD1_27, AD1_28, AD2_25, AD2_26, AD2_27, AD2_28, AD2_29, AD3, AD4 e AD5. Per i test può essere utilizzato il codice fiscale 11111111113.</li><li> $RichiestaAccessoRequest.idAppalto inserire obbligatoriamente l'idAppalto su cui si vuole eseguire la verifica della documentazione dell'OE</li></ul>|

### 2 Invocazione servizio 
#### Servizio:
../FVC/v2/richiesta-accesso-fvoe/
#### Payload:
```yaml
{
  "dataInizioAutorizzazione": "2024-06-05T12:02:05Z",
  "dataFineAutorizzazione": "2025-06-05T12:02:05Z",
  "operatoriEconomici": [
    {
      "codiceFiscale": "1111111113"
    },
    {
      "codiceFiscale": "80140110588"
    }
  ],
  "appalto": {
    "idAppalto": "4f8f5660-87e8-4dbb-b325-17e216f4a519"
  }
}
```
#### Response:
```yaml
{
  "status": 200,
  "title": "Operazione Effettuata",
  "detail": "Richiesta acquisita",
  "idRichiesta": "f81d4fae-7dec-11d0-a765-00a0c91e6bf6"
}
```
## Verifica Stato Richiesta di Accesso al Fascicolo dell'OE
L'autorizzazione può richiedere diversi giorni. Se entro un mese la richiesta non viene autorizzata/negata dall OE questa passa in stato 05 - SCADUTA. 
### 1 Preparazione dati 
| ModelloDati | Modifica |
| ---------- | ---------- |
| Parameters | <ul><li> $codiceFiscale  Inserire obbligatoriamente il CF dell'OE di cui si é richiesto l'accesso al Fascicolo</li> <li>$idAppalto.inserire obbligatoriamente l'idAppalto di cui si é eseguita la richiesta di accesso al fascicolo </li> </ul>|

### 2 Invocazione servizio 
#### Servizio:
../FVC/v2/verifica-richiesta-accesso-fvoe/
#### Payload:
```yaml
codiceFiscale : "1111111113"
idAppalto : "f81d4fae-7dec-11d0-a765-00a0c91e6bf6"
```
#### Response: Richiesta in Attesa di essere autorizzata
```yaml
{
  "status": 200,
  "title": "Operazione Effettuata",
  "autorizzazione": {
    "idAutorizzazione": "1789c793-bdbe-4e8c-aa7e-4117145c739b",
    "dataInizio": "2022-01-23T12:02:05Z",
    "dataFine": "2023-01-23T12:02:05Z",
    "operatoreEconomico": {
      "codiceFiscale": "1111111113"
    },
    "appalto": {
      "idAppalto": "4f8f5660-87e8-4dbb-b325-17e216f4a519"
    },
    "stato": {
      "codice": "01",
      "descrizione": {
        "it": "Richiesta"
      }
    },
    "richiestaAccesso": {
      "idRichiesta": "f81d4fae-7dec-11d0-a765-00a0c91e6bf6"
    },
  }
}
}
```

#### Response: Richiesta Autorizzata
```yaml
{
  "status": 200,
  "title": "Operazione Effettuata",
  "autorizzazione": {
    "idAutorizzazione": "1789c793-bdbe-4e8c-aa7e-4117145c739b",
    "dataInizio": "2022-01-23T12:02:05Z",
    "dataFine": "2023-01-23T12:02:05Z",
    "operatoreEconomico": {
      "codiceFiscale": "1111111113"
    },
    "appalto": {
      "idAppalto": "4f8f5660-87e8-4dbb-b325-17e216f4a519"
    },
    "stato": {
      "codice": "02",
      "descrizione": {
        "it": "Autorizzato"
      }
    },
    "motivo": "",
    "autorizzante": {
      "codiceFiscale": "4f8f5660-87e8-4dbb-b325-17e216f4a519"
    },
    "richiestaAccesso": {
      "idRichiesta": "f81d4fae-7dec-11d0-a765-00a0c91e6bf6"
    },
    "chiaveAccesso": "dafc5f6f-227c-4788-a523-72aa5244f649"
  }
}
}
```
