---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Uso di Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803413"
---
# <a name="using-import-dscresource"></a>Uso di Import-DSCResource

`Import-DScResource` è una parola chiave dinamica, ma può essere utilizzata solo all'interno di un blocco di script di configurazione. Il `Import-DSCResource` (parola chiave) per importare tutte le risorse necessarie nella configurazione. Le risorse sotto `$pshome` vengono importati automaticamente, ma si è ancora considerato consiste nell'importare in modo esplicito tutte le risorse usate nel [Configuration](Configurations.md).

La sintassi per `Import-DSCResource` è illustrato di seguito.  Quando si specificano i moduli in base al nome, è un requisito per elencare ognuno in una nuova riga.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parametro  |Description  |
|---------|---------|
|`-Name`|Il nome della risorsa DSC che è necessario importare. Se viene specificato il nome del modulo, il comando Cerca per tali risorse DSC all'interno del modulo; in caso contrario, il comando Cerca le risorse DSC in tutti i percorsi delle risorse DSC. I caratteri jolly sono supportati.|
|`-ModuleName`|Il nome del modulo o specifica del modulo.  Se si specificano le risorse per l'importazione da un modulo, il comando tenterà di importare solo le risorse. Se si specifica solo il modulo, il comando Importa tutte le risorse DSC nel modulo.|

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
> Specifica di più valori per i nomi delle risorse e i nomi dei moduli nel comando stesso non sono supportati. Ciò può avere un comportamento non deterministico sulla quale risorsa scegliere da caricare dal modulo cui nel caso in cui stessa risorsa esiste in più moduli. Comando seguente verrà generato errore durante la compilazione.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Aspetti da considerare quando si usa solo il parametro Name:

- È un'operazione a elevato utilizzo di risorse in base al numero dei moduli installati nel computer.
- Caricherà la prima risorsa trovata con il nome specificato. Nel caso in cui è presente più di una risorsa con lo stesso nome installato, è stato possibile caricare la risorsa non corretta.

L'utilizzo consigliato consiste nello specificare `–ModuleName` con il `-Name` parametro, come descritto di seguito.

Questo utilizzo offre i vantaggi seguenti:

- Riduce l'impatto sulle prestazioni, limitando l'ambito di ricerca per la risorsa specificata.
- Definisce in modo esplicito il modulo di definizione della risorsa, garantendo che la risorsa corretta viene caricata.

> [!NOTE]
> In PowerShell 5.0, le risorse DSC possono avere più versioni e possono essere installate in un computer side-by-side. Questo significa che più versioni di un modulo risorse sono disponibili nella stessa cartella di moduli.
> Per altre informazioni, vedere [Uso di risorse con più versioni](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense con Import-DSCResource

Quando si crea la configurazione DSC in ISE, PowerShell fornisce IntelliSence per le risorse e le proprietà delle risorse. Le definizioni delle risorse sotto il `$pshome` percorso del modulo vengono caricate automaticamente. Quando si importano le risorse usando il `Import-DSCResource` (parola chiave), le definizioni di risorse specificato vengono aggiunti e Intellisense viene espanso per includere lo schema della risorsa importata.

![Risorsa Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> A partire da PowerShell 5.0, completamento tramite tasto tab è stata aggiunta alla finestra di ISE per le risorse DSC e le relative proprietà. Per altre informazioni, vedere [risorse](../resources/resources.md).

Quando si compila la configurazione, PowerShell Usa le definizioni di risorsa importata per convalidare tutti i blocchi di risorsa nella configurazione.
Ogni blocco di risorse viene convalidato, tramite definizione dello schema della risorsa, per le regole seguenti.

- Vengono usate solo proprietà definite nello schema.
- I tipi di dati per ogni proprietà siano corretti.
- Proprietà delle chiavi sono specificate.
- Nessuna proprietà di sola lettura viene usata.
- La convalida sul valore esegue il mapping di tipi.

Prendere in considerazione la configurazione seguente:

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

La compilazione genera questa configurazione un errore.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

IntelliSense e convalida dello schema consentono di rilevare più errori durante la fase di analisi e compilazione, come evitare complicazioni in fase di esecuzione.

> [!NOTE]
> Ogni risorsa DSC può avere un nome e una **FriendlyName** definita dallo schema della risorsa. Di seguito sono le prime due righe di "MSFT_ServiceResource.shema.mof".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> Quando si usa questa risorsa in una configurazione, è possibile specificare **MSFT_ServiceResource** oppure **servizio**.

## <a name="powershell-v4-and-v5-differences"></a>Differenze di PowerShell v4 e v5

Ci sono differenze più che viene visualizzato durante la creazione di configurazioni in Visual Studio PowerShell 4.0. PowerShell 5.0 e versioni successive. In questa sezione verrà evidenziate le differenze che venga visualizzato rilevanti per questo articolo.

### <a name="multiple-resource-versions"></a>Più versioni di risorse

Installazione e l'utilizzo di più versioni di fianco a fianco delle risorse non è stata supportata in PowerShell 4.0. Se si verificano problemi di importazione delle risorse nella configurazione, assicurarsi di avere solo una versione della risorsa installata.

Nell'immagine seguente, due versioni del **xPSDesiredStateConfiguration** modulo vengono installati.

![Più versioni di risorse predefinite](/media/multiple-resource-versions-broken.md)

Copiare il contenuto della versione di modulo desiderato nel livello superiore della directory del modulo.

![Più versioni di risorse predefinite](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Posizione risorsa

Durante la creazione e compilazione di configurazioni, le risorse possono essere archiviate in qualsiasi directory specificata mediante il [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). In PowerShell 4.0, Gestione configurazione locale richiede tutti i moduli delle risorse DSC da archiviare in "Program Files\WindowsPowerShell\Modules" o `$pshome\Modules`. A partire da PowerShell 5.0, questo requisito è stato rimosso e i moduli delle risorse possono essere archiviati in qualsiasi directory specificata da `PSModulePath`.

## <a name="see-also"></a>Vedere anche

- [Risorse](../resources/resources.md)
