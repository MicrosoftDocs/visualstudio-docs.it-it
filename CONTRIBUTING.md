# <a name="contributing"></a>Contributi al codice

Grazie per aver contribuito alla documentazione di Visual Studio.

Questo argomento illustra il processo di base per l'aggiunta o l'aggiornamento del contenuto nel [sito della documentazione di Visual Studio](https://docs.microsoft.com/visualstudio).

In questo argomento verranno esaminati i seguenti aspetti:

* [Processo per fornire il contributo](#process-for-contributing)
* [Elenco di controllo per il materiale sussidiario](#guidance-checklist)
* [Creazione dei documenti](#building-the-docs)
* [Contributo per gli esempi](#contributing-to-samples)
* [Contratto di licenza con il collaboratore](#contributor-license-agreement)

## <a name="process-for-contributing"></a>Processo per fornire il contributo

**Passaggio 1:** aprire un problema che descrive l'articolo che si desidera scrivere e la relazione con il contenuto esistente.
Il contenuto all'interno della cartella **documenti** è suddiviso in sezioni suddivise per area del contenuto (ad esempio, debugger). Provare a determinare la cartella corretta per il nuovo contenuto. Ottenere feedback sulla proposta. 

È possibile saltare questo il primo passaggio per modifiche minime.

**Passaggio 2:** creare una copia tramite fork del repository `MicrosoftDocs/visualstudio-docs`.

**Passaggio 3:** creare un `branch` per l'articolo.

**Passaggio 4:** scrivere l'articolo.

Se si tratta di un nuovo argomento, è possibile usare questo [file modello](./styleguide/template.md) come punto di partenza. Contiene le linee guida per la scrittura e illustra anche i metadati necessari per ogni articolo, ad esempio le informazioni sull'autore.

Passare alla cartella che corrisponde alla posizione del sommario determinata per l'articolo nel passaggio 1.
Questa cartella contiene i file markdown per tutti gli articoli nella sezione. Se necessario, creare una nuova cartella in cui inserire i file per il contenuto.

Per le immagini e altre risorse statiche, aggiungerle alla sottocartella denominata **file multimediali**. Se si sta creando una nuova cartella per il contenuto, aggiungere una cartella di file multimediali alla nuova cartella.

Assicurarsi di seguire la sintassi di Markdown appropriata. Per altre informazioni, vedere la [guida di stile](./styleguide/template.md).

### <a name="example-structure"></a>Struttura di esempio

    docs
      /debugger
          debugging-installed-app-package.md
          /media
              debugging-installed-app-package.png

**Passaggio 5:** inviare una richiesta pull (PR) dal branch a `MicrosoftDocs/visualstudio-docs/master`.

Se la richiesta pull tratta un problema esistente, aggiungere la parola chiave `Fixes #Issue_Number` al messaggio di commit o alla descrizione della richiesta pull, in modo che il problema possa essere automaticamente chiuso quando viene eseguito il merge della richiesta pull. Per altre informazioni vedere l'argomento relativo alla [chiusura di problemi tramite i messaggi di commit](https://help.github.com/articles/closing-issues-via-commit-messages/).

Il team di Visual Studio esaminerà la richiesta pull e informerà l'utente se la modifica è corretta o se sono necessari altri aggiornamenti o modifiche per l'approvazione.

**Passaggio 6:** eseguire gli aggiornamenti necessari per il ramo come discusso con il team.

Dopo aver applicato il feedback e se le modifiche sono corrette, i responsabili eseguiranno il merge della richiesta pull nel ramo master.

A intervalli stabiliti, verrà eseguito il push di tutti i commit dal ramo master al ramo attivo e l'utente sarà in grado di visualizzare i propri contributi in tempo reale in https://docs.microsoft.com/visualstudio/.

## <a name="dos-and-donts"></a>Cosa fare e cosa non fare

Di seguito è riportato un breve elenco di regole che è necessario tenere presenti quando si inviano contributi alla documentazione di .NET.

- **NON** inviare richieste pull di grandi dimensioni. Al contrario, segnalare un problema e avviare una discussione in modo che si possa concordare una direzione prima di investire una grande quantità di tempo.
- **LEGGERE** le linee guida riportate nella [Guida di stile](./styleguide/template.md) e sulla [voce e tono](./styleguide/voice-tone.md).
- **USARE** il file [modello](./styleguide/template.md) come punto di partenza del proprio lavoro.
- **CREARE** un ramo separato nel fork prima di lavorare sugli articoli.
- **SEGUIRE** il [flusso di lavoro di GitHub Flow](https://guides.github.com/introduction/flow/).
- **SCIVERE UN BLOG O INVIARE TWEET** (o usare altri mezzi) frequentemente per informazioni sui contributi.

> [!NOTE]
> Si potrebbe notare che alcuni degli argomenti attualmente non seguono tutte le linee guida indicate qui e nella [Guida di stile](./styleguide/template.md). Ci stiamo impegnando per il raggiungimento della coerenza in tutto il sito. Controllare l'elenco dei [problemi aperti](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) che stiamo attualmente verificando per questo obiettivo specifico.

## <a name="building-the-docs"></a>Creazione dei documenti

La documentazione è scritta in [GitHub Flavored Markdown](https://help.github.com/categories/writing-on-github/) e compilata con [DocFX](https://dotnet.github.io/docfx/) e altri strumenti di pubblicazione/creazione interni. È ospitata in [docs.microsoft.com](https://docs.microsoft.com/dotnet).

Se si desidera creare la documentazione in locale, è necessario installare [DocFX](https://dotnet.github.io/docfx/); le versioni più recenti sono quelle più adatte.

Esistono diversi modi per usare DocFX e la maggior parte di essi vengono illustrati nell'[Introduzione a DocFX](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html).
Le istruzioni seguenti usano la versione [basata sulla riga di comando](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html#2-use-docfx-as-a-command-line-tool) dello strumento.
Se si ha familiarità con gli altri modi elencati nel collegamento precedente, è possibile usare altri strumenti.

**Nota:** attualmente DocFX richiede .NET Framework in Windows o Mono (per Linux o macOS). Speriamo di convertirlo in futuro per .NET Core.

È possibile creare e visualizzare in anteprima il sito risultante in locale usando un server Web incorporato. Passare alla cartella core-docs nel computer e digitare il comando seguente:

```
docfx -t default --serve
```

Verrà avviata l'anteprima locale su [localhost:8080](http://localhost:8080). È quindi possibile visualizzare le modifiche, andando all'indirizzo `http://localhost:8080/[path]`, ad esempio http://localhost:8080/articles/welcome.html.

**Nota:** l'anteprima locale attualmente non contiene i temi, pertanto l'aspetto non sarà lo stesso che verrà visualizzato nel sito della documentazione. Stiamo lavorando per risolvere tale esperienza.

# <a name="contributing-to-samples"></a>Contributo per gli esempi

Per ora, includere il codice di esempio necessario come blocchi di codice inline nell'articolo. Il repository contiene una cartella di Codesnippets ma non è pronta per i contributi pubblici.
