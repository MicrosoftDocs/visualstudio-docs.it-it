---
title: Creazione di un Windows Form controllo casella degli strumenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- winforms
- toolbox
- windows forms
ms.assetid: 0be6ffc1-8afd-4d02-9a5d-e27dde05fde6
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4229d9045dfe64fcb320eca7cf004de56e7f8f0d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-windows-forms-toolbox-control"></a>Creazione di un controllo casella degli strumenti di Windows Form
Il modello di elemento di controllo della casella degli strumenti di Windows Form incluso in Visual Studio Extensibility Tools (VS SDK) consente di creare un controllo che viene aggiunto automaticamente al **della casella degli strumenti** quando l'estensione è installata. In questo argomento viene illustrato come utilizzare il modello per creare un controllo semplice contatore che è possibile distribuire ad altri utenti.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-windows-forms-toolbox-control"></a>Creazione di un controllo casella degli strumenti di Windows Form  
 Il modello di controllo della casella degli strumenti di Windows Form consente di creare un controllo utente non definito e fornisce tutte le funzionalità necessarie per aggiungere il controllo di **della casella degli strumenti**.  
  
#### <a name="create-an-extension-with-a-windows-forms-toolbox-control"></a>Creare un'estensione con un controllo casella degli strumenti di Windows Form  
  
1.  Creare un progetto VSIX denominato `MyWinFormsControl`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un **il controllo della casella degli strumenti di Windows Form** modello di elemento denominato `Counter`. Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# / Extensibility** e selezionare **controllo della casella degli strumenti di Windows Form**  
  
3.  Aggiunge un controllo utente, un `ProvideToolboxControlAttribute` <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> per posizionare il controllo nel **della casella degli strumenti**e un **Microsoft.VisualStudio.ToolboxControl** voce della risorsa nel manifesto VSIX per la distribuzione.  
  
### <a name="building-a-user-interface-for-the-control"></a>Creazione di un'interfaccia utente per il controllo  
 Il `Counter` controllo richiede due controlli figlio: un <xref:System.Windows.Forms.Label> per visualizzare il conteggio corrente e un <xref:System.Windows.Forms.Button> per reimpostare il conteggio su 0. Poiché i chiamanti incrementeranno il contatore a livello di codice, altri controlli figlio non sono necessari.  
  
##### <a name="to-build-the-user-interface"></a>Per creare l'interfaccia utente  
  
1.  In **Esplora**, fare doppio clic su Counter.cs per aprirlo nella finestra di progettazione.  
  
2.  Rimuovere "Fare clic qui!" **Pulsante** inclusa per impostazione predefinita quando si aggiunge il modello di elemento di controllo della casella degli strumenti di Windows Form.  
  
3.  Dal **della casella degli strumenti**, trascinare un `Label` controllo e quindi un `Button` controllo sottostanti nell'area di progettazione.  
  
4.  Ridimensionare il controllo utente generale a 150, 50 pixel e ridimensionare il pulsante di controllo su 50, 20 pixel.  
  
5.  Nel **proprietà** finestra, impostare i valori seguenti per i controlli nell'area di progettazione.  
  
    |Control|Proprietà|Valore|  
    |-------------|--------------|-----------|  
    |`Label1`|**per**|""|  
    |`Button1`|**Name**|btnReset|  
    |`Button1`|**per**|Reimposta|  
  
### <a name="coding-the-user-control"></a>Codifica del controllo utente  
 Il controllo `Counter` esporrà un metodo per incrementare il contatore, un evento da generare ogni volta che il contatore viene incrementato, un pulsante `Reset` e tre proprietà per archiviare il conteggio corrente, il testo visualizzato e se mostrare o nascondere il pulsante `Reset` . Il `ProvideToolboxControl` attributo determina la posizione di **della casella degli strumenti** il `Counter` controllo verrà visualizzato.  
  
##### <a name="to-code-the-user-control"></a>Per codificare il controllo utente  
  
1.  Fare doppio clic sul form per aprire il gestore dell'evento carico nella finestra del codice.  
  
2.  Sopra il metodo del gestore eventi, creare un numero intero per archiviare il valore del contatore e una stringa per archiviare il testo visualizzato come illustrato nell'esempio seguente nella classe del controllo.  
  
    ```csharp  
    int currentValue;  
    string displayText;  
    ```  
  
3.  Creare le seguenti dichiarazioni di proprietà pubblica.  
  
    ```csharp  
    public int Value {  
        get { return currentValue; }   
    }  
  
    public string Message {  
        get { return displayText; }  
        set { displayText = value; }  
    }  
  
    public bool ShowReset {  
        get { return btnReset.Visible; }  
        set { btnReset.Visible = value; }  
    }  
  
    ```  
  
     I chiamanti possono accedere a queste proprietà per ottenere e impostare il testo visualizzato del contatore e per mostrare o nascondere il `Reset` pulsante. I chiamanti possono ottenere il valore corrente di sola lettura `Value` proprietà, ma non è possibile impostare il valore direttamente.  
  
4.  Inserire il codice seguente il `Load` evento per il controllo.  
  
    ```csharp  
    private void Counter_Load(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = Message + Value;  
    }  
  
    ```  
  
     L'impostazione di **etichetta** testo il <xref:System.Windows.Forms.UserControl.Load> evento consente di caricare prima i relativi valori vengono applicati le proprietà di destinazione. L'impostazione di **etichetta** testo nel costruttore genera un oggetto vuoto **etichetta**.  
  
