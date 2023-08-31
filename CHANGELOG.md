# Note di rilascio del dd/mm/aaaa

## Modello Dati

* modello-dati-tipologiche.yaml:
  * creato un nuovo oggetto TipologicaSchemaErroriType
  * modificato l'attributo $ref dell'oggetto ErroriEnum per estendere il nuovo schema dati ($ref: '#/components/schemas/TipologicaSchemaErroriType')

* modello-dati-npa.yaml:
  * aggiunta nuova scheda SQ1
      
### Regole

### Schede

* modello-dati-schede-dati-comuni.yaml:
  * modificato l'oggetto StazioneAppaltanteType rendendo il codiceFiscale obbligatorio
  * modificato l'oggetto AggiudicazioneA1_31Type rendendo il cig obbligatorio
  * modificato l'oggetto ModificaContrattualeType togliendo lotidentifier
  * modificato l'oggetto ModificaContrattuale_40Type togliendo lotidentifier
  * modificato l'oggetto AggiudicazioneA7Type togliendo il lotidentifier e inserendo il cig obbligatorio
  * modificato l'oggetto AppaltoA7Type togliendo l'idappalto

* modello-dati-schede-A2.31.yaml:
  * reso il cig obbligatorio

* modello-dati-schede-A3.5.yaml:
  * reso il cig obbligatorio

* modello-dati-schede-A3.6.yaml:
  * reso il cig obbligatorio

* modello-dati-schede-AD3.yaml:
  * reso il lotidentifier obbligatorio

* modello-dati-schede-AD4.yaml:
  * reso il lotidentifier obbligatorio

* modello-dati-schede-CL1.yaml:
  * tolto l'idcontratto dall'oggetto CollaudoType e inserito nell'anac form

* modello-dati-schede-CO1.yaml:
  * tolto l'idcontratto dall'oggetto ConclusioneType e inserito nell'anac form

* modello-dati-schede-CO2.yaml:
  * tolto l'idcontratto dall'oggetto ConclusioneType e inserito nell'anac form

* modello-dati-schede-I1.yaml:
  * tolto l'idcontratto dall'oggetto DatiInizioType e inserito nell'anac form

* modello-dati-schede-NAG.yaml:
  * reso obbligatorio il cig e i lotti

* modello-dati-schede-SC1.yaml:
  * tolto l'idcontratto dall'oggetto DatiContrattoType

* modello-dati-schede-RI1.yaml:
  * aggiunto l'attributo incidenzaCronoprogramma
  * eliminato l'array sospensioni e inserito l'elemento sospensione. tolto l'idcontratto dall'oggetto sospensioneType. inserito l'idscheda nell'anac form

* modello-dati-schede-SQ1.yaml:
  * aggiunta nuova scheda di superamento del quarto del tempo contrattuale

* modello-dati-schede-AC1.yaml:
  * eliminato l'array accordiBonari e inserito l'elemento accordoBonario. tolto l'idcontratto dall'oggetto AccordoBonarioType e inserito nell'anac form

* modello-dati-schede-IR1.yaml:
  * eliminato l'array ritardi e inserito l'elemento ritardo. tolto l'idcontratto dall'oggetto RitardoType e inserito nell'anac form

* modello-dati-schede-RSU1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto. tolto l'idcontratto dall'oggetto subappaltotype e inserito nell'anac form

* modello-dati-schede-CS1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto. tolto l'idcontratto dall'oggetto subappaltotype e inserito nell'anac form

* modello-dati-schede-ES1.yaml:
  * eliminato l'array subappalti e inserito l'elemento subappalto. tolto l'idcontratto dall'oggetto subappaltotype. aggiunto l'idScheda nell'anac form

* modello-dati-schede-S3.yaml:
  * tolto lotidentifier. reso il cig obbligatorio

* modello-dati-schede-S4.yaml:
  * tolto lotidentifier. reso il cig obbligatorio

* modello-dati-schede-SA1.yaml:
  * eliminato l'array avanzamenti e inserito l'elemento avanzamento. tolto l'idcontratto dall'oggetto avanzamentotype e inserito nell'anac form

* modello-dati-schede-SO1.yaml:
  * eliminato l'array sospensioni e inserito l'elemento sospensione. tolto l'idcontratto dall'oggetto sospensioneType e inserito nell'anac form

* modello-dati-schede-SU1.yaml:
  * eliminato l'array sospensioni e inserito l'elemento sospensione. tolto l'idcontratto dall'oggetto sospensioneType e inserito nell'anac form
 
### Tipologiche

* errori.json
  * corretto con art. 140 co. 10 D. Lgs. 36/2023

## Orchestratore

## Specifiche Interfacce

## Documentazione

* Nella sezione Standard adottati del file README.md è stata aggiornata la versione sdk dell'eForms da adottare.
