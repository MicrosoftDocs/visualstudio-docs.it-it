---
title: "Estensione di proprietà, elenco attività, Output e opzioni Windows | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: "37"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 631c336d0350fdf8a43d747eb6bda7b01e9d1eba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Estensione di proprietà, elenco attività, Output e opzioni Windows
È possibile accedere a qualsiasi finestra degli strumenti in Visual Studio. Questa procedura dettagliata viene illustrato come integrare informazioni sulla finestra di strumento in un nuovo **opzioni** pagina e una nuova impostazione nel **proprietà** pagina, nonché su come scrivere il **elenco attività** e **Output** windows.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumenti  
  
1.  Creare un progetto denominato **TodoList** utilizzando il modello di progetto VSIX e aggiungere un modello di elemento della finestra dello strumento personalizzato denominato **TodoWindow**.  
  
    > [!NOTE]
    >  Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Impostare la finestra degli strumenti  
 Aggiungere una casella di testo in cui digitare un nuovo elemento di attività, un pulsante per aggiungere il nuovo elemento all'elenco e una casella di riepilogo per visualizzare gli elementi nell'elenco.  
  
1.  In TodoWindow.xaml, eliminare i controlli pulsante e casella di testo StackPanel dalla UserControl.  
  
    > [!NOTE]
    >  Questa operazione non elimina il **button1_Click** gestore eventi, che verrà riutilizzata in un passaggio successivo.  
  
2.  Dal **tutti i controlli WPF** sezione il **della casella degli strumenti**, trascinare un **area di disegno** controllo alla griglia.  
  
3.  Trascinare un **TextBox**, **pulsante**e un **ListBox** all'area di disegno. Disporre gli elementi in modo che la casella di testo e il pulsante allo stesso livello, la casella di riepilogo riempie il resto della finestra di sotto di essi, come illustrato nell'immagine seguente.  
  
     ![Finestra degli strumenti completato](../extensibility/media/t5-toolwindow.png "T5 ToolWindow")  
  
4.  Nel riquadro di XAML, trovare il pulsante e impostarne la proprietà di contenuto su **Aggiungi**. Riconnettere il gestore dell'evento pulsante al controllo Button aggiungendo un `Click="button1_Click"` attributo. Il blocco dell'area di disegno dovrebbe essere simile al seguente:  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Personalizzare il costruttore  
  
1.  Nel file TodoWindowControl.xaml.cs, aggiungere la seguente istruzione using:  
  
    ```csharp  
    using System;  
    ```  
  
2.  Aggiungere un riferimento di TodoWindow pubblico in modo che il costruttore TodoWindowControl accettano un parametro TodoWindow. Il codice dovrebbe essere simile al seguente:  
  
    ```csharp  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  In TodoWindow.cs, modificare il costruttore TodoWindowControl per includere il parametro TodoWindow. Il codice dovrebbe essere simile al seguente:  
  
    ```csharp  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>Creare una pagina di opzioni  
 È possibile fornire una pagina di **opzioni** nella finestra di dialogo in modo che gli utenti possono modificare le impostazioni per la finestra degli strumenti. La creazione di una pagina di opzioni richiede sia una classe che descrive le opzioni e una voce nel file TodoListPackage.cs o TodoListPackage.vb.  
  
