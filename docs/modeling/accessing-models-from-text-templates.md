---
title: Accesso ai modelli da modelli di testo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, accessing models
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 397e60225740c34d1d70555ccd8294522550a3e1
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="accessing-models-from-text-templates"></a>Accesso ai modelli da modelli di testo
Tramite i modelli di testo, è possibile creare file di report, file di codice sorgente e altri file di testo che si basano sui modelli di linguaggio specifico di dominio. Per informazioni sui modelli di testo di base, vedere [la generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md). I modelli di testo funzioneranno in modalità sperimentale quando si esegue il debug di tale linguaggio DSL e funzionano anche in un computer in cui è stato distribuito del linguaggio DSL.

> [!NOTE]
>  Quando si crea una soluzione DSL, un modello di testo di esempio  **\*tt** vengono generati file nel progetto di debug. Quando si modificano i nomi delle classi di dominio, questi modelli non funzioneranno più. Tuttavia, le direttive di base che è necessario includere e vengono forniti esempi che è possibile aggiornare in modo che corrisponda il modello DSL.

 Per accedere a un modello da un modello di testo:

-   Impostare la proprietà di ereditarietà della direttiva template per <xref:Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation>. Fornisce l'accesso all'archivio.

-   Specificare i processori di direttive per DSL che si desidera accedere. In modo che è possibile utilizzare relative classi di dominio, proprietà e relazioni nel codice del modello di testo viene caricato l'assembly per il modello DSL. Permette inoltre di caricare il file del modello specificato.

 Oggetto `.tt` file simile all'esempio seguente viene creato nel progetto di debug quando si crea un nuovo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione del modello DSL minimo Language.

```
<#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ output extension=".txt" #>
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>

This text will be output directly.

This is the name of the model: <#= this.ModelRoot.Name #>

Here is a list of elements in the model:
<#
  // When you change the DSL Definition, some of the code below may not work.
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {#>
<#= element.Name #>
<#
  }
#>

```

 Si noti quanto segue su questo modello:

-   Il modello è possibile utilizzare le classi di dominio, proprietà e relazioni definite nella definizione DSL.

-   Il modello viene caricato il file del modello specificato nella `requires` proprietà.

-   Una proprietà in `this` contiene l'elemento radice. Da qui, il codice è possibile passare agli altri elementi del modello. Il nome della proprietà corrisponde in genere come la classe di dominio radice di tale linguaggio DSL. In questo esempio si tratta di `this.ExampleModel`.

-   Anche se la lingua in cui vengono scritti i frammenti di codice c#, è possibile generare il testo di qualsiasi tipo. In alternativa, è possibile scrivere il codice in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aggiungendo la proprietà `language="VB"` per il `template` direttiva.

-   Per eseguire il debug del modello, aggiungere `debug="true"` per il `template` direttiva. Il modello verrà aperto in un'altra istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se si verifica un'eccezione. Se si desidera interrompere il debugger in un momento specifico nel codice, inserire l'istruzione `System.Diagnostics.Debugger.Break();`

     Per ulteriori informazioni, vedere [debug di un modello di testo T4](../modeling/debugging-a-t4-text-template.md).

## <a name="about-the-dsl-directive-processor"></a>Sul processore di direttiva DSL
 Il modello è possibile utilizzare le classi di dominio definite nella propria definizione DSL. Questo è provocato da una direttiva che in genere viene visualizzato in prossimità dell'inizio del modello. Nell'esempio precedente, è il seguente.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1'" #>
