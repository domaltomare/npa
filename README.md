# Descrizione
Il repository contiene la documentazione tecnica dei servizi di cooperazione applicativa che **le stazioni appaltanti** possono utilizzare per integrarsi con la Nuova Piattaforma Appalti (NPA) e con il Fascicolo Virtuale dell'Operatore Economico (FVOE) messi a disposizione dall'Autorità Nazionale Anticorruzione (ANAC), per governare l'ecosistema nazionale di approvvigionamento digitale per la gestione degli appalti pubblici.

# Documentazione
## Specifiche delle interfacce
 - Il [file YAML](/docs/specifiche-interfacce/specifiche-servizi-appalto.yaml) relativo alle specifiche dei servizi esposti dalla NPA per la gestione del Ciclo di vita dell'Appalto
 - Il [file YAML](/docs/specifiche-interfacce/specifiche-servizi-fvoe-fva.yaml) relativo alle specifiche dei servizi esposti dalla NPA per la gestione del Fascicolo Virtuale dell'Operatore Economico e del Fascicolo Virtuale dell'Appalto
 - Il [documento](/docs/specifiche-interfacce/documento-specifiche-servizi-npa.md) di sintesi di Specifica delle Interfacce redatto utilizzando il linguaggio di markup Markdown

## Modello dati
Il modello dati di NPA rappresenta l'insieme di informazioni oggetto del monitoraggio dell'appalto. I dati che riguardano l'appalto sono organizzati in oggetti autoconsistenti denominati "Schede". Ogni evento significativo ai fini del monitoraggio di un appalto o ogni richiesta di azione (ad es la pubblicazione di un avviso) vengono notificati alla NPA tramite l'invio di una opportuna scheda.
La superclasse dalla quale derivano tutte le schede è riportata di seguito: 

```shell
  AvvisoRequest{
    idAvviso	[...]
    oneOf ->	
      DatiPianoType{
        idPianificazione	{...}
        scheda	SchedaPianificazioneType{
          oneOf ->	
            SchedaPIN.1Type{...}
            SchedaPIN.2Type{...}
            ...
        }
      }
      DatiAppaltoType{
        idAppalto	[...]
        scheda	SchedaComunicaAppaltoType{
          oneOf ->	
            SchedaP1.10Type{...}
            SchedaP1.11Type{...}
            SchedaP1.12Type{...}
            SchedaP1.13Type{...}
            ...
        }
      }
      DatiSchedaType{
        idAppalto	[...]
        idScheda	[...]
        scheda	SchedaPostPubblicazioneType{
          oneOf ->	
            SchedaA1.29Type{...}
            SchedaA1.30Type{...}
            ...
        }
     }
  }
 ```
Durante l'esercizio della piattaforma NPA il processo di aggiornamento del modello dati sarà continuo, gli aggiornamenti verranno riportati nel presente repository e la loro efficacia è regolata secondo le specifiche del paragrafo [Termini del servizio](#termini-del-servizio). Le piattaforme interoperabili con NPA sono tenute all'aggiornamento del payload inviato entro i tempi previsti.

La cartella [modello-dati](/docs/modello-dati/) contenente la definizione dinamica del modello dati referenziato nelle specifiche dei servizi esposti dalla NPA. *Esempio*:
 ```shell
 StatoAppaltoEnum:
   $ref: 'https://raw.githubusercontent.com/domaltomare/npa/main/docs/modello-dati/modello-dati-npa.yaml#/components/schemas/StatoAppaltoEnum'
 ```
## Gestione del processo
La gestione del processo di appalto è demandata al componente NPA di orchestrazione che, tramite il suo motore di regole, ha il compito di gestire il flusso di informazioni (schede) che caratterizzano il singolo appalto. 
Il modulo di ochestrazione è un componente di backend che non espone servizi in interoporabilità ma ha il compito di:
 - effettuare la validazione sintattica e semantica dei dati di input
 - verificare se la scheda dati passata in input è coerente con lo stato dell’Appalto. 
 - attivare uno o più servizi di backend per soddisfare le richieste avanzate dal fruitore (ad es. pubblicazione di un avviso, richiesta di documenti ad altri Enti)
 - In caso non siano rilevate anomalie, far avanzare il processo allo stato successivo.

