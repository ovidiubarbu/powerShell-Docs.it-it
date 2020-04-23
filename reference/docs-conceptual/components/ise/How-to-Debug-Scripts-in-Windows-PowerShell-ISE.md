---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Modalità di esecuzione del debug degli script in Windows PowerShell ISE
ms.openlocfilehash: 6fbe340cbff832b5d0e2a5515ef432cec574a3c1
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80500935"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Modalità di esecuzione del debug degli script in Windows PowerShell ISE

Questo articolo descrive come eseguire il debug degli script in un computer locale usando le funzionalità di debug visivo di Windows PowerShell Integrated Scripting Environment (ISE).

## <a name="how-to-manage-breakpoints"></a>Come gestire i punti di interruzione

Un punto di interruzione è un punto specificato all'interno di uno script in cui si vuole sospendere l'esecuzione delle operazioni per poter esaminare lo stato corrente delle variabili e l'ambiente di esecuzione dello script.
Quando lo script viene sospeso da un punto di interruzione, è possibile eseguire comandi nel riquadro della console per esaminare lo stato dello script. È anche possibile eseguire l'output di variabili o eseguire altri comandi. Si può persino modificare il valore di tutte le variabili visibili nel contesto dello script attualmente in esecuzione. Dopo aver esaminato gli elementi desiderati, è possibile riavviare l'esecuzione dello script.

Nell'ambiente di debug di Windows PowerShell si possono impostare tre tipi di punti di interruzione:

1. **Punto di interruzione riga** Lo script viene sospeso quando durante l'esecuzione viene raggiunta la riga specificata

1. **Punto di interruzione variabile.** Lo script viene sospeso ogni volta che cambia il valore della variabile specificata.

1. **Punto di interruzione comando.** Lo script viene sospeso ogni volta che durante il funzionamento dello script sta per essere eseguito il comando specificato. Può includere parametri per filtrare ulteriormente il punto di interruzione alla sola operazione desiderata. Il comando può essere anche una funzione creata dall'utente.

Nell'ambiente di debug di Windows PowerShell ISE solo i punti di interruzione riga possono essere impostati usando il menu o i tasti di scelta rapida. Gli altri due tipi di punti di interruzione vanno impostati dal riquadro della console usando il cmdlet [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint). Questa sezione illustra come eseguire le attività di debug in Windows PowerShell ISE usando i comandi di menu, ove disponibili, e come eseguire una gamma di comandi più ampia dal riquadro della console usando gli script.

### <a name="to-set-a-breakpoint"></a>Per impostare un punto di interruzione

È possibile impostare un punto di interruzione in uno script solo dopo averlo salvato. Fare clic con il pulsante destro del mouse sulla riga in cui si vuole impostare un punto di interruzione e scegliere **Attiva/disattiva punto di interruzione**. In alternativa, fare clic sulla riga in cui si vuole impostare un punto di interruzione e premere <kbd>F9</kbd> oppure scegliere **Attiva/disattiva punto di interruzione** dal menu **Debug**.

Lo script seguente è un esempio di come si può impostare un punto di interruzione variabile dal riquadro della console usando il cmdlet [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint).

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Elencare tutti i punti di interruzione

Visualizza tutti i punti di interruzione nella sessione di Windows PowerShell corrente.

Scegliere **Elenca punti di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si può ottenere un elenco di tutti i punti di interruzione dal riquadro della console usando il cmdlet [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint).

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Rimuovere un punto di interruzione

Rimuovere un punto di interruzione equivale a eliminarlo.

