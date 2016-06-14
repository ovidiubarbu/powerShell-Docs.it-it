# Just Enough Administration
Just Enough Administration (JEA) è la tecnologia di protezione che consente l'amministrazione delegata per qualsiasi elemento che possa essere gestito con PowerShell.
Con JEA, è possibile:
- **Ridurre il numero di amministratori dei computer** sfruttando gli account virtuali che eseguono azioni con privilegi per conto degli utenti normali.
- **Limitare le operazioni consentite agli utenti** specificando quali cmdlet, funzioni e comandi esterni possono eseguire.
- **Seguire da vicino le attività degli utenti** e capirle meglio grazie a trascrizioni "over-the-shoulder" che indicano esattamente quali comandi eseguono gli utenti durante una sessione.

Perché tutto questo è importante?
Consideriamo uno scenario comune in cui i server DNS condividono il percorso con i controller di dominio Active Directory.
Gli amministratori DNS devono avere privilegi di amministratore locale per risolvere i problemi del server DNS, ma per farlo è necessario che siano membri del gruppo di sicurezza con privilegi elevati "Domain Admins".
In questo modo saranno in grado di controllare l'intero dominio e di accedere a tutte le risorse del computer.

Se JEA è installato, è possibile configurare un ruolo per gli amministratori DNS che consenta l'accesso a tutti i comandi necessari per svolgere il proprio lavoro, ma niente di più.
Ciò significa che gli amministratori possono ripristinare facilmente una cache DNS danneggiata senza avere diritti per Active Directory, sfogliare il file system o eseguire script potenzialmente pericolosi.
In più, quando la sessione JEA è configurata per l'uso di account virtuali monouso con privilegi, gli amministratori DNS possono connettersi al server usando credenziali *non privilegiate* ed eseguire comunque comandi con privilegi.

## Guida introduttiva

### Installazione
La soluzione JEA è stata sviluppata insieme alla prossima versione di Windows Server 2016 ed è disponibile nelle versioni precedenti di Windows con gli aggiornamenti di Windows Management Framework.
La versione corrente di JEA è disponibile nelle piattaforme seguenti:

**Windows Server**
- Windows Server 2016 Technical Preview 4 e versioni successive
- Windows Server 2012 R2, 2012 e 2008 R2\* con [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installato

**Client Windows**
- Windows 10 con l'aggiornamento di novembre (1511) installato
- Windows 8.1, 8 e 7\* con [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installato

\* Il supporto per gli account virtuali nelle sessioni JEA attualmente non è disponibile in Windows Server 2008 R2 o Windows 7.


### Concetti principali
**Che cos'è esattamente JEA?**

JEA è un'estensione degli [endpoint vincolati](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) di PowerShell che aggiunge definizioni di ruoli, account virtuali e diversi altri miglioramenti per semplificare ulteriormente il blocco degli endpoint di gestione.
Un endpoint JEA è costituito da un file di configurazione di sessione di PowerShell e da uno o più file di capacità del ruolo.

**Che cosa sono i file di configurazione di sessione e i file di capacità del ruolo?**

I file di configurazione di sessione di PowerShell (estensione pssc) specificano *chi* può connettersi a un endpoint di PowerShell e *come* viene configurato l'endpoint.
Consentono di mappare utenti e gruppi di sicurezza a ruoli di gestione specifici e di configurare impostazioni globali come gli account virtuali e i criteri di trascrizione.
I file di configurazione di sessione sono specifici di ogni computer e questo consente di controllare l'accesso in base al computer, se necessario.

I file di capacità del ruolo di PowerShell (estensione psrc) definiscono *che cosa* sono in grado di eseguire nel sistema gli utenti appartenenti a un ruolo.
Consentono di limitare i cmdlet, le funzioni, i provider e i programmi esterni che un utente può usare nella sessione di JEA.
I file capacità del ruolo sono spesso generici per il ruolo servito (amministratore DNS, supporto tecnico di livello 1, controllo di sola lettura dell'inventario e così via) e appartengono ai moduli di PowerShell, rendendo più semplice la condivisione nel proprio ambiente e con altri utenti.

**In che modo JEA usa gli account virtuali?**

Nel file di configurazione di sessione di PowerShell è possibile configurare le sessioni JEA per usare gli account virtuali "RunAs".
Gli account virtuali sono account monouso con privilegi eseguiti per la connessione di un utente specifico in una sessione specifica nel cui contesto vengono eseguiti i comandi dell'utente.
Gli account virtuali appartengono al gruppo di sicurezza "Administrators" locale per impostazione predefinita, ma se necessario possono essere configurati in modo da appartenere solo a gruppi di sicurezza specificati.

### Esplorare la guida all'esperienza
Quando si è pronti a creare il primo endpoint JEA,
vedere la [guida all'esperienza di JEA](./JEA Guide.md) per sapere come creare, distribuire e usare il proprio endpoint JEA.
La guida consente di iniziare rapidamente con un endpoint JEA predefinito per avere un'idea di come sarà l'esperienza per l'utente finale, quindi spiega come ricreare l'endpoint da zero illustrando le configurazioni di sessione e le capacità del ruolo.

### Iniziare a creare i propri endpoint JEA
È facile creare un endpoint JEA: è sufficiente un sistema abilitato per JEA e un editor di testo, ad esempio PowerShell ISE.
Un suggerimento utile per iniziare è creare i file scheletro usando `New-PSRoleCapabilityFile -Path <path>` e `New-PSSessionCapabilityFile -Path <Path>` senza altri argomenti.
I file scheletro contengono tutti i campi di configurazione applicabili oltre a commenti utili che spiegano per cosa può essere usato ogni campo. 

Per semplificare ulteriormente la creazione degli endpoint JEA, vedere il [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) che offre un'interfaccia utente grafica con cui è possibile creare file di configurazione di sessione e file di capacità del ruolo.
È supportata anche la generazione di capacità del ruolo in base ai registri di PowerShell per iniziare a gestire i comandi eseguiti regolarmente dagli utenti per svolgere le proprie attività.


<!--HONumber=Jun16_HO1-->


