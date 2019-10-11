---
ms.date: 07/09/2019
keywords: dsc,gpo,powershell,configurazione
title: Avvio rapido - Convertire i criteri di gruppo in DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953468"
---
> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="quickstart-convert-group-policy-into-dsc"></a>Avvio rapido: Convertire i criteri di gruppo in DSC

È possibile generare una configurazione DSC da una baseline dei criteri di gruppo o del Centro sicurezza di Azure. Il modulo [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) include i comandi seguenti per l'esecuzione di questa attività.

- `ConvertFrom-GPO` - Converte i criteri di gruppo archiviati come file. È anche possibile specificare una directory che contiene più i criteri che verranno combinati in un'unica configurazione.
  - Per esportare i criteri di gruppo nell'ambiente in uso, usare il cmdlet [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) o seguire le istruzioni in [Esportare un oggetto Criteri di gruppo in un file](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).
- `ConvertFrom-SCM` - Converte le baseline di Security Compliance Manager archiviate come file `.xml`.
- `ConvertFrom-ASC` - Converte le baseline del Centro sicurezza di Azure archiviate come file `.json`.
- `Merge-GPOs` - Converte i criteri di gruppo applicati a un computer di destinazione.

I cmdlet elencati sopra convertono una baseline in un file `.mof` DSC. È anche possibile scegliere di creare uno script di configurazione (`.ps1`) che è possibile modificare e ricompilare. I cmdlet rilevano gli errori di compilazione per le risorse mancanti o i blocchi di risorse duplicati. I blocchi di risorse che causano errori di compilazione vengono impostati come commenti.

L'esempio seguente converte una [baseline di Microsoft Security](https://www.microsoft.com/en-us/download/details.aspx?id=55319) in uno script di configurazione DSC (`.ps1`) e in un file `.mof`.

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

Dopo aver eseguito i comandi, vengono visualizzati due file nella directory predefinita "Output" creata nel percorso corrente.

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

Ogni nodo gestito richiede anche i due moduli seguenti:

- [SecurityPolicyDSC](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [AuditPolicyDSC](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> **BaselineManagement** è una soluzione sviluppata dalla community per rendere più facilmente individuabile DSC per il supporto delle soluzioni della community che provengono dai gestori di progetti e non da Microsoft. È possibile aprire un nuovo argomento per **BaselineManagement** in [GitHub](https://github.com/microsoft/BaselineManagement).

## <a name="next-steps"></a>Passaggi successivi

- Per caricare lo script di configurazione nel servizio State Configuration di Automazione di Azure, vedere [Introduzione](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).
- Aggiungere i moduli **SecurityPolicyDSC** e **AuditPolicyDSC** all'[Account di Automazione](/azure/automation/shared-resources/modules).
- Le configurazioni e le risorse DSC sono disponibili in [PowerShell Gallery](https://www.powershellgallery.com/).
