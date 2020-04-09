---
title: Creazione di un provider di unità di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 88be7cc6cc0ab54604bc9de71e0ae07c20457514
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978458"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Creazione di un provider di unità di Windows PowerShell

Questo argomento descrive come creare un provider di unità di Windows PowerShell che fornisce un modo per accedere a un archivio dati tramite un'unità di Windows PowerShell. Questo tipo di provider è anche noto come provider di unità di Windows PowerShell. Le unità di Windows PowerShell utilizzate dal provider forniscono i mezzi per connettersi all'archivio dati.

Il provider di unità di Windows PowerShell descritto di seguito consente di accedere a un database di Microsoft Access.
Per questo provider, l'unità di Windows PowerShell rappresenta il database (è possibile aggiungere un numero qualsiasi di unità a un provider di unità), i contenitori di livello superiore dell'unità rappresentano le tabelle nel database e gli elementi dei contenitori rappresentano le righe nelle tabelle.

## <a name="defining-the-windows-powershell-provider-class"></a>Definizione della classe del provider di Windows PowerShell

Il provider di unità deve definire una classe .NET che deriva dalla classe di base [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Di seguito è illustrata la definizione di classe per questo provider di unità:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="29-30":::

Si noti che in questo esempio l'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) specifica un nome descrittivo per il provider e le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando.
I valori possibili per le funzionalità del provider sono definiti dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Questo provider di unità non supporta nessuna di queste funzionalità.

## <a name="defining-base-functionality"></a>Definizione della funzionalità di base

Come descritto nella pagina relativa alla [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) deriva dalla classe di base [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) che definisce i metodi necessari per l'inizializzazione e l'annullamento dell'inizializzazione del provider. Per implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio di risorse utilizzate dal provider, vedere [creazione di un provider di Windows PowerShell di base](./creating-a-basic-windows-powershell-provider.md).
Tuttavia, la maggior parte dei provider (incluso il provider descritto qui) può usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

## <a name="creating-drive-state-information"></a>Creazione di informazioni sullo stato dell'unità

Tutti i provider di Windows PowerShell sono considerati senza stato, il che significa che il provider di unità deve creare tutte le informazioni sullo stato necessarie al runtime di Windows PowerShell quando chiama il provider.

Per questo provider di unità, le informazioni sullo stato includono la connessione al database mantenuto come parte delle informazioni sull'unità. Ecco il codice che Mostra come queste informazioni vengono archiviate nell'oggetto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) che descrive l'unità:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="130-151":::

## <a name="creating-a-drive"></a>Creazione di un'unità

Per consentire al runtime di Windows PowerShell di creare un'unità, il provider di unità deve implementare il metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) . Il codice seguente illustra l'implementazione del metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) per questo provider di unità:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="42-84":::

L'override di questo metodo deve eseguire le operazioni seguenti:

- Verificare che il membro [System. Management. Automation. PSDriveinfo. root *](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) esista e che sia possibile effettuare una connessione all'archivio dati.
- Creare un'unità e popolare il membro della connessione, in supporto del cmdlet `New-PSDrive`.
- Convalidare l'oggetto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) per l'unità proposta.
- Modificare l'oggetto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) che descrive l'unità con le informazioni sulle prestazioni o sull'affidabilità richieste oppure fornire dati aggiuntivi per i chiamanti che usano l'unità.
- Gestire gli errori usando il metodo [System. Management. Automation. provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) e quindi restituire `null`.

  Questo metodo restituisce le informazioni sull'unità passate al metodo o a una versione specifica del provider.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Associazione di parametri dinamici a nuovaunità

Il cmdlet `New-PSDrive` supportato dal provider di unità potrebbe richiedere parametri aggiuntivi. Per alleghi questi parametri dinamici al cmdlet, il provider implementa il metodo [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) . Questo metodo restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Questo provider di unità non esegue l'override di questo metodo. Tuttavia, nel codice seguente viene illustrata l'implementazione predefinita di questo metodo:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Rimozione di un'unità

