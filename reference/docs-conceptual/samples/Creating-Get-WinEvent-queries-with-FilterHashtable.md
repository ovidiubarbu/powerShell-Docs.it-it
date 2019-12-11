---
ms.date: 09/13/2019
title: Creazione di query Get-WinEvent con FilterHashtable
ms.openlocfilehash: 35d18dc894d90e698b38395b79ff4cf395515909
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444387"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a>Creazione di query Get-WinEvent con FilterHashtable

Per leggere il post del blog **Scripting Guy** originale del 3 giugno 2014, vedere [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) (Usare FilterHashTable per filtrare il registro eventi con PowerShell).

Questo articolo è un estratto del post di blog originale e spiega come usare il parametro **FilterHashtable** del cmdlet `Get-WinEvent` per filtrare i registri eventi. Il cmdlet `Get-WinEvent` di PowerShell è un metodo efficace per filtrare i registri eventi e i log di diagnostica di Windows. Le prestazioni migliorano quando una query `Get-WinEvent` usa il parametro **FilterHashtable**.

Quando si lavora con registri eventi di grandi dimensioni, non è efficace inviare gli oggetti nella pipeline a un comando `Where-Object`. Prima di PowerShell 6, il cmdlet `Get-EventLog` rappresentava un'altra opzione per ottenere i dati di log. Ad esempio, i comandi seguenti non sono efficienti per filtrare i log **Microsoft-Windows-Defrag**:

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

Il comando seguente usa una tabella hash che migliora le prestazioni:

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a>Post di blog sull'enumerazione

