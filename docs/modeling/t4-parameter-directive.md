---
title: T4 Direttiva Parameter | Documenti Microsoft
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
ms.openlocfilehash: f44e25f9256cd37692970e92744d7564bc3abd19
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="t4-parameter-directive"></a>Direttiva parameter T4
In un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di testo, il `parameter` direttiva dichiara le proprietà nel codice del modello che vengono inizializzate dai valori passati dal contesto esterno. È possibile impostare questi valori se si scrive codice che richiama una trasformazione del testo.  
  
## <a name="using-the-parameter-directive"></a>Utilizzo della direttiva Parameter  
  
```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 Il `parameter` direttiva dichiara le proprietà nel codice del modello che vengono inizializzate dai valori passati dal contesto esterno. È possibile impostare questi valori se si scrive codice che richiama una trasformazione del testo. I valori possono essere passati nel `Session` dizionario, o in <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 È possibile dichiarare i parametri di qualsiasi tipo utilizzabile in remoto. Vale a dire, il tipo deve essere dichiarato con <xref:System.SerializableAttribute>, o deve derivare da <xref:System.MarshalByRefObject>. In questo modo i valori dei parametri da passare nell'AppDomain in cui viene elaborato il modello.  
  
 Ad esempio, è possibile scrivere un modello di testo con il seguente contenuto:  
  
```  
<#@ template language="C#" #>  
  
<#@ parameter type="System.Int32" name="TimesToRepeat" #>  
  
<# for (int i = 0; i < TimesToRepeat; i++) { #>  
Line <#= i #>  
<# } #>  
  
```  
  
## <a name="passing-parameter-values-to-a-template"></a>Passaggio dei valori di parametro a un modello  
 Se si sta scrivendo un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione, ad esempio un comando di menu o un gestore eventi, è possibile elaborare un modello utilizzando il servizio del modello di testo:  
  
```csharp  
// Get a service provider - how you do this depends on the context:  
IServiceProvider serviceProvider = dte; // or dslDiagram.Store, for example   
// Get the text template service:  
ITextTemplating t4 = serviceProvider.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
// Create a Session in which to pass parameters:  
host.Session = host.CreateSession();  
// Add parameter values to the Session:  
session["TimesToRepeat"] = 5;  
// Process a text template:  
string result = t4.ProcessTemplate("MyTemplateFile.t4",  
  System.IO.File.ReadAllText("MyTemplateFile.t4"));  
  
```  
  
## <a name="passing-values-in-the-call-context"></a>Passaggio di valori nel contesto di chiamata  
 In alternativa è possibile passare valori come dati logici in <xref:System.Runtime.Remoting.Messaging.CallContext>.  
  
 Nell'esempio seguente passa i valori utilizzando entrambi i metodi:  
  
```csharp  
ITextTemplating t4 = this.Store.GetService(typeof(STextTemplating)) as ITextTemplating;  
ITextTemplatingSessionHost host = t4 as ITextTemplatingSessionHost;  
host.Session = host.CreateSession();  
// Pass a value in Session:  
host.Session["p1"] = 32;  
// Pass another value in CallContext:  
System.Runtime.Remoting.Messaging.CallContext.LogicalSetData("p2", "test");  
  
// Process a small template inline:  
string result = t4.ProcessTemplate("",   
   "<#@parameter type=\"System.Int32\" name=\"p1\"#>"  
 + "<#@parameter type=\"System.String\" name=\"p2\"#>"  
 + "Test <#=p1#> <#=p2#>");  
  
// Result value is:  
//     Test 32 test  
  
```  
  
## <a name="passing-values-to-a-run-time-preprocessed-text-template"></a>Passaggio di valori per un modello di testo in fase di esecuzione (pre-elaborato)  
 Non è in genere, è necessario utilizzare il `<#@parameter#>` direttiva con modelli di testo (pre-elaborato) della fase di esecuzione. In alternativa, è possibile definire un costruttore aggiuntivo o una proprietà impostabile per il codice generato, tramite il quale si passano valori di parametro. Per ulteriori informazioni, vedere [la generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
 Tuttavia, se si desidera utilizzare `<#@parameter>` in un modello in fase di esecuzione, è possibile passare valori a esso utilizzando il dizionario di sessione. Ad esempio, se è stato creato il file come modello pre-elaborato chiamato `PreTextTemplate1`. È possibile richiamare il modello nel programma utilizzando il codice seguente.  
  
```csharp  
PreTextTemplate1 t = new PreTextTemplate1();  
t.Session = new Microsoft.VisualStudio.TextTemplating.TextTemplatingSession();  
t.Session["TimesToRepeat"] = 5;  
// Add other parameter values to t.Session here.  
t.Initialize(); // Must call this to transfer values.  
string resultText = t.TransformText();  
  
```  
  
## <a name="obtaining-arguments-from-texttemplateexe"></a>Acquisizione di argomenti da TextTemplate.exe  
  
> [!IMPORTANT]
>  Il `parameter` non recupera i valori impostati nella direttiva di `-a` parametro del `TextTransform.exe` utilità. Per ottenere questi valori, impostare `hostSpecific="true"` nel `template` direttiva e utilizzare `this.Host.ResolveParameterValue("","","argName")`.