---
title: Come dichiarare set di parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067893"
---
# <a name="how-to-declare-parameter-sets"></a>Come dichiarare i set di parametri

In questo esempio viene illustrato come definire due set di parametri quando si dichiarano i parametri per un cmdlet. Ogni set di parametri include un parametro univoco e un parametro condiviso usato da entrambi i set di parametri. Per altre informazioni sui set di parametri, incluse le procedure specificare il set di parametri predefiniti, vedere [imposta parametro di Cmdlet](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Quando possibile, definire il parametro unique di un set di parametri di un parametro obbligatorio. Tuttavia, se si desidera che i cmdlet per l'esecuzione senza specificare alcun parametro, il parametro unique può essere un parametro facoltativo. Ad esempio, il parametro unique del `Get-Command` cmdlet è facoltativo.

## <a name="how-to-define-two-parameter-sets"></a>Come definire due set di parametri

1. Aggiungere il `ParameterSet` una parola chiave per l'attributo di parametro per il parametro unique del primo set di parametri.

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

2. Aggiungere il `ParameterSet` una parola chiave per l'attributo di parametro per il parametro unique del secondo set di parametri.

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

3. Per il parametro appartenente a entrambi i set di parametri, aggiungere un attributo di parametro per ogni set di parametri e quindi aggiungere il `ParameterSet` (parola chiave) a ogni set. In ogni attributo di parametro, è possibile specificare come tale parametro è definito. Un parametro può essere facoltativo in un unico set e obbligatorio in un altro.

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

[Imposta parametro di cmdlet](./cmdlet-parameter-sets.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
