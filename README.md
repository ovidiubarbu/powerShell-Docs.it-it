# <a name="microsoft-open-source-code-of-conduct"></a>Codice di condotta Microsoft Open Source

Per questo progetto è stato adottato [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) (Codice di condotta Microsoft Open Source).
Per altre informazioni, vedere [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) (Domande frequenti sul codice di condotta) oppure contattare [opencode@microsoft.com](mailto:opencode@microsoft.com) per eventuali domande o commenti.

[![Stato della compilazione](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>Documentazione di PowerShell

Questo è il repository PowerShell-Docs, che contiene la documentazione ufficiale di PowerShell.

## <a name="repository-structure"></a>Struttura del repository

Ognuna delle cartelle di primo livello seguenti in questo repository contiene un set di documenti pubblicato in [Microsoft Docs](https://docs.microsoft.com/powershell).

- [/developer/](https://docs.microsoft.com/powershell/developer/) è la posizione futura della documentazione di PowerShell SDK
  - È in corso la migrazione di questo contenuto da MSDN
- [/dsc/](https://docs.microsoft.com/powershell/dsc/) per la funzionalità DSC (Desired State Configuration)
- [/gallery/](https://docs.microsoft.com/powershell/gallery) per [PowerShell Gallery](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) per la funzionalità JEA (Just Enough Administration)
- [/reference/](https://docs.microsoft.com/powershell/scripting/) per gli argomenti concettuali relativi a PowerShell e per le informazioni di riferimento sui moduli per le versioni 3.0, 4.0, 5.0, 5.1 e 6.0
  - Questo contenuto è anche l'origine del contenuto della Guida recuperato tramite il cmdlet `Get-Help`
- [/wmf](https://docs.microsoft.com/powershell/wmf/readme) contiene le note sulla versione per Windows Management Framework, il pacchetto usato per distribuire le nuove versioni di PowerShell nelle versioni precedenti di Windows.

## <a name="contributing"></a>Contributi

I contributi vengono aggiunti attivamente a questo repository tramite [richiesta pull](https://help.github.com/articles/using-pull-requests/) nel ramo di *staging*.
Si noti che prima di inviare una richiesta pull è necessario [firmare un contratto di licenza per i contributi](https://cla.microsoft.com/) in modo che la community possa liberamente usare i contributi inviati.

Per altre informazioni sui contributi, leggere la [guida per i collaboratori](CONTRIBUTING.md).
La guida per i collaboratori contiene informazioni dettagliate su come contribuire alla documentazione, sugli strumenti suggeriti, nonché sui requisiti di stile e di formattazione.
Usare i modelli per i problemi e le richieste di pull per garantire la coerenza della documentazione tra le varie versioni.

## <a name="licenses"></a>Licenze

Sono disponibili due file di licenza per questo progetto.
La licenza MIT si applica al codice contenuto in questo repository.
La licenza Creative Commons si applica alla documentazione.