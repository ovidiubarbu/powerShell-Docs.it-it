---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Uso di classi e metodi statici
ms.assetid: 418ad766-afa6-4b8c-9a44-471889af7fd9
ms.openlocfilehash: fe41c7d6b45564e7b5bc2b922a18587c9745e26d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="using-static-classes-and-methods"></a>Uso di classi e metodi statici
Non tutte le classi .NET Framework possono essere create usando **New-Object**. Ad esempio, se si prova a creare un oggetto **System.Environment** o **System.Math** con **New-Object**, verranno visualizzati i messaggi di errore seguenti:

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

Questi errori si verificano perché non è possibile creare un nuovo oggetto da queste classi. Queste classi sono librerie di riferimento di metodi e proprietà che non cambiano stato. Non devono essere create, ma solo usate. I metodi e le classi di questo tipo sono denominate *classi statiche*, perché non vengono create, eliminate o modificate. Per chiarire il concetto verranno forniti esempi che usano le classi statiche.

### <a name="getting-environment-data-with-systemenvironment"></a>Recupero di dati dell'ambiente con System.Environment
In genere, il primo passaggio quando si lavora con un oggetto in Windows PowerShell consiste nell'usare Get-Member per scoprire quali membri contiene. Con le classi statiche, il processo è leggermente diverso perché la classe non è realmente un oggetto.

#### <a name="referring-to-the-static-systemenvironment-class"></a>Riferimento alla classe statica System.Environment
Si può fare riferimento a una classe statica racchiudendo il nome della classe tra parentesi quadre. Ad esempio, si può fare riferimento a **System.Environment** digitando il nome tra parentesi quadre. In questo modo vengono visualizzate alcune informazioni di tipo generico:

```
PS> [System.Environment]

IsPublic IsSerial Name                                     BaseType
-------- -------- ----                                     --------
True     False    Environment                              System.Object
```

> [!NOTE]
> Come accennato in precedenza, Windows PowerShell antepone automaticamente '**System.**' ai nomi di tipo quando si usa **New-Object**. Lo stesso avviene quando si usa un nome di tipo tra parentesi quadre, quindi è possibile specificare **\[System.Environment]** come **\[Environment]**.

La classe **System.Environment** contiene informazioni generali sull'ambiente di lavoro per il processo corrente, che quando si lavora in Windows PowerShell è powershell.exe.

Se si prova a visualizzare i dettagli di questa classe digitando **\[System.Environment] | Get-Member**, il tipo di oggetto restituito è **System.RuntimeType**, non **System.Environment**:

```
PS> [System.Environment] | Get-Member

   TypeName: System.RuntimeType
```

Per visualizzare i membri statici con Get-Member, specificare il parametro **Static**:

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

A questo punto è possibile selezionare le proprietà da visualizzare da System.Environment.

#### <a name="displaying-static-properties-of-systemenvironment"></a>Visualizzazione delle proprietà statiche di System. Environment
Anche le proprietà di System.Environment sono statiche e devono essere specificate in modo diverso rispetto alle proprietà normali. Usiamo **::** per indicare a Windows PowerShell che intendiamo usare un metodo o una proprietà statica. Per visualizzare il comando usato per avviare Windows PowerShell, controlliamo la proprietà **CommandLine** digitando:

```
PS> [System.Environment]::Commandline
"C:\Program Files\Windows PowerShell\v1.0\powershell.exe"
```

Per controllare la versione del sistema operativo, visualizzare la proprietà OSVersion digitando:

```
PS> [System.Environment]::OSVersion

           Platform ServicePack         Version             VersionString
           -------- -----------         -------             -------------
            Win32NT Service Pack 2      5.1.2600.131072     Microsoft Windows...
```

Si può controllare se il computer sta eseguendo l'arresto visualizzando la proprietà **HasShutdownStarted**:

```
PS> [System.Environment]::HasShutdownStarted
False
```

### <a name="doing-math-with-systemmath"></a>Eseguire operazioni matematiche con System.Math
La classe statica System.Math è utile per l'esecuzione di operazioni matematiche. I membri importanti di **System.Math** sono per lo più metodi, che è possibile visualizzare usando **Get-Member**.

> [!NOTE]
> System.Math ha diversi metodi con lo stesso nome, che si distinguono in base al tipo dei relativi parametri.

Digitare il comando seguente per elencare i metodi della classe **System.Math**.

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

Il comando visualizza diversi metodi matematici. Ecco un elenco di comandi che illustra il funzionamento di alcuni metodi comuni:

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

