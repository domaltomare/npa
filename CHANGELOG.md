<details>
<summary><h1>Note di rilascio del 22/09/2023</h1></summary>

## Modello Dati
* modello-dati-tipologiche.yaml:
  * creato un nuovo oggetto TipologicaSchemaErroriType
  * modificato l'attributo $ref dell'oggetto ErroriEnum per estendere il nuovo schema dati ($ref: '#/components/schemas/TipologicaSchemaErroriType')
* modello-dati-npa.yaml:
  * aggiunta nuova scheda SQ1
  * aggiunti gli attributi idNuovaScheda e idNuovoAvviso in EsitoOperazioneType
      
### Regole
* A1_29.dmn, A1_30.dmn, A1_31.dmn, A1_32.dmn, A1_33.dmn, A1_34.dmn, A1_35.dmn, A1_36.dmn, A1_37.dmn, A2_29.dmn, A2_30.dmn, A2_31.dmn, A2_32.dmn, A2_33.dmn, A2_34.dmn, A2_35.dmn, A2_36.dmn, A2_37.dmn, A3_1.dmn, A3_2.dmn, A3_3.dmn, A3_4.dmn, A3_5.dmn, A3_6.dmn,M1_38.dmn, M1_39.dmn, M1_40.dmn, M2_38.dmn, M2_39.dmn, M2_40.dmn:
  * aggiunte nuove regole
* AD1_25.dmn, AD1_26.dmn, AD1_27.dmn, AD1_28.dmn, AD2_25.dmn, AD2_26.dmn, AD2_27.dmn, AD2_28.dmn, AD3.dmn, P1_10.dmn, P1_11.dmn, P1_12.dmn, P1_13.dmn, P1_16.dmn, P1_17.dmn, P1_20.dmn, P1_21.dmn, P2_10.dmn, P2_11.dmn, P2_12.dmn, P2_13.dmn, P2_16.dmn, P2_17.dmn, P2_20.dmn, P2_21.dmn, P3_4.dmn:
  * regola REG7 corretto il messaggio con art. 140 co. 10 D. Lgs. 36/2023
    
### Schede
* modello-dati-schede-dati-comuni.yaml:
  * modificato l'oggetto StazioneAppaltanteType rendendo tutti i campi obbligatori tranne funzioniSvolte
  * modificato l'oggetto AggiudicazioneA1_31Type rendendo il cig obbligatorio
  * modificato l'oggetto ModificaContrattualeType togliendo lotIdentifier
  * modificato l'oggetto ModificaContrattuale_40Type togliendo lotIdentifier
  * modificato l'oggetto AggiudicazioneA7Type togliendo il lotIdentifier e inserendo il cig obbligatorio
  * modificato l'oggetto AppaltoA7Type togliendo l'idAppalto
  * aggiunto all'oggetto AppaltoP4BaseType il campo boolean costituzioneSocietaDiScopo obbligatorio
  * modificato il format datetime in date-time su tutti gli oggetti
  * modificato l'oggetto DatiTerminiInvioType: oraScadenzaPresentazioneOfferte diventa date-time
  * modificato l'oggetto DatiBaseTerminiInvioSoloOraType: oraScadenzaPresentazioneOfferte diventa date-time
  * eliminati gli oggetti MisurePremialiType, MotivoDerogaType, LingueType, TipologiaLavoroType, CondizioniNegoziataType
  * modificato l'oggetto ParitaDiGenereGenerazionaleType: l'attributo misurePremiali diventa array di MisurePremialiEnum e motivoDeroga diventa array di MotivoDerogaEnum
  * modificato l'oggetto DatiBaseDocumentiType: l'attributo lingue diventa array di LingueEnum
  * modificati gli oggetti LottoP_10Type, LottoP_11Type, LottoP_15Type,	LottoP_16Type, LottoP_17Type, LottoP_19Type,  LottoP3BaseType, LottoP6BaseType, LottoP4BaseType,LottoP7BaseType: l'attributo tipologiaLavoro diventa array di TipologiaLavoroEnum
  * modificati gli oggetti LottoBaseType, LottoP4BaseType, LottoP7BaseType: l'attributo condizioniNegoziata diventa array di CondizioniNegoziataEnum
  * modificato l'oggetto DatiBaseAccessibilitaType: il campo accessibilita non è più array, secondo quanto indicato nel ted con la sdk 1.8.0
  * modificati gli oggetti PrestazioniEnum, TipoRealizzazioneContrattoEnum, FunzioniDelegateEnum, GiustificazioneAggiudicazioneDirettaEnum, EsitoProceduraEnum, GiustificazioneEsitoProceduraEnum, MotiviModificaContrattualeEnum, MotiviVariazioneAnagraficaEnum, MotiviInterruzioneEnum, TipologiaComunicazioneEnum: rinominato il riferimento al json
  * modificati gli oggetti InvitatoType, DatiPersonaGiuridicaType, AggiudicatarioType, AggiudicatarioA1_35Type, PartecipanteType, PartecipanteADType, SoggettoType: rinominato l'attributo tipo in tipoOE
  * modificato l'oggetto PrestazioneType: rinominato l'attributo tipo in tipoSoggetto
  * modificato l'oggetto FinanziamentoType: rinominato l'attributo tipo in tipoFinanziamento	 
