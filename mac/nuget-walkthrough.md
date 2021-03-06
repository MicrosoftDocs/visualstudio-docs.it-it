---
title: Inserimento di un pacchetto NuGet nel progetto
description: Questo documento illustra come includere un pacchetto NuGet in un progetto usando Visual Studio per Mac. Illustra in modo dettagliato come trovare e scaricare un pacchetto e offre un'introduzione alle funzionalità di integrazione dell'IDE.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.custom: conceptual
ms.openlocfilehash: 46ceb99617c6a0e9ba457fdb769c1162090d1d31
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493491"
---
# <a name="install-and-manage-nuget-packages-in-visual-studio-for-mac"></a>Installare e gestire i pacchetti NuGet in Visual Studio per Mac

L'interfaccia utente di gestione pacchetti NuGet in Visual Studio per Mac consente di installare, disinstallare e aggiornare facilmente i pacchetti NuGet in progetti e soluzioni. È possibile cercare e aggiungere pacchetti ai progetti .NET Core, ASP.NET Core e Novell.

Questo articolo descrive come includere un pacchetto NuGet in un progetto e illustra la catena di strumenti che rende facile il processo.

Per un'introduzione all'uso di NuGet in Visual Studio per Mac, vedere [Guida introduttiva: installare e usare un pacchetto in Visual Studio per Mac](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

## <a name="find-and-install-a-package"></a>Trovare e installare un pacchetto

1. Con un progetto aperto in Visual Studio per Mac, fare clic con il pulsante destro del mouse sulla cartella **dipendenze** (cartella **pacchetti** se si usa un progetto Novell) nella **finestra della soluzione** e selezionare **Gestisci pacchetti NuGet...**.

    ![Azione di contesto di aggiunta di un nuovo pacchetto NuGet](media/nuget-walkthrough-packages-menu.png)

2. Verrà avviata la finestra **Gestisci pacchetti NuGet** . Verificare che l'elenco a discesa di origine nell'angolo superiore sinistro della finestra di dialogo sia impostato su `nuget.org` , in modo che si stia eseguendo una ricerca nel repository di pacchetti NuGet centrale.

    ![Elenco di pacchetti NuGet](media/nuget-walkthrough-add-packages1.png)

3. Usare la casella di ricerca nell'angolo superiore destro per trovare un pacchetto specifico, ad esempio `EntityFramework`. Dopo aver trovato un pacchetto da usare, selezionarlo e fare clic sul pulsante **Aggiungi pacchetto** per avviare l'installazione.

    ![Aggiungere il pacchetto NuGet EntityFramework](media/nuget-walkthrough-add-packages2.png)

4. Dopo essere stato scaricato, il pacchetto verrà aggiunto al progetto. La soluzione cambierà a seconda del tipo di progetto che si sta modificando:

    **Progetti Novell**
    * Il nodo **Riferimenti** conterrà un elenco di tutti gli assembly che fanno parte di un pacchetto NuGet.
    * Il nodo **Pacchetti** mostra ogni pacchetto NuGet scaricato. È possibile aggiornare o rimuovere un pacchetto dall'elenco.
    
    **Progetti .NET Core**

    * Il nodo **dipendenze > NuGet** Visualizza ogni pacchetto NuGet scaricato. È possibile aggiornare o rimuovere un pacchetto dall'elenco.

## <a name="using-nuget-packages"></a>Uso di pacchetti NuGet

Dopo che il pacchetto NuGet è stato aggiunto e i riferimenti del progetto sono stati aggiornati, è possibile programmare usando le API come si farebbe con qualsiasi riferimento del progetto.

Assicurarsi di aggiungere le direttive `using` necessarie all'inizio del file:

```csharp
using Newtonsoft.Json;
```

<a name="Package_Updates" class="injected"></a>

## <a name="updating-packages"></a>Aggiornamento di pacchetti

Gli aggiornamenti dei pacchetti possono essere eseguiti contemporaneamente, facendo clic con il pulsante destro del mouse sul nodo **dipendenze** (nodo **pacchetti** per progetti Novell) o singolarmente in ogni pacchetto. Quando è disponibile una nuova versione di un pacchetto NuGet, viene visualizzata un'icona di aggiornamento ![ con il cerchio ](media/nuget-walkthrough-update-icon.png) .

Fare clic con il pulsante destro del mouse su **dipendenze** per accedere al menu di scelta rapida e scegliere **Aggiorna** per aggiornare tutti i pacchetti:

![Menu di scelta rapida dipendenze con il menu Aggiorna evidenziato](media/nuget-walkthrough-packages-menu-update.png)

* **Gestisci pacchetti NuGet** : apre la finestra per aggiungere altri pacchetti al progetto.
* **Aggiorna** - Controlla il server di origine per ogni pacchetto e scarica le eventuali versioni più recenti.
* **Ripristina** - Scarica tutti i pacchetti mancanti (senza aggiornare i pacchetti esistenti alle versioni più recenti).

Le opzioni Aggiorna e Ripristina sono disponibili anche a livello di soluzione e influiscono su tutti i progetti nella soluzione.

### <a name="updating-to-pre-release-versions-of-packages"></a>Aggiornamento alle versioni non definitive dei pacchetti
Per eseguire l'aggiornamento a una versione provvisoria più recente di un pacchetto, è possibile fare clic con il pulsante destro del mouse su **dipendenze** per aprire il menu di scelta rapida e scegliere il menu **Gestisci pacchetti NuGet** .

![Menu di scelta rapida dipendenze con Gestisci pacchetti NuGet... menu evidenziato](media/nuget-walkthrough-packages-menu-manage-nuget-packages.png)

Selezionare la casella di controllo **Mostra pacchetti pre-versione** nella parte inferiore della finestra di dialogo.

![Finestra di dialogo Gestisci pacchetti NuGet aperta con l'opzione ' Mostra pacchetti pre-versione ' selezionata](media/nuget-walkthrough-show-pre-release-packages.png)

Infine, nella scheda **aggiornamenti** della finestra di dialogo selezionare il pacchetto che si desidera aggiornare e scegliere la nuova versione non definitiva dall'elenco a discesa **nuova versione** , quindi fare clic su **Aggiorna pacchetto**.

![Finestra di dialogo Gestisci pacchetti NuGet aperta nella scheda installato con un pacchetto selezionato e l'elenco a discesa nuova versione.](media/nuget-walkthrough-packages-nuget-dialog-update-installed-package.png)

### <a name="locating-outdated-packages"></a>Individuazione di pacchetti obsoleti
Dalla finestra della soluzione è possibile visualizzare la versione di un pacchetto attualmente installata e fare clic con il pulsante destro del mouse sul pacchetto da aggiornare.

![Menu pacchetti con le opzioni per aggiornare, rimuovere, aggiornare](media/nuget-walkthrough-PackageMenu.png)

Verrà visualizzata anche una notifica accanto al nome del pacchetto quando sarà disponibile una nuova versione di un pacchetto, quindi è possibile decidere se è necessario aggiornarla.

![Notifica visualizzata quando è disponibile una nuova versione del pacchetto](media/nuget-walkthrough-package-update-available.png)

Nel menu visualizzato sono disponibili due opzioni:

* **Aggiorna** - Controlla il server di origine e scarica una versione più recente, se disponibile.
* **Rimuovi** - Rimuove il pacchetto dal progetto e gli assembly correlati dai riferimenti del progetto.

## <a name="manage-packages-for-the-solution"></a>Gestisci i pacchetti per la soluzione

La gestione dei pacchetti per una soluzione è un metodo pratico per utilizzare più progetti contemporaneamente.

1. Fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Gestisci pacchetti NuGet...** :

    ![Gestisci pacchetti NuGet per la soluzione](media/nuget-walkthrough-manage-packages-solution.png)

1. Quando si gestiscono i pacchetti per la soluzione, l'interfaccia utente consente di selezionare i progetti interessati dalle operazioni:

    ![Selettore di progetto durante la gestione dei pacchetti per la soluzione](media/nuget-walkthrough-add-to-projects.png)

### <a name="consolidate-tab"></a>Scheda Consolida

Quando si lavora in una soluzione con più progetti, è consigliabile assicurarsi che ovunque si usi lo stesso pacchetto NuGet in ogni progetto, si sta anche usando lo stesso numero di versione di tale pacchetto. Visual Studio per Mac semplifica questa operazione fornendo una scheda **consolidate** nell'interfaccia utente di gestione pacchetti quando si sceglie di gestire i pacchetti per una soluzione. Con questa scheda è possibile vedere facilmente dove i pacchetti con numeri di versione distinti vengono usati da progetti diversi nella soluzione:

![Scheda Consolida dell'interfaccia utente di Gestione pacchetti](media/nuget-walkthrough-consolidate-tab.png)

In questo esempio, il progetto NuGetDemo USA Microsoft. EntityFrameworkCore 2,20, mentre NuGetDemo. Shared USA Microsoft. EntityFrameworkCore 2.2.6. Per consolidare le versioni dei pacchetti, seguire questa procedura:

- Selezionare i progetti da aggiornare nell'elenco dei progetti.
- Selezionare la versione da usare in tutti i progetti nell'elenco **nuova versione** , ad esempio Microsoft. EntityFrameworkCore 3.0.0.
- Selezionare il pulsante **consolida pacchetto** .

Gestione pacchetti installa la versione del pacchetto selezionata in tutti i progetti selezionati e in seguito il pacchetto non compare più nella scheda **Consolida**.

## <a name="adding-package-sources"></a>Aggiunta di origini dei pacchetti

I pacchetti disponibili per l'installazione vengono inizialmente recuperati da nuget.org. Tuttavia, è possibile aggiungere altri percorsi di pacchetti a Visual Studio per Mac. Ciò può essere utile per testare i pacchetti NuGet in fase di sviluppo oppure per usare un server NuGet privato all'interno dell'azienda o dell'organizzazione.

In Visual Studio per Mac passare a **Visual Studio > Preferenze > NuGet > Origini** per visualizzare e modificare l'elenco di origini dei pacchetti. Si noti che le origini possono essere un server remoto (specificato da un URL) o una directory locale.

![Origini dei pacchetti](media/nuget-walkthrough-PackageSource.png)

Fare clic su **Aggiungi** per configurare una nuova origine. Immettere un nome descrittivo e l'URL (o il percorso file) dell'origine del pacchetto. Se l'origine è un server Web sicuro, immettere nome utente e password, in caso contrario lasciare vuote queste voci:

![Finestra di dialogo Aggiungi origine pacchetto con una richiesta per nome, URL percorso, nome utente e password.](media/nuget-walkthrough-PackageSource2.png)

Quando si cercano i pacchetti è quindi possibile selezionare origini diverse:

![Finestra di dialogo Aggiungi origine pacchetto che mostra un elenco a discesa con un elenco di origini di pacchetti.](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Controllo della versione

La documentazione di NuGet illustra come [usare NuGet senza eseguire il commit di pacchetti nel controllo del codice sorgente](/nuget/consume-packages/packages-and-source-control). Se si preferisce non archiviare i file binari e le informazioni non usate nel controllo del codice sorgente, è possibile configurare Visual Studio per Mac per il ripristino automatico dei pacchetti dal server. Ciò significa che quando uno sviluppatore recupera il progetto dal controllo del codice sorgente per la prima volta, Visual Studio per Mac scarica e installa automaticamente i pacchetti richiesti.

![Ripristino automatico dei pacchetti](media/nuget-walkthrough-AutoRestore.png)

Vedere la documentazione relativa al controllo del codice sorgente specifico per informazioni dettagliate su come escludere la directory `packages` dal controllo.

## <a name="related-video"></a>Video correlato

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Using-NuGet/player]

## <a name="see-also"></a>Vedere anche

* [Installare e usare un pacchetto in Visual Studio (in Windows)](/nuget/quickstart/install-and-use-a-package-in-visual-studio)