Se si pensa di riutilizzarlo in un momento successivo, si può anche pensare di [disabilitare il punto di interruzione](#disable-a-breakpoint). Fare clic con il pulsante destro del mouse sulla riga in cui si vuole rimuovere un punto di interruzione e scegliere **Attiva/disattiva punto di interruzione**.
In alternativa, fare clic sulla riga in cui si vuole rimuovere un punto di interruzione e scegliere **Attiva/disattiva punto di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si può rimuovere un punto di interruzione con un ID specificato dal riquadro della console usando il cmdlet [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint).

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Rimuovere tutti i punti di interruzione

Per rimuovere tutti i punti di interruzione definiti nella sessione corrente, scegliere **Rimuovi tutti i punti di interruzione** dal menu **Debug**.

Lo script seguente è un esempio di come si possono rimuovere tutti i punti di interruzione dal riquadro della console usando il cmdlet [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint).

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Disabilitare un punto di interruzione

La disabilitazione di un punto di interruzione non ne comporta la rimozione, ma la disattivazione fino a quando non viene abilitato di nuovo. Per disabilitare uno specifico punto di interruzione riga, fare clic con il pulsante destro del mouse sulla riga in cui si trova e quindi scegliere **Disattiva punto di interruzione**. In alternativa, fare clic sulla riga in cui si vuole disabilitare un punto di interruzione e premere <kbd>F9</kbd> oppure scegliere **Disattiva punto di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si può rimuovere un punto di interruzione con un ID specificato dal riquadro della console usando il cmdlet [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint).

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Disabilitare tutti i punti di interruzione

La disabilitazione di un punto di interruzione non ne comporta la rimozione, ma la disattivazione fino a quando non viene abilitato di nuovo. Per disabilitare tutti i punti di interruzione definiti nella sessione corrente, scegliere **Disattiva tutti i punti di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si possono disabilitare tutti i punti di interruzione dal riquadro della console usando il cmdlet [Disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint).

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Abilitare un punto di interruzione

Per abilitare uno specifico punto di interruzione, fare clic con il pulsante destro del mouse sulla riga in cui si trova e quindi scegliere **Attiva punto di interruzione**. In alternativa, fare clic sulla riga in cui si vuole abilitare un punto di interruzione e premere <kbd>F9</kbd> oppure scegliere **Attiva punto di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si possono abilitare specifici punti di interruzione dal riquadro della console usando il cmdlet [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint).

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Abilitare tutti i punti di interruzione

Per abilitare tutti i punti di interruzione definiti nella sessione corrente, scegliere **Attiva tutti i punti di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si possono abilitare tutti i punti di interruzione dal riquadro della console usando il cmdlet [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint).

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Come gestire una sessione di debug

Prima di avviare il debug è necessario impostare uno o più punti di interruzione. Non si può impostare un punto di interruzione finché lo script di cui si vuole eseguire il debug non è stato salvato. Per istruzioni su come impostare un punto di interruzione, vedere [Come gestire i punti di interruzione](#how-to-manage-breakpoints) o [Set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint).
Dopo avere avviato il debug, non è possibile modificare uno script se non si arresta il debug. Uno script in cui sono impostati uno o più punti di interruzione viene salvato automaticamente prima dell'esecuzione.

### <a name="to-start-debugging"></a>Per avviare il debug

Premere <kbd>F5</kbd> o fare clic sull'icona **Esegui script** sulla barra degli strumenti oppure in alternativa scegliere **Esegui/Continua** dal menu **Debug**. Lo script viene eseguito finché non incontra il primo punto di interruzione. L'esecuzione viene sospesa e la riga in cui è stata sospesa viene evidenziata.

### <a name="to-continue-debugging"></a>Per continuare il debug

Premere <kbd>F5</kbd> o fare clic sull'icona **Esegui script** sulla barra degli strumenti. In alternativa, scegliere **Esegui/Continua** dal menu **Debug** oppure digitare `C` nel riquadro della console e premere <kbd>INVIO</kbd>. In questo modo, l'esecuzione dello script continua fino al punto di interruzione successivo o, se non ne sono presenti altri, fino al termine dello script.

### <a name="to-view-the-call-stack"></a>Per visualizzare lo stack di chiamate

Lo stack di chiamate mostra la posizione di esecuzione corrente nello script. Se lo script è in esecuzione in una funzione chiamata da una funzione diversa, questa situazione viene rappresentata visualizzando righe aggiuntive nell'output. L'ultima riga mostra lo script originale e la riga in cui è stata chiamata una funzione. La riga successiva mostra tale funzione e la riga in cui potrebbe essere stata chiamata un'altra funzione. La prima riga mostra il contesto corrente della riga corrente in cui è impostato il punto di interruzione.

Per vedere lo stack di chiamate corrente mentre l'esecuzione è sospesa, premere <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>. In alternativa, dal menu **Debug** scegliere **Visualizza lo stack di chiamate** oppure nel riquadro della console digitare `K` e quindi premere <kbd>INVIO</kbd>.

### <a name="to-stop-debugging"></a>Per arrestare il debug

Premere <kbd>MAIUSC</kbd>+<kbd>F5</kbd>. In alternativa nel menu **Debug** scegliere **Arresta debugger** oppure nel riquadro della console digitare `Q` e quindi premere <kbd>INVIO</kbd>.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Come eseguire un'istruzione/routine, eseguire un'istruzione e uscire da un'istruzione/routine durante il debug

Per il debug è fondamentale eseguire le istruzioni una alla volta in varie modalità. È possibile arrestare il debug in corrispondenza di una riga di codice ed esaminare i valori delle variabili e lo stato del sistema. La tabella seguente descrive le attività di debug comuni, ad esempio eseguire un'istruzione/routine, eseguire un'istruzione e uscire da un'istruzione/routine.

| Attività di debug |                                                                                                                   Descrizione                                                                                                                    |                                                      Modalità di esecuzione in PowerShell ISE                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Esegui istruzione**  | Esegue l'istruzione corrente e quindi arresta l'esecuzione in corrispondenza dell'istruzione successiva. Se l'istruzione corrente è una chiamata di funzione o di script, il debugger esegue tale funzione o script. In caso contrario, si ferma in corrispondenza dell'istruzione successiva.                      | Premere <kbd>F11</kbd>, scegliere **Esegui istruzione** dal menu **Debug** oppure digitare `S` nel riquadro della console e premere <kbd>INVIO</kbd>.                 |
| **Esegui istruzione/routine**  | Esegue l'istruzione corrente e quindi arresta l'esecuzione in corrispondenza dell'istruzione successiva. Se l'istruzione corrente è una chiamata di funzione o di script, il debugger esegue l'intera funzione o script e si ferma in corrispondenza dell'istruzione successiva alla chiamata di funzione. | Premere <kbd>F10</kbd>, scegliere **Esegui istruzione/routine** dal menu **Debug** oppure digitare `V` nel riquadro della console e premere <kbd>INVIO</kbd>.                 |
| **Esci da istruzione/routine**   | Esce dall'istruzione/routine della funzione corrente e risale di un livello se la funzione è nidificata. Se si trova nel corpo principale, lo script viene eseguito fino al termine o fino al punto di interruzione successivo. Le istruzioni ignorate vengono eseguite, ma non una alla volta.                   | Premere <kbd>MAIUSC</kbd>+<kbd>F11</kbd>. In alternativa, dal menu **Debug** scegliere **Esci da istruzione/routine** oppure nel riquadro della console digitare `O` e quindi premere <kbd>INVIO</kbd>. |
| **Continua**   | Continua l'esecuzione fino al termine o fino al punto di interruzione successivo. Le funzioni e le chiamate ignorate vengono eseguite, ma non una alla volta.                                                                                                          | Premere <kbd>F5</kbd>, scegliere **Esegui/Continua** dal menu **Debug** oppure digitare `C` nel riquadro della console e premere <kbd>INVIO</kbd>.               |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Come visualizzare i valori delle variabili durante il debug

È possibile visualizzare i valori correnti delle variabili mentre si esamina il codice.

### <a name="to-display-the-values-of-standard-variables"></a>Per visualizzare i valori delle variabili standard

Utilizzare una delle seguenti modalità:

- Nel riquadro di script spostare il puntatore sulla variabile per visualizzarne il valore come descrizione comando.

- Nel riquadro della console digitare il nome della variabile e premere <kbd>INVIO</kbd>.

In Windows PowerShell ISE, tutti i riquadri si trovano sempre nello stesso ambito. Di conseguenza, durante il debug di uno script, i comandi digitati nel riquadro della console vengono eseguiti nell'ambito dello script. Questo consente di usare il riquadro della console per trovare i valori delle variabili e delle funzioni di chiamata definite solo nello script.

### <a name="to-display-the-values-of-automatic-variables"></a>Per visualizzare i valori delle variabili automatiche

Si può usare il metodo precedente per visualizzare il valore di quasi tutte le variabili durante il debug di uno script. Tuttavia, questi metodi non funzionano per le variabili automatiche seguenti.

- `$_`

- `$Input`

- `$MyInvocation`

- `$PSBoundParameters`

- `$Args`

Se si prova a visualizzare il valore di una di queste variabili, si ottiene il valore della variabile per una pipeline interna usata dal debugger, non il valore della variabile nello script. È possibile risolvere questo problema per alcune variabili (`$_`, `$Input`, `$MyInvocation`, `$PSBoundParameters` e `$Args`) usando il metodo seguente:

1. Nello script assegnare il valore della variabile automatica a una nuova variabile.

1. Visualizzare il valore della nuova variabile, spostando il puntatore sulla nuova variabile nel riquadro di script o digitando la nuova variabile nel riquadro della console.

Ad esempio, per visualizzare il valore della variabile `$MyInvocation`, nello script assegnare il valore a una nuova variabile, ad esempio `$scriptName` e quindi spostare il puntatore su `$scriptName` o digitare il nome della variabile per visualizzarne il valore.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptName = $MyInvocation.MyCommand.Path
```

```PowerShell
# In the Console Pane:
.\MyScript.ps1
$scriptName
```

```Output
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Vedere anche

[Esplorazione di Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
