---
title: Come dichiarare i parametri del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067916"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Come dichiarare i parametri dei cmdlet

Questi esempi mostrano come dichiarare denominati, posizionali, obbligatorio, facoltativo e parametri opzionali. Questi esempi illustrano inoltre come definire un alias del parametro.

## <a name="how-to-declare-a-named-parameter"></a>Come dichiarare un parametro denominato

- Definire una proprietà pubblica come illustrato nel codice seguente. Quando si aggiunge l'attributo Parameter, omettere il `Position` parola chiave dall'attributo.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Per altre informazioni relative all'attributo di parametro, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Come dichiarare un parametro posizionale

- Definire una proprietà pubblica come illustrato nel codice seguente. Quando si aggiunge l'attributo Parameter, impostare il `Position` una parola chiave per la posizione dell'argomento. Il valore 0 indica la prima posizione.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Per altre informazioni relative all'attributo di parametro, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Come dichiarare un parametro obbligatorio

- Definire una proprietà pubblica come illustrato nel codice seguente. Quando si aggiunge l'attributo Parameter, impostare il `Mandatory` parola chiave da `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Per altre informazioni relative all'attributo di parametro, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Come dichiarare un parametro facoltativo

- Definire una proprietà pubblica come illustrato nel codice seguente. Quando si aggiunge l'attributo Parameter, omettere il `Mandatory` (parola chiave).

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Come dichiarare un parametro opzionale

- Definire una proprietà pubblica come tipo [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)e quindi dichiarare l'attributo di parametro.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Per altre informazioni relative all'attributo di parametro, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Come dichiarare un parametro con alias

- Definire una proprietà pubblica come illustrato nel codice seguente. Aggiungere un Alias (attributo) che elenca gli alias per il parametro. In questo esempio vengono definiti tre alias per lo stesso parametro. L'alias prima fornisce un collegamento. Gli alias della secondo e terzi forniscono nomi che è possibile usare per scenari diversi.

    ```csharp
    [Alias("UN","Writer","Editor")]
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Per altre informazioni sull'attributo Alias, vedere [dichiarazione di attributo Alias](./alias-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Dichiarazione di attributo di parametro](./parameter-attribute-declaration.md)

[Dichiarazione di attributo alias](./alias-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
