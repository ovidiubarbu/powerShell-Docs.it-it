---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Modalità di esecuzione del debug degli script in Windows PowerShell ISE"
ms.assetid: 6dc6d8f9-8978-46e9-a92f-169af37e2817
ms.openlocfilehash: 2b8313c3f2ae1a8fb670099baa8950db49722330
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Modalità di esecuzione del debug degli script in Windows PowerShell ISE
Questo argomento descrive come eseguire il debug degli script in un computer locale usando le funzionalità di debug visivo di Windows PowerShell® Integrated Scripting Environment (ISE).

[Come gestire i punti di interruzione]()
[Come gestire una sessione di debug]()
[Come eseguire un'istruzione/routine, eseguire un'istruzione e uscire da un'istruzione/routine durante il debug]()
[Come visualizzare i valori delle variabili durante il debug]()

## <a name="bkmk_1"></a>Come gestire i punti di interruzione
Un punto di interruzione è un punto specificato all'interno di uno script in cui si vuole sospendere l'esecuzione delle operazioni per poter esaminare lo stato corrente delle variabili e l'ambiente di esecuzione dello script. Quando lo script viene sospeso da un punto di interruzione, è possibile eseguire comandi nel riquadro della console per esaminare lo stato dello script.  È anche possibile eseguire l'output di variabili o eseguire altri comandi. Si può persino modificare il valore di tutte le variabili visibili nel contesto dello script attualmente in esecuzione. Dopo aver esaminato gli elementi desiderati, è possibile riavviare l'esecuzione dello script.

Nell'ambiente di debug di Windows PowerShell si possono impostare tre tipi di punti di interruzione:

1.  **Punto di interruzione riga** Lo script viene sospeso quando durante l'esecuzione viene raggiunta la riga specificata

2.  **Punto di interruzione variabile.** Lo script viene sospeso ogni volta che il valore della variabile specificata cambia.

3.  **Punto di interruzione comando.** Lo script viene sospeso ogni volta che durante il funzionamento dello script sta per essere eseguito il comando specificato. Può includere parametri per filtrare ulteriormente il punto di interruzione alla sola operazione desiderata. Il comando può essere anche una funzione creata dall'utente.

Nell'ambiente di debug di Windows PowerShell ISE solo i punti di interruzione riga possono essere impostati usando il menu o i tasti di scelta rapida. Gli altri due tipi di punti di interruzione vanno impostati dal riquadro della console usando il cmdlet [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8). Questa sezione illustra come eseguire le attività di debug in Windows PowerShell ISE usando i comandi di menu, ove disponibili, e come eseguire una gamma di comandi più ampia dal riquadro della console usando gli script.

### <a name="to-set-a-breakpoint"></a>Per impostare un punto di interruzione
È possibile impostare un punto di interruzione in uno script solo dopo averlo salvato. Fare clic con il pulsante destro del mouse sulla riga in cui si vuole impostare un punto di interruzione e scegliere **Attiva/disattiva punto di interruzione**. In alternativa, fare clic sulla riga in cui si vuole impostare un punto di interruzione e premere **F9** oppure scegliere **Attiva/disattiva punto di interruzione** dal menu **Debug**.

Lo script seguente è un esempio di come si può impostare un punto di interruzione variabile dal riquadro della console usando il cmdlet [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420).

``` PowerShell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Elencare tutti i punti di interruzione
Visualizza tutti i punti di interruzione nella sessione di Windows PowerShell® corrente.

Scegliere **Elenca punti di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si può ottenere un elenco di tutti i punti di interruzione dal riquadro della console usando il cmdlet [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6).

``` PowerShell
# This command lists all breakpoints in the current session. 
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Rimuovere un punto di interruzione
Rimuovere un punto di interruzione equivale a eliminarlo.  Se si pensa di riutilizzarlo in un momento successivo, si può anche pensare di [disabilitarlo]().  Fare clic con il pulsante destro del mouse sulla riga in cui si vuole rimuovere un punto di interruzione e scegliere **Attiva/disattiva punto di interruzione**. In alternativa, fare clic sulla riga in cui si vuole rimuovere un punto di interruzione e scegliere **Attiva/disattiva punto di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si può rimuovere un punto di interruzione con un ID specificato dal riquadro della console usando il cmdlet [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6).

``` PowerShell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Rimuovere tutti i punti di interruzione
Per rimuovere tutti i punti di interruzione definiti nella sessione corrente, scegliere **Rimuovi tutti i punti di interruzione** dal menu **Debug**.

Lo script seguente è un esempio di come si possono rimuovere tutti i punti di interruzione dal riquadro della console usando il cmdlet [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6).

``` PowerShell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="bkmk_disable"></a>Disabilitare un punto di interruzione
La disabilitazione di un punto di interruzione non ne comporta la rimozione, ma la disattivazione fino a quando non viene abilitato di nuovo.  Per disabilitare uno specifico punto di interruzione riga, fare clic con il pulsante destro del mouse sulla riga in cui si trova e quindi scegliere **Disattiva punto di interruzione**. In alternativa, fare clic sulla riga in cui si vuole disabilitare un punto di interruzione e premere **F9** oppure scegliere **Disattiva punto di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si può rimuovere un punto di interruzione con un ID specificato dal riquadro della console usando il cmdlet [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8).

``` PowerShell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Disabilitare tutti i punti di interruzione
La disabilitazione di un punto di interruzione non ne comporta la rimozione, ma la disattivazione fino a quando non viene abilitato di nuovo.  Per disabilitare tutti i punti di interruzione definiti nella sessione corrente, scegliere **Disattiva tutti i punti di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si possono disabilitare tutti i punti di interruzione dal riquadro della console usando il cmdlet [Disable-PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8).

``` PowerShell
# This command disables all breakpoints in the current session. 
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Abilitare un punto di interruzione
Per abilitare uno specifico punto di interruzione, fare clic con il pulsante destro del mouse sulla riga in cui si trova e quindi scegliere **Attiva punto di interruzione**. In alternativa, fare clic sulla riga in cui si vuole abilitare un punto di interruzione e premere **F9** oppure scegliere **Attiva punto di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si possono abilitare specifici punti di interruzione dal riquadro della console usando il cmdlet [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0).

``` PowerShell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Abilitare tutti i punti di interruzione
Per abilitare tutti i punti di interruzione definiti nella sessione corrente, scegliere **Attiva tutti i punti di interruzione** dal menu **Debug**. Lo script seguente è un esempio di come si possono abilitare tutti i punti di interruzione dal riquadro della console usando il cmdlet [Enable-PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0).

``` PowerShell
# This command enables all breakpoints in the current session. 
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="bkmk_2"></a>Come gestire una sessione di debug
Prima di avviare il debug è necessario impostare uno o più punti di interruzione. Non si può impostare un punto di interruzione finché lo script di cui si vuole eseguire il debug non è stato salvato. Per istruzioni su come impostare un punto di interruzione, vedere [Come gestire i punti di interruzione]() o [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420). Dopo avere avviato il debug, non è possibile modificare uno script se non si arresta il debug. Uno script in cui sono impostati uno o più punti di interruzione viene salvato automaticamente prima dell'esecuzione.

### <a name="to-start-debugging"></a>Per avviare il debug
Premere **F5** o fare clic sull'icona **Esegui script** sulla barra degli strumenti oppure in alternativa scegliere **Esegui/Continua** dal menu **Debug**. Lo script viene eseguito finché non incontra il primo punto di interruzione. L'esecuzione viene sospesa e la riga in cui è stata sospesa viene evidenziata.

### <a name="to-continue-debugging"></a>Per continuare il debug
Premere **F5** o fare clic sull'icona **Esegui script** sulla barra degli strumenti. In alternativa, scegliere **Esegui/Continua** dal menu **Debug** oppure digitare **C** nel riquadro della console e premere **INVIO**. In questo modo, l'esecuzione dello script continua fino al punto di interruzione successivo o, se non ne sono presenti altri, fino al termine dello script.

### <a name="to-view-the-call-stack"></a>Per visualizzare lo stack di chiamate
Lo stack di chiamate mostra la posizione di esecuzione corrente nello script. Se lo script è in esecuzione in una funzione chiamata da una funzione diversa, questa situazione viene rappresentata visualizzando righe aggiuntive nell'output. L'ultima riga mostra lo script originale e la riga in cui è stata chiamata una funzione. La riga successiva mostra tale funzione e la riga in cui potrebbe essere stata chiamata un'altra funzione.  La prima riga mostra il contesto corrente della riga corrente in cui è impostato il punto di interruzione.

Per vedere lo stack di chiamate corrente mentre l'esecuzione è sospesa, premere **CTRL+MAIUSC+D**. In alternativa, scegliere **Visualizza lo stack di chiamate** dal menu **Debug** oppure digitare **K** nel riquadro della console e premere **INVIO**.

### <a name="to-stop-debugging"></a>Per arrestare il debug
Premere **MAIUSC+F5**, scegliere **Arresta debugger** dal menu **Debug** oppure digitare **Q** nel riquadro della console e premere **INVIO**.

## <a name="bkmk_3"></a>Come eseguire un'istruzione/routine, eseguire un'istruzione e uscire da un'istruzione/routine durante il debug
Per il debug è fondamentale eseguire le istruzioni una alla volta in varie modalità. È possibile arrestare il debug in corrispondenza di una riga di codice ed esaminare i valori delle variabili e lo stato del sistema. La tabella seguente descrive le attività di debug comuni, ad esempio eseguire un'istruzione/routine, eseguire un'istruzione e uscire da un'istruzione/routine.

| Attività di debug | Descrizione | Modalità di esecuzione in PowerShell ISE |
| --- | --- | --- |
| **Esegui istruzione** | Esegue l'istruzione corrente e quindi arresta l'esecuzione in corrispondenza dell'istruzione successiva. Se l'istruzione corrente è una chiamata di funzione o di script, il debugger esegue tale funzione o script. In caso contrario, si ferma in corrispondenza dell'istruzione successiva. | Premere **F11**, scegliere **Esegui istruzione** dal menu **Debug** oppure digitare **S** nel riquadro della console e premere **INVIO**. |
| **Esegui istruzione/routine** | Esegue l'istruzione corrente e quindi arresta l'esecuzione in corrispondenza dell'istruzione successiva. Se l'istruzione corrente è una chiamata di funzione o di script, il debugger esegue l'intera funzione o script e si ferma in corrispondenza dell'istruzione successiva alla chiamata di funzione. | Premere **F10**, scegliere **Esegui istruzione/routine** dal menu **Debug** oppure digitare **V** nel riquadro della console e premere **INVIO**. |
| **Esci da istruzione/routine** | Esce dall'istruzione/routine della funzione corrente e risale di un livello se la funzione è nidificata. Se si trova nel corpo principale, lo script viene eseguito fino al termine o fino al punto di interruzione successivo. Le istruzioni ignorate vengono eseguite, ma non una alla volta. | Premere **MAIUSC+F11**, scegliere **Esci da istruzione/routine** dal menu **Debug** oppure digitare **O** nel riquadro della console e premere **INVIO**. |
| **Continua** | Continua l'esecuzione fino al termine o fino al punto di interruzione successivo. Le funzioni e le chiamate ignorate vengono eseguite, ma non una alla volta. | Premere **F5**, scegliere **Esegui/Continua** dal menu **Debug** oppure digitare **C** nel riquadro della console e premere **INVIO**. |

## <a name="bkmk_4"></a>Come visualizzare i valori delle variabili durante il debug
È possibile visualizzare i valori correnti delle variabili mentre si esamina il codice.

### <a name="to-display-the-values-of-standard-variables"></a>Per visualizzare i valori delle variabili standard
Utilizzare uno dei seguenti metodi:

-   Nel riquadro di script spostare il puntatore sulla variabile per visualizzarne il valore come descrizione comando.

-   Nel riquadro della console digitare il nome della variabile e premere **INVIO**.

In Windows PowerShell ISE, tutti i riquadri si trovano sempre nello stesso ambito. Di conseguenza, durante il debug di uno script, i comandi digitati nel riquadro della console vengono eseguiti nell'ambito dello script. Questo consente di usare il riquadro della console per trovare i valori delle variabili e delle funzioni di chiamata definite solo nello script.

### <a name="to-display-the-values-of-automatic-variables"></a>Per visualizzare i valori delle variabili automatiche
Si può usare il metodo precedente per visualizzare il valore di quasi tutte le variabili durante il debug di uno script. Tuttavia, questi metodi non funzionano per le variabili automatiche seguenti.

-   $_

-   $Input

-   $MyInvocation

-   $PSBoundParameters

-   $Args

Se si prova a visualizzare il valore di una di queste variabili, si ottiene il valore della variabile per una pipeline interna usata dal debugger, non il valore della variabile nello script. Per alcune variabili ($_, $Input, $MyInvocation, $PSBoundParameters e $Args) si può risolvere il problema usando il metodo seguente:

1.  Nello script assegnare il valore della variabile automatica a una nuova variabile.

2.  Visualizzare il valore della nuova variabile, spostando il puntatore sulla nuova variabile nel riquadro di script o digitando la nuova variabile nel riquadro della console.

Ad esempio, per visualizzare il valore della variabile $MyInvocation, nello script assegnare il valore a una nuova variabile, ad esempio $scriptname e quindi spostare il puntatore su $scriptname o digitare il nome della variabile per visualizzarne il valore.

``` PowerShell
#In MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path

#In the Console Pane:
C:\ps-test> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Vedere anche
- [Uso di Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)

