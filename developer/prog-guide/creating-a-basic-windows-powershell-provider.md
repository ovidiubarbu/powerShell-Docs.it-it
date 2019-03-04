---
title: Creazione di un Provider PowerShell di base Windows | Microsoft Docs
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
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861767"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Creazione di un provider di Windows PowerShell di base

In questo argomento è il punto di partenza per apprendere come creare un provider di Windows PowerShell. Il provider di base descritte di seguito fornisce metodi per avviare e arrestare il provider, e sebbene questo provider non fornisce un mezzo per accedere a un archivio dati o per ottenere o impostare i dati nell'archivio dati, è fornire la funzionalità di base richiesto da tutti i provider.

Come accennato in precedenza, il provider di base descritto in questo caso implementa i metodi per avviare e arrestare il provider. Il runtime di Windows PowerShell chiama questi metodi per inizializzare e annullare l'inizializzazione del provider.

> [!NOTE]
> È possibile trovare un esempio di questo provider nel file AccessDBSampleProvider01.cs fornito da Windows PowerShell.

Le sezioni in questo argomento includono quanto segue:

- [Definizione della classe di Provider PowerShell per Windows](#Defining-the-Windows-PowerShell-Provider-Class)

- [La definizione di informazioni sullo stato specifico del Provider](#Defining-Provider-Specific-State-Information)

- [L'inizializzazione del Provider](#Initializing-the-Provider)

- [Parametri dinamici di inizio](#Start-Dynamic-Parameters)

- [Annullamento dell'inizializzazione del Provider](#Uninitializing-the-Provider)

- [Esempio di codice](#Code-Sample)

- [Test di un Provider Windows PowerShell](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definizione della classe di Provider PowerShell per Windows

Il primo passaggio nella creazione di un provider di Windows PowerShell consiste nel definire la classe .NET. Questo provider di base definisce una classe denominata `AccessDBProvider` che deriva dal [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe di base.

Si consiglia di posizionare le classi del provider in un `Providers` dello spazio dei nomi dello spazio dei nomi API, ad esempio, xxx. PowerShell.Providers. Questo provider Usa la `Microsoft.Samples.PowerShell.Provider` dello spazio dei nomi, in cui vengono eseguiti tutti gli esempi di provider di Windows PowerShell.

> [!NOTE]
> La classe per un provider di Windows PowerShell debba essere esplicitamente contrassegnata come pubblica. Le classi non contrassegnate come pubblici per impostazione predefinita saranno interno e non verranno trovate dal runtime di Windows PowerShell.

Ecco la definizione di classe per il provider di base:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Subito prima della definizione di classe, è necessario dichiarare la [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo, con la sintassi [CmdletProvider()].

È possibile impostare le parole chiave di attributo per un'ulteriore dichiarare la classe se necessario. Si noti che il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo dichiarato in questo caso sono inclusi due parametri. Il primo parametro di attributo specifica il nome predefinito per il provider che l'utente può modificare in un secondo momento. Il secondo parametro specifica le funzionalità di Windows PowerShell-definite che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando. I valori possibili per le funzionalità del provider sono definiti per il [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione. Poiché si tratta di un provider di base, non supporta alcuna funzionalità.

> [!NOTE]
> Il nome completo del provider di Windows PowerShell include il nome dell'assembly e altri attributi determinati da Windows PowerShell al momento della registrazione del provider.

## <a name="defining-provider-specific-state-information"></a>La definizione di informazioni sullo stato specifico del Provider

Il [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe di base e tutte le classi derivate sono considerate senza state perché il runtime di Windows PowerShell crea le istanze del provider solo secondo necessità. Pertanto, se il provider richiede il controllo completo e la manutenzione dello stato per i dati specifici del provider, è necessario derivare una classe dal [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) classe. La classe derivata deve definire i membri necessari per mantenere lo stato in modo che i dati specifici del provider sono accessibile quando il runtime di Windows PowerShell viene chiamato il [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodo per inizializzare il provider.

Un provider di Windows PowerShell è anche possibile mantenere lo stato basato sulla connessione. Per altre informazioni sulla gestione dello stato di connessione, vedere [creazione di un Provider di unità di PowerShell](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>L'inizializzazione del Provider

Per inizializzare il provider, il runtime di Windows PowerShell chiama il [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodo all'avvio di Windows PowerShell. Nella maggior parte, il provider può usare l'implementazione predefinita di questo metodo, che restituisce semplicemente il [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) che descrive il provider. Tuttavia, nel caso in cui si desidera aggiungere le informazioni di inizializzazione aggiuntive, è necessario implementare il proprio [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodo che restituisce una versione modificata del [ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) oggetto passato al provider. In generale, questo metodo deve restituire l'oggetto fornito [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) oggetto passato a essa o un oggetto modificato [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) oggetto contiene altre informazioni sull'inizializzazione.

Questo provider di base non esegue l'override di questo metodo. Tuttavia, il codice seguente illustra l'implementazione predefinita di questo metodo:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Il provider può mantenere lo stato di informazioni specifiche del provider come descritto in [stato dei dati specifici del Provider definizione](#Defining-Provider-Specific-State-Information). In questo caso, deve eseguire l'override dell'implementazione di [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodo per restituire un'istanza della classe derivata.

## <a name="start-dynamic-parameters"></a>Parametri dinamici di inizio

Implementazione del provider del [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodo potrebbe richiedere parametri aggiuntivi. In questo caso, il provider deve eseguire l'override di [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) metodo e restituire un oggetto che dispone di proprietà e campi con l'analisi degli attributi simile a un classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto.

Questo provider di base non esegue l'override di questo metodo. Tuttavia, il codice seguente illustra l'implementazione predefinita di questo metodo:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Annullamento dell'inizializzazione del Provider

Per liberare risorse utilizzato dal provider di Windows PowerShell, il provider deve implementare la propria [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) (metodo). Questo metodo viene chiamato dal runtime di Windows PowerShell da non inizializzare il provider alla chiusura di una sessione.

Questo provider di base non esegue l'override di questo metodo. Tuttavia, il codice seguente illustra l'implementazione predefinita di questo metodo:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Esempio di codice

Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Test di un Provider Windows PowerShell

Una volta registrato il provider di Windows PowerShell con Windows PowerShell, è possibile eseguirne il test eseguendo il cmdlet supportati nella riga di comando. Per questo provider di base, eseguire la nuova shell e usare il `Get-PSProvider` cmdlet per recuperare l'elenco dei provider e verificare che il provider AccessDb sia presente.

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

[Progettazione del Provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)