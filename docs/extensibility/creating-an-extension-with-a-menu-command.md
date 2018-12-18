---
title: Creazione di un'estensione con un comando di Menu | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00c80692929ac19b55f68b8aa20306f39ddceae6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-a-menu-command"></a>Creazione di un'estensione con un comando di Menu
Questa procedura dettagliata viene illustrato come creare un'estensione con un comando di menu che consente di avviare Blocco note.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-menu-command"></a>Creazione di un comando di Menu  
  
1.  Creare un progetto VSIX denominato **FirstMenuCommand**. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **FirstCommand**. Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **FirstCommand.cs**.  
  
3.  Compilare il progetto e avviare il debug.  
  
     Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4.  Nell'istanza sperimentale, aprire il **strumenti / estensioni e aggiornamenti** finestra. Verrà visualizzato il **FirstMenuCommand** estensione qui. (Se si apre **estensioni e aggiornamenti** nell'istanza di lavoro di Visual Studio, non verrà visualizzato **FirstMenuCommand**).  
  
     Passare quindi al **strumenti** menu nell'istanza sperimentale. Dovrebbe essere **richiamare FirstCommand** comando. A questo punto, solo apparirà una finestra di messaggio che afferma "FirstCommandPackage all'interno di FirstMenuCommand.FirstCommand.MenuItemCallback()". Vedremo come effettivamente avviare Blocco note di questo comando nella sezione successiva.  
  
## <a name="changing-the-menu-command-handler"></a>Modifica il gestore del comando di Menu  
 Ora consente di aggiornare il gestore del comando per avviare il blocco note.  
  
1.  Arrestare il debug e tornare all'istanza di lavoro di Visual Studio. Aprire il file FirstCommand.cs e aggiungere la seguente istruzione using:  
  
    ```csharp  
    using System.Diagnostics;  
    ```  
  
2.  Trovare il costruttore FirstCommand privato. Si tratta in cui il comando viene collegato al servizio di comando e viene specificato il gestore del comando. Modificare il nome del gestore comando per StartNotepad, come indicato di seguito:  
  
    ```csharp  
    private FirstCommand(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
         OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(CommandSet, CommandId);  
            // Change to StartNotepad handler.  
            MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
3.  Rimuovere il metodo MenuItemCallback e aggiungere un metodo StartNotepad che verrà avviato solo il blocco note:  
  
    ```csharp  
    private void StartNotepad(object sender, EventArgs e)  
    {  
        Process proc = new Process();  
        proc.StartInfo.FileName = "notepad.exe";  
        proc.Start();  
    }  
    ```  
  
4.  Provare ora a eseguire l'operazione. Quando si avvia il debug del progetto e fare clic su **strumenti / richiamare FirstCommand**, si dovrebbe essere visualizzata un'istanza del blocco note.  
  
     È possibile utilizzare un'istanza di <xref:System.Diagnostics.Process> classe per l'esecuzione di qualsiasi file eseguibile, non solo il blocco note. Provare con calc.exe, ad esempio.  
  
## <a name="cleaning-up-the-experimental-environment"></a>Pulizia dell'ambiente sperimentale  
 Se si siano sviluppando più estensioni, o semplicemente esplorare risultati con diverse versioni del codice di estensione, l'ambiente sperimentale potrebbe smettere di funzionare nel modo desiderato. In questo caso, è necessario eseguire lo script di reimpostazione. Viene chiamato **Reimposta l'istanza sperimentale di Visual Studio 2015**, e fornito come parte di Visual Studio SDK. Questo script rimuove tutti i riferimenti per le estensioni nell'ambiente sperimentale di conseguenza, iniziare da zero.  
  
 È possibile ottenere questo script in uno dei due modi:  
  
1.  Dal desktop, trovare **Reimposta l'istanza sperimentale di Visual Studio 2015**.  
  
2.  Dalla riga di comando, eseguire le operazioni seguenti:  
  
    ```  
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp && PAUSE  
  
    ```  
  
## <a name="deploying-your-extension"></a>L'estensione di distribuzione  
 Dopo aver creato l'estensione degli strumenti in esecuzione nel modo desiderato, è necessario preoccuparsi di condividerla con i colleghi e amici. Che è facile, purché dispongano di Visual Studio 2015 installati. È necessario effettuare è inviare loro il file con estensione VSIX è stato compilato. (Assicurarsi di compilare in modalità di rilascio.)  
  
 È possibile trovare il file. VSIX per questa estensione nella directory bin FirstMenuCommand. In particolare, se che è stata compilata la configurazione di rilascio, sarà:  
  
 **\<directory del codice > \FirstMenuCommand\FirstMenuCommand\bin\Release\ FirstMenuCommand.vsix**  
  
 Per installare l'estensione, amico è necessario chiudere tutte le istanze aperte di Visual Studio, quindi fare doppio clic sul file con estensione VSIX, che consente di visualizzare il **VSIX Installer**. I file vengono copiati il **%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions** directory.  
  
 Quando amica visualizzata nuovamente Visual Studio, sarà disponibile l'estensione FirstMenuCommand **strumenti / estensioni e aggiornamenti**. È possibile passare a **estensioni e aggiornamenti** per disinstallare o disabilitare l'estensione, troppo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Questa procedura dettagliata è stato illustrato solo una piccola parte di operazioni possibili con un'estensione di Visual Studio. Ecco un breve elenco di altre operazioni (relativamente semplice) con le estensioni di Visual Studio:  
  
1.  È possibile eseguire molte altre operazioni con un comando di menu semplice:  
  
    1.  Aggiungere la propria icona: [aggiunta di icone ai comandi di Menu](../extensibility/adding-icons-to-menu-commands.md)  
  
    2.  Modificare il testo del comando di menu: [modifica del testo di un comando di Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
  
    3.  Aggiungere un collegamento al menu a un comando: [associazione tasti di scelta rapida alle voci di Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
  
2.  Aggiungere diversi tipi di comandi, menu e barre degli strumenti: [estensione menu e comandi](../extensibility/extending-menus-and-commands.md)  
  
3.  Aggiungere finestre degli strumenti ed estendere le finestre degli strumenti di Visual Studio predefinite: [estensione e le finestre degli strumenti personalizzazione](../extensibility/extending-and-customizing-tool-windows.md)  
  
4.  Aggiungere i suggerimenti di codice, IntelliSense e altre funzionalità esistenti di editor di codice: [estensione dell'Editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)  
  
5.  Aggiungere pagine delle proprietà e le opzioni e impostazioni utente per l'estensione: [estensione di proprietà e la finestra delle proprietà](../extensibility/extending-properties-and-the-property-window.md) e [opzioni e impostazioni utente di estensione](../extensibility/extending-user-settings-and-options.md)  
  
 Altri tipi di estensioni richiedono un po' più operazioni, ad esempio la creazione di un nuovo tipo di progetto ([estensione progetti](../extensibility/extending-projects.md)), creare un nuovo tipo di editor ([creare editor personalizzati e finestre di progettazione](../extensibility/creating-custom-editors-and-designers.md)), o implementazione dell'estensione in una shell isolata: [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)