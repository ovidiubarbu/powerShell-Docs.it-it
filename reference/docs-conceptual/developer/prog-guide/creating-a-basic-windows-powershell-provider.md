---
title: Creazione di un provider di base di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: e825581b96f0f33893b38f9f6499dd46a7bf38eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360520"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Creazione di un provider di Windows PowerShell di base

Questo argomento è il punto di partenza per apprendere come creare un provider di Windows PowerShell. Il provider di base descritto di seguito fornisce i metodi per l'avvio e l'arresto del provider e anche se questo provider non fornisce un mezzo per accedere a un archivio dati o per ottenere o impostare i dati nell'archivio dati, fornisce le funzionalità di base richieste da tutti i provider.

Come indicato in precedenza, il provider di base descritto di seguito implementa i metodi per l'avvio e l'arresto del provider. Il runtime di Windows PowerShell chiama questi metodi per inizializzare e annullare l'inizializzazione del provider.

> [!NOTE]
> È possibile trovare un esempio di questo provider nel file AccessDBSampleProvider01.cs fornito da Windows PowerShell.

## <a name="defining-the-windows-powershell-provider-class"></a>Definizione della classe del provider di Windows PowerShell

Il primo passaggio nella creazione di un provider di Windows PowerShell consiste nel definirne la classe .NET. Questo provider di base definisce una classe denominata `AccessDBProvider` che deriva dalla classe di base [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

Si consiglia di inserire le classi del provider in uno spazio dei nomi `Providers` dello spazio dei nomi dell'API, ad esempio, xxx. PowerShell. Providers. Questo provider usa lo spazio dei nomi `Microsoft.Samples.PowerShell.Provider`, in cui vengono eseguiti tutti gli esempi del provider di Windows PowerShell.

> [!NOTE]
> La classe per un provider di Windows PowerShell deve essere contrassegnata in modo esplicito come Public. Per impostazione predefinita, le classi non contrassegnate come pubbliche saranno interne e non verranno trovate dal runtime di Windows PowerShell.

Di seguito è illustrata la definizione della classe per il provider Basic:

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Immediatamente prima della definizione della classe, è necessario dichiarare l'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) , con la sintassi [CmdletProvider ()].

È possibile impostare le parole chiave degli attributi per dichiarare ulteriormente la classe se necessario. Si noti che l'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) dichiarato qui include due parametri. Il primo parametro attribute specifica il nome descrittivo predefinito per il provider, che può essere modificato successivamente dall'utente. Il secondo parametro specifica le funzionalità definite da Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. I valori possibili per le funzionalità del provider sono definiti dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . Poiché si tratta di un provider di base, non supporta alcuna funzionalità.

> [!NOTE]
> Il nome completo del provider di Windows PowerShell include il nome dell'assembly e altri attributi determinati da Windows PowerShell al momento della registrazione del provider.

## <a name="defining-provider-specific-state-information"></a>Definizione delle informazioni sullo stato specifiche del provider

La classe di base [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) e tutte le classi derivate sono considerate senza stato perché il runtime di Windows PowerShell crea le istanze del provider solo se necessario. Pertanto, se il provider richiede il controllo completo e la manutenzione dello stato per i dati specifici del provider, deve derivare una classe dalla classe [System. Management. Automation. ProviderInfo restituito da](/dotnet/api/System.Management.Automation.ProviderInfo) . La classe derivata deve definire i membri necessari per mantenere lo stato in modo che sia possibile accedere ai dati specifici del provider quando il runtime di Windows PowerShell chiama il metodo [System. Management. Automation. provider. CmdletProvider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) per inizializzare il provider.

Un provider di Windows PowerShell è inoltre in grado di mantenere lo stato basato sulla connessione. Per ulteriori informazioni sulla gestione dello stato della connessione, vedere la pagina relativa alla [creazione di un provider di unità PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Inizializzazione del provider

Per inizializzare il provider, il runtime di Windows PowerShell chiama il metodo [System. Management. Automation. provider. CmdletProvider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) all'avvio di Windows PowerShell. Nella maggior parte dei casi, il provider può usare l'implementazione predefinita di questo metodo, che restituisce semplicemente l'oggetto [System. Management. Automation. ProviderInfo restituito da](/dotnet/api/System.Management.Automation.ProviderInfo) che descrive il provider. Tuttavia, nel caso in cui si desideri aggiungere ulteriori informazioni di inizializzazione, è necessario implementare il metodo [System. Management. Automation. provider. CmdletProvider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) che restituisce una versione modificata del [ Oggetto System. Management. Automation. ProviderInfo restituito da](/dotnet/api/System.Management.Automation.ProviderInfo) passato al provider. In generale, questo metodo deve restituire l'oggetto [System. Management. Automation. ProviderInfo restituito da](/dotnet/api/System.Management.Automation.ProviderInfo) fornito o un oggetto [System. Management. Automation. ProviderInfo restituito da](/dotnet/api/System.Management.Automation.ProviderInfo) modificato che contiene altre informazioni di inizializzazione.

Questo provider di base non esegue l'override di questo metodo. Tuttavia, nel codice seguente viene illustrata l'implementazione predefinita di questo metodo:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Il provider può mantenere lo stato delle informazioni specifiche del provider, come descritto in [definizione dello stato dei dati specifico del provider](#defining-provider-specific-state-information). In questo caso, l'implementazione deve eseguire l'override del metodo [System. Management. Automation. provider. CmdletProvider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) per restituire un'istanza della classe derivata.

## <a name="start-dynamic-parameters"></a>Avvia parametri dinamici

L'implementazione del provider del metodo [System. Management. Automation. provider. CmdletProvider. Start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) potrebbe richiedere parametri aggiuntivi. In questo caso, il provider deve eseguire l'override del metodo [System. Management. Automation. provider. CmdletProvider. Startdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) e restituire un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a [ Oggetto System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Questo provider di base non esegue l'override di questo metodo. Tuttavia, nel codice seguente viene illustrata l'implementazione predefinita di questo metodo:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Annullamento dell'inizializzazione del provider

Per liberare le risorse utilizzate dal provider di Windows PowerShell, il provider deve implementare il proprio metodo [System. Management. Automation. provider. CmdletProvider. Stop *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) . Questo metodo viene chiamato dal runtime di Windows PowerShell per annullare l'inizializzazione del provider alla chiusura di una sessione.

Questo provider di base non esegue l'override di questo metodo. Tuttavia, nel codice seguente viene illustrata l'implementazione predefinita di questo metodo:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Test del provider di Windows PowerShell

Dopo aver registrato il provider di Windows PowerShell con Windows PowerShell, è possibile testarlo eseguendo i cmdlet supportati nella riga di comando. Per questo provider di base, eseguire la nuova shell e usare il cmdlet `Get-PSProvider` per recuperare l'elenco di provider e verificare che sia presente il provider AccessDb.

```powershell
Get-PSProvider
```

Viene visualizzato l'output seguente:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Vedere anche

[Creazione di provider di Windows PowerShell](./how-to-create-a-windows-powershell-provider.md)

[Progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)
