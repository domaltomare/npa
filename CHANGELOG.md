# Note di rilascio del dd/mm/aaaa

## Modello Dati
* modello-dati-tipologiche.yaml:
  * creato un nuovo oggetto TipologicaSchemaErroriType
  * modificato l'attributo $ref dell'oggetto ErroriEnum per estendere il nuovo schema dati ($ref: '#/components/schemas/TipologicaSchemaErroriType')
* modello-dati-npa.yaml:
  * aggiunta nuova scheda SQ1
  * aggiunti gli attributi idNuovaScheda e idNuovoAvviso in EsitoOperazioneType
      
### Regole
* A1_29.dmn, A1_30.dmn, A1_31.dmn, A1_32.dmn, A1_33.dmn, A1_34.dmn, A1_35.dmn, A1_36.dmn, A1_37.dmn, A2_29.dmn, A2_30.dmn, A2_31.dmn, A2_32.dmn, A2_33.dmn, A2_34.dmn, A2_35.dmn, A2_36.dmn, A2_37.dmn, A3_1.dmn, A3_2.dmn, A3_3.dmn, A3_4.dmn, A3_5.dmn, A3_6.dmn,M1_38.dmn, M1_39.dmn, M1_40.dmn, M2_38.dmn, M2_39.dmn, M2_40.dmn
  * aggiunte nuove regole
* AD1_25.dmn, AD1_26.dmn, AD1_27.dmn, AD1_28.dmn, AD2_25.dmn, AD2_26.dmn, AD2_27.dmn, AD2_28.dmn, AD3.dmn, P1_10.dmn, P1_11.dmn, P1_12.dmn, P1_13.dmn, P1_16.dmn, P1_17.dmn, P1_20.dmn, P1_21.dmn, P2_10.dmn, P2_11.dmn, P2_12.dmn, P2_13.dmn, P2_16.dmn, P2_17.dmn, P2_20.dmn, P2_21.dmn, P3_4.dmn
  * regola REG7 corretto il messaggio con art. 140 co. 10 D. Lgs. 36/2023
    
### Schede
* modello-dati-schede-dati-comuni.yaml:
  * modificato l'oggetto StazioneAppaltanteType rendendo tutti i campi obbligatori tranne funzionisvolte
  * modificato l'oggetto AggiudicazioneA1_31Type rendendo il cig obbligatorio
  * modificato l'oggetto ModificaContrattualeType togliendo lotidentifier
  * modificato l'oggetto ModificaContrattuale_40Type togliendo lotidentifier
  * modificato l'oggetto AggiudicazioneA7Type togliendo il lotidentifier e inserendo il cig obbligatorio
  * modificato l'oggetto AppaltoA7Type togliendo l'idappalto
  * aggiunto all'oggetto AppaltoP4BaseType il campo boolean costituzioneSocietaDiScopo obbligatorio
  * modificato il format datetime in date-time su tutti gli oggetti
  * modificato l'oggetto DatiTerminiInvioType: oraScadenzaPresentazioneOfferte diventa date-time
  * modificato l'oggetto DatiBaseTerminiInvioSoloOraType: oraScadenzaPresentazioneOfferte diventa date-time
  * eliminato l'oggetto MisurePremialiType
  * eliminato l'oggetto MotivoDerogaType
  * eliminato l'oggetto LingueType
  * eliminato l'oggetto TipologiaLavoroType
  * eliminato l'oggetto CondizioniNegoziataType
  * modificato l'oggetto ParitaDiGenereGenerazionaleType: l'attributo misurePremiali diventa array di MisurePremialiEnum e motivoDeroga diventa array di MotivoDerogaEnum
  * modificato l'oggetto DatiBaseDocumentiType: l'attributo lingue diventa array di LingueEnum
  * modificati gli oggetti LottoP_10Type, LottoP_11Type, LottoP_15Type,	LottoP_16Type, LottoP_17Type, LottoP_19Type,  LottoP3BaseType, LottoP6BaseType, LottoP4BaseType,LottoP7BaseType: l'attributo tipologiaLavoro diventa array di TipologiaLavoroEnum
  * modificati gli oggetti LottoBaseType, LottoP4BaseType, LottoP7BaseType: l'attributo condizioniNegoziata diventa array di CondizioniNegoziataEnum
  * modificato l'oggetto DatiBaseAccessibilitaType: il campo accessibilita non è più array, secondo quanto indicato nel ted con la sdk 1.8
  * modificati gli oggetti PrestazioniEnum, TipoRealizzazioneContrattoEnum, FunzioniDelegateEnum, GiustificazioneAggiudicazioneDirettaEnum, EsitoProceduraEnum, GiustificazioneEsitoProceduraEnum, MotiviModificaContrattualeEnum, MotiviVariazioneAnagraficaEnum, MotiviInterruzioneEnum, TipologiaComunicazioneEnum: rinominato il riferimento al json
  * modificati gli oggetti InvitatoType, DatiPersonaGiuridicaType, AggiudicatarioType, AggiudicatarioA1_35Type, PartecipanteType, PartecipanteADType, SoggettoType: rinominato l'attributo tipo in tipoOE
  * modificato l'oggetto PrestazioneType: rinominato l'attributo tipo in tipoSoggetto
  * modificato l'oggetto FinanziamentoType: rinominato l'attributo tipo in tipoFinanziamento	 
