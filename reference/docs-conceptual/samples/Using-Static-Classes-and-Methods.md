---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Uso di classi e metodi statici
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: 0f2b02c3a40365ad0335118b057a4e548c9f6535
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401921"
---
# <a name="using-static-classes-and-methods"></a><span data-ttu-id="efde0-103">Uso di classi e metodi statici</span><span class="sxs-lookup"><span data-stu-id="efde0-103">Using Static Classes and Methods</span></span>
<span data-ttu-id="efde0-104">Non tutte le classi .NET Framework possono essere create usando **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="efde0-104">Not all .NET Framework classes can be created by using **New-Object**.</span></span> <span data-ttu-id="efde0-105">Ad esempio, se si prova a creare un oggetto **System.Environment** o **System.Math** con **New-Object**, verranno visualizzati i messaggi di errore seguenti:</span><span class="sxs-lookup"><span data-stu-id="efde0-105">For example, if you try to create a **System.Environment** or a **System.Math** object with **New-Object**, you will get the following error messages:</span></span>

```
PS> New-Object System.Environment
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Environment.
At line:1 char:11
+ New-Object  <<<< System.Environment

PS> New-Object System.Math
New-Object : Constructor not found. Cannot find an appropriate constructor for
type System.Math.
At line:1 char:11
+ New-Object  <<<< System.Math
```

<span data-ttu-id="efde0-106">Questi errori si verificano perché non è possibile creare un nuovo oggetto da queste classi.</span><span class="sxs-lookup"><span data-stu-id="efde0-106">These errors occur because there is no way to create a new object from these classes.</span></span> <span data-ttu-id="efde0-107">Queste classi sono librerie di riferimento di metodi e proprietà che non cambiano stato.</span><span class="sxs-lookup"><span data-stu-id="efde0-107">These classes are reference libraries of methods and properties that do not change state.</span></span> <span data-ttu-id="efde0-108">Non devono essere create, ma solo usate.</span><span class="sxs-lookup"><span data-stu-id="efde0-108">You don't need to create them, you simply use them.</span></span> <span data-ttu-id="efde0-109">I metodi e le classi di questo tipo sono denominate *classi statiche*, perché non vengono create, eliminate o modificate.</span><span class="sxs-lookup"><span data-stu-id="efde0-109">Classes and methods such as these are called *static classes* because they are not created, destroyed, or changed.</span></span> <span data-ttu-id="efde0-110">Per chiarire il concetto verranno forniti esempi che usano le classi statiche.</span><span class="sxs-lookup"><span data-stu-id="efde0-110">To make this clear we will provide examples that use static classes.</span></span>

### <a name="getting-environment-data-with-systemenvironment"></a><span data-ttu-id="efde0-111">Recupero di dati dell'ambiente con System.Environment</span><span class="sxs-lookup"><span data-stu-id="efde0-111">Getting Environment Data with System.Environment</span></span>
<span data-ttu-id="efde0-112">In genere, il primo passaggio quando si lavora con un oggetto in Windows PowerShell consiste nell'usare Get-Member per scoprire quali membri contiene.</span><span class="sxs-lookup"><span data-stu-id="efde0-112">Usually, the first step in working with an object in Windows PowerShell is to use Get-Member to find out what members it contains.</span></span> <span data-ttu-id="efde0-113">Con le classi statiche, il processo è leggermente diverso perché la classe non è realmente un oggetto.</span><span class="sxs-lookup"><span data-stu-id="efde0-113">With static classes, the process is a little different because the actual class is not an object.</span></span>

#### <a name="referring-to-the-static-systemenvironment-class"></a><span data-ttu-id="efde0-114">Riferimento alla classe statica System.Environment</span><span class="sxs-lookup"><span data-stu-id="efde0-114">Referring to the Static System.Environment Class</span></span>
<span data-ttu-id="efde0-115">Si può fare riferimento a una classe statica racchiudendo il nome della classe tra parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="efde0-115">You can refer to a static class by surrounding the class name with square brackets.</span></span> <span data-ttu-id="efde0-116">Ad esempio, si può fare riferimento a **System.Environment** digitando il nome tra parentesi quadre.</span><span class="sxs-lookup"><span data-stu-id="efde0-116">For example, you can refer to **System.Environment** by typing the name within brackets.</span></span> <span data-ttu-id="efde0-117">In questo modo vengono visualizzate alcune informazioni di tipo generico:</span><span class="sxs-lookup"><span data-stu-id="efde0-117">Doing so displays some generic type information:</span></span>

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> <span data-ttu-id="efde0-118">Come accennato in precedenza, Windows PowerShell antepone automaticamente '**System.**'</span><span class="sxs-lookup"><span data-stu-id="efde0-118">As we mentioned previously, Windows PowerShell automatically prepends '**System.**'</span></span> <span data-ttu-id="efde0-119">ai nomi di tipo quando si usa **New-Object**.</span><span class="sxs-lookup"><span data-stu-id="efde0-119">to type names when you use **New-Object**.</span></span> <span data-ttu-id="efde0-120">Lo stesso avviene quando si usa un nome di tipo tra parentesi quadre, quindi è possibile specificare **\[System.Environment]** come **\[Environment]**.</span><span class="sxs-lookup"><span data-stu-id="efde0-120">The same thing happens when using a bracketed type name, so you can specify **\[System.Environment]** as **\[Environment]**.</span></span>

