---
title: Creazione di un Provider di navigazione di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 5f7a61e261399d3d2abe62fe4523e8c9895d5ad4
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855164"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Creazione di un provider di navigazione di Windows PowerShell

In questo argomento viene descritto come creare un provider di navigazione di Windows PowerShell che può passare l'archivio dati. Questo tipo di provider supporta comandi ricorsiva, i contenitori nidificati e i percorsi relativi.

> [!NOTE]
> È possibile scaricare il C# file di origine (AccessDBSampleProvider05.cs) per questo provider tramite il Microsoft Windows Software Development Kit per Windows Vista e i componenti di Runtime di .NET Framework 3.0. Per istruzioni sul download, vedere [come installare Windows PowerShell e il Download di Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Sono disponibili in file di origine scaricato il  **\<esempi di PowerShell >** directory.
>
> Per altre informazioni sulle altre implementazioni del provider di Windows PowerShell, vedere [la progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md).

Il provider descritto di seguito consente l'handle dell'utente un database di Access come un'unità in modo che l'utente possa passare alle tabelle di dati nel database. Quando si crea un proprio provider di navigazione, è possibile implementare i metodi che possono rendere drivequalified percorsi necessari per la navigazione, normalizzare i percorsi relativi, spostare gli elementi dell'archivio dati, nonché i metodi che ottenere i nomi di figlio e ottenere il percorso padre di un elemento di test per identificare se un elemento è un contenitore.

> [!CAUTION]
> Tenere presente che questa progettazione si presuppone che un database con un campo con l'ID del nome e che il tipo del campo è LongInteger.

## <a name="define-the-windows-powershell-provider"></a>Definire il provider di Windows PowerShell

Un provider di navigazione di Windows PowerShell è necessario creare una classe .NET che deriva dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe di base. Ecco la definizione di classe per il provider di spostamento descritte in questa sezione.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Si noti che questo provider, il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo include due parametri. Il primo parametro specifica un nome descrittivo per il provider usato da Windows PowerShell. Il secondo parametro specifica le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. Per questo provider, non sono disponibili funzionalità specifiche di Windows PowerShell che vengono aggiunti.

## <a name="defining-base-functionality"></a>Definizione funzionalità di Base