Per chiudere la connessione al database, il provider di unità deve implementare il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) . Questo metodo chiude la connessione all'unità dopo avere pulito le informazioni specifiche del provider.

Il codice seguente illustra l'implementazione del metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) per questo provider di unità:

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="91-116":::

Se è possibile rimuovere l'unità, il metodo deve restituire le informazioni passate al metodo tramite il parametro `drive`. Se non è possibile rimuovere l'unità, il metodo deve scrivere un'eccezione e quindi restituire `null`. Se il provider non esegue l'override di questo metodo, l'implementazione predefinita di questo metodo restituisce solo le informazioni sull'unità passate come input.

## <a name="initializing-default-drives"></a>Inizializzazione di unità predefinite

Il provider di unità implementa il metodo [System. Management. Automation. provider. Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) per montare le unità. Il provider di Active Directory, ad esempio, può montare un'unità per il contesto dei nomi predefinito se il computer è aggiunto a un dominio.

Questo metodo restituisce una raccolta di informazioni sulle unità inizializzate o una raccolta vuota. La chiamata a questo metodo viene eseguita dopo che il runtime di Windows PowerShell chiama il metodo [System. Management. Automation. provider. CmdletProvider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) per inizializzare il provider.

Questo provider di unità non esegue l'override del metodo [System. Management. Automation. provider. Drivecmdletprovider. Initializedefaultdrives *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) . Tuttavia, nel codice seguente viene illustrata l'implementazione predefinita, che restituisce una raccolta di unità vuota:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Aspetti da ricordare sull'implementazione di InitializeDefaultDrives

Tutti i provider di unità devono montare un'unità radice per aiutare l'utente a individuarlo. L'unità radice potrebbe elencare le posizioni che funge da radice per altre unità montate. Ad esempio, il provider di Active Directory potrebbe creare un'unità in cui sono elencati i contesti di denominazione trovati negli attributi di `namingContext` sull'ambiente di sistema distribuito radice (DSE). Ciò consente agli utenti di individuare i punti di montaggio per altre unità.

## <a name="code-sample"></a>Codice di esempio

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Test del provider di unità di Windows PowerShell

Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile testarlo eseguendo i cmdlet supportati dalla riga di comando, inclusi tutti i cmdlet resi disponibili dalla derivazione. Testiamo il provider di unità di esempio.

1. Eseguire il cmdlet `Get-PSProvider` per recuperare l'elenco dei provider per verificare che sia presente il provider dell'unità AccessDB:

   **> PS `Get-PSProvider`**

   Viene visualizzato l'output seguente:

   ```Output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Assicurarsi che esista un nome del server di database (DSN) per il database accedendo alla parte **origini dati** degli **strumenti di amministrazione** per il sistema operativo. Nella tabella **DSN utente** fare doppio clic su **database di MS Access** e aggiungere il percorso dell'unità `C:\ps\northwind.mdb`.

3. Creare una nuova unità utilizzando il provider di unità di esempio:

   ```powershell
   new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb`
   ```

   Viene visualizzato l'output seguente:

   ```Output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Convalidare la connessione. Poiché la connessione è definita come membro dell'unità, è possibile verificarla utilizzando il cmdlet Get-PDDrive.

   > [!NOTE]
   > L'utente non può ancora interagire con il provider come unità, perché il provider richiede la funzionalità del contenitore per tale interazione. Per ulteriori informazioni, vedere [creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **PS > (Get-PSDrive MyDB). Connection**

   Viene visualizzato l'output seguente:

   ```Output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Rimuovere l'unità e uscire dalla shell:

   ```powershell
   PS> remove-psdrive mydb
   PS> exit
   ```

## <a name="see-also"></a>Vedere anche

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Progettare il provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Creazione di un provider di Windows PowerShell di base](./creating-a-basic-windows-powershell-provider.md)