1.  Aggiungere una classe denominata `ToolsOptions.cs`. Assicurarsi che la classe Options erediti dal <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  Aggiungere la seguente istruzione using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  La pagina di opzioni in questa procedura dettagliata fornisce solo un'opzione denominata DaysAhead. Aggiungere un campo privato denominato **daysAhead** e una proprietà denominata **DaysAhead** alla classe Options:  
  
    ```csharp  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 A questo punto è necessario compilare il progetto conoscenza di questa pagina di opzioni.  
  
#### <a name="make-the-options-page-available-to-users"></a>Rendere disponibile la pagina di opzioni per gli utenti  
  
1.  In TodoWindowPackage.cs, aggiungere un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla classe TodoWindowPackage:  
  
    ```csharp  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  Il primo parametro al costruttore ProvideOptionPage è il tipo di classe Options, creato in precedenza. Il secondo parametro, l'attività"", è il nome della categoria nella finestra di **opzioni** la finestra di dialogo. Il terzo parametro, "Generale", è il nome della sottocategoria del **opzioni** la finestra di dialogo in cui sarà disponibile la pagina di opzioni. I due parametri successivi sono ID di risorsa per le stringhe; il primo è il nome della categoria e il secondo è il nome della sottocategoria. L'ultimo parametro determina se questa pagina è possibile accedere utilizzando l'automazione.  
  
     Quando un utente apre la pagina delle opzioni, il risultato sarà simile nell'immagine seguente.  
  
     ![Pagina Opzioni](../extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Si noti la categoria **ToDo** e la sottocategoria **generale**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Rendere disponibili i dati alla finestra proprietà  
 È possibile rendere disponibile per eseguire l'elenco di informazioni tramite la creazione di una classe denominata TodoItem che archivia informazioni sui singoli elementi nell'elenco attività.  
  
1.  Aggiungere una classe denominata `TodoItem.cs`.  
  
     Quando la finestra degli strumenti è disponibile per gli utenti, gli elementi nella casella di riepilogo saranno rappresentati da TodoItems. Quando l'utente seleziona una di queste voci nella casella di riepilogo, il **proprietà** finestra vengono visualizzate informazioni sull'elemento.  
  
     Per rendere disponibili in dati di **proprietà** finestra, di trasformare i dati in proprietà pubbliche che dispongono di due attributi speciali, `Description` e `Category`. `Description`è il testo visualizzato in fondo il **proprietà** finestra. `Category`Determina dove dovrebbe essere visualizzata quando la proprietà di **proprietà** verrà visualizzata la finestra nel **categoria** visualizzazione. Nell'immagine seguente, il **proprietà** finestra è in **categoria** visualizzazione, il **nome** proprietà nel **ToDo Fields** categoria selezionata e la descrizione di **nome** proprietà viene visualizzata nella parte inferiore della finestra.  
  
     ![Finestra proprietà](../extensibility/media/t5properties.png "T5Properties")  
  
2.  Aggiungere le seguenti istruzioni using il file todoitem. cs.  
  
    ```csharp  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Aggiungere il `public` modificatore di accesso alla dichiarazione di classe.  
  
    ```csharp  
    public class TodoItem  
    {  
    }  
    ```  
  
     Aggiungere le due proprietà, nome e DueDate. Faremo il UpdateList() e CheckForErrors() in un secondo momento.  
  
    ```csharp  
    public class TodoItem  
    {  
        private TodoWindowControl parent;  
        private string name;  
        [Description("Name of the ToDo item")]  
        [Category("ToDo Fields")]  
        public string Name  
        {  
            get { return name; }  
            set  
            {  
                name = value;  
                parent.UpdateList(this);  
            }  
        }  
  
        private DateTime dueDate;  
        [Description("Due date of the ToDo item")]  
        [Category("ToDo Fields")]  
        public DateTime DueDate  
        {  
            get { return dueDate; }  
            set  
            {  
                dueDate = value;  
                parent.UpdateList(this);  
                parent.CheckForErrors();  
            }  
        }  
    }  
    ```  
  
4.  Aggiungere un riferimento privato per il controllo utente. Aggiungere un costruttore che accetta il controllo utente e il nome per questo elemento di attività. Per trovare il valore di daysAhead, ottiene la proprietà di pagina di opzioni.  
  
    ```csharp  
    private TodoWindowControl parent;  
  
    public TodoItem(TodoWindowControl control, string itemName)  
    {  
        parent = control;  
        name = itemName;  
        dueDate = DateTime.Now;  
  
        double daysAhead = 0;  
        IVsPackage package = parent.parent.Package as IVsPackage;  
        if (package != null)  
        {  
            object obj;  
            package.GetAutomationObject("ToDo.General", out obj);  
  
            ToolsOptions options = obj as ToolsOptions;  
            if (options != null)  
            {  
                daysAhead = options.DaysAhead;  
            }  
        }  
  
        dueDate = dueDate.AddDays(daysAhead);  
    }  
    ```  
  
5.  Perché le istanze del `TodoItem` classe verrà archiviata nella casella di riepilogo e la casella di riepilogo chiamerà il `ToString` funzione, è necessario eseguire l'overload di `ToString` (funzione). Todoitem. cs, aggiungere il codice seguente dopo il costruttore e prima della fine della classe.  
  
    ```csharp  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  In TodoWindowControl.xaml.cs, aggiungere i metodi stub per la classe TodoWindowControl per il `CheckForError` e `UpdateList` metodi. Inserirli dopo il ProcessDialogChar e prima della fine del file.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     Il `CheckForError` metodo verrà chiamato un metodo che ha lo stesso nome nell'oggetto padre e il metodo controllerà se tutti gli errori si sono verificati e gestiscono in modo corretto. Il `UpdateList` metodo aggiornerà la casella di riepilogo del controllo padre, il metodo viene chiamato quando il `Name` e `DueDate` proprietà in questa modifica di classe. Vengono implementati in un secondo momento.  
  
## <a name="integrate-into-the-properties-window"></a>Integrazione nella finestra proprietà  
 Ora scrivere il codice che gestisce una casella di riepilogo, che verrà collegato per il **proprietà** finestra.  
  
 È necessario modificare il pulsante, fare clic sul gestore di leggere la casella di testo, creare un oggetto TodoItem e lo aggiunge alla casella di riepilogo.  
  
1.  Sostituire `button1_Click` funzione con il codice che crea un nuovo TodoItem e lo aggiunge alla casella di riepilogo. Chiama TrackSelection(), che verranno definiti in un secondo momento.  
  
    ```csharp  
    private void button1_Click(object sender, RoutedEventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Nella visualizzazione Progettazione selezionare il controllo casella di riepilogo. Nel **proprietà** fare clic su finestra il **gestori eventi** pulsante e trovare l'evento SelectionChanged. Compilare la casella di testo con **listBox_SelectionChanged**. Questa operazione aggiunge uno stub per un gestore SelectionChanged e lo assegna all'evento.  
  
3.  Implementare il metodo TrackSelection(). Poiché è necessario ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> services, è necessario apportare la <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> il TodoWindowControl possono accedervi. Aggiungere il metodo seguente alla classe TodoWindow:  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Aggiungere le seguenti istruzioni using a TodoWindowControl.xaml.cs:  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Compilare il gestore SelectionChanged come segue:  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  A questo punto, compilare la funzione TrackSelection, che fornirà l'integrazione con il **proprietà** finestra. Questa funzione viene chiamata quando l'utente aggiunge un elemento alla casella di riepilogo o fa clic su un elemento nella casella di riepilogo. Aggiunge il contenuto della casella di riepilogo per un SelectionContainer e passa SelectionContainer per il **proprietà** della finestra <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> gestore dell'evento. Il servizio TrackSelection tiene traccia degli oggetti selezionati nell'interfaccia utente (UI) e le relative proprietà  
  
    ```csharp  
    private SelectionContainer mySelContainer;  
    private System.Collections.ArrayList mySelItems;  
    private IVsWindowFrame frame = null;  
  
    private void TrackSelection()  
    {  
        if (frame == null)  
        {  
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;  
            if (shell != null)  
            {  
                var guidPropertyBrowser = new  
                Guid(ToolWindowGuids.PropertyBrowser);  
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,  
                ref guidPropertyBrowser, out frame);  
            }  
        }  
        if (frame != null)  
            {  
                frame.Show();  
            }  
        if (mySelContainer == null)  
        {  
            mySelContainer = new SelectionContainer();  
        }  
  
        mySelItems = new System.Collections.ArrayList();  
  
        var selected = listBox.SelectedItem as TodoItem;  
        if (selected != null)  
        {  
            mySelItems.Add(selected);  
        }  
  
        mySelContainer.SelectedObjects = mySelItems;  
  
        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))  
                                as ITrackSelection;  
        if (track != null)  
        {  
            track.OnSelectChange(mySelContainer);  
        }  
    }  
    ```  
  
     Dopo aver creato una classe che il **proprietà** finestra è possibile utilizzare, è possibile integrare il **proprietà** finestra con la finestra degli strumenti. Quando l'utente fa clic su un elemento nella casella di riepilogo nella finestra degli strumenti, la **proprietà** finestra deve essere aggiornata di conseguenza. Analogamente, quando l'utente modifica un elemento di attività nel **proprietà** finestra, l'elemento associato deve essere aggiornato.  
  
7.  A questo punto, aggiungere il resto del codice della funzione UpdateList in TodoWindowControl.xaml.cs. Dovrebbe eliminare e aggiungere nuovamente il TodoItem modificato dalla casella di riepilogo.  
  
    ```csharp  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Testare il codice. Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato.  
  
