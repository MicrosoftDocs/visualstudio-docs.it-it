---
title: Generazione di testo in fase di esecuzione con modelli di testo T4 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Preprocessed Text Template project item
- TextTemplatingFilePreprocessor custom tool
- text templates, TransformText() method
- text templates, generating files at run time
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4f2681f3be13e98ff3b9dbf411b03ea9f3fc054a
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="run-time-text-generation-with-t4-text-templates"></a>Generazione di testo in fase di esecuzione con modelli di testo T4
È possibile generare stringhe di testo nell'applicazione in fase di esecuzione utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modelli di testo di runtime. Il computer in cui viene eseguita l'applicazione non ha [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Modelli di runtime sono talvolta denominati "pre-elaborato i modelli di testo" perché è in fase di compilazione, il modello genera codice che viene eseguito in fase di esecuzione.  
  
 Ogni modello è una combinazione del testo visualizzato nella stringa generata e frammenti di codice programma. I frammenti del programma forniscono valori per le parti variabili della stringa e inoltre controllano parti ripetute e condizionali.  
  
 Il modello seguente, ad esempio, potrebbe essere utilizzato in un'applicazione che crea un report HTML.  
  
```  
<#@ template language="C#" #>  
<html><body>  
<h1>Sales for Previous Month</h2>  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
This report is Company Confidential.  
</body></html>  
```  
  
 Si noti che il modello è una pagina HTML in cui le parti variabili sono state sostituite con il codice del programma. È possibile iniziare la progettazione di tale pagina scrivendo un prototipo statico della pagina HTML. È quindi possibile sostituire la tabella e le altre parti variabili con il codice programma che genera il contenuto che varia da una volta al successivo.  
  
 Utilizzo di un modello dell'applicazione consente risulta più semplice visualizzare il formato finale dell'output che potrebbe, ad esempio, una lunga serie di istruzioni di scrittura. Apportare modifiche al formato dell'output è più semplice e affidabile.  
  
## <a name="creating-a-run-time-text-template-in-any-application"></a>Creazione di un modello di testo in fase di esecuzione in qualsiasi applicazione  
  
#### <a name="to-create-a-run-time-text-template"></a>Per creare un modello di testo in fase di esecuzione  
  
1.  In Esplora soluzioni, nel menu di scelta rapida del progetto, scegliere **Aggiungi**, **nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** nella finestra di dialogo **il modello di testo di Runtime**. (In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] osserva **comuni\Generale**.)  
  
3.  Digitare un nome per il file modello.  
  
    > [!NOTE]
    >  Il nome del file modello da utilizzare come nome di classe nel codice generato. Pertanto, non dovrebbe avere spazi o segni di punteggiatura.  
  
4.  Scegliere **Aggiungi**.  
  
     Viene creato un nuovo file con estensione **tt**. Il relativo **lo strumento personalizzato** è impostata su **TextTemplatingFilePreprocessor**. Contiene le righe seguenti:  
  
    ```  
    <#@ template language="C#" #>  
    <#@ assembly name="System.Core" #>  
    <#@ import namespace="System.Linq" #>  
    <#@ import namespace="System.Text" #>  
    <#@ import namespace="System.Collections.Generic" #>  
    ```  
  
## <a name="converting-an-existing-file-to-a-run-time-template"></a>Conversione di un File esistente in un modello in fase di esecuzione  
 Un buon metodo per creare un modello consiste nel convertire un esempio dell'output esistente. Ad esempio, se l'applicazione genererà file HTML, è possibile avviare creando un file HTML semplice. Assicurarsi che funzioni correttamente e che il suo aspetto sia corretto. Successivamente, includerla nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del progetto e convertirlo in un modello.  
  
#### <a name="to-convert-an-existing-text-file-to-a-run-time-template"></a>Per convertire un file di testo esistente in un modello in fase di esecuzione  
  
1.  Includere il file nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. In Esplora soluzioni, nel menu di scelta rapida del progetto, scegliere **Aggiungi**, **elemento esistente**.  
  
2.  Impostare il file **strumenti personalizzati** proprietà **TextTemplatingFilePreprocessor**. In Esplora soluzioni, nel menu di scelta rapida del file, scegliere **proprietà**.  
  
    > [!NOTE]
    >  Se è già impostata la proprietà, assicurarsi che sia **TextTemplatingFilePreprocessor** e non **TextTemplatingFileGenerator**. Questa situazione può verificarsi se si include un file con estensione già **tt**.  
  
