Finora il codice dell'applicazione è stato eseguito come se all'app lavorasse un solo sviluppatore. In questa sezione si apprenderà come Connected Environment può semplificare lo sviluppo in team:
* Consentire a un team di sviluppatori di collaborare nello stesso ambiente di sviluppo.
* Ogni sviluppatore può eseguire iterazioni del codice di cui è responsabile in isolamento e senza timore di inficiare il lavoro di altri.
* Condurre test completi del codice, prima di eseguirne il commit, senza dover creare mockup o simulare dipendenze.

## <a name="challenges-with-developing-microservices"></a>Difficoltà per lo sviluppo di microservizi
L'applicazione di esempio non è molto complessa al momento. Nello sviluppo per il mondo reale, tuttavia, emergono difficoltà con l'aggiunta di altri servizi e l'espansione del team di sviluppo.

Si immagini di lavorare a un servizio che interagisce con decine di altri servizi.

1. Può diventare irrealistico eseguire tutto in locale per lo sviluppo. Il computer di sviluppo potrebbe non avere risorse sufficienti per eseguire l'intera app. L'app potrebbe anche avere endpoint che devono essere raggiungibili pubblicamente (ad esempio, l'app risponde a un webhook da un'app SaaS).
1. È possibile provare a eseguire solo i servizi da cui si dipende, ma in tal caso sarebbe necessario conoscere l'intera rete di dipendenze, incluse le dipendenze delle dipendenze. Occorre anche tenere conto che potrebbe non essere facile stabilire come compilare ed eseguire le dipendenze, perché sono state sviluppate da altri.
1. Alcuni sviluppatori ricorrono a simulazioni, o mockup, per molte delle dipendenze dei servizi. Questa soluzione può essere utile in alcuni casi, ma la gestione di questi mockup può diventare in fretta una vera e propria attività di sviluppo. Inoltre, in questo modo l'ambiente di sviluppo può diventare molto diverso da quello di produzione, con conseguente introduzione di bug difficili da individuare.
1. Ne consegue che diventa difficile eseguire in modo completo qualsiasi tipo di test. I test di integrazione possono avvenire realisticamente solo dopo il commit e questo significa che i problemi emergono in una fase avanzata del ciclo di sviluppo.

![](../media/microservices-challenges.png)


## <a name="work-in-a-shared-development-environment"></a>Lavorare in un ambiente di sviluppo condiviso
Con Connected Environment è possibile impostare un ambiente di sviluppo *condiviso* in Azure. Ogni sviluppatore può concentrarsi solo sulla parte assegnata dell'applicazione e può sviluppare in modo iterativo il *codice pre-commit* in un ambiente che già contiene tutti gli altri servizi e le risorse del cloud da cui dipendono i suoi scenari. Le dipendenze sono sempre aggiornate e gli sviluppatori lavorano in un ambiente che rispecchia quello di produzione.

## <a name="work-in-your-own-space"></a>Lavorare nello spazio personale
Quando si sviluppa il codice per il servizio e prima di essere pronti per l'archiviazione, spesso il codice non sarà in buono stato, perché sono ancora in corso le operazioni iterative di definizione, test e sperimentazione con soluzioni. Connected Environment usa il concetto di **spazio**, che consente di lavorare in isolamento e senza timore di inficiare il lavoro degli altri membri del team.

> [!Note]
> Prima di procedere, chiudere tutte le finestre di Visual Studio Code per entrambi i servizi, quindi eseguire `vsce up -d` in ciascuna delle cartelle radice del servizio. (Si tratta di una limitazione della versione di anteprima.)

Di seguito verrà esaminata più in dettaglio la posizione in cui sono in esecuzione i servizi. Eseguire il comando `vsce list`. Verrà visualizzato un output simile al seguente:

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------------------
mywebapi     mainline  mywebapi-0.1.0     80/TCP  2m ago     <not attached>
webfrontend  mainline  webfrontend-0.1.0  80/TCP  1m ago     https://webfrontend-contosodev.vsce.io
```

La colonna Space (Spazio) mostra che entrambi i servizi sono in esecuzione in uno spazio denominato `mainline`. Qualsiasi utente che apre l'URL pubblico e passa all'app Web richiamerà il percorso del codice scritto in precedenza che esegue entrambi i servizi. Si supponga ora di volere continuare a sviluppare `mywebapi`. Come è possibile eseguire questa operazione senza interruzioni per gli sviluppatori che usano l'ambiente di sviluppo? A tale scopo, verrà configurato uno spazio personale.

## <a name="create-a-space"></a>Creare uno spazio
Per eseguire una versione personalizzata di `mywebapi` in uno spazio diverso da `mainline`, verrà creato uno spazio specifico:
``` 
vsce space create --name scott
```

Nell'esempio precedente è stato usato il nome dello sviluppatore per il nuovo spazio in modo che sia facilmente identificabile per i colleghi, ma è possibile assegnare qualsiasi nome desiderato ed essere flessibili sul significato, ad esempio 'sprint4' o "demo". 

Eseguire il comando `vsce space list` per visualizzare un elenco di tutti gli spazi nell'ambiente di sviluppo. Accanto allo spazio attualmente selezionato viene visualizzato un asterisco (*). In questo caso, lo spazio denominato 'scott' è stato selezionato automaticamente al momento della creazione. È possibile selezionare un altro spazio in qualsiasi momento con il comando `vsce space select`.
