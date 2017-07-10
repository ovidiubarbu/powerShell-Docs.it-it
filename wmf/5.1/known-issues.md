---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: Problemi noti in WMF 5.1
ms.openlocfilehash: 93113962781f1cc84a80f8f97f56ffd7622fec6b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="known-issues-in-wmf-51" class="xliff"></a>
# Problemi noti in WMF 5.1 #

> Nota: queste informazioni sono soggette a modifiche.

<a id="starting-powershell-shortcut-as-administrator" class="xliff"></a>
## Avvio del collegamento di PowerShell come amministratore
Dopo l'installazione di WMF, se si tenta di avviare PowerShell come amministratore dal collegamento, è possibile che venga visualizzato il messaggio "Errore non specificato".
Riaprire il collegamento senza usare l'accesso come amministratore e il collegamento ora funziona anche come amministratore.

<a id="pester" class="xliff"></a>
## Pester
In questa versione vi sono due problemi che è necessario tenere presenti quando si usa Pester o Nano Server:

* L'esecuzione di test su Pester può generare errori a causa delle differenze tra FULL CLR e CORE CLR. In particolare, il metodo di convalida non è disponibile nel tipo XmlDocument. Sei test che tentano di convalidare lo schema dei log di output NUnit hanno esito negativo. 
* Attualmente un test code coverage non riesce perché la risorsa DSC *WindowsFeature* non esiste in Nano Server. Tuttavia, questi errori sono in genere innocui e possono essere ignorati.

<a id="operation-validation" class="xliff"></a>
## Convalida dell'operazione 

* Update-Help ha esito negativo per il modulo Microsoft.PowerShell.Operation.Validation a causa di un URI della guida non funzionante

<a id="dsc-after-uninstall-wmf" class="xliff"></a>
## DSC dopo la disinstallazione di WMF 
* La disinstallazione di WMF non comporta l'eliminazione dei documenti MOF di DSC dalla cartella di configurazione. DSC non funzionerà correttamente se i documenti MOF contengono proprietà più recenti che non sono disponibili nei sistemi precedenti. In questo caso, eseguire lo script seguente dalla console di PowerShell con privilegi elevati per pulire gli stati di DSC.
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  

<a id="jea-virtual-accounts" class="xliff"></a>
## Account virtuali JEA
Le configurazioni di endpoint e sessioni JEA impostate per l'uso di account virtuali in WMF 5.0 non saranno configurate per l'uso di un account virtuale dopo l'aggiornamento a WMF 5.1.
Questo significa che i comandi eseguiti in sessioni JEA verranno eseguiti nel contesto dell'identità dell'utente connesso anziché di un account amministratore temporaneo, impedendo potenzialmente all'utente di eseguire comandi che richiedono privilegi elevati.
Per ripristinare gli account virtuali, è necessario annullare la registrazione e registrare nuovamente le configurazioni di sessioni che usano account virtuali.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```

