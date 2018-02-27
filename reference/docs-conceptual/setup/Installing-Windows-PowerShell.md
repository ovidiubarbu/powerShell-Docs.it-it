---
ms.date: 2017-08-09
keywords: PowerShell, cmdlet, download, installazione, configurazione, Windows 10, Windows 8.1, Windows 8.0, Windows 7
title: Installazione di Windows PowerShell
ms.openlocfilehash: dffb6ec11ce265ebc4e6bc91f631650e1af5868d
ms.sourcegitcommit: 05d576cf107780fa52b2db4a042816be40b00fbc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="installing-windows-powershell"></a>Installazione di Windows PowerShell
Windows PowerShell viene installato per impostazione predefinita in tutte le versioni di Windows, a partire da Windows 7 SP1 e Windows Server 2008 R2 SP1.

Se si è interessati a PowerShell 6 e versioni successive, è necessario installare PowerShell Core invece di Windows PowerShell. Per altre informazioni, vedere [Installazione di PowerShell Core in Windows](Installing-PowerShell-Core-on-Windows.md).

## <a name="finding-powershell-in-windows-10-81-80-and-7"></a>Ricerca di PowerShell in Windows 10, 8.1, 8.0 e 7

Trovare la console o l'ISE (Integrated Scripting Environment) di PowerShell in Windows può risultare difficile, perché la posizione varia a seconda della versione di Windows.

Le tabelle seguenti permettono di trovare PowerShell nella versione di Windows corrente.
Tutte le versioni elencate di seguito sono versioni originali, così come rilasciate, senza aggiornamenti.

### <a name="for-console"></a>Per la console

Versione | Posizione
-- | --
Windows 10 | Fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell
Windows 8.1, 8.0 | Nella schermata Start iniziare a digitare PowerShell.<br/>Per l'edizione desktop, fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell
Windows 7 SP1 | Fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell nella casella di ricerca

### <a name="for-ise"></a>Per l'ISE

Versione | Posizione
-- | --
Windows 10 | Fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare ISE
Windows 8.1, 8.0 | Nella schermata Start digitare **PowerShell ISE**.<br/>Per l'edizione desktop, fare clic sull'icona di Windows nell'angolo in basso a sinistra e digitare **PowerShell ISE**
Windows 7 SP1 | Fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell nella casella di ricerca

## <a name="finding-powershell-in-windows-server-versions"></a>Ricerca di PowerShell nelle versioni di Windows Server

A partire da Windows Server 2008 R2, è possibile installare il sistema operativo Windows senza l'interfaccia utente grafica (GUI).
Le edizioni di Windows Server senza interfaccia utente grafica sono dette **Core**, mentre le edizioni con l'interfaccia utente grafica sono dette **Desktop**.

### <a name="windows-server-core-editions"></a>Windows Server Core Edition

In tutte le edizioni Core quando si accede al server viene visualizzata una finestra del prompt dei comandi di Windows.

Digitare `powershell` e premere **INVIO** per avviare PowerShell all'interno della sessione del prompt dei comandi. Digitare `exit` per terminare la sessione di PowerShell e tornare al prompt dei comandi.

### <a name="windows-server-desktop-editions"></a>Windows Server Desktop Edition

In tutte le edizioni desktop fare clic sull'icona di Windows nell'angolo in basso a sinistra e iniziare a digitare PowerShell.
Vengono visualizzate sia le opzioni console che ISE.

L'unica eccezione è rappresentata dall'ISE in Windows Server 2008 R2 SP1. In questo caso occorre fare clic sull'icona di Windows nell'angolo in basso a sinistra e digitare PowerShell ISE.

## <a name="how-to-check-the-version-of-powershell"></a>Come verificare la versione di PowerShell

Per determinare la versione di PowerShell installata, avviare una console o l'ISE di PowerShell, digitare `$PSVersionTable` e premere **INVIO**. Cercare il valore `PSVersion`.

## <a name="upgrading-existing-windows-powershell"></a>Aggiornamento di Windows PowerShell esistente

Il pacchetto di installazione di PowerShell viene fornito all'interno di un programma di installazione di WMF.
La versione del programma di installazione di WMF corrisponde alla versione di PowerShell. Non esiste un programma di installazione autonomo per Windows PowerShell.

Per aggiornare la versione esistente di PowerShell in Windows, usare la tabella seguente per trovare il programma di installazione per la versione di PowerShell da aggiornare.

Windows | PS 3.0 | PS 4.0 | PS 5.0 | PS 5.1 |
--|--|--|--|--|
Windows 10 (vedere la nota 1)<br/>Windows Server 2016 | - | - | - | installato
Windows 8.1<br/>Windows Server 2012 R2 | - | installato | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 8<br/>Windows Server 2012 | installato | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)
Windows 7 SP1<br/>Windows Server 2008 R2 SP1 | [WMF 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=34595) | [WMF 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=40855) | [WMF 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) | [WMF 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616)

> **Nota 1**:
  >>
  >> Nella versione iniziale di Windows 10, con gli aggiornamenti automatici abilitati, PowerShell viene aggiornato dalla versione 5.0 alla versione 5.1.
  >>
  >> Se la versione originale di Windows 10 non viene aggiornata tramite Aggiornamenti di Windows, la versione di PowerShell è la 5.0.

## <a name="need-azure-powershell"></a>È necessario Azure PowerShell

Se si cerca **Azure PowerShell**, è possibile iniziare da [Overview of Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure) (Panoramica di Azure PowerShell).

In caso contrario, potrebbe essere interessante vedere [Install and configure Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/install-azurerm-ps) (Installare e configurare Azure PowerShell)

## <a name="see-also"></a>Vedere anche

- [Requisiti di sistema di Windows PowerShell](Windows-PowerShell-System-Requirements.md)
- [Avvio di Windows PowerShell](Starting-Windows-PowerShell.md)