5.  Creare il metodo pubblico seguente per incrementare il contatore.  
  
    ```csharp  
    public void Increment()  
    {  
        currentValue++;  
        label1.Text = displayText + Value;  
        Incremented(this, EventArgs.Empty);  
    }  
  
    ```  
  
6.  Aggiungere una dichiarazione per il `Incremented` eventi alla classe del controllo.  
  
    ```csharp  
    public event EventHandler Incremented;  
    ```  
  
     I chiamanti possono aggiungere gestori all'evento per rispondere alle modifiche nel valore del contatore.  
  
7.  Tornare alla visualizzazione progettazione e fare doppio clic su di `Reset` pulsante per generare il `btnReset_Click` gestore eventi e compilare in, come illustrato nell'esempio seguente.  
  
    ```csharp  
    private void btnReset_Click(object sender, EventArgs e)  
    {  
        currentValue = 0;  
        label1.Text = displayText + Value;  
    }  
  
    ```  
  
8.  Immediatamente sopra la definizione di classe, nel `ProvideToolboxControl` dichiarazione di attributo, modificare il valore del primo parametro da `"MyWinFormsControl.Counter"` a `"General"`. In questo modo si imposta il nome del gruppo di elementi che ospiterà il controllo nella **casella degli strumenti**.  
  
     L'esempio seguente mostra l'attributo `ProvideToolboxControl` e la definizione di classe modificata.  
  
    ```csharp  
    [ProvideToolboxControl("General", false)]  
    public partial class Counter : UserControl  
    ```  
  
### <a name="testing-the-control"></a>Test del controllo  
 Per testare un **della casella degli strumenti** controllare, test prima di tutto nell'ambiente di sviluppo e quindi eseguirne il test in un'applicazione compilata.  
  
##### <a name="to-test-the-control"></a>Per testare il controllo  
  
1.  Premere F5.  
  
     Si compila il progetto e apre una seconda istanza sperimentale di Visual Studio con il controllo installato.  
  
2.  Nell'istanza sperimentale di Visual Studio, creare un **Windows Forms Application** progetto.  
  
3.  In **Esplora**, fare doppio clic su Form1. cs per aprirlo nella finestra di progettazione se non è già aperto.  
  
4.  Nel **della casella degli strumenti**, `Counter` controllo deve essere visualizzato nel **generale** sezione.  
  
5.  Trascinare un `Counter` il controllo al form e selezionarlo. Il `Value`, `Message`, e `ShowReset` proprietà verranno visualizzate nel **proprietà** finestra, insieme alle proprietà ereditate da <xref:System.Windows.Forms.UserControl>.  
  
6.  Impostare la proprietà `Message` su `Count:`.  
  
7.  Trascinare un <xref:System.Windows.Forms.Button> controllo al form e quindi impostare le proprietà di nome e il testo del pulsante su `Test`.  
  
8.  Fare doppio clic sul pulsante per aprire Form1 nella visualizzazione codice e creare un gestore eventi click.  
  
9. Nel gestore click, chiamare `counter1.Increment()`.  
  
10. Nella funzione del costruttore, dopo la chiamata a `InitializeComponent`, tipo `counter1``.``Incremented +=` e quindi premere TAB due volte.  
  
     Visual Studio genera un gestore a livello di modulo per il `counter1.Incremented` evento.  
  
11. Evidenziare il `Throw` istruzione nel gestore eventi, tipo `mbox`, e quindi premere TAB due volte per generare una finestra di messaggio dal frammento di codice mbox.  
  
12. Nella riga successiva, aggiungere il seguente `if` / `else` blocco per impostare la visibilità del `Reset` pulsante.  
  
    ```csharp  
    if (counter1.Value < 5) counter1.ShowReset = false;  
    else counter1.ShowReset = true;  
    ```  
  
13. Premere F5.  
  
     Il modulo verrà aperto. Il `Counter` controllo Visualizza il testo seguente.  
  
     **Conteggio: 0**  
  
14. Fare clic su **Test**.  
  
     L'incremento del contatore e Visual Studio consente di visualizzare una finestra di messaggio.  
  
15. Chiudere la finestra di messaggio.  
  
     Il **reimpostare** scompare.  
  
16. Fare clic su **Test** fino a quando il contatore raggiunge **5** la chiusura del messaggio caselle ogni volta.  
  
     Il **reimpostare** pulsante verrà nuovamente visualizzata.  
  
17. Fare clic su **Reimposta**.  
  
     Il contatore viene reimpostato su **0**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Quando si crea un controllo della **casella degli strumenti** , Visual Studio crea un file denominato *NomeProgetto*.vsix nella cartella \bin\debug\ del progetto. È possibile distribuire il controllo caricando il file VSIX in una rete o in un sito Web. Quando un utente apre il file. VSIX, il controllo viene installato e aggiunto a Visual Studio **della casella degli strumenti** nel computer dell'utente. In alternativa, è possibile caricare il file VSIX il [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=123847) sito Web in modo che gli utenti potranno trovarlo cercando con la **strumenti / estensioni e aggiornamenti** finestra di dialogo.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Creazione di un controllo casella degli strumenti WPF](../extensibility/creating-a-wpf-toolbox-control.md)   
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Nozioni fondamentali sullo sviluppo di controlli Windows Form](/dotnet/framework/winforms/controls/windows-forms-control-development-basics)