# Cmdlet Clipboard
**Get-Clipboard** e **Set-Clipboard** rendono più semplice il trasferimento del contenuto in e da una sessione di Windows PowerShell. Nell'esempio seguente viene usato Esplora file per copiare tre file:

È ora possibile accedere facilmente al contenuto degli Appunti come un elenco di file:

PS C:\\&gt; Get-Clipboard -Format FileDropList

Directory: C:\\Users\\slee\\Downloads\\Example

Mode LastWriteTime Length Name

---- ------------- ------ ----

-a---- 14/04/2015 1.19 0 File2.txt

-a---- 14/04/2015 1.19 0 File3.txt

-a---- 14/04/2015 1.19 0 File1.txt

I cmdlet Clipboard supportano immagini, file audio, elenchi di file e testo.
<!--HONumber=Mar16_HO2-->
