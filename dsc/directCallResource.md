---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Chiamata diretta dei metodi delle risorse DSC
ms.openlocfilehash: ab00e66d526eda244500a41e450c56b0151274ee
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="calling-dsc-resource-methods-directly"></a>Chiamata diretta dei metodi delle risorse DSC

>Si applica a: Windows PowerShell 5.0

È possibile usare il cmdlet [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) per chiamare direttamente le funzioni o i metodi di una risorsa DSC (le funzioni **Get-TargetResource**, **Set-TargetResource**, e **Test-TargetResource** di una risorsa basata su MOF, o i metodi **Get**, **Set**, e **Test** di una risorsa basata su classi). Il cmdlet può essere usato da terze parti che desiderano usare risorse DSC o come strumento utile d'aiuto durante lo sviluppo delle risorse. 

Questo cmdlet viene in genere usato in combinazione con una proprietà di metaconfigurazione `refreshMode = 'Disabled'`, ma può essere usato indipendentemente dall'impostazione di **refreshMode**.

Quando si chiama il cmdlet **Invoke-DscResource**, specificare il metodo o la funzione da chiamare usando il parametro **Method**. Specificare le proprietà della risorsa passando una tabella hash come valore del parametro **Property**.

Di seguito vengono riportati alcuni esempi di chiamate dirette ai metodi della risorsa:

## <a name="ensure-a-file-is-present"></a>Verificare che sia presente un file

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a>Eseguire un test per verificare la presenza di un file

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a>Ottenere il contenuto del file

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>**Nota:** la chiamata diretta di metodi di risorse composite non è supportata. Chiamare invece i metodi delle risorse sottostanti che costituiscono la risorsa composita.

## <a name="see-also"></a>Vedere anche
- [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md) 
- [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md)
- [Debug di risorse DSC](debugResource.md)

