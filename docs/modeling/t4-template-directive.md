---
title: T4 Direttiva Template | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3c4e53c4d123a5a5de493059c68ef09685c903a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="t4-template-directive"></a>Direttiva template T4
Un modello di testo T4 di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di solito inizia con la direttiva `template` che specifica come deve essere elaborato il modello. Un modello di testo e qualsiasi file in esso incluso non devono contenere più di una direttiva template.  
  
 Per una panoramica generale di scrittura di modelli di testo, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-template-directive"></a>Utilizzo della direttiva template  
  
```  
<#@ template [language="VB"] [compilerOptions="options"] [culture="code"] [debug="true"] [hostspecific="true"] [inherits="templateBaseClass"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 La direttiva `template` dispone di diversi attributi che consentono di specificare vari aspetti della trasformazione. Tutti gli attributi sono facoltativi.  
  
## <a name="compileroptions-attribute"></a>attributo compilerOptions  
 Esempio:  
 `compilerOptions="optimize+"`  
  
 Valori validi:  
 Qualsiasi opzione del compilatore valida.  
  
 Ignorato per i modelli (pre-elaborati) della fase di esecuzione.  
  
 Queste opzioni vengono applicate una volta che il modello è stato convertito in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)] e che è stato compilato il codice risultante.  
  
## <a name="culture-attribute"></a>attributo Culture  
 Esempio:  
 `culture="de-CH"`  
  
 Valori validi:  
 "", la lingua inglese, ovvero l'impostazione predefinita.  
  
 Impostazioni cultura espresse come una stringa nel formato xx-XX. Ad esempio, it-IT, en-US, ja-JP, de-CH e de-DE. Per altre informazioni, vedere <xref:System.Globalization.CultureInfo?displayProperty=fullName>.  
  
 L'attributo Culture specifica le impostazioni cultura da utilizzare quando un blocco di espressione viene convertito in testo.  
  
## <a name="debug-attribute"></a>attributo debug  
 Esempio:  
 ```  
debug="true"  
```  
  
 Valori validi:  
 `true, false`. False è l'impostazione predefinita.  
  
 Se l'attributo `debug` ha valore `true`, il file di codice intermedio conterrà le informazioni che consentono al debugger di identificare in modo più accurato la posizione nel modello in cui si è verificata un'interruzione o un'eccezione.  
  
 Per i modelli in fase di progettazione il file di codice intermedio verrà scritto per il **% TEMP %** directory.  
  
 Per eseguire un modello in fase di progettazione nel debugger, salvare il modello di testo, quindi aprire il menu di scelta rapida del modello di testo in Esplora soluzioni e scegliere **Debug modello T4**.  
  
## <a name="hostspecific-attribute"></a>attributo Hostspecific  
 Esempio:  
 ```  
hostspecific="true"  
```  
  
 Valori validi:  
 `true, false, trueFromBase`. False è l'impostazione predefinita.  
  
 Se si imposta il valore di questo attributo su `true`, viene aggiunta una proprietà denominata `Host` alla classe generata dal modello di testo. La proprietà è un riferimento all'host del motore di trasformazione e viene dichiarata come <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>. Se è stato definito un host personalizzato, è possibile eseguirne il cast sul tipo di host personalizzato.  
  
 Poiché il tipo di questa proprietà dipende dal tipo di host, è utile solo se si scrive un modello di testo che funziona solo con un host specifico. È applicabile a [in fase di progettazione modelli](../modeling/design-time-code-generation-by-using-t4-text-templates.md), ma non [modelli in fase di esecuzione](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Quando `hostspecific` è `true` e si utilizza [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile eseguire il cast di `this.Host` a IServiceProvider per accedere alle funzionalità di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. È inoltre possibile utilizzare `Host.ResolvePath(filename)` per ottenere il percorso assoluto di un file nel progetto. Ad esempio:  
  
```csharp  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="EnvDTE" #>  
<#@ import namespace="System.IO" #>  
<# // Get the Visual Studio API as a service:  
 DTE dte = ((IServiceProvider)this.Host).GetCOMService(typeof(DTE)) as DTE;    
#>  
Number of projects in this solution: <#=  dte.Solution.Projects.Count #>  
  
<#  
 // Find a path within the current project:  
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));  
#>  
Content of myFile is:  
<#= myFile #>  
  
```  
  
 Se si utilizzano insieme gli attributi `inherits` e `hostspecific`, specificare host="trueFromBase" nella classe derivata e host="true" nella classe base. Ciò impedisce una doppia definizione della proprietà `Host` nel codice generato.  
  
## <a name="language-attribute"></a>attributo Language  
 Esempio:  
 `language="VB"`  
  
 Valori validi:  
 `C#` (impostazione predefinita)  
  
 `VB`  
  
 L'attributo di linguaggio specifica la lingua ([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]) da utilizzare per il codice sorgente nei blocchi di istruzioni e di espressioni. Il file di codice intermedio dal quale viene generato l'output utilizzerà questo linguaggio. Questo linguaggio non è correlato al linguaggio generato dal modello, che può essere qualsiasi tipo di testo.  
  
 Ad esempio:  
  
```vb  
<#@ template language="VB" #>  
<#@ output extension=".txt" #>  
Squares of numbers:  
<#  
  Dim number As Integer  
  For number = 1 To 4  
#>  
  Square of <#= number #> is <#= number * number #>  
<#  
  Next number  
#>  
  
```  
  
## <a name="inherits-attribute"></a>attributo Inherits  
 È possibile specificare che il codice del programma del modello può ereditare da un'altra classe che può essere generata anche da un modello di testo.  
  