3.  Modificare l'estensione del nome file **tt**. Anche se questo passaggio è facoltativo, consente di evitare di aprire il file in un editor non corretto.  
  
4.  Rimuovere spazi o punteggiatura da parte del nome del file principale. Ad esempio "My Web Page.tt" risulta corretto, mentre "Paginaweb.tt" sia corretto. Il nome del file da utilizzare come nome di classe nel codice generato.  
  
5.  Inserire la riga seguente all'inizio del file. Se si lavora in un progetto di Visual Basic, sostituire "C#" con "VB".  
  
     `<#@ template language="C#" #>`  
  
## <a name="the-content-of-the-run-time-template"></a>Il contenuto del modello in fase di esecuzione  
  
### <a name="template-directive"></a>Direttiva template  
 Mantenere la prima riga del modello com'era quando è stato creato il file:  
  
 `<#@ template language="C#" #>`  
  
 Il parametro language dipende dalla lingua del progetto.  
  
### <a name="plain-content"></a>Contenuto semplice  
 Modificare il **tt** file per contenere il testo che si desidera che l'applicazione da generare. Ad esempio:  
  
```  
<html><body>  
<h1>Sales for January</h2>  
<!-- table to be inserted here -->  
This report is Company Confidential.  
</body></html>  
```  
  
### <a name="embedded-program-code"></a>Codice programma incorporato  
 È possibile inserire codice programma tra `<#` e `#>`. Ad esempio:  
  
```csharp  
<table>  
    <# for (int i = 1; i <= 10; i++)  
       { #>  
         <tr><td>Test name <#= i #> </td>  
             <td>Test value <#= i * i #> </td> </tr>  
    <# } #>  
 </table>  
```  
  
```vb  
<table>  
<#  
    For i As Integer = 1 To 10  
#>  
    <tr><td>Test name <#= i #> </td>  
      <td>Test value <#= i*i #> </td></tr>  
<#  
    Next  
#>  
</table>  
  
```  
  
 Si noti che le istruzioni vengono inserite tra `<# ... #>` e le espressioni vengono inserite tra `<#= ... #>`. Per ulteriori informazioni, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-template"></a>Uso del modello  
  
### <a name="the-code-built-from-the-template"></a>Il codice compilato dal modello  
 Ogni volta che si salva il **tt** file, una società affiliata **cs** o **vb** file verrà generato. Per visualizzare questo file in Esplora soluzioni, espandere il **tt** nodo del file. In un progetto di Visual Basic, sarà possibile espandere il nodo dopo aver fatto clic **Mostra tutti i file** nella barra degli strumenti Esplora soluzioni.  
  
 Si noti che questo file secondario contiene una classe parziale che contiene un metodo denominato `TransformText()`. È possibile chiamare questo metodo dall'applicazione.  
  
### <a name="generating-text-at-run-time"></a>Generazione di testo in fase di esecuzione  
 Nel codice dell'applicazione, è possibile generare il contenuto del modello tramite una chiamata simile al seguente:  
  
```csharp  
MyWebPage page = new MyWebPage();  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
  
```  
  
```vb  
Dim page = New My.Templates.MyWebPage  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
 Per inserire la classe generata in un determinato spazio dei nomi, impostare il **Namespace strumento personalizzato** proprietà del file di modello di testo.  
  
### <a name="debugging-runtime-text-templates"></a>Modelli di testo di Runtime di debug  
 Eseguire il debug e testare i modelli di testo runtime nello stesso modo come codice ordinario.  
  
 È possibile impostare un punto di interruzione in un modello di testo. Se si avvia l'applicazione in modalità di debug da Visual Studio, è possibile eseguire il codice e valutare espressioni nel modo consueto.  
  
### <a name="passing-parameters-in-the-constructor"></a>Passaggio di parametri nel costruttore  
 In genere un modello è necessario importare alcuni dati da altre parti dell'applicazione. Per facilitare questa operazione, il codice compilato dal modello è una classe parziale. È possibile creare un'altra parte della stessa classe in un altro file nel progetto. Tale file può includere un costruttore con parametri, proprietà e funzioni che è possano accedere dal codice che è incorporato nel modello e dal resto dell'applicazione.  
  
 Ad esempio, è possibile creare un file separato **MyWebPageCode.cs**:  
  
```csharp  
partial class MyWebPage  
{  
    private MyData m_data;  
    public MyWebPage(MyData data) { this.m_data = data; }}  
