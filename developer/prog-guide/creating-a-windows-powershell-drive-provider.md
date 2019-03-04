---
title: Creazione di un Provider di unità di PowerShell di Windows | Microsoft Docs
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
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855797"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Creazione di un provider di unità di Windows PowerShell

Questo argomento descrive come creare un provider di unità di Windows PowerShell che fornisce un modo per accedere a un archivio dati tramite un'unità di Windows PowerShell. Questo tipo di provider è detta anche i provider di unità di Windows PowerShell. Le unità di Windows PowerShell utilizzate dal provider forniscono i mezzi per la connessione all'archivio dati.

Il provider dell'unità Windows PowerShell descritto di seguito fornisce l'accesso a un database Microsoft Access. Per questo provider, l'unità di Windows PowerShell rappresenta il database (è possibile aggiungere qualsiasi numero di unità a un provider dell'unità), i contenitori di primo livello dell'unità rappresentano le tabelle nel database e gli elementi dei contenitori rappresentano le righe in le tabelle.

Ecco un elenco delle sezioni in questo argomento. Se non si ha familiarità con la scrittura di un provider di unità di Windows PowerShell, leggere le sezioni riportate nell'ordine in cui appaiono. Tuttavia, se si ha familiarità con la scrittura di un provider dell'unità, passare direttamente alle informazioni necessarie.