* modello-dati-schede-P3.5.yaml:
  * l'attributo condizioniNegoziata diventa array di CondizioniNegoziataEnum
* modello-dati-schede-A2.31.yaml, modello-dati-schede-A3.5.yaml, modello-dati-schede-A3.6.yaml:
  * reso il cig obbligatorio
* modello-dati-schede-A3.3.yaml:
  * modificato il format datetime in date-time
* modello-dati-schede-AD3.yaml:
  * reso il lotidentifier obbligatorio
* modello-dati-schede-AD4.yaml:
  * reso il lotidentifier obbligatorio
  * modificato il format datetime in date-time
* modello-dati-schede-CL1.yaml:
  * tolto l'idcontratto dall'oggetto CollaudoType e inserito nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-CO1.yaml, modello-dati-schede-CO2.yaml:
  * tolto l'idcontratto dall'oggetto ConclusioneType e inserito nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-I1.yaml:
  * tolto l'idcontratto dall'oggetto DatiInizioType e inserito nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-NAG.yaml:
  * reso obbligatorio il cig e i lotti
* modello-dati-schede-SC1.yaml:
  * tolto l'idcontratto dall'oggetto DatiContrattoType
  * modificato il format datetime in date-time
* modello-dati-schede-RI1.yaml:
  * aggiunto l'attributo incidenzaCronoprogramma
  * eliminato l'array sospensioni e inserito l'elemento sospensione.
  * tolto l'idcontratto dall'oggetto sospensioneType. inserito l'idscheda nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-SQ1.yaml:
  * aggiunta nuova scheda di superamento del quarto del tempo contrattuale
* modello-dati-schede-AC1.yaml:
  * eliminato l'array accordiBonari e inserito l'elemento accordoBonario.
  * tolto l'idcontratto dall'oggetto AccordoBonarioType e inserito nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-IR1.yaml:
  * eliminato l'array ritardi e inserito l'elemento ritardo.
  * tolto l'idcontratto dall'oggetto RitardoType e inserito nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-S2.yaml:
  * modificato il format datetime in date-time
* modello-dati-schede-RSU1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto.
  * tolto l'idcontratto dall'oggetto subappaltotype e inserito nell'anacForm
* modello-dati-schede-CS1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto.
  * tolto l'idcontratto dall'oggetto subappaltotype e inserito nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-ES1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto.
  * tolto l'idcontratto dall'oggetto subappaltotype. aggiunto l'idScheda nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-S3.yaml, modello-dati-schede-S4.yaml:
  * tolto lotidentifier. reso il cig obbligatorio
* modello-dati-schede-SA1.yaml:
  * eliminato l'array avanzamenti e inserito l'elemento avanzamento.
  * tolto l'idcontratto dall'oggetto avanzamentotype e inserito nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-SO1.yaml:
  * eliminato l'array sospensioni e inserito l'elemento sospensione.
  * tolto l'idcontratto dall'oggetto sospensioneType e inserito nell'anacForm
  * modificato il format datetime in date-time
* modello-dati-schede-SU1.yaml:
  * eliminato l'array sospensioni e inserito l'elemento sospensione.
  * tolto l'idcontratto dall'oggetto sospensioneType e inserito nell'anacForm 
* modello-dati-schede-P3.3.yaml:	
  * modificata label cigAccordoQuadro in cigAccordoQuadroConvenzione
* modello-dati-schede-P6.3.yaml, modello-dati-schede-P6.4.yaml, modello-dati-schede-P6.5.yaml, modello-dati-schede-P6.6.yaml:
  * file eliminati
  
### Tipologiche
* errori.json:
  * corretto con art. 140 co. 10 D. Lgs. 36/2023
  * inserito nuovo messaggio di errore REG77
  * inserito nuovo messaggio di errore ERR63
  * inserito nuovo messaggio di errore ERR64
  * modificato messaggio dell'errore ERR46
  * inserito nuovo messaggio di errore FVX30 
* codiceScheda.json: 
  * aggiunta la nuova scheda SQ1.
  * modificato codice C01 e C02 in CO1 e CO2