```

 Il nome della direttiva ( `MyLanguage`, in questo esempio) deriva dal nome di tale linguaggio DSL. Richiama un *processore di direttiva* che viene generato come parte di tale linguaggio DSL. È possibile trovare il codice sorgente nel **Dsl\GeneratedCode\DirectiveProcessor.cs**.

 Il processore di direttiva DSL esegue due attività principali:

-   Inserisce in modo efficace le direttive di importazione e di assembly nel modello che fa riferimento a tale linguaggio DSL. Ciò consente di utilizzare le classi di dominio nel codice del modello.

-   Carica il file specificato nella `requires` parametro e imposta una proprietà `this` che fa riferimento all'elemento radice del modello caricato.

## <a name="validating-the-model-before-running-the-template"></a>La convalida del modello prima di eseguire il modello
 È possibile generare il modello da convalidare prima che il modello viene eseguito.

```
<#@ MyLanguage processor="MyLanguageDirectiveProcessor" requires="fileName='Sample.myDsl1';validation='open|load|save|menu'" #>

```

 Si noti che:

1.  Il `filename` e `validation` i parametri sono separati da ";" e non deve essere presente alcun altro separatori o spazi.

2.  L'elenco delle categorie di convalida determina quali metodi di convalida verranno eseguiti. Più categorie devono essere separate da "&#124;" e non deve essere presente alcun altro separatori o spazi.

 Se viene rilevato un errore, verrà segnalato nella finestra degli errori e il file di risultati conterrà un messaggio di errore.

##  <a name="Multiple"></a> L'accesso a più modelli da un modello di testo

> [!NOTE]
>  Questo metodo consente di leggere più modelli nello stesso modello, ma non supporta riferimenti ModelBus. Per leggere i modelli che sono correlati da ModelBus riferimenti, vedere [utilizzando ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 Se si desidera accedere a più di un modello dallo stesso modello di testo, è necessario chiamare il processore di direttiva generato una volta per ogni modello. È necessario specificare il nome del file di ogni modello di `requires` parametro. È necessario specificare i nomi che si desidera utilizzare per la classe di dominio nella radice di `provides` parametro. È necessario specificare valori diversi per il `provides` parametri in ciascuna delle chiamate di direttiva. Ad esempio, si supponga di aver chiamati Library.xyz School.xyz e Work.xyz tre file di modello. Per accedere ad essi dallo stesso modello di testo, è necessario scrivere tre chiamate simili a quelle seguenti.

```
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Library.xyz'" provides="ExampleModel=LibraryModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='School.xyz'" provides="ExampleModel=SchoolModel" #>
<#@ ExampleModel processor="<YourLanguageName>DirectiveProcessor" requires="fileName='Work.xyz'" provides="ExampleModel=WorkModel" #>
```

> [!NOTE]
>  Questo esempio di codice è per una lingua che è basata sul modello di soluzione Language minimo.

 Per accedere ai modelli nel modello di testo, è ora possibile scrivere codice simile al codice nell'esempio seguente.

```csharp
<#
foreach (ExampleElement element in this.LibraryModel.Elements)
...
foreach (ExampleElement element in this.SchoolModel.Elements)
...
foreach (ExampleElement element in this.WorkModel.Elements)
...
#>
```

```vb
<#
For Each element As ExampleElement In Me.LibraryModel.Elements
...
For Each element As ExampleElement In Me.SchoolModel.Elements
...
For Each element As ExampleElement In Me.WorkModel.Elements
...
#>
```

## <a name="loading-models-dynamically"></a>Il caricamento dei modelli in modo dinamico
 Se si desidera determinare in fase di esecuzione quali modelli di carico, è possibile caricare un file di modello in modo dinamico nel codice programma, anziché utilizzare la direttiva DSL specifiche.

 Tuttavia, una delle funzioni della direttiva DSL specifiche è lo spazio dei nomi DSL, in modo che il codice del modello è possibile utilizzare le classi di dominio definite in tale linguaggio DSL. Poiché non si utilizza la direttiva, è necessario aggiungere  **\<assembly >** e  **\<importare >** direttive per tutti i modelli che è possibile caricare. Si tratta di una semplice se i modelli diversi che è possibile caricare sono tutte le istanze della stessa DSL.

 Per caricare il file, il metodo più efficace consiste nell'utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ModelBus. In uno scenario tipico, il modello di testo utilizzerà una direttiva DSL specifiche per il primo modello di carico nel modo consueto. Tale modello conterrebbe ModelBus di riferimenti a un altro modello. È possibile utilizzare ModelBus per aprire il modello di riferimento e accedere a un particolare elemento. Per ulteriori informazioni, vedere [utilizzando ModelBus di Visual Studio in un modello di testo](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

 In uno scenario meno comune, si potrebbe voler aprire un file di modello per cui si dispone solo di un nome file e che potrebbero non essere in corrente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto. In questo caso, è possibile aprire il file utilizzando la tecnica descritta in [procedura: aprire un modello dal File di codice programma](../modeling/how-to-open-a-model-from-file-in-program-code.md).

## <a name="generating-multiple-files-from-a-template"></a>La generazione di più file da un modello
 Se si desidera generare un file diversi, ad esempio, per generare un file separato per ogni elemento in un modello, esistono diversi approcci disponibili. Per impostazione predefinita, viene generato un solo file da ogni file di modello.

### <a name="splitting-a-long-file"></a>Suddivisione di un file lunghi
 In questo metodo, utilizzare un modello per generare un singolo file, separato da un delimitatore. Quindi si suddividere il file nelle relative parti. Esistono due modelli, uno per generare il singolo file e l'altro per la divisione.

 **LoopTemplate.t4** genera l'errore lungo singolo file. Si noti che l'estensione del file è ".t4", perché non deve essere elaborato direttamente quando fa clic su **Trasforma tutti i modelli**. Questo modello accetta un parametro che specifica la stringa delimitatore che separa i segmenti:

```
<#@ template ninherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
<#@ parameter name="delimiter" type="System.String" #>
<#@ output extension=".txt" #>
<#@ MyDSL processor="MyDSLDirectiveProcessor" requires="fileName='SampleModel.mydsl1';validation='open|load|save|menu'" #>
<#
  // Create a file segment for each element:
  foreach (ExampleElement element in this.ExampleModel.Elements)
  {
    // First item is the delimiter:
#>
<#= string.Format(delimiter, element.Id) #>

   Element: <#= element.Name #>
<#
   // Here you generate more content derived from the element.
  }
