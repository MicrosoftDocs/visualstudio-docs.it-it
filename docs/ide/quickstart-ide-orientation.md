---
title: Presentazione dell'IDE di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2017
ms.technology:
- vs-ide-general
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c9dfa3ba8f4e87b842d2ba8677f76aabd4931d1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="quickstart-first-look-at-the-visual-studio-ide"></a>Guida introduttiva: Presentazione dell'IDE di Visual Studio

In questa introduzione della durata di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio verranno presentati alcuni menu, finestre e altre funzionalità dell'interfaccia utente.

Se non è ancora stato installato Visual Studio, accedere alla pagina [Download di Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) per installarlo gratuitamente.

## <a name="start-page"></a>Pagina iniziale

Il primo elemento visualizzato dopo l'avvio di Visual Studio è molto probabilmente la pagina iniziale. La pagina iniziale è progettata come "centro di smistamento" per facilitare l'accesso ai comandi e ai file di progetto necessari più velocemente. Nella sezione **Recenti** sono visualizzati i progetti e le cartelle usati di recente. In **Nuovo progetto** è possibile fare clic su un collegamento per visualizzare la finestra di dialogo Nuovo progetto o in **Apri** è possibile aprire un progetto o una cartella di codice esistente. Sulla destra è visualizzato un feed di notizie aggiornate per sviluppatori.

![Pagina iniziale di Visual Studio](media/quickstart-IDE-start-page.png)

Se si chiude la pagina iniziale e si vuole visualizzarla di nuovo, è possibile riaprirla dal menu **File**.

![File (menu)](media/quickstart-IDE-file-menu-large.png)

Per continuare a esplorare l'IDE, di seguito verrà creato un nuovo progetto.

1. Nella **Pagina iniziale**, nella casella di ricerca sotto **Nuovo progetto**, immettere `console` per filtrare l'elenco dei tipi di progetto. Scegliere un'**App console (.NET Framework)** C# o VB. In alternativa, gli sviluppatori che usano C++, Javascript o altri linguaggi possono creare liberamente un progetto in uno di questi linguaggi. L'interfaccia utente è simile per tutti i linguaggi.

1. Nella finestra di dialogo **Nuovo progetto** accettare il nome di progetto predefinito e scegliere **OK**.

   Il progetto viene creato e viene aperto un file denominato **Program.cs** o **Program. vb** nella finestra **Editor**. L'editor mostra il contenuto dei file ed è la posizione in cui si esegue la maggior parte delle operazioni di scrittura del codice in Visual Studio.

## <a name="solution-explorer"></a>Esplora soluzioni

Esplora soluzioni mostra una rappresentazione grafica della gerarchia di file e cartelle nella cartella del progetto, della soluzione o del codice. È possibile esplorare la gerarchia e passare a un file in Esplora soluzioni.

![Esplora soluzioni](media/quickstart-IDE-solution-explorer.png)

## <a name="menus"></a>Menu

La barra dei menu nella parte superiore dell'IDE raggruppa i comandi in categorie. Ad esempio, il menu **Progetto** contiene i comandi correlati al progetto in uso. Dal menu **Strumenti** è possibile personalizzare l'IDE selezionando **Opzioni** oppure aggiungere funzionalità all'installazione selezionando **Ottieni strumenti e funzionalità**.

![Barra dei menu](media/quickstart-IDE-menu-bar.png)

Aprire la finestra Elenco errori scegliendo **Elenco errori** dal menu **Visualizza**.

## <a name="error-list"></a>Elenco errori

Nell'Elenco errori sono visualizzati gli errori, gli avvisi e i messaggi riguardanti lo stato corrente del codice. Se il file o il progetto in uso contiene errori, ad esempio un errore di sintassi, verranno elencati in questa posizione.

![Elenco errori](media/quickstart-IDE-error-list.png)

## <a name="output-window"></a>Output (finestra)

La finestra di output mostra i messaggi di output della compilazione e del controllo del codice sorgente.

Verrà ora compilato il progetto per esaminare alcune registrazioni di output. Scegliere **Compila soluzione** dal menu **Compila**. La finestra di output ottiene automaticamente lo stato attivo e visualizza un messaggio di completamento della compilazione.

![Finestra di output](media/quickstart-IDE-output.png)

## <a name="quick-launch"></a>Avvio veloce

La casella Avvio veloce è un modo rapido e semplice per eseguire pressoché qualsiasi operazione nell'IDE. È possibile immettere testo correlato all'operazione che si vuole eseguire e verrà visualizzato un elenco di opzioni pertinenti. Ad esempio, si supponga di voler aumentare il livello di dettaglio dell'output di compilazione per visualizzare informazioni di registrazione aggiuntive sulle operazioni eseguite esattamente dalla compilazione:

1. Immettere `verbosity` nella casella **Avvio veloce** e quindi scegliere **Progetti e soluzioni -> Compila ed Esegui** nella categoria **Opzioni**.

   ![Casella Avvio veloce](media/quickstart-IDE-quick-launch.png)

   Si apre la pagina delle opzioni **Compila ed esegui** della finestra di dialogo **Opzioni**.

1. In **Livello di dettaglio output in compilazione progetto MSBuild** scegliere **Normale** e quindi fare clic su **OK**.

1. A questo punto, compilare di nuovo il progetto facendo clic con il pulsante destro del mouse sul progetto **ConsoleApp1** in **Esplora soluzioni** e scegliendo **Ricompila** dal menu di scelta rapida.

   Questa volta la finestra di output mostra una registrazione più dettagliata del processo di compilazione, inclusi i file copiati e la posizione in cui sono stati copiati.

## <a name="send-feedback-menu"></a>Menu Invia commenti e suggerimenti

Se si verificano problemi durante l'uso di Visual Studio o se si hanno suggerimenti su come migliorare il prodotto, è possibile usare il menu **Invia commenti e suggerimenti** nella parte superiore dell'IDE, accanto alla casella Avvio veloce.

![Menu Invia commenti e suggerimenti](media/quickstart-IDE-send-feedback.png)

## <a name="next-steps"></a>Passaggi successivi

Sono state presentate solo alcune delle funzionalità dell'IDE di Visual Studio per iniziare ad acquisire familiarità con l'interfaccia utente. Per esplorare ulteriormente:

- Consultare la sezione Elementi generali dell'interfaccia utente della documentazione di Visual Studio, che illustra in modo più approfondito finestre come l'[Elenco errori](../ide/reference/error-list-window.md), la [finestra di output](../ide/reference/output-window.md), la [finestra Proprietà](../ide/reference/properties-window.md) e la [finestra di dialogo Opzioni](../ide/reference/options-dialog-box-visual-studio.md)

- Per esplorare in maggior dettaglio l'IDE ed esercitarsi con il debug, vedere [Panoramica dell'IDE di Visual Studio](../ide/visual-studio-ide.md).

## <a name="see-also"></a>Vedere anche

- [Guida introduttiva: Personalizzazione dell'IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Guida introduttiva: Scrittura di codice nell'editor](../ide/quickstart-editor.md)
- [Guida introduttiva: Progetti e soluzioni](../ide/quickstart-projects-solutions.md)