* lingue.json, statoScheda.json, statoAvviso.json, esitoOperazione.json, codNUTS.json, codIstat.json:
  * aggiornati i valori delle tipologiche  
* prestazioni.json:
  * rinominata in prestazioniComprese.json
* tipoRealizzazioneContratto.json:
  * rinominata in tipoRealizzazione.json
* funzioniDelegate.json:
  * rinominata in funzioniSvolte.json
* giustificazioneAggiudicazioneDiretta.json:
  * rinominata in giustificazioniAggiudicazioneDiretta.json
* esitoProcedura.json:
  * rinominata in esito.json
* giustificazioneEsitoProcedura.json:
  * rinominata in giustificazione.json
* motiviModificaContrattuale.json:
  * rinominata in motiviModifica.json
* motiviVariazioneAnagrafica.json:
  * rinominata in motivoVariazione.json
* motiviInterruzione.json:
  * rinominata in causaInterruzioneAnticipata.json
* tipologiaComunicazione.json:
  * rinominata in tipoComunicazione.json      
* cancellate le seguenti tipologiche perché rinominate o non utilizzate:
  * prestazioni.json
  * tipoRealizzazioneContratto.json
  * funzioniDelegate.json
  * giustificazioneAggiudicazioneDiretta.json
  * esitoProcedura.json
  * giustificazioneEsitoProcedura.json
  * motiviModificaContrattuale.json
  * motiviVariazioneAnagrafica.json
  * motiviInterruzione.json
  * erroriEform.json
  * tipologiaComunicazione.json
* tipoContenuto.json: 
  * nuova tipologica ad uso interno
    
## Orchestratore

## Specifiche Interfacce

## Documentazione
* Nella sezione Standard adottati del file README.md è stata aggiornata la versione sdk dell'eForms da adottare (1.8.0).
</details>

<details>
<summary><h1>Note di rilascio del 25/09/2023</h1></summary>

## JWS token 
ref. /docs/specifiche-jws/

* jws.yaml:
  * creato un nuovo file con le specifiche openAPI 3 del modello dati dell'oggetto body del token
* roadmap.md:
  * creato un nuovo file con la roadmap prevista per l'attivazione dei controlli di correttezza formale e sostanziale del JWS token 
</details>

# Note di rilascio del gg/mm/aaaa

## Modello Dati 

### Regole