#>

```

 `LoopSplitter.tt` richiama `LoopTemplate.t4`e quindi suddivide il file risultante in segmenti. Si noti che questo modello non è necessario essere un modello di modellazione, perché non è possibile leggere il modello.

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="Microsoft.VisualStudio.TextTemplating" #>
<#@ import namespace="System.Runtime.Remoting.Messaging" #>
<#@ import namespace="System.IO" #>

<#
  // Get the local path:
  string itemTemplatePath = this.Host.ResolvePath("LoopTemplate.t4");
  string dir = Path.GetDirectoryName(itemTemplatePath);

  // Get the template for generating each file:
  string loopTemplate = File.ReadAllText(itemTemplatePath);

  Engine engine = new Engine();

  // Pass parameter to new template:
  string delimiterGuid = Guid.NewGuid().ToString();
  string delimiter = "::::" + delimiterGuid + ":::";
  CallContext.LogicalSetData("delimiter", delimiter + "{0}:::");
  string joinedFiles = engine.ProcessTemplate(loopTemplate, this.Host);

  string [] separateFiles = joinedFiles.Split(new string [] {delimiter}, StringSplitOptions.None);

  foreach (string nameAndFile in separateFiles)
  {
     if (string.IsNullOrWhiteSpace(nameAndFile)) continue;
     string[] parts = nameAndFile.Split(new string[]{":::"}, 2, StringSplitOptions.None);
     if (parts.Length < 2) continue;
#>
 Generate: [<#= dir #>] [<#= parts[0] #>]
<#
     // Generate a file from this item:
     File.WriteAllText(Path.Combine(dir, parts[0] + ".txt"), parts[1]);
  }
#>

```