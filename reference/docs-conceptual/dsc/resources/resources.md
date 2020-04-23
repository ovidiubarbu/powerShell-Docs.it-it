---
ms.date: 02/28/2020
keywords: dsc,powershell,configurazione,installazione
title: Risorse DSC
ms.openlocfilehash: 863898d910cc3c75c3e5977a5b6b0657ba7ed512
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278248"
---
# <a name="dsc-resources"></a>Risorse DSC

> Si applica a Windows PowerShell 4.0 e versioni successive.

## <a name="overview"></a>Panoramica

Le risorse DSC (Desired State Configuration) forniscono i blocchi predefiniti per una configurazione DSC. Una risorsa espone le proprietà che possono essere configurate (schema) e contiene le funzioni di script di PowerShell chiamate da Gestione configurazione locale per assicurare il risultato desiderato.

Una risorsa può modellare un elemento generico come un file o uno specifico come un'impostazione del server IIS. I gruppi di tali risorse sono combinati in un modulo DSC, che organizza tutti i file necessari in una struttura portatile che include i metadati che permettono di identificare il modo in cui si intende usare le risorse.

Ogni risorsa dispone di uno *schema che determina la sintassi necessaria per usare la risorsa in una [configurazione](../configurations/configurations.md).
Lo schema di una risorsa può essere definito nei modi seguenti:

- File **'Schema.Mof'** : la maggior parte delle risorse definisce lo _schema_ in un file 'schema.mof' con [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-).
- File **'\<Nome risorsa\>.schema.psm1'** : le [risorse composite](../configurations/compositeConfigs.md) definiscono lo *schema* in un file '<ResourceName>.schema.psm1' file con un [blocco di parametri](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters).
- File **'\<Nome risorsa\>.psm1'** : le risorse DSC basate su classe definiscono lo _schema_ nella definizione della classe. Gli elementi della sintassi sono contrassegnati come proprietà della classe. Per altre informazioni, vedere [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc).

Per recuperare la sintassi per una risorsa DSC, usare il cmdlet [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) con il parametro `-Syntax`. Questo utilizzo è simile all'uso di [Get-Command](/powershell/module/microsoft.powershell.core/get-command) con il parametro `-Syntax` per ottenere la sintassi del cmdlet. L'output visualizzato indicherà il modello usato per un blocco di risorse per la risorsa specificata.

```powershell
Get-DscResource -Syntax Service
```

L'output visualizzato dovrebbe essere simile all'output seguente, anche se la sintassi di questa risorsa potrebbe cambiare in futuro. Come nella sintassi dei cmdlet, le _chiavi_ racchiuse tra parentesi quadre sono facoltative. I tipi specificano il tipo di dati previsto da ogni chiave.

> [!NOTE]
> La chiave **Ensure** è facoltativa perché l'impostazione predefinita è "Present".

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

All'interno di una configurazione, un blocco di risorse **Service** potrebbe avere questo aspetto per assicurare (**Ensure**) che il servizio spooler sia in esecuzione.

> [!NOTE]
> Prima di usare una risorsa in una configurazione, è necessario importarla tramite [Import-DSCResource](../configurations/import-dscresource.md).

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

Le configurazioni possono contenere più istanze dello stesso tipo di risorsa. Ogni istanza deve essere denominata in modo univoco. Nell'esempio seguente viene aggiunto un secondo blocco di risorse **Service** per configurare il servizio "DHCP".

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> A partire da PowerShell 5.0, è stato aggiunto IntelliSense per DSC. Questa nuova funzionalità consente di usare <kbd>TAB</kbd> e <kbd>CTRL</kbd>+<kbd>BARRA SPAZIATRICE</kbd> per il completamento automatico dei nomi delle chiavi.

![Completamento tramite TAB delle risorse](media/resources/resource-tabcompletion.png)

## <a name="types-of-resources"></a>Tipi di risorse

Windows include risorse predefinite e Linux ha risorse specifiche del sistema operativo. Sono disponibili risorse per le [dipendenze tra nodi](../configurations/crossNodeDependencies.md), risorse di gestione dei pacchetti, nonché [risorse gestite e di proprietà della community](https://github.com/dsccommunity). È possibile usare i passaggi precedenti per determinare la sintassi di queste risorse e come usarle. Le pagine relative a queste risorse sono archiviate in **Riferimento**.

### <a name="windows-built-in-resources"></a>Risorse predefinite di Windows

- [Risorsa Archive](../reference/resources/windows/archiveResource.md)
- [Risorsa Environment](../reference/resources/windows/environmentResource.md)
- [Risorsa File](../reference/resources/windows/fileResource.md)
- [Risorsa Group](../reference/resources/windows/groupResource.md)
- [Risorsa GroupSet](../reference/resources/windows/groupSetResource.md)
- [Risorsa Log](../reference/resources/windows/logResource.md)
- [Risorsa Package](../reference/resources/windows/packageResource.md)
- [Risorsa ProcessSet](../reference/resources/windows/ProcessSetResource.md)
- [Risorsa Registry](../reference/resources/windows/registryResource.md)
- [Risorsa Script](../reference/resources/windows/scriptResource.md)
- [Risorsa Service](../reference/resources/windows/serviceResource.md)
- [Risorsa ServiceSet](../reference/resources/windows/serviceSetResource.md)
- [Risorsa User](../reference/resources/windows/userResource.md)
- [Risorsa WindowsFeature](../reference/resources/windows/windowsFeatureResource.md)
- [Risorsa WindowsFeatureSet](../reference/resources/windows/windowsFeatureSetResource.md)
- [Risorsa WindowsOptionalFeature](../reference/resources/windows/windowsOptionalFeatureResource.md)
- [Risorsa WindowsOptionalFeatureSet](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
- [Risorsa WindowsPackageCabResource](../reference/resources/windows/windowsPackageCabResource.md)
- [Risorsa WindowsProcess](../reference/resources/windows/windowsProcessResource.md)

### <a name="cross-node-dependency-resources"></a>Risorse per le dipendenze tra nodi

- [Risorsa WaitForAll](../reference/resources/windows/waitForAllResource.md)
- [Risorsa WaitForSome](../reference/resources/windows/waitForSomeResource.md)
- [Risorsa WaitForAny](../reference/resources/windows/waitForAnyResource.md)

### <a name="package-management-resources"></a>Risorse di gestione pacchetti

- [Risorsa PackageManagement](../reference/resources/packagemanagement/PackageManagementDscResource.md)
- [Risorsa PackageManagementSource](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

#### <a name="linux-resources"></a>Risorse di Linux

- [Risorsa Archive Linux](../reference/resources/linux/lnxArchiveResource.md)
- [Risorsa Environment Linux](../reference/resources/linux/lnxEnvironmentResource.md)
- [Risorsa FileLine Linux](../reference/resources/linux/lnxFileLineResource.md)
- [Risorsa File Linux](../reference/resources/linux/lnxFileResource.md)
- [Risorsa Group Linux](../reference/resources/linux/lnxGroupResource.md)
- [Risorsa Package Linux](../reference/resources/linux/lnxPackageResource.md)
- [Risorsa Script Linux](../reference/resources/linux/lnxScriptResource.md)
- [Risorsa Service Linux](../reference/resources/linux/lnxServiceResource.md)
- [Risorsa SshAuthorizedKeys Linux](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
- [Risorsa User Linux](../reference/resources/linux/lnxUserResource.md)
