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
ms.sourcegitcommit: 26da6c80568327faadc6746099ac9869f2018fcf
ms.openlocfilehash: 8a10903c421f62311a28c9f32e352bba75f21052

---

# Installare e configurare WMF 5.1 (anteprima) #

***Nota:*** 
*questo contenuto è un segnaposto. I collegamenti seguenti puntano alle versioni di WMF 5.0 e verranno aggiornati al momento del rilascio dei file binari.*

Scaricare il pacchetto WMF 5.1 per il sistema operativo e l'architettura in cui si vuole eseguire l'installazione:

| Sistema operativo       | Architettura | Nome pacchetto              |
|------------------------|--------------|---------------------------|
| Windows Server 2012 R2 | x64      | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows Server 2012    | x64      | [W2K12-KB3156423-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717506) |
| Windows Server 2008 R2 | x64      | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 8.1            | x64          | [Win8.1AndW2K12R2-KB3156422-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717507) |
| Windows 8.1            | x86          | [Win8.1-KB3156422-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717963) |
| Windows 7 SP1          | x64          | [Win7AndW2K8R2-KB3156424-x64.msu](http://go.microsoft.com/fwlink/?LinkId=717504) |
| Windows 7 SP1          | x86          | [Win7-KB3156424-x86.msu](http://go.microsoft.com/fwlink/?LinkID=717962) |


## Installare WMF 5.1 da Esplora risorse (o Esplora file in Windows Server 2012 R2 e Windows 8.1)

1. Passare alla cartella in cui è stato scaricato il file MSU.

2. Fare doppio clic sul file MSU per eseguirlo.

## Installare WMF 5.1 dal prompt dei comandi##

1. Dopo aver scaricato il pacchetto corretto per l'architettura del computer, aprire una finestra del prompt dei comandi con diritti utente elevati (Esegui come amministratore). Con le opzioni di installazione dei componenti di base di Windows Server 2012 R2 o Windows Server 2012 o Windows Server 2008 R2 SP1, il prompt dei comandi viene aperto con diritti utente elevati per impostazione predefinita.

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

> **Dipendenza da WnRM:** il servizio di configurazione dello stato desiderato (DSC) tramite Windows PowerShell dipende da WinRM. WinRM non è abilitato per impostazione predefinita in Windows Server 2008 R2 e Windows 7. Per abilitare WinRM, in una sessione di Windows PowerShell con privilegi elevati eseguire `Set-WSManQuickConfig`.




<!--HONumber=Jul16_HO2-->