<span data-ttu-id="efde0-121">La classe **System.Environment** contiene informazioni generali sull'ambiente di lavoro per il processo corrente, che quando si lavora in Windows PowerShell è powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="efde0-121">The **System.Environment** class contains general information about the working environment for the current process, which is powershell.exe when working within Windows PowerShell.</span></span>

<span data-ttu-id="efde0-122">Se si prova a visualizzare i dettagli di questa classe digitando **\[System.Environment] | Get-Member**, il tipo di oggetto restituito è **System.RuntimeType**, non **System.Environment**:</span><span class="sxs-lookup"><span data-stu-id="efde0-122">If you try to view details of this class by typing **\[System.Environment] | Get-Member**, the object type is reported as being **System.RuntimeType** , not **System.Environment**:</span></span>

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

<span data-ttu-id="efde0-123">Per visualizzare i membri statici con Get-Member, specificare il parametro **Static**:</span><span class="sxs-lookup"><span data-stu-id="efde0-123">To view static members with Get-Member, specify the **Static** parameter:</span></span>

```
PS> [System.Environment] | Get-Member -Static

   TypeName: System.Environment

Name                       MemberType Definition
----                       ---------- ----------
Equals                     Method     static System.Boolean Equals(Object ob...
Exit                       Method     static System.Void Exit(Int32 exitCode)
...
CommandLine                Property   static System.String CommandLine {get;}
CurrentDirectory           Property   static System.String CurrentDirectory ...
ExitCode                   Property   static System.Int32 ExitCode {get;set;}
HasShutdownStarted         Property   static System.Boolean HasShutdownStart...
MachineName                Property   static System.String MachineName {get;}
NewLine                    Property   static System.String NewLine {get;}
OSVersion                  Property   static System.OperatingSystem OSVersio...
ProcessorCount             Property   static System.Int32 ProcessorCount {get;}
StackTrace                 Property   static System.String StackTrace {get;}
SystemDirectory            Property   static System.String SystemDirectory {...
TickCount                  Property   static System.Int32 TickCount {get;}
UserDomainName             Property   static System.String UserDomainName {g...
UserInteractive            Property   static System.Boolean UserInteractive ...
UserName                   Property   static System.String UserName {get;}
Version                    Property   static System.Version Version {get;}
WorkingSet                 Property   static System.Int64 WorkingSet {get;}
TickCount                               ExitCode
```

<span data-ttu-id="efde0-124">A questo punto è possibile selezionare le proprietà da visualizzare da System.Environment.</span><span class="sxs-lookup"><span data-stu-id="efde0-124">We can now select properties to view from System.Environment.</span></span>

#### <a name="displaying-static-properties-of-systemenvironment"></a><span data-ttu-id="efde0-125">Visualizzazione delle proprietà statiche di System. Environment</span><span class="sxs-lookup"><span data-stu-id="efde0-125">Displaying Static Properties of System.Environment</span></span>

<span data-ttu-id="efde0-126">Anche le proprietà di System.Environment sono statiche e devono essere specificate in modo diverso rispetto alle proprietà normali.</span><span class="sxs-lookup"><span data-stu-id="efde0-126">The properties of System.Environment are also static, and must be specified in a different way than normal properties.</span></span> <span data-ttu-id="efde0-127">Usiamo **::** per indicare a Windows PowerShell che intendiamo usare un metodo o una proprietà statica.</span><span class="sxs-lookup"><span data-stu-id="efde0-127">We use **::** to indicate to Windows PowerShell that we want to work with a static method or property.</span></span> <span data-ttu-id="efde0-128">Per visualizzare il comando usato per avviare Windows PowerShell, controlliamo la proprietà **CommandLine** digitando:</span><span class="sxs-lookup"><span data-stu-id="efde0-128">To see the command that was used to launch Windows PowerShell, we check the **CommandLine** property by typing:</span></span>

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

<span data-ttu-id="efde0-129">Per controllare la versione del sistema operativo, visualizzare la proprietà OSVersion digitando:</span><span class="sxs-lookup"><span data-stu-id="efde0-129">To check the operating system version, display the OSVersion property by typing:</span></span>

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

