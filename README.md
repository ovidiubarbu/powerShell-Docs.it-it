## <a name="microsoft-open-source-code-of-conduct"></a>Codice di condotta Microsoft Open Source

Per questo progetto è stato adottato [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) (Codice di condotta Microsoft Open Source).
Per altre informazioni, vedere [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) (Domande frequenti sul codice di condotta) oppure contattare [opencode@microsoft.com](mailto:opencode@microsoft.com) per eventuali domande o commenti.

[![Stato della compilazione](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

# <a name="powershell-documentation"></a>Documentazione di PowerShell

Questo è il repository PowerShell-Docs, che contiene la documentazione ufficiale di Windows PowerShell. 

## <a name="repository-structure"></a>Struttura del repository
Ogni cartella in questo repository viene pubblicata in [MSDN](https://msdn.microsoft.com/en-us/powershell). Le cartelle corrispondono alle risorse di PowerShell seguenti:
* [/dsc/](https://msdn.microsoft.com/en-us/powershell/dsc/) per la funzionalità DSC (Desired State Configuration)
* [/gallery/](https://msdn.microsoft.com/powershell/gallery) per [PowerShell Gallery](https://www.powershellgallery.com/)
* [/jea/](https://msdn.microsoft.com/powershell/jea/) per la funzionalità JEA (Just Enough Administration)
* [/reference/](https://msdn.microsoft.com/powershell/reference/) per le informazioni di riferimento sui moduli di PowerShell per le versioni 2.0, 3.0, 4.0, 5.0, 5.1 e 6.0
  * Questo contenuto verrà recuperato dal cmdlet `Get-Help` in futuro
* [/scripting/](https://msdn.microsoft.com/en-us/powershell/scripting/) per il contenuto di riferimento generale su PowerShell
* [/wmf](https://msdn.microsoft.com/en-us/powershell/wmf/readme) contiene le note sulla versione per Windows Management Framework, il pacchetto usato per distribuire le nuove versioni di PowerShell nelle versioni precedenti di Windows. 



## <a name="contributing"></a>Contributi

I contributi vengono aggiunti attivamente a questo repository tramite [richiesta pull](https://help.github.com/articles/using-pull-requests/) nel ramo di *staging*. Si noti che prima di inviare una richiesta pull è necessario [firmare un contratto di licenza per i contributi](https://cla.microsoft.com/) in modo che la community possa liberamente usare i contributi inviati.
Per altre informazioni sui contributi, leggere la [guida ai contributi](CONTRIBUTING.md).
Esiste una bozza della [guida di stile](./STYLE.md) da esaminare prima di inviare contributi.
Usare i modelli per i problemi e le richieste di pull per garantire la coerenza della documentazione tra le varie versioni. 

## <a name="licenses"></a>Licenze

Sono disponibili due file di licenza per questo progetto. La licenza MIT si applica al codice contenuto in questo repository.
La licenza Creative Commons si applica alla documentazione. 
