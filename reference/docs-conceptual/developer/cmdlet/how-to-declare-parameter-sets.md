---
title: Come dichiarare i set di parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365610"
---
# <a name="how-to-declare-parameter-sets"></a>Come dichiarare i set di parametri

Questo esempio illustra come definire due set di parametri quando si dichiarano i parametri per un cmdlet. Ogni set di parametri dispone sia di un parametro univoco che di un parametro condiviso utilizzato da entrambi i set di parametri. Per ulteriori informazioni sui set di parametri, inclusa la modalità di specifica del set di parametri predefinito, vedere set di parametri del [cmdlet](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Quando possibile, definire il parametro univoco di un set di parametri come parametro obbligatorio. Tuttavia, se si desidera che il cmdlet venga eseguito senza specificare parametri, il parametro Unique può essere un parametro facoltativo. Il parametro Unique del cmdlet `Get-Command`, ad esempio, è facoltativo.

## <a name="how-to-define-two-parameter-sets"></a>Come definire due set di parametri

1. Aggiungere la parola chiave `ParameterSet` all'attributo Parameter per il parametro Unique del primo set di parametri.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Aggiungere la parola chiave `ParameterSet` all'attributo Parameter per il parametro Unique del secondo set di parametri.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Per il parametro che appartiene a entrambi i set di parametri, aggiungere un attributo di parametro per ogni set di parametri e quindi aggiungere la parola chiave `ParameterSet` a ogni set. In ogni attributo di parametro è possibile specificare la modalità di definizione del parametro. Un parametro può essere facoltativo in un set e obbligatorio in un altro.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Vedere anche

[Set di parametri del cmdlet](./cmdlet-parameter-sets.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
