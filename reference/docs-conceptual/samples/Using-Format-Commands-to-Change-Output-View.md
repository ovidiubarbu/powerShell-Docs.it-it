---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Uso dei comandi Format per modificare la visualizzazione dell'output
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: fba37b1d0479bf605d8f2171da27cd1bceb9976e
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293045"
---
# <a name="using-format-commands-to-change-output-view"></a>Uso dei comandi Format per modificare la visualizzazione dell'output

Windows PowerShell include un set di cmdlet che consentono di controllare le proprietà visualizzate per oggetti specifici. I nomi di tutti i cmdlet iniziano con il verbo **Format**. Consentono di selezionare una o più proprietà da visualizzare.

I cmdlet **Format** sono **Format-Wide**, **Format-List**, **Format-Table** e **Format-Custom**. Questo Manuale dell'utente illustra solo i cmdlet **Format-Wide**, **Format-List** e **Format-Table**.

Ogni cmdlet Format ha proprietà predefinite che verranno usate se non si specificano proprietà specifiche da visualizzare. Tutti i cmdlet usano inoltre lo stesso nome di parametro, **Property**, per specificare le proprietà da visualizzare. Dal momento che **Format-Wide** indica solo una singola proprietà, il relativo parametro **Property** accetta solo un valore, ma i parametri della proprietà di **Format-List** e **Format-Table** accetteranno un elenco di nomi di proprietà.

Se si usa il comando **Get-Process -Name powershell** con due istanze di Windows PowerShell in esecuzione, si otterrà un output simile al seguente:

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

Nel resto di questa sezione verrà illustrato come usare i cmdlet **Format** per modificare il modo in cui viene visualizzato l'output di questo comando.

## <a name="using-format-wide-for-single-item-output"></a>Uso di Format-Wide per output a elemento singolo

Per impostazione predefinita, il cmdlet `Format-Wide` visualizza solo la proprietà predefinita di un oggetto.
Le informazioni associate a ogni oggetto sono visualizzate in una singola colonna:

```powershell
Get-Command -Verb Format | Format-Wide
```

```output
Format-Custom                          Format-Hex
Format-List                            Format-Table
Format-Wide
```

