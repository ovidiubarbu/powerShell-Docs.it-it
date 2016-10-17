
Distribuire in Automazione di Azure
===========================

Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) nella pagina dei dettagli dell'elemento consente di distribuire l'elemento da PowerShell Gallery in Automazione di Azure.

![Pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure)](Images/DeployToAzureAutomationButton.png)

Quando si fa clic su questo pulsante, si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure.
Se l'elemento include dipendenze, verranno distribuite anche tutte le dipendenze in Automazione di Azure.

AVVISO: se nell'account di Automazione esistono già lo stesso elemento e la stessa versione, se si esegue nuovamente la distribuzione da PowerShell Gallery, l'elemento nell'account di Automazione verrà sovrascritto.

Se si distribuisce un modulo, verrà visualizzato nella sezione Moduli di Automazione di Azure.  Se si distribuisce uno script, verrà visualizzato nella sezione Runbook di Automazione di Azure.

Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag AzureAutomationNotSupported ai metadati dell'elemento.

Per altre informazioni su Automazione di Azure, vedere il [sito Web di Automazione di Azure](http://azure.microsoft.com/en-us/services/automation/).



<!--HONumber=Aug16_HO3-->


