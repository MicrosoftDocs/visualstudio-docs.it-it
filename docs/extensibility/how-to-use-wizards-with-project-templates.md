---
title: 'Procedura: utilizzare procedure guidate con modelli di progetto | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d29d2a1313bdb4e8a5e8654068984893578af4a0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-wizards-with-project-templates"></a>Procedura: utilizzare procedure guidate con modelli di progetto
In Visual Studio è disponibile l'interfaccia <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> che, se implementata, consente di eseguire il codice personalizzato quando un utente crea un progetto da un modello.  
  
 Personalizzazione dei modelli di progetto consente di visualizzare l'interfaccia utente personalizzata che consente di raccogliere input utente per personalizzare il modello, aggiungere ulteriori file al modello, o qualsiasi altra azione consentita su un progetto.  
  
 Il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaccia vengono chiamati in vari momenti durante la creazione di progetti, avvio, non appena un utente fa clic **OK** sul **nuovo progetto** la finestra di dialogo. Ogni metodo dell'interfaccia denominato per descrivere il punto in cui viene chiamato. Ad esempio, Visual Studio chiama <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> non appena viene avviata creare il progetto, rendendolo un percorso valido per scrivere codice personalizzato per raccogliere l'input dell'utente.  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>Creazione di un progetto di modello di progetto con un progetto VSIX  
 Iniziare a creare un modello personalizzato con il progetto modello progetto, che fa parte di Visual Studio SDK. In questa procedura si utilizzerà un progetto di modello di progetto c#, ma è inoltre disponibile un progetto di modello di progetto Visual Basic. Quindi aggiungere un progetto VSIX nella soluzione che contiene il progetto di modello di progetto.  
  
