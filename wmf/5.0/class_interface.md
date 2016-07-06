# Dichiarare l'interfaccia implementata

È possibile dichiarare le interfacce implementate dopo i tipi di base o subito dopo i due punti (:), se non è specificato alcun tipo di base. Usare le virgole per separare tutti i nomi di tipo. La sintassi è molto simile a quella di C#.

```PowerShell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```

<!--HONumber=Jun16_HO4-->