<span data-ttu-id="efde0-130">Si può controllare se il computer sta eseguendo l'arresto visualizzando la proprietà **HasShutdownStarted**:</span><span class="sxs-lookup"><span data-stu-id="efde0-130">We can check whether the computer is in the process of shutting down by displaying the **HasShutdownStarted** property:</span></span>

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a><span data-ttu-id="efde0-131">Eseguire operazioni matematiche con System.Math</span><span class="sxs-lookup"><span data-stu-id="efde0-131">Doing Math with System.Math</span></span>

<span data-ttu-id="efde0-132">La classe statica System.Math è utile per l'esecuzione di operazioni matematiche.</span><span class="sxs-lookup"><span data-stu-id="efde0-132">The System.Math static class is useful for performing some mathematical operations.</span></span> <span data-ttu-id="efde0-133">I membri importanti di **System.Math** sono per lo più metodi, che è possibile visualizzare usando **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="efde0-133">The important members of **System.Math** are mostly methods, which we can display by using **Get-Member**.</span></span>

> [!NOTE]
> <span data-ttu-id="efde0-134">System.Math ha diversi metodi con lo stesso nome, che si distinguono in base al tipo dei relativi parametri.</span><span class="sxs-lookup"><span data-stu-id="efde0-134">System.Math has several methods with the same name, but they are distinguished by the type of their parameters.</span></span>

<span data-ttu-id="efde0-135">Digitare il comando seguente per elencare i metodi della classe **System.Math**.</span><span class="sxs-lookup"><span data-stu-id="efde0-135">Type the following command to list the methods of the **System.Math** class.</span></span>

```
PS> [System.Math] | Get-Member -Static -MemberType Methods

   TypeName: System.Math

Name            MemberType Definition
----            ---------- ----------
Abs             Method     static System.Single Abs(Single value), static Sy...
Acos            Method     static System.Double Acos(Double d)
Asin            Method     static System.Double Asin(Double d)
Atan            Method     static System.Double Atan(Double d)
Atan2           Method     static System.Double Atan2(Double y, Double x)
BigMul          Method     static System.Int64 BigMul(Int32 a, Int32 b)
Ceiling         Method     static System.Double Ceiling(Double a), static Sy...
Cos             Method     static System.Double Cos(Double d)
Cosh            Method     static System.Double Cosh(Double value)
DivRem          Method     static System.Int32 DivRem(Int32 a, Int32 b, Int3...
Equals          Method     static System.Boolean Equals(Object objA, Object ...
Exp             Method     static System.Double Exp(Double d)
Floor           Method     static System.Double Floor(Double d), static Syst...
IEEERemainder   Method     static System.Double IEEERemainder(Double x, Doub...
Log             Method     static System.Double Log(Double d), static System...
Log10           Method     static System.Double Log10(Double d)
Max             Method     static System.SByte Max(SByte val1, SByte val2), ...
Min             Method     static System.SByte Min(SByte val1, SByte val2), ...
Pow             Method     static System.Double Pow(Double x, Double y)
ReferenceEquals Method     static System.Boolean ReferenceEquals(Object objA...
Round           Method     static System.Double Round(Double a), static Syst...
Sign            Method     static System.Int32 Sign(SByte value), static Sys...
Sin             Method     static System.Double Sin(Double a)
Sinh            Method     static System.Double Sinh(Double value)
Sqrt            Method     static System.Double Sqrt(Double d)
Tan             Method     static System.Double Tan(Double a)
Tanh            Method     static System.Double Tanh(Double value)
Truncate        Method     static System.Decimal Truncate(Decimal d), static...
```

<span data-ttu-id="efde0-136">Il comando visualizza diversi metodi matematici.</span><span class="sxs-lookup"><span data-stu-id="efde0-136">This displays several mathematical methods.</span></span> <span data-ttu-id="efde0-137">Ecco un elenco di comandi che illustra il funzionamento di alcuni metodi comuni:</span><span class="sxs-lookup"><span data-stu-id="efde0-137">Here is a list of commands that demonstrate how some of the common methods work:</span></span>

```
PS> [System.Math]::Sqrt(9)
3
PS> [System.Math]::Pow(2,3)
8
PS> [System.Math]::Floor(3.3)
3
PS> [System.Math]::Floor(-3.3)
-4
PS> [System.Math]::Ceiling(3.3)
4
PS> [System.Math]::Ceiling(-3.3)
-3
PS> [System.Math]::Max(2,7)
7
PS> [System.Math]::Min(2,7)
2
PS> [System.Math]::Truncate(9.3)
9
PS> [System.Math]::Truncate(-9.3)
-9
```