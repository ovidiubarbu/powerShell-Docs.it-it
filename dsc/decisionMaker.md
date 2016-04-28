# Panoramica di DSC (Desired State Configuration) per decision maker #

Questo documento descrive i vantaggi dell'uso di PowerShell DSC (Desired State Configuration) per le aziende. Non si tratta di una guida tecnica.

## Che cos'è DSC (Desired State Configuration)? ##

Windows PowerShell DSC (Desired State Configuration) è una piattaforma di gestione delle configurazioni integrata in Windows e basata su standard aperti. DSC è sufficientemente flessibile per funzionare in modo affidabile e coerente in ogni fase del ciclo di distribuzione (sviluppo, test, pre-produzione, produzione), nonché quando viene applicata scalabilità orizzontale. 

DSC ha come concetto centrale l'idea di "<ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)">configurazioni</ctype="x-NOTFOUND">", ovvero documenti facili da leggere che descrivono un ambiente costituito da computer ("nodi") con caratteristiche specifiche. Queste caratteristiche possono essere semplici, ad esempio per abilitare una funzionalità specifica di Windows, o complesse, ad esempio per la distribuzione di SharePoint. 

In DSC sono anche integrate funzionalità di monitoraggio e creazione di report. Se un sistema non è più conforme, DSC può generare un avviso ed eseguire operazioni per correggere il sistema. 

## Vantaggi dell'uso di DSC (Desired State Configuration) ##

Le configurazioni sono progettate per essere facili da leggere, archiviare e aggiornare. Le configurazioni dichiarano semplicemente lo stato desiderato per i dispositivi di destinazione, senza che sia necessario scrivere istruzioni su come impostare tale stato. In questo modo, DSC semplifica notevolmente l'apprendimento, l'adozione, l'implementazione e la gestione della configurazione. 

La creazione di configurazioni comporta l'acquisizione di passaggi di distribuzione complessi come "unica origine di dati reali" in un'unica posizione. In questo modo, le distribuzioni ripetute di un set specifico di computer sono molto meno soggette a errori. Ciò rende le distribuzioni più veloci e affidabili. È quindi possibile eseguire distribuzioni complesse in tempi brevi.

Le configurazioni possono anche essere condivise tramite <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://powershellgallery.com)">PowerShell Gallery</ctype="x-NOTFOUND">. Ciò significa che potrebbero essere già disponibili scenari comuni e procedure consigliate per il lavoro da svolgere.


## DSC (Desired State Configuration) e DevOps ##

<ctype="x-NOTFOUND" mdpre="[" mdpost="](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx)">DevOps</ctype="x-NOTFOUND"> è una combinazione di persone, tecnologie e cultura che consente rapidità di distribuzione e iterazione. La soluzione DSC è stata progettata tenendo in considerazione DevOps. La disponibilità di una singola configurazione che definisce un ambiente significa che gli sviluppatori possono codificare i requisiti in una configurazione e verificare la configurazione nel controllo del codice sorgente, mentre i team operativi possono distribuire facilmente il codice senza dover eseguire processi manuali soggetti a errori. 

Le configurazioni sono anche <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/configdata)">guidate dai dati</ctype="x-NOTFOUND"> e quindi i team operativi possono identificare e modificare gli ambienti in modo più semplice, senza l'intervento di uno sviluppatore. 

## DSC (Desired State Configuration) in ambienti locali e non locali ##

È possibile usare DSC per gestire le distribuzioni sia locali che non locali. Per le soluzioni locali, DSC (Desired State Configuration) ha un <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver)">server di pull</ctype="x-NOTFOUND"> che è possibile usare per centralizzare la gestione dei computer e creare report sul loro stato. Per le soluzioni cloud, è possibile usare DSC (Desired State Configuration) ovunque sia possibile usare Windows. Ci sono anche offerte specifiche di Azure basate su DSC, ad esempio <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://azure.microsoft.com/en-us/documentation/services/automation/)">Automazione di Azure</ctype="x-NOTFOUND">, che consente di centralizzare la creazione di report di DSC. 

## DSC e compatibilità ##

Anche se la soluzione DSC è stata introdotta in Windows Server 2012 R2, è disponibile per sistemi operativi di livello inferiore attraverso il pacchetto Windows Management Framework (WMF). Altre informazioni su WMF sono disponibili nella <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/)">home page di PowerShell</ctype="x-NOTFOUND">. 

È possibile usare DSC anche per gestire Linux. Per altre informazioni, vedere <ctype="x-NOTFOUND" mdpre="[" mdpost="](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted)">Introduzione a DSC per Linux</ctype="x-NOTFOUND">.

<!--HONumber=Mar16_HO1-->