- [Definizione della classe di Provider PowerShell per Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definizione funzionalità di Base](#Defining-Base-Functionality)

- [Creazione di informazioni sullo stato unità](#Creating-Drive-State-Information)

- [Creazione di un'unità](#Creating-a-Drive)

- [Associazione di parametri dinamici a NewDrive](#Attaching-Dynamic-Parameters-to-NewDrive)

- [Rimozione di un'unità](#Removing-a-Drive)

- [L'inizializzazione predefinita di unità](#Initializing-Default-Drives)

- [Esempio di codice](#Code-Sample)

- [Test del Provider di unità di PowerShell di Windows](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definizione della classe di Provider PowerShell per Windows

Il provider dell'unità deve definire una classe .NET che deriva dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe di base. Ecco la definizione di classe per questo provider dell'unità:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Si noti che in questo esempio, il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo specifica un nome descrittivo per il provider e le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. I valori possibili per le funzionalità del provider sono definiti per il [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. Questo provider dell'unità non supporta uno qualsiasi di queste funzionalità.

## <a name="defining-base-functionality"></a>Definizione funzionalità di Base

Come descritto in [Provider di progettazione di Windows PowerShell](./designing-your-windows-powershell-provider.md), il [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) deriva dalla classe di [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base che definisce i metodi necessari per l'inizializzazione e annullamento dell'inizializzazione del provider. Per implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio delle risorse usate dal provider, vedere [creazione di un PowerShell Provider di Windows base](./creating-a-basic-windows-powershell-provider.md). Tuttavia, la maggior parte dei fornitori (tra cui il provider descritto di seguito) è possono usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.

## <a name="creating-drive-state-information"></a>Creazione di informazioni sullo stato unità

Tutti i provider Windows PowerShell sono considerati senza stati, il che significa che il provider di unità deve creare eventuali informazioni sullo stato necessarie per il runtime di Windows PowerShell quando si chiama il provider.

Per questo provider dell'unità, le informazioni sullo stato includono la connessione al database che viene mantenuto come parte di informazioni sull'unità. Ecco il codice che illustra come queste informazioni vengono archiviate nel [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) che descrive l'unità:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Creazione di un'unità

Per consentire al runtime di Windows PowerShell creare un'unità, il provider dell'unità deve implementare il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) (metodo). Il codice seguente viene illustrata l'implementazione del [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metodo per questo provider dell'unità:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

L'override di questo metodo deve eseguire le operazioni seguenti:

- Verificare che il [System.Management.Automation.Psdriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) membro esista e che può essere stabilita una connessione all'archivio dati.

- Creare un'unità e popolare il membro di connessione, supportare la `New-PSDrive` cmdlet.

- Convalidare il [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) oggetto per l'unità proposto.

- Modificare il [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) dell'oggetto che descrive l'unità con qualsiasi informazione di affidabilità o le prestazioni necessarie o fornire dati aggiuntivi per i chiamanti utilizzano l'unità.

- Gestire gli errori usando il [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodo e quindi restituirla `null`.

  Questo metodo restituisce le informazioni unità che è state passate al metodo o una versione specifica del provider.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Associazione di parametri dinamici a NewDrive

Il `New-PSDrive` cmdlet supportati dal provider di unità potrebbero richiedere parametri aggiuntivi. Per collegare questi parametri dinamici al cmdlet, il provider implementa il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) (metodo). Questo metodo restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto.

Questo provider dell'unità non esegue l'override di questo metodo. Tuttavia, il codice seguente illustra l'implementazione predefinita di questo metodo:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Rimozione di un'unità

Per chiudere la connessione al database, il provider dell'unità deve implementare il [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) (metodo). Questo metodo chiude la connessione all'unità dopo la pulizia di eventuali informazioni specifiche del provider.

Il codice seguente viene illustrata l'implementazione del [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metodo per questo provider dell'unità:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Se l'unità può essere rimosso, il metodo deve restituire le informazioni passate al metodo attraverso il `drive` parametro. Se l'unità non può essere rimosso, il metodo deve scrivere un'eccezione e quindi restituire `null`. Se il provider non esegue l'override di questo metodo, l'implementazione predefinita di questo metodo restituisce solo le informazioni dell'unità passate come input.

## <a name="initializing-default-drives"></a>L'inizializzazione predefinita di unità

Implementa il provider unità il [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metodo montare unità. Il provider di Active Directory, ad esempio, potrebbe essere montata un'unità per il contesto dei nomi se il computer è unito a un dominio predefinito.

Questo metodo restituisce una raccolta di unità di informazioni sulle unità inizializzata o una raccolta vuota. Viene effettuata la chiamata a questo metodo dopo le chiamate di runtime di Windows PowerShell il [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodo per inizializzare il provider.

Questo provider dell'unità non esegue l'override di [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) (metodo). Tuttavia, il codice seguente illustra l'implementazione predefinita che restituisce una raccolta di unità vuote:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Aspetti da ricordare sull'implementazione InitializeDefaultDrives

Tutti i provider di unità è consigliabile montare un'unità radice per consentire all'utente con l'individuazione. L'unità radice potrebbe elencare i percorsi che fungono da radici di altre unità montate. Ad esempio, il provider di Active Directory potrebbe creare un'unità in cui sono elencati i contesti dei nomi disponibili nel `namingContext` attributi nella directory principale ambiente di sistema distribuita (DSE). Ciò consente agli utenti di individuare i punti di montaggio per le altre unità.

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Test del Provider di unità di PowerShell di Windows

Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile eseguirne il test eseguendo il cmdlet supportati nella riga di comando, inclusi tutti i cmdlet resi disponibili dalla derivazione. È possibile testare il provider di unità di esempio.

1. Eseguire il `Get-PSProvider` cmdlet per recuperare l'elenco dei provider per assicurare che il provider dell'unità AccessDB sia presente:

   **PS> `Get-PSProvider`**

   Viene visualizzato l'output seguente:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Verificare l'esistenza di un nome di server di database (DSN) per il database tramite l'accesso di **Zdroje dat** parte del **strumenti di amministrazione** per il sistema operativo. Nel **DSN utente** tabella, fare doppio clic su **MS accesso Database** e aggiungere il percorso di unità C:\ps\northwind.mdb.

3. Creare una nuova unità utilizzando il provider di unità di esempio:

   **PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**

   Viene visualizzato l'output seguente:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Convalidare la connessione. Poiché la connessione è definita come membro dell'unità, è possibile archiviarlo tramite il cmdlet Get-PDDrive.

   > [!NOTE]
   > L'utente non è ancora interagire con il provider come un'unità, quando la funzionalità contenitore sono necessari per il provider per tale interazione. Per altre informazioni, vedere [creazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).

   **PS > .connection (mydb get-psdrive)**

   Viene visualizzato l'output seguente:

   ```output
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

   **PS > remove-psdrive mydb**

   **PS > uscire**

## <a name="see-also"></a>Vedere anche

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Progettare il Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)

[Creazione di un Provider PowerShell di Windows di base](./creating-a-basic-windows-powershell-provider.md)