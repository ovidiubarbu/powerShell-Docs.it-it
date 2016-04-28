---
title: Ordinamento degli oggetti
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
---
# Ordinamento degli oggetti
È possibile organizzare i dati visualizzati per semplificarne l'analisi tramite il cmdlet **Sort-Object**. **Sort-Object** acquisisce il nome di una o più proprietà in base a cui ordinare e restituisce i dati ordinati in base ai valori di tali proprietà.

Un esempio può essere costituito dall'esigenza di elencare le istanze Win32_SystemDriver. Se si vuole ordinare in base a **State** e quindi in base a **Name**, è possibile digitare:

```
Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap
```

Nonostante si tratti di una visualizzazione estesa, gli elementi con lo stesso stato vengono raggruppati:

```
Name           State   Started DisplayName
----           -----   ------- -----------
ACPI           Running    True Microsoft ACPI Driver
AFD            Running    True AFD
AmdK7          Running    True AMD K7 Processor Driver
AsyncMac       Running    True RAS Asynchronous Media Driver
...
Abiosdsk       Stopped   False Abiosdsk
ACPIEC         Stopped   False ACPIEC
aec            Stopped   False Microsoft Kernel Acoustic Echo Canceller
...
```

È possibile ordinare gli oggetti anche in ordine inverso, specificando il parametro **Descending**. L'ordine viene invertito in modo che i nomi vengano ordinati in ordine alfabetico inverso e i numeri vengano ordinati per dimensioni decrescenti.

```
PS> Get-WmiObject -Class Win32_SystemDriver | Sort-Object -Property State,Name -Descending | Format-Table -Property Name,State,Started,DisplayName -AutoSize -Wrap

Name           State   Started DisplayName
----           -----   ------- -----------
WS2IFSL        Stopped   False Windows Socket 2.0 Non-IFS Service Provider Supp
                               ort Environment
wceusbsh       Stopped   False Windows CE USB Serial Host Driver...
...
wdmaud         Running    True Microsoft WINMM WDM Audio Compatibility Driver
Wanarp         Running    True Remote Access IP ARP Driver
...
```



<!--HONumber=Apr16_HO1-->


