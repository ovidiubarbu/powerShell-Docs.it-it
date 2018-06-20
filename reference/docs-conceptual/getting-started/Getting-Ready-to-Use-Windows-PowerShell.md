---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Preparativi per l'uso di Windows PowerShell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 5e095984286ff89958dc0a4e3d27e40eae5b2c5e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950968"
---
# <a name="getting-ready-to-use-windows-powershell"></a>Preparativi per l'uso di Windows PowerShell
Dopo l'installazione e l'avvio di Windows PowerShell, prendere in considerazione le opzioni di installazione seguenti. È possibile eseguire queste attività in qualsiasi momento.

- **Installare i file della Guida.** I cmdlet inclusi in Windows PowerShell 3.0 non vengono forniti con i file della Guida. Tuttavia, è possibile usare il cmdlet [Update-Help](/powershell/module/microsoft.powershell.core/update-help) per scaricare e installare i file della Guida più recenti nel computer in uso. Quando i file vengono installati, è possibile usare il cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/get-help) per visualizzarli direttamente nella riga di comando. Per altre informazioni, vedere [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_updatable_help).

    Se si decide di non installare i file della Guida, è comunque possibile leggere gli argomenti della Guida online. Per trovare la versione online degli argomenti della Guida per qualsiasi cmdlet, digitare: `Get-Help <CmdletName> -Online`. Per esplorare gli argomenti della guida di Windows PowerShell, vedere la [documentazione di PowerShell](/powershell/scripting).

- **Eseguire gli script.** Per mantenere protetto Windows PowerShell, i criteri di esecuzione predefiniti in Windows PowerShell sono di tipo **Restricted**. Questi criteri consentono di eseguire i cmdlet, ma non gli script. Per eseguire gli script, usare il cmdlet [Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy) per modificare i criteri di esecuzione in **AllSigned** o **RemoteSigned**. Solo i membri del gruppo Administrators nel computer possono eseguire questo cmdlet. Per altre informazioni, vedere [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

- **Abilitare la comunicazione remota.** Il sistema è già configurato per l'esecuzione di comandi remoti in altri computer. In Windows Server 2012 R2 e Windows Server 2012 il sistema è configurato anche per ricevere comandi remoti, ovvero per consentire ad altri computer di eseguire comandi remoti nel computer locale. Per consentire ai computer che eseguono altre versioni di Windows di ricevere comandi remoti, eseguire il cmdlet [Enable-PSRemoting](/powershell/module/microsoft.powershell.core/enable-psremoting) nel computer che si vuole gestire in remoto. Solo i membri del gruppo Administrators nel computer possono eseguire questo cmdlet. Per altre informazioni, vedere [about_Remote](/powershell/module/microsoft.powershell.core/about/about_remote).

    NOTA: se la comunicazione remota è abilitata in un computer che esegue Windows PowerShell 2.0, resta abilitata dopo l'installazione di Windows Management Framework 3.0. Tuttavia, in Windows Server 2008, ma non in Windows Server 2008 R2, è necessario riabilitare la comunicazione remota dopo l'installazione di Windows Management Framework 3.0.

## <a name="see-also"></a>Vedere anche
- [Installazione di Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [Avvio di Windows PowerShell](/powershell/scripting/setup/starting-windows-powershell)