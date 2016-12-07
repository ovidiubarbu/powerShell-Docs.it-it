# <a name="clipboard-cmdlets"></a>Cmdlet Clipboard
**Get-Clipboard** e **Set-Clipboard** rendono più semplice il trasferimento del contenuto in e da una sessione di Windows PowerShell. Se ad esempio si usa Esplora risorse per copiare tre file negli Appunti (selezionandoli e premendo `ctrl-c` ad esempio), è possibile accedere facilmente al contenuto degli Appunti come elenco di file:

```powershell 
PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 4/14/2015 1:19 PM 0 File2.txt

-a---- 4/14/2015 1:19 PM 0 File3.txt

-a---- 4/14/2015 1:19 PM 0 File1.txt
```


I cmdlet Clipboard supportano immagini, file audio, elenchi di file e testo.
