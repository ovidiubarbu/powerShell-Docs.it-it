---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Uso di Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080102"
---
# <a name="using-import-dscresource"></a>Uso di Import-DSCResource

`Import-DScResource` è una parola chiave dinamica che può essere usata solo all'interno di un blocco di script di configurazione. La parola chiave `Import-DSCResource` consente di importare le risorse necessarie nella configurazione. Le risorse in `$pshome` vengono importate automaticamente, ma è comunque consigliabile importare in modo esplicito tutte le risorse usate nella [configurazione](Configurations.md).

La sintassi per `Import-DSCResource` è illustrata di seguito.  Quando si specificano moduli in base al nome, è necessario elencarne ognuno in una nuova riga.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parametro  |Description  |
|---------|---------|
|`-Name`|Nome della risorsa DSC che è necessario importare. Se viene specificato il nome del modulo, il comando cerca queste risorse DSC all'interno del modulo; in caso contrario, il comando cerca le risorse DSC in tutti i percorsi delle risorse DSC. I caratteri jolly sono supportati.|
|`-ModuleName`|Nome del modulo o specifica del modulo.  Se si specificano risorse per l'importazione da un modulo, il comando tenterà di importare solo queste risorse. Se si specifica solo il modulo, il comando importa tutte le risorse DSC nel modulo.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Esempio: Usare Import-DSCResource all'interno di una configurazione

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry
    
    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> Non è consentito specificare più valori per i nomi delle risorse e i nomi dei moduli nello stesso comando. Può verificarsi un comportamento non deterministico sulla risorsa da caricare dal modulo cui nel caso in cui stessa risorsa sia presente in più moduli. Il comando seguente genererà un errore durante la compilazione.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Aspetti da considerare quando si usa solo il parametro Name:

- È un'operazione a elevato utilizzo di risorse in base al numero di moduli installati nel computer.
- Verrà caricata la prima risorsa trovata con il nome specificato. Nel caso in cui sia installata più di una risorsa con lo stesso nome, potrebbe essere caricata la risorsa non corretta.

L'utilizzo consigliato consiste nello specificare `–ModuleName` con il parametro `-Name`, come descritto di seguito.

Questo utilizzo offre i vantaggi seguenti:

- Riduce l'impatto sulle prestazioni, limitando l'ambito di ricerca per la risorsa specificata.
- Definisce in modo esplicito il modulo di definizione della risorsa, garantendo il caricamento della risorsa corretta.

> [!NOTE]
> In PowerShell 5.0, le risorse DSC possono avere più versioni e possono essere installate in un computer side-by-side. Questo significa che più versioni di un modulo risorse sono disponibili nella stessa cartella di moduli.
> Per altre informazioni, vedere [Uso di risorse con più versioni](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense con Import-DSCResource

Quando si crea la configurazione DSC in ISE, PowerShell fornisce IntelliSense per le risorse e le proprietà delle risorse. Le definizioni delle risorse nel percorso del modulo `$pshome` vengono caricate automaticamente. Quando si importano risorse con la parola chiave `Import-DSCResource`, le definizioni di risorse specificate vengono aggiunte e IntelliSense viene espanso per includere lo schema della risorsa importata.

![Risorsa IntelliSense](/media/resource-intellisense.png)

> [!NOTE]
> A partire da PowerShell 5.0 è stato aggiunto il completamento tramite TAB a ISE per le risorse DSC e le relative proprietà. Per altre informazioni, vedere [Risorse](../resources/resources.md).

In fase di compilazione della configurazione, PowerShell usa le definizioni delle risorse importate per convalidare tutti i blocchi di risorse nella configurazione.
Ogni blocco di risorse viene convalidato tramite definizione dello schema della risorsa per le regole seguenti.

- Vengono usate solo le proprietà definite nello schema.
- I tipi di dati per ogni proprietà sono corretti.
- Sono specificate le proprietà delle chiavi.
- Non viene usata alcuna proprietà di sola lettura.
- La convalida sul valore esegue il mapping di tipi.

Considerare la configurazione seguente:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

La compilazione di questa configurazione genera un errore.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense e la convalida dello schema consentono di rilevare più errori durante le fasi di analisi e compilazione, evitando complicazioni in fase di esecuzione.

> [!NOTE]
> Ogni risorsa DSC può avere un nome e un **FriendlyName** definito dallo schema della risorsa. Di seguito sono riportate le prime due righe di "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Quando si usa questa risorsa in una configurazione, è possibile specificare **MSFT_ServiceResource** o **Service**.

## <a name="powershell-v4-and-v5-differences"></a>Differenze tra PowerShell v4 e v5

Sussistono varie differenze nell'ambito della creazione di configurazioni in PowerShell 4.0 e PowerShell 5.0 e versioni successive. Questa sezione evidenzia le differenze pertinenti a questo articolo.

### <a name="multiple-resource-versions"></a>Più versioni di risorse

L'installazione e l'utilizzo di più versioni di risorse affiancate non sono supportati in PowerShell 4.0. Se si verificano problemi di importazione delle risorse nella configurazione, assicurarsi di avere solo una versione della risorsa installata.

Nell'immagine seguente sono installare due versioni del modulo **xPSDesiredStateConfiguration**.

![Più versioni di risorse corrette](/media/multiple-resource-versions-broken.md)

Copiare il contenuto della versione del modulo desiderata nel livello superiore della directory del modulo.

![Più versioni di risorse corrette](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Posizione risorsa

Durante la creazione e la compilazione di configurazioni, le risorse possono essere archiviate in qualsiasi directory specificata mediante [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). In PowerShell 4.0, Gestione configurazione locale richiede che tutti i moduli delle risorse DSC siano archiviati in "Programmi\WindowsPowerShell\Modules" o `$pshome\Modules`. A partire da PowerShell 5.0, questo requisito è stato rimosso e i moduli delle risorse possono essere archiviati in qualsiasi directory specificata mediante `PSModulePath`.

## <a name="see-also"></a>Vedere anche

- [Risorse](../resources/resources.md)