Come descritto in [Design Your PS Provider](./designing-your-windows-powershell-provider.md), il [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe base derivi da altre classi che ha fornito provider diverso funzionalità. Un provider di navigazione di Windows PowerShell, pertanto, è necessario definire tutte le funzionalità fornite da tali classi.

Per implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio delle risorse usate dal provider, vedere [creazione di un Provider di PS base](./creating-a-basic-windows-powershell-provider.md). Tuttavia, la maggior parte dei fornitori (tra cui il provider descritto di seguito) è possono usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

Per ottenere l'accesso all'archivio dati tramite un'unità di Windows PowerShell, è necessario implementare i metodi del [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe di base. Per altre informazioni sull'implementazione di questi metodi, vedere [creazione di un Provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md).

Per modificare gli elementi di un archivio dati, ad esempio il recupero, impostazione e cancellare elementi, il provider deve implementare i metodi forniti dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe di base. Per altre informazioni sull'implementazione di questi metodi, vedere [creazione di un Provider di Windows PowerShell elemento](./creating-a-windows-powershell-item-provider.md).

Per ottenere gli elementi figlio o i nomi, dell'archivio dati, nonché i metodi che creano, copiano, rinominano e rimuovere elementi, è necessario implementare i metodi forniti dal [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)classe di base. Per altre informazioni sull'implementazione di questi metodi, vedere [creazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Creazione di un percorso di Windows PowerShell

Provider di navigazione di Windows PowerShell utilizzare un percorso di Windows PowerShell interna al provider per passare gli elementi dell'archivio dati. Per creare un percorso interna al provider il provider deve implementare il [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metodo supporta la chiama del cmdlet Combine-Path. Questo metodo combina un percorso padre e figlio in un percorso di provider interno, usando un separatore di percorso specifico del provider tra i percorsi padre e figlio.

L'implementazione predefinita accetta percorsi con "/" o "\\"come separatore di percorso, Normalizza il separatore di percorso"\\" combina le parti del percorso padre e figlio con il separatore tra di essi e quindi restituisce una stringa che contiene il percorsi combinati.

Questo provider di navigazione non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita del [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) (metodo).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Aspetti da ricordare sull'implementazione MakePath

Le condizioni seguenti possono si applicano all'implementazione di [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- L'implementazione del [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metodo non deve convalidare il percorso come un percorso completo valido nello spazio dei nomi del provider. Tenere presente che ogni parametro può rappresentare solo una parte di un percorso e le parti combinate non potrebbero generare un percorso completo. Ad esempio, il [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metodo per il provider filesystem potrebbe ricevere "windows\system32" nel `parent` parametro e "abc. dll" nel `child` parametro. Il metodo viene aggiunto a questi valori con la "\\" seguito dal separatore e restituisce "windows\system32\abc.dll", che non è un percorso completo.

  > [!IMPORTANT]
  > Le parti del percorso fornite nella chiamata a [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) potrebbe contenere caratteri non consentiti nello spazio dei nomi del provider. Questi caratteri vengono probabilmente utilizzati per l'espansione di caratteri jolly e l'implementazione di questo metodo non necessario rimuoverli.

## <a name="retrieving-the-parent-path"></a>Recupero del percorso dell'elemento padre

Provider di navigazione di Windows PowerShell implementa il [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) recuperare la parte padre del functoid con registrazione completa o parziale (metodo) percorso specifico del provider. Il metodo rimuove la parte figlio del percorso e restituisce l'elemento padre come parte di percorso. Il `root` parametro specifica il percorso completo della radice di un'unità. Questo parametro può essere null o vuoto se un'unità montata non è in uso per l'operazione di recupero. Se si specifica una radice, il metodo deve restituire un percorso a un contenitore nello stesso albero come radice.

Il provider di navigazione di esempio non esegue l'override di questo metodo, ma utilizza l'implementazione predefinita. Accetta percorsi che usano entrambi "/" e "\\" come separatore di percorso. Innanzitutto Normalizza il percorso è disponibile solo "\\" separatori, quindi divide il percorso padre all'ultimo "\\" e restituisce il percorso padre.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Tenere presente sull'implementazione GetParentPath

L'implementazione del [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metodo deve dividere il tracciato lessicalmente su separatore di percorso per lo spazio dei nomi del provider. Ad esempio, il provider filesystem utilizza questo metodo per cercare l'ultima "\\" e restituisce tutti gli elementi a sinistra del separatore.

## <a name="retrieve-the-child-path-name"></a>Recuperare il nome del percorso figlio

Implementa il provider navigazione il [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metodo per recuperare il nome (elemento foglia) dell'elemento figlio dell'elemento che si trova in alla versione completa indicata o percorso parziale specifico del provider.

Il provider di navigazione di esempio non esegue l'override di questo metodo. Di seguito è riportata l'implementazione predefinita. Accetta percorsi che usano entrambi "/" e "\\" come separatore di percorso. Innanzitutto Normalizza il percorso è disponibile solo "\\" separatori, quindi divide il percorso padre all'ultimo "\\" e restituisce il nome dell'elemento figlio come parte di percorso.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Aspetti da ricordare sull'implementazione GetChildName

L'implementazione del [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metodo deve dividere il tracciato lessicalmente su separatore di percorso. Se il percorso specificato non contiene separatori alcun percorso, il metodo deve restituire il percorso senza modificato.

> [!IMPORTANT]
> Il percorso specificato nella chiamata a questo metodo potrebbe contenere caratteri che non sono validi nello spazio dei nomi del provider. Questi caratteri sono probabilmente usato per la corrispondenza di espressione regolare o espansione di caratteri jolly e l'implementazione di questo metodo non necessario rimuoverli.

## <a name="determining-if-an-item-is-a-container"></a>Determinare se un elemento è un contenitore

Il provider di navigazione può implementare il [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metodo per determinare se il percorso specificato indica un contenitore. Restituisce true se il percorso rappresenta un contenitore e false in caso contrario. L'utente deve essere in grado di usare questo metodo il `Test-Path` cmdlet per il percorso fornito.

Il codice seguente illustra il [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementazione nel nostro provider di navigazione di esempio. Il metodo verifica che il percorso specificato sia corretto e se la tabella esiste e restituisce true se il percorso indica un contenitore.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Aspetti da ricordare sull'implementazione IsItemContainer

Il provider di navigazione classe .NET può dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questo caso, l'implementazione di [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) deve garantire che il percorso passato soddisfi i requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) proprietà.

## <a name="moving-an-item"></a>Spostamento di un elemento

Supportare le `Move-Item` implementa il provider di navigazione di cmdlet, il [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) (metodo). Questo metodo consente di spostare l'elemento specificato tramite il `path` del contenitore nel percorso specificato nel parametro il `destination` parametro.

Il provider di navigazione di esempio non esegue l'override di [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) (metodo). Di seguito è l'implementazione predefinita.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Aspetti da ricordare sull'implementazione MoveItem

Il provider di navigazione classe .NET può dichiarare funzionalità del provider di ExpandWildcards, filtro, inclusione o esclusione, dal [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. In questo caso, l'implementazione di [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) necessario assicurarsi che il percorso passato soddisfi i requisiti. A tale scopo, il metodo deve accedere alla proprietà appropriata, ad esempio, il **CmdletProvider.Exclude** proprietà.

Per impostazione predefinita, gli override di questo metodo devono non spostare gli oggetti tramite gli oggetti esistenti, a meno che il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Ad esempio, il provider filesystem non copierà c:\temp\abc.txt tramite un file esistente c:\bar.txt a meno che non la [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) è impostata su `true`. Se il percorso specificato nella `destination` parametro esista e sia un contenitore, il [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) proprietà non è necessaria. In questo caso, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) consigliabile spostare l'elemento indicato dal `path` parametro per il contenitore indicato dal `destination` parametro come elemento figlio.

L'implementazione del [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metodo deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) e controllare il valore restituito corrispondente prima di apportare modifiche all'archivio dati. Questo metodo viene utilizzato per confermare l'esecuzione di un'operazione quando viene apportata una modifica lo stato del sistema, ad esempio, l'eliminazione di file. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) invia il nome della risorsa da modificare per l'utente, con il runtime di Windows PowerShell prendendo in considerazione eventuali impostazioni riga di comando o variabili di preferenza in determinare ciò che deve essere visualizzato all'utente.

Dopo la chiamata a [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) restituisce `true`, il [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metodo deve chiamare il [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) (metodo). Questo metodo invia un messaggio all'utente per consentire il feedback a dire se l'operazione deve proseguire. Il provider deve chiamare [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) come verifica aggiuntiva per le modifiche del sistema potenzialmente pericolose.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Associare i parametri dinamici per il Cmdlet Move-Item

In alcuni casi il `Move-Item` cmdlet richiede parametri aggiuntivi che vengono forniti in modo dinamico in fase di esecuzione. Per fornire i parametri dinamici, il provider di navigazione deve implementare il [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) metodo per ottenere i valori dei parametri obbligatori dall'elemento in corrispondenza il percorso indicato e restituire un oggetto che dispone di proprietà e campi con l'analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto.

Questo provider di navigazione non implementa questo metodo. Tuttavia, il codice seguente è l'implementazione predefinita di [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalizzazione di un percorso relativo

Implementa il provider navigazione il [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metodo normalizzare il percorso completo è indicato nel `path` parametro come in corso relativo al percorso specificato da di `basePath` parametro. Il metodo restituisce una rappresentazione di stringa del percorso normalizzato. Scrive un errore se il `path` parametro specifica un percorso inesistente.

Il provider di navigazione di esempio non esegue l'override di questo metodo. Di seguito è l'implementazione predefinita.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Aspetti da ricordare sull'implementazione NormalizeRelativePath

L'implementazione di [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) devono analizzare il `path` parametro, ma non è necessario utilizzare l'analisi puramente sintattico. Si sono invitati a progettazione questo metodo per utilizzare il percorso per cercare le informazioni sul percorso dell'archivio dati e creare un percorso che corrisponde alle maiuscole e minuscole e standardizzato sintassi del percorso.

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definizione di tipi di oggetto e formattazione

È possibile che un provider aggiungere i membri per gli oggetti esistenti o definire nuovi oggetti. Per altre informazioni, vedere[estendendo i tipi di oggetto e formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Creazione del provider di Windows PowerShell

Per altre informazioni, vedere [come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Test di un provider Windows PowerShell

Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile eseguirne il test eseguendo il cmdlet supportati nella riga di comando, inclusi i cmdlet resi disponibili dalla derivazione. In questo esempio verrà testati i provider di navigazione di esempio.

1. Eseguire la nuova shell e usare il `Set-Location` cmdlet per impostare il percorso per indicare il database di Access.

   ```powershell
   Set-Location mydb:
   ```

2. Eseguire ora il `Get-Childitem` cmdlet per recuperare un elenco degli elementi del database, quali sono le tabelle di database disponibili. Per ogni tabella, questo cmdlet recupera anche il numero di righe della tabella.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
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

3. Usare il `Set-Location` cmdlet per impostare il percorso della tabella di dati dipendenti.

   ```powershell
   Set-Location Employees
   ```

4. Si usi ora il `Get-Location` cmdlet per recuperare il percorso per la tabella Employees.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. A questo punto usare il `Get-Childitem` cmdlet inviato tramite pipe al `Format-Table` cmdlet. Questo set di cmdlet recupera gli elementi per la tabella di dati dipendenti, quali sono le righe della tabella. Sono formattati come specificato da di `Format-Table` cmdlet.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
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

6. È ora possibile eseguire il `Get-Item` cmdlet per recuperare gli elementi per riga 0 della tabella di dati dipendenti.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Usare il `Get-Item` cmdlet per recuperare i dati dei dipendenti per gli elementi nella riga 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
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

[Provider di progettazione di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Estensione di tipi di oggetto e la formattazione](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementare un provider di contenitori Windows PowerShell](./creating-a-windows-powershell-container-provider.md)

[Come registrare i cmdlet, provider e applicazioni Host](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)