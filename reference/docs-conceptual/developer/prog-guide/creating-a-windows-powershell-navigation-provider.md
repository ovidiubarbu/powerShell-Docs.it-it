---
title: Creazione di un provider di navigazione di Windows PowerShell
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
ms.openlocfilehash: 7ca7e3ca6feeba018ad793d074caf67cd9506a68
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500811"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Creazione di un provider di navigazione di Windows PowerShell

Questo argomento descrive come creare un provider di navigazione di Windows PowerShell in grado di spostarsi nell'archivio dati. Questo tipo di provider supporta comandi ricorsivi, contenitori annidati e percorsi relativi.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider05.cs) per questo provider utilizzando Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3,0. Per istruzioni sul download, vedere [come installare Windows PowerShell e scaricare Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> I file di origine scaricati sono disponibili nella directory **\<PowerShell samples >** . Per ulteriori informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

Il provider descritto di seguito consente all'utente di gestire un database di Access come unità in modo che l'utente possa accedere alle tabelle di dati del database. Quando si crea un provider di navigazione personalizzato, è possibile implementare metodi che possono rendere necessari i percorsi qualificati per l'esplorazione, normalizzare i percorsi relativi, spostare gli elementi dell'archivio dati, nonché metodi che ottengono i nomi figlio, ottengono il percorso padre di un elemento e testano per identificare se un elemento è un contenitore.

> [!CAUTION]
> Tenere presente che questa progettazione presuppone che il database disponga di un campo con ID nome e che il tipo del campo sia LongInteger.

## <a name="define-the-windows-powershell-provider"></a>Definire il provider di Windows PowerShell

