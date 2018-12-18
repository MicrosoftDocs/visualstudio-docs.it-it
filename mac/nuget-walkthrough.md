---
title: Procedura dettagliata - Inserimento di un pacchetto NuGet nel progetto
description: Questo documento descrive come includere un pacchetto NuGet in un progetto Xamarin. Illustra in modo dettagliato come trovare e scaricare un pacchetto e offre un'introduzione alle funzionalità di integrazione dell'IDE.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 5C800815-0B13-4B27-B017-95FCEF1A0EA2
ms.openlocfilehash: 05762df8b06a69647c6c7a628db54ac499248374
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="including-a-nuget-package-in-your-project"></a>Inserimento di un pacchetto NuGet nel progetto

NuGet è il più diffuso strumento di gestione pacchetti per lo sviluppo .NET ed è integrato in Visual Studio per Mac e Visual Studio in Windows. È possibile cercare e aggiungere pacchetti nei progetti Xamarin.iOS e Xamarin.Android usando entrambi gli IDE.

Questo documento esamina come includere un pacchetto NuGet in un progetto e illustra la catena di strumenti che rende facile il processo.

## <a name="nuget-in-visual-studio-for-mac"></a>NuGet in Visual Studio per Mac

Per illustrare le funzionalità dei pacchetti NuGet, verrà prima di tutto illustrata la procedura di creazione di una nuova applicazione e aggiunta di un pacchetto. Verranno quindi descritte le funzionalità dell'IDE utili per la gestione dei pacchetti.

## <a name="create-a-new-project"></a>Creare un nuovo progetto

Creare prima di tutto un progetto denominato `HelloNuget`, come illustrato di seguito. Questo esempio mostra il modello di app visualizzazione singola iOS, ma è possibile scegliere qualsiasi tipo di progetto supportato:

![Creare un nuovo progetto iOS](media/nuget-walkthrough-NewProject.png)

<a name="Adding_a_Package" class="injected"></a>

## <a name="adding-a-package"></a>Aggiunta di un pacchetto

Con il progetto aperto in Visual Studio per Mac, fare clic con il pulsante destro del mouse sulla cartella **Pacchetti** nel **riquadro della soluzione** e scegliere **Aggiungi pacchetti**:

![Azione di contesto di aggiunta di un nuovo pacchetto NuGet](media/nuget-walkthrough-PackagesMenu.png)

Verrà visualizzata la finestra _Aggiungi pacchetti_. Verificare che l'elenco a discesa Origine sia impostato su `nuget.org`:

![Elenco a discesa Origine](media/nuget-walkthrough-Source.png)

Quando la finestra viene visualizzata, carica un elenco di pacchetti dall'origine dei pacchetti predefinita: nuget.org. I risultati iniziali sono simili ai seguenti:

![Elenco di pacchetti NuGet](media/nuget-walkthrough-AddPackages1.png)

Usare la casella di ricerca nell'angolo superiore destro per trovare un pacchetto specifico, ad esempio `azure`. Dopo aver trovato un pacchetto da usare, selezionarlo e fare clic sul pulsante **Aggiungi pacchetto** per avviare l'installazione.


[Aggiungere un pacchetto NuGet Azure](media/nuget-walkthrough-AddPackages2.png)

Dopo essere stato scaricato, il pacchetto verrà aggiunto al progetto. La soluzione verrà modificata come illustrato di seguito:

*   Il nodo **Riferimenti** conterrà un elenco di tutti gli assembly che fanno parte di un pacchetto NuGet.
*   Il nodo **Pacchetti** mostra ogni pacchetto NuGet scaricato. È possibile aggiornare o rimuovere un pacchetto dall'elenco.
*   Al progetto verrà aggiunto un file **packages.config**. Questo file XML viene usato dall'IDE per tenere traccia delle versioni del pacchetto a cui si fa riferimento nel progetto. Questo file non deve essere modificato manualmente, ma è consigliabile includerlo nel controllo della versione. Si noti che è possibile usare un file project.json al posto di un file packages.config. Il file project.json è un nuovo formato di file di pacchetto introdotto con NuGet 3, che supporta il ripristino transitivo. Per altre informazioni dettagliate su project.json, vedere la [documentazione di NuGet](http://docs.microsoft.com/NuGet/Schema/Project-Json). Per poter usare il file project.json in Visual Studio per Mac è necessario aggiungerlo manualmente e quindi chiudere e riaprire il progetto.

## <a name="using-nuget-packages"></a>Uso di pacchetti NuGet

