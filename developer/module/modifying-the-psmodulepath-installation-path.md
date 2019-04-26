---
title: Modifica il percorso di installazione di PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082210"
---
# <a name="modifying-the-psmodulepath-installation-path"></a>Modifica del percorso di installazione di PSModulePath

Il `PSModulePath` variabile di ambiente vengono archiviati i percorsi per i percorsi dei moduli installati nel disco. Windows PowerShell Usa questa variabile per individuare i moduli quando l'utente non specifica il percorso completo di un modulo. La ricerca vengono eseguiti nell'ordine in cui vengono visualizzati i percorsi nella variabile.

Quando si avvia Windows PowerShell, `PSModulePath` viene creata come una variabile di ambiente di sistema con il seguente valore predefinito: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.

## <a name="to-view-the-psmodulepath-variable"></a>Per visualizzare la variabile PSModulePath

Per visualizzare i percorsi specificati nel `PSModulePath` variabile, digitare il comando seguente:

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a>Aggiungere percorsi alla variabile PSModulePath

Per aggiungere i percorsi a questa variabile, usare uno dei metodi seguenti:

- Per aggiungere un valore temporaneo che è disponibile solo per la sessione corrente, eseguire il comando seguente dalla riga di comando:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- Per aggiungere un valore persistente che è disponibile ogni volta che viene aperta una sessione, aggiungere il comando seguente a un profilo di Windows PowerShell:

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  Per altre informazioni sui profili, vedere [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) nella libreria Microsoft TechNet.

- Per aggiungere una variabile persistente nel Registro di sistema, creare una nuova variabile di ambiente utente denominata `PSModulePath` usando l'Editor delle variabili di ambiente nel **le proprietà di sistema** nella finestra di dialogo.

- Per aggiungere una variabile persistente usando uno script, usare il **SetEnvironmentVariable** metodo sulla classe di ambiente. Ad esempio, lo script seguente aggiunge il "c:\Programmi\Microsoft Files\Fabrikam\Module percorso al valore della variabile di ambiente PSModulePath per il computer. Per aggiungere il percorso alla variabile di ambiente PSModulePath utente, impostare la destinazione su "Utente".

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a>Per rimuovere i percorsi da PSModulePath

È possibile rimuovere i percorsi dalla variabile tramite metodi simili: ad esempio, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` rimuoverà il **c:\ModulePath** percorso dalla sessione corrente.

## <a name="see-also"></a>Vedere anche

[Scrittura di un modulo di Windows PowerShell](./writing-a-windows-powershell-module.md)