È inoltre possibile specificare una proprietà non predefinita:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```output
Custom                                 Hex
List                                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>Controllo della visualizzazione di Format-Wide con il parametro Column

Con il cmdlet `Format-Wide` è possibile visualizzare unicamente una sola proprietà alla volta.
Questa funzionalità risulta utile per la visualizzazione di elenchi semplici che mostrano un solo elemento per riga.
Per ottenere un elenco semplice, impostare il valore del parametro **Column** su 1 digitando:

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

## <a name="using-format-list-for-a-list-view"></a>Uso di Format-List per una visualizzazione elenco

Il cmdlet **Format-List** visualizza un oggetto sotto forma di elenco, con ogni proprietà denominata e visualizzata in una riga distinta:

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

È possibile specificare il numero di proprietà che si vuole:

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>Ottenere informazioni dettagliate usando Format-List con i caratteri jolly

Il cmdlet **Format-List** consente di usare un carattere jolly come valore del relativo parametro **Property**. In questo modo si possono visualizzare informazioni dettagliate. Gli oggetti includono spesso più informazioni di quelle richieste, motivo per cui per impostazione predefinita Windows PowerShell non mostra tutti i valori della proprietà. Per visualizzare tutte le proprietà di un oggetto, usare il comando **Format-List -Property \&#42;**. Il comando seguente genera oltre 60 righe di output per un unico processo:

```powershell
Get-Process -Name powershell | Format-List -Property *
```

Anche se il comando **Format-List** è utile per la visualizzazione dei dettagli, se si vuole una panoramica dell'output che includa molti elementi, spesso una visualizzazione semplificata in formato tabulare è più utile.

## <a name="using-format-table-for-tabular-output"></a>Uso di Format-Table per output in formato tabulare

Se si usa il cmdlet **Format-Table** senza nomi di proprietà specificati per formattare l'output del comando **Get-Process**, si ottiene esattamente lo stesso output di quando non si esegue alcuna formattazione. Il motivo è che i processi sono in genere visualizzati in formato tabulare, come quasi tutti gli oggetti di Windows PowerShell.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

### <a name="improving-format-table-output-autosize"></a>Ottimizzazione dell'output di Format-Table (AutoSize)

Anche se una visualizzazione tabulare è utile per mostrare molte informazioni da mettere a confronto, potrebbe essere difficile interpretarle se lo schermo è troppo ridotto rispetto ai dati. Se ad esempio si prova a visualizzare il percorso, l'ID, il nome e la società di un processo, si otterrà un output troncato per la colonna della società e del percorso del processo:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

Se si specifica il parametro **AutoSize** quando si esegue il comando **Format-Table**, Windows PowerShell calcolerà la larghezza delle colonne in base ai dati effettivi da visualizzare. In questo modo la colonna **Path** risulta leggibile, ma la colonna della società rimane troncata:

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

Il cmdlet **Format-Table** potrebbe comunque troncare i dati, ma solo alla fine della schermata. Per tutte le proprietà, fatta eccezione per l'ultima visualizzata, viene assegnato tutto lo spazio richiesto per la corretta visualizzazione degli elementi di dati più lunghi. Si può notare che il nome della società è visibile ma il percorso risulta troncato se si invertono le posizioni di **Path** e **Company** nell'elenco dei valori di **Property**:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

Il comando **Format-Table** presuppone che quanto più una proprietà sia vicina all'inizio dell'elenco dei valori, tanto più sia importante. Per questo motivo, tenta di visualizzare interamente le proprietà più vicino all'inizio dell'elenco. Se il comando **Format-Table** non è in grado di visualizzare tutte le proprietà, alcune colonne saranno rimosse dalla visualizzazione e apparirà un avviso. È possibile osservare questo comportamento specificando **Name** come ultima proprietà dell'elenco:

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

Nell'output precedente la colonna ID viene troncata per essere adattata alle dimensioni dell'elenco e le intestazioni di colonna sono impilate. Il ridimensionamento automatico delle colonne non comporta sempre i risultati sperati.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>Ritorno a capo automatico dell'output di Format-Table nelle colonne (Wrap)

È possibile forzare il ritorno a capo automatico dei dati più lunghi di **Format-Table** nella relative colonne visualizzate usando il parametro **Wrap**. Con il solo parametro **Wrap**, tuttavia, l'operazione non produrrà necessariamente i risultati previsti, dal momento che verranno usate le impostazioni predefinite se non si specifica anche **AutoSize**:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

Un vantaggio dell'uso del solo parametro **Wrap** è che non rallenta molto l'elaborazione. Se si esegue un elenco di file ricorsivo di un sistema di directory di grandi dimensioni, potrebbe richiedere molto tempo e usare una grande quantità di memoria prima di visualizzare i primi elementi dell'output se si usa **AutoSize**.

Se si non teme il carico del sistema, **AutoSize** produce buoni risultati con il parametro **Wrap**. Alle colonne iniziali è sempre assegnato lo spazio necessario per visualizzare gli elementi su una riga, proprio come quando si specifica **AutoSize** senza il parametro **Wrap**. L'unica differenza è che la colonna finale verrà mandata a capo se necessario:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

Alcune colonne potrebbero non essere visualizzate se si specificano per prime le colonne più larghe, pertanto è consigliabile specificare per primi gli elementi di dati più piccoli. Nell'esempio seguente viene specificato per primo l'elemento del percorso estremamente lungo, ma anche con il ritorno a capo automatico la colonna finale **Name** viene persa:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

### <a name="organizing-table-output--groupby"></a>Organizzazione dell'output di tabella (-GroupBy)

Un altro parametro utile per il controllo dell'output in formato tabulare è **GroupBy**. Specialmente gli elenchi in formato tabulare più lunghi possono essere difficili da confrontare. Il parametro **GroupBy** raggruppa l'output in base al valore di una proprietà. È ad esempio possibile raggruppare i processi per società per un controllo più semplice, omettendo il valore della società nell'elenco delle proprietà:

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```