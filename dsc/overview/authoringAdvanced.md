---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Informazioni sul ruolo di DSC in una pipeline CI/CD
ms.openlocfilehash: 7aec414b3d8e61d1daa1ce796184ac34dbbb43ce
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803379"
---
# <a name="understanding-dscs-role-in-a-cicd-pipeline"></a>Informazioni sul ruolo di DSC in una pipeline CI/CD

Questo articolo descrive i tipi di approcci disponibili per la combinazione di configurazioni e risorse.
L'obiettivo per ogni scenario è lo stesso: ridurre la complessità quando sono preferibili più configurazioni per raggiungere uno stato finale della distribuzione del server.
Ad esempio, si possono avere più team che contribuiscono al risultato di una distribuzione di server, da un lato il proprietario dell'applicazione che gestisce lo stato dell'applicazione e dall'altro un team centrale che rilascia le modifiche per le baseline della sicurezza.
Di seguito sono descritte in dettaglio le caratteristiche di ogni approccio con i relativi vantaggi e rischi.

![Pipeline](../images/Pipeline.jpg)

## <a name="types-of-collaborative-authoring-techniques"></a>Tipi di tecniche di creazione e modifica in collaborazione

Esistono due soluzioni integrate in Gestione configurazione locale per abilitare questo concetto:

| Concetto | Informazioni dettagliate
|-|-
| Configurazioni parziali | [Documentazione](../pull-server/partialConfigs.md)
| Risorse composite | [Documentazione](../resources/authoringResourceComposite.md)

## <a name="understanding-the-impact-of-each-approach"></a>Informazioni sull'impatto di ogni approccio

Ognuna di queste soluzioni può essere usata per gestire il risultato di una distribuzione di server.
Tuttavia, vi è una differenza significativa in termini di impatto tra i vari approcci.

## <a name="partial-configurations"></a>Configurazioni parziali

Quando si usano configurazioni parziali, la gestione della configurazione locale è configurata in modo da gestire più configurazioni in modo indipendente.
Le configurazioni vengono compilate in modo indipendente e quindi assegnate al nodo.
Questa operazione richiede che la gestione della configurazione locale venga configurata in anticipo con il nome di ogni configurazione.

![PartialConfiguration](../images/PartialConfiguration.jpg)

Le configurazioni parziali consentono a due o più team di controllare completamente la configurazione di un server, spesso senza il vantaggio della comunicazione o collaborazione.

I clienti hanno indicato nei propri commenti che questo può causare conflitti tra le risorse, override accidentali e in definitiva la perdita del controllo reale della configurazione dell'asset.

I clienti hanno inoltre indicato che, usando questo modello, le modifiche apportate alla configurazione dai team di gestione probabilmente non vengono completamente testate attraverso una pipeline di rilascio, con risultati imprevisti nell'ambiente di produzione.

**È essenziale che sia usata una singola pipeline per valutare tutte le modifiche rilasciate ai server.**

Nell'illustrazione seguente il Team B rilascia la propria configurazione parziale al Team A. Il Team A esegue i propri test su un server applicando entrambe le configurazioni.
In questo modello solo un'autorità è autorizzata ad apportare modifiche nell'ambiente di produzione.

![PartialSinglePipeline](../images/PartialSinglePipeline.jpg)

Quando il Team B richiede delle modifiche, deve inviare una richiesta pull per l'ambiente di controllo del codice sorgente del Team A.
Il Team A esamina le modifiche usando l'automazione dei test e rilascia la configurazione alla produzione quando è certo che le modifiche non causano errori nelle applicazioni o nei servizi ospitati dal server.

## <a name="composite-resources"></a>Risorse composite

Una risorsa composita è semplicemente una configurazione DSC inserita in un pacchetto come risorsa.
Non sono previsti requisiti speciali per configurare Gestione configurazione locale in modo che accetti le risorse composite.
Le risorse vengono usate all'interno di una nuova configurazione e un'unica compilazione produce un file MOF.

![CompositeResource](../images/CompositeResource.jpg)

Esistono due scenari comuni per le risorse composite.
Il primo consiste nel ridurre la complessità e astrarre concetti univoci.
Il secondo consiste nel consentire l'inserimento in pacchetti delle baseline per un team dell'applicazione per distribuire in modo sicuro alla produzione attraverso la pipeline di rilascio dopo aver superato tutti i test.

```PowerShell
Configuration Name
{
  File 1
  {
    Ensure = “Present”
    Path = “c:\inetpub\file1.zip”
    Source = “http://uri/file1.zip”
  }
  Service A
  {
    Ensure = “Present”
    Name = “ServiceA”
    Status = “Running”
  }
  SecurityBaseline Settings
  {
    Ensure = “Present”
    Datacenter = “NorthAmerica”
  }
}
```

Le risorse composite alzano di livello sia la composizione che la collaborazione usando una pipeline e creando maturità operativa

È possibile che l'utente stia già usando le risorse composite senza saperlo.
Un esempio è **ServiceSet**.
Questa risorsa gestisce lo stato di più servizi Windows senza indicarli singolarmente.
La proprietà Name accetta una matrice di stringhe per specificare il nome di ogni servizio.
Quando viene compilata la configurazione, il file MOF contiene una sezione Service univoca per ogni nome passato a ServiceSet.

Le organizzazioni possono avere "agenti" o "middleware" che devono essere installati in ogni server.
Una risorsa composita è l'approccio migliore per gestire le dipendenze, l'installazione e la configurazione di tali strumenti e utilità.

La persona o il team responsabile delle soluzioni che si estendono su più server crea una configurazione che contiene i requisiti.
Successivamente, la configurazione viene compressa come risorsa composita seguendo le istruzioni contenute nella documentazione della risorsa composita.
Infine, la nuova risorsa composita deve essere pubblicata in un percorso, ad esempio una condivisione file o un feed NuGet in cui i team dell'applicazione possano usarla per le configurazioni.

Ogni volta che il team rilascia una nuova versione, incrementa il numero di versione nel manifesto del modulo per la risorsa composita.
I team dell'applicazione includono la risorsa composita nella configurazione che creano per la gestione delle dipendenze dell'applicazione.
Quando i team addetti a operazioni e sicurezza rilasciano una nuova versione della propria risorsa, informano i team dell'applicazione che è stata apportata una nuova modifica.

I team dell'applicazione possono attivare un rilascio alla produzione in cui l'unica modifica è apportata alle baseline.
Tuttavia, questo offre la possibilità di valutare l'impatto sulle applicazioni prima di rischiare un'interruzione del servizio.

Nota: il feedback relativo all'uso delle risorse composite include anche critiche per il fatto che apportare modifiche richiede la compilazione e il rilascio di un nuovo file MOF.
Questo comportamento è da progettazione.
Ogni nuova versione della configurazione deve includere un riferimento statico a una versione specifica di ogni risorsa e deve essere convalidata dai test prima di raggiungere i nodi del server di produzione.
Il processo di test e rilascio delle modifiche dal controllo del codice sorgente consente di creare un ambiente sicuro per il rilascio delle modifiche in batch di piccole dimensioni ma frequenti.

Per altre informazioni sull'uso di pipeline di versione per gestire l'infrastruttura di base, vedere il white paper sul [modello di pipeline di versione](../further-reading/whitepapers.md).
