---
title: "modello di esempio di writeup di una funzionalità o di uno scenario"
contributor: KeithB
translationtype: Human Translation
ms.sourcegitcommit: 8c55ca4b972c8d708a09b922f27eec585ddc33d0
ms.openlocfilehash: 025565404b60cebefac27e51c70d70edb5e47bc9

---

>Nota: specificare una proposta di titolo descrittivo e una breve descrizione

## Miglioramenti di PowerShellGet ##
I cmdlet nel modulo PowerShellGet sono stati aggiornati in modo consistente in WMF 5.1. Sono ora supportati i nuovi scenari seguenti:

- **Supporto proxy:** ora è supportato l'uso dei cmdlet PowerShellGet con un proxy interno, con l'aggiunta dei parametri Proxy e ProxyCredential a tutti i cmdlet Find-, Install-, Save- e Publish- nel modulo PowerShellGet, ad esempio Find-Module, Install-Module, Save-Module e Publish-Module. 
- **Applicazione della firma dei cataloghi:** tutti i cmdlet PowerShellGet ora verificano la disponibilità e impongono l'applicazione degli aggiornamenti dei moduli firmati. I moduli firmati usando i nuovi cmdlet Catalog verranno controllati dai cmdlet PowerShellGet per verificare che il modulo non sia stato modificato durante il transito e che gli aggiornamenti al modulo provengano solo dall'entità di pubblicazione originale. Questo riguarda i cmdlet Install-Module e Update-Module. 
- **Condivisione e acquisizione di funzionalità del ruolo:** le funzionalità del ruolo sono le definizioni di endpoint usate per configurare Just Enough Administration per il vincolo e verranno condivise con PowerShell Gallery nei moduli di PowerShell. I cmdlet includono Find-RoleCapability e New-PSRoleCapabilityFile. 
- **Ricerca comando:** Find-Command consente agli utenti di trovare un modulo in PowerShell Gallery contenente un comando che stanno cercando. 
- **Repository autenticati:** il feed Gestione pacchetti di Visual Studio richiede l'autenticazione, operazione che ora è supportata con i cmdlet PowerShellGet.

Dal feedback degli utenti è emersa la necessità di altri miglioramenti che sono stati inseriti nella versione 5.1, tra cui:

- **Modifiche a Install-Script:** la posizione usata da Install-script non viene aggiunta automaticamente al percorso utente nella versione 5.1. Questa modifica è stata apportata nella versione autonoma di PowerShellGet e ora è presente in WMF 5.1.
- **Aggiunta di campi di metadati agli script esistenti:** ora è possibile usare Update-ScriptFileInfo negli script esistenti per aggiungere i campi di metadati predefiniti necessari per la pubblicazione in PowerShellGallery. In precedenza era necessario aggiungerli manualmente a uno script esistente.
- **Pubblicazione di un modulo di una versione inferiore in PowerShell Gallery:** ora è possibile pubblicare in PowerShell Gallery un modulo con un numero di versione inferiore rispetto alla versione corrente usando Publish-Module. Se un'entità di pubblicazione pubblicava la versione 2.0.0 di un modulo con modifiche di rilievo rispetto delle versioni 1.x, non poteva rilasciare facilmente una correzione alla versione 1.5.0. Ora può pubblicare una versione 1.5.1, con conseguente miglioramento del supporto per la gestione di moduli in PowerShell Gallery. 
- **Controllo della sovrascrittura di comandi durante l'installazione di script e moduli:** Install-Module e Install-Script ora verificano se alcuni dei loro comandi sono già presenti nel sistema e, in caso affermativo, generano un errore per impostazione predefinita. 
- **Bootstrap di Nuget nei cmdlet Publish-:** in precedenza non era possibile installare automaticamente il provider Nuget durante l'uso di Publish-Module o Publish-Script, per cui alcune attività di automazione risultavano estremamente difficili. Ora gli utenti possono aggiungere comandi -Force to Publish- per ignorare la richiesta. 

>Nota: i dettagli aggiuntivi relativi a nuovi concetti, implementazione, esempi e così via devono essere collegati alla documentazione tecnica canonica

**Altre informazioni sull'uso di PowerShellGet**
- [About-CatalogSigning]()
- []()
- [Filtrare i risultati di Get-Module in base a CompatiblePSEditions]()
- [Impedire l'esecuzione di script a meno che non vengano eseguiti in un'edizione compatibile di PowerShell]()






<!--HONumber=Aug16_HO3-->