Un provider di navigazione di Windows PowerShell deve creare una classe .NET che deriva dalla classe di base [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Di seguito è riportata la definizione della classe per il provider di navigazione descritto in questa sezione.

[!code-csharp[AccessDBProviderSample05.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Si noti che in questo provider l'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) include due parametri. Il primo parametro specifica un nome descrittivo per il provider utilizzato da Windows PowerShell. Il secondo parametro specifica le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. Per questo provider non sono state aggiunte funzionalità specifiche di Windows PowerShell.

## <a name="defining-base-functionality"></a>Definizione della funzionalità di base

Come descritto in [progettare il provider PS](./designing-your-windows-powershell-provider.md), la classe di base [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) deriva da diverse altre classi che forniscono funzionalità del provider diverse. Un provider di navigazione di Windows PowerShell deve quindi definire tutte le funzionalità fornite da tali classi.

Per implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio di risorse utilizzate dal provider, vedere [creazione di un provider PS di base](./creating-a-basic-windows-powershell-provider.md). Tuttavia, la maggior parte dei provider (incluso il provider descritto qui) può usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

Per ottenere l'accesso all'archivio dati tramite un'unità di Windows PowerShell, è necessario implementare i metodi della classe di base [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Per ulteriori informazioni sull'implementazione di questi metodi, vedere [creazione di un provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Per modificare gli elementi di un archivio dati, ad esempio per ottenere, impostare e cancellare elementi, il provider deve implementare i metodi forniti dalla classe di base [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Per ulteriori informazioni sull'implementazione di questi metodi, vedere [creazione di un provider di elementi di Windows PowerShell](./creating-a-windows-powershell-item-provider.md).

Per ottenere gli elementi figlio, o i relativi nomi, dell'archivio dati, nonché i metodi che creano, copiano, rinominano e rimuovono elementi, è necessario implementare i metodi forniti dalla classe di base [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Per ulteriori informazioni sull'implementazione di questi metodi, vedere [creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Creazione di un percorso di Windows PowerShell

Il provider di navigazione di Windows PowerShell usa un percorso di Windows PowerShell interno al provider per spostarsi tra gli elementi dell'archivio dati. Per creare un percorso interno del provider, il provider deve implementare il metodo [System. Management. Automation. provider. Navigationcmdletprovider. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) per supportare le chiamate dal cmdlet Combine-Path. Questo metodo combina un percorso padre e un percorso figlio in un percorso interno del provider, usando un separatore di percorso specifico del provider tra i percorsi padre e figlio.

L'implementazione predefinita accetta i percorsi con "/" o "\\" come separatore di percorso, normalizza il separatore di percorso in "\\", combina le parti del percorso padre e figlio con il separatore tra di essi, quindi restituisce una stringa che contiene i percorsi combinati.

Questo provider di navigazione non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita del metodo [System. Management. Automation. provider. Navigationcmdletprovider. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Aspetti da ricordare sull'implementazione di MakePath

Per l'implementazione di [System. Management. Automation. provider. Navigationcmdletprovider. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath)è possibile che si verifichino le condizioni seguenti:

- L'implementazione del metodo [System. Management. Automation. provider. Navigationcmdletprovider. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) non deve convalidare il percorso come percorso completo valido nello spazio dei nomi del provider. Tenere presente che ogni parametro può rappresentare solo una parte di un percorso e le parti combinate potrebbero non generare un percorso completo. Ad esempio, il metodo [System. Management. Automation. provider. Navigationcmdletprovider. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) per il provider FileSystem potrebbe ricevere "Windows\System32" nel parametro `parent` e "ABC. dll" nel parametro `child`. Il metodo unisce questi valori al separatore "\\" e restituisce "windows\system32\abc.dll", che non è un percorso di file system completo.

  > [!IMPORTANT]
  > Le parti del percorso fornite nella chiamata a [System. Management. Automation. provider. Navigationcmdletprovider. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) potrebbero contenere caratteri non consentiti nello spazio dei nomi del provider. Questi caratteri vengono probabilmente usati per l'espansione con caratteri jolly e l'implementazione di questo metodo non deve rimuoverli.

## <a name="retrieving-the-parent-path"></a>Recupero del percorso padre

I provider di navigazione di Windows PowerShell implementano il metodo [System. Management. Automation. provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) per recuperare la parte padre del percorso specifico del provider completo o parziale indicato. Il metodo rimuove la parte figlio del percorso e restituisce la parte del percorso padre. Il parametro `root` specifica il percorso completo della radice di un'unità. Questo parametro può essere null o vuoto se un'unità montata non è in uso per l'operazione di recupero. Se viene specificata una radice, il metodo deve restituire un percorso a un contenitore nella stessa struttura ad albero della radice.

Il provider di navigazione di esempio non esegue l'override di questo metodo, ma usa l'implementazione predefinita.
Accetta i percorsi che usano sia "/" che "\\" come separatori di percorso. Per prima cosa normalizza il percorso in modo che includa solo separatori "\\", quindi suddivide il percorso padre all'ultimo "\\" e restituisce il percorso padre.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Per ricordare l'implementazione di GetParentPath

L'implementazione del metodo [System. Management. Automation. provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) deve suddividere il percorso in modo lessicale nel separatore di percorso per lo spazio dei nomi del provider. Ad esempio, il provider FileSystem usa questo metodo per cercare l'ultimo "\\" e restituisce tutti gli elementi a sinistra del separatore.

## <a name="retrieve-the-child-path-name"></a>Recuperare il nome del percorso figlio

Il provider di navigazione implementa il metodo [System. Management. Automation. provider. Navigationcmdletprovider. getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) per recuperare il nome (elemento foglia) del figlio dell'elemento che si trova nel percorso specifico del provider completo o parziale.

Il provider di navigazione di esempio non esegue l'override di questo metodo. Di seguito è illustrata l'implementazione predefinita. Accetta i percorsi che usano sia "/" che "\\" come separatori di percorso. Per prima cosa normalizza il percorso in modo che includa solo separatori "\\", quindi suddivide il percorso padre all'ultimo "\\" e restituisce il nome della parte del percorso figlio.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Aspetti da ricordare sull'implementazione di getchildname

L'implementazione del metodo [System. Management. Automation. provider. Navigationcmdletprovider. getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) deve suddividere il percorso in modo lessicale nel separatore di percorso. Se il percorso fornito non contiene separatori di percorso, il metodo deve restituire il percorso senza modifiche.

> [!IMPORTANT]
> Il percorso specificato nella chiamata a questo metodo potrebbe contenere caratteri non validi nello spazio dei nomi del provider. Questi caratteri vengono usati più spesso per l'espansione con caratteri jolly o per la corrispondenza di espressioni regolari e l'implementazione di questo metodo non deve rimuoverli.

## <a name="determining-if-an-item-is-a-container"></a>Determinare se un elemento è un contenitore

Il provider di navigazione può implementare il metodo [System. Management. Automation. provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) per determinare se il percorso specificato indica un contenitore. Restituisce true se il percorso rappresenta un contenitore e false in caso contrario. Questo metodo è necessario per l'utente per poter utilizzare il cmdlet `Test-Path` per il percorso specificato.

Il codice seguente illustra l'implementazione di [System. Management. Automation. provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) nel provider di navigazione di esempio. Il metodo verifica che il percorso specificato sia corretto e se la tabella esiste e restituisce true se il percorso indica un contenitore.

[!code-csharp[AccessDBProviderSample05.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Aspetti da ricordare sull'implementazione di IsItemContainer

La classe .NET del provider di navigazione potrebbe dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questo caso, l'implementazione di [System. Management. Automation. provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) deve garantire che il percorso passato soddisfi i requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio la proprietà [System. Management. Automation. provider. CmdletProvider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) .

## <a name="moving-an-item"></a>Trasferimento di un elemento

Per supportare il cmdlet `Move-Item`, il provider di navigazione implementa il metodo [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . Questo metodo sposta l'elemento specificato dal parametro `path` nel contenitore nel percorso specificato nel parametro `destination`.

Il provider di navigazione di esempio non esegue l'override del metodo [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . Di seguito è riportata l'implementazione predefinita.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Aspetti da ricordare sull'implementazione di MoveItem

La classe .NET del provider di navigazione potrebbe dichiarare le funzionalità del provider di ExpandWildcards, Filter, include o Exclude dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . In questo caso, l'implementazione di [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) deve garantire che il percorso passato soddisfi i requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio la proprietà **CmdletProvider. Exclude** .

Per impostazione predefinita, le sostituzioni di questo metodo non devono spostare gli oggetti sugli oggetti esistenti a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. Ad esempio, il provider FileSystem non copierà c:\temp\abc.txt su un file c:\bar.txt esistente a meno che la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non sia impostata su `true`. Se il percorso specificato nel parametro `destination` esiste ed è un contenitore, la proprietà [System. Management. Automation. provider. CmdletProvider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) non è obbligatoria. In questo caso, [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) deve spostare l'elemento indicato dal parametro `path` nel contenitore indicato dal parametro `destination` come figlio.

L'implementazione del metodo [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e verificare il relativo valore restituito prima di apportare eventuali modifiche all'archivio dati. Questo metodo viene usato per confermare l'esecuzione di un'operazione quando viene apportata una modifica allo stato del sistema, ad esempio l'eliminazione di file.
[System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare all'utente, con il runtime di Windows PowerShell che prende in considerazione le impostazioni della riga di comando o le variabili di preferenza per determinare gli elementi da visualizzare all'utente.

Dopo che la chiamata a [System. Management. Automation. provider. CmdletProvider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il metodo [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) deve chiamare il metodo [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Questo metodo invia un messaggio all'utente per consentire il feedback per indicare se l'operazione deve essere continuata. Il provider deve chiamare [System. Management. Automation. provider. CmdletProvider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) come controllo aggiuntivo per le modifiche di sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Associazione di parametri dinamici al cmdlet Move-Item

A volte il cmdlet `Move-Item` richiede parametri aggiuntivi che vengono forniti dinamicamente in fase di esecuzione. Per fornire questi parametri dinamici, il provider di navigazione deve implementare il metodo [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) per ottenere i valori di parametro necessari dall'elemento nel percorso indicato e restituire un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Questo provider di navigazione non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di [System. Management. Automation. provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalizzazione di un percorso relativo

Il provider di navigazione implementa il metodo [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) per normalizzare il percorso completo indicato nel parametro `path` come relativo al percorso specificato dal parametro `basePath`. Il metodo restituisce una rappresentazione di stringa del percorso normalizzato. Scrive un errore se il parametro `path` specifica un percorso inesistente.

Il provider di navigazione di esempio non esegue l'override di questo metodo. Di seguito è riportata l'implementazione predefinita.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Aspetti da ricordare sull'implementazione di NormalizeRelativePath

L'implementazione di [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) deve analizzare il parametro `path`, ma non è necessario usare l'analisi puramente sintattica. Si consiglia di progettare questo metodo in modo da usare il percorso per cercare le informazioni sul percorso nell'archivio dati e creare un percorso che corrisponda alla sintassi di maiuscole e minuscole e al percorso standardizzato.

## <a name="code-sample"></a>Codice di esempio

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetti e formattazione

Un provider può aggiungere membri a oggetti esistenti o definire nuovi oggetti. Per ulteriori informazioni, vedere[estensione di tipi di oggetti e formattazione](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-windows-powershell-provider"></a>Compilazione del provider di Windows PowerShell

Per ulteriori informazioni, vedere [come registrare i cmdlet, i provider e le applicazioni host](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Test del provider di Windows PowerShell

Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile testarlo eseguendo i cmdlet supportati dalla riga di comando, inclusi i cmdlet resi disponibili dalla derivazione. In questo esempio viene testato il provider di navigazione di esempio.

1. Eseguire la nuova shell e usare il cmdlet `Set-Location` per impostare il percorso in modo da indicare il database di Access.

   ```powershell
   Set-Location mydb:
   ```

2. A questo punto, eseguire il cmdlet `Get-Childitem` per recuperare un elenco degli elementi del database, ovvero le tabelle di database disponibili. Per ogni tabella, questo cmdlet recupera anche il numero di righe della tabella.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```Output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Utilizzare di nuovo il cmdlet `Set-Location` per impostare il percorso della tabella dati Employees.

   ```powershell
   Set-Location Employees
   ```

4. A questo punto è possibile usare il cmdlet `Get-Location` per recuperare il percorso della tabella Employees.

   ```powershell
   Get-Location
   ```

   ```Output
   Path
   ----
   mydb:\Employees
   ```

5. A questo punto, usare il cmdlet `Get-Childitem` inviato tramite pipe al cmdlet `Format-Table`. Questo set di cmdlet recupera gli elementi della tabella dati Employees, che corrispondono alle righe della tabella. Sono formattati come specificato dal cmdlet `Format-Table`.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```Output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. È ora possibile eseguire il cmdlet `Get-Item` per recuperare gli elementi per la riga 0 della tabella dati Employees.

   ```powershell
   Get-Item 0
   ```

   ```Output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Utilizzare di nuovo il cmdlet `Get-Item` per recuperare i dati dei dipendenti per gli elementi nella riga 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```Output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Vedere anche

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Progettare il provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estensione di tipi di oggetti e formattazione](/previous-versions/ms714665(v=vs.85))

[Implementare un provider di Windows PowerShell per contenitori](./creating-a-windows-powershell-container-provider.md)

[Come registrare cmdlet, provider e applicazioni host](/previous-versions/ms714644(v=vs.85))

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
