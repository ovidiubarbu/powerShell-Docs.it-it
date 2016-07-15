# Risorse DSC basate su classi

## Definizione delle risorse DSC con le classi

In base ai commenti e ai suggerimenti ricevuti, la creazione di risorse DSC basate su classi è stata semplificata ed è di più facile comprensione. Le principali differenze tra una risorsa DSC basata su classe e un provider di risorse DSC basato su cmdlet sono:

* Non è necessario un file MOF per lo schema.
* Non è necessaria una sottocartella **DSCResource** nella cartella del modulo.
* Un file di modulo di PowerShell può contenere più classi di risorse DSC.

Per altre informazioni, vedere [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](https://msdn.microsoft.com/powershell/dsc/authoringresource).


<!--HONumber=Jul16_HO1-->


