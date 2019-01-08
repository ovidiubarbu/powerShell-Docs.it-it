---
title: Uso di Visual Studio Code per la modifica e il debug remoti
description: Uso di Visual Studio Code per la modifica e il debug remoti
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655607"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Uso di Visual Studio Code per la modifica e il debug remoti

Per coloro che sono stati familiarità con l'ambiente ISE, come si ricorderà che è possibile eseguire `psedit file.ps1` dalla console integrata per aprire i file - locali o remoti: pulsante destro del mouse in ISE.

Ebbene, anche questa funzionalità è disponibile nell'estensione di PowerShell per Visual Studio code. Questa Guida illustrerà come eseguire questa operazione.

## <a name="prerequisites"></a>Prerequisiti

Questa guida si presuppone di avere:

- una risorsa remota (es: una macchina virtuale, un contenitore) di avere accesso a
- PowerShell in esecuzione e il computer host
- Visual Studio code e l'estensione di PowerShell per Visual Studio code

Questa funzionalità funziona in Windows PowerShell e PowerShell Core.

Questa funzionalità funziona anche quando ci si connette a un computer remoto tramite Gestione remota Windows, PowerShell Direct o SSH. Se si vuole usare SSH, ma si usa Windows, consultare il [versione Win32 di SSH](https://github.com/PowerShell/Win32-OpenSSH)!

## <a name="lets-go"></a>Partiamo

In questa sezione, esaminerò remoto di modifica e debug dal mio MacBook Pro, a una VM Ubuntu in esecuzione in Azure. Non potrei essere utilizza Windows, ma **il processo è identico**.

### <a name="local-file-editing-with-open-editorfile"></a>File locale modifica con Open-EditorFile

Con l'estensione di PowerShell per avviata Visual Studio code e la Console integrata di PowerShell aperta, è possibile digitare `Open-EditorFile foo.ps1` o `psedit foo.ps1` per aprire il file locale foo.ps1 si direttamente nell'editor.

![EditorFile Open foo.ps1 si lavora in locale](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 si deve esistere già.

Da qui, è possibile:

aggiungere i punti di interruzione alla barra di navigazione ![aggiunta punto di interruzione per barra](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

e premere F5 per eseguire il debug di script di PowerShell.
![debug dello script di PowerShell locale](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Durante il debug, è possibile interagire con la console di debug, vedere le variabili nell'ambito a sinistra e tutti gli altri standard gli strumenti di debug.

### <a name="remote-file-editing-with-open-editorfile"></a>File remoto modifica con Open-EditorFile

A questo punto è possibile passare in file remoti di modifica e debug. I passaggi sono quasi lo stesso, solo una cosa da fare prima di tutto: immettere la sessione di PowerShell nel server remoto.

È disponibile un cmdlet per eseguire questa operazione. Viene chiamato `Enter-PSSession`.

La spiegazione ridotta verso il basso del cmdlet è:

- `Enter-PSSession -ComputerName foo` Avvia una sessione tramite WinRM
- `Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` avviare una sessione tramite PowerShell Direct
- `Enter-PSSession -HostName foo` Avvia una sessione tramite SSH

Per altre informazioni sul `Enter-PSSession`, vedere la documentazione [qui](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Userà SSH per la comunicazione remota poiché voglio da macOS una VM Ubuntu in Azure.

In primo luogo, nella Console integrata, eseguiamo il Enter-PSSession. Si saprà che sia aperta la sessione perché `[something]` verrà visualizzato a sinistra della finestra del prompt dei comandi.

![La chiamata a Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Da qui, possiamo eseguire la procedura esatta come se si stava modificando uno script locale.

1. Eseguire `Open-EditorFile test.ps1` oppure `psedit test.ps1` per aprire il computer remoto `test.ps1` file ![Open-EditorFile file test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Modificare i file o impostare punti di interruzione ![modificare e impostare i punti di interruzione](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Avviare il debug (F5) il file remoto

![debug di file remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Questo è tutto qui! Ci auguriamo che questa guida ha contribuito a deselezionare le eventuali domande sul debug remoto e la modifica di PowerShell in Visual Studio code.

Se si verificano problemi, è possibile segnalare problemi [nel repository GitHub](http://github.com/powershell/vscode-powershell).