Questo articolo presenta informazioni su come usare i valori enumerati in una tabella hash. Per altre informazioni sull'enumerazione, leggere questi post del blog **Scripting Guy**. Per creare una funzione che restituisce i valori enumerati, vedere [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values) (Enumerazioni e valori).
Per altre informazioni, vedere la [serie di post del blog Scripting Guy sull'enumerazione](https://devblogs.microsoft.com/scripting/?s=about+enumeration).

## <a name="hash-table-key-value-pairs"></a>Coppie chiave-valore della tabella hash

Per creare query efficienti, usare il cmdlet `Get-WinEvent` con il parametro **FilterHashtable**.
**FilterHashtable** accetta una tabella hash come filtro per ottenere informazioni specifiche dai registri eventi di Windows. Una tabella hash usa coppie **chiave-valore**. Per altre informazioni sulle tabelle hash, vedere [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).

Se le coppie **chiave-valore** sono sulla stessa riga, devono essere separate da un punto e virgola. Se ogni coppia **chiave-valore** è su una riga separata, il punto e virgola non è necessario. In questo articolo ad esempio le coppie **chiave-valore** sono posizionate su righe separate e non vengono usati punti e virgola.

Questo esempio usa varie coppie **chiave-valore** del parametro **FilterHashtable**. La query completa include **LogName**, **ProviderName**, **Keywords**, **ID** e **Level**.

Le coppie **chiave-valore** accettate sono riportate nella tabella seguente e sono incluse nella documentazione per il parametro [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable**.

Nella tabella seguente vengono visualizzati i nomi delle chiavi, i tipi di dati e viene indicato se i caratteri jolly sono consentiti per un valore di dati.

|    Nome chiave    | Tipo di dati del valore | Caratteri jolly accettati? |
| -------------- | --------------- | ---------------------------- |
| LogName        | `<String[]>`    | Sì                          |
| ProviderName   | `<String[]>`    | Sì                          |
| Path           | `<String[]>`    | No                           |
| Parole chiave       | `<Long[]>`      | No                           |
| ID             | `<Int32[]>`     | No                           |
| Livello          | `<Int32[]>`     | No                           |
| StartTime      | `<DateTime>`    | No                           |
| EndTime        | `<DateTime>`    | No                           |
| UserID         | `<SID>`         | No                           |
| Dati           | `<String[]>`    | No                           |
| `<named-data>` | `<String[]>`    | No                           |

La chiave `<named-data>` rappresenta un campo dati dell'evento denominato. Ad esempio, l'evento 1008 Perflib può contenere i dati dell'evento seguenti:

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

È possibile eseguire una query per questi eventi usando il comando seguente:

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> In PowerShell 6 è stata aggiunta la possibilità di eseguire una query per `<named-data>`.

## <a name="building-a-query-with-a-hash-table"></a>Creazione di una query con una tabella hash

Per verificare i risultati e risolvere i problemi, è utile creare la tabella hash con una coppia **chiave-valore** alla volta. La query ottiene i dati dal log **Application**. La tabella hash è equivalente a `Get-WinEvent –LogName Application`.

Per iniziare, creare la query `Get-WinEvent`. Usare la coppia **chiave-valore** del parametro **FilterHashtable** con la chiave **LogName** e il valore **Application**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

Continuare a comporre la tabella hash con la chiave **ProviderName**. **ProviderName** è il nome visualizzato nel campo **Origine** nel **Visualizzatore eventi di Windows**. Ad esempio, **.NET Runtime** nello screenshot seguente:

![Immagine delle origini di Visualizzatore eventi di Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

Aggiornare la tabella hash e includere la coppia **chiave-valore** con la chiave **ProviderName e il valore **.NET Runtime**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

Se la query deve ottenere dati da registri eventi archiviati, usare la chiave **Path**. Il valore **Path** specifica il percorso completo del file di log. Per altre informazioni, vedere il post del blog **Scripting Guy** [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors) (Usare PowerShell per analizzare i registri eventi salvati per individuare gli errori).

## <a name="using-enumerated-values-in-a-hash-table"></a>Uso dei valori enumerati in una tabella hash

La chiave successiva nella tabella hash è **Keywords**. Il tipo di dati **Keywords** è una matrice del tipo valore `[long]` che contiene un numero elevato. Usare il comando seguente per trovare il valore massimo di `[long]`:

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

Per la chiave **Keywords** PowerShell usa un numero e non una stringa come **Security**. **Visualizzatore eventi di Windows** visualizza i valori di **Keywords** come stringhe, ma sono valori enumerati. Nella tabella hash, se si usa la chiave **Keywords** con un valore stringa, viene visualizzato un messaggio di errore.

Aprire il **Visualizzatore eventi di Windows** e dal riquadro **Azioni** fare clic su **Filtro registro corrente**.
Nel menu a discesa **Keywords** vengono visualizzate le parole chiave disponibili, come illustrato nello screenshot seguente:

![Immagine delle parole chiave di Visualizzatore eventi di Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

Usare il comando seguente per visualizzare i nomi delle proprietà `StandardEventKeywords`.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

I valori enumerati sono documentati in **.NET Framework**. Per altre informazioni, vedere [Enumerazione StandardEventKeywords](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).

I nomi e i valori enumerati per **Keywords** sono i seguenti:

| Nome             |  Value            |
| ---------------- | ------------------|
| AuditFailure     | 4503599627370496  |
| AuditSuccess     | 9007199254740992  |
| CorrelationHint2 | 18014398509481984 |
| EventLogClassic  | 36028797018963968 |
| Sqm              | 2251799813685248  |
| WdiDiagnostic    | 1125899906842624  |
| WdiContext       | 562949953421312   |
| ResponseTime     | 281474976710656   |
| Nessuno             | 0                 |

Aggiornare la tabella hash e includere la coppia **chiave-valore** con la chiave **Keywords** e il valore di enumerazione **EventLogClassic** **36028797018963968**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a>Valore della proprietà statica Keywords (facoltativo)

La chiave **Keywords** viene enumerata, ma è possibile usare un nome di proprietà statica nella query per la tabella hash.
Invece di usare la stringa restituita, il nome della proprietà deve essere convertito in un valore con la proprietà **Value_** .

Ad esempio, lo script seguente usa la proprietà **Value_** .

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a>Filtro per ID evento

Per ottenere dati più specifici, i risultati della query vengono filtrati in base all'**ID evento**. Per fare riferimento all'**ID evento** nella tabella hash si usano la chiave **ID** e un **ID evento** specifico come valore. Il **Visualizzatore eventi di Windows** visualizza l'**ID evento**. In questo esempio viene usato l'**ID evento 1023**.

Aggiornare la tabella hash e includere la coppia **chiave-valore** con la chiave **ID** e il valore **1023**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a>Filtro per livello

Per affinare ulteriormente i risultati e includere solo gli eventi che sono errori, usare la chiave **Level**.
**Visualizzatore eventi di Windows** visualizza i valori di **Level** come valori stringa, ma sono valori enumerati. Nella tabella hash, se si usa la chiave **Level** con un valore stringa viene visualizzato un messaggio di errore.

**Level** include valori come **Error**, **Warning** o **Informational**. Usare il comando seguente per visualizzare i nomi delle proprietà `StandardEventLevel`.

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

I valori enumerati sono documentati in **.NET Framework**. Per altre informazioni, vedere [Enumerazione StandardEventLevel](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).

I nomi e i valori enumerati per la chiave **Level** sono i seguenti:

| Nome           | Value |
| -------------- | ----- |
| Verbose        |   5   |
| Informativo  |   4   |
| Avviso        |   3   |
| Errore di          |   2   |
| Critico       |   1   |
| LogAlways      |   0   |

La tabella hash della query completata include la chiave **Level** e il valore **2**.

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a>Proprietà statica Level nell'enumerazione (facoltativo)

La chiave **Level** viene enumerata, ma è possibile usare un nome di proprietà statica nella query per la tabella hash.
Invece di usare la stringa restituita, il nome della proprietà deve essere convertito in un valore con la proprietà **Value_** .

Ad esempio, lo script seguente usa la proprietà **Value_** .

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```