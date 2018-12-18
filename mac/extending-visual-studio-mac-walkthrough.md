---
title: Procedura dettagliata per l'estensione di Visual Studio per Mac | Microsoft Docs
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: 30571e0f83d2b54fdb5346030cc7cc4430901797
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Procedura dettagliata per l'estensione di Visual Studio per Mac

Questo argomento descrive la compilazione di un [semplice pacchetto di estensione](https://github.com/mjh4/AddIns/tree/master/DateInserter). Il pacchetto di estensione crea un nuovo comando nel menu Modifica di Visual Studio per Mac che permette all'utente di inserire la data e l'ora corrente in un documento di testo aperto.

Questo esempio usa Addin Maker. Addin Maker crea un nuovo modello di progetto e lo completa con i file necessari per il pacchetto di estensione personalizzato.

1.   Per iniziare, avviare Visual Studio per Mac, se non è già aperto:

  ![Screenshot di Visual Studio per Mac](media/extending-visual-studio-mac-addin3.png)

2.   Installare il _pacchetto di estensione Addin Maker_ usando Gestione estensioni. Dal menu di Visual Studio scegliere **Estensioni**:

  ![Scheda di gestione dei componenti aggiuntivi](media/extending-visual-studio-mac-addin4.png)

3.   Passare alla scheda Raccolta e digitare `Addin Maker` sulla barra di ricerca in alto a destra. Selezionare Addin Maker nella categoria relativa allo sviluppo di componenti aggiuntivi e fare clic su <kbd>Installa</kbd>. Se non viene visualizzato, fare clic su Aggiorna ed eseguire una nuova ricerca:

  ![Gestione estensioni](media/extending-visual-studio-mac-addin5.png)

4.   Dopo aver installato Addin Maker, è possibile iniziare a compilare un pacchetto di estensione. Per iniziare, creare una nuova soluzione.

5.  Nella **finestra di dialogo Nuova soluzione** scegliere il modello in **Altro > Varie > Generale > Xamarin Studio Addin > C#** e nella schermata successiva assegnare un nome alla nuova soluzione `DateInserter`:

  ![Creazione di una nuova soluzione](media/extending-visual-studio-mac-addin7New.png)

6.   Visual Studio per Mac popolerà una nuova soluzione:

  ![Soluzione popolata](media/extending-visual-studio-mac-addin8.png)

7.   Rimuovere il codice del modello da `Manifest.addin.xml` e sostituirlo con il seguente:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
        <ExtensionModel>
            <Extension path = "/MonoDevelop/Ide/Commands/Edit">
                <Command id = "DateInserter.DateInserterCommands.InsertDate"
                    _label = "Insert Date"
                    defaultHandler = "DateInserter.InsertDateHandler" />
            </Extension>

            <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
                <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
            </Extension>
        </ExtensionModel>
    ```

8.   È ora necessario configurare i file che dovranno gestire l'inserimento della data e dell'ora nell'editor di testo. Fare clic con il pulsante destro del mouse sul nodo del progetto e aggiungere un nuovo file. Selezionare **Generale > Classe vuota** e assegnare al nuovo file il nome *InsertDateHandler*:

  ![InsertDateHandler](media/extending-visual-studio-mac-addin9.png)

9.   Rimuovere il codice del modello da `InsertDateHandler.cs` e sostituirlo con il seguente:

    ```cs
    using MonoDevelop.Components.Commands;
    using MonoDevelop.Ide;
    using MonoDevelop.Ide.Gui;
    using System;

    namespace DateInserter
    {
        class InsertDateHandler : CommandHandler
        {
            protected override void Run()
            {

            }

            protected override void Update(CommandInfo info)
            {

            }
        }
    }
    ```

  Questi due metodi segnaposto verranno espansi in un secondo momento.

10.   Fare clic con il pulsante destro del mouse sul progetto **DateInserter** e selezionare **Aggiungi > Nuovo file**. Selezionare **Generale > Enumerazione vuota** e quindi assegnare al nuovo file il nome *DateInserterCommands*:

  ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11.   Aggiungere il comando `InsertDate` come nuova enumerazione nel file `DateInserterCommands.cs`:

    ``` cs
    using System;

    namespace DateInserter
    {
        public enum DateInserterCommands
        {
            InsertDate,
        }
    }
    ```

12.   A questo punto, dovrebbe essere disponibile un pacchetto di estensione funzionante. È possibile testarlo salvando il lavoro ed eseguendo l'applicazione. L'IDE avvierà una nuova istanza di Visual Studio per Mac con il nuovo pacchetto di estensione installato. Se si passa al **menu Modifica**, si noterà che Visual Studio per Mac include una nuova opzione chiamata **Inserisci data**, mostrata nello screenshot seguente:

  ![Comando Inserisci data](media/extending-visual-studio-mac-addin11.png)

  Si noti che la selezione di Inserisci data nel menu non produce alcun effetto, in quanto l'implementazione corrente include solo metodi segnaposto.

13.   Il framework per il pacchetto di estensione è disponibile ed è ora possibile scrivere il codice che attiva l'inserimento della data. Prima di tutto, assicurarsi che il **comando Inserisci data** sia abilitato solo quando l'utente ha un file di testo aperto sostituendo il metodo `Update` in `InsertDateHandler.cs` con il codice seguente:

    ```cs
    protected override void Update(CommandInfo info)
    {
        info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14.   Aggiornare il metodo `Run` del comando per l'inserimento della data e dell'ora con il codice seguente:

    ``` cs
    protected override void Run () {
        var editor = IdeApp.Workbench.ActiveDocument.Editor;
        var date = DateTime.Now.ToString ();
        editor.InsertAtCaret (date);

    }
    ```

15.   Infine, eseguire il pacchetto di estensione per testarlo. Nella nuova istanza di Visual Studio per Mac selezionare **Modifica > Inserisci data**. La data e l'ora corrente vengono aggiunte nel punto di inserimento, come mostrato nello screenshot seguente:

  ![Screenshot dell'inserimento della data](media/extending-visual-studio-mac-addin12.png)
