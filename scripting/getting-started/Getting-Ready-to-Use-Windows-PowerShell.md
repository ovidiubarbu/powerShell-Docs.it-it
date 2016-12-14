---
title: Preparativi per l&quot;uso di Windows PowerShell
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 6dc7052d-cc5a-4220-950f-98f963a2b587
ms.openlocfilehash: 2564ab148fb1de1cb58ee775d2000d321a1d36c1
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="getting-ready-to-use-windows-powershell"></a>Preparativi per l'uso di Windows PowerShell
Dopo l'installazione e l'avvio di Windows PowerShell, prendere in considerazione le opzioni di installazione seguenti. È possibile eseguire queste attività in qualsiasi momento.

-   **Installare i file della Guida.** I cmdlet inclusi in Windows PowerShell 3.0 non vengono forniti con i file della Guida. Tuttavia, è possibile usare il cmdlet [Update-Help](https://technet.microsoft.com/en-us/library/93e1d870-ace6-432b-8778-8920291d7545) per scaricare e installare i file della Guida più recenti nel computer in uso. Quando i file vengono installati, è possibile usare il cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/1f46eeb4-49d7-4bec-bb29-395d9b42f54a) per visualizzarli direttamente nella riga di comando. Per altre informazioni, vedere [about_Updatable_Help](https://technet.microsoft.com/en-us/library/10bba75c-f4ac-4ca1-bbf3-8f34dd521ffe).

    Se si decide di non installare i file della Guida, è comunque possibile leggere gli argomenti della Guida online. Per trovare la versione online degli argomenti della Guida per qualsiasi cmdlet, digitare: `Get-Help <CmdletName> -Online`. Per esplorare gli argomenti della Guida di Windows PowerShell nella Libreria TechNet, accedere all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=107116](http://go.microsoft.com/fwlink/?LinkID=107116).

-   **Eseguire gli script.** Per mantenere protetto Windows PowerShell, i criteri di esecuzione predefiniti in Windows PowerShell sono di tipo **Restricted**. Questi criteri consentono di eseguire i cmdlet, ma non gli script. Per eseguire gli script, usare il cmdlet [Set-ExecutionPolicy[PSITPro5_Security]](https://technet.microsoft.com/en-us/library/5690a0e1-495b-4e63-8280-65ead7bf01ab) per modificare i criteri di esecuzione in **AllSigned** o **RemoteSigned**. Solo i membri del gruppo Administrators nel computer possono eseguire questo cmdlet. Per altre informazioni, vedere [about_Execution_Policies [v4]](https://technet.microsoft.com/en-us/library/347708dc-1515-4d74-978b-8334603472e6).

-   **Abilitare la comunicazione remota.** Il sistema è già configurato per l'esecuzione di comandi remoti in altri computer. In Windows Server 2012 R2 e Windows Server 2012 il sistema è configurato anche per ricevere comandi remoti, ovvero per consentire ad altri computer di eseguire comandi remoti nel computer locale. Per consentire ai computer che eseguono altre versioni di Windows di ricevere comandi remoti, eseguire il cmdlet [Enable-PSRemoting](https://technet.microsoft.com/en-us/library/19437c28-33b8-4ac1-9113-8439cc8beffb) nel computer che si vuole gestire in remoto. Solo i membri del gruppo Administrators nel computer possono eseguire questo cmdlet. Per altre informazioni, vedere [about_Remote](https://technet.microsoft.com/en-us/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970).

    NOTA: se la comunicazione remota è abilitata in un computer che esegue Windows PowerShell 2.0, resta abilitata dopo l'installazione di Windows Management Framework 3.0. Tuttavia, in Windows Server 2008, ma non in Windows Server 2008 R2, è necessario riabilitare la comunicazione remota dopo l'installazione di Windows Management Framework 3.0.

## <a name="see-also"></a>Vedere anche
- [Installazione di Windows PowerShell](../setup/Installing-Windows-PowerShell.md)
- [Avvio di Windows PowerShell [ps]](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

