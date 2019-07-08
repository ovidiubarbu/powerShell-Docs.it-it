---
title: Uso di Visual Studio Code per la modifica e il debug remoti
description: Uso di Visual Studio Code per la modifica e il debug remoti
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263943"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Uso di Visual Studio Code per la modifica e il debug remoti

Gli utenti che hanno familiarità con l'ambiente ISE ricorderanno forse che è possibile eseguire `psedit file.ps1` dalla console integrata per aprire i file, locali o remoti, direttamente nell'ISE.

Questa funzionalità è disponibile anche nell'estensione di PowerShell per VSCode. Questa guida illustra come eseguire queste operazioni.

## <a name="prerequisites"></a>Prerequisiti

Questa guida presuppone che si disponga di:

- Una risorsa remota ( ad esempio una macchina virtuale o un contenitore) a cui si ha accesso
- PowerShell in esecuzione nella risorsa remota e nel computer host
- VSCode e l'estensione di PowerShell per VSCode

Questa funzionalità funziona in Windows PowerShell e PowerShell Core.

Questa funzionalità funziona anche quando ci si connette a un computer remoto tramite WinRM, PowerShell Direct o SSH. Se si desidera usare SSH, ma si usa Windows, considerare la [versione Win32 di SSH](https://github.com/PowerShell/Win32-OpenSSH).

> [!IMPORTANT]
> I comandi `Open-EditorFile` e `psedit` funzionano solo nella **console integrata di PowerShell** creata dall'estensione di PowerShell per VSCode.

## <a name="usage-examples"></a>Esempi di utilizzo

Questi esempi illustrano le operazioni di modifica e debug remoti da un MacBook Pro a una macchina virtuale Ubuntu in esecuzione in Azure. Il processo è identico in Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Modifica dei file locali con Open-EditorFile

Con l'estensione di PowerShell per VSCode avviata e la console integrata di PowerShell aperta, è possibile digitare `Open-EditorFile foo.ps1` o `psedit foo.ps1` per aprire il file locale foo.ps1 direttamente nell'editor.

![Open-EditorFile foo.ps1 funziona localmente](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> Il file `foo.ps1` deve esistere già.

Da qui, è possibile:

- Aggiungere punti di interruzione alla barra di navigazione

  ![aggiunta di punti di interruzione alla barra di navigazione](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Premere F5 per eseguire il debug dello script di PowerShell.

  ![debug dello script locale di PowerShell](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Durante il debug, è possibile interagire con la console di debug, verificare le variabili nell'ambito a sinistra e tutti gli altri gli strumenti standard di debug.

### <a name="remote-file-editing-with-open-editorfile"></a>Modifica dei file remoti con Open-EditorFile

È ora possibile passare alla modifica e al debug dei file remoti. I passaggi sono quasi gli stessi, occorre solo fare prima di tutto una cosa: avviare la sessione di PowerShell nel server remoto.

È disponibile un cmdlet per eseguire questa operazione. È denominato `Enter-PSSession`.

La spiegazione semplificata del cmdlet è:

- `Enter-PSSession -ComputerName foo` avvia una sessione tramite Gestione remota Windows
- `Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` avviano una sessione tramite PowerShell Direct
- `Enter-PSSession -HostName foo` avvia una sessione tramite SSH

Per altre informazioni, vedere la documentazione di [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Poiché si sta passando da macOS a una macchina virtuale Ubuntu in Azure, per la comunicazione remota si userà SSH.

Nella console integrata eseguire prima di tutto `Enter-PSSession`. Quando `[<hostname>]` viene visualizzato a sinistra del prompt, si è connessi alla sessione remota.

![La chiamata a Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Ora è possibile eseguire gli stessi passaggi che si eseguono per modificare uno script locale.

1. Eseguire `Open-EditorFile test.ps1` o `psedit test.ps1` per aprire il file remoto `test.ps1`

  ![Eseguire Open-EditorFile sul file test.ps1](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Modificare i file/impostare punti di interruzione

   ![modificare i file e impostare punti di interruzione](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Avviare il debug del file remoto (F5)

   ![debug del file remoto](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Se si verificano problemi, è possibile segnalarli [nel repository GitHub](https://github.com/powershell/vscode-powershell).