* modello-dati-schede-P3.5.yaml:
	* l'attributo condizioniNegoziata diventa array di CondizioniNegoziataEnum
* modello-dati-schede-A2.31.yaml:
  * reso il cig obbligatorio
* modello-dati-schede-A3.3.yaml:
  * modificato il format datetime in date-time
* modello-dati-schede-A3.5.yaml:
  * reso il cig obbligatorio
* modello-dati-schede-A3.6.yaml:
  * reso il cig obbligatorio
* modello-dati-schede-AD3.yaml:
  * reso il lotidentifier obbligatorio
* modello-dati-schede-AD4.yaml:
  * reso il lotidentifier obbligatorio
  * modificato il format datetime in date-time
* modello-dati-schede-CL1.yaml:
  * tolto l'idcontratto dall'oggetto CollaudoType e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-CO1.yaml:
  * tolto l'idcontratto dall'oggetto ConclusioneType e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-CO2.yaml:
  * tolto l'idcontratto dall'oggetto ConclusioneType e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-I1.yaml:
  * tolto l'idcontratto dall'oggetto DatiInizioType e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-NAG.yaml:
  * reso obbligatorio il cig e i lotti
* modello-dati-schede-SC1.yaml:
  * tolto l'idcontratto dall'oggetto DatiContrattoType
  * modificato il format datetime in date-time
* modello-dati-schede-RI1.yaml:
  * aggiunto l'attributo incidenzaCronoprogramma
  * eliminato l'array sospensioni e inserito l'elemento sospensione. tolto l'idcontratto dall'oggetto sospensioneType. inserito l'idscheda nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-SQ1.yaml:
  * aggiunta nuova scheda di superamento del quarto del tempo contrattuale
* modello-dati-schede-AC1.yaml:
  * eliminato l'array accordiBonari e inserito l'elemento accordoBonario. tolto l'idcontratto dall'oggetto AccordoBonarioType e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-IR1.yaml:
  * eliminato l'array ritardi e inserito l'elemento ritardo. tolto l'idcontratto dall'oggetto RitardoType e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-S2.yaml:
  * modificato il format datetime in date-time
* modello-dati-schede-RSU1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto. tolto l'idcontratto dall'oggetto subappaltotype e inserito nell'anac form
* modello-dati-schede-CS1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto. tolto l'idcontratto dall'oggetto subappaltotype e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-ES1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto. tolto l'idcontratto dall'oggetto subappaltotype. aggiunto l'idScheda nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-S3.yaml:
  * tolto lotidentifier. reso il cig obbligatorio
* modello-dati-schede-S4.yaml:
  * tolto lotidentifier. reso il cig obbligatorio
* modello-dati-schede-SA1.yaml:
  * eliminato l'array avanzamenti e inserito l'elemento avanzamento. tolto l'idcontratto dall'oggetto avanzamentotype e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-SO1.yaml:
  * eliminato l'array sospensioni e inserito l'elemento sospensione. tolto l'idcontratto dall'oggetto sospensioneType e inserito nell'anac form
  * modificato il format datetime in date-time
* modello-dati-schede-SU1.yaml:
  * eliminato l'array sospensioni e inserito l'elemento sospensione. tolto l'idcontratto dall'oggetto sospensioneType e inserito nell'anac form 
* modello-dati-schede-P3.3.yaml:	
  * modificata label cigAccordoQuadro in cigAccordoQuadroConvenzione
* modello-dati-schede-P6.3.yaml:
  * eliminato
* modello-dati-schede-P6.4.yaml:
  * eliminato
* modello-dati-schede-P6.5.yaml:
  * eliminato
* modello-dati-schede-P6.6.yaml:
  * eliminato
  
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
* erroriEform.json:
  * eliminato file non utilizzato
* lingue.json:
  * aggiornati i valori della tipologica
* statoScheda.json: 
  * aggiornati i valori della tipologica
* statoAvviso.json: 
  * aggiornati i valori della tipologica
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
* esitoOperazione.json:
  * aggiornati i valori della tipologica
* codNUTS.json:
  * aggiornati i valori della tipologica
* codIstat.json:
  * aggiornati i valori della tipologica        
* cancellate le seguenti tipologiche perché rinominate:
  * prestazioni.json
  * tipoRealizzazioneContratto.json
  * funzioniDelegate.json
  * giustificazioneAggiudicazioneDiretta.json
  * esitoProcedura.json
  * giustificazioneEsitoProcedura.json
  * motiviModificaContrattuale.json
  * motiviVariazioneAnagrafica.json
  * motiviInterruzione.json
* tipoContenuto.json: 
  * nuova tipologica ad uso interno
    
## Orchestratore

## Specifiche Interfacce

## Documentazione
* Nella sezione Standard adottati del file README.md è stata aggiornata la versione sdk dell'eForms da adottare.