9. Aprire il **Strumenti / opzioni** pagine. Verrà visualizzata la categoria di attività nel riquadro a sinistra. Categorie sono elencate in ordine alfabetico, quindi cercare in di Servizi terminal.  
  
10. Nella pagina di opzioni di attività, si dovrebbe vedere la proprietà DaysAhead impostata su **0**. Modificarla in modo che **2**.  
  
11. Nella vista o altre finestre dal menu aprirlo **TodoWindow**. Tipo **EndDate** nella casella di testo e fare clic su **Aggiungi**.  
  
12. Nella casella di riepilogo dovrebbe essere una data di due giorni successivi alla data odierna.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Aggiungere testo nella finestra di Output e gli elementi all'elenco attività  
 Per il **elenco attività**, creare un nuovo oggetto di tipo attività e quindi aggiungere tale oggetto attività per il **elenco attività** chiamando il metodo Add. Per scrivere il **Output** finestra, si chiama il metodo GetPane per ottenere un oggetto del riquadro e quindi si chiama il metodo OutputString dell'oggetto riquadro.  
  
1.  In TodoWindowControl.xaml.cs, nel `button1_Click` metodo, aggiungere codice per ottenere il **generale** riquadro del **Output** finestra (ovvero l'impostazione predefinita) e in scrittura. Il metodo dovrebbe essere simile al seguente:  
  
    ```csharp  
    private void button1_Click(object sender, EventArgs e)  
    {  
        if (textBox.Text.Length > 0)  
        {  
            var item = new TodoItem(this, textBox.Text);  
            listBox.Items.Add(item);  
  
            var outputWindow = parent.GetVsService(  
                typeof(SVsOutputWindow)) as IVsOutputWindow;  
            IVsOutputWindowPane pane;  
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;  
            outputWindow.GetPane(ref guidGeneralPane, out pane);  
            if (pane != null)  
            {  
                 pane.OutputString(string.Format(  
                    "To Do item created: {0}\r\n",  
                 item.ToString()));  
        }  
            TrackSelection();  
            CheckForErrors();  
        }  
    }  
    ```  
  
2.  Per aggiungere elementi all'elenco attività, è necessario un per aggiungere una classe annidata nella classe TodoWindowControl. La classe annidata deve derivare da <xref:Microsoft.VisualStudio.Shell.TaskProvider>. Aggiungere il codice seguente alla fine della classe TodoWindowControl.  
  
    ```csharp  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  Aggiungere un riferimento a TodoTaskProvider privato e un metodo CreateProvider() alla classe TodoWindowControl. Il codice dovrebbe essere simile al seguente:  
  
    ```csharp  
    private TodoWindowTaskProvider taskProvider;  
    private void CreateProvider()  
    {  
        if (taskProvider == null)  
        {  
            taskProvider = new TodoWindowTaskProvider(parent);  
            taskProvider.ProviderName = "To Do";  
        }  
    }  
    ```  
  
4.  Aggiungere la classe TodoWindowControl ClearError(), che svuota l'elenco di attività, e ReportError(), che aggiunge una voce all'elenco attività.  
  
    ```csharp  
    private void ClearError()  
    {  
        CreateProvider();  
        taskProvider.Tasks.Clear();  
    }  
    private void ReportError(string p)  
    {  
        CreateProvider();  
        var errorTask = new Task();  
        errorTask.CanDelete = false;  
        errorTask.Category = TaskCategory.Comments;  
        errorTask.Text = p;  
  
        taskProvider.Tasks.Add(errorTask);  
  
        taskProvider.Show();  
  
        var taskList = parent.GetVsService(typeof(SVsTaskList))  
            as IVsTaskList2;  
        if (taskList == null)  
        {  
            return;  
        }  
  
        var guidProvider = typeof(TodoWindowTaskProvider).GUID;  
         taskList.SetActiveProvider(ref guidProvider);  
    }  
    ```  
  
5.  Ora di implementare il metodo CheckForErrors, come indicato di seguito.  
  
    ```csharp  
    public void CheckForErrors()  
    {  
        foreach (TodoItem item in listBox.Items)  
        {  
            if (item.DueDate < DateTime.Now)  
            {  
                ReportError("To Do Item is out of date: "  
                    + item.ToString());  
            }  
        }  
    }  
    ```  
  
## <a name="trying-it-out"></a>Durante il tentativo e  
  
1.  Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale.  
  
2.  Aprire il TodoWindow (**visualizzazione / finestre / TodoWindow**).  
  
3.  Digitare una domanda nella casella di testo e quindi fare clic su **Aggiungi**.  
  
     Data di scadenza 2 giorni dalla data odierna viene aggiunto alla casella di riepilogo. Non vengono generati errori e **elenco attività** (**visualizzare / attività elenco**) non deve avere alcuna voce.  
  
4.  Modificare ora l'impostazione sul **Strumenti / opzioni / ToDo** pagina da **2** al **0**.  
  
5.  Digitare un'altra caratteristica di **TodoWindow** e quindi fare clic su **Aggiungi** nuovamente. Questo genera un errore e anche una voce di **elenco attività**.  
  
     Quando si aggiungono elementi, la data iniziale è ora più di 2 giorni.  
  
6.  Nel **vista** menu, fare clic su **Output** per aprire la **Output** finestra.  
  
     Si noti che ogni volta che si aggiunge un elemento, in cui viene visualizzato un messaggio di **elenco attività** riquadro.  
  
7.  Fare clic su uno degli elementi nella casella di riepilogo.  
  
     Il **proprietà** finestra Visualizza due proprietà per l'elemento.  
  
8.  Modificare una delle proprietà e quindi premere INVIO.  
  
     L'elemento viene aggiornato nella casella di riepilogo.