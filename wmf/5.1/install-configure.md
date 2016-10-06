---
title: Installare e configurare WMF 5.1 (anteprima)
ms.date: 2016-05-16
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
contributor: kriscv
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: c88163b5a7d8805d0dea82d321796d8f41d17bb8
ms.openlocfilehash: 26a325dc7a18ba167ddc56ca226fce3eded79f52

---

# Installare e configurare WMF 5.1 (anteprima) #

## Installare .Net 4.6
Per usare WMF 5.1, è necessario installare .NET Framework 4.6. Questo requisito consente di abilitare le nuove funzionalità di firma del catalogo, con un impatto sulle diverse aree di caricamento di moduli e script in WMF 5.1. 

[.NET Framework 4.6 è disponibile come KB 3045560](https://support.microsoft.com/en-us/kb/3045560). Le istruzioni di installazione sono disponibili nel percorso di download.

> **Nota:** è un problema noto che il requisito .NET 4.6 non viene rilevato dal programma di installazione WMF 5.1 (anteprima). Sarà quindi possibile installare WMF 5.1 (anteprima) prima di .NET 4.6. I test hanno dimostrato che è possibile installare .NET 4.6 dopo l'installazione di WMF 5.1 (anteprima). La versione finale di WMF 5.1 sarà in grado di controllare correttamente questo prerequisito prima di procedere all'installazione. 

## Scaricare e installare WMF 5.1 (anteprima)

Scaricare il pacchetto WMF 5.1 per il sistema operativo e l'architettura in cui si vuole eseguire l'installazione:

| Sistema operativo       | Prerequisiti | Collegamenti al pacchetto             |
|------------------------|---------------|---------------------------|
| Windows Server 2012 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586)|
| Windows Server 2012    | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823587)|
| Windows Server 2008 R2 | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> Aggiornamento della sicurezza per la [firma del codice SHA-2](https://technet.microsoft.com/en-us/library/security/3033929) | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) |
| Windows 8.1            | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) | **x64:** [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823586) </br> **x86:** [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823589) |
| Windows 7 SP1          | [.NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560) </br> [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855) </br> Aggiornamento della sicurezza per la [firma del codice SHA-2](https://technet.microsoft.com/en-us/library/security/3033929) | **x64:** [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkID=823588) </br> **x86:** [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=823590) |


## Installare WMF 5.1 da Esplora risorse (o Esplora file in Windows Server 2012 R2 e Windows 8.1)

1. Passare alla cartella in cui è stato scaricato il file MSU.

2. Fare doppio clic sul file MSU per eseguirlo.

## Installare WMF 5.1 dal prompt dei comandi##

1. Dopo aver scaricato il pacchetto corretto per l'architettura del computer, aprire una finestra del prompt dei comandi con diritti utente elevati (Esegui come amministratore). Con le opzioni di installazione dei componenti di base di Windows Server 2012 R2, Windows Server 2012 o Windows Server 2008 R2 SP1, il prompt dei comandi viene aperto con diritti utente elevati per impostazione predefinita.

2. Passare alla cartella in cui è stato scaricato o copiato il pacchetto di installazione di WMF 5.1.

3. Eseguire uno dei comandi seguenti:
    - Nei computer che eseguono Windows Server 2012 R2 o Windows 8.1 x64 eseguire `Win8.1AndW2K12R2-KB3156422-x64.msu /quiet`.
    - Nei computer che eseguono Windows Server 2012 eseguire `W2K12-KB3156423-x64.msu /quiet`.
    - Nei computer che eseguono Windows Server 2008 R2 SP1 o Windows 7 SP1 x64 eseguire `Win7AndW2K8R2-KB3156424-x64.msu /quiet`.
    - Nei computer che eseguono Windows 8.1 x86 eseguire `Win8.1-KB3156422-x86.msu /quiet`.
    - Nei computer che eseguono Windows 7 SP1 x86 eseguire `Win7-KB3156424-x86.msu /quiet`.

## Altre note sull'installazione per Windows Server 2008 SP1 e Windows 7 SP1##
L'installazione di WMF 5.1 in Windows Server 2008 SP1 o Windows 7 SP1, richiede l'installazione di:
- Service Pack più recente
- [WMF 4.0](http://www.microsoft.com/en-us/download/details.aspx?id=40855)
- WMF 5.1 richiede [Microsoft .NET Framework 4.6](https://support.microsoft.com/en-us/kb/3045560). È possibile installare Microsoft .NET Framework 4.6 seguendo le istruzioni disponibili nel percorso di download.
- Aggiornamento della sicurezza per la [firma del codice SHA-2](https://technet.microsoft.com/en-us/library/security/3033929). Questo aggiornamento è necessario per usare nuovi cmdlet di PowerShell per i file di catalogo di Windows. 

> **Dipendenza da WnRM:** il servizio di configurazione dello stato desiderato (DSC) tramite Windows PowerShell dipende da WinRM. WinRM non è abilitato per impostazione predefinita in Windows Server 2008 R2 e Windows 7. Per abilitare WinRM, eseguire `Set-WSManQuickConfig` in una sessione di Windows PowerShell con privilegi elevati.




<!--HONumber=Aug16_HO3-->


