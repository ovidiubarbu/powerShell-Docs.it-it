---
title: Problemi noti in WMF 5.1
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: b341f57592feb183eb0e7228cdc08460e370369f
ms.sourcegitcommit: f06ef671c0a646bdd277634da89cc11bc2a78a41
translationtype: HT
---
# <a name="known-issues-in-wmf-51"></a>Problemi noti in WMF 5.1 #

> Nota: queste informazioni sono soggette a modifiche.

## <a name="starting-powershell-shortcut-as-administrator"></a>Avvio del collegamento di PowerShell come amministratore
Dopo l'installazione di WMF, se si tenta di avviare PowerShell come amministratore dal collegamento, è possibile che venga visualizzato il messaggio "Errore non specificato".
Riaprire il collegamento senza usare l'accesso come amministratore e il collegamento ora funziona anche come amministratore.

## <a name="pester"></a>Pester
In questa versione vi sono due problemi che è necessario tenere presenti quando si usa Pester o Nano Server:

* L'esecuzione di test su Pester può generare errori a causa delle differenze tra FULL CLR e CORE CLR. In particolare, il metodo di convalida non è disponibile nel tipo XmlDocument. Sei test che tentano di convalidare lo schema dei log di output NUnit hanno esito negativo. 
* Attualmente un test code coverage non riesce perché la risorsa DSC *WindowsFeature* non esiste in Nano Server. Tuttavia, questi errori sono in genere innocui e possono essere ignorati.

## <a name="operation-validation"></a>Convalida dell'operazione 

* Update-Help ha esito negativo per il modulo Microsoft.PowerShell.Operation.Validation a causa di un URI della guida non funzionante

## <a name="dsc-after-uninstall-wmf"></a>DSC dopo la disinstallazione di WMF 
* La disinstallazione di WMF non comporta l'eliminazione dei documenti MOF di DSC dalla cartella di configurazione. DSC non funzionerà correttamente se i documenti MOF contengono proprietà più recenti che non sono disponibili nei sistemi precedenti. In questo caso, eseguire lo script seguente dalla console di PowerShell con privilegi elevati per pulire gli stati di DSC.
 ```PowerShell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```  