### <a name="inheritance-in-a-run-time-preprocessed-text-template"></a>Ereditarietà in un modello di testo (pre-elaborato) della fase di esecuzione  
 È possibile utilizzare l'ereditarietà tra i modelli di testo della fase di esecuzione per creare un modello di base che disponga di molte varianti derivate. Modelli in fase di esecuzione sono quelli che dispongono di **lo strumento personalizzato** proprietà impostata su **TextTemplatingFilePreprocessor**. Un modello della fase di esecuzione genera codice che è possibile chiamare nell'applicazione per creare il testo definito nel modello. Per ulteriori informazioni, vedere [la generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Se non si specifica un attributo `inherits`, una classe di base e una classe derivata vengono generate dal modello di testo. Quando si specifica l'attributo `inherits`, viene generata solo la classe derivata. È possibile scrivere manualmente una classe di base, ma deve fornire i metodi utilizzati dalla classe derivata.  
  
 Più in generale è possibile specificare un altro modello pre-elaborato come classe di base. Il modello di base fornisce blocchi di testo comuni che possono essere interfogliati con il testo dei modelli derivati. È possibile utilizzare i blocchi della funzionalità di classe `<#+ ... #>` per definire i metodi che contengono frammenti di testo. Ad esempio, è possibile inserire il framework del testo di output nel modello di base, fornendo i metodi virtuali che possono essere sottoposti a override nei modelli derivati:  
  
 Modello di testo (pre-elaborato) della fase di esecuzione BaseTemplate.tt:  
 ```scr  
This is the common header.  
<#   
  SpecificFragment1();   
#>  
A common central text.  
<#   
  SpecificFragment2();   
#>  
This is the common footer.  
<#+   
  // Declare abstract methods  
  protected virtual void SpecificFragment1() { }  
  protected virtual void SpecificFragment2() { }  
#>  
  
```  
  
 Modello di testo (pre-elaborato) della fase di esecuzione DerivedTemplate1.tt:  
 ```csharp  
<#@ template language="C#" inherits="BaseTemplate" #>  
<#   
  // Run the base template:  
  base.TransformText();  
#>  
<#+  
// Provide fragments specific to this derived template:  
protected override void SpecificFragment1()  
{  
#>  
   Fragment 1 for DerivedTemplate1  
<#+  
}  
protected override void SpecificFragment2()  
{  
#>  
   Fragment 2 for DerivedTemplate1  
<#+  
}  
#>  
  
```  
  
 Codice dell'applicazione per richiamare DerivedTemplate1:  
 ```csharp  
Console.WriteLine(new DerivedTemplate().TransformText());  
```  
  
 Output risultante:  
 ```  
This is the common header.  
   Fragment 1 for DerivedTemplate1  
A common central text.  
   Fragment 2 for DerivedTemplate1  
This is the common footer.  
```  
  
 È possibile compilare le classi di base e derivate in progetti diversi. Ricordarsi di aggiungere il progetto di base o l'assembly di riferimenti del progetto derivato.  
  
 È inoltre possibile utilizzare una classe comune scritta manualmente come classe di base. La classe di base deve fornire i metodi utilizzati dalla classe derivata.  
  
> [!WARNING]
>  Se si utilizzano insieme gli attributi `inherits` e `hostspecific`, specificare hostspecific="trueFromBase" nella classe derivata e host="true" nella classe base. Ciò impedisce una doppia definizione della proprietà `Host` nel codice generato.  
  
### <a name="inheritance-in-a-design-time-text-template"></a>Ereditarietà in un modello di testo della fase di progettazione  
 Un modello di testo in fase di progettazione è un file per cui **lo strumento personalizzato** è impostato su **TextTemplatingFileGenerator**. Il modello genera un file di output di codice o testo che fa parte del progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per generare il file di output, il modello viene prima tradotto in un file del codice del programma intermedio che non viene in genere visualizzato. L'attributo `inherits` specifica la classe di base per questo codice intermedio.  
  
 Per un modello di testo della fase di progettazione, è possibile specificare qualsiasi classe di base derivata da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Utilizzare la direttiva `<#@assembly#>` per caricare l'assembly o il progetto contenente la classe di base.  
  
 Per ulteriori informazioni, vedere ["Ereditarietà in modelli di testo" nel Blog degli Mathew](http://go.microsoft.com/fwlink/?LinkId=208373).  
  
## <a name="linepragmas-attribute"></a>Attributo LinePragmas  
 Esempio:  
 `linePragmas="false"`  
  
 Valori validi:  
 `true` (impostazione predefinita)  
  
 `false`  
  
 Impostare questo attributo su false rimuove i tag che identificano i numeri di riga nel codice generato. Ciò significa che il compilatore segnalerà gli errori utilizzando i numeri di riga del codice generato. Ciò rende disponibili più opzioni di debug, infatti è possibile scegliere di eseguire il debug del modello di testo o del codice generato.  
  
 Questo attributo consente, inoltre, quando si che i nomi di file assoluti nei pragma stanno causando Distraggono nel controllo del codice sorgente.  
  
## <a name="visibility-attribute"></a>Attributo di visibilità  
 Esempio:  
 `visibility="internal"`  
  
 Valori validi:  
 `public` (impostazione predefinita)  
  
 `internal`  
  
 In un modello di testo della fase di esecuzione, imposta l'attributo di visibilità della classe generata. Per impostazione predefinita, la classe fa parte dell'API pubblica del codice, ma impostando `visibility="internal"` è possibile fare in modo che solo il proprio codice possa utilizzare la classe generatrice di testo.
