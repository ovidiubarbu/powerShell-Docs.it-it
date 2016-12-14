# <a name="new-guid"></a>New-Guid
Spesso, durante la scrittura di script o anche di una risorsa DSC, può risultare necessario un identificatore univoco. I GUID sono adatti ed è semplice chiamare la classe Guid di .NET Framework per generarne uno, ma la disponibilità di un cmdlet rende questo meccanismo più visibile per gli utenti finali che non hanno già familiarità con questa classe di .NET Framework:

PS C:\\&gt; New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