```  
  
 Nel file di modello **paginaweb.tt**, è possibile scrivere:  
  
```csharp  
<h2>Sales figures</h2>  
<table>  
<# foreach (MyDataItem item in m_data.Items)   
   // m_data is declared in MyWebPageCode.cs  
   { #>  
      <tr><td> <#= item.Name #> </td>  
          <td> <#= item.Value #> </td></tr>  
<# } // end of foreach  
#>  
</table>  
```  
  
 Per utilizzare questo modello nell'applicazione:  
  
```csharp  
MyData data = ...;  
MyWebPage page = new MyWebPage(data);  
String pageContent = page.TransformText();  
System.IO.File.WriteAllText("outputPage.html", pageContent);  
```  
  
#### <a name="constructor-parameters-in-visual-basic"></a>Parametri del costruttore in Visual Basic  
 In [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], il file separato **MyWebPageCode.vb** contiene:  
  
```vb  
Namespace My.Templates  
  Partial Public Class MyWebPage  
    Private m_data As MyData  
    Public Sub New(ByVal data As MyData)  
      m_data = data  
    End Sub  
  End Class  
End Namespace  
```  
  
 Il file di modello può contenere:  
  
```vb  
<#@ template language="VB" #>  
<html><body>  
<h1>Sales for January</h2>  
<table>  
<#  
    For Each item In m_data.Items  
#>  
    <tr><td>Test name <#= item.Name #> </td>  
      <td>Test value <#= item.Value #> </td></tr>  
<#  
    Next  
#>  
</table>  
This report is Company Confidential.  
</body></html>  
  
```  
  
 E il modello viene richiamato passando il parametro nel costruttore:  
  
```vb  
Dim data = New My.Templates.MyData  
    ' Add data values here ....  
Dim page = New My.Templates.MyWebPage(data)  
Dim pageContent = page.TransformText()  
System.IO.File.WriteAllText("outputPage.html", pageContent)  
  
```  
  
#### <a name="passing-data-in-template-properties"></a>Passaggio di dati nelle proprietà dei modelli  
 Un metodo alternativo per passare dati al modello consiste nell'aggiungere le proprietà pubbliche per la classe di modello in una definizione di classe parziale. L'applicazione è possibile impostare le proprietà prima di richiamare `TransformText()`.  
  
 È anche possibile aggiungere campi alla classe del modello in una definizione parziale. Ciò consente di passare dati tra le esecuzioni successive del modello.  
  
### <a name="use-partial-classes-for-code"></a>Usare le classi parziali per il codice  
 Molti sviluppatori preferiscono evitare di scrivere grandi quantità di codice nei modelli. In alternativa, è possibile definire metodi in una classe parziale che ha lo stesso nome del file del modello. Chiamare i metodi dal modello. In questo modo, il modello Mostra più chiaramente quale destinazione stringa di output sarà simile. Discussioni sull'aspetto del risultato possono essere separate dalla logica della creazione di dati che vengono visualizzati.  
  
### <a name="assemblies-and-references"></a>Assembly e i riferimenti  
 Se si desidera fare riferimento a .NET o altri assembly, ad esempio il codice del modello **System.Xml.dll**, è necessario aggiungerlo al progetto **riferimenti** nel modo consueto.  
  
 Se si desidera importare uno spazio dei nomi nello stesso modo come un `using` istruzione, è possibile farlo con il `import` direttiva:  
  
```  
<#@ import namespace="System.Xml" #>  
```  
  
 Queste direttive devono essere inserite all'inizio del file, immediatamente dopo il `<#@template` direttiva.  
  
### <a name="shared-content"></a>Contenuto condiviso  
 Se si dispone di testo che viene condiviso tra diversi modelli, è possibile inserirlo in un file separato e includerlo in ogni file in cui verrà visualizzato:  
  
```  
<#@include file="CommonHeader.txt" #>  
```  
  
 Il contenuto incluso può contenere qualsiasi combinazione di codice programma e testo normale e può contenere altre direttive di inclusione e altre direttive.  
  
 La direttiva include può essere utilizzata in un punto qualsiasi all'interno del testo di un file di modello o un file incluso.  
  
### <a name="inheritance-between-run-time-text-templates"></a>Ereditarietà tra modelli di testo in fase di esecuzione  
 È possibile condividere il contenuto tra i modelli in fase di esecuzione mediante la scrittura di un modello di classe di base, che può essere astratto. Utilizzare il `inherits` parametro il `<@#template#>` direttiva per fare riferimento a un'altra classe di modello di runtime.  
  
#### <a name="inheritance-pattern-fragments-in-base-methods"></a>Modello di ereditarietà: frammenti nei metodi di Base  
 Nel modello utilizzato nell'esempio che segue, tenere presente quanto segue:  
  
-   La classe di base `SharedFragments` definisce i metodi all'interno di blocchi della funzionalità di classe `<#+ ... #>`.  
  
-   La classe di base non contiene testo libero. Tutti i relativi blocchi di testo, invece, si verificano all'interno di metodi di funzionalità della classe.  
  
-   La classe derivata richiama i metodi definiti `SharedFragments`.  
  
-   L'applicazione chiama il `TextTransform()` metodo della classe derivata, ma non trasforma la classe di base `SharedFragments`.  
  
-   Le classi base e derivate sono modelli di testo di runtime:, ovvero il **lo strumento personalizzato** è impostata su **TextTemplatingFilePreprocessor**.  
  
 **SharedFragments.tt:**  
  
```csharp  
<#@ template language="C#" #>  
<#+  
protected void SharedText(int n)  
{  
#>  
   Shared Text <#= n #>  
<#+  
}  
// Insert more methods here if required.  
#>  
  
```  
  
 **MyTextTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" inherits="SharedFragments" #>  
begin 1  
   <# SharedText(2); #>  
end 1  
  
```  
  
 **MyProgram.cs:**  
  
```csharp  
...   
MyTextTemplate1 t1  = new MyTextTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **L'output risultante:**  
  
```  
begin 1  
    Shared Text 2  
end 1  
```  
  
#### <a name="inheritance-pattern-text-in-base-body"></a>Modello di ereditarietà: Testo nel corpo di Base  
 In questo approccio alternativo all'utilizzo dell'ereditarietà del modello, la maggior parte del testo è definita nel modello di base. I modelli derivati forniscono dati e frammenti di testo che corrispondono al contenuto di base.  
  
 **AbstractBaseTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" #>  
  
Here is the description for this derived template:  
  <#= this.Description #>  
  
Here is the fragment specific to this derived template:  
<#   
  this.PushIndent("  ");  
  SpecificFragment(42);   
  this.PopIndent();  
#>  
End of common template.  
<#+   
  // State set by derived class before calling TextTransform:  
  protected string Description = "";  
  // 'abstract' method to be defined in derived classes:  
  protected virtual void SpecificFragment(int n) { }  
#>  
  
```  
  
 **DerivedTemplate1.tt:**  
  
```csharp  
<#@ template language="C#" inherits="AbstractBaseTemplate1" #>  
<#   
  // Set the base template properties:  
  base.Description = "Description for this derived class";   
  
  // Run the base template:  
  base.TransformText();  
  
#>  
End material for DerivedTemplate1.  
  
<#+  
// Provide a fragment specific to this derived template:  
  
protected override void SpecificFragment(int n)  
{  
#>  
   Specific to DerivedTemplate1 : <#= n #>  
<#+  
}  
#>  
  
```  
  
 **Codice dell'applicazione:**  
  
```csharp  
...   
DerivedTemplate1 t1 = new DerivedTemplate1();  
string result = t1.TransformText();  
Console.WriteLine(result);  
```  
  
 **Output risultante:**  
  
```  
Here is the description for this derived template:  
  Description for this derived class  
  
Here is the fragment specific to this derived template:  
     Specific to DerivedTemplate1 : 42  
End of common template.  
End material for DerivedTemplate1.  
```  
  
## <a name="related-topics"></a>Argomenti correlati  
 Progettazione modelli di tempo: Se si desidera utilizzare un modello per generare il codice che diventa parte dell'applicazione, vedere [generazione codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Modelli di runtime possono essere utilizzati in qualsiasi applicazione in cui i modelli e il relativo contenuto sono determinati in fase di compilazione. Tuttavia, se si desidera scrivere un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione che generi il testo dai modelli che cambiano in fase di esecuzione, vedere [richiamo di trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md)   
 [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)   
 [Informazioni su T4: Pre-elaborato modelli di testo](http://www.olegsych.com/2009/09/t4-preprocessed-text-templates/)