### Schede
* modello-dati-schede-P1.10.yaml, modello-dati-schede-P1.11.yaml, modello-dati-schede-P1.12.yaml, modello-dati-schede-P1.13.yaml, modello-dati-schede-P1.14.yaml, modello-dati-schede-P1.15.1.yaml, modello-dati-schede-P1.15.2.yaml, modello-dati-schede-P1.16.yaml, modello-dati-schede-P1.17.yaml, modello-dati-schede-P1.18.yaml, modello-dati-schede-P1.19.yaml, modello-dati-schede-P1.20.yaml, modello-dati-schede-P1.21.yaml, modello-dati-schede-P1.23.yaml, modello-dati-schede-P1.24.yaml, modello-dati-schede-PL1.1.yaml, modello-dati-schede-PL1.2.yaml, modello-dati-schede-PL1.3.yaml, modello-dati-schede-PL1.4.yaml, modello-dati-schede-PL1.5.yaml, modello-dati-schede-PL1.6.yaml, modello-dati-schede-PL1.7.yaml, modello-dati-schede-PL1.8.yaml, modello-dati-schede-PL1.9.yaml, modello-dati-schede-PL2.1.yaml, modello-dati-schede-PL2.2.yaml, modello-dati-schede-PL2.3.yaml, modello-dati-schede-PL2.7.yaml, modello-dati-schede-PL2.8.yaml, modello-dati-schede-PL2.9.yaml, modello-dati-schede-P2.10.yaml, modello-dati-schede-P2.11.yaml, modello-dati-schede-P2.12.yaml, modello-dati-schede-P2.13.yaml, modello-dati-schede-P2.14.yaml, modello-dati-schede-P2.16.yaml, modello-dati-schede-P2.17.yaml, modello-dati-schede-P2.18.yaml, modello-dati-schede-P2.19.yaml, modello-dati-schede-P2.20.yaml, modello-dati-schede-P2.21.yaml, modello-dati-schede-P2.23.yaml, modello-dati-schede-P2.24.yaml, modello-dati-schede-P3.1.yaml, modello-dati-schede-P3.2.yaml, modello-dati-schede-P3.3.yaml, modello-dati-schede-P3.4.yaml, modello-dati-schede-P3.5.yaml, modello-dati-schede-P4.1.yaml, modello-dati-schede-P4.2.yaml, modello-dati-schede-P4.3.yaml, modello-dati-schede-P4.4.yaml, modello-dati-schede-P4.5.yaml, modello-dati-schede-P4.6.yaml, modello-dati-schede-P5.yaml, modello-dati-schede-P6.1.yaml, modello-dati-schede-P6.2.yaml, modello-dati-schede-P7.1.1.yaml, modello-dati-schede-P7.1.2.yaml, modello-dati-schede-P7.1.3.yaml, modello-dati-schede-P7.2.yaml, modello-dati-schede-P7.3.yaml, modello-dati-schede-AD1.25.yaml, modello-dati-schede-AD1.26.yaml, modello-dati-schede-AD1.27.yaml, modello-dati-schede-AD1.28.yaml, modello-dati-schede-AD2_25.yaml, modello-dati-schede-AD2.26.yaml, modello-dati-schede-AD2.27.yaml, modello-dati-schede-AD2.28.yaml, modello-dati-schede-AD3.yaml, modello-dati-schede-AD4.yaml, modello-dati-schede-AD5.yaml, modello-dati-schede-A1.29.yaml, modello-dati-schede-A1.30.yaml, modello-dati-schede-A1.31.yaml, modello-dati-schede-A1.32.yaml, modello-dati-schede-A1.33.yaml, modello-dati-schede-A1.34.yaml, modello-dati-schede-A1.35.yaml, modello-dati-schede-A1.36.yaml, modello-dati-schede-A1.37.yaml, modello-dati-schede-A2.29.yaml, modello-dati-schede-A2.30.yaml, modello-dati-schede-A2.31.yaml, modello-dati-schede-A2.32.yaml, modello-dati-schede-A2.33.yaml, modello-dati-schede-A2.34.yaml, modello-dati-schede-A2.35.yaml, modello-dati-schede-A2.36.yaml, modello-dati-schede-A2.37.yaml, modello-dati-schede-A3.1.yaml, modello-dati-schede-A3.2.yaml, modello-dati-schede-A3.3.yaml, modello-dati-schede-A3.4.yaml, modello-dati-schede-A3.5.yaml, modello-dati-schede-A3.6.yaml, modello-dati-schede-A4.1.yaml, modello-dati-schede-A4.2.yaml, modello-dati-schede-A4.3.yaml, modello-dati-schede-A4.4.yaml, modello-dati-schede-A4.5.yaml, modello-dati-schede-A4.6.yaml, modello-dati-schede-A7.1.1.yaml, modello-dati-schede-A7.1.2.yaml, modello-dati-schede-M1.yaml, modello-dati-schede-M1.40.yaml, modello-dati-schede-M2.yaml, modello-dati-schede-M2.40.yaml, modello-dati-schede-SA1.yaml, modello-dati-schede-RSU1.yaml, modello-dati-schede-ES1.yaml, modello-dati-schede-CS1.yaml, modello-dati-schede-SO1.yaml, modello-dati-schede-SQ1.yaml, modello-dati-schede-RI1.yaml, modello-dati-schede-AC1.yaml, modello-dati-schede-CL1.yaml:
  * modificata la descrizione della scheda uniformandola al file Cronologia-schede-finale.xlsx

* modello-dati-schede-dati-comuni.yaml:
  * eliminato l'oggetto DatiBaseAggiudicazioneSubappaltoType
  * modificato l'oggetto AggiudicazioneA4Type: rinominata la property datibaseSubappalti in datiBaseSubappalti

* modello-dati-schede-A2.32.yaml, modello-dati-schede-A2.33.yaml, modello-dati-schede-A2.34.yaml, modello-dati-schede-A2.35.yaml:
  * modificata la property datiBaseAggiudicazioneSubappalto: sostituito il puntamento all'oggetto DatiBaseAggiudicazioneSubappaltoType con DatiBaseSubappaltiType
  * rinominata la property datibaseSubappalti in datiBaseSubappalti

* modello-dati-schede-A2.29.yaml, modello-dati-schede-A2.30.yaml, modello-dati-schede-A2.31.yaml, modello-dati-schede-A7.1.2.yaml, modello-dati-schede-A3.1.yaml, modello-dati-schede-A3.2.yaml, modello-dati-schede-A3.3.yaml, modello-dati-schede-A3.4.yaml, modello-dati-schede-A3.5.yaml:
  * rinominata la property datiBaseAggiudicazioneSubappalto in datiBaseSubappalti

### Tipologiche
* subappalto.json:
  * modificati i valori secondo la codelist Applicability del TED
* errori.json
  * aggiornate descrizioni
  * inserito nuovo messaggio di errore ERR65
    
## Orchestratore

## Specifiche Interfacce

## Documentazione