Dopo che il pacchetto NuGet è stato aggiunto e i riferimenti del progetto sono stati aggiornati, è possibile programmare usando le API come si farebbe con qualsiasi riferimento del progetto.

Assicurarsi di aggiungere le direttive `using` necessarie all'inizio del file:


    using Newtownsoft.json;

La maggior parte dei pacchetti NuGet fornisce informazioni aggiuntive, ad esempio un file leggimi o un collegamento della pagina del progetto all'origine NuGet. In genere, è possibile trovare un collegamento nella descrizione del pacchetto nella pagina Aggiungi pacchetti:

[Visualizzare il collegamento alla pagina del progetto](media/nuget-walkthrough-project-page.png)

<a name="Package_Updates" class="injected"></a>

## <a name="package-updates"></a>Aggiornamenti dei pacchetti

Gli aggiornamenti dei pacchetti possono essere eseguiti tutti in una sola volta, facendo clic con il pulsante destro del mouse sul nodo **Pacchetti**, oppure singolarmente in ogni componente.

Fare clic con il pulsante destro del mouse su **Pacchetti** per accedere al menu di scelta rapida:

![Menu Pacchetti](media/nuget-walkthrough-PackagesMenu.png)

*   **Aggiungi pacchetti** - Apre la finestra per l'aggiunta di altri pacchetti al progetto.
*   **Aggiorna** - Controlla il server di origine per ogni pacchetto e scarica le eventuali versioni più recenti.
*   **Ripristina** - Scarica tutti i pacchetti mancanti (senza aggiornare i pacchetti esistenti alle versioni più recenti).

Le opzioni Aggiorna e Ripristina sono disponibili anche a livello di soluzione e influiscono su tutti i progetti nella soluzione. 

È anche possibile fare clic con il pulsante destro del mouse sui singoli pacchetti per accedere a un menu di scelta rapida:

![Menu Pacchetti](media/nuget-walkthrough-PackageMenu.png)

*   **Numero di versione** - La voce di menu Numero di versione è disabilitata e viene fornita esclusivamente a scopo informativo.
*   **Aggiorna** - Controlla il server di origine e scarica una versione più recente, se disponibile.
*   **Rimuovi** - Rimuove il pacchetto dal progetto e gli assembly correlati dai riferimenti del progetto.


## <a name="adding-package-sources"></a>Aggiunta di origini dei pacchetti

I pacchetti disponibili per l'installazione vengono recuperati inizialmente da nuget.org. È tuttavia possibile aggiungere in Visual Studio per Mac altri percorsi dei pacchetti. Ciò può essere utile per testare i pacchetti NuGet in fase di sviluppo oppure per usare un server NuGet privato all'interno dell'azienda o dell'organizzazione.

In Visual Studio per Mac passare a **Visual Studio > Preferenze > NuGet > Origini** per visualizzare e modificare l'elenco di origini dei pacchetti. Si noti che le origini possono essere un server remoto (specificato da un URL) o una directory locale. 

![Origini dei pacchetti](media/nuget-walkthrough-PackageSource.png)

Fare clic su **Aggiungi** per configurare una nuova origine. Immettere un nome descrittivo e l'URL (o il percorso file) dell'origine del pacchetto. Se l'origine è un server Web sicuro, immettere nome utente e password, in caso contrario lasciare vuote queste voci:

![Aggiungere origini dei pacchetti](media/nuget-walkthrough-PackageSource2.png)

Quando si cercano i pacchetti è quindi possibile selezionare origini diverse:

![Aggiungere origini dei pacchetti](media/nuget-walkthrough-PackageSource3.png)

## <a name="version-control"></a>Controllo della versione

La documentazione di NuGet illustra come [usare NuGet senza eseguire il commit di pacchetti nel controllo del codice sorgente](https://docs.microsoft.com/nuget/consume-packages/packages-and-source-control). Se si preferisce non archiviare i file binari e le informazioni non usate nel controllo del codice sorgente, è possibile configurare Visual Studio per Mac per il ripristino automatico dei pacchetti dal server. Ciò significa che quando uno sviluppatore recupera il progetto dal controllo del codice sorgente per la prima volta, Visual Studio per Mac scarica e installa automaticamente i pacchetti richiesti.

![Ripristino automatico dei pacchetti](media/nuget-walkthrough-AutoRestore.png)

Vedere la documentazione relativa al controllo del codice sorgente specifico per informazioni dettagliate su come escludere la directory `packages` dal controllo.

