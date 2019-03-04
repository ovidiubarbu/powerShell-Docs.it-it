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
ms.openlocfilehash: d6613889ebd2ba139ce0b3de1b8d24e4aec37d2a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861397"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="52790-102">Come dichiarare i parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="52790-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="52790-103">Questi esempi mostrano come dichiarare denominati, posizionali, obbligatorio, facoltativo e parametri opzionali.</span><span class="sxs-lookup"><span data-stu-id="52790-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="52790-104">Questi esempi illustrano inoltre come definire un alias del parametro.</span><span class="sxs-lookup"><span data-stu-id="52790-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="52790-105">Come dichiarare un parametro denominato</span><span class="sxs-lookup"><span data-stu-id="52790-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="52790-106">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="52790-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="52790-107">Quando si aggiunge l'attributo Parameter, omettere il `Position` parola chiave dall'attributo.</span><span class="sxs-lookup"><span data-stu-id="52790-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="52790-108">Per altre informazioni relative all'attributo di parametro, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="52790-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="52790-109">Come dichiarare un parametro posizionale</span><span class="sxs-lookup"><span data-stu-id="52790-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="52790-110">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="52790-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="52790-111">Quando si aggiunge l'attributo Parameter, impostare il `Position` una parola chiave per la posizione dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="52790-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="52790-112">Il valore 0 indica la prima posizione.</span><span class="sxs-lookup"><span data-stu-id="52790-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="52790-113">Per altre informazioni relative all'attributo di parametro, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="52790-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="52790-114">Come dichiarare un parametro obbligatorio</span><span class="sxs-lookup"><span data-stu-id="52790-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="52790-115">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="52790-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="52790-116">Quando si aggiunge l'attributo Parameter, impostare il `Mandatory` parola chiave da `true`.</span><span class="sxs-lookup"><span data-stu-id="52790-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="52790-117">Per altre informazioni relative all'attributo di parametro, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="52790-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="52790-118">Come dichiarare un parametro facoltativo</span><span class="sxs-lookup"><span data-stu-id="52790-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="52790-119">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="52790-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="52790-120">Quando si aggiunge l'attributo Parameter, omettere il `Mandatory` (parola chiave).</span><span class="sxs-lookup"><span data-stu-id="52790-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="52790-121">Come dichiarare un parametro opzionale</span><span class="sxs-lookup"><span data-stu-id="52790-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="52790-122">Definire una proprietà pubblica come tipo [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter)e quindi dichiarare l'attributo di parametro.</span><span class="sxs-lookup"><span data-stu-id="52790-122">Define a public property as type [System.Management.Automation.Switchparameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="52790-123">Per altre informazioni relative all'attributo di parametro, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="52790-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="52790-124">Come dichiarare un parametro con alias</span><span class="sxs-lookup"><span data-stu-id="52790-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="52790-125">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="52790-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="52790-126">Aggiungere un Alias (attributo) che elenca gli alias per il parametro.</span><span class="sxs-lookup"><span data-stu-id="52790-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="52790-127">In questo esempio vengono definiti tre alias per lo stesso parametro.</span><span class="sxs-lookup"><span data-stu-id="52790-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="52790-128">L'alias prima fornisce un collegamento.</span><span class="sxs-lookup"><span data-stu-id="52790-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="52790-129">Gli alias della secondo e terzi forniscono nomi che è possibile usare per scenari diversi.</span><span class="sxs-lookup"><span data-stu-id="52790-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="52790-130">Per altre informazioni sull'attributo Alias, vedere [dichiarazione di attributo Alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="52790-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="52790-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="52790-131">See Also</span></span>

[<span data-ttu-id="52790-132">System.Management.Automation.Switchparameter</span><span class="sxs-lookup"><span data-stu-id="52790-132">System.Management.Automation.Switchparameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="52790-133">Dichiarazione di attributo di parametro</span><span class="sxs-lookup"><span data-stu-id="52790-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="52790-134">Dichiarazione di attributo alias</span><span class="sxs-lookup"><span data-stu-id="52790-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="52790-135">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52790-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
