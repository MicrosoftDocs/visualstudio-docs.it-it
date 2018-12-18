---
title: Creazione di una pagina di opzioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], creating
ms.assetid: 9f4e210c-4b47-4daa-91fa-1c301c4587f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9fe021816b990a068bbd74d2fba62e073ff3136
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-options-page"></a>Creazione di una pagina di opzioni
Questa procedura dettagliata crea una pagina di opzioni semplice che utilizza una griglia delle proprietà per esaminare e impostare le proprietà.  
  
 Per salvare queste proprietà per il ripristino da un file di impostazioni, eseguire la procedura seguente, quindi vedere [la creazione di una categoria di impostazioni](../extensibility/creating-a-settings-category.md).  
  
 Il Framework MPF fornisce due classi che consentono di creare pagine di opzioni del menu Strumenti, la <xref:Microsoft.VisualStudio.Shell.Package> classe e <xref:Microsoft.VisualStudio.Shell.DialogPage> classe. Creare un pacchetto VSPackage per fornire un contenitore per le pagine Creazione di una sottoclasse della classe del pacchetto. Creare ogni pagina di opzioni di strumenti derivandolo dalla classe DialogPage.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tools-options-grid-page"></a>Creazione di una pagina della griglia di opzioni strumenti  
 In questa sezione è creare una semplice griglia delle proprietà opzioni del menu Strumenti. Utilizzare questa griglia per visualizzare e modificare il valore di una proprietà.  
  
#### <a name="to-create-the-vsix-project-and-add-a-vspackage"></a>Per creare il progetto VSIX e aggiungere un pacchetto VSPackage  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX, che conterrà gli asset di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `MyToolsOptionsExtension`. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  Aggiungere un pacchetto VSPackage tramite l'aggiunta di un modello di elemento di pacchetto di Visual Studio denominato `MyToolsOptionsPackage`. Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Nel **finestra di dialogo Aggiungi nuovo elemento**, passare a **elementi di Visual c# / Extensibility** e selezionare **pacchetto di Visual Studio**. Nel **nome** campo nella parte inferiore della finestra di dialogo, modificare il nome di file in `MyToolsOptionsPackage.cs`. Per ulteriori informazioni su come creare un pacchetto VSPackage, vedere [creazione di un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md).  
  
#### <a name="to-create-the-tools-options-property-grid"></a>Per creare la griglia delle proprietà di opzioni del menu Strumenti  
  
1.  Aprire il file MyToolsOptionsPackage nell'editor di codice.  
  
2.  Aggiungere la seguente istruzione using.  
  
    ```csharp  
    using System.ComponentModel;  
    ```  
  
