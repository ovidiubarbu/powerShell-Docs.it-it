# Dichiarare una classe di base
È possibile dichiarare una classe di Windows PowerShell come tipo di base per un'altra classe di Windows PowerShell.

```PowerShell
class bar
{
   [int]foo() 
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

Si possono anche usare i tipi .NET Framework esistenti come classi di base:

```PowerShell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

<!--HONumber=Jun16_HO4-->


