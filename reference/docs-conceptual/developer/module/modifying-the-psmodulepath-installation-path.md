---
title: Modifica del percorso di installazione di PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953841"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modifica del percorso di installazione di PSModulePath

La variabile di ambiente `PSModulePath` archivia i percorsi delle posizioni dei moduli installati su disco. PowerShell usa questa variabile per individuare i moduli quando l'utente non specifica il percorso completo di un modulo. I percorsi in questa variabile vengono cercati nell'ordine in cui sono visualizzati.

All'avvio di PowerShell, `PSModulePath` viene creato come variabile di ambiente di sistema con il valore predefinito seguente: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` o `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` per Windows PowerShell.

## <a name="to-view-the-psmodulepath-variable"></a>Per visualizzare la variabile PSModulePath

Per visualizzare i percorsi specificati nella variabile `PSModulePath`, digitare il comando seguente:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Per aggiungere percorsi alla variabile PSModulePath

Per aggiungere percorsi a questa variabile, usare uno dei metodi seguenti:

- Per aggiungere un valore temporaneo disponibile solo per la sessione corrente, eseguire il comando seguente dalla riga di comando:

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- Per aggiungere un valore permanente disponibile ogni volta che viene aperta una sessione, aggiungere il comando precedente a un file di profilo di PowerShell (`$PROFILE`) >

  Per altre informazioni sui profili, vedere [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).

- Per aggiungere una variabile persistente al registro di sistema, creare una nuova variabile di ambiente utente denominata `PSModulePath` usando l'editor delle variabili di ambiente nella finestra di dialogo **proprietà del sistema** .

- Per aggiungere una variabile persistente usando uno script, usare il metodo .NET [nell'SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) sulla classe [System. Environment](https://docs.microsoft.com/dotnet/api/system.environment) . Ad esempio, lo script seguente aggiunge il percorso `C:\Program Files\Fabrikam\Module` al valore della variabile di ambiente `PSModulePath` per il computer. Per aggiungere il percorso alla variabile di ambiente `PSModulePath` utente, impostare la destinazione su "User".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Per rimuovere i percorsi dal PSModulePath

È possibile rimuovere i percorsi dalla variabile utilizzando metodi simili. ad esempio, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` eliminerà il percorso **c:\ModulePath** dalla sessione corrente.

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