3.  Dichiarare una classe OptionPageGrid e derivare da <xref:Microsoft.VisualStudio.Shell.DialogPage>.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  }  
    ```  
  
4.  Applicare un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla classe VSPackage per assegnare una categoria di opzioni e il nome di pagina di opzioni per la OptionPageGrid alla classe. Il risultato dovrebbe essere simile al seguente:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
5.  Aggiungere un `OptionInteger` proprietà per il `OptionPageGrid` classe.  
  
    -   Applicare un <xref:System.ComponentModel.CategoryAttribute?displayProperty=fullName> da assegnare alla proprietà di una categoria di proprietà della griglia.  
  
    -   Applicare un <xref:System.ComponentModel.DisplayNameAttribute?displayProperty=fullName> da assegnare alla proprietà di un nome.  
  
    -   Applicare un <xref:System.ComponentModel.DescriptionAttribute?displayProperty=fullName> da assegnare alla proprietà di una descrizione.  
  
    ```csharp  
    public class OptionPageGrid : DialogPage  
    {  
        private int optionInt = 256;  
  
        [Category("My Category")]  
        [DisplayName("My Integer Option")]  
        [Description("My integer option")]  
        public int OptionInteger  
        {  
            get { return optionInt; }  
            set { optionInt = value; }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  L'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage> supporta le proprietà che dispongono di convertitori appropriati o che sono strutture o matrici che possono essere espanso in una proprietà che dispongono di convertitori di tipo appropriati. Per un elenco di convertitori di tipi, vedere il <xref:System.ComponentModel> dello spazio dei nomi.  
  
6.  Compilare il progetto e avviare il debug.  
  
7.  Nell'istanza sperimentale di Visual Studio, sul **strumenti** dal menu **opzioni**.  
  
     Nel riquadro a sinistra dovrebbe essere **categoria My**. (Opzioni categorie sono elencate in ordine alfabetico, in modo deve essere visualizzato sulla metà verso il basso nell'elenco.) Aprire **categoria My** e quindi fare clic su **pagina griglia personale**. La griglia di opzioni viene visualizzata nel riquadro di destra. La categoria della proprietà è **My Options**, e il nome della proprietà è **opzione intero My**. La descrizione della proprietà, **l'opzione di numeri interi**, viene visualizzata nella parte inferiore del riquadro. Modificare il valore dal valore iniziale pari a 256 su un altro nome. Fare clic su **OK**e quindi riaprire **pagina griglia personale**. È possibile vedere che il nuovo valore viene mantenuto.  
  
     La pagina delle opzioni è anche disponibile tramite avvio veloce di Visual Studio. Nella finestra di avvio veloce nell'angolo superiore destro dell'IDE, digitare **categoria My** e verrà visualizzato **categoria My -> pagina della griglia My** nell'elenco a discesa.  
  
## <a name="creating-a-tools-options-custom-page"></a>Creazione di un oggetto personalizzato di opzioni di strumenti pagina  
 In questa sezione creare una pagina di opzioni del menu Strumenti con un'interfaccia utente personalizzata. Utilizzare questa pagina per visualizzare e modificare il valore di una proprietà.  
  
1.  Aprire il file MyToolsOptionsPackage nell'editor di codice.  
  
2.  Aggiungere la seguente istruzione using.  
  
    ```vb  
    using System.Windows.Forms;  
    ```  
  
3.  Aggiungere un `OptionPageCustom` classe, appena prima di `OptionPageGrid` classe. Derivare la nuova classe da `DialogPage`.  
  
    ```csharp  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
4.  Aggiungere un attributo GUID. Aggiungere una proprietà OptionString:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
    }  
    ```  
  
5.  Applicare un secondo <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> alla classe VSPackage. Questo attributo assegna la classe di una categoria di opzioni e il nome di pagina di opzioni.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)]  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [Guid(GuidList.guidMyToolsOptionsPkgString)]  
    [ProvideOptionPage(typeof(OptionPageGrid),  
        "My Category", "My Grid Page", 0, 0, true)]  
    [ProvideOptionPage(typeof(OptionPageCustom),  
        "My Category", "My Custom Page", 0, 0, true)]  
    public sealed class MyToolsOptionsPackage : Package  
    ```  
  
6.  Aggiungere un nuovo **controllo utente** denominato MyUserControl al progetto.  
  
7.  Aggiungere un **TextBox** nel controllo utente.  
  
     Nel **proprietà** finestra, sulla barra degli strumenti, fare clic su di **eventi** pulsante e quindi fare doppio clic su di **lasciare** evento. Il nuovo gestore eventi viene visualizzato nel codice MyUserControl. cs.  
  
8.  Aggiungere un pubblico `OptionsPage` campo, un `Initialize` metodo alla classe del controllo e aggiornamento, il gestore dell'evento per impostare l'opzione valore per il contenuto della casella di testo:  
  
    ```csharp  
    public partial class MyUserControl : UserControl  
    {  
        public MyUserControl()  
        {  
            InitializeComponent();  
        }  
  
        internal OptionPageCustom optionsPage;  
  
        public void Initialize()  
        {  
            textBox1.Text = optionsPage.OptionString;  
        }  
  
        private void textBox1_Leave(object sender, EventArgs e)  
        {  
            optionsPage.OptionString = textBox1.Text;  
        }  
    }  
    ```  
  
     Il `optionsPage` campo contiene un riferimento all'elemento padre `OptionPageCustom` istanza. Il `Initialize` metodo visualizza `OptionString` nel **TextBox**. Il gestore dell'evento scrive il valore corrente del **TextBox** per il `OptionString` quando lo stato attivo lascia il **TextBox**.  
  
9. Nel file di codice del pacchetto, aggiungere una sostituzione per il `OptionPageCustom.Window` proprietà alla classe OptionPageCustom per creare, inizializzare e restituire un'istanza di `MyUserControl`. La classe dovrebbe risultare simile al seguente:  
  
    ```csharp  
    [Guid("00000000-0000-0000-0000-000000000000")]  
    public class OptionPageCustom : DialogPage  
    {  
        private string optionValue = "alpha";  
  
        public string OptionString  
        {  
            get { return optionValue; }  
            set { optionValue = value; }  
        }  
  
        protected override IWin32Window Window  
        {  
            get  
            {  
                MyUserControl page = new MyUserControl();  
                page.optionsPage = this;  
                page.Initialize();  
                return page;  
            }  
        }  
    }  
    ```  
  
10. Compilare ed eseguire il progetto.  
  
11. Nell'istanza sperimentale, fare clic su **Strumenti / opzioni**.  
  
12. Trovare **del nome della categoria** e quindi **personalizzato pagina**.  
  
13. Modificare il valore di **OptionString**. Fare clic su **OK**e quindi riaprire **My Custom pagina**. È possibile vedere che il nuovo valore è resa persistente.  
  
## <a name="accessing-options"></a>Accedere alle opzioni  
 In questa sezione ottenere il valore di un'opzione dal VSPackage che ospita la pagina di opzioni del menu Strumenti associata. La stessa tecnica può essere utilizzata per ottenere il valore di qualsiasi proprietà pubblica.  
  
1.  Nel file di codice del pacchetto, aggiungere una proprietà pubblica denominata **OptionInteger** per il **MyToolsOptionsPackage** classe.  
  
    ```  
    public int OptionInteger  
    {  
        get  
        {  
            OptionPageGrid page = (OptionPageGrid)GetDialogPage(typeof(OptionPageGrid));  
            return page.OptionInteger;  
        }  
    }  
  
    ```  
  
     Questo codice chiama <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> per creare o recuperare un `OptionPageGrid` istanza. `OptionPageGrid` chiamate <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromStorage%2A> per caricare le relative opzioni, che sono proprietà pubbliche.  
  
2.  Aggiungere un modello di elemento di comando personalizzato denominato **MyToolsOptionsCommand** per visualizzare il valore. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **MyToolsOptionsCommand.cs**.  
  
3.  Nel file MyToolsOptionsCommand, sostituire il corpo del comando `ShowMessageBox` metodo con le operazioni seguenti:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        MyToolsOptionsPackage myToolsOptionsPackage = this.package as MyToolsOptionsPackage;  
        System.Windows.Forms.MessageBox.Show(string.Format(CultureInfo.CurrentCulture, "OptionInteger: {0}", myToolsOptionsPackage.OptionInteger));  
    }  
  
    ```  
  
4.  Compilare il progetto e avviare il debug.  
  
5.  Nell'istanza sperimentale, nel **strumenti** menu, fare clic su **MyToolsOptionsCommand richiamare**.  
  
     Una finestra di messaggio consente di visualizzare il valore corrente di `OptionInteger`.  
  
## <a name="see-also"></a>Vedere anche  
 [Opzioni e pagine di opzioni](../extensibility/internals/options-and-options-pages.md)