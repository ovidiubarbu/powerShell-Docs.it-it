---
title: Come dichiarare i parametri dei cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c0509cc-5a50-49ad-a74f-5527023d0270
caps.latest.revision: 10
ms.openlocfilehash: 80e3e27bcf72b078c192525a843a3b3afb306529
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365680"
---
# <a name="how-to-declare-cmdlet-parameters"></a>Come dichiarare i parametri dei cmdlet

In questi esempi viene illustrato come dichiarare i parametri denominati, posizionali, obbligatori, facoltativi e di cambio. Questi esempi illustrano anche come definire un alias di parametro.

## <a name="how-to-declare-a-named-parameter"></a>Come dichiarare un parametro denominato

- Definire una proprietà pubblica come illustrato nel codice seguente. Quando si aggiunge l'attributo Parameter, omettere la parola chiave `Position` dall'attributo.

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Per ulteriori informazioni sull'attributo Parameter, vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-positional-parameter"></a>Come dichiarare un parametro posizionale

- Definire una proprietà pubblica come illustrato nel codice seguente. Quando si aggiunge l'attributo Parameter, impostare la parola chiave `Position` sulla posizione dell'argomento. Il valore 0 indica la prima posizione.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Per ulteriori informazioni sull'attributo Parameter, vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-mandatory-parameter"></a>Come dichiarare un parametro obbligatorio

- Definire una proprietà pubblica come illustrato nel codice seguente. Quando si aggiunge l'attributo Parameter, impostare la parola chiave `Mandatory` su `true`.

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

Per ulteriori informazioni sull'attributo Parameter, vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).

## <a name="how-to-declare-an-optional-parameter"></a>Come dichiarare un parametro facoltativo

- Definire una proprietà pubblica come illustrato nel codice seguente. Quando si aggiunge l'attributo Parameter, omettere la parola chiave `Mandatory`.

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a>Come dichiarare un parametro switch

- Definire una proprietà pubblica come Type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), quindi dichiarare l'attributo Parameter.

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

Per ulteriori informazioni sull'attributo Parameter, vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).

## <a name="how-to-declare-a-parameter-with-aliases"></a>Come dichiarare un parametro con alias

- Definire una proprietà pubblica come illustrato nel codice seguente. Aggiungere un attributo alias che elenchi gli alias per il parametro. In questo esempio vengono definiti tre alias per lo stesso parametro. Il primo alias fornisce un collegamento. Il secondo e il terzo alias forniscono i nomi che è possibile usare per diversi scenari.

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

Per ulteriori informazioni sull'attributo alias, vedere [dichiarazione di attributo alias](./alias-attribute-declaration.md).

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter)

[Dichiarazione dell'attributo Parameter](./parameter-attribute-declaration.md)

[Dichiarazione dell'attributo alias](./alias-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
