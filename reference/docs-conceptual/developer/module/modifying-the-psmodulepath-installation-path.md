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
ms.openlocfilehash: b176d8439025ac132962859f79e72ae6f9703e82
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78405045"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modifica del percorso di installazione di PSModulePath

La variabile di ambiente `PSModulePath` archivia i percorsi delle posizioni dei moduli installati su disco. PowerShell usa questa variabile per individuare i moduli quando l'utente non specifica il percorso completo di un modulo. I percorsi in questa variabile vengono cercati nell'ordine in cui sono visualizzati.

All'avvio di PowerShell, `PSModulePath` viene creato come variabile di ambiente di sistema con il valore predefinito seguente: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` in Windows e `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` su Linux o Mac e `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` per Windows PowerShell.

> [!NOTE]
> Il percorso **CurrentUser** specifico dell'utente è la cartella `WindowsPowerShell\Modules` che si trova nel percorso dei **documenti** nel profilo utente. Il percorso specifico di tale percorso varia in base alla versione di Windows e a seconda che si usi o meno il reindirizzamento cartelle. Per impostazione predefinita, in Windows 10 il percorso è `$HOME\Documents\WindowsPowerShell\Modules`.

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

[about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules)
