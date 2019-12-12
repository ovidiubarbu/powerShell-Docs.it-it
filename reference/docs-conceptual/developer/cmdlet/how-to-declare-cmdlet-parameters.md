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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365680"
---
# <a name="how-to-declare-cmdlet-parameters"></a><span data-ttu-id="adbc8-102">Come dichiarare i parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="adbc8-102">How to Declare Cmdlet Parameters</span></span>

<span data-ttu-id="adbc8-103">In questi esempi viene illustrato come dichiarare i parametri denominati, posizionali, obbligatori, facoltativi e di cambio.</span><span class="sxs-lookup"><span data-stu-id="adbc8-103">These examples show how to declare named, positional, required, optional, and switch parameters.</span></span> <span data-ttu-id="adbc8-104">Questi esempi illustrano anche come definire un alias di parametro.</span><span class="sxs-lookup"><span data-stu-id="adbc8-104">These examples also show how to define a parameter alias.</span></span>

## <a name="how-to-declare-a-named-parameter"></a><span data-ttu-id="adbc8-105">Come dichiarare un parametro denominato</span><span class="sxs-lookup"><span data-stu-id="adbc8-105">How to Declare a Named Parameter</span></span>

- <span data-ttu-id="adbc8-106">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="adbc8-106">Define a public property as shown in the following code.</span></span> <span data-ttu-id="adbc8-107">Quando si aggiunge l'attributo Parameter, omettere la parola chiave `Position` dall'attributo.</span><span class="sxs-lookup"><span data-stu-id="adbc8-107">When you add the Parameter attribute, omit the `Position` keyword from the attribute.</span></span>

    ```csharp
    [Parameter()]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="adbc8-108">Per ulteriori informazioni sull'attributo Parameter, vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="adbc8-108">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-positional-parameter"></a><span data-ttu-id="adbc8-109">Come dichiarare un parametro posizionale</span><span class="sxs-lookup"><span data-stu-id="adbc8-109">How to Declare a Positional Parameter</span></span>

- <span data-ttu-id="adbc8-110">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="adbc8-110">Define a public property as shown in the following code.</span></span> <span data-ttu-id="adbc8-111">Quando si aggiunge l'attributo Parameter, impostare la parola chiave `Position` sulla posizione dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="adbc8-111">When you add the Parameter attribute, set the `Position` keyword to the argument position.</span></span> <span data-ttu-id="adbc8-112">Il valore 0 indica la prima posizione.</span><span class="sxs-lookup"><span data-stu-id="adbc8-112">A value of 0 indicates the first position.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="adbc8-113">Per ulteriori informazioni sull'attributo Parameter, vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="adbc8-113">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-mandatory-parameter"></a><span data-ttu-id="adbc8-114">Come dichiarare un parametro obbligatorio</span><span class="sxs-lookup"><span data-stu-id="adbc8-114">How to Declare a Mandatory Parameter</span></span>

- <span data-ttu-id="adbc8-115">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="adbc8-115">Define a public property as shown in the following code.</span></span> <span data-ttu-id="adbc8-116">Quando si aggiunge l'attributo Parameter, impostare la parola chiave `Mandatory` su `true`.</span><span class="sxs-lookup"><span data-stu-id="adbc8-116">When you add the Parameter attribute, set the `Mandatory` keyword to `true`.</span></span>

    ```csharp
    [Parameter(Position = 0, Mandatory = true)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

<span data-ttu-id="adbc8-117">Per ulteriori informazioni sull'attributo Parameter, vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="adbc8-117">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-an-optional-parameter"></a><span data-ttu-id="adbc8-118">Come dichiarare un parametro facoltativo</span><span class="sxs-lookup"><span data-stu-id="adbc8-118">How to Declare an Optional Parameter</span></span>

- <span data-ttu-id="adbc8-119">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="adbc8-119">Define a public property as shown in the following code.</span></span> <span data-ttu-id="adbc8-120">Quando si aggiunge l'attributo Parameter, omettere la parola chiave `Mandatory`.</span><span class="sxs-lookup"><span data-stu-id="adbc8-120">When you add the Parameter attribute, omit the `Mandatory` keyword.</span></span>

    ```csharp
    [Parameter(Position = 0)]
    public string UserName
    {
      get { return userName; }
      set { userName = value; }
    }
    private string userName;
    ```

## <a name="how-to-declare-a-switch-parameter"></a><span data-ttu-id="adbc8-121">Come dichiarare un parametro switch</span><span class="sxs-lookup"><span data-stu-id="adbc8-121">How to Declare a Switch Parameter</span></span>

- <span data-ttu-id="adbc8-122">Definire una proprietà pubblica come Type [System. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), quindi dichiarare l'attributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="adbc8-122">Define a public property as type [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter), and then declare the Parameter attribute.</span></span>

    ```csharp
    [Parameter(Position = 1)]
    public SwitchParameter GoodBye
    {
      get { return goodbye; }
      set { goodbye = value; }
    }
    private bool goodbye;
    ```

<span data-ttu-id="adbc8-123">Per ulteriori informazioni sull'attributo Parameter, vedere [dichiarazione di attributo Parameter](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="adbc8-123">For more information about the Parameter attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

## <a name="how-to-declare-a-parameter-with-aliases"></a><span data-ttu-id="adbc8-124">Come dichiarare un parametro con alias</span><span class="sxs-lookup"><span data-stu-id="adbc8-124">How to Declare a Parameter with Aliases</span></span>

- <span data-ttu-id="adbc8-125">Definire una proprietà pubblica come illustrato nel codice seguente.</span><span class="sxs-lookup"><span data-stu-id="adbc8-125">Define a public property as shown in the following code.</span></span> <span data-ttu-id="adbc8-126">Aggiungere un attributo alias che elenchi gli alias per il parametro.</span><span class="sxs-lookup"><span data-stu-id="adbc8-126">Add an Alias attribute that lists the aliases for the parameter.</span></span> <span data-ttu-id="adbc8-127">In questo esempio vengono definiti tre alias per lo stesso parametro.</span><span class="sxs-lookup"><span data-stu-id="adbc8-127">In this example, three aliases are defined for the same parameter.</span></span> <span data-ttu-id="adbc8-128">Il primo alias fornisce un collegamento.</span><span class="sxs-lookup"><span data-stu-id="adbc8-128">The first alias provides a shortcut.</span></span> <span data-ttu-id="adbc8-129">Il secondo e il terzo alias forniscono i nomi che è possibile usare per diversi scenari.</span><span class="sxs-lookup"><span data-stu-id="adbc8-129">The second and third aliases provide names you can use for different scenarios.</span></span>

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

<span data-ttu-id="adbc8-130">Per ulteriori informazioni sull'attributo alias, vedere [dichiarazione di attributo alias](./alias-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="adbc8-130">For more information about the Alias attribute, see [Alias Attribute Declaration](./alias-attribute-declaration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="adbc8-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="adbc8-131">See Also</span></span>

[<span data-ttu-id="adbc8-132">System. Management. Automation. SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="adbc8-132">System.Management.Automation.SwitchParameter</span></span>](/dotnet/api/System.Management.Automation.SwitchParameter)

[<span data-ttu-id="adbc8-133">Dichiarazione dell'attributo Parameter</span><span class="sxs-lookup"><span data-stu-id="adbc8-133">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="adbc8-134">Dichiarazione dell'attributo alias</span><span class="sxs-lookup"><span data-stu-id="adbc8-134">Alias Attribute Declaration</span></span>](./alias-attribute-declaration.md)

[<span data-ttu-id="adbc8-135">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="adbc8-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