Lo schema delle regole di orchestrazione è consultabile nella cartella [orchestratore](/docs/orchestratore/). Le piattaforme fruitrici dei servizi di NPA sono tenute ad adeguare la sequenza di invio delle informazioni al flusso descritto.

Al pari del modello dati le regole che gestiscono il flusso delle informazioni sono soggette a variazioni continue in adeguamento alla normativa di settore, gli aggiornamenti verranno riportati nel presente repository e la loro efficacia è regolata secondo le specifiche del paragrafo [Termini del servizio](#termini-del-servizio). Le piattaforme interoperabili con NPA sono tenute all'aggiornamento del flusso di lavoro entro i tempi previsti.

## Modello statico e dinamico
I diagrammmi di contesto, di sequenza e di transizione di stato per l'intero Ciclo di Vita dell'Appalto sono consultabili nella cartella [diagrammi-drawio](/docs/diagrammi-drawio/) e, sono stati disegnati mediante l'utilizzo di [Draw.io](https://www.draw.io/).
Gli stessi sono anche disponibili in formato immagine nella nella cartella [immagini](/docs/immagini/).

# Termini del servizio
Le specifiche di interoperabilità per NPA sono presenti esclusivamente su questo repository. 
L'aggiornamento della documentazione può avvenire in qualsiasi momento e non verrà pubblicizzata in altro modo, gli utenti fruitori sono tenuti a consultare periodicamente il repository per ottenere le nuove specifiche.

## Tempi di adozione delle nuove specifiche
Nella tabella seguente sono disciplinati i tempi massimi e minimi per l'adozione da parte di NPA delle nuove specifiche e la conseguente eventuale deprecazione delle precedenti. In casi specifici, di particolare urgenza o in adempimento a normative di settore, ANAC può indicare tempi più ristretti ripetto a quelli standard.
 - Nuovi servizi o operazioni: non prima di 90 giorni dal rilascio della specifica;
 - Aggiornamento di servizi esistenti con deprecazione e mantenimento della versione precedente: non prima di 90 giorni dal rilascio della specifica;
 - Mantenimento della versione deprecata di un servizio: non meno di 180 giorni dal rilascio della specifica della nuova versione;
 - Aggiornamento di servizi esistenti con radiazione della versione precedente: non prima di 180 giorni dal rilascio della specifica;
 - Aggiornamento modello dati: non meno di 30 giorni e non più di 90 giorni dal rilascio della specifica
 - Aggiornamento del flusso di monitoraggio*: non meno di 30 giorni e non più di 90 giorni dal rilascio della specifica

* NB: l'aggiornamento del flusso di monitoraggio può includere l'aggiornamento o l'estensione del modello dati anche mediante l'introduzione di nuove schede.

## Standard adottati
 - eForms sdk versione 1.7;
 - Espd versione 2.11;

* NB: Nel momento in cui il sistema sarà in esercizio, l'upgrade delle versioni utilizzate è pubblicato con almeno 90 giorni di anticipo.

## Domande, chiarimenti e ulteriori infomazioni
Il canale di comunicazione con ANAC è rappresentato dall'apposita sezione [Issues](https://github.com/domaltomare/npa/issues) nella quale sarà possibile inserire una richiesta.

## Disclaimer
L’Autorità Nazionale Anticorruzione si riserva la facoltà di non fornire risposta puntuale a tutte le issues ricevute ed è sollevata da eventuali responsabilità dovuta:
- alla mancanza di risposta per richieste pervenute al di fuori dell'unico canale di comunicazione con ANAC rappresentato dalla sezione [Issues](https://github.com/domaltomare/npa/issues)
- alla possibile mancanza di risposta per tutte le richieste pervenute nell'apposita sezione Issues o che potrebbero essere di competenza di organizzazioni esterne.

# Roadmap del progetto
Le scadenze principali del progetto (milestones) sono consultabili nella [Roadmap](./roadmap.md). Fermo restando le scadenze principali la roadmap può essere aggiornata in qualunque momento