1.  Creare un progetto di modello di progetto c# (in Visual Studio, **File > Nuovo > progetto > Visual c# > estendibilità > modello di progetto c#**). Il nome **MyProjectTemplate**.  
  
    > [!NOTE]
    >  Potrebbe essere necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Aggiungere un nuovo progetto VSIX (**File > Nuovo > progetto > Visual c# > estendibilità > progetto VSIX**) nella stessa soluzione come progetto di modello di progetto (nel **Esplora**, selezionare il nodo della soluzione, pulsante destro del mouse e scegliere **Aggiungi > Nuovo progetto**). Denominarla **MyProjectWizard.**  
  
3.  Impostare il progetto VSIX come progetto di avvio. Nel **Esplora**, selezionare il nodo del progetto VSIX, pulsante destro del mouse e selezionare **imposta come progetto di avvio**.  
  
4.  Aggiungere il progetto di modello come un asset del progetto VSIX. Nel **Esplora**, sotto il nodo del progetto VSIX, trovare il **vsixmanifest** file. Fare doppio clic su esso per aprirlo nell'editor del manifesto.  
  
5.  Nell'editor del manifesto, selezionare il **asset** scheda sul lato sinistro della finestra.  
  
6.  Nel **asset** , selezionare **New**. Nel **Aggiungi nuovo Asset** finestra per il campo tipo **Microsoft.VisualStudio.ProjectTemplate**. Nel **origine** campi, selezionare **un progetto nella soluzione corrente**. Nel **progetto** campi, selezionare **MyProjectTemplate**. Fare quindi clic su **OK**.  
  
7.  Compilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio. (L'operazione potrebbe richiedere alcuni minuti).  
  
8.  Nella seconda istanza di Visual Studio, provare a creare un nuovo progetto con il nuovo modello. (**File > Nuovo > progetto > c# > modello MyProject**). Il nuovo progetto deve essere visualizzato con una classe denominata **Class1**. Ora creato un modello di progetto personalizzati! Arrestare il debug.  
  
## <a name="creating-a-custom-template-wizard"></a>Creazione di una procedura guidata modello personalizzato  
 In questo argomento viene illustrato come creare una procedura guidata personalizzata che consente di aprire un Windows Form prima che venga creato il progetto. Il form consente agli utenti di aggiungere un valore del parametro personalizzato che viene aggiunto al codice sorgente durante la creazione del progetto.  
  
1.  Configurare il progetto VSIX per consentire la creazione di un assembly.  
  
2.  Nel **Esplora**, selezionare il nodo del progetto VSIX. In Esplora soluzioni, verrà visualizzato il **proprietà** finestra. In caso contrario, selezionare **Vista > finestra delle proprietà**, oppure premere **F4**. Nella finestra Proprietà, selezionare i campi seguenti per `true`:  
  
    -   **IncludeAssemblyInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInVSIXContainer**  
  
    -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3.  Aggiungere l'assembly come asset per il progetto VSIX. Aprire il file vsixmanifest e selezionare il **asset** scheda. Nel **Aggiungi nuovo Asset** finestra per **tipo** selezionare **Microsoft.VisualStudio.Assembly**, per **origine** selezionare **A progetto nella soluzione corrente**e per **progetto** selezionare **MyProjectWizard**.  
  
4.  Aggiungere i riferimenti seguenti al progetto VSIX. (Nel **Esplora**, sotto il progetto VSIX progetto selezionare nodo **riferimenti**, pulsante destro del mouse e selezionare **Aggiungi riferimento**.) Nel **Aggiungi riferimento** finestra di dialogo, nel **Framework** scheda, trovare il **System. Windows Forms** assembly e selezionarlo. Selezionare il **estensioni** trova sulla scheda di **EnvDTE** assembly e selezionarlo. Inoltre il **Microsoft.VisualStudio.TemplateWizardInterface** assembly e selezionarlo. Fare clic su **OK**.  
  
5.  Aggiungere una classe per l'implementazione della procedura guidata per il progetto VSIX. (In Esplora soluzioni, fare doppio clic sul nodo del progetto VSIX e selezionare **Aggiungi**, quindi **nuovo elemento**, quindi **classe**.) Nome della classe **WizardImplementation**.  
  
6.  Sostituire il codice di **WizardImplementationClass.cs** file con il codice seguente:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.TemplateWizard;  
    using System.Windows.Forms;  
    using EnvDTE;  
  
    namespace MyProjectWizard  
    {  
        public class WizardImplementation:IWizard  
        {  
            private UserInputForm inputForm;  
            private string customMessage;  
  
            // This method is called before opening any item that   
            // has the OpenInEditor attribute.  
            public void BeforeOpeningFile(ProjectItem projectItem)  
            {  
            }  
  
            public void ProjectFinishedGenerating(Project project)  
            {  
            }  
  
            // This method is only called for item templates,  
            // not for project templates.  
            public void ProjectItemFinishedGenerating(ProjectItem   
                projectItem)  
            {  
            }  
  
            // This method is called after the project is created.  
            public void RunFinished()  
            {  
            }  
  
            public void RunStarted(object automationObject,  
                Dictionary<string, string> replacementsDictionary,  
                WizardRunKind runKind, object[] customParams)  
            {  
                try  
                {  
                    // Display a form to the user. The form collects   
                    // input for the custom message.  
                    inputForm = new UserInputForm();  
                    inputForm.ShowDialog();  
  
                    customMessage = UserInputForm.CustomMessage;  
  
                    // Add custom parameters.  
                    replacementsDictionary.Add("$custommessage$",   
                        customMessage);  
                }  
                catch (Exception ex)  
                {  
                    MessageBox.Show(ex.ToString());  
                }  
            }  
  
            // This method is only called for item templates,  
            // not for project templates.  
            public bool ShouldAddProjectItem(string filePath)  
            {  
                return true;  
            }          
        }  
    }  
    ```  
  
     Il **UserInputForm** a cui fa riferimento in questo codice verrà implementato in un secondo momento.  
  
     Il `WizardImplementation` classe contiene le implementazioni del metodo per ogni membro di <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>. In questo esempio, solo il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo esegue un'attività. Tutti gli altri metodi non esegue alcuna operazione o restituiscono `true`.  
  
     Il <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> metodo accetta quattro parametri:  
  
    -   Un <xref:System.Object> parametro che può essere la radice <xref:EnvDTE._DTE> oggetto, che consente di personalizzare il progetto.  
  
    -   Oggetto <xref:System.Collections.Generic.Dictionary%602> parametro che contiene una raccolta di tutti i parametri predefiniti nel modello. Per ulteriori informazioni sui parametri di modello, vedere [parametri di modello](../ide/template-parameters.md).  
  
    -   Oggetto <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> parametro che contiene informazioni sul tipo di modello è in uso.  
  
    -   Un <xref:System.Object> matrice che contiene un set di parametri passati alla procedura guidata da Visual Studio.  
  
     Questo esempio viene aggiunto un valore di parametro di input dell'utente per il <xref:System.Collections.Generic.Dictionary%602> parametro. Ogni istanza di `$custommessage$` parametro nel progetto verrà sostituito con il testo immesso dall'utente. È necessario aggiungere gli assembly seguenti al progetto: **sistema** e **Drawing**.
  
7.  Creare ora il **UserInputForm**. Nel **WizardImplementation.cs** file, aggiungere il codice seguente dopo la fine del **WizardImplementation** classe.  
  
    ```csharp  
    public partial class UserInputForm : Form  
        {  
            private static string customMessage;  
            private TextBox textBox1;  
            private Button button1;  
  
            public UserInputForm()  
            {  
                this.Size = new System.Drawing.Size(155, 265);   
  
                button1 = new Button();  
                button1.Location = new System.Drawing.Point(90, 25);  
                button1.Size = new System.Drawing.Size(50, 25);  
                button1.Click += button1_Click;  
                this.Controls.Add(button1);  
  
                textBox1 = new TextBox();  
                textBox1.Location = new System.Drawing.Point(10, 25);  
                textBox1.Size = new System.Drawing.Size(70, 20);  
                this.Controls.Add(textBox1);  
            }  
            public static string CustomMessage  
            {  
                get  
                {  
                    return customMessage;  
                }  
                set  
                {  
                    customMessage = value;  
                }     
            }  
            private void button1_Click(object sender, EventArgs e)  
            {  
                customMessage = textBox1.Text;  
                this.Close();
            }  
        }  
    ```  
  
     Input dell'utente fornisce un semplice form per l'immissione di un parametro personalizzato. Il modulo contiene una casella di testo denominata `textBox1` e un pulsante denominato `button1`. Quando si fa clic sul pulsante, il testo dalla casella di testo viene archiviato nel `customMessage` parametro.  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>Connettere la procedura guidata per il modello personalizzato  
 Affinché il modello di progetto personalizzato per utilizzare la creazione guidata personalizzata, è necessario firmare l'assembly della procedura guidata e aggiungere alcune righe al modello di progetto personalizzato che indichi la posizione in cui trovare l'implementazione della procedura guidata quando viene creato un nuovo progetto.  
  
1.  Firmare l'assembly. Nel **Esplora**, selezionare il progetto VSIX, pulsante destro del mouse e selezionare **le proprietà del progetto**.  
  
2.  Nel **le proprietà del progetto** finestra, seleziona il **firma** scheda nel **firma** scheda **firmare l'assembly**. Nel **Scegli un file chiave con nome sicuro** campi, selezionare  **\<nuovo >**. Nel **Crea chiave con nome sicuro** finestra, nel **nome file di chiave** digitare **key.snk**. Deselezionare la **Proteggi file di chiave con una password** campo.  
  
3.  Nel **Esplora**, selezionare il progetto VSIX e trovare il **proprietà** finestra.  
  
4.  Impostare il **Directory di Output nell'Output di compilazione copia** campo **true**. In questo modo l'assembly deve essere copiato nella directory di output quando la soluzione viene ricompilata. È comunque contenuto nel file. VSIX. È necessario visualizzare l'assembly per scoprire la chiave di firma.  
  
5.  Ricompilare la soluzione.  
  
6.  È possibile individuare il file key.snk nella directory del progetto MyProjectWizard (**\<il percorso del disco > \MyProjectTemplate\MyProjectWizard\key.snk**). Copiare il file snk.  
  
7.  Passare alla directory di output e trovare l'assembly (**\<il percorso del disco > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**). Incollare il file snk qui. (Questo non è assolutamente necessario, ma per facilitare la procedura seguente).  
  
8.  Aprire una finestra di comando e passare alla directory in cui è stato creato l'assembly.  
  
9. Trovare il **sn.exe** strumento firma digitale. Ad esempio, in un sistema operativo a 64 bit di Windows 10, un tipico percorso potrebbe essere la seguente:  
  
     **C:\Programmi\Microsoft file (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 strumenti**  
  
     Se non si trova lo strumento, provare a eseguire **dove /R.  Sn.exe** nella finestra di comando. Prendere nota del percorso.  
  
10. Estrarre la chiave pubblica dal file snk. Nella finestra di comando, digitare  
  
     **\<percorso di sn.exe > \sn.exe -p snk outfile.key.**  
  
     Non dimenticare di racchiudere il percorso di sn.exe tra virgolette se sono presenti spazi dei nomi di directory.  
  
11. Ottenere il token di chiave pubblica dal file di output:  
  
     **\<percorso di sn.exe > \sn.exe -t outfile.key.**  
  
     Nuovamente, non dimenticare le virgolette. Verrà visualizzata una riga nell'output simile al seguente  
  
     **Token di chiave pubblica è <token>**  
  
     Prendere nota di questo valore.  
  
12. Aggiungere il riferimento per la creazione guidata personalizzata per il file. vstemplate del modello di progetto. In Esplora soluzioni, trovare il file denominato MyProjectTemplate.vstemplate e aprirlo. Dopo la fine del \<TemplateContent >, quindi aggiungere la sezione seguente:  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     Dove **MyProjectWizard** è il nome dell'assembly, e **token** è il token è stato copiato nel passaggio precedente.  
  
13. Salvare tutti i file nel progetto e ricompilare.  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>Aggiunta del parametro personalizzato per il modello  
 In questo esempio, il progetto utilizzato come modello Visualizza il messaggio specificato nel modulo di input dell'utente della procedura guidata personalizzata.  
  
1.  In Esplora soluzioni, individuare il **MyProjectTemplate** del progetto e aprire **Class1. cs**.  
  
2.  Nel `Main` metodo dell'applicazione, aggiungere la riga di codice seguente.  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     Il parametro `$custommessage$` viene sostituito con il testo immesso nel modulo di input dell'utente quando viene creato un progetto dal modello.  
  
 Ecco il file di codice completo, prima è stato esportato in un modello.  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>Utilizzando la creazione guidata personalizzata  
 È ora possibile creare un progetto dal modello e utilizzare la creazione guidata personalizzata.  
  
1.  Ricompilare la soluzione e avviare il debug. Verrà visualizzata una seconda istanza di Visual Studio.  
  
2.  Creare un nuovo progetto MyProjectTemplate. (**File > Nuovo > progetto > c# > MyProjectTemplate**)  
  
3.  Nel **nuovo progetto** la finestra di dialogo, individuare il modello, digitare un nome e fare clic su **OK**.  
  
     Verrà visualizzata la procedura guidata input dell'utente.  
  
4.  Digitare un valore per il parametro personalizzato e fare clic sul pulsante.  
  
     Chiude il form dell'input utente procedura guidata e viene creato un progetto dal modello.  
  
5.  In **Esplora**, fare doppio clic su file del codice sorgente e fare clic su **Visualizza codice**.  
  
     Si noti che `$custommessage$` è stato sostituito con il testo immesso nella procedura guidata input dell'utente.  
  
## <a name="see-also"></a>Vedere anche  

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
[Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)  
[Elemento WizardExtension (modelli di Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)  
[Pacchetti NuGet in modelli di Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
