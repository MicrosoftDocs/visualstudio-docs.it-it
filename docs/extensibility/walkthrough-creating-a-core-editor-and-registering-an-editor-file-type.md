---
title: Creazione di un Editor di componenti di base e la registrazione di un tipo di File Editor | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6bb9b9443a60e54d875d6e3992a18ac1f0691244
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Procedura dettagliata: Creazione di un Editor di componenti di base e la registrazione di un tipo di File dell'Editor
Questa procedura dettagliata viene illustrato come creare un pacchetto VSPackage che inizia il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale quando un file con estensione .myext viene caricato.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Percorsi per il modello di progetto di pacchetto di Visual Studio  
 Il modello di progetto di pacchetto di Visual Studio si trova in tre posizioni diverse nella finestra di dialogo **Nuovo progetto** :  
  
1.  Nella sezione relativa all'estendibilità di Visual Basic. Il linguaggio predefinito del progetto è Visual Basic.  
  
2.  Nella sezione relativa all'estendibilità di C#. Il linguaggio predefinito del progetto è C#.  
  
3.  Nella sezione relativa all'estendibilità di altri tipi di progetto. Il linguaggio predefinito del progetto è C++.  
  
### <a name="to-create-the-vspackage"></a>Per creare il pacchetto VSPackage  
  
-   Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e creare un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pacchetto VSPackage denominato `MyPackage`, come descritto in [procedura dettagliata: creazione di un pacchetto VSPackage comando di Menu](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Per aggiungere la factory editor  
  
1.  Fare doppio clic su di **MyPackage** , scegliere **Aggiungi** e quindi fare clic su **classe**.  
  
2.  Nel **Aggiungi nuovo elemento** finestra di dialogo, accertarsi di **classe** il modello è selezionato, tipo `EditorFactory.cs` per il nome e quindi fare clic su **Aggiungi** per aggiungere la classe al progetto.  
  
     Il file di EditorFactory.cs deve essere aperto automaticamente.  
  
3.  Riferimento agli assembly seguenti dal codice.  
  
    ```vb  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```csharp  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  Aggiungere un GUID per il `EditorFactory` classe aggiungendo il `Guid` attributo immediatamente prima della dichiarazione di classe.  
  
     È possibile generare un nuovo GUID usando il programma guidgen.exe nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prompt dei comandi, oppure facendo clic su **Crea GUID** sul **strumenti** menu. Il GUID utilizzato qui è solo un esempio; non utilizzarlo nel progetto.  
  
    ```vb  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```csharp  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  Nella definizione della classe, aggiungere due variabili private per contenere il pacchetto padre e un provider di servizi.  
  
    ```vb  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```csharp  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  Aggiungere un costruttore di classe pubblica che accetta un parametro di tipo <xref:Microsoft.VisualStudio.Shell.Package>:  
  
    ```vb  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```csharp  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  Modificare il `EditorFactory` classe dichiarazione da cui derivare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia.  
  
    ```vb  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```csharp  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  Fare doppio clic su <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, fare clic su **implementa interfaccia**, quindi fare clic su **implementa interfaccia in modo esplicito**.  
  
     Aggiunge i quattro metodi che devono essere implementati nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia.  
  
9. Sostituire il contenuto del metodo `IVsEditorFactory.Close` con il codice riportato di seguito.  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Sostituire il contenuto del `IVsEditorFactory.SetSite` con il codice seguente.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Sostituire il contenuto del metodo `IVsEditorFactory.MapLogicalView` con il codice riportato di seguito.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Sostituire il contenuto del metodo `IVsEditorFactory.CreateEditorInstance` con il codice riportato di seguito.  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```csharp  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Compilare il progetto e verificare che non siano presenti errori.  
  
### <a name="to-register-the-editor-factory"></a>Per registrare la factory editor  
  
1.  In **Esplora**, doppio clic sul file resources. resx per aprirlo in una tabella di stringhe, in cui la voce **String1 è** selezionato.  
  
2.  Modificare il nome dell'identificatore di `IDS_EDITORNAME` e il testo da **MyPackage Editor.** Questa stringa verrà visualizzata come nome dell'editor.  
  
3.  Aprire il file VSPackage.resx e aggiungere una nuova stringa, impostare il nome su **101** e il valore da `IDS_EDITORNAME`. In questo modo il pacchetto con un ID di risorsa per accedere alla stringa che appena creato.  
  
    > [!NOTE]
    >  Se il file VSPackage.resx contiene un'altra stringa di `name` attributo impostato su **101**, sostituire con un altro valore univoco, numeric, qui e nei passaggi seguenti.  
  
4.  In **Esplora**, aprire il file MyPackagePackage.cs.  
  
     Si tratta del file del pacchetto principale.  
  
5.  Aggiungere i seguenti attributi di utente subito prima di `Guid` attributo.  
  
    ```vb  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```csharp  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     Il <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> attributo associa l'estensione del file .myext il factory editor in modo che ogni volta che un file che viene caricata l'estensione, viene richiamato il factory editor.  
  
6.  Aggiungere una variabile privata per il `MyPackage` prima il costruttore di classe e assegnarle il tipo `EditorFactory`.  
  
    ```vb  
    Private editorFactory As EditorFactory  
    ```  
  
    ```csharp  
    private EditorFactory editorFactory;  
    ```  
  
7.  Trovare il `Initialize` (metodo) (potrebbe essere necessario aprire il `Package Members` area nascosta) e aggiungere il codice seguente dopo la chiamata a `base.Initialize()`.  
  
    ```vb  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```csharp  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  Compilare il programma e assicurarsi che non ci siano errori.  
  
     Questo passaggio registra la factory dell'editor nell'hive del Registro di sistema sperimentale per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se viene chiesto di sovrascrivere il file Resource. h, fare clic su **OK**.  
  
9. Creare un file di esempio denominato TextFile1.myext.  
  
10. Premere **F5** per aprire un'istanza dell'istanza sperimentale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. Nell'istanza sperimentale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]via di **File** dal menu **aprire** e quindi fare clic su **File**.  
  
12. Trovare TextFile1.myext e quindi fare clic su **aprire**.  
  
     Ora è stato possibile caricare il file.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale gestisce un'ampia gamma di tipi di file di testo e strettamente con servizi di linguaggio forniscono un'ampia gamma di funzionalità quali l'evidenziazione della sintassi, corrispondenza parentesi graffe e gli elenchi di completamento di parole e il membro completamento IntelliSense. Se si lavora con file di testo, è possibile utilizzare l'editor di componenti di base con un servizio di linguaggio personalizzato che supporta i tipi di file specifico.  
  
 Un pacchetto VSPackage può richiamare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale, fornendo un factory dell'editor. Questa factory editor viene utilizzata ogni volta che viene caricato un file che è associato. Se il file fa parte di un progetto, l'editor di componenti di base viene richiamato automaticamente a meno che non viene sottoposto a override per il pacchetto VSPackage. Tuttavia, se il file viene caricato all'esterno di un progetto, quindi l'editor di componenti di base deve essere in modo esplicito richiamato dal pacchetto VSPackage.  
  
 Per ulteriori informazioni sull'editor di componenti di base, vedere [all'interno di componenti di base Editor](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)   
 [Creazione di istanze di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)